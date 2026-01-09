# Third-Party Vendor Compromise Scenario - Cloud Services Provider Breach

**Difficulty Level:** Advanced
**Recommended Duration:** 4-hour or full-day exercise
**Industry Applicability:** All industries (any organization using cloud services, SaaS platforms, managed services)
**Scenario Type:** Trusted vendor compromised, affecting your customer data and infrastructure
**Technical Weight:** Moderate-Tech

---

## Executive Summary

This scenario simulates a breach of a trusted third-party vendor who has access to your critical systems and customer data. Unlike supply chain attacks (where you distribute malware), this scenario focuses on a vendor you depend on being compromised, potentially exposing your infrastructure, customer data, and giving attackers persistent access to your environment.

**Key Characteristics:**
- **Trust violation** (vendor breach shatters trust relationship)
- **Cascading access** (vendor has keys to your kingdom)
- **Regulatory complexity** (your breach + vendor breach = dual liability)
- **Customer impact** (their data may be at risk through your systems)
- **Operational disruption** (vendor may need to be disconnected mid-service)
- **Vendor coordination** (work with compromised vendor in real-time)
- **Unknown exposure** (unclear what vendor had access to)

**Scenario Tests:**
1. **Vendor due diligence** - Did you know what vendor could access?
2. **Rapid incident triage** - Can you quickly assess impact?
3. **Operational continuity** - Can you keep services running after vendor disconnection?
4. **Vendor communication** - Managing difficult conversations with compromised vendor
5. **Customer transparency** - Communicating to customers about third-party risk
6. **Regulatory response** - Reporting breach of vendor that breached you
7. **Contract enforcement** - What recourse do you have against vendor?

---

## Threat Actor Profile

### Advanced Persistent Threat (Nation-State or Sophisticated Criminal)

**Motivation:**
- **Persistent access:** Compromise vendor to gain long-term access to multiple customers
- **High-value targets:** Target large customer using the vendor
- **Business intelligence:** Steal trade secrets, financial data, strategic plans from customers
- **Leverage:** Use vendor compromise as stepping stone to government/financial targets
- **Disruption:** Cause operational chaos or system failures

**Attack Path:**
1. **Intelligence:** Identifies your organization as target
2. **Vendor selection:** Researches which vendors have deepest access to your systems
3. **Vendor compromise:** Targets vendor with weaker security than yours
4. **Access expansion:** Uses vendor access to explore your infrastructure
5. **Lateral movement:** Moves from vendor systems into your customer systems
6. **Persistence:** Establishes backdoors for long-term access
7. **Exploitation:** Steals data, maintains access, prepares for broader attack

**Timeline:**
- **Vendor compromise:** 4-8 weeks before your discovery
- **Attacker reconnaissance:** 2-3 weeks inside your infrastructure
- **Preparation:** 1-2 weeks developing persistence mechanisms
- **Discovery:** External report, customer report, or internal detection
- **Your incident:** T+0 (vendor breach notification)

---

## Attack Narrative Timeline

### Phase 1: Vendor Compromise (Weeks Before Your Incident)

**How Vendor Gets Breached:**

1. **Initial access to vendor** (4 weeks before)
   - Phishing of vendor employee with admin credentials
   - Exploit of unpatched vendor server
   - Insider threat at vendor company
   - Supply chain attack on vendor's own dependencies

2. **Establishing persistence** (3-4 weeks before)
   - Creates admin accounts with backdoor access
   - Installs web shell in vendor's infrastructure
   - Modifies vendor's backup/recovery systems (disables ransomware cleanup)
   - Establishes encrypted C2 (command & control) channel

3. **Vendor doesn't notice** (ongoing)
   - Vendor may have weak detection capabilities
   - Vendor logs not reviewed regularly
   - Attacker is careful (low-and-slow reconnaissance)
   - Vendor's security team focused on external threats, not internal compromise

---

### Phase 2: Lateral Movement to Your Infrastructure (2-3 weeks before)

**How Attacker Gets From Vendor to You:**

**Vendor's privileged access to your systems:**
- API keys and credentials stored in vendor infrastructure
- SSH keys for your cloud environments
- Database passwords for your customer data
- Application credentials for your SaaS platforms
- VPN access to your private networks

**Attacker's progression:**
1. **Extracts credentials** from vendor's configuration management systems
2. **Tests access** to your infrastructure (API calls, VPN connections)
3. **Explores your environment:** Cloud accounts, database servers, application servers
4. **Identifies valuable targets:** Where is customer data? Where are crown jewels?
5. **Plants persistence:** Backdoors, scheduled tasks, modified cloud IAM policies
6. **Prepares exfiltration:** Sets up data collection and covert channels

**What attacker can potentially access:**
- **Your infrastructure:** Cloud accounts, servers, databases, backups
- **Customer data:** Personal information, financial data, healthcare records
- **Intellectual property:** Source code, product roadmaps, patents
- **Financial systems:** Billing systems, payment processing, accounting
- **Communications:** Email, Slack, internal documents, meetings

**Attacker's mindset:**
- Focuses on stealth (wants to access your systems for weeks without detection)
- May be gathering intelligence for future attack
- May be selling access to other criminals
- May be preparing ransomware extortion

---

### Phase 3: Discovery (Hours Before Exercise Starts)

**How You Discover the Breach:**

**Discovery Path 1: Vendor Transparency (Best Case)**
- Vendor notices suspicious activity in their infrastructure
- Vendor conducts forensic investigation
- Vendor realizes attacker had YOUR credentials
- Vendor contacts you: "We think we were breached. You may be affected."
- Notification: Within 24 hours of vendor discovering compromise

**Discovery Path 2: Regulatory/Law Enforcement Notification**
- FBI contacts you: "We're investigating attacks originating from [VENDOR]. Your organization appears affected."
- You learn about vendor breach from law enforcement, not vendor
- Notification: 48-72 hours after breach, but attacker may have had longer access

**Discovery Path 3: Your Security Team Detects Indicators**
- Your SOC detects: Unusual API activity, cloud account modifications, unusual login locations
- Your threat hunting team finds: Unfamiliar IAM roles, unexpected cloud resources
- Investigation reveals: Attacker used vendor-provided credentials
- Notification: Depends on detection capabilities (hours to days after activity)

**Discovery Path 4: Customer Reports Impact**
- Your customer reports their data was accessed from your systems
- You investigate and discover: Attacker accessed via your vendor's compromised access
- Notification: Could be days/weeks after initial breach (worst case)

**For Exercise Purposes - Assume Discovery Path 1:**
- Vendor contact: "We were breached. Your credentials were compromised. We're not sure if attacker used them."
- Your immediate assessment: "We don't know if we were compromised or how extensive the access was."
- Timeline pressure: Vendor recommends credential rotation, password resets, security review

---

## Exercise Briefing (T+0)

### Your Situation:

You are the Head of Security for [YOUR COMPANY], which relies heavily on [VENDOR NAME] for cloud infrastructure, identity management, and data backup.

**What's happening:**
- [VENDOR NAME] contacts your security team: "We experienced a security incident. Your API credentials and SSH keys were stored in our systems and may have been accessed."
- [VENDOR] provides: Forensic summary showing attacker access from [DATES] to [DATES]
- Estimated access window: 3 weeks

**Your immediate assessment:**
- [VENDOR] has credentials to: AWS accounts, GCP projects, Azure subscriptions, databases, VPN
- Unknown: Did attacker actually use the credentials? What did they access?
- Unknown: Did attacker plant persistence mechanisms before we discovered them?
- Unknown: Is attacker still in our systems?

**Vendor's offer:**
- Forensic investigation of vendor's infrastructure (available tomorrow)
- Help rotating your credentials (can start immediately)
- Access logs showing when YOUR credentials were used (available in 4 hours)
- No guaranteed timeline for complete forensic report

**Known Information:**
- [VENDOR] is critical to your operations (70% of infrastructure depends on them)
- You have ~500 customers using your platform
- Customer data stored in [VENDOR]-managed databases: 50 million records
- You have no alternative vendor readily available (switching would take weeks)
- Some of your customer data is regulated (GDPR, HIPAA, PCI-DSS)

**Unknown Information:**
- Did attacker access your infrastructure?
- What specific credentials were accessed? (Not all, or all?)
- How many of your cloud resources were touched?
- Was customer data accessed or exfiltrated?
- Are there persistence mechanisms (backdoors) still active?
- Is attacker still inside your systems?

---

## Key Decision Points

### Decision Point 1: Immediate Credential & Access Management (T+0 to T+2 hours)

**Core Dilemma:** Defend against unknown attacker while maintaining operations

**Option A: Aggressive Rotation ("Assume Compromise")**
- Immediately rotate ALL credentials that were potentially compromised
- Revoke all API keys issued to [VENDOR]
- Force password resets for all employees
- Disconnect [VENDOR] entirely (emergency plan)
- **Pros:** Stops attacker's access, assumes worst-case scenario
- **Cons:** [VENDOR] services go offline (no backups, no infrastructure management), operations disrupted, customers impacted
- **Risk:** If [VENDOR] had your database passwords, rotating means re-establishing access (downtime)
- **Timeline:** 4-6 hours to complete rotation, 2-4 hours downtime

**Option B: Targeted Rotation ("Smart Triage")**
- Request detailed list of which credentials [VENDOR] had access to
- Prioritize: Database passwords, admin cloud credentials, SSH keys
- Rotate only high-risk credentials first
- Keep [VENDOR] access for non-critical functions
- **Pros:** Minimizes operational impact, maintains services
- **Cons:** Incomplete protection, attacker may still have some credentials
- **Risk:** Incomplete rotation misses critical access
- **Timeline:** Depends on [VENDOR] providing credential list (potentially hours)

**Option C: Monitored Credentials ("Let's Watch")**
- Don't rotate credentials immediately
- Implement enhanced monitoring on all [VENDOR]-related access
- Watch for attacker using credentials
- Rotate when you have evidence of attacker activity
- **Pros:** No operational disruption, maximum visibility into attacker behavior
- **Cons:** Attacker still has access, may be actively exploiting, data at risk
- **Risk:** Waiting for evidence may be too late
- **Timeline:** Watch for 2-4 hours, then reassess

**Option D: Phased Approach ("Staged Remediation")**
- Phase 1 (Immediate): Rotate database passwords and admin credentials
- Phase 2 (Within 1 hour): Disconnect [VENDOR] from production, establish alternative access
- Phase 3 (Within 4 hours): Migrate critical workloads off [VENDOR] infrastructure
- Phase 4 (Ongoing): Complete migration to alternative vendor
- **Pros:** Balances security with operational continuity
- **Cons:** Complex coordination, risk of incomplete transitions
- **Risk:** Phase transitions fail, operational chaos
- **Timeline:** 4-6 hours for phases 1-3, days for phase 4

**Impact:**
- Determines: Operational impact to your customers, discovery of attacker persistence
- Affects: Regulatory notification timeline (if systems go down, customers notice)
- Influences: Vendor response and future relationship

### Decision Point 2: Investigation Scope & Speed (T+2 to T+4 hours)

**Challenge:** Understand the extent of attacker access

**Option A: Internal Investigation ("DIY")**
- Your security team investigates your infrastructure
- Analyze cloud access logs, API usage, IAM changes
- Search for persistence mechanisms, unusual configurations
- Takes time: 8-24 hours to comprehensive findings
- **Pros:** Complete control, potentially faster initial findings
- **Cons:** May miss sophisticated persistence, resource intensive
- **Timeline:** 24+ hours to complete picture

**Option B: Vendor-led Investigation ("Trust the Vendor")**
- [VENDOR] leads full forensic investigation
- Your team provides access to your infrastructure
- Relies on vendor's forensic capabilities
- **Pros:** Vendor familiar with their own systems, dedicated resources
- **Cons:** Vendor may be overwhelmed, may miss attacker activity in YOUR systems
- **Risk:** Vendor has reputational incentive to minimize findings
- **Timeline:** 48+ hours for comprehensive report

**Option C: Third-Party Forensics ("Bring in Experts")**
- Engage major forensic firm (Mandiant, CrowdStrike, etc.)
- They investigate both vendor and your infrastructure
- Provides objective, credible findings
- **Pros:** Expert capability, objective findings, legal credibility
- **Cons:** Expensive ($500K-$2M+), takes 48+ hours to mobilize
- **Timeline:** 2-4 hours to engage, 24+ hours to investigation start

**Option D: Parallel Investigations ("Everyone Investigates")**
- Your team investigates your infrastructure immediately
- Third-party firm investigates both vendor and your systems
- Vendor conducts their own investigation
- Share findings in real-time
- **Pros:** Multiple perspectives, parallel timelines, rapid findings
- **Cons:** Coordination complexity, costs ($1M+), potential contradictions
- **Timeline:** Fastest to comprehensive findings (real-time updates)

**Impact:**
- Determines: Speed and completeness of understanding
- Affects: Customer notification timeline (can't notify without evidence)
- Influences: Legal liability (investigation quality affects regulatory response)

### Decision Point 3: Customer Notification & Transparency (T+4 to T+24 hours)

**Complexity:** Customers depend on [VENDOR]. Telling them [VENDOR] was breached creates panic.

**Option A: Transparent Immediate Disclosure**
- Contact customers within 4 hours
- "Our vendor [VENDOR] was breached. Your data may be at risk. Here's what we're doing."
- Provide indicators of compromise, detection guidance
- Assume worst-case: Attacker accessed customer data
- **Pros:** Transparent, customers can take protective measures
- **Cons:** Massive reputation damage, customer panic, immediate churn, support overload
- **Risk:** Customers may switch vendors before you understand actual impact
- **Timeline:** Fastest to notification

**Option B: Wait for Investigation Findings ("Informed Notification")**
- Conduct investigation first
- Determine actual impact to customer data
- Notify only when you have definitive information
- **Pros:** Accurate information, no false alarms, less panic
- **Cons:** Delayed notification (regulatory risk), customers may self-discover
- **Risk:** Regulators may consider delay as violation of notification requirements
- **Timeline:** 24-48 hours to investigation completion

**Option C: Phased Notification ("Progressive Updates")**
- Notify customers of vendor breach immediately (factual, no speculation)
- Provide initial findings within 4 hours
- Commitment to daily updates as investigation progresses
- Final assessment within 48 hours
- **Pros:** Transparency + investigation time, controlled information flow
- **Cons:** Requires frequent updates, inconsistencies may appear
- **Timeline:** Balanced approach

**Option D: Managed Disclosure ("Control the Narrative")**
- Make one public statement: "We became aware of vendor issue, taking precautions"
- Don't mention "your data," minimize technical details
- Provide detailed information only to customers who ask
- **Pros:** Limits panic, controls information flow
- **Cons:** Appears evasive, information will leak, customers angry at lack of transparency
- **Timeline:** Slowest to full customer awareness

**Impact:**
- Determines: Brand reputation, customer retention, class action lawsuit risk
- Affects: Regulatory penalties (transparency vs. minimization)
- Influences: Employee morale (company credibility in eyes of staff)

### Decision Point 4: Vendor Relationship & Contract Enforcement (T+6 to T+48 hours)

**Difficult Choice:** Hold vendor accountable vs. Maintain critical business relationship

**Option A: Aggressive Legal Response ("Hold Them Liable")**
- Immediately notify [VENDOR] of breach-of-contract
- Demand: Full forensic investigation, cost reimbursement, liability acceptance
- Threaten legal action and contractual termination
- Hire lawyers to prepare damages claim
- **Pros:** Holds vendor accountable, potential compensation, sets precedent
- **Cons:** Vendor may stonewall, slows investigation, relationship destroyed
- **Risk:** If you terminate vendor, operations disrupted (they still manage your infrastructure)
- **Timeline:** Legal process takes weeks

**Option B: Cooperative Investigation ("Work Together")**
- Approach vendor as partner in investigation
- "Help us understand what happened and ensure it doesn't happen again"
- Avoid blame initially, focus on remediation
- Negotiate cost-sharing for investigation and remediation
- **Pros:** Vendor more likely to cooperate fully, investigation faster, maintains relationship
- **Cons:** Vendor may minimize liability, you may not get full accountability
- **Risk:** Vendor escapes responsibility for breach
- **Timeline:** Faster investigation, ongoing relationship

**Option C: Hybrid Approach ("Accountability + Partnership")**
- Make vendor responsibility clear in documentation
- Open investigation cooperation channels
- Reserve right to pursue claims later when facts clear
- Negotiate immediate actions: Vendor-funded investigation, enhanced monitoring
- **Pros:** Clear accountability, cooperative investigation, preserved option to litigate
- **Cons:** Requires careful communication, legal coordination
- **Timeline:** Balanced approach to investigation and negotiation

**Option D: Immediate Termination ("Break the Relationship")**
- Terminate vendor contract immediately
- Begin emergency migration to alternative vendor
- Inform customers: "We're moving away from [VENDOR]"
- Pursue maximum legal damages
- **Pros:** Clear separation from compromised vendor, strong customer response
- **Cons:** Operational chaos (vendor still manages infrastructure), migration takes weeks
- **Risk:** Your infrastructure goes offline, customers lose services
- **Timeline:** Crisis management mode for 2-4 weeks

**Impact:**
- Determines: Vendor cooperation with investigation, remediation speed
- Affects: Operational continuity (can you stay on vendor's infrastructure?)
- Influences: Your ability to move customers to alternative vendor

### Decision Point 5: Regulatory & Law Enforcement Engagement (T+0 onwards)

**Multiple Agencies Will Be Involved:**
- FBI/CISA (if critical infrastructure)
- State regulators (if financial or healthcare data)
- SEC (if public company)
- International agencies (if EU data)

**Option A: Proactive Full Cooperation ("Help Us Catch Them")**
- Immediately contact FBI/CISA with breach notification
- Provide full forensic findings and infrastructure access
- Cooperate completely with investigation
- **Pros:** Law enforcement support, expertise, international coordination
- **Cons:** Investigation controls your timeline, public attribution may cause international incident
- **Timeline:** Law enforcement engagement within 4 hours

**Option B: Defensive Response ("Minimum Required")**
- Wait for regulators to contact you
- Provide required information only
- Minimize government interference in your investigation
- **Pros:** Maintain operational control, faster timeline
- **Cons:** Agencies suspicious, potentially slower federal investigation
- **Timeline:** Regulators contact within 24-48 hours

**Option C: Legal-Mediated Engagement ("Lawyers First")**
- All regulatory communication through outside counsel
- Negotiate disclosure scope with regulators
- Seek attorney-client privilege protection
- **Pros:** Legal protection, careful information control
- **Cons:** Slower response (lawyers add coordination), agencies frustrated
- **Timeline:** Legal preparation adds 2-4 hours

**Option D: Public Statement + Cooperation ("Transparency + Professional")**
- Issue public statement acknowledging vendor breach
- Commit to transparency about your investigation findings
- Engage with regulators and law enforcement openly
- Provide findings as available, not under pressure
- **Pros:** Shows accountability, regulatory trust, public confidence
- **Cons:** Detailed disclosures may inform attackers, slower investigation
- **Timeline:** Balanced approach to transparency

**Impact:**
- Determines: Government investigation trajectory, international response
- Affects: Potential sanctions/criminal referrals, recovery of stolen data
- Influences: Media narrative (cooperative vs. evasive)

---

## Investigation Questions

As incident unfolds, team must answer:

1. **Did attacker actually use credentials?** (Access logs from vendor and your systems)
2. **What data did attacker access?** (Customer data? IP? Financial data?)
3. **What was exfiltrated?** (Did data leave your systems?)
4. **How long had attacker access?** (Days? Weeks? Months?)
5. **What persistence mechanisms remain?** (Backdoors? Modified configurations?)
6. **Is attacker still active?** (Currently accessing systems?)
7. **Which customer data is affected?** (Which customers? What information?)
8. **Who's the attacker?** (Criminal? Nation-state? Signatures?)
9. **Why did [VENDOR] security fail?** (To prevent this vendor from being hit again)
10. **What's our liability to customers?** (What compensation/remediation required?)
11. **What regulatory notification is required?** (GDPR? HIPAA? CCPA? Others?)
12. **Can we trust [VENDOR] going forward?** (Stay or switch?)

---

## Complications (Scenario Escalation)

### Complication 1: Persistence Discovered (T+6 to T+12 hours)

**Trigger:** Investigation finds attacker backdoors in your infrastructure

**Scenario:**
- "We found [number] unauthorized IAM roles created during the compromise window"
- "There's a scheduled Lambda function that executes every night, exfiltrating data to external S3 bucket"
- "We found modified VPC flow logs - attacker disabled logging for their own activity"
- "SSH keys on [NUMBER] servers have been replaced with attacker's public key"

**Impact:**
- Attacker may still be monitoring your infrastructure
- Remediation becomes more complex (find and remove all persistence)
- Data exfiltration may still be ongoing
- Regulatory implication: "You didn't detect this immediately"

### Complication 2: Customer Data Confirmed Exfiltrated (T+12 to T+24 hours)

**Trigger:** Investigation evidence shows data was stolen

**Scenario:**
- "We found outbound connections from our database server to attacker IP address"
- "File transfer logs show 500GB of data downloaded during the compromise period"
- "Database backups stored in [VENDOR] infrastructure are missing - attacker copied them"
- "Customer financial data from [CUSTOMER NAME] accessed and downloaded"

**Impact:**
- Moves from "may have been accessed" to "definitely compromised"
- Mandatory customer notification required
- Regulatory investigation certain
- Class action lawsuit risk becomes real
- Financial impact: Notification costs, credit monitoring, potential damages

### Complication 3: Multiple Vendor Compromise Chain (T+24 to T+48 hours)

**Trigger:** Investigation reveals vendor's vendor was also compromised

**Scenario:**
- "[VENDOR] uses [SUB-VENDOR] for backup services - that vendor was also breached"
- "Attacker used [SUB-VENDOR]'s access to get deeper into [VENDOR], then into you"
- "Scope of compromise may be even worse than initially assessed"
- "Multiple layers of vendor relationships now exposed"

**Impact:**
- Supply chain risk becomes apparent
- Regulators will ask: "Why didn't you audit your vendor's vendors?"
- Scope of compromise may be unknown (how deep does the chain go?)
- Trust in entire vendor ecosystem questioned

### Complication 4: Customer Self-Discovery Before Your Notification (T+18 to T+36 hours)

**Trigger:** Customer discovers their data was compromised before you notify them

**Scenario:**
- Major customer (or multiple customers) detects attacker activity in their own infrastructure
- Customers begin forensic investigation, discover it came from your systems
- Customers demand immediate answers before you've completed investigation
- Customers announce their breach publicly before your formal notification
- **Media narrative shifts:** "Customer discovered breach first, vendor was slow to notify"

**Impact:**
- Reputation damage (appears you were hiding information)
- Regulatory concern (notification was too late)
- Customer churn (they lose confidence)
- Media coverage accelerates

### Complication 5: Regulatory Investigation Initiated (T+24 to T+72 hours)

**Trigger:** Regulators formalize investigation into your incident response

**Scenario:**
- GDPR authority issues formal investigative order
- SEC files formal investigation (if public company)
- FBI presents grand jury subpoena
- Regulators demand: Full forensic reports, timeline of discovery, evidence of response

**Impact:**
- Your incident response becomes subject of regulatory scrutiny
- If you made mistakes (slow response, inadequate investigation), penalties increase
- All communications become discoverable
- Legal process becomes formal and adversarial

### Complication 6: Breach Becomes Ransomware Enabler (T+24 to T+48 hours)

**Trigger:** Attacker uses compromised access to deploy ransomware

**Scenario:**
- Attacker uses backdoors to encrypt your databases and backup systems
- Ransom demand: $5 million
- Message: "We have your data and encrypted your systems. Pay or we publish to customers and FBI."
- Timeline: 72 hour deadline

**Impact:**
- Incident escalates from "breach" to "operational crisis"
- Operations team must decide: Pay ransom or rebuild from scratch?
- Negotiation with threat actor required (illegal in some jurisdictions)
- Regulatory and law enforcement restrictions on ransom payment

### Complication 7: Vendor Bankruptcy/Closure (T+48 to T+72 hours)

**Trigger:** [VENDOR] announces they can't recover from breach and shutting down

**Scenario:**
- "Due to the scope of the compromise, [VENDOR] can no longer guarantee service integrity"
- "[VENDOR] is closing and returning customer data within 30 days"
- "Migration to new vendor required for all customers - [VENDOR] will not assist"

**Impact:**
- Emergency migration required
- 500+ customers must migrate immediately
- Operational continuity crisis
- Vendor failure adds to reputational damage to you

---

## Facilitator Guidance

### What to Watch For

**Excellent Responses:**
- Rapid assessment of vendor's actual access to systems
- Immediate triage: What credentials were exposed? What's critical?
- Balanced approach: Defend systems while maintaining operations
- Vendor coordination: Work with breached vendor despite circumstances
- Investigation quality: Understand scope before customer notification
- Regulatory proactivity: Contact agencies, don't wait for them
- Prevention focus: Change vendor selection and monitoring processes

**Common Mistakes:**
- Assuming [VENDOR] had limited access (many vendors have broad access)
- Rotating all credentials at once (causes operational chaos)
- Delaying customer notification (regulatory violation)
- Blaming vendor publicly (hardens their position, slows investigation)
- Assuming you understand scope without investigation (impacts customer notification accuracy)
- No systemic change (fixes this incident but doesn't prevent next)

### Socratic Facilitation Prompts

1. **On credentials:** "You're rotating [X] credentials. What happens to the systems that depend on those credentials? Have you tested the rollback?"

2. **On timeline:** "You're investigating for [Y hours] before notifying customers. Will that meet regulatory notification requirements?"

3. **On vendor:** "You're suing the vendor. Will they cooperate with your investigation? What if you need their help later?"

4. **On scope:** "You're assuming [X amount] of customer data is at risk. What evidence supports that? What if you're wrong?"

5. **On communication:** "You're telling customers [X]. Is that consistent with the facts you have? What if investigation proves something different?"

6. **On operations:** "You're staying with [VENDOR] for infrastructure. How do you trust them after compromise?"

7. **On prevention:** "This happened through a vendor you trusted. What changes to vendor management prevent recurrence?"

### Evaluation Criteria

**Evaluate on:**
- ☐ Speed of initial triage (how quickly assessed vendor's scope of access?)
- ☐ Operations preservation (maintained customer services while defending?)
- ☐ Investigation quality (comprehensive, credible findings?)
- ☐ Vendor coordination (effective communication with breached vendor?)
- ☐ Customer communication (transparent, timely, accurate?)
- ☐ Regulatory engagement (proactive vs. reactive?)
- ☐ Decision quality (good risk/benefit decisions under uncertainty?)
- ☐ Team coordination (security, ops, legal, exec working together?)
- ☐ Vendor management changes (prevented recurrence through process improvement?)

---

## Industry-Specific Variations

### Financial Services
- Immediate SEC/federal regulator notification required
- Systemic risk implications (impacts other financial institutions)
- Regulatory penalties focus on vendor risk management practices
- Customer account compensation likely required

### Healthcare (HIPAA)
- Breach notification within 60 days
- HHS Office for Civil Rights investigation
- Vendor vetting requirements become stricter
- Liability: Did vendor compromise contribute to patient harm?

### Government/Critical Infrastructure
- National security implications
- CISA involvement mandatory
- International cyber response if nation-state involved
- Potential sanctions/criminal referrals

---

## Duration Variations

### Full-Day Exercise (6-8 hours)
- Complete incident response with investigation and remediation
- Multiple complications (ransomware, vendor closure, etc.)
- Focus: Crisis management, vendor relationship, prevention
- Includes: All decision points with real consequences

### 4-Hour Exercise (Standard)
- Initial incident response and investigation start
- First 1-2 complications
- Focus: Immediate decision-making and triage
- Stop after: Investigation findings and customer notification strategy
- Emphasis: Speed and decision quality under uncertainty

---

**End of Third-Party Vendor Compromise Scenario**

This scenario emphasizes that modern organizations are highly dependent on vendors, creating both risk and responsibility. The response requires rapid triage, careful vendor coordination, and transparent customer communication.
