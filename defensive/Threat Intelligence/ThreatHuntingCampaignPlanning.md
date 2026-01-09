## Threat Hunting Campaign Planning

**Task:** Design structured threat hunting campaign to proactively identify undetected threats in environment

**Advanced Techniques:** Hypothesis-driven approach, TTPs mapping, data source planning, systematic investigation workflow

**Principles Applied:** Context (threat landscape + environment visibility), Structure (phased hunting approach), Specificity (testable hypotheses), Iteration (refinement based on findings)

```markdown
You are a threat hunter planning a proactive hunting campaign to search for [THREAT_TYPE] that may have evaded existing detections. Your goal is to develop a structured hunting plan with testable hypotheses, defined data sources, and systematic investigation procedures.

CAMPAIGN OBJECTIVE:
- Threat Focus: [SPECIFIC_THREAT]
  🏢 Enterprise: "Hunt for indicators of [specific ransomware family] infrastructure based on recent threat intelligence indicating our sector targeting. Recent incident at [peer organization] used similar TTPs."
  🌐 Consumer: "Hunt for ransomware-related activity based on recent sector-specific threat intelligence and peer incident reports."

- Campaign Driver: [REASON]
  Example: "Recent threat intel suggests [threat actor] actively targeting [our industry] using [technique]. Our current detection coverage for this TTP is limited to [known signatures]. Hunt goal: identify novel or evasive variants we haven't detected."

- Success Criteria: [MEASURABLE_OUTCOMES]
  Example: "Validate no [threat] presence in environment, OR identify undetected compromise requiring response, OR develop new detection logic for ongoing monitoring."

THREAT INTELLIGENCE CONTEXT:
What do you know about this threat?

**Threat Actor Profile** (if applicable):
- Actor Name/ID: [Reference from threat intel]
- Motivation: [Financial, Espionage, Destructive]
- Typical Targets: [Industries, organization sizes, geographies]
- Sophistication Level: [Opportunistic / Moderate / Advanced]

**Known TTPs** (MITRE ATT&CK Framework):
List specific techniques this threat typically employs:

Example:
"Known TTPs for [threat]:
- Initial Access: T1566.001 (Spearphishing Attachment), T1190 (Exploit Public-Facing Application)
- Execution: T1059.001 (PowerShell), T1059.003 (Windows Command Shell)
- Persistence: T1053.005 (Scheduled Task), T1547.001 (Registry Run Keys)
- Privilege Escalation: T1068 (Exploitation for Privilege Escalation)
- Defense Evasion: T1070.004 (File Deletion), T1562.001 (Disable or Modify Tools)
- Credential Access: T1003.001 (LSASS Memory), T1555 (Credentials from Password Stores)
- Discovery: T1082 (System Information Discovery), T1083 (File and Directory Discovery)
- Lateral Movement: T1021.001 (Remote Desktop Protocol), T1021.002 (SMB/Windows Admin Shares)
- Collection: T1560.001 (Archive via Utility)
- Exfiltration: T1041 (Exfiltration Over C2 Channel)
- Impact: T1486 (Data Encrypted for Impact)"

**Indicators of Compromise** (if available):
🏢 Enterprise: Include specific IoCs from your threat intelligence:
"Known IoCs for [threat]:
- C2 Domains: [example.com, malicious-domain.net] (sanitized examples)
- File Hashes: [MD5/SHA256 hashes]
- Mutex Names: [specific strings]
- Registry Keys: [specific paths]
- User-Agents: [specific strings]
- SSL Certificate Subjects: [specific strings]"

🌐 Consumer: Reference IoC categories:
"IoC Categories:
- Network indicators (C2 infrastructure patterns)
- File-based indicators (malware signatures)
- Host-based artifacts (registry/file system indicators)
- Behavioral patterns"

ENVIRONMENT CONTEXT:
- Environment Size: [SCOPE]
  🏢 Enterprise: "Windows: 2,500 endpoints, 400 servers. Linux: 50 servers. Network: 3 data centers, AWS presence (50 EC2 instances)."
  🌐 Consumer: "Enterprise Windows environment with limited Linux presence, hybrid cloud deployment."

- Crown Jewels: [CRITICAL_ASSETS]
  🏢 Enterprise: "Domain controllers (DC01, DC02, DC03), Financial database (FINDB-PROD), Customer data warehouse (DWPROD-01), Payment processing systems"
  🌐 Consumer: "Authentication infrastructure, financial systems, customer data repositories, payment processing"

- Known Visibility Gaps: [LOGGING_LIMITATIONS]
  Example: "Limited visibility: Legacy Linux systems (no EDR, basic syslog only), SCADA network (isolated, no central logging), Mobile device management (limited endpoint telemetry)"

AVAILABLE DATA SOURCES:
What telemetry can you hunt across?

🏢 Enterprise: List specific tools and data:
"Available for Hunting:
- EDR: CrowdStrike Falcon (all Windows systems, 90-day retention)
- SIEM: Splunk (Windows Security logs, Sysmon, Firewall, Proxy, DNS, AD logs - 90 days)
- Network: Zeek/Bro IDS logs (flows, conn, DNS, HTTP - 30 days)
- Threat Intel: MISP feeds, [commercial feeds], internal IoC database
- Asset Inventory: ServiceNow CMDB (all endpoints, servers, network devices)
- Proxy: Zscaler logs (web traffic, 60 days)
- Email Gateway: Proofpoint logs (email metadata, 180 days)"

🌐 Consumer: Keep sources generic:
"Available Data Sources:
- Endpoint detection and response telemetry (retention: [period])
- SIEM aggregating multiple log sources (retention: [period])
- Network monitoring (flows, DNS, HTTP - retention: [period])
- Threat intelligence feeds (internal and external)
- Asset inventory (endpoint and server catalog)
- Proxy/web filtering logs (retention: [period])
- Email security logs (retention: [period])"

HUNTING TEAM CONTEXT:
- Team Composition: [PEOPLE]
  Example: "2 threat hunters (you + 1 colleague), can request support from SOC analysts for specific investigations, 1 week dedicated time for this campaign."

- Time Allocation: [DURATION]
  Example: "Campaign duration: 5 business days. Estimated 60% hunting time (meetings, on-call duties reduce dedicated time)."

- Reporting Stakeholder: [WHO]
  Example: "Results briefing to: CISO, SOC Manager, IR Lead. Deliverable: Campaign summary with findings, recommended detections, IR tickets for any compromises found."

---

THREAT HUNT CAMPAIGN DESIGN:

Think through hunting campaign systematically:

**PHASE 1: HYPOTHESIS DEVELOPMENT**

Generate specific, testable hypotheses about threat presence:

**Hypothesis Template**:

H[number]: If [threat actor/behavior] is present in our environment, then we should observe [specific evidence] in [data source] because [reasoning based on TTPs].

Develop 3-5 hypotheses covering different attack stages:

**Example Hypotheses:**

**H1 - Initial Compromise**:
"If [ransomware operator] successfully phished credentials in the past 90 days, then we should observe unusual VPN authentication patterns (successful logins from new geolocations followed by internal network activity outside business hours) in AD/VPN logs because ransomware operators commonly test stolen credentials before main attack."

Data Source: Active Directory authentication logs, VPN logs
Timeframe: 90 days lookback
Success Indicator: Unusual auth pattern + subsequent internal activity correlation

**H2 - Credential Access**:
"If [threat] accessed credentials via LSASS dumping, then we should observe non-standard process access to lsass.exe from systems where security tools didn't alert in EDR process access logs because attackers use techniques that evade signature-based detection."

Data Source: EDR process telemetry (Sysmon Event ID 10 or equivalent)
Timeframe: 90 days lookback
Success Indicator: LSASS access from unexpected processes/users with no corresponding security tool alert

**H3 - Lateral Movement**:
"If [threat] moved laterally using RDP, then we should observe RDP connections from workstations to servers (unusual pattern) or RDP connections during off-hours to critical assets in Windows Security logs because ransomware operators use RDP for lateral movement to high-value targets."

Data Source: Windows Event ID 4624 (Logon Type 10 - RemoteInteractive)
Timeframe: 90 days lookback
Success Indicator: Workstation-to-server RDP sessions or off-hours RDP to crown jewels

**H4 - C2 Communication**:
"If [threat] maintains C2 infrastructure, then we should observe periodic outbound connections to uncommon domains with [characteristic pattern] in DNS/Proxy logs because ransomware C2 often uses DGA domains or recently-registered domains with specific patterns."

Data Source: DNS queries, Proxy logs, Firewall outbound connections
Timeframe: 30 days (network logs retention)
Success Indicator: Connections to domains matching [threat] C2 profile (age, TLD, entropy, threat intel)

**H5 - Pre-Ransomware Staging**:
"If [threat] is staging for ransomware deployment, then we should observe unusual file staging activity (large archive creation, file system enumeration, disabling of security tools) in file system logs and EDR telemetry because ransomware operators prepare environment before payload deployment."

Data Source: EDR file system activity, Windows Security logs (service modifications)
Timeframe: 30 days (recent staging would be most actionable)
Success Indicator: Archive utility usage + security service tampering + unusual file enumeration on same system

---

**PHASE 2: DATA COLLECTION STRATEGY**

For each hypothesis, define data collection approach:

**Collection Plan Template**:

**Hypothesis**: [H number and description]

**Data Source(s)**: [Specific logs/telemetry]

**Query/Search Strategy**:
🏢 Enterprise: Provide actual SIEM query

# Example Splunk query for H1:
index=windows EventCode=4624 Logon_Type=3 
| where NOT match(Source_Network_Address, "^10\.|^172\.(1[6-9]|2[0-9]|3[01])\.|^192\.168\.")
| stats dc(Source_Network_Address) as unique_sources, 
        earliest(_time) as first_seen, 
        latest(_time) as last_seen by Account_Name
| where unique_sources > 1 AND (tonumber(strftime(first_seen, "%H")) < 6 OR tonumber(strftime(first_seen, "%H")) > 20)
| eval geographic_diversity="External sources: " . unique_sources

🌐 Consumer: Provide query logic conceptually

# Conceptual query for H1:
Filter: Authentication events (successful logons)
Criteria: Source IP outside internal ranges
Group By: Account name
Aggregate: Count unique source IPs, earliest/latest timestamp
Filter Results: Multiple external sources AND outside business hours
Output: Accounts with unusual geographic authentication patterns

**Baseline Understanding**:
What's "normal" in your environment for this hypothesis?
Example for H1: "Normal VPN usage: ~200 unique users/day, 95% from [home country], primarily 7am-7pm. International travel: typically [specific executives] with advance notice via [travel request system]."

**Expected Volume**:
How many results do you anticipate reviewing?
Example: "Expect ~500 external authentication events/day = 45K over 90 days. After filtering for unusual patterns, estimate ~50-100 accounts requiring manual review."

**Analysis Approach**:
How will you triage results to identify true threats?
Example: "For each flagged account:
1. Verify if user was traveling (check travel calendar, expense reports, or direct user contact)
2. Review subsequent activity: What did user access after unusual login?
3. Correlate with other hypotheses: Does same user appear in credential access or lateral movement data?
4. Asset context: Did user access sensitive systems? Unusual for their role?"

---

**PHASE 3: HUNTING EXECUTION PLAN**

Define systematic execution approach:

**Day 1: Initial Reconnaissance**
- Morning: Execute H1 and H2 queries (authentication and credential access patterns)
- Afternoon: Triage results, identify accounts/systems requiring deeper investigation
- Output: Priority list of suspicious accounts/systems for Day 2 pivot

**Day 2: Behavioral Analysis**
- Morning: Execute H3 and H4 queries (lateral movement and C2 communication)
- Afternoon: Correlate findings across hypotheses (do same accounts appear in multiple datasets?)
- Output: Correlated timeline of suspicious activity if patterns emerge

**Day 3: Targeted Investigation**
- Morning: Deep dive on highest-priority findings from Days 1-2
- Afternoon: Execute H5 query (pre-ransomware staging indicators)
- Output: Determination if findings represent actual compromise or false positives

**Day 4: Crown Jewels Focus**
- Morning: Hunt specifically on critical assets (domain controllers, financial systems)
- Apply all hypotheses narrowly to crown jewels even if negative results on broader hunt
- Afternoon: Analyze any privilege escalation or persistence mechanisms on critical systems
- Output: High-confidence assessment of crown jewel security status

**Day 5: Synthesis and Detection Engineering**
- Morning: Compile findings, create incident tickets if compromise found
- Afternoon: Develop detection logic for any hunting queries that revealed gaps
- Output: Campaign report + detection rules + IR tickets

---

**PHASE 4: FINDINGS DOCUMENTATION**

Define how results will be documented:

**For Each Hypothesis:**

**Hypothesis H[number]**: [Restate hypothesis]

**Data Analyzed**: [Volume and sources reviewed]
Example: "Analyzed 45,323 external authentication events across 90 days from AD and VPN logs"

**Key Findings**:

NEGATIVE (No Threat Detected):
- No accounts showed [suspicious pattern] outside established baseline
- [X] accounts required manual review, all explained by [legitimate activity]
- Conclusion: No evidence supporting hypothesis

POSITIVE (Potential Threat / Investigation Required):
- Account [sanitized identifier] showed [specific suspicious pattern]
- Timeline: [Dates and activities]
- Context: [Why this is concerning]
- Action: Created IR ticket [reference] for full investigation
- Preliminary assessment: [Confidence level] this represents compromise

INCONCLUSIVE (Requires Further Investigation):
- Observed [pattern] that's ambiguous
- Context: [Why can't determine malicious vs. legitimate]
- Action: [Follow-up investigation plan]

**Detection Gap Identified**: (If applicable)
"Current detections do not cover [specific behavior]. Recommend implementing detection for [scenario] using [approach]. Draft detection logic provided in Appendix."

**False Positive Lessons**:
"During hunting, [X] false positives resulted from [pattern]. Recommend [tuning action] to improve signal-noise ratio in future campaigns."

---

**PHASE 5: CAMPAIGN DELIVERABLES**

**Campaign Summary Report**:
- Executive Summary (1 page): What was hunted, what was found (or not found), recommendations
- Methodology: Hypotheses and approach
- Detailed Findings: Results per hypothesis
- Detection Recommendations: New rules to implement
- Process Improvements: Lessons for future campaigns

**Technical Artifacts**:
- SIEM queries used (documented and validated)
- IoC lists generated (if any new indicators discovered)
- Detection logic (for any new rules developed)
- Investigation notes (for any incidents identified)

**Metrics**:
- Data volume analyzed: [Size and sources]
- Hypotheses tested: [Number and types]
- True positives: [Number requiring IR]
- False positives: [Number and patterns]
- Detection gaps: [Number identified]
- New detections: [Number created]

---

OUTPUT FORMAT:

## Threat Hunt Campaign Plan: [Campaign Name]

**Campaign Metadata**:
- Campaign Name: [Descriptive identifier]
- Threat Focus: [Specific threat being hunted]
- Lead Hunter: [Your role]
- Team: [Additional hunters/support]
- Start Date: [DATE]
- Duration: [Time allocated]
- Status: [PLANNING / ACTIVE / COMPLETE]

**Campaign Objective** (2-3 sentences):
[Clear statement of what you're hunting and why]

**Threat Intelligence Summary**:
[Your threat actor profile and known TTPs]

**Environment Context**:
[Your environment scope and critical assets]

**Hypotheses**:
[Your Phase 1 hypotheses - numbered list with data source mapping]

**Data Collection Strategy**:
[Your Phase 2 collection plans per hypothesis]

**Execution Plan**:
[Your Phase 3 day-by-day hunting schedule]

**Success Criteria**:
How you'll determine campaign success:
- [ ] All hypotheses tested with documented results
- [ ] High-confidence assessment of [threat] presence/absence
- [ ] Any detected compromises escalated to IR
- [ ] Detection gaps documented with remediation plan
- [ ] Campaign findings briefed to [stakeholders]

**Risk Considerations**:
What could go wrong during this campaign?
- Data availability: [Risk that log sources unavailable]
- False positive burden: [Risk that hunt generates excessive false positives consuming time]
- Attacker awareness: [Risk that hunting queries alert sophisticated attacker to being hunted]
- Resource constraints: [Risk that other priorities interrupt campaign]

**Contingency Plans**:
- If H1-H3 all negative: [Expand to lower-priority hypotheses or declare high confidence in "no threat present"]
- If positive findings: [Immediate escalation to IR, preserve evidence, continue hunt to determine scope]
- If data gaps discovered: [Pivot to alternative data sources or document for future visibility improvement]

---

CRITICAL CONSTRAINTS:
- Hypotheses must be testable with available data sources (don't hypothesize about data you don't collect)
- Queries must be performant at your data scale (don't design queries that timeout)
- Timeline must be realistic given team capacity (don't over-commit)
- Focus must be narrow enough to complete in allocated time (broad "hunt for everything" campaigns fail)
- If assumptions required, note: "[Assumes threat intel accurate]" or "[Assumes logs contain X field]"

TONE:
- Hypothesis-driven (scientific method applied to threat hunting)
- Systematic (structured approach, not random exploration)
- Evidence-based (findings supported by data)
- Actionable (deliver outcomes that improve security posture)

⚠️ HUNTING REMINDER:
Threat hunting is resource-intensive work that should result in actionable outcomes:
1. High-confidence determination of threat presence/absence
2. Incident response investigations for any compromise discovered
3. New detection logic to prevent future manual hunting for same threats
4. Improved understanding of environment baseline and detection coverage gaps

Document lessons learned to improve future campaigns.
```

**🏢 Enterprise Tool Additions:**
- Include specific threat actor names from your threat intelligence
- Reference actual IoCs (domains, hashes, IPs) appropriately sanitized
- Provide real SIEM queries in your platform's language
- Name specific data sources (CrowdStrike, Splunk indexes, etc.)
- Include actual critical asset hostnames (appropriately sanitized)
- Reference actual MITRE ATT&CK technique IDs
- Include actual team member names/roles and campaign timeline dates
- Reference specific incident response ticketing system

**🌐 Consumer Tool Restrictions:**
- Use threat actor categories ("ransomware operator", "APT group")
- Provide IoC patterns rather than specific indicators
- Offer query logic conceptually, not platform-specific syntax
- Use generic data source categories
- Abstract critical assets to types ("authentication servers", "financial systems")
- Reference MITRE technique categories generally
- Use generic roles and relative timelines
- Generic IR process references

**Verification Checklist:**
- [ ] Each hypothesis is testable with stated available data sources
- [ ] Queries are syntactically valid for your SIEM platform (if enterprise)
- [ ] Expected data volumes are realistic for your environment scale
- [ ] Timeline is achievable given stated team capacity and competing priorities
- [ ] Hypotheses cover multiple stages of attack lifecycle (not just one TTP)
- [ ] Baseline understanding is documented to distinguish anomalies from normal
- [ ] Success criteria are measurable and achievable
- [ ] Stakeholder reporting expectations are clear
- [ ] Detection gap remediation plan is defined

**Iteration Guidance:**
- If hypotheses too broad: Narrow focus to specific TTPs or attack stages
- If data sources insufficient: Identify alternative telemetry or accept visibility limitations
- If queries return overwhelming volume: Add more filters based on baseline understanding or aggregate before analysis
- If false positives too high: Refine hypotheses with more specific behavioral indicators
- After campaign completion: Document what worked, what didn't, and lessons for next campaign
- If no findings: Consider whether hypotheses were too specific (threat not present) or too vague (everything looks normal)

---
