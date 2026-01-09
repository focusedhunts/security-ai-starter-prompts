# TTX Style Guide - Gamification vs. Traditional

**How to adapt the TTX Generator components for different exercise styles and participant preferences**

This guide helps consultants choose between **gamification-enhanced TTX** (dynamic, game-like elements) and **traditional TTX** (discussion-based, scenario-driven), or blend them. The same component libraries support both approaches—what differs is facilitation style and how components are activated.

---

## TTX Style Spectrum

```
TRADITIONAL                          BLENDED                          GAMIFIED
(Discussion-based)              (Moderate engagement)           (Game mechanics)

• Linear scenario flow          • Structured scenario            • Time pressure mechanics
• Facilitator reads injects     • Injects with consequences    • Resource allocation
• Team discusses decisions      • Score/outcome tracking        • Rolling/probability
• Focus: Learning & Planning    • Team vs. team options         • Competitive elements
• Pace: Moderator controlled    • Mixed metrics                 • Point-based scoring
• Engagement: Intellectual      • Engagement: Balanced          • Engagement: High energy
```

---

## TRADITIONAL TTX APPROACH

### Philosophy

**Traditional TTX** is discussion-based incident response training where:
- Facilitator presents scenario and injects in a linear fashion
- Participants discuss options and make decisions
- Focus is on learning IR processes and testing communication
- Pace is set by facilitator and group discussion
- Engagement is intellectual and deliberative

### How Components Support Traditional TTX

#### Injects Library (inject-library.md)

**Usage in Traditional TTX:**
- Facilitator reads inject content exactly as written (or slightly adapted)
- Group discusses inject for 5-10 minutes
- Facilitator asks: "What do you do?" or "What's your response?"
- Group discusses options and decides on action
- Facilitator describes consequences (from library), moves to next inject

**Example Flow:**
```
Facilitator: "It's T+20 minutes. You receive this inject:
             [reads INV-1: Backup Status Check]"

Group discusses for 5-7 minutes:
- What are the backup implications?
- Does this change our strategy?
- What do we do about it?

Facilitator: "Your backup recovery will take 10 days with data loss.
             How does that affect your decisions?"

Group continues discussion and moves forward
```

**What's Minimized in Traditional TTX:**
- Timing pressure (injects happen when discussion is ready, not on a clock)
- Surprise/randomness (facilitator telegraphs what's coming)
- Parallel threads (one thing at a time, discussed sequentially)
- Scoring/metrics (focus is on learning, not winning)

**What's Emphasized:**
- Deep discussion (20-30 minutes per inject is normal)
- Exploring options (why did you choose that? what if?)
- Team communication (how did you decide? did everyone agree?)
- Learning moments (facilitator uses pitfalls library to coach)

#### Decision Points Library (decision-points.md)

**Usage in Traditional TTX:**
- Facilitator presents full decision point context at once
- Group discusses all options with full information
- Discussion is comprehensive (15-30 minutes typical)
- Facilitator uses evaluation criteria to assess quality of thinking
- Decision is documented

**Example Flow:**
```
Facilitator: "It's T+45 minutes. Major decision time:
             [presents DP-1: Containment Approach & Timing]

             Here are your three options:
             A) Aggressive immediate isolation (Option A)
             B) Selective containment (Option B)
             C) Monitored response (Option C)

             For each option, here are the pros/cons..."

Group discusses for 20-30 minutes:
- Which option feels right? Why?
- What are we sacrificing?
- Can we pivot if we're wrong?
- Who decides this?

Facilitator: "OK, what's your decision? Document it and your reasoning.
             Here's what happens next..."
```

**Emphasis:**
- Understanding tradeoffs (decision quality matters)
- Learning process (how did you decide?)
- Team alignment (did everyone understand?)
- Real-world comparison (in [actual incident], they chose X. Here's what happened...)

#### Complications Library (complications.md)

**Usage in Traditional TTX:**
- Facilitator introduces complications one at a time, clearly
- Group discusses impact on current strategy
- Complications are learning tools, not surprises
- May highlight assumptions ("We thought backups were good")

**Example Flow:**
```
Facilitator: "Update from IT Operations:
             [introduces BC-1: Backups Are Older Than Expected]

             This changes things. How does this affect your recovery strategy?"

Group recalibrates strategy based on new information
Facilitator coaches: "This is why you test backups"
```

**Emphasis:**
- Reflection (how does new info change assumptions?)
- Adaptation (can we pivot strategy?)
- Root cause analysis (how could this have been prevented?)

---

## GAMIFIED TTX APPROACH

### Philosophy

**Gamified TTX** enhances engagement through game mechanics where:
- Time pressure is real (injects arrive on schedule, not when group is ready)
- Consequences are tracked (decisions have scoring/resource impact)
- Surprise/discovery is built in (unexpected events happen)
- Competition or challenge creates tension (team vs. team or team vs. scenario)
- Success is measured (points, resources remaining, objectives achieved)
- Energy is high (fast pace, dynamic surprises, victory/failure moments)

### How Components Support Gamified TTX

#### Injects Library as Timed Events

**Gamified Usage:**
- Injects arrive on a **schedule**, not when group is ready
- Groups must decide QUICKLY ("You have 3 minutes to respond")
- Timing pressure creates realism (real incidents don't wait for discussion to finish)
- Missed injects or delayed responses have consequences (encryption spreads faster, data is exfiltrated)

**Example Gamified Inject Timing:**
```
T+0:    Exercise starts (DET-1: Initial Alert)
T+5:    Group must respond to alert (3-minute response window)
T+10:   DET-2: Scope Confirmation arrives (whether group responded or not)
T+15:   INV-1: Backup Status arrives (parallel with ongoing discussion)
T+20:   RANSOM-DECISION deadline looms (decisions have deadline)
T+25:   RESP-1: Law Enforcement arrives (external constraints)
T+30:   REC-1: Recovery Timeline arrives (business pressure)

Real clock driving the exercise, not group discussion pace
```

**Mechanics:**
- **Time pressure:** "You have 5 minutes to decide. Tick tock."
- **Parallel threads:** Multiple injects happening simultaneously
- **Consequences:** Slow decision = encryption spreads more
- **No rewind:** "Your call was to wait and see. During those 30 minutes, 50 more systems encrypted. Too late now."

#### Decision Points as Scored Moments

**Gamified Usage:**
- Each decision has **point values** based on quality
- Resources are tracked (budget, systems functional, time available)
- Decisions affect downstream scenarios (choosing to pay ransom affects recovery options)
- Success/failure states exist (good decisions = lower costs, bad decisions = higher costs)

**Example Scoring System:**

```
Decision Quality Scoring (0-100 points per decision):

DP-1: Containment Approach
  - Choosing aggressive isolation early: +30 points
    (Stops spread, but costs in downtime)
  - Choosing selective containment: +20 points
    (Moderate cost, moderate risk)
  - Choosing monitored response: -10 points
    (High risk if spread accelerates)
  - BONUS: +10 if decision made with clear reasoning & documented

DP-2: Ransom Payment
  - Deciding NOT to pay + having good backup: +25 points
  - Deciding NOT to pay + having bad backup: -5 points
    (Lost data, regulatory fines)
  - Deciding to pay + negotiating down: +20 points
  - Deciding to pay + paying full amount: +5 points
    (Faster recovery, but funded criminals)
  - BONUS: +15 if coordinated with legal/insurance/FBI

DP-3: Notification Timing
  - Early notification (conservative): +20 points
  - Phased notification (balanced): +25 points
  - Late notification (risky): -15 points
    (Regulators angry, affected individuals angry)

Score Tracking:
  - Below 40: "Problematic response" - many failures, high costs
  - 40-60: "Adequate response" - managed incident, significant impact
  - 60-80: "Good response" - effective decisions, controlled damage
  - 80-100: "Excellent response" - exemplary IR (rare!)
```

**Resources Tracked:**
```
Starting Resources:
  - Budget: $[AMOUNT]
  - Functional Systems: 100%
  - Recovery Timeline: Baseline
  - Regulatory Risk: Low
  - Customer Confidence: High
  - Team Morale: Normal

Decision Impacts:
  - Choose aggressive isolation: -$[AMOUNT] (downtime costs), -30% systems
  - Choose not to pay ransom: -$[AMOUNT] (recovery costs), +20 days
  - Choose to pay ransom: -$[AMOUNT] (payment), +5 days
  - Poor communication: -[VALUE] customer confidence
  - Miss regulatory deadline: -$[FINE AMOUNT]

Final Score = Starting 100 - cumulative deductions + bonuses for quality decisions
```

#### Complications as Random/Timed Surprises

**Gamified Usage:**
- Complications arrive **unexpectedly** (not telegraphed in advance)
- Surprise creates challenge and learning
- Complications can "cascade" (one bad outcome triggers another)
- Groups must adapt on the fly

**Example Gamified Complication Delivery:**

```
Group thinks they're making progress on recovery...

T+90 (surprise inject arrives):
"Update from IT: Backup restoration is taking much longer than expected.
 Our estimate was 10 days. New estimate: 21 days.
 Also: We just discovered we don't have clean gold images.
 Rebuild from scratch may not even be possible.

 What's your new strategy?"

This is BC-2 (Backup Restoration Broken) + scenario consequence
Arrives WITHOUT warning, forcing immediate adaptation
Group must recalibrate recovery strategy in real-time
```

**Cascade Example:**
```
Decision: "Don't isolate immediately, observe for 30 minutes"
Consequence: SC-1 (Scope Expansion) arrives
  - 50 additional systems encrypted in that 30 minutes
  - Costs increase by $[AMOUNT]
  - Timeline extends by 3 days
  - Score penalty: -20 points

New challenge: "You're now facing worse situation than if you'd isolated earlier.
              What do you do to recover from this mistake?"
```

---

## BLENDED TTX APPROACH (Recommended for Most)

### Philosophy

**Blended TTX** combines best of both:
- Structured scenario (like traditional) but with time pressure
- Deep discussion (like traditional) but with consequence tracking
- Linear flow (like traditional) but with surprise elements
- Learning focus (like traditional) but with engagement metrics

### How to Blend

**Timeline Structure:**
```
Duration: 4-hour exercise

T+0-30:   Traditional Phase
          - Facilitator presents scenario and initial injects
          - Group discusses situation, forms initial strategy
          - Pace: Facilitator-controlled, deep discussion encouraged
          - Focus: Understanding the situation

T+30-90:  Blended Phase
          - Injects arrive on tighter schedule (every 10-15 min)
          - Group must respond within timeframe (10-15 min to decide)
          - Complications arrive with consequences
          - Facilitator tracks decisions and impacts
          - Focus: Decision-making under pressure + learning

T+90-120: High-Intensity Gamified Phase
          - Injects arrive rapidly (5 min intervals)
          - Time pressure is real (3-5 min decisions)
          - Complications cascade
          - Consequences accumulate
          - Focus: Adaptive thinking and communication
```

**Scoring in Blended Approach:**
```
Light Scoring (not competitive, informative):
  - Track "decision quality" (0-100 points)
  - Show cumulative impact (costs, timeline, risk)
  - NOT comparing teams or ranking
  - Purpose: Provide feedback, not competition

Emphasis:
  - "Here's how your choices impacted the organization"
  - "You made good decisions here, but that one cost you"
  - "Let's discuss what would have changed the outcome"
```

---

## CHOOSING YOUR TTX STYLE

### Traditional TTX Best For:

**Participant Profile:**
- [ ] Non-technical executives (need discussion time)
- [ ] First tabletop exercise (need to understand basics)
- [ ] Learning-focused (less experienced teams)
- [ ] Small group size (5-10 people)
- [ ] Lower maturity IR organizations

**Exercise Goals:**
- [ ] Understand IR plan and processes
- [ ] Identify gaps in planning
- [ ] Improve cross-functional communication
- [ ] Training/education primary goal

**Time Available:**
- [ ] 4+ hours (deep discussion requires time)
- [ ] Can't have fast-paced surprises
- [ ] Preferred: Full-day for full discussion

**Example:** Hospital board + IT team (beginner-intermediate mix) doing first TTX. Need to understand what happens, not stress about speed.

---

### Gamified TTX Best For:

**Participant Profile:**
- [ ] Technical IR team (experienced with incidents)
- [ ] Competitive group (responds to challenge)
- [ ] High energy environment
- [ ] Medium-large group (10-30 people, can have parallel teams)
- [ ] Advanced maturity IR organizations

**Exercise Goals:**
- [ ] Test response speed and decision-making
- [ ] Identify weak points in processes
- [ ] Build team cohesion through challenge
- [ ] Assessment/validation primary goal

**Time Available:**
- [ ] 2-4 hours (compressed timeline)
- [ ] Can sustain high pace
- [ ] Participants want "realistic" pressure

**Example:** SOC team doing quarterly IR challenge. Want to test how fast they respond, decision quality under pressure, team coordination.

---

### Blended TTX Best For:

**Participant Profile:**
- [ ] Mixed experience levels (some technical, some not)
- [ ] Moderate learning + moderate challenge
- [ ] Most real-world consultancies

**Exercise Goals:**
- [ ] Learn AND validate IR capability
- [ ] Build engagement while teaching
- [ ] Identify gaps AND improve response

**Time Available:**
- [ ] 3-4 hours (balanced approach)
- [ ] Some pressure, some reflection time

**Example:** Most consultant engagements. Need executives to learn, need technicians to be challenged, need visibility on what works and what doesn't.

---

## ADAPTING COMPONENTS BY STYLE

### Inject Library Adaptations

| Component | Traditional | Blended | Gamified |
|-----------|-------------|---------|----------|
| **Delivery** | Facilitator reads at discussion pace | Scheduled with 10-15 min response window | Timed arrivals on schedule |
| **Surprise** | Telegraphed ("Next we'll discuss...") | Some surprise elements | High surprise ("Unexpected inject!") |
| **Timing** | Whenever group finishes discussion | Clock-driven with flexibility | Strict clock (T+15, T+25, etc.) |
| **Response Time** | 20-30 minutes per inject | 10-15 minutes per inject | 3-5 minutes per inject |
| **Facilitator Role** | Guides discussion | Manages time + discussion | Enforces deadlines + tracks impact |
| **Follow-up** | Detailed debrief of each inject | Quick debrief + move forward | Move forward, debrief later |

### Decision Point Adaptations

| Component | Traditional | Blended | Gamified |
|-----------|-------------|---------|----------|
| **Time Allowed** | 20-30 min discussion | 15 min discussion + 5 min decision | 5 min decision, no discussion |
| **Information Given** | All context upfront | Most context, some gaps | Limited context, learn as you go |
| **Options Presented** | All options clearly laid out | Options clear, but time pressure | Limited options, must choose fast |
| **Documentation** | Thorough reasoning documented | Brief decision + rationale | Decision logged, debrief later |
| **Scoring** | N/A | Light tracking of decision quality | Point-based scoring |
| **Reversal** | "Can we reconsider?" - Yes, discuss | "Time's up, moving forward" | Absolutely not, live with it |

### Complication Adaptations

| Component | Traditional | Blended | Gamified |
|-----------|-------------|---------|----------|
| **When Introduced** | Clearly telegraphed ("Next issue...") | With some warning (5 min) | Completely surprise |
| **How Many** | 1-2 total (discussed thoroughly) | 3-4 (some surprise, some expected) | 5+ (cascading surprises) |
| **Response Time** | Unlimited, discuss fully | 10 min to discuss, decide | 3 min to respond |
| **Consequence Tracking** | Discussed & understood | Tracked with light scoring | Heavily scored |
| **Cascade Effect** | Individual issues addressed | Some cascade effect | Cascade is core mechanic |

---

## FACILITATOR GUIDE BY STYLE

### Traditional TTX Facilitator Role

**Before Exercise:**
- Read entire scenario and plan discussion flow
- Prepare discussion prompts ("Why did you choose that?")
- Prepare teaching points for common pitfalls
- Plan timing (assume 20-30 min per major decision)

**During Exercise:**
- Read injects clearly, give group time to absorb
- Ask probing questions (don't tell them answers)
- Allow disagreement and debate (it's learning)
- Track decisions on flip chart/document
- Coach using facilitation prompts from library
- Pause for reflection/discussion as needed

**Tone:** Socratic (guide through questions), supportive, patient

**Pace:** Group controls (you don't rush them)

---

### Gamified TTX Facilitator Role

**Before Exercise:**
- Set up scoreboard/tracking visible to all
- Explain scoring system and rules
- Prepare timing (know when each inject arrives)
- Brief on high-pace expectations ("This will be fast")

**During Exercise:**
- Announce time remaining ("5 minutes to decide")
- Deliver injects on schedule (don't wait for group)
- Track points/consequences in real-time
- Move forward decisively ("Time's up, here's what happens")
- Inject surprise/cascading complications
- Keep energy high

**Tone:** Energetic, demanding, fast-paced

**Pace:** Facilitator controls (you drive the clock)

---

### Blended TTX Facilitator Role

**Before Exercise:**
- Have scoreboard for impact tracking (optional, light)
- Plan timing with flexibility (T+30 is "about" 30 min)
- Prepare both discussion prompts AND surprise injects
- Plan where to shift pace (start slow, accelerate mid-exercise)

**During Exercise:**
- Phase 1: Guide discussion, deep questions
- Phase 2: Tighten timeline, add surprise elements
- Phase 3: Move faster, track consequences
- Allow some debate, but not endless discussion
- Track decisions for debrief

**Tone:** Professional, engaging, balanced between support and challenge

**Pace:** Controlled flexibility (start slow, accelerate)

---

## STARTER PROMPT ADAPTATIONS

The STARTER-PROMPT.md can be adapted for style. Here are key prompt variations:

### For Traditional TTX

**Prompt Adaptation:**
```
[After collecting basic information]

"For this exercise, we're taking a DISCUSSION-FOCUSED approach.
We'll move through the scenario together, discussing each phase thoroughly.

My role: Present injects and ask questions to guide your thinking
Your role: Discuss, debate, decide, and learn

There's no time pressure. We have time to think deeply about tradeoffs.
We'll debrief each major decision to understand your reasoning.

Ready?"
```

**Output Instructions to AI:**
"Generate a traditional TTX with:
- Linear scenario flow (one phase at a time)
- 3-5 major decision points (deep discussion expected)
- Facilitator prompts for 20-30 min discussions
- Learning-focused debrief guidance
- NO time pressure mechanics"

### For Gamified TTX

**Prompt Adaptation:**
```
[After collecting basic information]

"For this exercise, we're taking a GAME-ENHANCED approach with real time pressure.

Injects will arrive on a schedule. You'll have LIMITED TIME to respond.
Your decisions will be scored and tracked.
Consequences accumulate - bad decisions cost you.

This is intense. You'll feel the pressure. That's intentional.
This is as close to a real incident as tabletop gets.

Ready?"
```

**Output Instructions to AI:**
"Generate a gamified TTX with:
- Timed injects on strict schedule
- Point-based scoring for decision quality
- Cascading complications
- Resource tracking (budget, systems, timeline)
- High-intensity facilitation notes"

### For Blended TTX

**Prompt Adaptation:**
```
[After collecting basic information]

"For this exercise, we're taking a BALANCED approach.

First half: We'll discuss the scenario and your initial strategy (learning phase)
Second half: We'll add time pressure and surprise elements (challenge phase)

You'll have discussion time, but also need to decide under some pressure.
We're building both understanding AND testing your response capability.

Ready?"
```

**Output Instructions to AI:**
"Generate a blended TTX with:
- Structured scenario (discussion-based first half)
- Tightening timeline (second half faster)
- Light scoring/tracking (not heavily weighted)
- 2-3 surprise complications (not cascading)
- Balanced facilitation tone"

---

## PHASED APPROACH EXAMPLE

Here's how a 4-hour blended exercise might flow:

### Phase 1: Understanding (T+0 to T+60, Traditional Style)

**Goal:** Understand situation, form initial strategy

```
T+0-15:   Scenario briefing + DET-1 (Initial Alert)
          Group discusses: "What happened? What do we do?"
          Facilitator guides discussion, no rush

T+15-30:  DET-2 (Scope Confirmation)
          Group discusses: "This is bigger than we thought. Now what?"
          Facilitator: "What assumptions need to change?"

T+30-45:  INV-1 + INV-2 (Backup Status + Forensic Timeline)
          Group discusses: "How long were they in our network?"
          Facilitator: "What does that mean for our recovery approach?"

T+45-60:  DP-1 (Containment Decision) - MAJOR DECISION POINT
          Group thoroughly discusses options A/B/C
          Group documents decision + reasoning
          Facilitator: "Tell me why you chose that?"
```

### Phase 2: Challenge (T+60 to T+120, Blended Style)

**Goal:** Test decision-making under pressure, add complexity

```
T+60-75:  INV-3 (Lateral Movement Surprise)
          Scope expanded beyond expectations
          Mild time pressure: "You have 10 min to recalibrate"
          Group adjusts strategy

T+75-90:  CONT-1 (Executive Pressure) + DP-2 (Ransom Decision)
          Major decision with competing pressures
          Time pressure: "You have 15 min to brief the CEO"
          Group documents decision

T+90-105: Complication arrives (unexpected + impacts previous decision)
          BC-1 or SC-1 or REG-1 (selected based on group's decisions)
          Time pressure: "How do you adapt? 10 min to decide"
          Consequences tracked (costs increase, timeline extends)

T+105-120: Recovery Phase Begins (REC-1)
          "Here's where you are now (factoring in your decisions)"
          Time pressure increases: "5 min to decide recovery approach"
          Group finalizes strategy
```

### Phase 3: Debrief (T+120 to T+240, Learning Focus)

**Goal:** Reflect on decisions, extract lessons

```
[If using gamified scoring]
"Here's your impact summary:
- Decision quality: 68/100
- Budget remaining: 60% (good cost management)
- Recovery timeline: 14 days (expected 10 days due to complications)
- Regulatory exposure: Medium (notified on time, not early)
- Team alignment: Good (clear communication observed)"

Structured debrief:
1. "Walk me through your ransom decision. Why that choice?"
2. "What surprised you about how the incident evolved?"
3. "What would you do differently if you could rewind?"
4. "What will you change in your actual IR plan?"
5. "Any 'aha' moments you want to discuss?"
```

---

## RECOMMENDATIONS FOR PHASE 3 (Scenario Expansion)

When we add more scenarios (Insider Threat, Data Breach, DDoS, etc.), we should plan for style variations from the start:

### Scenarios Suited to Each Style

**Traditional Focus:**
- Data Breach (regulatory/procedural learning)
- Cloud Misconfiguration (discovery/learning pace)

**Gamified Focus:**
- DDoS / Availability (time pressure, real-time response)
- Business Email Compromise (fast decision-making)

**Balanced (Blended):**
- Ransomware (default - what we're building)
- Insider Threat (complex, needs both discussion and pressure)
- Supply Chain (complex, multi-org coordination)
- Third-Party Vendor (complex, external constraints)

### Component Library Considerations

For Phase 3, each scenario's component libraries should include:

```
INJECT-LIBRARY for [SCENARIO]
├── Traditional-style injects (discussion-paced)
├── Gamified-style injects (time-pressured)
└── Timing variants (5-min, 10-min, 20-min response windows)

DECISION-POINTS for [SCENARIO]
├── Traditional-discussion (20-30 min per decision)
├── Gamified-challenge (5 min per decision)
└── Scoring variants (if applicable to scenario)

COMPLICATIONS for [SCENARIO]
├── Telegraphed (traditional)
├── Surprise (gamified)
└── Cascade options (gamified)
```

---

## Summary: Choosing and Executing Your Style

| Dimension | Traditional | Blended | Gamified |
|-----------|-------------|---------|----------|
| **Participant Experience** | "Learning moment" | "Challenging but fair" | "Intense/competitive" |
| **Facilitator Pace** | Group-controlled | Hybrid | Facilitator-controlled |
| **Time per Major Decision** | 20-30 min | 15 min | 5 min |
| **Surprise Elements** | Few/none | Moderate | Many |
| **Scoring** | None | Light | Heavy |
| **Team vs. Team** | N/A | Optional | Common |
| **Best Scenario Type** | Any (works for all) | Ransomware | DDoS, BEC |
| **Maturity Level** | All | All | Advanced IR teams |
| **Engagement Level** | Intellectual | High | Very High |
| **Learning Retention** | High | Very High | High (+ skills) |

**Golden Rule:**
- **Start simple and safe** (traditional approach)
- **Add pressure gradually** (blended approach)
- **Only gamify if group is ready** (advanced teams with strong IR foundations)

Your STARTER-PROMPT should ask: "What's your preferred learning style—discussion-focused, balanced, or high-pressure challenge?" Then AI adapts output accordingly.
