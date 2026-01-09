# Complications Library - Difficulty Modifiers

**Customizable difficulty enhancement system for tailoring ransomware exercises to participant skill level and exercise duration**

Use this library to calibrate exercise difficulty. Select complications based on your participant skill level (beginner/intermediate/advanced) and desired exercise challenge level. Each complication is designed to create realistic decision pressure without being artificially difficult.

---

## How to Use This Library

1. **Identify your participant skill level:** Beginner, Intermediate, or Advanced
2. **Choose appropriate complications** from the library below
3. **Decide when to introduce each complication** during exercise
4. **Weave complication into relevant inject** (use the Inject Library to customize)
5. **Facilitate participant response** without providing solution

### Difficulty Levels and Complication Counts

- **Beginner (2-hour):** 0-1 complication (straightforward, minimal surprises)
- **Intermediate (4-hour):** 2-3 complications (some pressure, realistic complexity)
- **Advanced (full-day):** 4+ complications (high pressure, organizational chaos)

---

## BACKUP COMPLICATIONS (High Impact on Recovery)

These complications create pressure around the recovery strategy decision. They force teams to reconsider assumptions about data restoration.

---

### BC-1: Backups Are Older Than Expected

**Trigger:** When IT checks backup status (typically T+20 to T+30)

**Complication Content:**
```
[FROM BACKUP OPERATIONS]
"We have a problem with backup retention.

Our normal backup retention policy is 7 days (daily incrementals, weekly full).

But due to [REASON: storage capacity issue / policy change / misconfiguration],
the oldest CLEAN backup we have is [DAYS] days old.

That means:
- We're losing [NUMBER] days of data
- Files modified in the last [DAYS] days will be reverted
- [CRITICAL-SYSTEM] transactions from the last [DAYS] days are lost

Is this acceptable? Or do we need a different recovery strategy?"
```

**Impact on Decisions:**
- Forces team to assess business tolerance for data loss
- May push toward backup restoration despite old data
- May push toward ransom payment (avoids data loss)
- May require hybrid strategy (restore what's good, rebuild critical systems)

**Variations by Difficulty:**
- **Beginner:** Oldest backup is 3 days old (manageable data loss)
- **Intermediate:** Oldest backup is 5-7 days old (significant data loss)
- **Advanced:** Oldest backup is 2+ weeks old (unacceptable data loss, forces hard choices)

**Industry Customizations:**
- **Healthcare:** "EHR data from last 3 days is lost. Patients' treatment records are incomplete."
- **Finance:** "Transaction records from last 7 days don't match customer accounts. Reconciliation nightmare."
- **Retail:** "Inventory data from last 3 days is lost. No record of recent sales/receiving."

---

### BC-2: Backup Restoration Process Is Broken or Untested

**Trigger:** When team decides to restore from backups (T+60 to T+90)

**Complication Content:**
```
[FROM BACKUP OPERATIONS]
"We've begun restoration testing, and we have a problem.

When we tried to restore a test system from backup:
- Restoration is taking [HOURS] per system (much slower than estimated)
- There's a [TECHNICAL-ISSUE] that's blocking faster restoration
- We've never actually tested this recovery process end-to-end

Our original estimate was [DAYS] days to full recovery.
Revised estimate: [DAYS-LONG] days (or longer, if we hit more issues).

Also: We discovered [GOLD-IMAGE-ISSUE] with our system images.
Our clean images are from [DATE] (outdated OS patches, old application versions).

This is going to take longer than we thought."
```

**Impact on Decisions:**
- Forces reality check on recovery timeline
- May force escalation to rebuild-from-scratch (slower, but more predictable)
- May force reconsideration of ransom payment ("At least we'd have a known timeline")
- Creates pressure on business (longer downtime than expected)

**Variations by Difficulty:**
- **Beginner:** Restoration is slow but works (take longer, but it works)
- **Intermediate:** Restoration process has issues (1-2 complications to solve)
- **Advanced:** Restoration process is severely broken (backup may not work at all, may need to rebuild)

**Industry Customizations:**
- **Healthcare:** "EHR restoration is slower because of database size and dependencies."
- **Finance:** "Database restoration includes data validation (must verify integrity). Adding days."
- **Retail:** "Cloud recovery slower than expected (data transfer is bottleneck)."

---

### BC-3: Backups Were Encrypted Too

**Trigger:** During investigation of backup status (T+25 to T+45)

**Complication Content:**
```
[FROM BACKUP OPERATIONS - CRITICAL]
"We have BAD NEWS about our backups.

The attacker didn't just encrypt our live systems.
They found the backup destination and encrypted those too.

Status:
- Daily incremental backups: ENCRYPTED (unusable)
- Weekly full backups: ENCRYPTED (unusable)
- Monthly archived backups: ENCRYPTED (unusable)

The only backup we can use is [VERY-OLD-BACKUP] from [DATE].
That's [WEEKS/MONTHS] of data loss.

Do we:
A) Accept that much data loss?
B) Negotiate with attacker (need paying ransom for decryption)?
C) Try to recover from [VERY-OLD-BACKUP] anyway (obsolete systems)?
D) Rebuild from scratch (long recovery, but no more data loss)?

This changes everything about our recovery strategy."
```

**Impact on Decisions:**
- Eliminates backup-based recovery as viable option
- May force ransom payment decision (only fast option left)
- May force rebuild-from-scratch (very slow, but only secure option)
- Creates huge business impact (all data loss or massive delay)

**Variations by Difficulty:**
- **Beginner:** Some backups encrypted, but older clean backup exists (2+ weeks old)
- **Intermediate:** All recent backups encrypted, oldest clean backup is very old (1+ month)
- **Advanced:** All backups encrypted, no clean backup available (only attacker's decryption key or rebuild)

**Facilitation Note:** This is high-impact complication. Use only when exercise needs major pressure point.

---

## SCOPE EXPANSION COMPLICATIONS (Creates Pressure to Re-Evaluate Containment)

These complications force teams to realize their containment strategy was insufficient.

---

### SC-1: Encryption Spreads Faster Than Contained

**Trigger:** During investigation/containment (T+40 to T+70)

**Complication Content:**
```
[FROM NETWORK MONITORING]
"The containment you implemented is working, but not completely.

Systems we thought were isolated are still getting encrypted:
- [DEPARTMENT-1] workstations (should have been isolated, still encrypting)
- [FILE-SERVER-2] (should have been isolated, still encrypting)
- Cloud storage buckets (backups that should have been offline)

Either:
A) Our isolation wasn't complete (perimeter still has access)
B) Encryption is spreading via pre-established connections we didn't block
C) There's another infected system we missed

Scope is now [HIGHER-NUMBER] systems instead of [ORIGINAL-NUMBER].

Do we escalate containment? Full network isolation?"
```

**Impact on Decisions:**
- Forces team to re-evaluate containment strategy
- May push toward more aggressive isolation
- May reveal that containment assumptions were wrong
- Creates time pressure (more systems encrypting while you debate)

**Variations by Difficulty:**
- **Beginner:** Spread to nearby systems (few additional machines affected)
- **Intermediate:** Spread to other departments (dozens more systems)
- **Advanced:** Spread to partner/cloud systems (scope explodes beyond original estimate)

---

### SC-2: Attacker Maintains Access Via Backdoor

**Trigger:** During investigation (T+50 to T+100)

**Complication Content:**
```
[FROM FORENSICS TEAM]
"We found a problem in our analysis.

During the attack, the attacker created multiple persistence mechanisms:
- Scheduled tasks (found and removed)
- Registry run keys (found and removed)
- WMI event subscriptions (found and removed)

BUT - we also found evidence of a backdoor:
- Hidden user account created: [ACCOUNT-NAME]
- VPN access configured to external C2 infrastructure
- Remote access tool installed on [SYSTEMS]

The backdoor is still active. The attacker may still have access to our network.

This means:
- Attacker can see our containment efforts (watching our response)
- Attacker could re-establish full access if we don't remove persistence completely
- Recovery is not just restore systems; must eliminate all access

What's our strategy for finding and eliminating ALL backdoors?"
```

**Impact on Decisions:**
- Changes recovery strategy (can't just restore and hope)
- Requires thorough forensic validation before any recovery
- May force more aggressive eradication approach
- Creates timeline pressure (if attacker is still watching, they may act)

**Variations by Difficulty:**
- **Beginner:** One backdoor found, location clear, easily removed
- **Intermediate:** Multiple backdoors found, some harder to locate, may take time to fully eradicate
- **Advanced:** Backdoors are sophisticated, not fully understood, may require forensic analysis before removal

---

### SC-3: Multiple Locations or Business Units Affected

**Trigger:** During scope confirmation (T+30 to T+60)

**Complication Content:**
```
[FROM EXECUTIVE BRIEF]
"Scope expanded significantly.

We initially thought this was localized to [DEPARTMENT].

Update shows it's broader:
- [DEPARTMENT-1]: 40 systems
- [DEPARTMENT-2]: 25 systems
- [REMOTE-OFFICE]: 15 systems
- [PARTNER-LOCATION]: Unknown systems
- [CLOUD-INFRASTRUCTURE]: Multiple instances

Total scope is now ~100+ systems across 3+ locations.

Impact on decisions:
- Containment becomes much more complex (multiple perimeters)
- Recovery is significantly longer (more systems to rebuild)
- Executive impact is organization-wide (not just one department)
- Cost impact: [HIGHER-COST]

Recovery timeline estimate: [LONGER-TIMELINE]

What's our new strategy?"
```

**Impact on Decisions:**
- Escalates severity and visibility
- Forces resource prioritization across locations
- May require additional external help (more contractors, longer timelines)
- Changes business continuity narrative (full organization affected, not just one area)

---

## REGULATORY COMPLICATIONS (Creates Notification and Compliance Pressure)

These complications force teams to deal with external regulatory and legal requirements.

---

### REG-1: Data Exfiltration Triggers HIPAA/PCI/GDPR Notification

**Trigger:** During investigation (T+40 to T+80)

**Complication Content:**
```
[FROM LEGAL]
"Forensics confirms the attacker exfiltrated data.

The data includes [DATA-TYPE]:
- [NUMBER] patient records (PHI - protected health information)
- [NUMBER] credit card records (PCI-DSS)
- [NUMBER] EU resident records (GDPR)

Regulatory notification is REQUIRED:

HIPAA: Must notify affected individuals within 60 days
        Must notify HHS within 60 days
        Must notify media if >500 individuals
        Fines: $[AMOUNT] per violation, up to $[AMOUNT] total

PCI-DSS: Must notify card processor within 30 days
         Must notify affected cardholders
         May be fined $[AMOUNT] per month non-compliance

GDPR: Must notify EU Data Protection Authority within 72 hours (if high risk)
      Must notify EU residents without undue delay
      Fines: Up to 4% of global revenue (or $[AMOUNT], whichever is higher)

[JURISDICTION] State Law:
      Must notify state AG if >500 residents
      Notification within 30 days
      Required credit monitoring notification

So now you need to:
1. Determine exact scope of each data type
2. Draft notification messages (subject to legal review)
3. Arrange credit monitoring (cost: $[AMOUNT] for X individuals)
4. Coordinate with regulators
5. Prepare for media inquiry (if >500 individuals)
6. Budget for legal/notification costs (estimate: $[AMOUNT])

Notification deadline: [DATE] ([DAYS] away)
Are we on track?"
```

**Impact on Decisions:**
- Adds major time and cost component
- Forces legal involvement (likely increases complexity)
- May force decision on ransom payment (affects timing)
- Adds to executive pressure (regulatory fines are significant)
- May affect recovery timeline (legal may want forensic evidence preserved)

**Variations by Difficulty:**
- **Beginner:** Notification required, but relatively straightforward (one jurisdiction, one data type)
- **Intermediate:** Notification to multiple jurisdictions, multiple data types, some complexity
- **Advanced:** GDPR involved (72-hour deadline!), multiple jurisdictions, high-value data, significant fines possible

---

### REG-2: Board/Regulatory Notification Required

**Trigger:** During executive briefing (T+70 to T+120)

**Complication Content:**
```
[FROM GENERAL COUNSEL]
"We need to notify the Board of Directors AND regulators about this incident.

Board Notification:
- Audit committee must be briefed (corporate governance requirement)
- Board needs to vote on CEO action (incident response strategy)
- Board may demand specific involvement (independent IR firm, forensics firm)
- Board may demand incident report (within [TIMEFRAME])

Regulatory Notification:
- SEC Disclosure (if publicly traded - likely 8-K filing required)
- Banking Regulators (if financial institution)
- HIPAA Regional Office (if healthcare)
- State Attorney General (if state breach law triggered)

Each notification has specific requirements:
- Timeline: [HOURS/DAYS]
- Content: Very specific (what to disclose, what to hold back)
- Legal risk: If we disclose too much or too little, legal consequences
- Market impact: If publicly traded, stock may be affected

Also, these external parties will now be involved in decisions:
- Board will want to weigh in on ransom decision
- Regulators may have requirements (preserve evidence, notify FBI, etc.)
- Each adds complexity and timeline pressure

You now have external stakeholders in your incident response process."
```

**Impact on Decisions:**
- Adds governance layer (Board now involved in decisions)
- Adds regulatory constraints (may limit options)
- Adds timeline pressure (disclosure deadlines)
- Changes decision authority (CEO may need Board approval for major decisions)
- Public/market impact (if SEC disclosure required)

---

## BUSINESS PRESSURE COMPLICATIONS (Creates Time and Revenue Impact)

These complications create pressure from business side—non-technical stakeholders demanding action.

---

### BP-1: Media Inquiry/Public Story

**Trigger:** During escalation phase (T+80 to T+120)

**Complication Content:**
```
[FROM PR TEAM]
"A reporter from [MAJOR-NEWS-OUTLET] has reached out.

They know:
- We experienced a ransomware attack [HOURS] ago
- Approximately [NUMBER] systems were affected
- Threat actors claim to have [DATA-TYPE] data
- Are asking if we paid the ransom

Reporter's deadline: [TIME] (in [HOURS] hours)

PR team is saying: "We should proactively release a statement,
or we'll look like we're hiding something."

Legal is saying: "Be very careful what we admit. Minimize liability."

CEO is saying: "I want to talk to the reporter before they publish."

What's our official statement? And how much do we tell them?"
```

**Impact on Decisions:**
- Forces decision on ransom payment (reporter will ask directly)
- Forces decision on data breach notification (reporter may trigger public awareness)
- Forces messaging strategy (transparency vs. legal caution)
- May influence executive decisions (wanting to look good to media)

**Variations by Difficulty:**
- **Beginner:** Reporter has limited info (story is small, not much pressure)
- **Intermediate:** Reporter has detailed info (may have insider source, story is credible)
- **Advanced:** Reporter publishes regardless (now you're responding to published story, narrative is out of your control)

---

### BP-2: Large Customer Threatening to Leave

**Trigger:** During recovery phase (T+100 to T+150)

**Complication Content:**
```
[FROM BUSINESS OPERATIONS]
"Our largest customer just called.

They want to know:
- When will their systems be available?
- What data did we lose of theirs?
- Is their data secure now?
- Why didn't we prevent this?

They're threatening to terminate the contract if we don't:
A) Restore their systems by [DATE]
B) Provide written guarantee that their data is secure
C) Offer service credits for downtime

Financial impact: If they leave, we lose $[AMOUNT] annual revenue.

This is URGENT. Customer relationship is now on the line."
```

**Impact on Decisions:**
- Creates revenue pressure on recovery timeline
- May force accelerated recovery (even if not fully validated)
- May force customer communication decision (transparency vs. confidentiality)
- May affect business decision-making (push toward ransom payment if it recovers faster)

---

### BP-3: Board/Executive Demanding Hourly Updates

**Trigger:** During ongoing incident (T+60 to T+120+)

**Complication Content:**
```
[FROM CEO OFFICE]
"The Board is now in special session on this incident.

CEO wants hourly update briefings at [TIME] each hour.

Board is asking:
- Why hasn't IT solved this yet?
- Have we considered paying the ransom?
- Are we talking to law enforcement?
- What's the financial impact?
- What's the recovery timeline?
- Is anyone being held accountable?

CEO is stressed. Board is impatient. They want simple answers,
but the situation is complex.

Prepare 5-minute executive briefing for next update ([TIME])."
```

**Impact on Decisions:**
- Creates time pressure on briefing preparation (reduces focus on actual incident)
- Executive pressure may influence technical decisions
- May force decision before investigation is complete
- Adds stress and complexity to already-stressed team

---

## TECHNICAL COMPLICATIONS (Creates Investigation Challenges)

These complications create technical investigation challenges that extend timeline and add uncertainty.

---

### TC-1: Decryption Key Only Partially Works

**Trigger:** If group pays ransom and receives decryption key (T+120+)

**Complication Content:**
```
[FROM RECOVERY OPERATIONS]
"The decryption key from the attacker is working, but not completely.

Status:
- File servers: 100% of data decrypted (working)
- Workstations: 85-90% of files decrypted (some files remain encrypted)
- Cloud storage: 0% decrypted (key doesn't work for this)
- Database: 60% decrypted (some transactions are corrupted in restoration)

Options:
A) Accept partial recovery (some data permanently lost)
B) Negotiate with attacker for another key (uncertain if they'll help)
C) Attempt to recover encrypted remainder from backups (time consuming)
D) Use file recovery tools (maybe 30-40% recovery of lost files)

This is not the full recovery we were promised."
```

**Impact on Decisions:**
- Demonstrates ransom payment was incomplete solution
- Forces team to implement workarounds
- Extends recovery timeline (now need additional recovery methods)
- May create permanent data loss
- Validates concern that paying ransom isn't guaranteed to work

---

### TC-2: EDR/SIEM Didn't Capture Full Attack Chain

**Trigger:** During forensic investigation (T+60 to T+90)

**Complication Content:**
```
[FROM FORENSICS TEAM]
"We're analyzing the attack chain, and we have a gap problem.

Timeline we can see:
- T-[DAYS] days: Initial phishing email (email archive shows this)
- T-[HOURS]: PowerShell commands (EDR captured this)
- [GAP - NO VISIBILITY]
- T-[CURRENT]: Ransomware deployment (file system shows this)

The gap is [HOURS/DAYS] long. During that time:
- Attacker was in the network
- We have no direct evidence of what they did
- Could have done reconnaissance, lateral movement, data exfiltration, persistence

This means:
- We don't know for certain HOW they escalated privileges
- We don't know exactly WHAT systems they accessed
- We don't know IF they exfiltrated data (they might not be claiming they did just to create pressure)
- We don't know if ALL backdoors are found

Our investigation is incomplete. We're working with gaps in the chain."
```

**Impact on Decisions:**
- Creates uncertainty about attack scope (may be worse than thought, or may be exaggerated)
- May affect ransom payment decision (if we don't know what they took, how do we know ransom threats are real?)
- May affect forensic approach (need deeper investigation to fill gaps)
- Extends timeline (investigation discovery phase takes longer)

---

## TEAM/ORGANIZATIONAL COMPLICATIONS (Creates Coordination Challenges)

These complications create internal organizational friction during incident.

---

### ORG-1: IT and Security Teams Disagree on Approach

**Trigger:** During containment/recovery decision (T+60 to T+90)

**Complication Content:**
```
[INTERNAL CONFLICT]
"There's significant disagreement between IT Operations and Security teams.

IT Operations perspective:
"We need to restore services ASAP. Longer downtime costs millions.
We should restore from backup immediately. Security can investigate in parallel.
This is too cautious—we're losing money while doing forensics."

Security Team perspective:
"We need to be thorough. If we restore before finding all persistence,
attacker comes back in. We need complete investigation before ANY recovery.
This is too risky—we'll pay for this mistake later."

CEO sees the conflict and is frustrated:
"Why can't you just agree on a plan? I need one unified recommendation,
not two different teams arguing."

Your incident commander needs to resolve this and present unified strategy."
```

**Impact on Decisions:**
- Forces team to resolve internal conflict (visible to leadership)
- May delay decisions (teams are negotiating instead of executing)
- May force compromise (half-measures that satisfy nobody)
- Tests leadership capability (can IC resolve the conflict?)

---

### ORG-2: Key Personnel Are Unavailable

**Trigger:** During critical decision point (T+60 to T+100)

**Complication Content:**
```
[DURING CRITICAL DECISION]
"We have a staffing problem:

- Your IR lead / CISO is [SICK / ON VACATION / UNREACHABLE]
- Your backup incident commander is [IN MEETING / OVERLOADED]
- Your forensics specialist is [TRAVELING / OFF-SHIFT]

Key decisions need to be made, but not all decision-makers are available.

Who makes the call on:
- Containment strategy?
- Ransom payment decision?
- Executive briefing content?

You need to decide authority NOW, or decisions get delayed."
```

**Impact on Decisions:**
- Forces organization to clarify succession and authority
- May require different person to make decision than originally planned
- Tests whether cross-training exists (backup personnel ready to step up)

---

## Using Complications in Your Exercise

### Recommended Complications by Duration and Difficulty

**2-Hour Beginner:**
- No complications (let them succeed)

**2-Hour Intermediate:**
- BC-1 (older backups)
- SC-1 (scope expansion)

**4-Hour Beginner:**
- BC-1 (older backups)

**4-Hour Intermediate:**
- BC-1 (older backups) + SC-1 (scope expansion)
- REG-1 (regulatory notification)
- BP-1 (media inquiry)

**4-Hour Advanced:**
- BC-1 + BC-2 (backup problems)
- SC-1 + SC-2 (scope expansion + backdoor)
- REG-1 (regulatory notification)
- BP-1 + BP-2 (media + customer pressure)
- TC-1 (decryption key fails)

**Full-Day Advanced:**
- BC-2 or BC-3 (serious backup failure)
- SC-2 + SC-3 (backdoor + multi-location spread)
- REG-2 (board/regulatory notification)
- BP-1 + BP-2 + BP-3 (media + customer + executive pressure)
- ORG-1 + ORG-2 (internal conflict + staffing issues)
- TC-1 (decryption key fails)

### Timing Complications

**Early complications (T+30 to T+60):**
- Backup problems (BC-1, BC-2)
- Scope expansion (SC-1)
- Forces early strategy decisions

**Mid-exercise complications (T+60 to T+100):**
- Regulatory (REG-1)
- Business pressure (BP-1, BP-2)
- Organizational (ORG-1, ORG-2)
- Forces resource/priority decisions

**Late complications (T+100+):**
- Technical issues during recovery (TC-1)
- Executive pressure (BP-3)
- Forces adaptation mid-recovery

### Calibration Tips

- **Start simpler than you think necessary** - Real groups need time to organize
- **Add complications if pace is slow** - Keep energy up
- **Hold complications if pace is fast** - Let them work through logic
- **Watch for panic points** - Complications should create pressure, not overwhelm
- **Cluster complications strategically** - Don't dump all at once (groups lose focus)

### Debrief Discussion

After complications surface and groups deal with them:

1. **Realism:** Did this complica feel realistic? Have you seen this in real incidents?
2. **Impact:** How did this change your strategy?
3. **Preparation:** Could this have been prevented? How?
4. **Adaptation:** How did you adapt when circumstances changed?
5. **Lessons:** What will you do differently in your actual environment?

---

## Notes for Facilitators

- **Complications aren't punishment** - They're teaching tools
- **Don't pile on at once** - Space them out strategically
- **Watch group energy** - Remove complications if group is losing focus/hope
- **Validate difficult choices** - Sometimes right answer looks like failure (paid ransom, still lost data)
- **Real incidents are messy** - Your complications should create realistic chaos
