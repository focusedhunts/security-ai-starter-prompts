# SCENARIO 1: RANSOMWARE ATTACK

**Threat Type:** Ransomware / Extortion / Cryptographic Encryption / Data Exfiltration

**Difficulty Level:** Intermediate

**Duration Suitability:**
- 2-hour (compressed): 8-12 injects, detection → initial response
- 4-hour (standard): 15-20 injects, full IR lifecycle
- Full-day (comprehensive): 25-35 injects, deep investigation + complications

**Why This Matters:**
Ransomware remains the #1 cybersecurity threat globally. Combines technical response (forensics, containment, eradication) with non-technical responses (ransom payment decision, regulatory notification, customer communication, executive pressure). Tests decision-making under extreme business pressure with imperfect information.

---

## Threat Actor Profile

**Motivation:** Financial - extortion, ransom payments, data sale

**Sophistication:** Moderate to Advanced
- Develops custom malware or uses commodity ransomware with customization
- Conducts target reconnaissance (knows valuable assets)
- Maintains operation like business (ransom negotiation, victim tracking, payment processing)

**Operational Model:**
- Identifies targets with valuable data and good backup systems (means to pay)
- Conducts phishing campaigns at scale
- Uses double-extortion (encryption + data publication threat)
- Actively negotiates ransom (may settle for partial payment)
- Maintains victim databases and threat communications

**Geographic Origin:** Often Eastern European, Russia, North Korea (varying capabilities by group)

---

## Detailed Attack Narrative

### Timeline (Attacker Perspective)

**Day 1, Morning:**
- Phishing campaign with malicious attachment (Microsoft Office document with macro)
- Attachment appears legitimate (vendor invoice, resume, document from trusted contact)
- Email bypasses filters (spoofed domain or legitimate sender account)

**Day 1, Midday:**
- User receives email, opens attachment
- Macro executes (depending on Office security settings)
- First-stage payload downloads (lightweight downloader or C2 beacon)
- Establishes persistence (scheduled task, registry run keys, WMI event subscription)
- Communicates with attacker C2 infrastructure

**Day 1-2, Reconnaissance Phase:**
- Attacker (or automated tools) begins network scanning
- Maps network topology, identifies servers and critical systems
- Enumerates user accounts and permissions
- Identifies backup systems and their location
- Assesses security tools and their configuration
- Looks for high-value targets (databases, file servers, financial systems)

**Day 2, Privilege Escalation:**
- Attacker extracts credentials from memory (LSASS dumping)
- Cracks weak passwords or attempts pass-the-hash
- Obtains domain admin credentials or equivalent
- May exploit unpatched systems for privilege escalation

**Day 2-3, Lateral Movement:**
- Uses stolen credentials to move laterally across network
- RDP into servers, uses admin shares, PsExec, or other lateral movement techniques
- Targets critical systems identified during reconnaissance
- Tests access and ensures persistence on key systems

**Day 3, Data Exfiltration:**
- Stages valuable data for exfiltration (copies to central location)
- Exfiltrates data via C2 channel, compromised cloud account, or staged external service
- Confirms data access and quality before encryption
- Maintains copy of data for extortion (double-extortion threat)

**Day 3 Evening, Ransomware Deployment:**
- Triggers coordinated ransomware deployment across organization
- Typically uses Group Policy, scheduled tasks, or direct system execution
- Encryption begins on file servers, workstations, backups if accessible
- Rapid spread designed to maximize impact before containment

**Day 4, Extortion:**
- Ransom note appears on encrypted systems (desktop wallpaper, text files, web browsers)
- Contains payment instructions (cryptocurrency wallet, temporary email)
- Specifies payment deadline (typically 24-72 hours)
- Threatens data publication if payment not received
- May include sample of exfiltrated data as proof

---

## Initial Detection Points

**Most Common:**

1. **EDR Alert** - Suspicious PowerShell, WMI, or command execution detected
2. **Help Desk Calls** - Users reporting files are unreadable or have changed extensions
3. **File Share Unavailability** - System admins notice SMB shares locked or inaccessible
4. **Backup System Alert** - Backup software detects unusual access or deletion attempts

**Less Common But Earlier:**

5. **Network Monitoring** - Unusual C2 traffic or data exfiltration detected
6. **SIEM Alert** - Credential dumping or lateral movement pattern
7. **DLP Alert** - Large data transfer to external location
8. **External Notification** - ISP, security vendor, or partner alerts to suspicious activity

**Late Detection (Most Dangerous):**

9. **Business Impact** - Operations disrupted, services unavailable, revenue loss
10. **Media/External Alert** - Ransom data appears on dark web, media reports compromise
11. **Customer Complaint** - Customer reports inaccessibility or data concerns

---

## Key Technical Elements (MITRE ATT&CK)

| ATT&CK Phase | Techniques | Detection Difficulty |
|--------------|-----------|---------------------|
| **Initial Access** | Phishing: Attachment / Link | Medium - email filters may miss, user behavior determines |
| **Execution** | Windows Script (Macro, PowerShell, WMI) | Low-Medium - EDR/SIEM alerts on suspicious execution |
| **Persistence** | Scheduled Task / Registry Run Key / WMI Event | Medium - requires system enumeration to find |
| **Privilege Escalation** | LSASS Dumping / Credential Theft / Exploitation | Medium-High - requires memory access or exploitation |
| **Defense Evasion** | Disable Security Tools / Obfuscation / Log Deletion | Medium - depends on tool configuration |
| **Credential Access** | OS Credential Dumping / Credential Store Access | Low - multiple evidence sources (EDR, Event Logs, SIEM) |
| **Discovery** | System/Network Enumeration / Software Discovery | High - difficult to detect enumeration in normal environment |
| **Lateral Movement** | Remote Services / Stolen Credentials / Admin Shares | Medium - depends on logging of privileged access |
| **Collection** | Archive Data / Data from Local System | Medium - unusual file access patterns |
| **Exfiltration** | C2 / Cloud Storage / Scheduled Transfer | Medium-High - depends on egress monitoring |
| **Impact** | Service Stop / Inhibit Recovery / Data Encrypted | Very Low - obvious when it happens |

---

## Key Decision Points for Participants

### Decision 1: Containment Approach & Timing

**The Dilemma:** Balance immediate spread-stopping with business continuity

**Options:**

**Option A: Aggressive Immediate Isolation** (Recommended technically)
- Action: Disconnect all potentially affected systems from network immediately
- Pro: Stops spread quickly, prevents further encryption, limits damage
- Con: Major operational disruption, customer/partner impact, potential data loss in progress
- Timeline: Immediate (minutes)
- Facilitator Note: "Network team is asking if they should pull the plug on the file server. It will stop the encryption but will cause customer impact."

**Option B: Selective Containment** (Business compromise)
- Action: Isolate only confirmed affected systems; monitor others closely for spread
- Pro: Minimizes business disruption, allows investigation continuation
- Con: Risk of encryption continuing to spread if scope assessment incomplete
- Timeline: 30 minutes to 1 hour
- Facilitator Note: "We could isolate just the infected file server, but if lateral movement happened, other systems may start encrypting any minute."

**Option C: Monitored Response** (Dangerous)
- Action: Observe closely for 30-60 minutes to understand scope before acting
- Pro: Gather intelligence about attacker behavior, lateral movement patterns
- Con: High risk of massive encryption spread during observation window
- Timeline: 30-60 minutes before forced isolation
- Facilitator Note: "More investigation would help us understand scope, but we risk losing that time to encryption."

**Participant Struggle:** Most participants initially want Option B (business compromise), then realize they don't know scope, leading to either regret or escalation to Option A. Rarely do groups proactively choose A.

**Evaluation Criteria:**
- [ ] Decision made with clear reasoning (not just panic or business pressure)
- [ ] Understands implications of each option
- [ ] Scope determination considered before containment
- [ ] If chose containment, timing is appropriate to likely spread rate

---

### Decision 2: Ransom Payment Decision

**The Dilemma:** Complex decision with ethical, legal, practical, and financial dimensions

**Context to Provide:**
- Ransom demand: $[Amount] in Bitcoin (varies by scenario complexity)
- Deadline: Typically 48-72 hours from ransom note
- Threat: "Data will be published if payment not received"
- Data exfiltrated includes: [Specify PII, trade secrets, patient records, etc.]

**Factors to Consider:**

**Legal Framework:**
- Some regulations prohibit ransom payment (OFAC sanctions, government agencies)
- Some allow but require reporting
- Some silent (no explicit prohibition)

**Insurance:**
- Some cyber insurance policies cover ransom payments
- Some pay only if FBI notified
- Some don't cover if negotiated without insurance knowledge
- Some require "professional negotiation" (can't pay directly)

**Practical Reality:**
- Attacker is criminal enterprise - no guarantee of decryption
- Even if decryption provided, malware may remain
- Payment validates targeting and encourages future attacks
- FBI strongly discourages (but acknowledges business reality)

**FBI Guidance:**
- "Do not pay ransoms"
- But understands organizations may choose to do so
- Requests notification if payment made
- May be able to recover funds in some cases

**Ethical/Reputation:**
- Paying ransoms funds criminal enterprises
- Public disclosure of payment may damage reputation with customers, partners
- Not paying demonstrates principle but accepts data loss/publication

**Facilitator Prompts:**
- "Your CFO is asking 'Can we legally pay?'"
- "Insurance company is on the phone wanting to know if you'll pay. They need to know to budget."
- "FBI is offering to negotiate. Would you use them?"
- "An anonymous darknet forum has the data sample. Media may find it soon. Do you publicly disclose breach?"

**Participant Struggle:** Participants want a "right answer." Reality is complex decision requiring judgment.

**Evaluation Criteria:**
- [ ] Considers legal/regulatory constraints
- [ ] Checks insurance coverage and requirements
- [ ] Discusses (not just decides) ethical implications
- [ ] Coordinates with legal, executive leadership (not security team alone)
- [ ] Considers alternatives (recovery without paying, law enforcement involvement)
- [ ] Documents decision and rationale

---

### Decision 3: Data Breach Notification

**The Dilemma:** Regulatory requirement, timeline pressure, reputation management

**Triggered By:**
- If data was exfiltrated (not just encrypted), regulatory notification required
- Scope: How many individuals' PII/data compromised?
- Severity: What type of data (SSN, payment card, medical records)?

**Regulatory Timelines** (varies by jurisdiction):
- HIPAA: 60 days from discovery
- State laws: 30-90 days (varies)
- GDPR: 72 hours to regulators (if high risk)
- PCI-DSS: 30 days minimum (payment card)

**Notification Parties:**
- Affected individuals (primary requirement)
- State Attorneys General
- Regulators (industry-specific: HIPAA, PCI, etc.)
- Credit bureaus (if SSN compromised)
- Law enforcement (optional but recommended)
- Customers/Public (if material impact)

**Message Development:**
- What data was compromised?
- When did compromise occur?
- When was it discovered?
- What are we doing about it?
- What should affected individuals do (credit monitoring, password change)?
- How can they contact us with questions?

**Cost Implications:**
- Individual notification (printing, postage, staff time)
- Credit monitoring (3 years) for affected individuals
- Regulatory fines (if notification violations)
- Lawyer costs (preparation, review, coordination)
- PR agency costs (reputation management)

**Facilitator Prompts:**
- "Legal says notification deadline is [date]. That's _____ days away. Are we on track?"
- "We need to notify _____ [number] individuals. That costs $[amount] for credit monitoring."
- "State AG is asking why notification took so long."

**Participant Struggle:** Tension between accuracy (ensuring you have right data count) and timeline pressure (regulators won't wait).

**Evaluation Criteria:**
- [ ] Scope of exfiltration determined or estimated with confidence level
- [ ] Regulatory requirements identified
- [ ] Notification timeline established with dates
- [ ] Draft notification message prepared
- [ ] Affected parties (regulators, individuals) identified
- [ ] Costs estimated and approved

---

### Decision 4: Recovery Strategy

**The Dilemma:** Restore vs. Rebuild vs. Negotiate - each with tradeoffs

**Recovery Options:**

**Option A: Restore from Backups** (Fastest IF backups are good)
- Action: Restore systems from pre-infection backups
- Timeline: Hours to days depending on data volume
- Requirement: Backups must be recent, uncorrupted, and isolated from network during encryption
- Risk: If backups compromised too, restoration just restores infection
- Validation needed: Verify clean restore, no persistence, no reinfection
- Facilitator shock: "IT says backups from 48 hours ago are corrupted too. Oldest clean backup is 5 days old."

**Option B: Rebuild from Scratch** (Safest but slowest)
- Action: Rebuild systems from clean gold images, restore data from clean backups
- Timeline: Days to weeks depending on system complexity
- Requirement: Clean system images must exist, must be current
- Advantage: Eliminates any risk of persistence or residual malware
- Disadvantage: Significant business disruption
- Facilitator shock: "We don't have clean gold images. We've been patching servers for 3 years."

**Option C: Negotiate Decryption with Attacker** (NOT RECOMMENDED)
- Action: Pay ransom and hope attacker provides working decryption key
- Risk: No guarantee key works, key may be intercepted, attacker may demand additional payment
- Reality: Criminal enterprise, no contract enforcement
- FBI guidance: Don't do this
- Sometimes only option if backups failed

**Decision Sequencing:**
- [ ] Determine backup status and viability FIRST
- [ ] Assess for remaining malware/persistence BEFORE recovery
- [ ] Validate recovery before bringing systems back online
- [ ] If rebuilding, verify clean gold images exist
- [ ] If negotiating, understand FBI may track cryptocurrency

**Facilitator Prompts:**
- "IT tested backup restoration. It's taking 4 hours per file server. You have 20 file servers. Business needs them back online ASAP. What's your timeline?"
- "Backup restoration worked but EDR is still showing suspicious activity on restored system. Is backup still infected?"
- "Decryption key from attacker only works on 70% of files. What do you do with the remaining 30%?"

**Participant Struggle:** Backup confidence is frequently misplaced (backups aren't tested, aren't current, or were encrypted too).

**Evaluation Criteria:**
- [ ] Backup status and viability assessed BEFORE recovery starts
- [ ] Recovery timeline is realistic based on actual constraints
- [ ] Validation plan includes forensic check for persistence
- [ ] Rebuild approach has access to clean gold images
- [ ] Data restoration prioritization is clear (which systems/data first)
- [ ] Success criteria for recovery defined (how do you know you're "clean"?)

---

### Decision 5: Stakeholder Communication & Leadership Briefing

**The Dilemma:** Executives need clear decisions and timeline; technicians have uncertainty

**Communication Challenge:**
Translating technical complexity into business language executives understand, while maintaining accuracy and acknowledging uncertainty.

**Key Stakeholders & Their Concerns:**

**CEO/Board of Directors:**
- "How bad is this?" (Scope)
- "When will we be back online?" (Timeline)
- "What's the financial impact?" (Costs + revenue loss)
- "What will media say?" (Reputation)
- "Is this going to bankrupt us?" (Existential risk)

**CFO/Finance:**
- "How much will this cost?" (Immediate: remediation, notification, credit monitoring)
- "Is insurance covering this?" (Claim process)
- "Should we pay ransom?" (Cost-benefit analysis)
- "What's the revenue impact of downtime?" (Business continuity costs)

**Customers/Partners:**
- "Is my data safe?" (Reassurance)
- "Will services be restored?" (Timeline)
- "Am I being notified appropriately?" (Transparency)
- "Is my data about to be published?" (Risk assessment)

**Law Enforcement (if involved):**
- "Preserve evidence" (Investigation priority)
- "Don't pay ransom" (FBI guidance)
- "Notify us of developments" (Information sharing)

**Media (if reached):**
- "What happened?" (Facts)
- "When?" (Timeline)
- "Who's responsible?" (Blame/accountability)
- "What's the data impact?" (Newsworthiness)

**Briefing Structure:**

**Opening (1-2 min):**
- Acknowledgment of incident ("We experienced a ransomware attack")
- Current status ("We're in active response")
- Why we're meeting ("Need decisions and alignment on strategy")

**Situation (3-5 min):**
- What happened (attack narrative, not all technical details)
- When detected (timeline from now backward to initial compromise)
- Scope (systems affected, data exfiltrated if known)
- Current status (containment status, immediate actions taken)

**Options & Recommendations (5-10 min):**
- Containment approach (with tradeoffs)
- Recovery timeline and approach
- Communication strategy
- Escalation/decision authority (what needs their approval)

**Q&A (as long as needed):**
- Answer in plain language
- Acknowledge uncertainty where it exists
- Provide confidence levels ("We're confident about X, still determining Y")
- Redirect out-of-scope questions ("Legal team will handle that")

**Facilitator Prompts:**
- "CEO just asked 'Are we back online yet?' You're 4 hours into incident and haven't even finished scope assessment."
- "Board wants to know if they should halt operations completely or continue what they can. What's your recommendation?"
- "Media has the story. PR wants to release statement within 30 minutes. Legal says we don't have enough facts. What do you do?"

**Participant Struggle:** Technical people struggle to translate complexity to non-technical audience. Executive pressure for immediate answers when situation still uncertain.

**Evaluation Criteria:**
- [ ] Executive briefing is clear, concise, avoids jargon
- [ ] Accurately represents technical situation
- [ ] Acknowledges uncertainty where appropriate
- [ ] Provides specific recommendations (not just options)
- [ ] Escalation point is clear (what decision is needed from them)
- [ ] Anticipates likely executive questions

---

## IR Capabilities Tested

This scenario assesses multiple IR competencies:

**Technical IR:**
- [ ] Forensic investigation (initial access determination, timeline reconstruction, scope assessment)
- [ ] Log analysis and correlation (SIEM query development, evidence collection)
- [ ] Malware analysis (understanding attacker TTPs, identifying persistence mechanisms)
- [ ] Containment execution (coordinating technical isolation without business impact)
- [ ] Eradication validation (ensuring no persistence remains post-cleanup)
- [ ] Evidence preservation (capturing artifacts while enabling recovery)

**Business Continuity:**
- [ ] Backup system validation (understanding backup status, recovery process)
- [ ] RTO/RPO assessment (realistic recovery timelines)
- [ ] Communication with IT operations (coordinating technical work)
- [ ] Resource prioritization (which systems first, which data salvageable)

**Decision-Making & Leadership:**
- [ ] Executive briefing (translating technical complexity to business language)
- [ ] Options analysis (understanding tradeoffs, not just picking easy path)
- [ ] Value judgment (ransom payment, legal/ethical considerations)
- [ ] Decision documentation (recording decisions and rationale)

**Coordination & Communication:**
- [ ] Internal communication (keeping team informed, assigning tasks)
- [ ] Cross-functional coordination (IT, Security, Legal, Finance, PR working together)
- [ ] Executive escalation (knowing when to involve senior leadership)
- [ ] External communication (law enforcement, insurance, customers)

**Regulatory & Legal:**
- [ ] Notification requirements (HIPAA, state breach laws, industry-specific)
- [ ] Notification timelines (understanding deadlines)
- [ ] Regulatory coordination (keeping regulators informed if required)
- [ ] Insurance coordination (claim process, coverage questions)

---

## Complexity Factors & Calibration

The core ransomware scenario is straightforward: phishing → lateral movement → encryption. Increase difficulty by adding complications:

### Complications (Select to calibrate difficulty)

**Backup Complications (High impact):**
- [ ] Backups corrupted or encrypted too (attacker deleted backups)
- [ ] Backup retention too old (oldest good backup is 7+ days old, unacceptable data loss)
- [ ] Backup restoration process broken or untested (discovered during incident)
- [ ] RPO/RTO requirements can't be met with available backups
- [ ] Backups in cloud storage that was also compromised

**Scope Expansion (High impact):**
- [ ] Encryption spreads faster than contained (cloud infrastructure, partner systems)
- [ ] Attacker maintains access via backdoor (persistence missed during cleanup)
- [ ] Multiple locations or business units affected
- [ ] Vendor/partner systems also infected (supply chain spread)
- [ ] Manufacturing systems or OT systems affected

**Regulatory Complications (High impact):**
- [ ] Data exfiltrated triggers HIPAA notification (healthcare context)
- [ ] Payment card data compromised (PCI-DSS notification + fines)
- [ ] International data (GDPR 72-hour notification)
- [ ] Multiple state breach laws triggered (varying timelines and requirements)
- [ ] Critical infrastructure (NERC CIP implications)

**Business Pressure (Medium-high impact):**
- [ ] Media inquiry received during incident (reputation pressure)
- [ ] Large customer threatening to terminate contract (revenue pressure)
- [ ] Board demanding hourly updates (executive pressure)
- [ ] Financial deadline/quarter-end processing (business disruption cost)
- [ ] Life-critical services affected (healthcare, 911, utilities)

**Technical Complications (Medium impact):**
- [ ] Decryption key only partially works (some files decrypt, others don't)
- [ ] Lateral movement more extensive than initially believed (scope surprise)
- [ ] EDR/SIEM didn't capture full attack chain (visibility gaps)
- [ ] Malware also disabled backups (additional impact)
- [ ] Attacker negotiation demands increase (extortion escalation)

**Team/Organizational Complications (Medium impact):**
- [ ] Key personnel unavailable during critical decision points
- [ ] IT and Security teams disagree on approach
- [ ] Insurance and Legal have conflicting guidance
- [ ] External IR firm engaged with different recommendations
- [ ] Public/customer communication concerns override security concerns

### Difficulty Levels

**BEGINNER (2-hour):** No complications
- Straightforward phishing → detection → containment → backup restore
- Ransomware stops spreading immediately upon containment
- Backups are recent, accessible, and uncorrupted
- Scope is limited (single location, single department)
- No regulatory notification required
- Executive briefing is supportive, not pressuring

**INTERMEDIATE (4-hour):** 2-3 complications
- + Backup issue (corrupted or slow restore)
- + Scope expansion during investigation
- + Regulatory notification requirement
- Most likely: 4-hour exercise, intermediate skill participants

**ADVANCED (full-day):** 4+ complications
- + Multiple simultaneous issues (backups, scope, regulation, business pressure)
- + Parallel decision threads (ransom vs. recovery vs. negotiation)
- + Conflicting stakeholder demands
- + Persisting threat (backdoor reinfection)
- Advanced facilitation required to manage parallel threads

---

## Customization Opportunities

### Industry-Specific Customization

**Healthcare:**
- Patient care systems affected (urgent treatment disruption)
- HIPAA protected health information (automatic notification requirement)
- Regulatory scrutiny (CMS, state health department)
- Data at stake: Medical records, SSN, insurance information
- Recovery urgency: Critical care systems cannot wait
- Unique decision: Patient safety vs. incident response procedures

**Finance/Banking:**
- Transaction processing systems affected (revenue-critical)
- PCI-DSS implications (payment card data)
- SEC reporting requirements (if publicly traded)
- Data at stake: Customer financial information, account details
- Regulatory scrutiny: Banking regulators, SEC
- Unique decision: Ransom payment may violate OFAC/sanctions

**Retail/E-Commerce:**
- Customer-facing systems affected (revenue-critical)
- Customer PII at stake (credit cards, shipping addresses)
- Peak season considerations (holiday season = maximum impact)
- Data at stake: Customer accounts, purchase history, payment info
- Unique decision: Service restoration vs. data recovery priority

**Manufacturing:**
- Production systems affected (supply chain disruption)
- OT/IT convergence (industrial control systems)
- Supply chain impact (inability to fulfill orders)
- Data at stake: Intellectual property, supply chain information
- Recovery urgency: Production equipment may need reset/recalibration
- Unique decision: Halt production or try to operate partially

**Technology/SaaS:**
- Customer-facing services down (SaaS platform unavailable)
- Reputation damage (service uptime is core business)
- Multi-tenant impact (many customers affected)
- Data at stake: Customer data in database
- Unique decision: Restore entire platform vs. subset of customers
- Regulatory: Depends on customer data sensitivity

### Technical Environment Customization

**Infrastructure Type:**
- Replace generic "file servers" with actual client systems (SAP, Oracle, Salesforce, etc.)
- Reference actual cloud platform if applicable (AWS, Azure, GCP, hybrid)
- Use actual network segment names
- Reference actual backup solution (NetBackup, Commvault, Veeam, etc.)
- Mention actual security tools (EDR: CrowdStrike/Carbon Black, SIEM: Splunk/ELK, etc.)

**Scale Customization:**
- Adjust encryption scope based on environment size
- Adjust recovery timeline based on actual backup infrastructure
- Adjust financial impact based on organization size and data value
- Adjust notification scope based on customer data sensitivity

### Organizational Customization

**Decision Authority:**
- Who actually makes ransomware payment decision? (CFO? CEO? Board?)
- Does insurance company have veto? (Some policies require their approval)
- Does legal have approval rights? (May ban payments due to OFAC)
- Is there established escalation path?

**Team Structure:**
- Who is incident commander? (Security lead? IT lead? Both?)
- How does IT Ops relate to Security team? (Supportive? Adversarial? Absent?)
- Is IR retainer active? (External firm already engaged?)
- Are decision-makers available? (Key executives often traveling or unavailable)

**Culture Factors:**
- Is organization risk-averse or pragmatic? (Affects ransom decision)
- Is there blame culture? (Affects information sharing and transparency)
- Is security prioritized? (Affects IR plan quality and team authority)

---

## Sample Injects (Detailed for Stage 2)

Ransomware scenario injects by exercise phase:

**Detection Phase (Minutes 0-15):**
1. EDR alert or helpdesk call (initial indicator)
2. Scope confirmation ("It's more than one system")
3. Initial assessment ("We need to understand what we're dealing with")

**Investigation Phase (Minutes 15-45):**
4. Backup status check ("Are backups okay?")
5. Forensic findings ("Attacker was in network for _____ days")
6. Lateral movement confirmation ("Multiple systems show encryption")

**Containment Decision (Minutes 45-60):**
7. Executive pressure for immediate answers
8. Ransom note appears ("Demand with deadline")
9. Escalation decision (Need to brief Board/CEO)

**Response Phase (Minutes 60+):**
10. Law enforcement involvement (FBI offers assistance)
11. Insurance coordination (Claim process and coverage questions)
12. Media inquiry (Reputation/PR concerns)
13. Customer concern (Large customer calls)
14. Recovery progress updates (Status briefing requirements)

---

## Common Participant Pitfalls

| Pitfall | Why It Happens | Consequence | Coaching |
|---------|----------------|------------|----------|
| **Scope Underestimation** | Assume isolated system until proven otherwise | Encryption continues spreading while time wasted | Emphasize: Get full scope before any remediation action |
| **Backup Over-Confidence** | Assume backups are current and uncorrupted | Shocked when recovery blocked by backup failure | Say: "Always verify backup status in ransomware incidents" |
| **Ransom Decision Oversimplification** | Treat as simple yes/no instead of complex decision | Business pressure leads to hasty payment without full analysis | Emphasize: Legal, insurance, ethical, practical all matter |
| **Forensics vs. Recovery Trade-off** | Want both perfect forensics AND rapid recovery | Conflict leads to poor decision (do forensics during recovery?) | Say: "Prioritize based on business impact. Forensics can continue post-recovery" |
| **Executive Communication Delays** | Security team tries to have all answers before briefing | Executive finds out from other sources, makes uninformed decisions | Emphasize: Brief early with what you know, update as you learn |
| **Evidence Destruction During Recovery** | Eager to restore systems, accidentally overwrite forensic evidence | Can't prove attack path later, regulatory implications | Say: "Capture forensic artifacts BEFORE recovery actions" |
| **Team Siloing** | Security team acts independently from IT operations | Conflicting actions, IT doesn't know incident happening | Emphasize: IT Ops is critical partner, not adversary |
| **Ignoring Backdoors** | Focus on encryption, miss attacker's persistence mechanism | After cleanup, attacker comes back in via backdoor | Say: "Containment ≠ eradication. Verify all persistence removed" |

---

## Success Indicators - What Effective Response Looks Like

### Technical Indicators

- [ ] Scope determination is systematic (enumerated affected systems, not assumed)
- [ ] Containment is prioritized and executed decisively (not delayed by analysis paralysis)
- [ ] Evidence is captured BEFORE recovery (forensic artifacts preserved)
- [ ] Recovery process is validated (systems are truly clean, no persistence)
- [ ] Backdoors/persistence mechanisms are actively hunted (not missed)

### Business/Decision Indicators

- [ ] Executive team is briefed early and informed throughout (not discovering from media)
- [ ] Legal and insurance are coordinated (no conflicting guidance)
- [ ] Ransom decision (if made) is documented with reasoning (not just by panic)
- [ ] Recovery timeline is realistic based on actual constraints (not optimistic)
- [ ] Communications to customers/public are planned (not reactive)

### Organizational Indicators

- [ ] IT Ops and Security are coordinated (not working at cross-purposes)
- [ ] Incident command is clear (people know who's in charge of what)
- [ ] Decision-making authority is clear (decisions not blocked by unclear approval)
- [ ] Team communication is structured (not ad-hoc chaos)
- [ ] Post-incident actions are planned (lessons learned, preventive measures)

### Regulatory Indicators

- [ ] Notification timeline is calculated (not guessed)
- [ ] Regulatory requirements are identified (HIPAA, state laws, PCI, etc.)
- [ ] Notification process is planned (who notifies whom, message content)
- [ ] Law enforcement coordination is considered (FBI, state AG, etc.)
