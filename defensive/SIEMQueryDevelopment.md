## SIEM Query Development

**Task:** Develop SIEM detection query for specific threat behavior with acceptable performance and false positive rate

**Advanced Techniques:** Query optimization, baseline awareness, false positive suppression, detection logic validation

**Principles Applied:** Context (SIEM platform + data sources), Specificity (exact detection criteria), Structure (query building phases), Iteration (tuning based on testing)

```markdown
You are a detection engineer developing a SIEM query to detect [SPECIFIC_THREAT_BEHAVIOR] in your environment. Your goal is to create a performant, accurate detection that integrates with existing alert workflow and produces actionable alerts for SOC analysts.

DETECTION OBJECTIVE:
- Threat Behavior: [WHAT_YOU_WANT_TO_DETECT]
  🏢 Enterprise: "Detect: Credential dumping via LSASS memory access using non-security tools. Driven by: Recent threat intel indicates [threat actor] using this technique against [our sector]."
  🌐 Consumer: "Detect: Suspicious memory access to authentication process. Driven by: Known attack technique targeting credentials."

- MITRE ATT&CK Mapping: [TECHNIQUE_ID]
  Example: "T1003.001 - OS Credential Dumping: LSASS Memory"

- Detection Priority: [CRITICAL / HIGH / MEDIUM / LOW]
  Example: "Priority: HIGH - Known technique, high impact (credential theft → lateral movement), recent threat actor use."

SIEM PLATFORM CONTEXT:
- SIEM Platform: [PRODUCT]
  🏢 Enterprise: "Splunk Enterprise 9.x"
  🌐 Consumer: "Enterprise SIEM platform"

- Query Language: [LANGUAGE]
  🏢 Enterprise: "SPL (Search Processing Language)"
  🌐 Consumer: "Platform-specific query language"

- Data Ingestion: [VOLUME]
  🏢 Enterprise: "500GB/day, 90-day retention"
  🌐 Consumer: "Enterprise-scale data ingestion"

- Search Performance Budget: [CONSTRAINTS]
  Example: "Scheduled searches must complete in <60 seconds. Real-time searches: <5 seconds for alert generation."

AVAILABLE DATA SOURCES:
List log sources relevant to this detection:

🏢 Enterprise: Be specific
"Available for Detection:
- Sysmon Logs (all Windows systems):
  - Event ID 10 (ProcessAccess): Source process, target process, granted access rights, call trace
  - Event ID 1 (ProcessCreate): Process creation with command line
  - Event ID 7 (ImageLoad): DLL loading
  - Index: index=sysmon
  - Fields: EventCode, SourceImage, TargetImage, GrantedAccess, CallTrace, User, Computer

- Windows Security Logs:
  - Event ID 4688 (Process Creation) - if command line logging enabled
  - Event ID 4673 (Sensitive Privilege Use)
  - Index: index=windows
  - Fields: EventCode, ProcessName, CommandLine, SubjectUserName, Computer

- EDR Telemetry (CrowdStrike):
  - Process telemetry, memory access events, module loads
  - Index: index=crowdstrike
  - Fields: event_type, process_name, target_process, access_rights, user, hostname

Logging Coverage: 100% Windows endpoints and servers"

🌐 Consumer: Keep generic
"Available Log Sources:
- Enhanced endpoint logging (process creation, memory access, DLL loads)
- Security event logs (authentication, privilege use)
- EDR telemetry
- Coverage: Enterprise endpoints"

BASELINE UNDERSTANDING:
What's normal in your environment that might look like this threat?

🏢 Enterprise: Be specific about your legitimate tools
"Legitimate LSASS Access (should NOT alert):
- CrowdStrike Falcon: csagent.exe (EDR sensor)
  - Typical GrantedAccess: 0x1410 (PROCESS_QUERY_INFORMATION | PROCESS_VM_READ)
  - Frequency: Continuous monitoring
  - Path: C:\\Program Files\\CrowdStrike\\csagent.exe

- Microsoft Defender: MsMpEng.exe
  - Typical GrantedAccess: 0x1410
  - Path: C:\\Program Files\\Windows Defender\\MsMpEng.exe

- Approved Admin Tools: Process Explorer (procexp64.exe)
  - Used by: [specific admin accounts]
  - From: [admin jump boxes only]
  - Typical GrantedAccess: 0x1fffff (full access)
  - Path: C:\\Program Files\\ProcessExplorer\\procexp64.exe

- Backup Software: Veeam
  - Process: veeam.backup.service.exe
  - Limited scheduled windows (daily 2-4am)

Baseline Volume: ~50 LSASS access events per day from legitimate sources"

🌐 Consumer: Abstract patterns
"Legitimate Activity:
- Security software (EDR, AV, monitoring tools)
- Approved administrative utilities
- Scheduled backup/monitoring tasks
Baseline: [X] events per day typically"

KNOWN ATTACKER BEHAVIORS:
How do attackers typically execute this technique?

"Malicious LSASS Access Patterns:
- Tools: Mimikatz (mimikatz.exe, mimilib.dll), ProcDump (procdump.exe), Dumpert, Out-Minidump.ps1
- Techniques:
  1. Direct process access: mimikatz.exe → lsass.exe
  2. Process injection: malware.exe → legitimate.exe → lsass.exe
  3. Living-off-land: rundll32.exe comsvcs.dll MiniDump [PID] [dumpfile]
  4. Task Manager: User right-clicks lsass.exe → Create Dump File

- Access Rights (GrantedAccess values indicating credential dumping intent):
  - 0x1410 (PROCESS_VM_READ | PROCESS_QUERY_INFORMATION) - Read memory
  - 0x1438 (Above + PROCESS_DUP_HANDLE)
  - 0x143a (Above + PROCESS_CREATE_THREAD)
  - 0x1fffff (PROCESS_ALL_ACCESS) - Full control

- Call Traces (indicating direct memory read - suspicious):
  - Contains: dbghelp.dll, dbgcore.dll (debugging/dumping libraries)

- Parent Processes (common attack origins):
  - cmd.exe, powershell.exe, wscript.exe, cscript.exe (script-based)
  - User-executed processes from unusual locations (C:\\Users\\*, C:\\Temp\\*)

- Timing: Often occurs during reconnaissance phase, may be automated (multiple attempts)"

---

SIEM QUERY DEVELOPMENT METHODOLOGY:

Build detection query in phases:

**PHASE 1: CORE DETECTION LOGIC**

Start with most specific indicators:

**Initial Query** (Cast wide net first):

spl
# Splunk SPL Example:
index=sysmon EventCode=10 
TargetImage="C:\\Windows\\System32\\lsass.exe"
| table _time, Computer, User, SourceImage, TargetImage, GrantedAccess, CallTrace

**Purpose**: Find ALL process access to lsass.exe
**Expected Volume**: [Estimate based on baseline]
Example: "~50 events/day from legitimate tools + unknown malicious"

**Analysis**: Run this query against 7 days of historical data.
- Review results: What legitimate activity appears?
- Identify patterns: Specific source processes, access rights, call traces
- Document findings: Build exclusion list

---

**PHASE 2: NOISE REDUCTION (False Positive Filtering)**

Add exclusions for known-good activity:

index=sysmon EventCode=10 
TargetImage="C:\\Windows\\System32\\lsass.exe"

# Filter: Known legitimate processes
| where NOT match(SourceImage, "(?i)csagent\.exe|MsMpEng\.exe|veeam\.backup\.service\.exe")

# Filter: Known legitimate paths (security tools typically in Program Files)
| where NOT match(SourceImage, "(?i)^C:\\\\Program Files\\\\(CrowdStrike|Windows Defender|Veeam)")

# Filter: Specific accounts + tools (admin using Process Explorer from jump box)
| where NOT (match(SourceImage, "(?i)procexp64\.exe") AND match(User, "(?i)^DOMAIN\\\\admin-"))

| table _time, Computer, User, SourceImage, TargetImage, GrantedAccess, CallTrace

**Analysis**: Re-run against 7 days.
- Remaining events: Likely malicious OR unidentified legitimate
- Validate: For each remaining source process, determine if legitimate (research, ask system owners)
- Iterate: Add more exclusions if legitimate, or refine detection if still noisy

**Goal**: Reduce to <5 events/day, ideally only malicious activity

---

**PHASE 3: ENHANCE FIDELITY (Add Suspicion Indicators)**

Rather than just excluding good, actively look for bad:

index=sysmon EventCode=10 
TargetImage="C:\\Windows\\System32\\lsass.exe"

# Exclusions (from Phase 2)
| where NOT match(SourceImage, "(?i)csagent\.exe|MsMpEng\.exe|veeam\.backup\.service\.exe")
| where NOT match(SourceImage, "(?i)^C:\\\\Program Files\\\\(CrowdStrike|Windows Defender)")

# Suspicion Indicators (favor these in results)
| eval suspicion_score=0

# HIGH suspicion: Access rights commonly used for dumping
| eval suspicion_score=if(match(GrantedAccess, "0x1410|0x1438|0x143a|0x1fffff"), suspicion_score+3, suspicion_score)

# HIGH suspicion: Call trace includes debugging DLLs
| eval suspicion_score=if(match(CallTrace, "(?i)dbghelp\.dll|dbgcore\.dll"), suspicion_score+3, suspicion_score)

# MEDIUM suspicion: Process from unusual location
| eval suspicion_score=if(match(SourceImage, "(?i)C:\\\\Users\\\\|C:\\\\Temp\\\\|C:\\\\ProgramData\\\\"), suspicion_score+2, suspicion_score)

# MEDIUM suspicion: Known offensive tool names (even if renamed, partial match)
| eval suspicion_score=if(match(SourceImage, "(?i)mimikatz|procdump|dumpert|minidump"), suspicion_score+2, suspicion_score)

# LOW suspicion: Scripting process (cmd, powershell, wscript)
| eval suspicion_score=if(match(SourceImage, "(?i)cmd\.exe|powershell\.exe|wscript\.exe|cscript\.exe"), suspicion_score+1, suspicion_score)

# Filter: Only alert on suspicion_score >= 3 (at least one HIGH indicator)
| where suspicion_score >= 3

| sort -suspicion_score
| table _time, Computer, User, SourceImage, TargetImage, GrantedAccess, CallTrace, suspicion_score

**Analysis**: Test against known malicious samples (if available from threat intel or prior incidents).
- Does query catch known attacks? (Validate true positive detection)
- Does query still have false positives? (Refine scoring or exclusions)
- Adjust threshold: Is suspicion_score >= 3 right balance, or should it be higher/lower?

---

**PHASE 4: ENRICHMENT (Add Context for Analysts)**

Make alerts actionable:


index=sysmon EventCode=10 
TargetImage="C:\\Windows\\System32\\lsass.exe"

# [All filtering and scoring logic from Phase 3]

# Enrichment: Lookup user details (department, title, last login)
| lookup user_inventory username as User OUTPUT department, title, last_login

# Enrichment: Lookup asset details (criticality, owner, patch level)
| lookup asset_inventory hostname as Computer OUTPUT asset_criticality, asset_owner, last_patched

# Enrichment: Recent authentication from this user (any unusual login sources?)
| join type=left User [
  search index=windows EventCode=4624 earliest=-24h
  | stats dc(src_ip) as unique_login_sources by User
]

# Enrichment: Other suspicious activity on this system (last 24h)
| join type=left Computer [
  search index=* (malware OR suspicious OR alert) host=Computer earliest=-24h
  | stats count as recent_alerts by host
  | rename host as Computer
]

# Enrichment: VirusTotal check (if hash available and VT integration exists)
# [Optional advanced integration]

| table _time, Computer, User, SourceImage, TargetImage, GrantedAccess, suspicion_score, department, asset_criticality, unique_login_sources, recent_alerts

**Purpose**: Provide analysts with context to triage faster
- Is this a high-value user/system? (Priority triage)
- Is this user/system showing other suspicious behavior? (Corroboration)
- Is this expected for this user's role? (Reduce false positives)

---

**PHASE 5: ALERT CONFIGURATION**

Configure as scheduled search or real-time alert:

**Alert Settings**:

Alert Name: Suspicious LSASS Memory Access - Potential Credential Dumping
Search Schedule: Every 5 minutes (real-time detection)
Search Window: -10m to now (10-minute lookback with overlap to prevent gaps)
Trigger Condition: Results > 0 (any match generates alert)
Throttle: Suppress duplicate alerts for same Computer + User + SourceImage for 1 hour
Alert Action: 
  - Email: SOC Analyst distribution list
  - Webhook: Ticketing system (ServiceNow, Jira)
  - SOAR: Enrich + Auto-contain (if integrated)

**Alert Message Template**:

Subject: [HIGH] Suspicious LSASS Memory Access on ${Computer}

Alert: Potential credential dumping detected via LSASS memory access

Details:
- System: ${Computer} (Criticality: ${asset_criticality})
- User: ${User} (Department: ${department})
- Source Process: ${SourceImage}
- Access Rights: ${GrantedAccess}
- Suspicion Score: ${suspicion_score}
- Time: ${_time}

Context:
- User's recent unique login sources: ${unique_login_sources} (normal: 1-2)
- Recent alerts on this system: ${recent_alerts}

Investigation Steps:
1. Verify if ${User} was performing legitimate admin activity (check with user/manager)
2. Review process tree: What spawned ${SourceImage}?
3. Check for credential misuse: Any unusual authentication or lateral movement from ${Computer}?
4. Isolate ${Computer} if confirmed malicious (EDR containment)

Playbook: [Link to LSASS Access Investigation Playbook]
MITRE ATT&CK: T1003.001

---

**PHASE 6: VALIDATION AND TUNING**

Test query before production deployment:

**Validation Checklist**:

✅ True Positive Testing:
- [ ] Query detects known malicious activity (mimikatz, procdump)
  - Test: Run mimikatz in test environment, confirm alert generates
  - Result: [PASS / FAIL]

- [ ] Query detects living-off-land technique
  - Test: rundll32 comsvcs.dll MiniDump [lsass PID] dump.dmp
  - Result: [PASS / FAIL]

✅ False Positive Testing:
- [ ] Query does NOT alert on legitimate security tools
  - Test: Verify CrowdStrike, Defender operations don't generate alerts
  - Result: [PASS / FAIL]

- [ ] Query does NOT alert on approved admin tools
  - Test: Admin using Process Explorer from jump box
  - Result: [PASS / FAIL]

✅ Performance Testing:
- [ ] Query completes within performance budget (<60 seconds)
  - Test: Run as scheduled search, measure execution time
  - Result: [TIME] seconds

- [ ] Query doesn't overload SIEM (reasonable resource consumption)
  - Test: Monitor search job inspector, CPU/memory usage
  - Result: [ACCEPTABLE / NEEDS OPTIMIZATION]

✅ Volume Testing:
- [ ] Alert volume is manageable (<10 alerts/day in typical environment)
  - Test: Run as scheduled search for 7 days, count alerts
  - Result: [X] alerts/day average

✅ Enrichment Testing:
- [ ] Lookups function correctly (user/asset data populates)
  - Test: Verify enrichment fields in alert output
  - Result: [PASS / FAIL]

**Tuning Based on Results**:

IF true positive tests fail:
  → Detection logic too restrictive, revisit Phase 3 (may need to lower suspicion threshold)

IF false positive tests fail:
  → Add more exclusions (Phase 2), or tighten suspicion indicators (Phase 3)

IF performance tests fail:
  → Optimize query:
    - Narrow index/sourcetype selection
    - Add time constraints (earliest=-24h instead of searching all 90 days)
    - Use indexed fields (avoid regex on non-indexed fields)
    - Use summary indexing if query runs repeatedly on same data

IF volume too high:
  → Increase suspicion score threshold, add more exclusions, or aggregate alerts (e.g., alert only if same user/system triggers >3 times in 1 hour)

IF enrichment fails:
  → Verify lookup tables exist and are populated, check join syntax

---

OUTPUT FORMAT:

## SIEM Detection Rule: [RULE_NAME]

**Rule Metadata**:
- Rule Name: [Descriptive name]
- Rule ID: [Unique identifier for tracking]
- MITRE ATT&CK: [Technique ID and name]
- Severity: [CRITICAL / HIGH / MEDIUM / LOW]
- Author: [Your name/team]
- Date Created: [DATE]
- Last Updated: [DATE]
- Status: [DEVELOPMENT / TESTING / PRODUCTION]

**Detection Summary** (2-3 sentences):
[Explain what this rule detects in plain language]

Example: "This rule detects suspicious process access to lsass.exe memory, which is commonly used by attackers to dump credentials (Mimikatz, ProcDump). It excludes known legitimate security tools and applies suspicion scoring to prioritize high-confidence alerts for SOC investigation."

---

### DETECTION LOGIC

**Data Sources**:
[Your available data sources from context]

**Core Detection Criteria**:
[Your Phase 1 initial query showing what you're looking for]

**False Positive Filtering**:
[Your Phase 2 exclusion logic with justification]

**Suspicion Indicators**:
[Your Phase 3 scoring logic with thresholds]

**Enrichment**:
[Your Phase 4 context additions]

---

### COMPLETE SIEM QUERY

# Platform: [Splunk / Sentinel / Chronicle / Other]
# Language: [SPL / KQL / YARA-L / Other]

[Your complete, production-ready query from Phase 3-4]

**Query Performance**:
- Execution Time: [X] seconds (Target: <60s)
- Events Scanned: [Y] per search (5-minute window)
- Resource Impact: [LOW / MEDIUM / HIGH]

**Expected Alert Volume**:
- Baseline Environment: [X] alerts per day
- During Attack: [Y] alerts per incident

---

### ALERT CONFIGURATION

**Search Schedule**: [Frequency]
**Search Window**: [Timeframe]
**Trigger Condition**: [Criteria]
**Throttling**: [Deduplication logic]

**Alert Actions**:
- [Action 1]: Example: "Send email to soc-alerts@company.com"
- [Action 2]: Example: "Create ticket in ServiceNow (P2 priority)"
- [Action 3]: Example: "Trigger SOAR playbook: LSASS-Investigation"

**Alert Message Template**:

[Your Phase 5 alert message template]


---

### INVESTIGATION GUIDANCE

**Triage Questions** (for SOC analysts):
1. Was ${User} performing legitimate administrative tasks at ${_time}?
   - Action: Contact user/manager for verification
   
2. What process tree led to ${SourceImage} execution?
   - Action: Review Sysmon Event ID 1 (ProcessCreate) for parent process
   - Look for: cmd.exe, powershell.exe with suspicious command lines

3. Is there evidence of credential misuse after this event?
   - Action: Search for unusual authentication from ${User} or ${Computer}
   - Timeframe: 1 hour after alert timestamp to present
   
4. Are there other indicators of compromise on ${Computer}?
   - Action: Review recent EDR alerts, file modifications, network connections
   
5. Has ${SourceImage} been seen elsewhere in environment?
   - Action: Search for same file hash across all systems

**Investigation Playbook**: [Link to detailed IR procedure]

**MITRE ATT&CK Context**:
- Technique: T1003.001 - OS Credential Dumping: LSASS Memory
- Tactic: Credential Access
- Detection: Process monitoring (Sysmon Event ID 10)
- Mitigation: Credential Guard, Protected Process Light for LSASS
- Related Techniques: T1003.002 (Security Account Manager), T1003.003 (NTDS)

---

### VALIDATION RESULTS

**True Positive Testing**:
[Your Phase 6 TP test results]

**False Positive Testing**:
[Your Phase 6 FP test results]

**Performance Testing**:
[Your Phase 6 performance results]

**Volume Testing**:
[Your Phase 6 volume results - alerts per day]

**Tuning History**:
| Date | Change | Reason | Impact |
|------|--------|--------|--------|
| [DATE] | Initial deployment | N/A | Baseline: [X] alerts/day |
| [DATE] | Added exclusion for Veeam | False positives from backup | Reduced to [Y] alerts/day |
| [DATE] | Increased suspicion threshold to 4 | Too many low-confidence alerts | Reduced to [Z] alerts/day |

---

### MAINTENANCE

**Review Schedule**: [Monthly / Quarterly]

**Update Triggers**:
- New legitimate security tools deployed (update exclusions)
- New attack techniques observed (update suspicion indicators)
- Performance degradation (optimize query)
- False positive patterns (add exclusions or tune scoring)

**Exclusion List Maintenance**:
- Review quarterly: Are all exclusions still valid?
- Process: Any excluded tool decommissioned should be removed from exclusion list

**Dependencies**:
- Lookup Tables: `user_inventory`, `asset_inventory` (refresh: daily)
- Data Sources: Sysmon Event ID 10 (if logging fails, detection fails)
- Infrastructure: SIEM search scheduler (if down, no alerts)

---

### KNOWN LIMITATIONS

What does this detection NOT catch?

1. **Evasion via Direct Syscalls**: Attackers using direct NT API calls bypass hooking mechanisms that create Event ID 10 logs
   - Likelihood: LOW (advanced technique)
   - Mitigation: Kernel-level EDR with syscall monitoring

2. **Credential Theft via Alternative Methods**: This detects LSASS access, not SAM hive theft or NTDS.dit extraction
   - Mitigation: Separate detections for T1003.002 and T1003.003

3. **Attack from SYSTEM Context Mimicking Security Tools**: Attacker gains SYSTEM, renames malware to csagent.exe or signs with stolen certificate
   - Likelihood: MEDIUM (sophisticated attackers)
   - Mitigation: Verify process signatures and paths, not just names

4. **Network-Based Credential Theft**: Pass-the-hash, pass-the-ticket attacks don't access LSASS memory
   - Mitigation: Separate network-based detections (Kerberos ticket anomalies)

**Recommendation**: Layer multiple credential access detections to cover various techniques (defense-in-depth)

---

### APPENDICES

**Appendix A: Reference Queries**

Useful related queries for investigation:

# Find process tree for suspicious process:
index=sysmon EventCode=1 host=${Computer} ${SourceImage}
| fields _time, ParentImage, Image, CommandLine, User
| sort _time

# Search for unusual authentication after credential access:
index=windows EventCode=4624 host=${Computer} earliest=[alert_time] latest=now
| where Logon_Type!="2" AND Logon_Type!="7" 
| stats count by User, src_ip, Logon_Type

**Appendix B: Known Attack Samples**

For testing, reference these known malicious samples:
- Mimikatz: [SHA256 hash]
- ProcDump: [SHA256 hash]
- Out-Minidump.ps1: [SHA256 hash or GitHub link]

**Appendix C: Threat Intelligence Sources**

- [TTP documentation from threat intel]
- [Recent incident reports using this technique]
- [MITRE ATT&CK technique page]

---

**Detection Rule Maintained By**: [Detection Engineering Team]
**Feedback**: [How to report false positives or missed detections]

---

CRITICAL CONSTRAINTS:
- Query must be syntactically valid for stated SIEM platform (test before production)
- Exclusions must be specific (avoid wildcards that create blind spots)
- Performance must meet organizational SLA (don't create queries that timeout)
- Alert volume must be manageable for SOC capacity (don't overwhelm analysts)
- Enrichment lookups must exist and be maintained (document dependencies)
- If assumptions required, note: "[Assumes Sysmon Event ID 10 logging enabled]"

TONE:
- Technically precise (detection engineers need exact query syntax)
- Operationally aware (SOC analysts need actionable alerts)
- Performance-conscious (SIEM resources are finite)
- Maintenance-oriented (detections require ongoing tuning)

⚠️ DETECTION ENGINEERING REMINDER:
SIEM detections are living systems requiring ongoing maintenance:
1. Test thoroughly before production (false positives erode analyst trust)
2. Validate true positive detection with known attack samples
3. Monitor alert volume and quality after deployment
4. Tune based on feedback from SOC analysts
5. Update when environment changes (new tools, decommissioned systems)
6. Document rationale for exclusions (future engineers need context)

Detection rules optimize over time through systematic validation and tuning.
```

**🏢 Enterprise Tool Additions:**
- Include specific SIEM product and exact query language
- Provide actual index names, source types, and field names from your SIEM
- Reference actual security tool names and file paths for exclusions
- Include real process names, service accounts, and system details
- Provide actual lookup table names and schemas
- Reference specific alert distribution lists and ticketing integrations
- Include actual playbook links and documentation references

**🌐 Consumer Tool Restrictions:**
- Use generic SIEM query templates
- Provide conceptual field names (translate to your schema)
- Reference tool categories in exclusions
- Use generic process patterns
- Abstract lookup concepts without specific implementations
- Generic alerting workflows
- Conceptual investigation guidance

**Verification Checklist:**
- [ ] Query syntax is valid for target SIEM platform
- [ ] Query executes within performance budget (tested with production data volume)
- [ ] True positive detection validated (detects known malicious activity)
- [ ] False positive rate acceptable (tested against baseline for 7+ days)
- [ ] Exclusions are specific and justified (documented rationale)
- [ ] Enrichment lookups function correctly (tested with sample data)
- [ ] Alert template includes investigation guidance
- [ ] Dependencies documented (logging requirements, lookup tables)
- [ ] Known limitations identified and documented

**Iteration Guidance:**
- If query times out: Optimize with narrower time ranges, indexed field filters, or summary indexing
- If too many false positives: Add more specific exclusions or increase suspicion threshold
- If missing attacks: Lower suspicion threshold, broaden detection logic, or add alternative indicators
- If alert volume too high: Aggregate similar alerts, increase throttle window, or require multiple corroborating indicators
- After deployment: Monitor weekly and tune based on SOC analyst feedback and investigation outcomes
- When environment changes: Update exclusions for new security tools and revalidate detection accuracy

---
