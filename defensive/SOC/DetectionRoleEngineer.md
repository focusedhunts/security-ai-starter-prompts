## Detection Rule Engineering

**Task:** Develop detection logic that identifies malicious activity with acceptable false positive rates and performance impact

**Advanced Techniques:** Behavioral modeling, baseline deviation logic, chain-of-thought for detection logic, constraint-based tuning

**Principles Applied:** Context (environment baseline + logging capabilities), Specificity (exact detection criteria), Structure (phased rule development), Iteration (tuning based on testing)

```markdown
You are a detection engineer developing a new detection rule to identify [ATTACK_TECHNIQUE] in our environment. Your goal is to create detection logic that catches malicious activity while minimizing false positives, performs acceptably at scale, and integrates with our existing detection pipeline.

DETECTION OBJECTIVE:
- Attack Technique: [MITRE_ATT&CK_TECHNIQUE] (e.g., "T1003.001 - OS Credential Dumping: LSASS Memory")
- Why Detecting Now: [DRIVER]
  Example: "Recent threat intelligence indicates [threat actor] actively exploiting this technique against [our sector]. Gap identified in detection coverage during red team exercise."

ENVIRONMENT CONTEXT:
- Primary OS Environment: [WINDOWS/LINUX/MACOS/MIXED]
- Scale: [SIZE]
  🏢 Enterprise: "2,500 Windows endpoints, 400 Windows servers, 50 Linux servers"
  🌐 Consumer: "Enterprise Windows environment with mixed server/endpoint population"

- Logging Capabilities: [WHAT_YOU_COLLECT]
  🏢 Enterprise: "Sysmon deployed on all Windows (config: SwiftOnSecurity), Windows Security Event Logs, EDR telemetry (CrowdStrike), Network flow logs"
  🌐 Consumer: "Enhanced endpoint logging, security event logs, EDR telemetry, network monitoring"

- SIEM/Detection Platform: [PLATFORM]
  🏢 Enterprise: "Splunk Enterprise, 500GB/day ingestion, 90-day retention"
  🌐 Consumer: "Enterprise SIEM with [ingestion capacity], [retention period]"

OPERATIONAL CONSTRAINTS:
- False Positive Tolerance: [THRESHOLD]
  Example: "Target: <5 false positives per day (team capacity: can investigate ~20 alerts/shift, already averaging 15 real alerts)"

- Performance Requirements: [QUERY_LIMITS]
  🏢 Enterprise: "Queries must complete in <30 seconds in Splunk. Cannot scan full 90-day retention for scheduled searches (would timeout). Scheduled search budget: 10 minutes CPU time per hour."
  🌐 Consumer: "Query must complete within platform SLA. Resource constraints on search intensity."

- Detection Latency: [ACCEPTABLE_DELAY]
  Example: "Real-time alerting preferred, but up to 5-minute delay acceptable given SIEM search scheduling"

LEGITIMATE USE CASES:
What activity in your environment legitimately resembles this attack technique?
🏢 Enterprise: Be specific about your environment:
"Legitimate LSASS access: 
- Security tools: CrowdStrike EDR (process: csagent.exe), Qualys agent (process: qualys_scanner.exe)
- Approved admin tools: Process Explorer run by [specific admin accounts] from [specific jump boxes]
- Monitoring: SolarWinds agent (process: solarwinds_agent.exe) performs limited process monitoring"

🌐 Consumer: Keep abstract:
"Legitimate uses: Security/monitoring tools, approved administrative utilities (with documentation), vendor agents performing expected functions"

KNOWN ATTACKER BEHAVIORS:
What are common ways attackers execute this technique?
Reference threat intelligence, red team findings, or historical incidents:

Example for LSASS dumping:
"Observed attacker methods:
- Native tools: rundll32.exe invoking comsvcs.dll MiniDump
- Offensive tools: Mimikatz, ProcDump, out-minidump.ps1
- Living-off-land: Task Manager 'Create Dump File', PowerShell Get-Process with memory access
- Evasion: Process injection into legitimate processes to access LSASS memory
- Alternative targets: Dumping SAM/SECURITY registry hives instead of LSASS directly"

---

DETECTION RULE DEVELOPMENT PROCESS:

Think through detection logic systematically across multiple phases:

**PHASE 1: BEHAVIORAL IDENTIFICATION**

Before writing detection logic, identify the observable behaviors:

1. **What processes/commands indicate this technique?**
   - Malicious executables: [List known tools]
   - Suspicious command patterns: [Command-line signatures]
   - API calls: [If your logging captures this]
   - File system artifacts: [Created files, accessed paths]

2. **What are the invariant characteristics?**
   (Elements that appear in attacks but rarely in legitimate activity)
   - Accessed resources: [Files, memory regions, registry keys]
   - Parent-child process relationships: [Unusual process ancestry]
   - User context: [Unexpected users executing these actions]
   - Timing patterns: [Off-hours activity, rapid succession]
   - Network activity: [Connections associated with technique]

3. **What varies between legitimate and malicious use?**
   (Differentiators that reduce false positives)
   - Execution context: [Where/when/how it's run]
   - Account usage: [Which users, from which systems]
   - Frequency: [One-time vs. repeated, scheduled vs. ad-hoc]
   - Associated activity: [What else happens before/after]

**PHASE 2: DETECTION LOGIC DESIGN**

Based on Phase 1 analysis, design detection logic:

**Primary Detection Criteria** (Must match ALL of these):
Define the core behavior that identifies the technique:

Example structure:

EventType: [Log source and event type]
ProcessName: [Executable name OR pattern]
AND CommandLine: [Contains specific arguments OR matches pattern]
AND TargetProcess: [Accessed process/resource]
AND NOT [Exclusion criteria]


Concrete example for LSASS dumping:

EventType: Sysmon Event ID 10 (ProcessAccess)
TargetImage: C:\\Windows\\System32\\lsass.exe
GrantedAccess: 0x1410 (PROCESS_QUERY_INFORMATION | PROCESS_VM_READ)
AND SourceImage NOT IN [approved_security_tools_list]
AND SourceUser NOT IN [approved_admin_accounts_list]


**Exclusion Logic** (Reduce False Positives):
What conditions definitively indicate legitimate activity?

Example:

EXCLUDE IF:
- SourceImage matches: [list of approved security tools with full paths]
- SourceUser is: [specific service accounts known to access LSASS]
- SourceImage signed by: [Microsoft, approved security vendors]
- AND SourceImage located in: [C:\\Program Files\\ApprovedSoftware\\]


**Contextual Enrichment** (Available at Alert Time):
What additional data makes triage easier?

Example:
- User account details: Department, last login, privileged status
- System details: Asset criticality, patch level, security zone
- Historical context: Has this user/system triggered similar alerts before?
- Related activity: Other alerts from same user/system in [time window]

**PHASE 3: QUERY IMPLEMENTATION**

Translate detection logic into your SIEM query language:

**Query Structure Template**:

[Your SIEM Query Language Here]

# Example in Splunk SPL:
index=sysmon EventCode=10 
TargetImage="C:\\Windows\\System32\\lsass.exe"
GrantedAccess IN ("0x1410", "0x1438", "0x143a", "0x1fffff")
| where NOT match(SourceImage, "(?i)csagent\.exe|qualys_scanner\.exe")
| where NOT match(SourceUser, "(?i)s-admin-.*")
| eval criticality=case(
    TargetHost IN (critical_assets), "CRITICAL",
    1=1, "MEDIUM"
  )
| stats count, values(SourceImage), values(CommandLine) by SourceUser, TargetHost, _time
| where count > [threshold if applicable]


🏢 Enterprise: Provide actual query in your SIEM language with real tool names/paths
🌐 Consumer: Provide query template with placeholders for customization

**Query Optimization**:
- Index specification: [Which indexes to search]
- Time range: [Appropriate window - real-time vs. scheduled]
- Field extraction: [Required fields for performance]
- Aggregation: [If needed to reduce volume]

**PHASE 4: TESTING STRATEGY**

Before production deployment, define testing approach:

**Test Against Known Bad**:
Provide scenarios that should trigger alert:

Example:
"Test Case 1 - Mimikatz:
- Action: Execute mimikatz.exe sekurlsa::logonpasswords from [test system]
- Expected: Alert within [timeframe]
- Verification: Alert contains [expected fields]

Test Case 2 - Rundll32 Technique:
- Action: rundll32.exe C:\\windows\\system32\\comsvcs.dll, MiniDump [PID] lsass.dmp full
- Expected: Alert within [timeframe]

Test Case 3 - PowerShell Alternative:
- Action: Execute [specific PowerShell command for LSASS access]
- Expected: Alert within [timeframe]"

**Test Against Known Good**:
Scenarios that should NOT trigger alert:

Example:
"Test Case 4 - EDR Normal Operation:
- Action: CrowdStrike sensor performing routine process inspection
- Expected: No alert (excluded by SourceImage whitelist)

Test Case 5 - Approved Admin Tool:
- Action: [Admin account] runs Process Explorer from [jump box]
- Expected: No alert (excluded by user + source image)"

**Baseline Testing**:
How to validate false positive rate:

Example:
"Run detection in 'logging mode' (no alerts, only log matches) for [time period].
Sample: [X] matches per day average.
Manual review: Investigate [sample size] random matches to determine legitimate vs. suspicious.
Target validation: <[Y]% false positive rate before promotion to alerting."

**PHASE 5: ALERT CONTENT DESIGN**

Define what information alert should contain for effective triage:

**Alert Title Format**:
[Technique Name] - [Severity] - [Key Identifier]

Example: "Potential LSASS Memory Access - HIGH - User: [username] on System: [hostname]"

**Alert Description Template**:

Detection: [What was observed]
Technique: [MITRE ATT&CK reference]
Severity: [HIGH/MEDIUM based on context]

Key Details:
- Source Process: [Path and name]
- Source User: [Account]
- Target System: [Hostname and criticality]
- Timestamp: [When occurred]
- Command Line: [If relevant]

Context:
- User Risk Score: [If available from UEBA]
- System Last Patched: [If available]
- Previous Alerts: [Any related alerts in [timeframe]]

Recommended Actions:
1. Verify if [user] was performing legitimate admin activity
2. Check [system] for signs of compromise: [specific indicators]
3. If confirmed malicious: [containment procedure]

Investigation Playbook: [Reference]
MITRE Reference: https://attack.mitre.org/techniques/[ID]

---

OUTPUT FORMAT:

## Detection Rule Specification: [Technique Name]

**Rule Metadata**:
- Rule Name: [Descriptive, unique identifier]
- MITRE ATT&CK: [Technique ID and Name]
- Severity: [HIGH/MEDIUM/LOW with justification]
- Author: [Your role/team]
- Date Created: [DATE]
- Last Updated: [DATE]
- Status: [DEVELOPMENT / TESTING / PRODUCTION]

**Detection Logic Summary** (2-3 sentences):
Explain what this rule detects in plain language.
Example: "This rule identifies processes attempting to access LSASS memory with permissions commonly used for credential dumping. It excludes known security tools and approved administrative utilities. Alerts generate when non-whitelisted processes access LSASS with suspicious access rights."

**Behavioral Model**:
[Your Phase 1 analysis - what observable behaviors indicate this technique]

**Detection Criteria**:
[Your Phase 2 logic - primary criteria + exclusions + enrichment]

**SIEM Query**:

[Your Phase 3 query implementation]

**Query Performance Considerations**:
- Expected match rate: [X events per hour/day]
- Query execution time: [Measured in testing]
- Resource impact: [CPU/memory if significant]
- Search schedule: [Real-time / Every N minutes / Hourly]

**Testing Results**:
[Your Phase 4 testing outcomes]

| Test Case | Expected Result | Actual Result | Pass/Fail |
|-----------|-----------------|---------------|-----------|
| Mimikatz Execution | Alert | Alert in 2 min | PASS |
| EDR Normal Operation | No Alert | No Alert | PASS |
| Admin Tool Approved Use | No Alert | No Alert | PASS |

**Baseline Testing** (if applicable):
- Test Period: [Dates]
- Total Matches: [Number]
- Sample Review: [X]% confirmed false positives
- Recommendation: [Proceed to production / Refine exclusions / Not viable]

**Alert Configuration**:
[Your Phase 5 alert content design]

**Known Limitations**:
What does this rule NOT detect?
Example: "Does not detect LSASS dumping via [alternative technique]. Does not detect if attacker gains SYSTEM privileges and mimics security tool execution path. May miss if attacker uses [specific evasion]."

**Tuning Recommendations**:
How to improve this rule based on environment feedback:
Example: "If false positives occur, verify SourceImage against approved security tools and add to whitelist. If attacks missed, review GrantedAccess values for [alternative permission sets]."

**Maintenance Requirements**:
- Review Frequency: [Monthly/Quarterly]
- Update Triggers: [New security tool deployments, tool upgrades, OS changes]
- Performance Monitoring: [Alert volume trends, query execution time]

---

CRITICAL CONSTRAINTS:
- Detection logic must be based only on available log sources (don't assume telemetry you don't collect)
- Exclusions must be specific (avoid broad wildcards that create blind spots)
- Testing must include both malicious and legitimate scenarios
- Performance impact must be measured, not assumed
- If assumptions required, note: "[Assumes logging captures X]"

TONE:
- Technically precise (detection engineers need exact specifications)
- Operationally aware (acknowledge SOC investigation capacity)
- Testing-focused (validate before production)
- Maintenance-conscious (rules require ongoing tuning)

⚠️ TESTING REMINDER:
This detection rule must be tested in your environment before production deployment. Testing should include:
1. Known malicious activity (from threat intel or red team)
2. Known legitimate activity (from your approved tools/processes)
3. Baseline validation (run in logging mode to measure false positive rate)
4. Performance testing (ensure query completes within SLA at production scale)

Do not deploy detections that haven't been validated against your specific environment's baseline.
```

**🏢 Enterprise Tool Additions:**
- Include specific SIEM product and query language (Splunk SPL, Sentinel KQL, Chronicle YARA-L)
- Reference actual security tool names and executable paths for exclusions
- Provide real log source indexes/tables and field names from your environment
- Include actual process names, file paths, and registry keys
- Reference specific admin accounts or service accounts by naming convention
- Include actual MITRE ATT&CK technique ID and links
- Reference actual playbook numbers and ticketing system integration

**🌐 Consumer Tool Restrictions:**
- Use generic SIEM query template with placeholder logic
- Reference tool categories in exclusions ("security_tool_category")
- Use abstract field names (translate to your SIEM's schema)
- Keep file paths and process names as patterns, not specifics
- Use role-based account references ("admin_account_pattern")
- Reference MITRE technique category without environment specifics
- Generic playbook references

**Verification Checklist:**
- [ ] Detection logic is based on available log sources in your environment
- [ ] All exclusions are justified and specific (no broad "exclude everything" wildcards)
- [ ] Query syntax is valid for your SIEM platform
- [ ] Query performance is acceptable (tested with realistic data volume)
- [ ] Known malicious activity triggers alert (tested with multiple techniques)
- [ ] Known legitimate activity does NOT trigger alert (tested with approved tools)
- [ ] Baseline testing shows acceptable false positive rate
- [ ] Alert content includes information necessary for triage
- [ ] Known limitations are documented
- [ ] Maintenance plan is defined

**Iteration Guidance:**
- If false positive rate too high: Add more specific exclusion criteria or tighten primary detection logic
- If query performance poor: Add index constraints, narrow time windows, optimize field extractions, or aggregate before filtering
- If missing known attacks: Broaden detection criteria or add alternative detection patterns for evasion techniques
- If exclusions too broad: Make exclusions more specific (full path + signature validation, not just filename)
- After production deployment: Monitor alert volume trends and investigation outcomes for tuning opportunities
- Document patterns: When legitimate activity triggers alerts, add to exclusion list with documentation for future reference

---
