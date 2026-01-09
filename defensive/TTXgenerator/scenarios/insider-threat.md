# Insider Threat Scenario - Malicious Employee

**Difficulty Level:** Advanced
**Recommended Duration:** 4-hour or Full-day exercise
**Industry Applicability:** Technology, Manufacturing, Finance, Healthcare
**Scenario Type:** Insider threat with data exfiltration and backdoor persistence

---

## Executive Summary

This scenario simulates a departing employee who has exfiltrated intellectual property and created persistent backdoors in critical systems before officially leaving the company. Unlike external attacks, insider threats require investigation into employee actions, coordination with HR and Legal, management of internal relationships, and careful evidence handling.

The scenario tests:
- **Digital forensics and timeline reconstruction**
- **HR/Legal/Security coordination**
- **Covert investigation techniques**
- **Evidence preservation and chain of custody**
- **Communication and containment of sensitive information**
- **Employment law considerations (wrongful termination risks)**

---

## Threat Actor Profile

### The Insider

**Name:** [Regional identity if using, or generic "departing employee"]
**Role:** [Senior Engineer / Architect / DBA / Access control similar to Ransomware, but focused on data/access]
**Tenure:** 7+ years at company
**Motivation:**
- Primary: Financial gain (selling IP to competitors, freelance work)
- Secondary: Revenge (recent negative performance review, denied promotion)
- Tertiary: Ideological (believes company wronged them)

**Technical Sophistication:** Advanced
- Deep knowledge of company systems and security controls
- Understands detection avoidance (knows what's monitored)
- Can create backdoors that evade standard detection
- Familiar with credential rotation and access patterns

**Operational Pattern:**
- Months of preparation (not discovered until departure)
- Careful credential staging and access persistence
- Data exfiltration disguised as normal job activity
- Multiple backdoor creation locations
- Clean-up attempts to cover tracks

### Why They're Dangerous

1. **Trusted Access:** Already has legitimate credentials and system access
2. **System Knowledge:** Understands architecture, backup locations, IR processes
3. **Detection Avoidance:** Knows what gets monitored, what doesn't
4. **Persistence Planning:** Has prepared for long-term access after departure
5. **Evidence Destruction:** Can cover tracks or corrupt evidence

---

## Attack Narrative Timeline

### Phase 1: Preparation (Months 1-4 Before Departure)

**Month 1: Motivation & Planning**
- Employee receives negative performance review
- Denial of promotion triggers decision to leave (and get revenge/profit)
- Begins researching data value and potential buyers
- Identifies what data is most valuable and what's most accessible

**Month 2: Credential & Access Staging**
- Creates secondary service accounts on key systems (appears legitimate)
- Adds own account to shared credential vaults
- Gains access to backup systems by modifying backup scripts
- Documents system architecture and critical asset locations
- Installs personal SSH key on critical jump servers

**Month 3: Backdoor Preparation**
- Stages multiple backdoor tools across different systems
- Modifies startup scripts to maintain persistence
- Creates hidden scheduled tasks that will execute after departure
- Prepares credential theft tools (password vault dumps, Kerberos ticket exporters)
- Sets up reverse shell infrastructure (personal cloud servers, VPN)

**Month 4: Data Exfiltration Begins**
- Begins copying intellectual property to personal cloud storage
- Starts in small amounts to avoid triggering DLP alerts
- Uses legitimate business channels (email archives, scheduled reports)
- Copies architectural diagrams, source code repositories
- Extracts customer lists and financial data
- **Data Stolen:** Approximately 500GB over the month (disguised as normal work)

### Phase 2: Departure & Escalation (Days Before - Day of Departure)

**Day -2: Final Preparations**
- Finalizes all backdoors and persistence mechanisms
- Tests remote access from personal infrastructure
- Transfers last batch of sensitive data
- Modifies security logs to remove evidence of suspicious activity
- Clears browser history and temp files from work computer

**Day -1: Official Departure (Last Day of Work)**
- Completes final tasks appearing normal
- Doesn't communicate anything suspicious
- Leaves company facilities at end of day
- Systems still appear normal; no immediate signs of compromise

**Day 0 (Discovery Window Opens):**
- Company begins offboarding process
- IT attempts to reset departing employee's password
- Discovery: Password resets fail (employee has disabled password change capability)
- IT discovers unauthorized accounts created by departing employee
- Initial investigation begins (this is when exercise starts)

---

## Initial Detection Points

### Detection Point 1: Failed Offboarding
**Time:** T+0 (Start of exercise)
**What IT discovers:**
- Password reset command fails with "Access Denied" error
- Investigation shows password change has been restricted at domain level
- Employee account still shows active login sessions from unknown locations
- Multi-factor authentication has been disabled from the account

**What This Reveals:**
- Departing employee has administrative access to domain controllers or identity systems
- Someone has intentionally prevented normal account disabling
- Possible remote session active from external location

**Initial Concern Level:** Medium-High (unusual for normal departing employee)

### Detection Point 2: Unauthorized Accounts
**Time:** T+15 minutes (discovered during investigation)
**What discovered:**
- Audit logs show service accounts created by departing employee 5 weeks ago
- These accounts have been used to access file servers, databases, and backup systems
- Account names appear legitimate but weren't in approved service account list
- No tickets or approvals in change management system

**What This Reveals:**
- Intentional unauthorized access creation
- Preparation over weeks, not days
- Possible data access through these accounts
- Deliberate circumvention of change management process

**Initial Concern Level:** High (intentional unauthorized accounts)

### Detection Point 3: Suspicious Scheduled Tasks
**Time:** T+30 minutes (discovered during deeper audit)
**What discovered:**
- Scheduled tasks on critical servers created with departing employee's account
- Tasks are set to execute immediately, daily, and on system startup
- Task actions include: credential dumping, data copying, reverse shell connections
- Tasks would execute successfully even after account is disabled

**What This Reveals:**
- Sophisticated persistence planning
- Intent to maintain access after departure
- Automated attacks prepared to execute remotely
- This is no longer HR issue - this is security incident

**Initial Concern Level:** Critical (prepared backdoors, intentional persistence)

### Detection Point 4: Data Exfiltration Evidence
**Time:** T+60 minutes (forensics/log analysis)
**What discovered:**
- Logs show 500GB data transfers to cloud services over past month
- Transfers disguised within normal business data flows
- Destination services are consumer-grade cloud (not corporate approved)
- File access logs show access to IP core repositories, customer databases, architectural documentation

**What This Reveals:**
- Massive data theft already occurred
- Targeted specific high-value data
- Deliberate obfuscation of exfiltration
- Already transferred, potentially sold or shared

**Initial Concern Level:** Critical (data breach has occurred)

---

## Initial Conditions - What Participants Inherit

**Current Time:** Morning after departure discovered (T+0 of exercise)

**Known Facts:**
- Departing employee's account has suspicious activity
- Unauthorized accounts created by that employee have been discovered
- Backdoors appear to be staged on critical systems
- Data has likely been exfiltrated over past month
- Employee is no longer in company facilities
- No immediate evidence of active breach (backdoors set for future execution)

**Current State:**
- IT is in panic (failed offboarding)
- Security is investigating (unauthorized accounts)
- HR is confused (why would departing employee do this?)
- Legal has not been notified yet
- Company does not know scope of data theft
- Employee's personal contact information: [address / family / social media]

**What Participants DON'T Know Yet:**
- How much data was actually stolen
- Where the data went (who it was sold to?)
- How many backdoors exist and on which systems
- If there are accomplices (external parties helping)
- If the employee is still accessing systems remotely
- Whether data has already been sold to competitors
- Risk to customer confidentiality, IP protection, litigation

---

## Organizational Impact Assessment

### Immediate Business Impact (First 24 Hours)
- **Systems:** No immediate system outage, but critical systems potentially compromised
- **Data:** Unknown amount of IP/customer data has been stolen
- **Operations:** No disruption yet, but security of operations is questioned
- **Compliance:** Potential breach notification requirements if customer data involved
- **Reputation:** If data theft becomes public, significant reputational damage

### Longer-Term Implications
- **Customer Confidence:** If customers learn their data was stolen, trust is damaged
- **Competitive Impact:** If stolen IP is sold to competitors, product strategy compromised
- **Regulatory:** Potential CFAA violations, breach notification requirements, SEC reporting if public company
- **Legal:** Employment law considerations (wrongful termination if investigation is wrong?), civil litigation if employee sues
- **Operational:** Forensic investigation will take weeks, multiple systems must be audited

---

## Key Decision Points

### Decision Point 1: Investigation Scope & Approach

**Timing:** T+90 minutes (after initial findings)

**Situation:**
You've confirmed unauthorized accounts, backdoors, and data theft. Now you must decide: How do you approach the investigation?

**Key Tension:** Speed vs. Stealth
- Fast investigation means quickly finding everything but potentially alerts the employee
- Slow investigation means learning full scope without alerting but risks employee destroying evidence or using backdoors
- Wide investigation means examining all systems but takes massive resources
- Narrow investigation means focused but might miss secondary compromises

**Option A: Aggressive Rapid Investigation**
- **Approach:** Immediately audit all systems for backdoors, scan for active remote sessions, reconstruct all data access
- **Timeline:** 48-72 hours intensive forensics
- **Action:** Notify the employee you're investigating (required for employment law in some jurisdictions)
- **Risk:** Employee may destroy evidence from external location, may activate backdoors defensively
- **Benefit:** Quick understanding of full scope
- **Legal Consideration:** Employee has right to know they're being investigated

**Option B: Covert Investigation**
- **Approach:** Silently monitor systems for employee access attempts, audit logs without alerting, gradually understand scope
- **Timeline:** 1-2 weeks to full investigation
- **Action:** Do not notify employee immediately
- **Risk:** Takes longer, misses active threats if employee accesses systems
- **Benefit:** Can catch employee in act of using backdoors, gather evidence of malicious intent
- **Legal Consideration:** May violate employee privacy rights - consult legal counsel immediately
- **Question:** Is this even legal in your jurisdiction?

**Option C: Hybrid Approach**
- **Approach:** Immediately isolate critical systems, begin silent monitoring, notify legal/HR about investigation but not employee
- **Timeline:** Phased investigation (critical systems in 48hrs, full scope in 1 week)
- **Risk:** Moderate on all fronts
- **Benefit:** Balanced approach
- **Action:** Contains damage while gathering evidence

**Who Decides:** Security leadership + Legal counsel + HR leadership

**Evaluation:** Which approach demonstrates good judgment about balancing speed, evidence preservation, and legal compliance?

---

### Decision Point 2: System Containment & Risk Mitigation

**Timing:** T+2 hours (after confirming backdoors)

**Situation:**
Multiple backdoors are staged on critical systems, set to execute after departure. You must decide: Do you shut them down now, or leave them in place to monitor?

**Key Tension:** Kill the threat vs. Monitor the threat
- Immediate shutdown prevents any remote access but loses evidence opportunity
- Leaving backdoors operational creates risk of further compromise but allows monitoring
- Need to secure systems without tipping off employee that you know about backdoors

**Option A: Immediate System Isolation & Remediation**
- **Action:**
  - Isolate all affected systems from network
  - Kill all unauthorized scheduled tasks
  - Remove backdoors and persistence mechanisms
  - Force password reset on all accounts
  - Deploy EDR/monitoring to detect re-entry attempts
- **Timeline:** 24 hours for critical systems
- **Risk:** High - backdoors are destroyed, evidence of sophistication is lost
- **Benefit:** Systems are immediately secure, no risk of remote attack escalation
- **Consequence:** Can't monitor employee's reaction or catch them using backdoors

**Option B: Maintain Backdoors with Silent Monitoring**
- **Action:**
  - Deploy enhanced monitoring on systems with backdoors
  - Leave backdoors in place but monitor for execution attempts
  - Watch for employee logons from external locations
  - Log all activities if backdoors are activated
  - Set alerts for suspicious activity
- **Timeline:** 1-2 weeks while gathering evidence
- **Risk:** High - if backdoors execute, could cause significant damage
- **Benefit:** Can observe employee behavior, gather evidence of intent
- **Consequence:** Takes technical sophistication and constant vigilance

**Option C: Selective Containment**
- **Action:**
  - Immediately remove critical backdoors (those on most sensitive systems)
  - Leave less critical backdoors in place for monitoring
  - Monitor critical systems heavily
  - Set trap alarms if backdoors are accessed
- **Timeline:** Immediate on critical, monitored over time on others
- **Risk:** Moderate
- **Benefit:** Balanced approach

**Who Decides:** CISO + System owners + Legal

**Evaluation:** Which approach shows understanding of incident response priorities (contain the threat) vs. forensic investigation (preserve evidence)?

---

### Decision Point 3: External Notification & Investigation Authority

**Timing:** T+3 hours (when confirming data breach)

**Situation:**
You've confirmed 500GB of company data has been stolen, including customer information. You must decide: Who do you tell and when?

**Stakeholders Who Need to Know:**
- Board/Executive Leadership (corporate governance obligation)
- Customers (if their data was taken - regulatory requirement)
- Law Enforcement (FBI? Local authorities? Private investigator?)
- Insurance Company (cyber insurance may cover)
- Legal Counsel (multiple liability issues)
- External Forensics Firm (specialized investigation)
- Affected Customers/Regulators (breach notification)

**Key Tension:** Transparency vs. Control
- Telling everyone immediately creates accountability but loses control of narrative
- Keeping quiet longer maintains control but increases legal/regulatory risk
- Involving law enforcement helps investigation but limits your options (they take control)
- Not involving law enforcement keeps control but misses investigative resources

**Option A: Controlled Internal Investigation**
- **Action:**
  - Keep investigation internal (security + legal)
  - Do NOT notify law enforcement immediately
  - Do NOT tell customers yet
  - Do notify insurance company (claim investigation)
  - Do notify board privately
  - Attempt to determine if data has been sold/used
  - If no evidence of external sale, consider not notifying customers
- **Justification:** Minimize reputational damage, maintain control
- **Risk:** High - regulators may view this as concealment, customers may have legal claims if we don't notify appropriately, law enforcement later finds out we didn't report timely
- **Legal Reality:** Breach notification laws typically require notification within 30-90 days (varies by state and regulation), but only if there's reasonable likelihood of harm to consumers
- **Regulatory Exposure:** If we self-report, we may get better treatment; if discovered hiding, much worse

**Option B: Immediate Full Disclosure**
- **Action:**
  - Immediately notify board and insurance
  - Immediately notify law enforcement (FBI, local cybercrime unit)
  - Notify affected customers within 48 hours
  - Notify regulators as required
  - Retain external forensics firm
  - Retain external legal counsel
- **Justification:** Transparent, legal compliance, law enforcement resources
- **Risk:** Immediate reputational damage, public incident, loss of investigation control, customer panic, potential stock impact
- **Benefit:** Meets regulatory requirements, law enforcement investigation resources, insurance coverage, demonstrates good faith

**Option C: Staged Disclosure**
- **Action:**
  - Immediately notify board, insurance, and legal
  - Within 24 hours: Notify law enforcement and external forensics
  - Within 72 hours: Notify affected customers
  - Notify regulators per regulatory timeline
  - Maintain coordination between parties
- **Justification:** Balances speed and control
- **Timeline:** Legal and measured approach

**Who Decides:** Board/CEO + Legal + CISO

**Evaluation:** Which approach shows understanding of legal obligations vs. business impact management?

---

### Decision Point 4: Employment Law & Investigation Ethics

**Timing:** T+6 hours (when Legal gets involved)

**Situation:**
Legal counsel points out: "We need to be careful here. We have a former employee we're accusing of crimes. If our investigation is wrong or if we violate their rights, we could face wrongful termination, defamation, or other lawsuits."

**Questions Forcing a Decision:**
1. **Can we investigate without notifying the employee?**
   - Answer: It depends on jurisdiction and circumstances. Some places require notification of employment-related investigations.

2. **Can we cooperate with law enforcement?**
   - Answer: Yes, but be careful about self-incrimination (if company knew about security gaps that allowed this, that's liability).

3. **Should we contact the employee directly?**
   - Answer: Probably not without legal counsel present. They may admit things, or use conversation against you.

4. **What if our evidence is circumstantial?**
   - Answer: With forensics, probably provable, but if investigation is wrong, employee could sue.

**Option A: Investigation with Extreme Caution (Defensive Posture)**
- **Action:**
  - Investigate thoroughly but do NOT accuse employee
  - Document everything professionally
  - Involve legal counsel at every step
  - Do NOT contact employee until legal says OK
  - If law enforcement takes over, let them handle employee contact
  - Assume we might be wrong and prepare alternate explanations
- **Justification:** Protects company from legal liability
- **Risk:** Investigation moves slowly, employee may not cooperate
- **Benefit:** Legally defensible if our investigation is wrong

**Option B: Direct Employee Contact (Confrontational)**
- **Action:**
  - Contact employee with findings
  - Request explanation
  - Make clear this is evidence of criminal activity
  - Inform them law enforcement will be contacted
- **Risk:** Very high - employee may lawyering up, refuse to cooperate, sue us preemptively
- **Benefit:** Get their version of events
- **Likely Outcome:** Employee retains criminal defense attorney, stops cooperating

**Option C: Law Enforcement First (Delegating Decision)**
- **Action:**
  - Contact FBI / local cybercrime unit with findings
  - Let law enforcement lead employee contact
  - Let them handle investigation
  - Company cooperates with their investigation
  - Let prosecutors decide whether to charge employee
- **Justification:** Let professionals handle it
- **Risk:** Law enforcement moves slower, may not prioritize
- **Benefit:** Removes liability from company if investigation goes wrong

**Who Decides:** CEO + General Counsel + CISO

**Evaluation:** Which approach balances thorough investigation with legal risk management?

---

### Decision Point 5: IP Protection & Competitive Response

**Timing:** T+12 hours (when you've confirmed what was stolen)

**Situation:**
Forensics confirms the following was stolen:
- Complete source code for product currently in beta (unreleased)
- Customer lists (500+ enterprise customers)
- Architectural documentation
- Internal roadmap for next 3 years

**Immediate Business Questions:**
1. **Is the stolen IP being used?** Do we know if competitors have it? Has it been sold?
2. **What do we do about the beta product?** Cancel it? Accelerate release? Change architecture?
3. **What about customers?** Do we warn them their data was stolen? Risk losing them to competitors who now have list?
4. **How do we protect remaining IP?** Do we assume all code repositories are compromised?

**Option A: Aggressive IP Protection - Assume Everything is Sold**
- **Action:**
  - Assume stolen IP is now in competitors' hands
  - Immediately change all security credentials (all API keys, database passwords, SSH keys)
  - Rebuild core systems with new architecture
  - Cancel the beta product (competitor will likely release it)
  - Launch counter-intelligence to identify where IP went
  - Immediately patent or file trade secret protections on remaining IP
  - Threat notification to all competitors/law enforcement about stolen IP
- **Cost:** Massive engineering effort, product delay, legal costs
- **Benefit:** Removes competitive advantage of stolen IP
- **Likely Outcome:** 6-12 month delay in all product development

**Option B: Controlled Response - Investigate Before Acting**
- **Action:**
  - Investigate whether stolen IP has been used or sold (monitor dark web, competitor releases, job postings)
  - Change critical credentials only (don't over-react)
  - Keep beta product timeline but accelerate if evidence shows competitor has it
  - Selectively notify key customers if their data is at risk
  - Work with law enforcement on IP theft investigation
- **Cost:** Investigation costs, possible legal costs
- **Benefit:** More surgical response, doesn't over-invest in overreaction
- **Risk:** If waiting to investigate, competitor gets head start

**Option C: Competitive Ace Play - Release Early**
- **Action:**
  - Immediately release the beta product before competitor can (if you think they have source code)
  - Announce the product publicly (first-mover advantage)
  - Claim the idea as yours (not a competitor's)
- **Cost:** Product readiness issues, potentially buggy release
- **Benefit:** First-mover advantage, public IP claim
- **Risk:** Very risky - releasing untested software, competitor might have better version

**Who Decides:** CEO + Product Leadership + Legal + CISO

**Evaluation:** Which approach demonstrates understanding of business impact of IP theft?

---

## Complications & Surprise Elements

### Complication 1: Active Backdoor Execution

**When It's Introduced:** T+8 hours

**What Happens:**
Monitoring alerts show one of the scheduled backdoors has executed. Remote connection established from employee's personal IP address. The connection is attempting to:
- Download additional malware
- Copy more recent data (since departure)
- Modify logs to cover tracks

**Why This Complication Matters:**
- Shows threat is ACTIVE, not historical
- Demonstrates employee is still accessing systems remotely
- Creates legal evidence of criminal intent
- Requires immediate action to stop the ongoing access

**Impact on Previous Decisions:**
- If they chose covert investigation: Now they have evidence of active criminal access
- If they chose aggressive investigation: Confirms the investigation was justified
- If they didn't isolate systems: This is now showing damage happening in real-time

**How to Facilitate:**
- Alert participants: "I've just received an alert from your SOC - they're showing active remote connection from [location] attempting data access"
- Assess their reaction: Do they panic? Stay calm? What's their immediate response?
- Evaluate: Can they respond to active threat while investigating historical compromise?

**Escalation Potential:** This can introduce additional complications if participants don't respond quickly:
- Secondary backdoor activates if first one isn't stopped
- Attacker might wipe evidence if they realize they're detected
- Attacker could establish new persistent access if you don't close all doors

---

### Complication 2: Employee Disappearance / Fleeing Jurisdiction

**When It's Introduced:** T+10 hours

**What Happens:**
Law enforcement reports that the departing employee has disappeared. Their residence is empty, car is gone, and they've stopped responding to calls. International flight records show they departed the country 6 hours ago on a one-way ticket.

**Why This Complication Matters:**
- Makes investigation much harder
- Suggests premeditation (they planned to flee)
- Indicates this wasn't just about getting revenge on company
- May suggest they sold the IP to international buyer
- Creates extradition complications if criminal charges filed

**Impact on Investigation:**
- Can't interview employee directly
- Must pursue international legal cooperation (Interpol, mutual legal treaties)
- Investigation becomes much more resource-intensive
- Assumes employee knew about investigation attempt (or planned to flee anyway)

**Legal Implication:**
- Fleeing jurisdiction after stealing IP strongly suggests criminal intent
- Strengthens case for prosecution
- May indicate international buyer or conspiracy

**How to Facilitate:**
- "Just received call from law enforcement - they checked on the employee and the residence is abandoned. They've left the country."
- Assess participants: Does this change their investigation approach? Their urgency?
- Evaluate: Can they think strategically about international investigation vs. domestic?

---

### Complication 3: Secondary Insider Involved

**When It's Introduced:** T+14 hours

**What Happens:**
Forensic investigation reveals that a SECOND employee (still employed at company) was involved. This employee:
- Created some of the unauthorized accounts
- Provided passwords to the departing employee
- May have provided information about what data would be most valuable
- Is still working at company (in adjacent department)

**Why This Complication Matters:**
- Turns this from insider threat to conspiracy
- Shows security culture problem (multiple employees willing to compromise)
- Creates urgent need to prevent second employee from continuing compromise
- HR/Legal question: Are we exposing ourselves by not acting immediately on second employee?

**Immediate Crisis:**
- Do we immediately terminate second employee?
- Do we immediately notify law enforcement?
- Can we investigate second employee without second one knowing?
- Could second employee be an accomplice to ongoing data theft?

**How to Facilitate:**
- "During log forensics, the team found evidence that a second employee was creating some accounts on behalf of the departing employee. Here's what we found: [details]"
- Assess participants: How do they handle a second-order discovery mid-investigation?
- Evaluate: Can they balance urgency of stopping second threat vs. building case against both employees?

---

### Complication 4: Regulatory Notification Timing Pressure

**When It's Introduced:** T+18 hours (if data breach confirmed)

**What Happens:**
Legal counsel informs participants:
- If customer data is included in the theft, notification is required within 30-90 days (depending on jurisdiction)
- The notification requirement triggers automatically at time of discovery (now)
- There's no grace period for investigation
- Delaying notification creates liability even if breach is ultimately not that bad

**Why This Complication Matters:**
- Forces a decision despite incomplete investigation
- Regulators don't care that you're still investigating - notification clock is running
- Public notification will likely reach competitors (who'll now know IP was stolen)
- Affects business operations (must prepare customer response, legal team, communications)

**The Impossible Choice:**
- Notify now with incomplete picture (might overstate the breach)
- Delay notification risking regulatory penalties (might understate the breach)
- Notify regulatory bodies first, then customers? (Complicated coordination)

**How to Facilitate:**
- "Your legal team just informed you that the notification clock started the moment you confirmed customer data was taken. They're asking: Do you want to notify customers this week, or do you need more investigation time first?"
- Key insight: You can't wait for perfect information - you must decide now based on what you know
- Evaluate: Can they make a decision with incomplete information while managing multiple risks?

---

### Complication 5: Insurance Coverage Question

**When It's Introduced:** T+20 hours

**What Happens:**
Insurance company gets involved and raises a question:
- "Your cyber insurance policy covers external attacks but has an exclusion for insider threats."
- "We're reviewing whether this claim qualifies as 'insider threat' (not covered) or 'compromised credentials' (covered)"
- "The distinction affects whether we reimburse forensics, legal, and notification costs"
- "We need more information about how the compromise occurred to make this determination"

**Financial Impact:**
- Forensics costs: $500K (covered if compromised credentials, not covered if insider threat)
- Legal/notification costs: $300K (similar coverage question)
- Difference: Your company pays $800K out of pocket vs. insurance covers it

**Why This Complication Matters:**
- Creates financial pressure to frame the incident a certain way
- Insurance company investigation may interfere with law enforcement investigation
- Different investigations may reach different conclusions
- Coordination challenge: Security, Legal, Insurance, and Law Enforcement all investigating

**How to Facilitate:**
- "Your insurance broker just called - they need clarity on coverage before committing to payment. The insider threat vs. compromised credentials distinction affects whether they cover your forensics and legal bills."
- Assess: Do participants understand insurance implications? Do they try to manipulate the narrative?
- Evaluate: Can they maintain investigation integrity while managing financial/insurance pressures?

---

## Scenario-Specific Customizations by Industry

### Healthcare

**HIPAA-Specific Elements:**
- Patient records are confirmed to be in stolen data
- HIPAA breach notification requires notification of:
  - Affected individuals (60+ day window)
  - Media (if affects 500+ people)
  - HHS (if affects 500+ people)
  - State health department
- Breach report to HHS becomes public record

**Industry-Specific Impact:**
- Patient privacy is critical - notification is non-negotiable
- Regulatory action from state health department
- Potential HIPAA penalties: $100-$50K per violation
- Loss of reputation in healthcare market

**Additional Complication for Healthcare:**
- Insider might have had access to medical records of specific high-profile patients
- These patients may sue company directly for privacy breach
- Media picks up story: "Hospital Data Thief Stole Records of [Notable Patient]"

---

### Finance/Banking

**Regulatory-Specific Elements:**
- Customer financial data stolen (PII + account information)
- Triggers notification requirements under:
  - Gramm-Leach-Bliley Act (GLB)
  - SEC reporting requirements (if public company)
  - State banking regulators
  - Consumer Financial Protection Bureau (CFPB)

**Industry-Specific Impact:**
- Reputation damage in financial services (trust is everything)
- SEC reporting requirement triggers stock disclosures
- Bank regulators may restrict business operations pending investigation
- Potential for civil litigation from customers

**Additional Complication for Finance:**
- Insider may have had access to wire transfer systems
- Threat: If insider gives credentials to accomplices, fraudulent transfers could happen
- This creates need for immediate access revocation and transaction monitoring
- Complication: System shutdown for access review impacts business operations

---

### Manufacturing

**Industry-Specific Elements:**
- Stolen IP might include:
  - Product designs
  - Manufacturing processes
  - Supply chain information
  - Licensing/patent information

**Impact:**
- Competitive advantage immediately lost
- Manufacturing partners now at risk if supply chain info is stolen
- Possible disruption of supply chain if partners discovered breach
- Product liability if stolen design has flaws that outsiders exploit

**Additional Complication for Manufacturing:**
- Insider might also have factory access credentials
- Threat: Insider could sabotage manufacturing equipment remotely
- Creates occupational safety risk (if equipment is compromised)
- Complication: May need to halt manufacturing pending security audit

---

### Technology / SaaS

**Industry-Specific Elements:**
- Source code is primary asset
- Stolen code might include:
  - Customer data access code
  - Authentication/authorization mechanisms
  - Vulnerability research
  - Zero-day information

**Impact:**
- Security of entire customer base at risk
- Insider might have access to backdoors or persistent access mechanisms
- Customers may lose confidence in product security
- Competitors can now re-engineer product

**Additional Complication for Technology:**
- Insider likely created backdoors for remote access
- Threat: Insider could pivot to customer accounts through application backdoors
- Creates immediate need to audit all customer accounts
- Complication: Customer notification about potential account compromise (separate from IP theft notification)

---

### Finance/Investment

**Insider Trading Risk (If Finance):**
- Insider with access to insider information stole company financial data
- Threat: They could trade on insider knowledge
- SEC Investigation becomes possible
- Complication: Company executives may be subject to SEC investigations themselves

---

## IR Capabilities Tested

### Digital Forensics
- **Timeline Reconstruction:** Can they determine when compromise started?
- **Evidence Collection:** Can they preserve evidence properly for legal/prosecution?
- **Data Exfiltration Tracing:** Can they determine what data left and where it went?
- **Artifact Analysis:** Can they find evidence of tool usage, persistence mechanisms, data staging?

### HR / Legal Coordination
- **Employment Law:** Do they understand investigation ethics and employee rights?
- **Evidence Handling:** Do they maintain chain of custody properly?
- **Communication:** Can HR and Security work together effectively?
- **Termination Decision:** When/how is it safe to fire second employee if involved?

### Internal Investigation Leadership
- **Scope Management:** Do they investigate appropriately without over-reaching?
- **Timeline Management:** Can they balance speed with thoroughness?
- **Resource Allocation:** Do they understand what forensics costs and what it requires?
- **Communication Management:** Can they keep investigation confidential while needing executive awareness?

### Regulatory Compliance
- **Notification Requirements:** Do they understand breach notification laws?
- **Timing:** Can they make decisions despite notification clock pressure?
- **Evidence Preservation:** Do they understand legal hold requirements?
- **Law Enforcement Cooperation:** Can they work with law enforcement appropriately?

---

## Success Indicators

### Strong Response (Advanced Maturity)
- ✓ Immediately recognized this as more complex than external attack
- ✓ Involved Legal early and throughout
- ✓ Understood investigation ethics and employee rights
- ✓ Balanced investigation scope (thorough but not overreaching)
- ✓ Coordinated with law enforcement appropriately
- ✓ Understood regulatory notification requirements
- ✓ Made clear chain of custody decisions for forensics
- ✓ Identified both the threat (departing employee) and the systemic issue (second employee involvement)
- ✓ Understood the business/competitive implications of stolen IP
- ✓ Managed communications appropriately (not leaking investigation details)

### Developing Response (Intermediate)
- ✓ Recognized this was an insider threat
- ✓ Involved security and HR leadership
- △ Some Legal involvement but maybe not early enough
- △ Investigation scope was appropriate but some confusion about HR vs. security roles
- △ Made good decisions but some hesitation or second-guessing
- △ Understood breach notification but unclear on timeline

### Weak Response (Emerging Capability)
- ✗ Didn't recognize severity initially
- ✗ Treated as pure IT problem without involving HR/Legal
- ✗ Investigation approach was either too aggressive (privacy violations) or too passive (missed threats)
- ✗ Didn't understand breach notification requirements
- ✗ Made decisions without considering legal implications
- ✗ Didn't involve law enforcement
- ✗ Poor communication about investigation (leaked information or failed to keep leadership informed)

---

## Scenario Customization Notes

### For Beginner Groups
- Simplify by removing Complication 2 (employee fleeing) and Complication 3 (second insider)
- Reduce number of backdoors to investigate
- Make data theft more obvious and complete (less ambiguity)
- Reduce legal/regulatory complexity

### For Advanced Groups
- Add complication about potential international buyer for IP
- Introduce law enforcement investigation that conflicts with company investigation
- Add complication about insurance coverage disputes
- Introduce second-order insider threat (second employee may have had accomplices)
- Explore ethical questions around investigation methods and employee privacy

### For Different Styles
- **Traditional:** Emphasize discussion of each decision point, deep exploration of "what if" scenarios
- **Blended:** Introduce complications mid-decision to add pressure while maintaining discussion
- **Gamified:** Time each investigation phase, introduce complications as timed surprises, track decision quality with scoring

---

**Scenario Complete**

This insider threat scenario is ready for use in TTX exercises. It tests different capabilities than the ransomware scenario (digital forensics, HR/Legal coordination, investigation ethics) while maintaining the same structure and component library support.

All 5 decision points are industry-agnostic. All complications have industry-specific variants. All injects follow the template from `components/inject-library.md` (with industry customization examples).
