## SOC Alert Triage & Prioritization

**Task:** Systematically triage high-volume alert queue to identify critical threats requiring immediate investigation

**Advanced Techniques:** Decision tree logic, risk-based prioritization matrix, pattern recognition across alert metadata

**Principles Applied:** Context (environment baseline + threat model), Specificity (triage criteria), Structure (systematic evaluation), Iteration (refinement based on false positive patterns)

```markdown
You are a SOC analyst conducting alert triage during [SHIFT] with [NUMBER] unreviewed alerts in queue. Your goal is to identify the [TOP_N] alerts requiring immediate investigation while safely deferring or closing low-priority items, enabling efficient use of limited analyst time during [TIME_SENSITIVE_PERIOD].

ORGANIZATIONAL CONTEXT:
- Industry: [SECTOR] with [REGULATORY_ENVIRONMENT]
  🏢 Enterprise: "Healthcare provider (HIPAA obligations), 24/7 clinical operations, cannot tolerate extended system downtime"
  🌐 Consumer: "Healthcare sector with regulatory obligations and continuous operations requirements"

- Environment Size: [SCOPE]
  🏢 Enterprise: "2,500 endpoints, 150 servers, 3 data centers, hybrid cloud (AWS + on-premises)"
  🌐 Consumer: "Mid-size enterprise environment with hybrid infrastructure"

- Alert Volume Baseline: [NORMAL_RATE]
  Example: "Typical night shift: 200-300 alerts. Current queue: 847 alerts due to emergency patching cycle"

- Security Maturity: [LEVEL]
  Example: "Mature detection program with documented playbooks, but limited automation. 3-person SOC covering 24/7."

THREAT MODEL:
What threats are most relevant to your organization?
🏢 Enterprise: Be specific:
"Primary threats: Ransomware (healthcare sector targeted by [specific groups]), Insider threat (privileged access to PHI), Supply chain (medical device vulnerabilities). Recent intel: [Threat group] actively exploiting [CVE] in our sector."

🌐 Consumer: Keep abstract:
"Primary threats: Ransomware targeting our industry, insider risk, supply chain vulnerabilities. Recent sector-specific threat activity observed."

CURRENT OPERATIONAL CONTEXT:
- Shift: [TIME_PERIOD] (e.g., "Night shift: 11pm-7am EST, reduced staffing")
- Team Capacity: [AVAILABLE_ANALYSTS]
- Known System Changes: [RECENT_ACTIVITY]
  🏢 Enterprise: "Emergency patching completed 6 hours ago (CVE-2024-XXXXX). Expect authentication noise from reboots. Marketing campaign launched today (expect traffic spike to web properties)."
  🌐 Consumer: "Recent emergency maintenance window. Legitimate business activity creating baseline deviation."

- Critical Systems/Events: [PRIORITIES]
  Example: "Payroll processing begins 5am. Patient records system must remain operational. Executive travel to [region] this week (watch for targeted phishing)."

ALERT QUEUE OVERVIEW:
Provide summary of current alert types and volumes:

| Alert Type | Count | Source | Typical Priority |
|------------|-------|--------|------------------|
| Failed Authentication | 312 | AD/Okta | Low-Med |
| Suspicious Network Traffic | 156 | Firewall/IDS | Med-High |
| Malware Detection | 89 | EDR | High-Critical |
| DLP Violations | 74 | DLP System | Med |
| Vulnerability Scanner Findings | 203 | Nessus | Low-Med |
| Anomalous User Behavior | 13 | UEBA | Med-High |

🏢 Enterprise: Include specific tool names in "Source" column
🌐 Consumer: Use generic tool categories

---

TRIAGE METHODOLOGY:

Think through alert prioritization systematically using this decision framework:

**STEP 1: IMMEDIATE ESCALATION CRITERIA (Stop and Investigate Now)**

Identify alerts matching ANY of these critical patterns:
- Known malicious indicators: [How you define this]
  Example: "Alert contains IoC from [threat intel feed] published <48 hours, OR IoC associated with active campaign against our sector"

- Confirmed exploitation: [Your criteria]
  Example: "EDR/IDS shows successful execution of exploit code, OR alert on internet-facing asset with known vulnerable version"

- Critical asset involvement: [Define critical assets]
  🏢 Enterprise: "Domain controllers (DC01, DC02), patient records database (PHRDB-PROD), payment processing (PAYSVR-01)"
  🌐 Consumer: "Authentication infrastructure, sensitive data repositories, financial systems"

- Privileged account activity: [Scope]
  Example: "Domain admin, service accounts with elevated privileges, OR any admin activity from [non-standard location/time]"

- Data exfiltration indicators: [Signals]
  Example: "Large outbound transfers [>threshold], connections to file-sharing sites, OR encryption of file shares"

**STEP 2: HIGH PRIORITY CRITERIA (Investigate After Critical)**

Alerts matching MULTIPLE indicators:
- Unusual but not confirmed malicious
- Involves sensitive (but not critical) systems
- Moderate risk indicators (failed logins + unusual source, etc.)
- Aligns with recent threat intelligence but not confirmed IoC

**STEP 3: DEFERRED/LOW PRIORITY CRITERIA**

Alerts matching patterns that can wait:
- Known false positive patterns: [Document these]
  🏢 Enterprise: "Failed auth from VPN pool during patching window, Vulnerability scan findings for [specific non-exploitable CVE], DLP alerts on [approved business process]"
  🌐 Consumer: "Authentication failures during maintenance, scanner findings for accepted risks, policy violations from approved workflows"

- Informational alerts with no threat indication
- Vulnerability findings with no exploit available + not internet-facing
- Policy violations with business justification

**STEP 4: CONTEXT ENRICHMENT (For Borderline Cases)**

For alerts that don't clearly fit above categories, enrich with:
- User role/department: [Does this match expected behavior?]
- Asset criticality: [What's the business impact if compromised?]
- Time context: [During business hours? Maintenance window?]
- Recent activity: [Has this user/system behaved unusually before?]
- Threat intelligence: [Any recent campaigns using similar TTPs?]

---

TRIAGE OUTPUT REQUIREMENTS:

Produce a structured triage assessment with THREE priority tiers:

## **TIER 1: IMMEDIATE INVESTIGATION REQUIRED** (Target: Top [N] alerts)

For each alert, provide:

**Alert ID**: [Reference from your SIEM/queue]
**Alert Type**: [Category]
**Asset Involved**: [Sanitized identifier]
🏢 Enterprise: "HOSTNAME: FILESRV-03 (File server hosting [department] data)"
🌐 Consumer: "Asset Type: File server hosting sensitive data"

**Criticality Rationale**: (2-3 sentences)
Explain WHY this requires immediate attention using your decision framework:
- What critical criterion does it match?
- What's the potential impact?
- What makes this time-sensitive?

Example: "EDR detected execution of PowerShell Empire stager on FILESRV-03. This server hosts [sensitive data type]. Execution timestamp: 02:34 UTC (outside business hours). This matches IMMEDIATE ESCALATION criteria: confirmed exploitation attempt + critical asset + suspicious timing."

**Recommended Action**: [Specific next step]
Example: "Isolate system from network (coordinate with [team]), pull memory dump, review process tree, check for lateral movement indicators from this host"

**Investigation Playbook**: [Reference if available]
Example: "Follow: [Playbook-014-Malware-Investigation]"

---

## **TIER 2: HIGH PRIORITY - INVESTIGATE NEXT** (Next [N] alerts)

[Same structure as Tier 1, but with rationale explaining why not Tier 1]

Example Rationale: "Multiple failed authentication attempts from [location] for [user account]. Doesn't match IMMEDIATE criteria (not privileged account, no successful login), but unusual pattern (50+ attempts in 10 minutes) and user recently targeted in phishing campaign (context from Ticket #12345)."

---

## **TIER 3: DEFERRED/LOW PRIORITY** (Can wait until [timeframe])

Provide summary categories rather than individual alerts:

**Category**: [Alert pattern]
**Count**: [Number of similar alerts]
**Deferral Rationale**: [Why these can wait]
**Recommended Handling**: [Batch investigation approach or auto-closure criteria]

Example:
"Category: Failed VPN authentication from [IP_RANGE]
Count: 187 alerts
Deferral Rationale: Known false positive pattern during patching window (users re-authenticating after system reboots). Source IPs match [approved VPN pool]. No successful authentications from suspicious sources.
Recommended Handling: Bulk acknowledge with note: 'Post-patch authentication noise - expected behavior per Change #2024-1234'"

---

## **PATTERN ANALYSIS ACROSS QUEUE**

After triaging individual alerts, identify patterns:

**Correlated Activity**: Are multiple alerts potentially related?
Example: "17 alerts involve [asset group/user/network segment] - potential coordinated activity or single incident creating multiple alerts?"

**False Positive Trends**: What's creating noise?
Example: "203 vulnerability alerts from scanner. 87% are [specific CVE] marked as accepted risk per Ticket #9876. Recommendation: Tune scanner to exclude accepted risks."

**Missing Context**: What information would improve future triage?
Example: "Cannot determine criticality of [alert type] without [missing data field]. Recommendation: Configure [tool] to include [field] in alert metadata."

**Resource Allocation**: Based on triage, how should team prioritize?
Example: "Tier 1: 8 alerts requiring ~4 hours investigation (2 analysts). Tier 2: 23 alerts requiring ~8 hours (batch process similar alerts). Tier 3: 816 alerts deferrable to day shift with context documentation."

---

CONSTRAINTS:
- Base prioritization only on information provided (don't assume context not given)
- If criticality cannot be determined, note: "[Requires additional context: X]"
- Don't recommend actions beyond stated team capabilities
- If alert patterns suggest tool tuning needed, note this separately from triage decisions

TONE:
- Operationally focused (analyst needs clear actions)
- Risk-based reasoning (explain WHY priority assigned)
- Time-conscious (acknowledge shift constraints)
- Systematic (consistent application of criteria)

⚠️ VERIFICATION REMINDER:
This triage assessment informs investigation priorities but doesn't replace investigation. Tier assignments are based on available alert metadata; actual investigation may reveal different severity. Document your triage rationale for shift handoff and playbook refinement.
```

**🏢 Enterprise Tool Additions:**
- Include specific SIEM/EDR/IDS product names (Splunk, CrowdStrike, Palo Alto, etc.)
- Reference actual hostnames, IP ranges (sanitized appropriately for your risk tolerance)
- Name specific threat intelligence feeds you subscribe to
- Reference actual playbook numbers and ticketing system references
- Include specific user roles, departments, or asset classifications
- Mention actual shift schedules and team member count

**🌐 Consumer Tool Restrictions:**
- Use tool categories only ("SIEM", "EDR", "Network IDS")
- Use generic asset identifiers ("File server", "Web application server")
- Reference "threat intelligence sources" without naming feeds
- Use generic "Playbook-[category]" references
- Abstract organizational details to general descriptions
- Keep team structure generic

**Verification Checklist:**
- [ ] Tier 1 alerts genuinely meet stated IMMEDIATE criteria (no false escalation)
- [ ] Tier 3 deferrals have legitimate rationale (not hiding real threats)
- [ ] Recommended actions are within stated team capabilities
- [ ] Asset criticality assessments match organizational priorities
- [ ] Pattern analysis identifies actual correlations (not coincidence)
- [ ] False positive identification is supported by evidence
- [ ] Triage rationale is documented for shift handoff
- [ ] No sensitive security data exposed in assessment

**Iteration Guidance:**
- If tiers seem misaligned: Clarify your immediate escalation criteria more explicitly
- If too many Tier 1 alerts: Tighten critical criteria or provide more baseline context to eliminate false positives
- If missing critical alerts: Provide more detail about your threat model and recent intelligence
- If rationale unclear: Add examples of past incidents that matched similar patterns
- If actions not specific enough: Provide more detail about available response playbooks and team capabilities
- After using in production: Document patterns that consistently appear in wrong tier for prompt refinement

---
