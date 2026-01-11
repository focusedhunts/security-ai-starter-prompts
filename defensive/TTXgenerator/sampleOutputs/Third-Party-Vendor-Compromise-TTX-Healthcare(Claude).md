# Third-Party Vendor Compromise TTX Exercise
## Small Healthcare Organization | 4-Hour Blended Format

**Organization Context:** Small healthcare provider (150 employees), new executive leadership team, beginner IR maturity

**Exercise Objectives:** Decision-making under uncertainty, regulatory readiness, vendor coordination

**Duration:** 4 hours | **Format:** In-person | **Participants:** 8 (mixed technical/executive)

**Style:** Blended (discussion-focused early phase, increasing time pressure mid/late phases)

---

## EXERCISE OVERVIEW

### Scenario Summary

Your organization uses a cloud-based medical records backup and archival service (CloudMed Secure) that has been operational for 3 years. Today, you receive notification that CloudMed Secure was breached by an advanced threat actor. The attacker gained access 6 weeks ago through compromised vendor credentials and maintained persistent access to your customer records.

Your organization faces cascading challenges:
- **Immediate:** Do your backups still contain the attacker's artifacts? Are they still present in your live systems?
- **Hours 1-2:** Can you continue operations without this critical vendor?
- **Hours 2-4:** What do you tell your patients? What do regulators require?
- **Ongoing:** What recourse do you have against the vendor?

### Learning Objectives

Participants will:
1. Practice rapid decision-making when information is incomplete
2. Balance operational continuity with security isolation
3. Understand regulatory notification timelines and requirements (HIPAA)
4. Develop vendor communication strategies during crisis
5. Recognize when to escalate to external partners (legal, law enforcement, regulators)

### Participant Roles (Assign one per person or share roles)

- **Clinical Operations Lead** - Responsible for patient care continuity
- **IT Security Director** - Leads technical investigation
- **Compliance Officer** - Manages regulatory obligations
- **Chief Financial Officer** - Handles insurance, legal costs, vendor contracts
- **CEO/Executive Lead** - Final decision authority, board/regulatory communications
- **Vendor Relationship Manager** - Direct contact with CloudMed Secure
- **Clinical Director** - Patient privacy advocate, clinical system expertise
- **General Participant** - Observer/consultant role, asks clarifying questions

### Exercise Logistics

**Duration:** 4 hours (including breaks)
- Phase 1 (0-30 min): Scenario briefing, initial response, discovery
- Phase 2 (30-90 min): Investigation decisions, vendor communication
- Phase 3 (90-150 min): Patient notification, regulatory engagement
- Phase 4 (150-240 min): Recovery planning, debrief

**Facilitation Approach:**
- Early phases allow discussion and exploration of options
- Middle/late phases introduce time pressure and cascading complications
- Facilitator tracks decisions but allows team to debate approaches
- Light scoring (informative, not competitive) on decision quality

**Materials Needed:**
- Printed scenario briefing for each participant
- Whiteboard/flip chart for decision tracking
- Timer for response windows (visible to team)
- Injection cards (printed or read aloud by facilitator)
- Complication deck for mid-exercise disruptions

---

<!-- EXPORT MARKER: FACILITATOR-GUIDE START -->

## FACILITATOR GUIDE

### Pre-Exercise Setup (30 minutes before start)

1. **Arrange the room:** Theater style or U-shape with clear view of facilitator
2. **Assign roles:** Distribute role cards; allow participants to self-select if willing
3. **Set expectations:** Explain blended format—early discussion, later time pressure
4. **Review scenario:** Brief facilitator on key decision points and complications
5. **Test materials:** Ensure timer, injection delivery method, and tracking sheets work

### Facilitation Philosophy for Blended Format

**Phase 1 (0-30 min) - Discovery & Learning Focus:**
- Slow inject pace; facilitate deep discussion
- Answer questions openly; allow exploration of options
- Goal: Build shared understanding of crisis scope

**Phase 2 (30-90 min) - Moderate Pressure:**
- Tighter inject schedules (10-15 min response windows)
- Begin introducing time constraints
- Complications start appearing; team must adjust
- Goal: Test decision-making under realistic pressure

**Phase 3 (90-150 min) - High Pressure:**
- Rapid injects (5-10 min response windows)
- Cascading complications simulate real chaos
- Facilitator allows minimal discussion; decisions must be made quickly
- Goal: Stress-test team coordination and crisis management

**Phase 4 (150-240 min) - Debrief & Reflection:**
- Slow pace returns; review decisions and outcomes
- Facilitator guides discussion on what worked/didn't work
- Connect exercise decisions to real-world policies and procedures
- Goal: Extract learning and identify systemic improvements

### Key Facilitation Moves

**When participants are stuck:** Ask Socratic questions rather than providing answers
- "What information do you need before deciding?"
- "Who needs to be in this decision?"
- "What happens if you choose X vs. Y?"

**When participants are moving too fast:** Slow them down
- "Before we move forward, let's make sure everyone understands why we chose that approach"
- "What's our confidence level in that decision?"

**When discussion goes off-track:** Redirect gently
- "That's an interesting question, but let's table it for debrief. Right now, we need to decide about X"

**When delivering complications:** Present as real injects, not facilitator commentary
- Read complication as if from an external source (call, email alert, message)
- Allow team time to react before explaining implications
- Track how they respond and adjust subsequent injects based on their decisions

---

## SCENARIO NARRATIVE (Detailed Version for Facilitator)

### The Incident Timeline

**Week 1-6 (6 weeks ago - unknown to organization):**
- Threat actor targets CloudMed Secure (not your organization specifically)
- Attacker uses spear-phishing against CloudMed's support engineer, obtains credentials
- Attacker gains access to CloudMed's customer portal and backup infrastructure
- Attacker maintains low-profile presence, avoids detection, begins data exfiltration

**Today (T+0):**
- CloudMed Secure discovers breach during incident response (triggered by external security researcher report)
- CloudMed notifies your organization by email: "We experienced an unauthorized access incident affecting customer backup data. We are investigating and will provide more details shortly."
- Your IT team receives the notification; begins escalation

### Critical Context for Facilitator

**Your organization's relationship with CloudMed Secure:**
- 3-year relationship; CloudMed holds ALL patient backups (electronic health records, imaging data, lab results)
- Backup data = 8.5 million medical records (350GB of data)
- CloudMed is your ONLY backup solution; no redundant backup provider exists
- Your organization depends on CloudMed for disaster recovery and regulatory compliance (HIPAA requires backup retention)
- CloudMed Secure has NO cyber insurance (this becomes important later)

**What the attacker accessed:**
- Patient names, dates of birth, medical record numbers
- Diagnoses, medications, medical history for 347 of your patients (not all patients, subset)
- No credit card data or social security numbers (patient financial data stored separately on-premises)
- Attacker had access for 6 weeks; unclear what exactly was exfiltrated

**What participants DON'T know yet (revealed through injects):**
- Whether attacker still has access to your live systems
- Whether attacker had persistence mechanisms (backdoors) in your environment
- Exact scope of patient data compromised
- Whether attacker will publish/sell the data
- What CloudMed is doing to remediate and secure systems

**Regulatory context (key for healthcare):**
- HIPAA Breach Notification Rule: notify affected individuals "without unreasonable delay" (generally interpreted as 30-60 days)
- HIPAA requires notification to HHS, FBI, and media if breach affects >500 residents
- Your state also has separate breach notification laws (typically 30 days)
- State's healthcare authority (Department of Health or similar) requires incident reporting for any breach involving ≥5 patient records
- Cyber insurance carrier requires prompt notification and may deny coverage if you delay reporting

---

<!-- EXPORT MARKER: SCENARIO-NARRATIVE END -->

---

<!-- EXPORT MARKER: INJECT-TIMELINE START -->

## INJECT TIMELINE & DELIVERY SCHEDULE

**Blended Format:** 4-hour exercise | 17 injects total | Paced 10-15 min early, 5-10 min later

| Timing | Inject # | Delivery | Content Summary | Expected Response | Facilitator Notes |
|--------|----------|----------|-----------------|-------------------|------------------|
| T+0 | INJ-1 | Email alert + verbal | CloudMed Secure breach notification received | Escalate to leadership; call incident response meeting | Scene-setting; allow 5 min discussion of initial reaction |
| T+5 | INJ-2 | Conference call (facilitator role-plays) | CloudMed CSO provides initial details: breach confirmed, 6-week access window, scope TBD | Participants request information from CloudMed; begin assessing internal systems | **Decision Point 1 Trigger**: Ask team what they need to know first |
| T+15 | INJ-3 | Email (read aloud) | Internal IT reports: CloudMed access credentials found in use logs; unclear if attacker still has access | Team must decide: aggressive credential rotation vs. targeted rotation | Allow 10 min discussion; this is Phase 1 (learning-focused) |
| T+25 | INJ-4 | Security alert popup (verbal) | Firewall logs show unusual outbound connection to CloudMed infrastructure from clinical workstation at 3:47 AM this morning | **Complication 1**: Suggests possible persistence mechanism in your environment | Facilitator asks: "What does this mean? What's your next step?" |
| T+35 | INJ-5 | Call from CFO (facilitator) | "We just got a call from our cyber insurance carrier. They want us to start formal incident response immediately. They need hourly updates and expect us to have forensics completed by end of week. They also said CloudMed's policy doesn't cover customer breaches—only their own costs." | Team realizes vendor cannot help with costs; insurance pressure mounting | **Complication 2**: Deadline pressure added; team must prioritize |
| T+45 | INJ-6 | Email from legal counsel | "I've reviewed our contract with CloudMed. Section 7.3 requires them to notify us within 24 hours of discovering a breach affecting customer data. They notified us 6 hours after discovering the breach internally. That's a violation. Also, there's no liability cap for customer data breaches—only their infrastructure costs. We may have a lawsuit." | Team realizes CloudMed is contractually liable; legal action possible | Introduce decision point about vendor cooperation vs. legal action |
| T+55 | **DP-1** | Facilitator prompt | **Decision Point 1: Credential & System Isolation Strategy** - How aggressively do you isolate? What's your timeline? | Team chooses Aggressive, Targeted, or Monitoring approach | **CRITICAL**: This is blended format, so allow 15 min of discussion. Capture the decision; track it for debrief. |
| T+70 | INJ-7 | Email (read aloud) | "CloudMed forensics team reports: Attacker used stolen credentials to access customer backup portal starting 2024-11-15 at 2:34 AM UTC. Last login detected 2025-01-09 at 11:22 PM UTC. That's... 12 hours ago." | Team realizes attacker may have accessed data as recently as yesterday | This validates the alarm from INJ-4; heightens urgency |
| T+80 | INJ-8 | Call from Compliance Officer (internal) | "I just finished the regulatory assessment. If we don't notify HHS within 60 days, we're looking at fines. If we don't notify patients within state deadline (30 days), additional fines. We need to decide on notification scope ASAP. Do we notify all 8.5 million patients or just the 347 in the confirmed sample?" | Team realizes notification is mandatory; scope decision is complex | **Decision Point 2 Trigger**: When do you notify? How many patients? |
| T+90 | **DP-2** | Facilitator prompt | **Decision Point 2: Investigation & Scope Approach** - Do you hire external forensics? How long can you wait for findings? When do you notify patients? | Team chooses internal investigation, external forensics, or hybrid | Allow 12 min of discussion; time pressure starting to increase |
| T+105 | INJ-9 | News alert (email) | "A patient at your organization just posted on social media: 'My medical records were on the news because of CloudMed breach. Why didn't my doctor tell me? #HealthDataBreach'" | **Complication 3**: Customer self-discovery of breach before official notification | Team realizes they're losing narrative control; must accelerate notification |
| T+115 | INJ-10 | Call from CEO's admin | "The board is meeting today at 4 PM. They want a briefing on the incident. What do you want me to tell them?" | Team prepares talking points; realizes board/stakeholder management is critical | Allow 8 min to draft key messages |
| T+125 | INJ-11 | Email from CloudMed CEO | "We're taking full responsibility for the breach. We will cover notification costs for affected patients, engage a national call center for patient questions, and hire the top forensics firm in the country. However, we need your organization to make the first public statement. We recommend immediate notification to all customers: 'Your data may have been accessed.'" | **Complication 4**: Vendor pushing aggressive notification; changing cost responsibility | Team must decide: follow vendor's recommendation or conduct independent assessment? |
| T+135 | INJ-12 | Forensics email (from external firm, if chosen) | "Preliminary findings: Attacker accessed backup records for 347 specific patients (highly selective access pattern—suggests targeting). No evidence of lateral movement to your live production systems. No backdoors found. Attacker exfiltrated patient names, DOBs, and diagnoses to external server. Ransomware deployment tools were in attacker's toolkit but NOT executed. Full report in 48 hours." | **Positive complication**: Scope is smaller than feared, but exfiltration confirmed | Reduces panic; allows more measured notification approach |
| T+150 | **DP-3** | Facilitator prompt | **Decision Point 3: Patient Notification Strategy** - Notify immediately? Notify selectively (347 only)? Dual notification (all + detailed notice to 347)? | Team chooses notification approach based on investigation findings | **CRITICAL**: Time pressure HIGH; allow only 8 min discussion. Emphasize this is a binding decision affecting 8.5M patients or 347 patients. |
| T+160 | INJ-13 | Call from state health department | "We received a report of a breach involving >5 patient records. We're opening an investigation. We need copies of your incident response plan, notification templates, and forensics findings within 5 business days. Your organization may face penalties if we determine you violated notification timelines." | **Complication 5**: Regulatory investigation formal; adds compliance pressure | Team realizes they may face fines regardless of actions taken; emphasizes importance of documentation |
| T+175 | INJ-14 | Email from FBI (Cyber Division) | "Your organization's data was identified in a data broker's inventory. Attacker is offering patient records from your breach for sale on dark web marketplace. Price: $15,000 for full dataset. Our preliminary assessment: this attacker is a sophisticated Eastern European criminal group. We're opening a formal investigation and recommend your organization participate in information sharing." | **Complication 6**: Data publication confirmed; law enforcement involvement | Team must decide: cooperate with FBI? Offer reward for attacker information? |
| T+190 | INJ-15 | Call from Board Chair | "The board has reviewed your briefing. They're supportive of your response, but they want to know: Are we going to sue CloudMed? What's our timeline for recovery? What's the financial impact?" | Team must present decision on legal action, costs, recovery planning | Prepare legal/financial summary; this is decision point 4 |
| T+210 | **DP-4** | Facilitator prompt | **Decision Point 4: Vendor Accountability & Legal Strategy** - Sue CloudMed? Cooperate to recover data faster? Demand payment for notification costs? | Team chooses legal strategy based on contract review and investigation findings | Allow 8 min of discussion; emphasize this is binding and affects vendor relationship |
| T+225 | INJ-16 | Internal IT report (email) | "We've completed the system access review. Confirmed: Attacker never accessed your live EHR systems. All compromised data was in CloudMed backups. Your live systems remain secure. We recommend maintaining backup isolation (disconnecting from production) for 30 days as a precaution, then gradually restoring services." | **Relief inject**: Validates containment strategy; clarifies scope | Team should feel some weight lifting; provides path to recovery |
| T+240 | INJ-17 | Facilitator closing | Exercise complete. No new injects. Begin debrief. | Team reflects on decisions and outcomes | Transition to debrief phase |

---

<!-- EXPORT MARKER: INJECT-TIMELINE END -->

---

<!-- EXPORT MARKER: DECISION-POINTS START -->

## DECISION POINT FACILITATION GUIDE

### Decision Point 1: Credential & System Isolation Strategy
**Timing:** T+55 (Phase 1, learning-focused) | **Duration:** 15 minutes discussion + decision

**The Dilemma:**
You know the attacker used CloudMed credentials to access backups, but you don't know if they accessed your live systems. Do you aggressively rotate ALL credentials (operational disruption) or take a targeted approach (incomplete protection)?

**Three Options:**

**Option A: Aggressive Isolation (Defensive/Safe)**
- Immediately disconnect all systems from CloudMed backups
- Force password resets for all user accounts
- Block all outbound connections to third-party vendors for 24 hours
- Conduct full forensics before restoring services
- **Timeline:** 3-5 days to full restoration
- **Impact:** Clinical operations severely disrupted; patient appointments delayed
- **Benefit:** Maximum assurance of attacker removal
- **Indicator of good decision-making:** Team recognizes this may be overkill but chooses it to be safe; discusses impact with clinical team

**Option B: Targeted Containment (Balanced)**
- Rotate only credentials with access to CloudMed and sensitive systems
- Enhance monitoring of lateral movement indicators
- Establish forensics investigation while maintaining partial operations
- **Timeline:** 1-2 days to establish baseline; forensics ongoing
- **Impact:** Moderate operational impact; some systems isolated but critical services continue
- **Benefit:** Balance of security and continuity
- **Indicator of good decision-making:** Team articulates specific targets for isolation; explains monitoring strategy

**Option C: Monitor & Wait (Risk-Tolerant)**
- Increase monitoring; gather evidence before acting
- Wait for CloudMed forensics findings before isolating
- Assume attacker is already gone (6 weeks + passive monitoring unlikely)
- **Timeline:** 24-48 hours before deciding on isolation scope
- **Impact:** Minimal operational impact; continued risk if attacker remains
- **Benefit:** Operational continuity maintained
- **Indicator of good decision-making:** Team acknowledges risk; explains why monitoring is sufficient

**Socratic Questions for Facilitator:**
1. "What would it take for you to be confident the attacker is gone?"
2. "Who needs to be in this decision? What does the clinical director say about operational impact?"
3. "If you choose targeted isolation, how will you know if the attacker moved laterally?"
4. "What's your tolerance for operational disruption vs. security assurance?"

**Evaluation Checkboxes:**
- [ ] Team articulated specific isolation targets
- [ ] Team discussed operational impact with clinical stakeholders
- [ ] Team explained monitoring or forensics strategy
- [ ] Decision authority was clear (CTO/CEO/Security)
- [ ] Team acknowledged timeline tradeoffs
- [ ] Team discussed how they'd know if isolation was insufficient

**Expected Responses by Experience Level:**
- **Beginner:** Often choose aggressive (safest); may not consider operational impact
- **Intermediate:** Weigh options carefully; lean toward targeted + monitoring
- **Advanced:** Ask specific technical questions; design monitoring strategy

**Facilitation Notes:**
- This decision is **reversible** (can escalate to aggressive later if evidence emerges)
- Clinical director's input should be weighted heavily
- If team is struggling, ask: "What's the minimum you must do TODAY vs. what you can do over next 48 hours?"

---

### Decision Point 2: Investigation & Forensics Scope
**Timing:** T+90 (Phase 2, moderate pressure) | **Duration:** 12 minutes discussion + decision

**The Dilemma:**
You need to know exactly what the attacker accessed, but you can't wait weeks for forensics. Internal investigation is fast but shallow. External forensics is thorough but slow. Do you do both, or choose one?

**Three Options:**

**Option A: Internal Investigation Only (Fast/Risky)**
- Your IT team conducts forensics on your own systems
- You contact CloudMed; ask them for their findings
- You complete investigation in 3-5 days
- **Benefit:** Fast answers; lower cost (~$5K)
- **Risk:** Shallow findings; may miss persistence mechanisms or lateral movement
- **Regulatory perception:** "We tried to investigate ourselves" = weaker response
- **Indicator of good decision-making:** Team acknowledges they're accepting incomplete findings; articulates why speed matters more

**Option B: External Forensics Only (Thorough/Slow)**
- Hire Big 4 forensics firm (Deloitte, EY, KPMG) to investigate both your systems and coordinate with CloudMed
- Complete forensics in 10-14 days
- **Benefit:** Thorough, defensible findings; stronger for regulatory and legal purposes
- **Cost:** $50K-$100K
- **Risk:** Slow answers; longer notification delay; patient calls pile up
- **Indicator of good decision-making:** Team acknowledges delay impacts notification timeline; discusses notification messaging during investigation

**Option C: Hybrid Approach (Balanced)**
- Internal team begins immediate triage (Day 1-2) to establish baseline
- Hire external forensics in parallel (Day 2)
- Internal team provides quick answers for notifications; external team provides detailed findings for regulatory
- **Timeline:** Quick answers in 48 hours; full forensics in 7-10 days
- **Cost:** $30K-$50K (shared scope between internal/external)
- **Benefit:** Speed + Thoroughness
- **Indicator of good decision-making:** Team explains what questions they need answered TODAY vs. LATER

**Socratic Questions for Facilitator:**
1. "When do you need answers to know whether to notify patients?"
2. "Who are you explaining this investigation to—regulators, patients, board? What level of rigor do they expect?"
3. "What are the financial tradeoffs? Cost vs. timeline?"
4. "If you choose internal investigation and it's incomplete, can you revise notifications later?"

**Evaluation Checkboxes:**
- [ ] Team articulated what questions need answering and on what timeline
- [ ] Team discussed regulatory expectations for investigation rigor
- [ ] Team weighed cost vs. timeline tradeoffs
- [ ] Team explained how incomplete findings would affect notification
- [ ] Team identified who would lead investigation (internal vs. external expertise)
- [ ] Team discussed insurance/legal requirements for investigation rigor

**Expected Responses by Experience Level:**
- **Beginner:** Often choose external (assumes "better")
- **Intermediate:** Hybrid approach most common; recognize both timelines matter
- **Advanced:** Push back on external findings timelines; question forensics firm's availability

**Facilitation Notes:**
- This decision **drives the timing** of Decision Point 3 (notification)
- If team chooses external forensics, follow up later with timeline pressure ("It's been 7 days; investigation is 50% complete but board wants answers")
- **Inject 12** reveals preliminary forensics findings (if external path chosen) or requires team to make notification decision with incomplete data (if internal path chosen)

---

### Decision Point 3: Patient Notification Strategy
**Timing:** T+150 (Phase 3, high pressure) | **Duration:** 8 minutes discussion + BINDING DECISION

**The Dilemma:**
Your investigation shows 347 patients were specifically targeted, but 8.5 million patients' backups were accessible. Do you notify just the 347 (accurate but incomplete) or all 8.5 million (defensive but alarmist)?

**Three Options:**

**Option A: Selective Notification (Accurate/Risky)**
- Notify only the 347 patients with confirmed compromised records
- Explain in detail: what data, what the attacker likely saw, what you're doing
- Recommend credit monitoring or identity theft insurance for those 347 only
- **Benefit:** Accurate, measured; avoids panic among unaffected patients
- **Risk:** If investigation incomplete and other patients' data WAS accessed, you failed to notify them; regulatory violation
- **Regulatory risk:** HIPAA may require broader notification if evidence suggests scope uncertainty
- **Indicator of good decision-making:** Team acknowledges uncertainty; explains why they're confident scope is limited

**Option B: Broad Notification (Defensive/Alarmist)**
- Notify all 8.5 million patients: "Your medical records backup may have been accessed"
- Explain attacker accessed CloudMed, but specific impact TBD
- Offer identity theft protection to all
- **Benefit:** Covers you completely; no risk of "we didn't tell you"
- **Cost:** $2-3 million in notification + identity theft insurance
- **Risk:** Massive panic; media coverage; patient calls; reputation damage
- **Regulatory perception:** "Excessive but safe"
- **Indicator of good decision-making:** Team acknowledges overkill; justifies cost as insurance against uncertainty

**Option C: Phased Notification (Balanced)**
- Immediate notice to all 8.5 million: "We experienced a third-party breach; investigating scope"
- 48-72 hour follow-up: Detailed notice to 347 (confirmed impact); explanation to others (no confirmed impact, monitoring ongoing)
- Offer identity theft protection to all for 30 days; extended support to 347
- **Timeline:** Initial notice sent immediately; detailed notice after investigation completes
- **Benefit:** Transparency + measured response; demonstrates diligence
- **Cost:** $1-2 million (lower than broad notification)
- **Regulatory perception:** "Appropriate and thorough"
- **Indicator of good decision-making:** Team explains why phasing makes sense; acknowledges upfront notification cost

**Socratic Questions for Facilitator:**
1. "How confident are you in your investigation findings? What if you're wrong?"
2. "What will patients' lawyers say if we notify 347 and later find out 500 were affected?"
3. "How will media cover each option? What's the reputational impact?"
4. "What does your cyber insurance require? What does HIPAA require?"
5. "Who do you want to hear about this first—your patients or the news?"

**Evaluation Checkboxes:**
- [ ] Team articulated confidence level in investigation findings
- [ ] Team discussed regulatory requirements (HIPAA 72-hour rule, state laws)
- [ ] Team considered patient perception and reputational impact
- [ ] Team discussed cost implications with CFO
- [ ] Team explained notification messaging and who delivers it (CEO, patient advocate, doctor)
- [ ] Team discussed how to handle media inquiries

**Expected Responses by Experience Level:**
- **Beginner:** Often choose broad notification (safest)
- **Intermediate:** Push for data; want to notify selectively if evidence supports
- **Advanced:** Ask about investigation confidence intervals; request detailed forensics before deciding

**Facilitation Notes:**
- **CRITICAL**: This decision is **binding** and affects 8.5M patients or 347 patients
- Time pressure should be HIGH; allow only 8 minutes for discussion
- Decision must be documented (who decided, when, what information they had)
- **Inject 14** reveals data is being sold on dark web; team must be prepared to discuss this in notifications
- If team hasn't done forensics (chose internal investigation), they must make this decision with uncertainty; this tests risk tolerance

---

### Decision Point 4: Vendor Accountability & Legal Strategy
**Timing:** T+210 (Phase 4, moderate pressure) | **Duration:** 8 minutes discussion + decision

**The Dilemma:**
CloudMed was contractually required to notify you within 24 hours. They notified you 6 hours late (a violation). Their insurance doesn't cover customer breaches. Do you sue, cooperate, or negotiate?

**Three Options:**

**Option A: Aggressive Legal Action (Punitive)**
- Hire outside counsel; file breach of contract lawsuit
- Pursue damages for notification costs, remediation costs, reputational harm
- Demand CloudMed pay for all patient notifications, credit monitoring, regulatory fines
- **Benefit:** CloudMed pays; full cost recovery
- **Risk:** CloudMed declares bankruptcy (they have no cyber insurance); you get nothing
- **Timeline:** 1-2 years to resolution
- **Relationship impact:** Destroys relationship; CloudMed stops cooperating with investigation
- **Indicator of good decision-making:** Team acknowledges they're choosing principle over dollars; understands bankruptcy risk

**Option B: Cooperative Recovery (Pragmatic)**
- Demand CloudMed pay for forensics and notification costs (within reason)
- Allow CloudMed to cooperate fully with investigation
- Preserve relationship for potential recovery of data or future vendor contract
- Avoid litigation costs
- **Benefit:** Faster resolution; CloudMed may contribute to costs; maintains investigation cooperation
- **Risk:** May not recover full damages; CloudMed may declare bankruptcy later anyway
- **Timeline:** 30-60 days to cost settlement
- **Indicator of good decision-making:** Team weighs litigation costs vs. likelihood of recovery; chooses pragmatism

**Option C: Insurance Claim Approach (Risk-Mitigation)**
- File claim with your cyber insurance immediately
- Allow insurance to manage relationship with CloudMed's insurance
- Focus on incident response rather than litigation
- **Benefit:** Insurance handles recovery; you focus on response
- **Risk:** Insurance may deny coverage if you violated contractual timelines; deductible applies
- **Indicator of good decision-making:** Team understands insurance requirements; lets professionals handle legal

**Socratic Questions for Facilitator:**
1. "What's CloudMed's financial situation? Can they actually pay damages?"
2. "How much will litigation cost? How long will it take?"
3. "What does your insurance cover? Who negotiates with their insurance?"
4. "Is pursuing CloudMed worth the distraction and cost?"
5. "Do you want to send a message to other vendors about accountability?"

**Evaluation Checkboxes:**
- [ ] Team researched CloudMed's financial status/insurance
- [ ] Team calculated litigation costs and recovery timeline
- [ ] Team consulted legal counsel on contract violation severity
- [ ] Team discussed insurance deductible and coverage limits
- [ ] Team weighed litigation costs vs. likely recovery
- [ ] Team considered impact on incident investigation cooperation

**Expected Responses by Experience Level:**
- **Beginner:** Often choose litigation (assumes "we should sue")
- **Intermediate:** Ask about CloudMed's finances; lean toward cooperative + insurance claim
- **Advanced:** Immediately focus on whether CloudMed is solvent; push for early settlement before bankruptcy filing

**Facilitation Notes:**
- This decision is **long-term** (impacts next 1-2 years) but doesn't need to be made in the next 24 hours
- Team can choose to defer this decision until investigation completes
- **Inject 15** includes board pressure to decide; use this to force closure
- If team chooses litigation, ask in debrief: "You'll spend $200K on lawyers over 2 years. Will you recover it?"

---

<!-- EXPORT MARKER: DECISION-POINTS END -->

---

<!-- EXPORT MARKER: COMPLICATIONS START -->

## COMPLICATIONS SEQUENCE

Complications are disruptions that escalate difficulty and force team to re-evaluate decisions. Blended exercises include 3-4 complications strategically timed to maintain engagement.

### Complication 1: Persistence Indicator (T+25)
**Inject:** Firewall logs show outbound connection to CloudMed infrastructure from clinical workstation at 3:47 AM this morning

**Trigger:** This complication is always delivered; validates urgency

**Impact:**
- Suggests attacker may have planted a backdoor or persistence mechanism in your network
- Forces team to escalate isolation strategy (may require aggressive approach)
- Increases urgency of forensics investigation

**Facilitation:**
- Present as security alert; let team react
- Ask: "What does this connection mean? Is the attacker still here?"
- Allow 5-10 minutes of discussion before moving forward
- **Do not reveal** whether this is false alarm or genuine persistence (keep team in uncertainty)

---

### Complication 2: Insurance Deadline Pressure (T+35)
**Inject:** Call from cyber insurance carrier with hourly update requirements and deadline pressure

**Trigger:** Always delivered; creates time pressure and cost awareness

**Impact:**
- Insurance carrier is now involved; they have financial stake in your decisions
- Hourly reporting requirements create administrative burden
- End-of-week forensics deadline creates artificial urgency
- Team realizes they're not alone in this decision; external parties are watching

**Facilitation:**
- Role-play as insurance adjuster; read tone of financial pressure
- After delivering, ask: "How does this change your priority?"
- Allows team to discuss time pressure explicitly
- **Expected outcome:** Team accelerates investigation and decision timelines

---

### Complication 3: Customer Self-Discovery (T+105)
**Inject:** Patient posts on social media about breach before official notification

**Trigger:** Always delivered at T+105; creates narrative control problem

**Impact:**
- Organization is losing control of the story
- Must make notification decision NOW (can't wait for investigation to complete)
- Media may pick up social media post; story goes public before official statement
- Validates why communication strategy matters

**Facilitation:**
- Present as news alert; read real quote from social media post
- Ask: "What do you do right now?"
- Allow 5-10 minutes of discussion on communication response
- This complication validates Decision Point 3 (notification strategy) timing

---

### Complication 4: Vendor Narrative Shift (T+125)
**Inject:** CloudMed CEO offers to cover notification costs; urges aggressive notification to all customers

**Trigger:** Delivered if team has NOT yet made notification decision

**Impact:**
- Vendor is now trying to influence your notification strategy
- Covering costs sounds good but may bias your decision-making
- Creates conflict: your independent judgment vs. vendor's interests
- Forces team to decide independently

**Facilitation:**
- Role-play as CloudMed CEO; convey urgency and responsibility-taking
- After delivering, ask: "Does this change your notification approach? Why or why not?"
- Highlight that vendor's interests may not align with yours
- **Expected outcome:** Team makes independent notification decision, doesn't just follow vendor's lead

---

### Complication 5: Regulatory Investigation (T+160)
**Inject:** State health department opens formal investigation; demands documentation in 5 days

**Trigger:** Delivered after notification decision; adds compliance pressure

**Impact:**
- Formal regulatory investigation adds legal/compliance burden
- Regulators can impose fines regardless of your actions
- Documentation requirements create additional work
- Emphasizes that breaches = regulatory response

**Facilitation:**
- Present as official phone call from state health department; convey bureaucratic tone
- Ask: "What documents do you need to prepare? Who owns this?"
- Allow 5-10 minutes to discuss compliance response
- This complication validates importance of detailed documentation

---

### Complication 6: Data Publication Confirmation (T+175)
**Inject:** FBI informs you attacker is selling patient data on dark web

**Trigger:** Delivered after forensics/notification decisions; confirms worst-case scenario

**Impact:**
- Confirms attacker's intent (money, not ransom)
- Data is now permanently compromised (can't be recovered)
- Opens new investigation thread (law enforcement involvement)
- Validates why forensics thoroughness mattered
- Requires decision on FBI cooperation

**Facilitation:**
- Present as official FBI notification; convey gravity
- This complication arrives AFTER notification, so it validates patient notification strategy
- Ask: "Does this change anything? What do you tell patients?"
- Allow 5-10 minutes of discussion on law enforcement involvement

---

### Complication Summary Table

| Complication | Timing | Type | Impact | Response Required |
|-------------|--------|------|--------|-------------------|
| Persistence Indicator | T+25 | Technical/Urgency | Suggests attacker still present | Escalate isolation if needed |
| Insurance Deadline | T+35 | Business/Time Pressure | Hourly reporting, end-of-week deadline | Accelerate investigation |
| Customer Self-Discovery | T+105 | Reputational/Control | Patient posts breach before notification | Rapid communication decision |
| Vendor Narrative Shift | T+125 | Strategic/Influence | Vendor offers cost coverage; urges action | Independent decision-making |
| Regulatory Investigation | T+160 | Compliance/Pressure | State opens formal investigation | Documentation + remediation response |
| Data Publication | T+175 | Confirmation/Legal | Data confirmed on dark web | FBI cooperation decision |

---

<!-- EXPORT MARKER: COMPLICATIONS END -->

---

<!-- EXPORT MARKER: DEBRIEF-TEMPLATE START -->

## DEBRIEF STRUCTURE (30-45 minutes)

The debrief is where learning happens. Use this structure to guide reflection.

### Phase 1: Decision Review (15 minutes)

**Facilitator facilitates; no right/wrong answers**

Review each critical decision in order:

**Decision Point 1: Isolation Strategy**
- "Walk us through that decision. What information drove your choice?"
- "If you could redo it, would you? Why or why not?"
- "What did you learn about the tradeoff between security and operations?"

**Decision Point 2: Investigation Scope**
- "You chose [Internal/External/Hybrid]. Why did that seem right at the time?"
- "How long was the investigation? Did timeline match your expectations?"
- "What would you do differently if this happened again?"

**Decision Point 3: Patient Notification**
- "Your decision affected [347/8.5M] patients. Was that right?"
- "How did the complications (social media post, regulatory pressure) affect your thinking?"
- "Looking back, what information would have made you more confident?"

**Decision Point 4: Vendor Accountability**
- "You chose to [sue/cooperate/insure]. What was the business logic?"
- "If CloudMed went bankrupt, how would that affect your recovery?"

### Phase 2: Competency Assessment (15 minutes)

**Evaluator discusses observations on seven core competencies:**

1. **Vendor Due Diligence**
   - "Did you understand CloudMed's access scope BEFORE the breach?"
   - "Should you have required redundant backups earlier?"
   - Insight: Third-party risk must be managed continuously, not just at contract signing

2. **Rapid Incident Triage**
   - "How quickly did you determine scope? What slowed you down?"
   - "Did you prioritize learning what you needed vs. learning everything?"
   - Insight: 80/20 rule—focus on critical questions first

3. **Operational Continuity**
   - "How did you balance security isolation with patient care?"
   - "What was your backup plan if isolation took longer than expected?"
   - Insight: Healthcare uniquely values continuity; build this into vendor strategy

4. **Vendor Communication**
   - "How did you interact with CloudMed? Did they cooperate?"
   - "What contract language would have improved outcomes?"
   - Insight: Vendors often have competing incentives; manage this proactively

5. **Customer Transparency**
   - "When you notified patients, what was their reaction?"
   - "Did your messaging reassure or alarm them?"
   - Insight: Transparency + specificity = trust; vague notifications = distrust

6. **Regulatory Response**
   - "Did you understand HIPAA requirements? State deadlines?"
   - "When did you involve regulators? Should it have been earlier/later?"
   - Insight: Regulators prefer proactive engagement; hiding extends investigations

7. **Contract Enforcement**
   - "Did you know CloudMed had a 24-hour notification clause?"
   - "Would you have discovered the breach earlier if you'd required CISO-level notifications?"
   - Insight: Contract language must be specific and monitored

### Phase 3: Systemic Improvements (15 minutes)

**Facilitator guides group to extract lessons and translate to policy:**

"Based on this exercise, what are we going to change in how we manage third-party risk?"

**For your organization specifically:**

- **Vendor Continuity Planning**
  - Do we have documented procedures for disconnecting a critical vendor?
  - Do we test backup restoration procedures quarterly?
  - Do we have redundancy for any critical third-party service?

- **Incident Response Plan Updates**
  - Does our IR plan specifically address third-party breach scenarios?
  - Do we have pre-identified forensics firms we can hire within hours?
  - Do we have notification templates that comply with HIPAA/state law?

- **Vendor Contracts**
  - Do our contracts require 24-hour breach notification?
  - Do we require vendors to maintain cyber insurance?
  - Do we have right-to-audit clauses for critical vendors?

- **Communication & Training**
  - Do clinical staff know what to do if they notice unusual network activity?
  - Does leadership understand third-party risk implications?
  - Do we practice incident response at least annually?

- **Regulatory Relationships**
  - Have we identified our state's breach notification requirements?
  - Do we know who to contact at the state health department if a breach occurs?
  - Should we brief the FBI/CISA on our critical vendors?

### Phase 4: Closing Reflection (5 minutes)

**Facilitator closes with big-picture insights:**

"This exercise showed us that when a vendor is compromised, we can't just wait for them to fix it. We have to act independently: isolate, investigate, notify, and recover. The decisions we make in the first 24-48 hours determine whether this becomes a manageable incident or a crisis.

Your executive team handled this well. You asked the right questions, involved the right people, and made decisions despite incomplete information. In a real breach, that's exactly what we need.

Are there any final questions or concerns?"

---

<!-- EXPORT MARKER: DEBRIEF-TEMPLATE END -->

---

<!-- EXPORT MARKER: PARTICIPANT-BRIEF START -->

## PARTICIPANT MATERIALS

### Welcome Letter

**From:** Exercise Facilitator
**To:** All Participants
**Subject:** Third-Party Vendor Compromise Tabletop Exercise
**Date:** [Exercise Date]

---

Dear Colleagues,

Thank you for participating in today's incident response tabletop exercise. This is a learning opportunity—not a test of your current knowledge, but a chance to strengthen our organization's response to a real and growing threat.

**What This Exercise Is:**
- A realistic simulation of a cybersecurity incident involving one of our critical vendors
- An opportunity to practice decision-making under pressure and incomplete information
- A chance to improve our incident response plan, vendor management, and communication procedures

**What This Exercise Is NOT:**
- A test of individuals (we're evaluating team decisions, not performance)
- A prediction of what will actually happen (real incidents are more chaotic)
- An evaluation of your department or role

**Ground Rules:**
1. **Stay in character** - Treat the scenario as real; respond as you would in an actual incident
2. **Make decisions with available information** - You won't have perfect data; make the best choice you can
3. **Speak up** - Ask questions, challenge assumptions, voice concerns
4. **Focus on process** - We care about HOW you decide, not whether you make the "right" choice
5. **Respect confidentiality** - Exercise details stay in this room

**How This Works:**
- You'll receive scenario briefing and detailed incident information
- The facilitator will inject new information every 5-15 minutes
- You'll make key decisions at critical moments
- We'll track decisions and outcomes; discuss them in debrief

**Your Roles:**
You've been assigned a role in the organization (CEO, IT Director, Compliance Officer, etc.). The role card explains your responsibilities and what information you have access to. Feel free to reference your role card during the exercise.

**Duration:** 4 hours (including breaks)
- Scenario & briefing: 15 min
- Exercise: 3.5 hours
- Debrief: 15-30 min

**Questions Before We Start?**

Let's begin!

---

### Scenario Briefing (Distributed at Exercise Start)

**SCENARIO: Third-Party Vendor Compromise**

**Your Organization:**
- [Name] Healthcare System
- Small provider (150 employees, 8 clinical locations)
- Serves [County/Region] area
- Critically dependent on cloud-based backup service

**The Incident:**
This morning, you received notification that CloudMed Secure (your backup vendor) was breached by an advanced threat actor. The attacker had access to CloudMed's systems for 6 weeks and may have accessed your patient data.

**What You Know Right Now:**
- CloudMed Secure: Compromised (definitely)
- Your patient data: Possibly accessed (unknown extent)
- Your live clinical systems: Status unclear
- Attacker identity: Unknown
- Attacker intent: Unknown
- Extent of damage: Under investigation

**What You Don't Know:**
- Did the attacker access YOUR systems or just CloudMed's?
- How many of your patients were affected?
- Did the attacker plant backdoors in your infrastructure?
- Is the attacker still present?
- What do regulators require you to do?
- What will your patients expect from you?

**Your Job Today:**
Make critical decisions about isolation, investigation, notification, and vendor accountability despite incomplete information. Your decisions will be evaluated on quality of process, not correctness of outcome.

**Key Constraints:**
- You have 4 hours to respond to an incident that would take 7-10 days in reality
- You're in constant contact with insurance, regulators, vendors, and patients
- Every decision creates consequences that ripple through the organization

**Ready?** The facilitator will begin with Inject 1.

---

<!-- EXPORT MARKER: PARTICIPANT-BRIEF END -->

---

## NEXT STEPS: Creating Professional Deliverables

### Overview

This markdown document contains everything you need to run the exercise facilitator guide, manage participant materials, and extract sections for your team. You now have multiple options for delivery and sharing:

### Option 1: Markdown Delivery (This Document)
**Use this if:** You prefer working with markdown or sharing directly with facilitators
- Facilitators print or read from this document
- Sections are easily searchable and editable
- Minimal formatting; works on any device

**How to use:**
- Print the entire document for the facilitator (recommended: 2-sided, color-coded tabs)
- Separate PARTICIPANT-BRIEF section and print for participants
- Use the INJECT-TIMELINE section as your master control for exercise pacing
- Reference DECISION-POINTS section during each decision point

### Option 2: Extract Sections Using Export Markers (Recommended for Teams)
**Use this if:** You want to share specific sections with different team members
- Export markers (HTML comments) allow you to extract sections programmatically
- Facilitators get FACILITATOR-GUIDE + INJECT-TIMELINE + DECISION-POINTS + COMPLICATIONS
- Participants get PARTICIPANT-BRIEF + SCENARIO-NARRATIVE only
- Legal/compliance gets DECISION-POINTS + DEBRIEF-TEMPLATE

**Available Sections:**
```
FACILITATOR-GUIDE: Complete facilitator instructions and notes
SCENARIO-NARRATIVE: Non-spoiler scenario description for participant preview
INJECT-TIMELINE: Full inject table (facilitator only; do not share)
DECISION-POINTS: Decision frameworks and facilitation guidance
COMPLICATIONS: Complications sequence and triggers
DEBRIEF-TEMPLATE: Post-exercise review structure
PARTICIPANT-BRIEF: Welcome letter and scenario briefing
```

**How to extract:** Search this document for `<!-- EXPORT MARKER:` and copy content between START and END markers

### Option 3: Convert to PowerPoint for Professional Delivery
**Use this if:** You want professional presentation slides for client delivery

**Recommended approach:**
1. Read the DELIVERABLE-CREATION-GUIDE at: https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/designGuides/DELIVERABLE-CREATION-GUIDE.md
2. Use this markdown as source content
3. Create PowerPoint slides for:
   - Title slide (exercise name, date, organization, duration)
   - Exercise objectives and learning outcomes
   - Participant role assignments
   - Scenario overview (do NOT include inject details)
   - Key decision point slides (one per DP with options)
   - Debrief agenda
4. Print or project slides during exercise
5. Share post-exercise with participants for reference

### For Facilitators: Pre-Exercise Checklist

Before running this exercise:

- [ ] Read the entire FACILITATOR-GUIDE (this document)
- [ ] Assign participant roles (8 roles provided; adjust if needed)
- [ ] Print PARTICIPANT-BRIEF and SCENARIO-BRIEFING for each participant
- [ ] Print INJECT-TIMELINE for yourself (reference during exercise)
- [ ] Print DECISION-POINTS section (reference during each DP)
- [ ] Test timer and alert system (how will you alert team to injects?)
- [ ] Review COMPLICATIONS section; prepare delivery method
- [ ] Brief yourself on DEBRIEF-TEMPLATE; plan 30-45 min closing discussion
- [ ] Arrange room: Theater-style or U-shape for visibility
- [ ] Have backup plan if technical delivery fails (printed injections ready)

### Customization Opportunities

This exercise is customizable to your organization:

**Organization-Specific Details (Find & Replace):**
- Replace "[Name] Healthcare System" with actual organization name
- Replace "CloudMed Secure" with an actual vendor you use
- Replace patient counts (8.5 million, 347) with realistic numbers
- Replace "[County/Region]" with actual geographic context
- Replace regulatory references (HIPAA, state laws) if operating in different jurisdiction

**Difficulty Adjustments:**
- **Easier:** Remove Complication 4 (vendor narrative shift); provide earlier forensics findings
- **Harder:** Add Complication 4 (ransomware in attacker toolkit); make forensics take longer
- **Longer (6-hour version):** Add parallel investigation thread (discover sub-vendor was also compromised)

**Time Adjustments:**
- **2-hour version:** Run Phases 1-2 only; skip Complications 4-6
- **Full-day version:** Add parallel investigation thread; include board/regulatory notification simulations

---

## Quality Validation Checklist

Before delivering this exercise to your client, verify:

### Critical Requirements (Must-Have)
- [ ] Scenario is specific to healthcare (HIPAA, patient privacy context included)
- [ ] 17 injects provided (meets 4-hour requirement of 15-20 injects)
- [ ] 4 decision points with 3 options each and facilitator guidance
- [ ] 6 complications with clear triggers and facilitation notes
- [ ] Blended format applied: early discussion (0-30 min), moderate pressure (30-90 min), high pressure (90-150 min)
- [ ] All 7 export markers present and clearly labeled
- [ ] Debrief template included with 4-phase structure
- [ ] Participant materials (welcome letter, scenario briefing) provided
- [ ] All injects include: content (300-500 words), expected responses, facilitator notes
- [ ] No placeholder text ("TBD," "TK," incomplete sections)

### Quality Requirements (Should-Have)
- [ ] Injects escalate in complexity and time pressure
- [ ] Complications are triggered by team decisions (not random)
- [ ] Facilitator notes include Socratic questions for deeper learning
- [ ] Decision point options have clear tradeoffs (no obvious "right" answer)
- [ ] Regulatory context (HIPAA, state breach notification) is accurate
- [ ] Evaluation checkboxes allow observable assessment of team competency
- [ ] Debrief structure connects decisions to systemic improvements

### Deliverable Guidance (Nice-to-Have)
- [ ] Exercise duration matches team's 4-hour availability
- [ ] Participant count (8 people) aligns with role assignments
- [ ] Organization size (small healthcare provider) reflected in scale of operations
- [ ] Regulatory readiness testing is explicit (HIPAA notifications, state requirements)
- [ ] This "Next Steps" section included for client reference

---

## Files Included in This Exercise Package

- **This markdown file:** Complete facilitator guide, injects, decision points, complications, debrief, participant materials
- **Role assignment cards:** (To be created; one card per participant with role description and information access)
- **Inject delivery cards:** (To be created; print each inject for facilitator to read aloud)
- **Timer resource:** (Optional; use phone timer or kitchen timer, visible to group)
- **Complication deck:** (Optional; print complications on cards for dramatic delivery)

---

## Final Notes for Facilitators

This is a well-designed exercise that will challenge your participants and generate real learning. A few facilitation principles to remember:

1. **Uncertainty is the point** - Don't resolve ambiguities too quickly; let team sit in discomfort
2. **Process over outcome** - Evaluate how they decided, not whether they decided correctly
3. **Listen more than talk** - Your job is to facilitate discussion, not provide answers
4. **Track decisions** - Write down each decision, who made it, and what they said; this is debrief gold
5. **Watch for silence** - When the room goes quiet, resist the urge to fill it; wait for someone to speak
6. **Validate effort** - At the end, acknowledge the difficulty of the task; real incidents are harder

**Good luck! Your team is going to learn a lot today.**

---

**Exercise Generated:** [Current Date]
**Template Version:** Third-Party Vendor Compromise | Healthcare | Blended | 4-Hour
**Customized For:** Small healthcare organization, new executive team, beginner IR maturity
**Facilitator:** [Your Name]

