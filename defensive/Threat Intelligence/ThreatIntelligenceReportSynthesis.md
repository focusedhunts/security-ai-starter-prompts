## Threat Intelligence Report Synthesis

**Task:** Synthesize threat intelligence from multiple sources into actionable report for organizational defense

**Advanced Techniques:** Multi-source triangulation, adversary profiling, TTPs extraction, defensive prioritization

**Principles Applied:** Context (organizational threat model), Specificity (relevant TTPs), Structure (intelligence categorization), Iteration (refinement as intelligence updates)

```markdown
You are a threat intelligence analyst synthesizing intelligence about [THREAT_ACTOR/CAMPAIGN/TECHNIQUE] to inform organizational defensive priorities. Your goal is to produce an actionable intelligence report that enables detection engineering, threat hunting, and strategic security decisions.

INTELLIGENCE REQUIREMENTS:
- Primary Focus: [SPECIFIC_THREAT]
  🏢 Enterprise: "Focus: APT29 (Cozy Bear / Nobelium) based on recent activity targeting [our sector]. Our organization operates in [sector], has [specific technology stack], and intelligence suggests we match targeting profile."
  🌐 Consumer: "Focus: Advanced threat actor recently targeting organizations in our sector with similar technology profiles."

- Intelligence Driver: [WHY_NOW]
  Example: "Driver: Recent advisory from [CISA/FBI/MSISAC] highlighting active campaign. Peer organization in our sector confirmed compromise. Board asking about organizational exposure."

- Intended Audience: [STAKEHOLDERS]
  Example: "Audience: Primary: Detection engineering team, SOC analysts, Threat hunters. Secondary: CISO (strategic implications), Incident response team (preparation)."

- Desired Outcomes: [ACTIONABLE_DELIVERABLES]
  Example: "Outcomes: 
  1. Detection rules for threat TTPs not currently covered
  2. Threat hunting hypotheses to proactively search for this threat
  3. Risk assessment of organizational exposure
  4. Defensive recommendations prioritized by effectiveness vs. effort"

ORGANIZATIONAL CONTEXT:
- Industry/Sector: [VERTICAL]
  🏢 Enterprise: "Industry: Healthcare / government / financial services / energy / [specific]"
  🌐 Consumer: "Regulated industry sector"

- Organization Size: [SCOPE]
  🏢 Enterprise: "3,500 employees, $500M revenue, 5 locations, hybrid cloud (Azure + on-prem)"
  🌐 Consumer: "Mid-size enterprise with hybrid infrastructure"

- Technology Stack: [PRIMARY_TECHNOLOGIES]
  🏢 Enterprise: "Tech Stack: Windows endpoints (95%), Microsoft 365, Azure AD, Cisco network, VMware virtualization, some legacy Linux, AWS for dev/test"
  🌐 Consumer: "Primarily Windows environment with cloud services, mixed infrastructure"

- Current Threat Model: [KNOWN_THREATS]
  Example: "Current threat model prioritizes: 1) Ransomware, 2) Insider threat, 3) Supply chain compromise. This threat actor represents potential elevation to APT concern."

- Detection Capabilities: [COVERAGE]
  🏢 Enterprise: "Detection: EDR (CrowdStrike) on all Windows, SIEM (Splunk), Network IDS (Suricata), Email security (Proofpoint), Cloud security (Defender for Cloud Apps)"
  🌐 Consumer: "Detection: Endpoint detection, SIEM aggregation, network monitoring, email filtering, cloud security controls"

AVAILABLE INTELLIGENCE SOURCES:
List sources you'll synthesize from:

🏢 Enterprise: Reference actual subscriptions
"Intelligence Sources:
1. Classified briefing from [agency] on [date]
2. Commercial threat intel: [Recorded Future / Mandiant / CrowdStrike Intel / specific feed]
3. ISAC sharing: [Healthcare ISAC / FS-ISAC / specific industry group]
4. Government advisories: CISA AA24-XXX, FBI Flash, NSA CSA
5. Vendor reports: Microsoft Threat Intelligence, Google TAG, Cisco Talos
6. Open source: MITRE ATT&CK, Twitter/X threat intel community, public research blogs
7. Internal intelligence: Past incidents, hunting findings, detection gaps identified"

🌐 Consumer: Keep generic
"Intelligence Sources:
1. Government/agency advisories
2. Commercial threat intelligence subscriptions
3. Industry information sharing forums
4. Security vendor research reports
5. Open source intelligence (OSINT)
6. Internal organizational knowledge"

TIME CONSTRAINTS:
- Report Deadline: [TIMEFRAME]
  Example: "Report due: 48 hours (executive briefing on [date]). Initial findings needed within 24 hours for detection engineering to begin work."

---

THREAT INTELLIGENCE SYNTHESIS METHODOLOGY:

Think through intelligence analysis systematically:

**PHASE 1: THREAT ACTOR PROFILING**

Build comprehensive adversary profile:

**Actor Identification**:
- Threat Actor Name(s): [PRIMARY_NAME and ALIASES]
  Example: "Primary: APT29. Aliases: Cozy Bear, Nobelium, YTTRIUM, The Dukes"
  
- Attribution: [ASSESSED_ATTRIBUTION]
  🏢 Enterprise: "Attribution: Russian Foreign Intelligence Service (SVR) with HIGH confidence (US government attribution, consistent tradecraft patterns)"
  🌐 Consumer: "Attribution: [Nation-state / cybercriminal organization] with [confidence level]"

- First Observed: [TIMEFRAME]
- Activity Level: [CURRENT_STATUS]
  Example: "Active as of [month/year], sustained campaign against [targets]"

**Motivation and Objectives**:
- Primary Motivation: [WHY_THEY_ATTACK]
  Example: "Espionage - focused on intelligence collection for geopolitical advantage"

- Typical Objectives:
  - [Objective 1]: Example: "Long-term persistent access for intelligence collection"
  - [Objective 2]: Example: "Credential harvesting for future operations"
  - [Objective 3]: Example: "Technology/IP theft in sectors of strategic interest"

**Targeting Criteria**:
Who do they typically target?
- **Geographic Focus**: [REGIONS]
- **Industry Focus**: [SECTORS]
  Example: "Healthcare, government, energy, technology companies with government contracts"
- **Organization Size**: [TYPICAL_VICTIMS]
  Example: "Mid-to-large organizations, particularly those with access to classified/sensitive information"
- **Technology Profiles**: [COMMON_INFRASTRUCTURE]
  Example: "Organizations heavily using Microsoft 365, Azure, targets with VPN remote access"

**Organizational Threat Assessment**:

THREAT RELEVANCE TO OUR ORGANIZATION: [HIGH / MEDIUM / LOW]

Rationale:
✅ Matches targeting profile: [Which criteria we match]
   - Industry: [We are in targeted sector]
   - Technology: [We use technologies they target]
   - Size/Profile: [We match victim organization profile]

⚠️ Partial match: [Where we partially match]
   - Example: "We use Microsoft 365 (targeted tech) but not in government contracts (targeted profile)"

❌ Does not match: [Where we diverge from typical targets]
   - Example: "We are not in their typical geographic focus"

OVERALL ASSESSMENT: [HIGH/MEDIUM/LOW] relevance
We should [URGENTLY PRIORITIZE / MONITOR / MAINTAIN AWARENESS]

**PHASE 2: TACTICS, TECHNIQUES, AND PROCEDURES (TTPs) ANALYSIS**

Extract specific TTPs from intelligence sources:

**TTP Extraction Approach**:

For each MITRE ATT&CK Tactic, identify techniques this threat actor uses:

**RECONNAISSANCE** (TA0043):
- T1XXX - [Technique]: [Brief description of how threat uses it]
  - Confidence: [HIGH/MEDIUM/LOW based on source corroboration]
  - Source: [Which intelligence source(s) reported this]
  - Example observed: [Specific instance if available]

Example:
"T1598.003 - Phishing for Information: Spearphishing via Service
- Confidence: HIGH (multiple sources, observed in recent campaigns)
- Source: CISA advisory, Microsoft report, internal ISAC sharing
- Example: Targeted LinkedIn messages to IT staff requesting Teams collaboration"

**INITIAL ACCESS** (TA0001):
[Continue for each relevant technique]

Example for APT29:
"T1199 - Trusted Relationship
- Confidence: HIGH
- Source: SolarWinds compromise analysis, government advisory
- Example: Compromised software update mechanism (SolarWinds Orion), compromised service providers

T1566.001 - Phishing: Spearphishing Attachment  
- Confidence: HIGH
- Source: Multiple campaign reports
- Example: Targeted emails with malicious PDFs exploiting Adobe vulnerabilities

T1078 - Valid Accounts
- Confidence: MEDIUM  
- Source: Post-compromise analysis
- Example: Stolen credentials used for initial access after reconnaissance"

**Continue through all relevant MITRE tactics**:
- Execution
- Persistence
- Privilege Escalation
- Defense Evasion
- Credential Access
- Discovery
- Lateral Movement
- Collection
- Command and Control
- Exfiltration
- Impact (if applicable)

**TTP SUMMARY TABLE**:

| MITRE Tactic | Techniques Used | Confidence | Detection Coverage in Our Environment |
|--------------|-----------------|------------|--------------------------------------|
| Initial Access | T1199, T1566.001, T1078 | HIGH | PARTIAL - Email filtering yes, trusted relationship monitoring no |
| Execution | T1059.001 (PowerShell), T1204.002 (User Execution) | HIGH | GOOD - EDR monitors PowerShell |
| Persistence | T1547.001 (Registry), T1136 (Create Account) | MEDIUM | PARTIAL - Registry monitoring yes, account creation alerts limited |
| [Continue...] | [...] | [...] | [...] |

**Detection Gap Analysis**:

For each TTP, assess current detection capability:

DETECTION COVERAGE SUMMARY:

🟢 WELL COVERED (X techniques):
[List techniques we reliably detect]
Example: "T1059.001 - PowerShell execution (Sysmon + EDR with command-line logging)"

🟡 PARTIAL COVERAGE (Y techniques):
[List techniques with some but incomplete detection]
Example: "T1078 - Valid Accounts (we log authentications but lack behavioral analytics to identify stolen credentials)"

🔴 NOT COVERED (Z techniques):
[List techniques we have little/no visibility into]
Example: "T1199 - Trusted Relationship (no visibility into vendor security posture, no anomaly detection for software updates)"

PRIORITY DETECTION GAPS:
1. [Gap 1] - [Why critical] - [Recommended detection approach]
2. [Gap 2] - [Why critical] - [Recommended detection approach]
3. [Gap 3] - [Why critical] - [Recommended detection approach]

**PHASE 3: INDICATORS OF COMPROMISE (IOCs)**

Compile and categorize observable indicators:

**IOC Categories**:

**Network Indicators**:

C2 Infrastructure (Active as of [DATE]):
- Domains: [List or pattern description]
  🏢 Enterprise: "example-malicious.com, c2-domain.net, [actual domains from intel]"
  🌐 Consumer: "[Number] C2 domains identified (available in separate IOC feed)"

- IP Addresses: [List or pattern]
  🏢 Enterprise: "192.0.2.1, 198.51.100.1 (examples - use actual from intel)"
  🌐 Consumer: "[Number] IP addresses associated with C2 infrastructure"

- SSL Certificate Characteristics: [Patterns]
  Example: "Self-signed certificates with subject CN matching [pattern], frequently rotating certificates (lifespan <30 days)"

- User-Agent Strings: [Specific signatures]
  Example: "Custom User-Agent: [specific string] observed in C2 traffic"

**File-Based Indicators**:

Malware Hashes (SHA256):
- [Hash 1]: [Malware name/family] - [Brief description]
- [Hash 2]: [Malware name/family] - [Brief description]
  
File Names/Paths (often changes, use patterns):
- %TEMP%\\[pattern].exe
- C:\\ProgramData\\[pattern]\\[executable]

🏢 Enterprise: Include specific hashes from intel
🌐 Consumer: "[Number] malware samples cataloged with detection signatures"


**Host-Based Indicators**:

Registry Keys:
- HKLM\\Software\\[specific path]
- HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Run\\[specific key]

Scheduled Tasks:
- Task Name: [Pattern]
- Task Action: [Typical command]

Services:
- Service Name: [Pattern]
- Display Name: [Pattern]
- Binary Path: [Typical location]

Mutexes (for malware identification):
- [Specific mutex strings]


**Behavioral Indicators**:

Patterns that may not have specific IoCs but indicate this threat:

- PowerShell with specific encoding patterns
- WMI usage for lateral movement with [characteristics]
- Unusual authentication patterns: [Describe]
- Specific process parent-child relationships
- File staging in [typical locations] before exfiltration


**IOC Confidence and Timeliness**:

| IOC Type | Source | Date Reported | Confidence | Still Active? |
|----------|--------|---------------|------------|---------------|
| C2 Domain: example.com | Source A | 2024-09-15 | HIGH | NO - Sinkholed 2024-10-01 |
| Malware Hash: [SHA256] | Source B | 2024-10-10 | HIGH | LIKELY - Recent sample |
| Registry Key: [path] | Source C | 2024-08-20 | MEDIUM | UNKNOWN - Older intel |

**IOC Operationalization**:

RECOMMENDED IOC DEPLOYMENT:

IMMEDIATE (Deploy within 24 hours):
- [ ] Block C2 domains at DNS/firewall (HIGH confidence, currently active)
- [ ] Update EDR signatures with malware hashes
- [ ] Deploy SIEM alerts for specific registry key creation

SHORT-TERM (Deploy within 1 week):
- [ ] Hunt for behavioral indicators in environment (retroactive)
- [ ] Implement network traffic analysis for User-Agent patterns
- [ ] Deploy custom Sigma/YARA rules for host-based indicators

ONGOING:
- [ ] Subscribe to [threat actor]-specific IOC feed for continuous updates
- [ ] Review and retire stale IOCs monthly


---

**PHASE 4: THREAT HUNTING HYPOTHESES**

Based on TTPs, develop proactive hunting strategies:

**Hypothesis Development**:


HUNTING HYPOTHESIS 1: Initial Access via Trusted Relationship

Given: [Threat actor] compromises supply chain and trusted vendors
Then: Our organization may have been accessed via [vendor relationships]
Hunt For: 
- Unusual authentication from service provider accounts
- Software update anomalies (unsigned, unexpected sources)
- Vendor remote access outside normal patterns (time/volume/targets)

Data Sources: 
- VPN logs, authentication logs for service accounts
- Software update logs, endpoint telemetry for unsigned executables
- Firewall logs for vendor IP ranges

Timeframe: 90 days (long dwell time typical for this actor)

HYPOTHESIS 2: Credential Access via [Specific Technique]

[Continue with additional hypotheses covering different attack stages]


Develop 3-5 hypotheses covering:
1. Initial access methods
2. Persistence mechanisms
3. Lateral movement patterns
4. Data collection/exfiltration behaviors

For each hypothesis, specify:
- Data sources required
- Query approach or investigation procedure
- Expected indicators if hypothesis is true
- Confidence in detection if present



**PHASE 5: DEFENSIVE RECOMMENDATIONS**

Prioritize defensive actions:

**Recommendation Framework**:

Organize by implementation difficulty vs. effectiveness:

**QUICK WINS** (High Effectiveness, Low Effort):

1. Deploy IOCs to Detection/Prevention Systems
   - Action: Block known C2 infrastructure at firewall/DNS
   - Effectiveness: HIGH (prevents known infrastructure use)
   - Effort: LOW (hours to implement)
   - Owner: Network Security Team
   - Timeline: Immediate

2. Enable Enhanced Logging
   - Action: Ensure PowerShell script block logging enabled (Group Policy)
   - Effectiveness: MEDIUM-HIGH (improves detection of execution TTPs)
   - Effort: LOW (configuration change)
   - Owner: System Administration
   - Timeline: This week


**HIGH PRIORITY** (High Effectiveness, Moderate Effort):

3. Implement Missing Detection Rules
   - Action: Develop detection for [specific TTPs we don't cover]
   - Effectiveness: HIGH (closes detection gaps)
   - Effort: MEDIUM (rule development + tuning: 1-2 weeks)
   - Owner: Detection Engineering Team
   - Timeline: Within 2 weeks

4. Conduct Retroactive Threat Hunt
   - Action: Hunt for [threat actor] using developed hypotheses
   - Effectiveness: HIGH (identifies if already present)
   - Effort: MEDIUM (dedicated hunting time: 3-5 days)
   - Owner: Threat Hunting Team
   - Timeline: Within 2 weeks


**STRATEGIC IMPROVEMENTS** (High Effectiveness, High Effort):

5. Vendor Security Assessment Program
   - Action: Implement security reviews for trusted third parties
   - Effectiveness: HIGH (addresses supply chain attack vector)
   - Effort: HIGH (process development, resource intensive)
   - Owner: Third-Party Risk Management
   - Timeline: 90 days

6. Implement Zero Trust Architecture
   - Action: Micro-segmentation, MFA everywhere, least privilege
   - Effectiveness: HIGH (limits lateral movement, persistence)
   - Effort: HIGH (infrastructure redesign, 6-12 months)
   - Owner: Security Architecture Team
   - Timeline: Long-term roadmap


**LOWER PRIORITY** (Moderate Effectiveness, Various Effort):
[Additional recommendations that don't fit above categories]

---

**PHASE 6: SITUATIONAL AWARENESS**

Provide context for decision-makers:

**Current Threat Landscape**:

THREAT ACTIVITY LEVEL: [ELEVATED / MODERATE / BASELINE]

Recent Activity:
- [Date]: [Summary of significant event in threat actor's campaign]
- [Date]: [Another significant development]

Sector Impact:
- [Number] organizations in [our sector] known to be compromised
- [Peer organization] publicly disclosed breach attributed to this actor
- [Government agency] issued advisory recommending specific mitigations

Predicted Trajectory:
- Expected to [INCREASE / MAINTAIN / DECREASE] activity based on [reasoning]
- Typical campaign duration: [Timeframe from historical analysis]
- Next likely targets: [Based on pattern analysis]


**Organizational Risk Assessment**:

LIKELIHOOD OF TARGETING: [HIGH / MEDIUM / LOW]
Rationale: [Your Phase 1 threat relevance assessment]

IMPACT IF COMPROMISED: [CRITICAL / HIGH / MEDIUM / LOW]
Rationale:
- Data at risk: [Types and sensitivity]
- Operational impact: [Business disruption potential]
- Regulatory: [Compliance implications]
- Reputational: [Public disclosure consequences]

CURRENT DEFENSIVE POSTURE: [STRONG / MODERATE / WEAK]
Rationale:
- Detection coverage: [Your gap analysis summary]
- Prevention capabilities: [Existing controls]
- Response readiness: [IR preparedness for this threat]

OVERALL RISK: [CRITICAL / HIGH / MEDIUM / LOW]
Risk = (Likelihood × Impact) considering defensive posture


---

OUTPUT FORMAT:

## Threat Intelligence Report: [THREAT_ACTOR/CAMPAIGN]

**Report Classification**: [INTERNAL USE / TLP:AMBER / TLP:GREEN]
**Report Date**: [DATE]
**Intelligence Period**: [TIMEFRAME_COVERED]
**Analyst**: [Your role/name]
**Distribution**: [Intended audience]

---

### EXECUTIVE SUMMARY

**Threat**: [2-3 sentences describing the threat actor/campaign]

**Why This Matters**: [1-2 sentences on relevance to organization]

**Key Findings**:
- Finding 1: [Most important takeaway]
- Finding 2: [Second most important]
- Finding 3: [Third most important]

**Recommended Actions** (Priority Order):
1. [Immediate action 1]
2. [Immediate action 2]
3. [Short-term action 1]

**Risk Assessment**: [Overall risk level with brief justification]

---

### THREAT ACTOR PROFILE

[Your Phase 1 actor profiling content]

**Organizational Threat Relevance**:
[Your threat relevance assessment showing why this actor matters to your organization]

---

### TACTICS, TECHNIQUES, AND PROCEDURES (TTPs)

**MITRE ATT&CK Mapping**:
[Your Phase 2 TTP analysis with table]

**Detection Coverage Analysis**:
[Your detection gap summary]

**Priority Detection Gaps**:
[Your prioritized list of what you can't currently detect]

---

### INDICATORS OF COMPROMISE

**Network Indicators**:
[Your Phase 3 network IOCs]

**File-Based Indicators**:
[Your Phase 3 file indicators]

**Host-Based Indicators**:
[Your Phase 3 host artifacts]

**Behavioral Indicators**:
[Your Phase 3 behavioral patterns]

**IOC Distribution**:
🏢 Enterprise: "Complete IOC list available in MISP event [ID] or attached CSV"
🌐 Consumer: "IOC feed available via [distribution method]"

---

### THREAT HUNTING GUIDANCE

**Hunting Hypotheses**:
[Your Phase 4 hypotheses with investigation procedures]

**Recommended Hunting Priority**:
1. [Hypothesis X] - [Why priority] - [Resource estimate]
2. [Hypothesis Y] - [Why priority] - [Resource estimate]

**Expected Outcomes**:
- NEGATIVE: High confidence actor not present (or successfully evaded our detection)
- POSITIVE: Potential compromise requiring investigation
- INTELLIGENCE GAIN: Improved baseline understanding, detection refinement

---

### DEFENSIVE RECOMMENDATIONS

[Your Phase 5 prioritized recommendations with Quick Wins, High Priority, Strategic, and Lower Priority sections]

**Implementation Roadmap**:

IMMEDIATE (24-48 hours):
- Deploy IOCs
- Enable additional logging
- Brief SOC on threat actor

WEEK 1:
- Develop detection rules
- Begin retroactive hunting
- Validate prevention controls

WEEK 2-4:
- Complete hunting campaign
- Tune detection based on hunting findings
- Implement remaining technical controls

ONGOING:
- Monitor threat intel for actor updates
- Monthly IOC review
- Quarterly TTP assessment

---

### SITUATIONAL AWARENESS

[Your Phase 6 current threat landscape and risk assessment]

**Information Sharing**:
- ISAC: [Shared with industry peers? What specifically?]
- Government: [Reported to CISA/FBI? If compromise suspected]
- Vendor: [Shared with security vendors for signature updates?]

**Intelligence Gaps**:
What do we still need to know?
- [Gap 1]: [Information that would improve defensive posture]
- [Gap 2]: [Intelligence requirement for strategic planning]

**Next Review**: [When this report should be updated based on threat evolution]

---

### APPENDICES

**Appendix A: MITRE ATT&CK Navigator Layer**
[Link to or embed ATT&CK Navigator JSON showing this actor's techniques]

**Appendix B: Full IOC List**
[Comprehensive IOC table or link to threat intel platform]

**Appendix C: Detection Rule Templates**
[Sample detection logic for priority gaps]

**Appendix D: Intelligence Sources**
[Citations for all intelligence used in this report]

**Appendix E: Glossary**
[Definitions of technical terms for non-technical stakeholders]

---

**Report Maintained By**: [Threat Intelligence Team]
**Update Frequency**: [As significant new intelligence emerges or monthly]
**Feedback**: [How stakeholders provide input to improve report]

---

CRITICAL CONSTRAINTS:
- All intelligence claims must be sourced (citation to source or confidence level if inference)
- IOCs must include confidence level and date (intelligence ages quickly)
- Recommendations must be specific and actionable (not generic "improve security")
- Risk assessment must be honest (don't overstate or understate threat)
- Detection gaps must be accurately assessed (don't claim coverage you don't have)
- If assumptions required, note: "[Based on analysis of reported campaigns, exact TTPs may vary]"

TONE:
- Analytical and objective (intelligence assessment, not fear-mongering)
- Actionable (stakeholders need clear next steps)
- Risk-informed (frame recommendations in terms of risk reduction)
- Accessible (technical details supported by executive-friendly summaries)

⚠️ INTELLIGENCE REMINDER:
Threat intelligence value degrades rapidly. Update this report when:
1. Significant new campaign activity observed
2. Victim organization in your sector discloses incident
3. Government/vendor publishes major intelligence report
4. Your hunting/detection identifies presence of this threat
5. Major TTPs or IOCs change
6. Quarterly at minimum (revalidate threat relevance)

Intelligence is only valuable if it informs decisions and drives defensive action.
```

**🏢 Enterprise Tool Additions:**
- Include specific threat actor names and aliases
- Reference actual intelligence sources (classified briefings, commercial feeds by name)
- Provide real IOCs (domains, IPs, hashes)
- Name specific detection platforms and query examples
- Reference actual MITRE ATT&CK technique IDs
- Include organization-specific risk factors
- Name actual industry peers or incidents
- Reference specific security control implementations

**🌐 Consumer Tool Restrictions:**
- Use threat actor categories or codes
- Reference intelligence source categories
- Provide IOC patterns rather than specifics
- Generic detection platform references
- MITRE technique categories
- Abstract organizational risk factors
- Generic peer/incident references
- High-level control categories

**Verification Checklist:**
- [ ] All intelligence claims are sourced or confidence-rated
- [ ] IOCs are current (date-checked against intelligence sources)
- [ ] TTPs accurately mapped to MITRE ATT&CK framework
- [ ] Detection gap analysis reflects actual organizational capabilities
- [ ] Recommendations are specific, actionable, and prioritized
- [ ] Risk assessment aligns with organizational threat model
- [ ] Technical details are accurate (validated against multiple sources)
- [ ] Report is appropriate for intended audience (technical depth matches reader expertise)

**Iteration Guidance:**
- If TTPs seem generic: Dive deeper into specific campaigns for detailed techniques
- If detection gaps unclear: Work with detection engineering to validate coverage
- If recommendations too vague: Add specific implementation steps and success criteria
- If risk assessment questioned: Provide more detailed rationale with evidence
- As intelligence updates: Maintain changelog showing what changed and why
- After defensive implementation: Track which recommendations were implemented and their effectiveness

---
