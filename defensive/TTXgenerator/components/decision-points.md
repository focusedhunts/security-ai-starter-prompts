# Decision Points Library - Ransomware Scenario

**Framework for major decision points that test leadership, judgment, and coordination skills**

These are the critical moments where participants must make difficult choices with incomplete information, competing priorities, and real consequences. Each decision point is detailed with options, tradeoffs, evaluation criteria, and facilitation guidance.

---

## How to Use This Library

Each decision point includes:
- **Decision ID:** Unique identifier (DP-1, DP-2, etc.)
- **The Dilemma:** The core tension or conflict
- **Context:** What information participants have at this point
- **Options:** 2-4 choices (none perfect; all have tradeoffs)
- **Option Analysis:** For each option, include pros/cons/implications
- **Decision Authority:** Who actually decides (key insight often missing)
- **Expected Responses:** What different groups typically choose
- **Evaluation Criteria:** What to observe/assess
- **Facilitation Prompts:** Questions to push thinking
- **Debrief Discussion Points:** What to discuss afterward

---

## DP-1: CONTAINMENT APPROACH & TIMING

**Difficulty:** Medium-High
**When:** T+15 to T+45 (after scope confirmed, before major spread)
**Duration:** 10-20 minutes (high debate potential)
**Core Tension:** Speed of containment vs. business disruption vs. investigation needs

### The Dilemma

The ransomware is spreading. You don't know the full scope. You have three possible approaches, each with very different implications. You must decide NOW, because every hour of delay increases encryption.

**Context at this decision point:**
- You've confirmed ransomware on ~50 systems
- Spread rate is ~5-10 systems per hour (estimate)
- Backups may be compromised (still investigating)
- You don't have full picture of what attacker already accessed
- CEO wants updates in 30 minutes

---

### Option A: Aggressive Immediate Isolation

**Description:** Immediately disconnect ALL systems that touch potentially infected systems.

**Action:**
- Network team pulls network cables from file servers, key workstations
- Cloud instances are terminated
- VPN access is disabled
- Only critical communication systems remain online (phone, email to external contacts)
- Everything else goes dark until verified clean

**Timeline:** Immediate (15-30 minutes to execute)

**Pros:**
- Stops spread almost completely
- Gives forensics team time to investigate without new encryption happening
- Clear, decisive action (shows leadership)
- Limits data exfiltration possibilities
- Reduces ransom amount (less damage = less attacker leverage)

**Cons:**
- Massive operational disruption
- Business systems completely unavailable
- Customer impact is immediate and severe
- May panic employees ("Something big happened")
- May trigger media inquiry from customer calls
- Data loss during investigation (users can't save work)
- Recovery takes longer (all systems must be validated before restart)
- Staff cannot work remotely or from partially available systems

**Business Impact:**
- Revenue: $[AMOUNT] per hour of complete downtime
- Customer confidence: Significant damage if downtime extends beyond hours
- Regulatory: May trigger notifications even if no data lost (operational failure)

**Real-World Context:**
- Technically the most secure option
- Operationally, many organizations choose this reluctantly AFTER seeing rapid spread
- Some choose this proactively and feel validated later
- Some choose this and regret it (if damage wasn't as bad as feared)

---

### Option B: Selective Containment with Close Monitoring

**Description:** Isolate confirmed-affected systems; monitor others closely for spread; continue investigation.

**Action:**
- Disconnect infected file servers from network immediately
- Isolate affected departments' workstations
- Leave other departments connected but monitored heavily
- Keep cloud infrastructure online but with enhanced monitoring
- Recovery starts in parallel with investigation

**Timeline:** 30-60 minutes to implement

**Pros:**
- Maintains partial business continuity
- Allows selective remote work for unaffected departments
- Continues investigation to understand scope
- Faster recovery for unaffected systems
- Reduces customer/employee disruption
- Shows thoughtful, measured response
- May reduce business impact to manageable levels
- Allows evidence collection while systems are still running

**Cons:**
- Risk: If you misjudged scope, encryption continues in "unaffected" areas
- Requires real-time monitoring (resource-intensive)
- Data exfiltration may continue during investigation
- Recovery is messier (some systems need rebuild, others were OK)
- Participants/executives second-guess every hour ("Did we isolate enough?")
- If spread continues after decision, looks like bad judgment

**Business Impact:**
- Revenue: $[AMOUNT] per hour for affected departments (not complete loss)
- Customer impact: Some services degraded, not completely down
- Regulatory: May be defensible (proportional response to threat)

**Real-World Context:**
- Most organizations choose something like this initially
- It's a "business compromise" position
- Often regretted if scope was worse than thought
- Often validated if scope was actually contained

---

### Option C: Monitored Response - Wait and See

**Description:** Close observation for 30-60 minutes without isolation; gather intelligence on spread rate; make bigger decision armed with better information.

**Action:**
- DO NOT isolate yet
- Increase monitoring (EDR, SIEM, network traffic)
- Watch spread patterns to understand scope better
- Forensics team works in parallel to understand attack timeline
- After 30-60 minutes of data, make informed containment decision

**Timeline:** 30-60 minutes before decision, then containment begins

**Pros:**
- Gather better intelligence before acting
- No premature business disruption if threat is contained
- Can optimize containment strategy (know exactly which systems to isolate)
- Shows confidence and strategic thinking
- Buys time for CEO to prepare stakeholders

**Cons:**
- HIGH RISK: Encryption continues spreading during observation window
- If attacker is still actively spreading: You can lose 50-100+ additional systems
- Ransomware spreads FAST (can encrypt dozens of systems in 30 minutes)
- Observation window may be long enough for complete network compromise
- Data exfiltration definitely continues
- Participants often look back with regret ("Why didn't we isolate?")
- If spread is worse: You're blamed for allowing it to happen

**Business Impact:**
- Revenue: Unpredictable—ranges from minimal to catastrophic
- Customer impact: Unknown—could be manageable or devastating
- Regulatory: May look reckless to regulators (chose observation over action)

**Real-World Context:**
- Rarely chosen proactively
- Often forced by analysis paralysis
- Few organizations feel good about this choice in hindsight
- Only justified if spread actually was slow (rare in organized ransomware)
- Often represents "we didn't want to make the hard decision"

---

### Key Decision Variables

**Factors that should influence choice:**

1. **Spread rate:** If it's accelerating, Option A more justified
2. **Data criticality:** If data is customer PII, faster containment needed
3. **Business tolerance:** Can CEO accept downtime or must services stay up?
4. **Investigation maturity:** Can you understand what happened while systems run?
5. **Backup status:** If backups are compromised, slower recovery anyway (Option A less disruptive)
6. **Incident history:** If you've had ransomware before, might be faster to decide

---

### Expected Responses

**Beginner groups typically:**
- Choose Option B (seems balanced)
- Get surprised by continued spread
- Escalate to Option A mid-exercise
- Learn: "Should have decided earlier"

**Intermediate groups typically:**
- Debate between A and B (good discussion)
- May choose A if they're risk-averse
- May choose B if they're business-focused
- Both responses are defensible

**Advanced groups typically:**
- Understand implications deeply
- May choose A decisively (prepared for it)
- May choose B strategically (understand their network well)
- May choose C intentionally (have monitoring in place)
- Explain decisions clearly

**Executives typically:**
- Initially push for Option B ("We need to stay operational")
- Escalate to Option A when spread accelerates ("Just shut it down")
- Rarely proactively choose Option A
- Blame IT regardless of choice made

---

### Evaluation Criteria

**Strong response includes:**
- [ ] Clear reasoning (not just gut feel)
- [ ] Understands implications of chosen option
- [ ] Considers worst-case scenario
- [ ] Makes decision decisively (doesn't waffle)
- [ ] Communicates decision clearly to team
- [ ] Documents decision and rationale
- [ ] Prepares contingency (what if wrong?)
- [ ] Coordinates with leadership before final call

**Weak response includes:**
- [ ] No clear reasoning
- [ ] Surprised by consequences
- [ ] Second-guesses decision constantly
- [ ] Doesn't tell team/executive clearly
- [ ] No contingency plan
- [ ] Blame-shifting if consequences emerge

---

### Facilitation Prompts

**If group is deciding slowly:**
- "The encryption is continuing while you debate. Every minute costs you more systems."
- "What information would change your mind? Do you have that information?"
- "If you had to decide in 5 minutes, what would you choose?"

**If group chooses Option B:**
- "How will you know if isolation is working? What's your trigger to escalate?"
- "What happens if spread continues despite your monitoring?"
- "How will you explain to CEO that we let it spread further while we investigated?"

**If group chooses Option A:**
- "How long do you think recovery will take if you isolate now?"
- "What if your scope assessment was wrong and 80% of systems were actually unaffected?"
- "What's the worst business impact of complete downtime for [DURATION]?"

**If group chooses Option C:**
- "That's a bold choice. What happens if you're wrong?"
- "If spread accelerates in the next 30 minutes, can you pivot to isolation?"
- "How will team handle pressure from executives while you're watching?"

---

### Debrief Discussion

**After decision is made and consequences play out:**

1. **Decision Quality:** Was this a good decision given information at the time?
   - Good decisions can have bad outcomes (bad luck)
   - Bad decisions can have good outcomes (good luck)
   - Evaluate process, not just results

2. **Information Sufficiency:** Did they have enough info to decide? What was missing?

3. **Authority & Communication:** Was it clear who decided? Did team understand why?

4. **Contingency Thinking:** Did they prepare for "what if I'm wrong"?

5. **Organizational Factors:** How did business pressure influence decision?

6. **Real Incident Comparison:** "In [real ransomware incident], organization chose [Option]. Here's what happened..."

---

---

## DP-2: RANSOM PAYMENT DECISION

**Difficulty:** Very High
**When:** T+60 to T+120 (after forensics show data exfiltration)
**Duration:** 20-40 minutes (most contentious decision)
**Core Tension:** Ethical/legal principles vs. practical business necessity

### The Dilemma

The attacker has your data. You have strong evidence they exfiltrated before encryption. You can't recover all data from backups. Your CEO is asking: "Should we pay?"

**Context at this decision point:**
- Ransomware is deployed across network
- Backup recovery will take ~10 days and lose critical data
- Attacker claims they have [DATA-TYPE] worth millions
- Sample data published by attacker proves legitimacy
- Payment deadline is ~20 hours away
- Insurance covers negotiation (~$[AMOUNT]) and partial ransom
- FBI recommends strongly against payment
- Board is asking "what's our best option?"

---

### Option A: Don't Pay - Restore from Backup & Accept Data Loss

**Description:** Refuse to pay. Restore systems from backups. Accept that exfiltrated data may be published.

**Action:**
- Notify attacker: "We will not pay"
- Begin backup recovery process immediately
- Coordinate with law enforcement to investigate
- Prepare for potential data publication
- Focus on preventing future access

**Timeline:** Recovery starts immediately; takes 10-14 days

**Pros:**
- Maintains ethical principle (don't fund criminals)
- Aligns with law enforcement guidance
- Doesn't validate targeting (less likely to be targeted again)
- No payment risk (funds may not reach attacker anyway)
- Shows organizational principle and integrity
- May reduce liability (can argue you acted responsibly)
- Recovery process begins without delay

**Cons:**
- Business operations disrupted for 10-14 days
- Revenue loss during downtime: ~$[AMOUNT]
- Exfiltrated data WILL be published (attacker keeps their copy)
- Customers may see their data in dark web
- Regulatory notifications required anyway (data was exfiltrated)
- Competitive damage (if data is intellectual property)
- Employees may lose faith ("We wouldn't pay to protect our data")
- Customer trust damaged ("Data was stolen despite our security")

**Compliance & Legal:**
- Complies with FBI guidance
- May comply with regulatory requirements (depending on jurisdiction)
- Some regulations prohibit ransom payment (OFAC, government agencies)
- Shows "responsible" incident response to auditors
- May improve insurance coverage (followed guidance)

**Real-World Context:**
- Rarely chosen in practice (only 10-20% of organizations)
- Usually requires very principled leadership OR constraints that force it (OFAC, public sector)
- Most organizations regret this ONLY if recovery is faster than expected
- Some organizations regret this if data publication is truly damaging

---

### Option B: Pay the Ransom - Get Faster Recovery & Hope for Decryption

**Description:** Negotiate and pay ransom. Get decryption key. Restore systems faster.

**Action:**
- Contact insurance negotiator
- Begin negotiations with attacker (through ransom negotiation firm)
- Attempt to reduce ransom amount
- Coordinate with law enforcement (FBI must be notified)
- If negotiations successful, make payment to crypto wallet
- Receive (hopefully) decryption key
- Begin restoration process

**Timeline:** Negotiation 24-48 hours; decryption/recovery 3-5 days (if key works)

**Pros:**
- Faster recovery: 3-5 days vs. 10-14 days
- Revenue loss reduced: Saved ~$[AMOUNT] vs. longer downtime
- Decryption key may work (usually does for organized groups)
- Insurance covers most of ransom cost
- Negotiator may reduce ransom amount (30% reduction common)
- Business can resume operations sooner
- Competitive advantage recovered faster
- Employees back to work sooner

**Cons:**
- Funds criminal enterprise (ethical problem)
- No guarantee key works (some keys don't decrypt everything)
- Attacker STILL has your data (will publish anyway)
- May violate sanctions (OFAC) if attacker is from sanctioned country
- FBI will investigate the payment (may freeze assets, create hassle)
- Public relations disaster if data confirms (media headline: "Company paid hackers")
- Validates targeting (you're more likely to be targeted again)
- May violate insurance policy if ransom was negotiated incorrectly
- Attacker may demand additional payment ("Key only works on 50% of files")

**Compliance & Legal:**
- Violates FBI guidance (though FBI acknowledges many organizations do this)
- May violate OFAC if attacker is sanctioned entity
- Creates paper trail (FBI may investigate payment)
- Some insurance policies require notification of law enforcement (FBI involvement)
- May be defensible to board: "We followed insurance guidance and recovered faster"

**Real-World Context:**
- Chosen by 80% of organizations with cyber insurance
- Most organizations don't regret IF recovery is fast and data publication is limited
- Some organizations regret if key doesn't work or publication is damaging
- Organized ransomware groups generally keep their word (their reputation matters for future victims)

---

### Option C: Hybrid Approach - Begin Recovery & Negotiate in Parallel

**Description:** Start backup recovery immediately; simultaneously negotiate with attacker; pay if negotiations favorable; abandon plan if recovery is faster.

**Action:**
- Begin backup recovery process (Day 1)
- Contact insurance negotiator; begin negotiations
- Set internal deadline: If ransom not reduced to $[AMOUNT], stop negotiating
- Track recovery progress: Can we be ready before payment deadline?
- Decision point: Make final call at T+24 hours
- If ransom is good deal AND recovery is slow: Pay
- If recovery is on track AND ransom is high: Don't pay

**Timeline:** Flexible; recovery in parallel with negotiation

**Pros:**
- Maximum optionality (you can still choose either direction)
- Recovery starts immediately (not waiting for negotiation)
- Negotiation may reduce ransom (get better deal)
- More information by decision time (recovery progress known)
- Reduces panic decision-making (you have time)
- Shows strategic thinking (multiple options active)

**Cons:**
- Requires high-level coordination (multiple teams working in parallel)
- Negotiator may feel abandoned if you switch to recovery
- Recovery may be slower if team is distracted
- Negotiation may be faster if team is less committed
- Creates ambiguity: "What's our actual plan?"
- Board/CEO may be frustrated: "Just decide!"
- Insurance may be less supportive (paying if we're already recovering)

**Compliance & Legal:**
- Balanced approach (looks responsible either way)
- IF payment made: Same legal implications as Option B
- IF payment not made: Same implications as Option A
- Creates better narrative: "We explored all options before deciding"

**Real-World Context:**
- Chosen by some sophisticated organizations (those with good BC/DR)
- Requires confidence in recovery capability
- Works if recovery is actually going well
- Fails if recovery stalls (then you're forced to pay at worst time)

---

### Key Decision Variables

**Factors that should influence choice:**

1. **Insurance coverage:** What does policy cover? Required notifications?
2. **Data sensitivity:** How damaging is publication of this data?
3. **Backup capability:** How realistic is recovery timeline?
4. **OFAC risk:** Is attacker from sanctioned jurisdiction?
5. **Regulatory requirement:** Any rules against ransom?
6. **Organizational principle:** What do our values say?
7. **Business tolerance:** How long can we stay down?
8. **Reputation concern:** How important is "we didn't pay"?

---

### Decision Authority: Who Should Decide?

This is critical insight often missed:

**Who should actually make this decision:**
- CEO/Executive leadership (affects entire organization)
- Legal (may have compliance constraints)
- CFO/Finance (affects budget and insurance)
- Insurance broker (may have policy requirements)
- Board (in some organizations, for amounts >$[AMOUNT])

**Who should NOT decide alone:**
- IT/Security team (important input, but not decision-makers)
- Incident commander (execution lead, not strategist)
- Insurance company (they have conflict of interest)
- External IR firm (they may push toward their preferred approach)

**Strong process includes:**
- [ ] Executive leadership makes decision
- [ ] Legal consulted (compliance constraints)
- [ ] Insurance consulted (coverage implications)
- [ ] FBI notified (law enforcement coordination)
- [ ] Decision documented with reasoning
- [ ] Team unified behind decision (no public disagreement)

---

### Expected Responses

**Beginner groups typically:**
- Want "someone to tell us what to do"
- Panic and lean toward payment ("Just pay it and move on")
- Don't involve right decision-makers (IT decides alone)
- Don't document reasoning

**Intermediate groups typically:**
- Debate Option A vs. Option B (good discussion)
- Try to involve leadership (sometimes late in discussion)
- May choose payment if recovery looks slow
- May choose not-to-pay if recovery looks fast
- Reasonable decision either way

**Advanced groups typically:**
- Understand decision authority clearly
- Executive leadership makes clear decision
- Legal is consulted on constraints
- Decision is explained to team
- Option C (hybrid) appeals to strategic thinkers
- Decision is documented clearly

---

### Evaluation Criteria

**Strong decision-making process:**
- [ ] Right people in the room (executive, legal, finance, insurance)
- [ ] Clear decision authority (CEO decides, not IT)
- [ ] Legal constraints understood (OFAC, regulatory)
- [ ] Insurance coverage understood (what's covered, what's not)
- [ ] Recovery timeline assessed realistically (not optimistic)
- [ ] Data sensitivity understood (how damaging if published?)
- [ ] FBI involvement planned (law enforcement coordination)
- [ ] Decision documented with reasoning (not just gut feel)
- [ ] Team alignment achieved (people agree with decision or at least accept it)

**Weak decision-making:**
- [ ] Wrong people deciding (IT alone, insurance company alone)
- [ ] No legal review
- [ ] Insurance coverage unknown
- [ ] Recovery timeline is wishful thinking
- [ ] No documentation
- [ ] Decision reverses mid-exercise (shows uncertainty)
- [ ] Team alignment missing (people arguing about decision)

---

### Facilitation Prompts

**If group is indecisive:**
- "Your CEO is waiting for a recommendation. What do you tell them?"
- "If you had to choose in the next 2 minutes, which would it be?"
- "What would change your mind? Do you have that information?"

**If leaning toward payment:**
- "What does the FBI say about this? Should that matter?"
- "If this becomes public ('Company paid $X ransom'), how does that look?"
- "What if the decryption key doesn't work? What's your fallback?"

**If leaning toward not paying:**
- "Your recovery timeline just extended to 21 days. Still comfortable with that downtime?"
- "The attacker just published the first batch of data—your customer PII. Still OK?"
- "CEO is asking: Could we have prevented 2 weeks of downtime for $2M payment?"

**If choosing Option C:**
- "Your negotiation just reduced ransom to $[AMOUNT]. Recovery is on pace for 9 days. What's your threshold for payment?"
- "Negotiation is stalling; recovery is tracking well. What's your decision?"

---

### Debrief Discussion

**After decision and consequences:**

1. **Decision Process Quality:** Was the right person/group deciding?
2. **Information Gathering:** Did they understand all constraints?
3. **Organizational Values:** What does this decision say about the organization?
4. **Business Impact:** What's the financial impact of their choice?
5. **Regret Factor:** In hindsight, would they choose the same?
6. **Real Incident Comparison:** "In [actual ransomware incidents], organizations chose [A/B/C]..."
7. **Prevention Discussion:** "How could this situation have been avoided?"

---

---

## DP-3: DATA BREACH NOTIFICATION

**Difficulty:** Medium (more procedural than DP-1 or DP-2, but regulatory complexity is high)
**When:** T+45 to T+90 (parallels with containment decision)
**Duration:** 10-20 minutes
**Core Tension:** Regulatory speed requirements vs. investigation completion

### The Dilemma

Data was exfiltrated (not just encrypted). You must notify regulators and affected individuals. But you don't know exactly how much data, exactly who was affected, or exactly what was stolen. Regulators have tight deadlines; you need time to investigate.

**Context:**
- HIPAA/PCI/GDPR/State law notification required (depending on industry)
- Regulatory deadline: [Days/hours] from discovery
- Investigation is ongoing (full scope not yet known)
- Legal is drafting notification message
- Communications/PR are worried about message

---

### Key Framework Elements

**Regulatory Timelines (varies by jurisdiction):**
- HIPAA: 60 days from discovery
- GDPR: 72 hours to regulator (if high risk); individuals may have longer grace period
- State laws: 30-90 days (varies by state)
- PCI-DSS: 30 days minimum
- Industry-specific: May be faster

**Notification Decisions:**
1. **Scope:** How many individuals affected? (Uncertainty is problem)
2. **Data type:** What type of data? (Different data = different notification)
3. **Timing:** When to notify? (ASAP vs. after investigation)
4. **Content:** What do we tell them? (Be honest without admitting liability)
5. **Credit monitoring:** Do we offer credit monitoring? (Cost decision)

**Regulatory Parties:**
- Regulators (HIPAA, state AG, etc.)
- Affected individuals (direct notification)
- Law enforcement (optional but recommended)
- Credit bureaus (if SSN compromised)
- Media (if threshold crossed)

---

### Option A: Conservative Notification - Notify As Soon As Evidence of Exfiltration

**Description:** As soon as forensics shows data was exfiltrated, begin notification immediately.

**Pros:**
- Complies with "without unreasonable delay" regulatory language
- Gives affected individuals time to take protective actions
- Avoids accusation: "You waited too long to tell us"
- Shows transparency and responsibility
- Less legal risk (you followed guidance)

**Cons:**
- Scope may be overstated (notification sent to more people than necessary)
- Cost of unnecessary credit monitoring
- Message may be vague ("We don't know exactly what was taken")
- May cause unnecessary panic
- Notification costs multiply if scope changes

---

### Option B: Conservative Wait - Investigate First, Notify With Complete Picture

**Description:** Complete investigation first; then notify with accurate scope and details.

**Pros:**
- Notification is accurate (don't have to re-notify)
- Scope is precise (don't overestimate affected individuals)
- Message is confident and clear
- Avoids unnecessary credit monitoring costs
- Can explain what happened and what they should do

**Cons:**
- May exceed regulatory deadline
- Regulators may be angry ("Why did you wait?")
- Affected individuals discover breach from other sources first (darknet, media)
- Legal risk increases ("You should have notified sooner")
- Looks less transparent

---

### Option C: Phased Notification - Notify Preliminary, Update Later

**Description:** Notify affected individuals quickly with preliminary information; update message as investigation completes.

**Pros:**
- Meets regulatory timeline
- Gives individuals time to protect themselves
- Shows transparency and speed
- Allows updating message with more details later
- Reduces legal risk

**Cons:**
- Multiple notifications may confuse/frustrate people
- Preliminary notification may trigger unnecessary panic
- Later notification may look like you're hiding something ("Why didn't you tell us this initially?")
- Cost of repeat notifications
- May require repeat credit monitoring offers

---

### Expected Responses

**Groups typically:**
- Involve legal (good—they should be involved)
- Argue timeline pressure vs. investigation completion
- Choose phased approach (reasonable middle ground)
- Struggle with message content (how honest to be?)

---

### Evaluation Criteria

**Strong response includes:**
- [ ] Regulatory timeline understood
- [ ] Legal consulted on requirements
- [ ] Scope assessment realistic (not over/under estimated)
- [ ] Notification timeline decided (with reasoning)
- [ ] Draft message prepared
- [ ] Affected parties identified (regulators, individuals, credit bureaus)
- [ ] Credit monitoring decision made (offer it or not?)
- [ ] Law enforcement coordination considered
- [ ] Cost implications discussed

---

---

## DP-4: RECOVERY STRATEGY

**Difficulty:** Medium-High
**When:** T+80 to T+140+ (after containment, parallel with other decisions)
**Duration:** 15-30 minutes
**Core Tension:** Speed of recovery vs. assurance that systems are clean

### The Dilemma

You need to get systems back online. You have three strategies: restore from backup, rebuild from scratch, or negotiate with attacker. Each has different timelines, risks, and costs.

---

### Option A: Restore from Backups

**Timeline:** 3-5 days (if backups are good)
**Risk:** High - if backups are compromised, restoration just restores infection

**Pros:**
- Fastest recovery path (if backups work)
- Least expensive
- Minimizes business downtime
- Familiar process

**Cons:**
- Backups may be corrupted/encrypted too
- Must verify NO malware on restored systems
- Oldest backup loss (some data loss)
- Attacker may have planted persistence in backup

---

### Option B: Rebuild from Scratch

**Timeline:** 1-3 weeks (depending on complexity)
**Risk:** Medium - slowest, but most secure

**Pros:**
- Most secure (fresh start, no persistence)
- Eliminates any lingering malware
- Validates that backups work (as part of recovery)
- Forces infrastructure review/improvement
- Can modernize systems during rebuild

**Cons:**
- Very slow (business impact is significant)
- Expensive (significant engineering effort)
- Requires clean system images (often don't exist)
- All systems down longer
- Backup restoration still required (for data)

---

### Option C: Negotiate with Attacker

**Timeline:** Hours to days
**Risk:** Very High - attacker provides decryption key (sometimes works, sometimes doesn't)

**Pros:**
- Potentially fastest if key works
- Avoids lengthy downtime if infrastructure is complex

**Cons:**
- No guarantee key works
- Attacker may have kept backdoor (persistence remains)
- Requires payment (which may not be approved)
- FBI guidance strongly against
- Doesn't address data that was exfiltrated

---

### Expected Responses

**Groups typically:**
- Choose restore from backup (seems fastest/cheapest)
- Get blindsided when backups don't work as expected
- Escalate to rebuild if backup recovery fails
- Rarely choose rebuild proactively (too slow)

---

### Evaluation Criteria

**Strong response includes:**
- [ ] Backup status verified BEFORE choosing strategy
- [ ] Recovery timeline is realistic (not optimistic)
- [ ] Plan B exists (if primary strategy fails)
- [ ] Validation plan includes forensic verification
- [ ] Persistence hunting is planned (don't just restore and hope)
- [ ] Prioritization is clear (which systems first?)
- [ ] Data vs. system recovery sequenced (systems first, then data)

---

---

## DP-5: STAKEHOLDER COMMUNICATION & LEADERSHIP BRIEFING

**Difficulty:** Medium (less about technical choice, more about communication skill)
**When:** T+50 to T+100+ (ongoing throughout exercise)
**Duration:** 10-30 minutes (repeated briefings)
**Core Tension:** Need for speed vs. uncertainty; technical accuracy vs. executive simplicity

### The Dilemma

Your executives and board need updates. You're still investigating. You don't have complete answers. But they're making decisions based on your briefings. How do you communicate uncertainty while maintaining confidence?

---

### Key Briefing Moments

**First Briefing (T+50):** Initial situation report
- "Here's what we know so far"
- "Here's what we're still investigating"
- "Here's what we need to decide NOW vs. what can wait"

**Second Briefing (T+80):** Updated situation
- "Scope is worse/better than we thought"
- "Here are our options"
- "Here's what we recommend"

**Third Briefing (T+120+):** Status and recovery progress
- "Recovery is on track/delayed"
- "Unexpected complications appeared"
- "Here's our next milestone"

---

### Evaluation Criteria

**Strong communication includes:**
- [ ] Clear, jargon-free language
- [ ] Honest assessment (not sugar-coated, but not panic-inducing)
- [ ] Specific recommendations (not just options)
- [ ] Confidence levels ("We're confident about X, still determining Y")
- [ ] Timeline clarity (when will we have next update?)
- [ ] Scope/financial impact explained in business terms
- [ ] Who needs to decide what (clarity of decision authority)

**Weak communication:**
- [ ] Too much jargon
- [ ] Unclear recommendations
- [ ] No timeline/confidence levels
- [ ] Blame-shifting ("IT should have...")
- [ ] Contradicts previous briefings
- [ ] Inadequate answers to executive questions

---

### Facilitation Prompts

**If group struggles with non-technical audience:**
- "The CEO doesn't know what 'lateral movement' means. Explain it differently."
- "Don't tell them how—tell them what it means to the business."
- "What's the one thing they MUST understand?"

**If group is over-promising:**
- "You said 5 days to recovery. What if backup restoration is slower?"
- "If you miss that deadline, what's your backup plan?"

**If group is unclear:**
- "Your message was too vague. Did you actually tell them anything?"
- "What specific decision do you need from them?"

---

## Summary: Using These Decision Points in Your Exercise

**For 2-hour exercise:**
- Focus on DP-1 (Containment) only
- Quick decision, big impact
- Good for beginner groups

**For 4-hour exercise:**
- DP-1 (Containment) + DP-2 (Ransom) or DP-3 (Notification)
- Two major decisions, sequential or parallel
- Good for intermediate groups

**For full-day exercise:**
- All 5 decision points, with complexity
- Decisions have consequences that surface in later decisions
- Good for advanced groups

**Facilitation Note:** Real incidents don't have neat sequential decisions. Run them in parallel when possible to create realistic chaos.
