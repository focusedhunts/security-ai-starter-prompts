# AI Generation Guide for TTX Exercises

**Purpose:** This guide instructs the AI (ChatGPT, Claude, etc.) on how to generate appropriate TTX exercises based on the 5 consultant questions.

**Use Case:** When a consultant pastes STARTER-PROMPT.md into an AI tool and answers the 5 questions, the AI uses THIS guide to generate the correct style/duration/difficulty variant.

---

## How to Use This Guide

After the consultant answers the 5 questions, you (the AI) will:

1. **Understand the constraints** (Q1-Q5)
2. **Select from component libraries** (inject-library.md, decision-points.md, complications.md)
3. **Apply style-specific guidance** (from TTX-STYLE-GUIDE.md)
4. **Generate duration-appropriate content** (using templates)
5. **Output a facilitator package** (markdown document ready to use)

---

## Step 1: Parse the 5 Questions

### Question 1: Client Context
**Extract:**
- **Industry:** Healthcare / Finance / Retail / Manufacturing / Technology / Other
- **Size:** Small (<500 people) / Medium (500-5000) / Large (5000+)
- **IR Maturity:** Beginner / Intermediate / Advanced
- **Specific Context:** Recent incident? Regulatory pressure? Staffing issues?

**Impact on Generation:**
- Industry determines customization layer (healthcare = HIPAA focus, finance = PCI focus, etc.)
- Size affects complication intensity (bigger companies = more complex scope)
- Maturity affects difficulty of injects (beginners = simpler, advanced = ambiguous)
- Context may drive specific decision point emphasis

---

### Question 2: Exercise Objective
**Extract:**
- What capability is being tested? (IR plan validation, communication, decision-making, regulatory readiness, technical response, business continuity, leadership coordination, etc.)

**Impact on Generation:**
- If "IR plan validation" → Focus on decision quality evaluation
- If "communication" → Emphasize multi-stakeholder notifications and messaging
- If "regulatory readiness" → Highlight compliance and notification requirements
- If "decision-making" → Add ambiguity and pressure to decision points
- If "technical response" → Include detailed forensic and containment details

---

### Question 3: Duration & Format
**Extract:**
- Duration: 2-hour / 4-hour / 6-hour / Full-day
- Format: In-person / Virtual / Hybrid

**Impact on Generation:**

| Duration | Injects | Decision Points | Complications | Focus |
|----------|---------|-----------------|----------------|-------|
| **2-hour** | 8-12 | 2-3 | 1-2 (early) | Detection & initial response |
| **4-hour** | 15-20 | 4-5 | 2-3 (mid & late) | Full IR lifecycle |
| **6-hour** | 25-35 | All 5 | 4-5 (cascading) | Deep investigation, parallel threads |
| **Full-day** | 40+ | All 5 | 6+ (complex interactions) | Leadership, regulatory, recovery |

**Format Impact:**
- Virtual: Focus on clear written instructions for breakout rooms
- In-person: Can use more complex group interactions and side conversations
- Hybrid: Provide alternatives for both modalities

---

### Question 4: Participant Profile
**Extract:**
- Skill distribution: Technical / Executive / Mixed
- Approx. count of participants
- Any role-specific notes

**Impact on Generation:**
- Technical-heavy → More forensic detail, technical decision complexity
- Executive-heavy → Focus on business impact, regulatory, stakeholder communication
- Mixed → Balance between technical detail and business context
- Larger groups → More breakout room options, parallel discussion threads
- Smaller groups → More whole-group discussion

---

### Question 5: Exercise Style
**Extract:**
- Traditional / Blended / Gamified

**Impact on Generation:**
- **Traditional:** No time pressure, all options presented, focus on discussion depth
- **Blended:** Moderate time pressure, most information given, balanced challenge
- **Gamified:** Strict time limits, limited info, point scoring, competitive elements

---

## Step 2: Select Inject Library Items

**Source:** Reference `components/inject-library.md`

### By Duration:

**2-hour Exercise (8-12 injects):**
- Detection Phase: DET-1, DET-2, DET-3 (all three)
- Investigation Phase: INV-1 only (1 inject)
- Containment: CONT-1 (1 inject, used as decision trigger)
- Response: RESP-1 (1 inject)
- Recovery: REC-1 (1 inject)
- Decision Points: 2-3 major decisions
- **Total: 8-10 injects for 2 hours**

**4-hour Exercise (15-20 injects):**
- Detection: DET-1, DET-2, DET-3 (all three)
- Investigation: INV-1, INV-2, INV-3 (all three)
- Containment: CONT-1, CONT-2 (leadership pressure)
- Response: RESP-1, RESP-2, RESP-3 (full response path)
- Recovery: REC-1, REC-2 (recovery complications)
- Decision Points: 4-5 major decisions
- **Total: 15-18 injects for 4 hours**

**6-hour Exercise (25-35 injects):**
- All injects from each phase (multiple variants)
- Include parallel decision threads
- All 5 decision points fully developed
- Multiple complication interactions
- **Total: 25-35 injects for 6 hours**

**Full-day (40+ injects):**
- All injects with detailed variations
- Multiple parallel incident threads
- Full leadership/regulatory coordination
- Post-incident planning
- **Total: 40+ injects**

### Customize Injects by Industry:

For each selected inject, apply the industry customization from `inject-library.md`:
- **Healthcare:** Add HIPAA notification requirements, patient care impact
- **Finance:** Add PCI/SEC considerations, wire fraud complications, regulatory reporting
- **Retail:** Add customer data focus, seasonal timing impact
- **Manufacturing:** Add OT/IT convergence, production disruption
- **Technology:** Add multi-tenant impact, SLA violations

---

## Step 3: Select Decision Points

**Source:** Reference `components/decision-points.md`

### By Duration & Difficulty:

**2-hour Exercise (2-3 decisions):**
- DP-1: Containment Approach (always included)
- DP-2: Ransom Payment OR Recovery Strategy (pick one)
- Evaluation emphasis: Single best answer vs. good reasoning

**4-hour Exercise (4-5 decisions):**
- DP-1: Containment Approach
- DP-2: Ransom Payment
- DP-3: Notification Timing
- DP-4 or DP-5: Recovery OR Communication (pick based on objective)

**6-hour+ Exercise (all 5 decisions):**
- DP-1: Containment Approach & Timing
- DP-2: Ransom Payment Decision
- DP-3: Data Breach Notification
- DP-4: Recovery Strategy
- DP-5: Stakeholder Communication & Leadership Briefing
- Each decision has deeper exploration of consequences

---

## Step 4: Select & Apply Complications

**Source:** Reference `components/complications.md`

### By Duration:

| Duration | # Complications | When Triggered | Branching |
|----------|-----------------|-----------------|-----------|
| 2-hour | 1-2 | Early (T+45 min) | None - always same |
| 4-hour | 2-3 | Mid & late (T+90, T+150) | Slight variations |
| 6-hour | 4-5 | Distributed throughout | Based on decisions |
| Full-day | 6+ | Cascading effects | Multiple paths |

### By Style:

**Traditional:**
- Fewer complications (1-2 for 2-hour, 2-3 for 4-hour)
- Introduced clearly: "Here's the next challenge..."
- Facilitator controls timing
- Same complications regardless of previous decisions

**Blended:**
- Medium complications (2-3 for 2-hour, 3-4 for 4-hour)
- Introduced with 5-10 minute warning: "Here's something coming..."
- Mixed timing (some facilitor-paced, some scheduled)
- Minor variations if decisions were particularly good/bad

**Gamified:**
- More complications (2-3 for 2-hour, 4-5 for 4-hour)
- Surprise introductions (no warning or minimal)
- Strict scheduled timing (T+20, T+40, etc.)
- Conditional complications based on earlier decisions and scores

### By Difficulty:

**Beginner Group:**
- Fewer complications
- Easier complications (backup issues, slower scope expansion)
- Complications early (so team can adapt)

**Intermediate Group:**
- Standard complications (mid-level difficulty)
- Mix of early & late complications
- Some parallel complications

**Advanced Group:**
- More complications (4-5+ even in 4-hour)
- Complex complications with cascading effects
- Complications triggered by earlier decisions
- Second-order complications (caused by how they handled first complication)

---

## Step 5: Apply Style-Specific Formatting

### TRADITIONAL Style Generation:

**Inject Presentation:**
```
[Inject Title]
Timing: [Time facilitator chooses, not strict]
Delivery: [Facilitator reads content]

**Content:** [Full details provided]

**Facilitator Notes:**
- Discussion Points: [What should the group discuss?]
- Expected Responses: [What might they say? How to coach?]
- Duration: Allow 20-30 minutes discussion
- Flexibility: Adjust timing based on group engagement
```

**Decision Point Presentation:**
```
[Decision Title]
Situation: [Full context provided]

**All Options Presented:**
- Option A: [Full details + pros/cons]
- Option B: [Full details + pros/cons]
- Option C: [Full details + pros/cons]

**Discussion Guide:**
- "What are we trying to achieve?"
- "What are the risks of each option?"
- "Can we pivot if we're wrong?"

**Facilitator Role:** Ask Socratic questions, guide thinking, don't rush to decision
**Typical Time:** 20-30 minutes discussion
```

**Complication Presentation:**
```
**Complication: [Name]**
Introduction: "Here's what's happening now: [Clear statement]"
Impact: [What changes based on this?]
Discussion: "How does this affect our previous decision?"
```

**No Scoring:** Don't include point allocations or score tracking

---

### BLENDED Style Generation:

**Inject Presentation:**
```
[Inject Title]
Timing: T+[Time] minutes (or after participants complete [milestone])
Delivery: [Chat/Email/Facilitator announcement]
Response Window: [10-15 minutes]

**Content:** [Most details provided, 1-2 gaps for learning]

**Facilitator Notes:**
- Announce: "You have [X] minutes to respond to this inject"
- Facilitator role: Time tracker, guide discussion
- Expected Response: [What should they do?]
- If stuck: [Coaching prompts]
- Duration: 10 min discussion + 5 min decision
```

**Decision Point Presentation:**
```
[Decision Title]
Timing: T+[Time] (announce timing)
Situation: [Most context given, some details unclear]

**Options Provided:**
- Option A: [Most details, some trade-offs unclear]
- Option B: [Most details, some trade-offs unclear]
- Option C: [Most details, some trade-offs unclear]

**Facilitation:**
- T+[Time] to T+[Time+10]: Present situation, allow questions
- T+[Time+10] to T+[Time+15]: Group discusses
- T+[Time+15]: "Decision time. What are you doing?"
- Announce scores for this decision point

**Score for This Decision:** [Point allocation]
```

**Light Scoring:**
```
Decision Point Score: [X points for choosing Option A, Y for B, Z for C]
Bonus Points: [Points for supporting reasoning]
Running Score: [Total so far]
Note: "This is tracking capability, not determining winners"
```

**Complications with Warning:**
```
**Complication: [Name]**
T+[Time-10]: Announcement: "In about 10 minutes, something's going to change"
T+[Time]: "This just happened: [Complication details]"
Impact: [What changes?]
```

---

### GAMIFIED Style Generation:

**Inject Presentation:**
```
[Inject Title]
Timing: T+[Time] (strict, on schedule)
Delivery: [Rapid announcement, brief content]

**Content (Abbreviated):** [Key details only, less context]

**Facilitator Script:**
"T+[Time]: [Rapid-fire announcement of inject]
 [Brief details]
 What's your response? You have [3-5] minutes."

**Facilitator Role:** Strict time keeper, move fast, record decision/response
**Response Window:** [X minutes, strict]
**Next Inject Triggers at:** T+[Time], regardless of readiness
```

**Decision Point Presentation:**
```
[Decision Title]
Timing: T+[Time] (strict)
Situation: [Limited context, some ambiguity]

**Options NOT Pre-stated:** "Here are your constraints: [Framework]
You have [5] minutes. Go."

**Facilitator Role:**
- T+[Time]: Announce decision point and constraint
- T+[Time] to T+[Time+4]: Team discusses
- T+[Time+4:00]: "Decision time. What are you doing?"
- T+[Time+5]: Record decision, announce score, move to next inject
- NO additional discussion or debate after decision

**Points for This Decision:**
- Option A chosen: [X] points (+ [Y] bonus for speed)
- Option B chosen: [X] points (+ [Y] bonus for business acumen)
- Option C chosen: [X] points (+ [Y] bonus for innovation)
- Timing bonus: +[points] if decided before T+4:30
- Speed bonus: +[points] if decided before T+3:00
```

**Resource Tracking (Gamified Only):**
```
**Scenario Status Tracker:**
System Availability: [Start: 100%] → [After each decision/complication, adjust]
Customer Confidence: [Start: 100%] → [Decreases with each poor decision]
Regulatory Risk: [Start: 0%] → [Increases with notification delays]
Financial Cost: [Start: $0] → [Increases with recovery efforts]

**Track After Each Major Event:**
"After that decision, your systems availability dropped to [85%]
Your customer confidence is now at [90%]
Regulatory risk increased to [15%]
Financial cost so far: $[amount]"
```

**Surprise Complications (Gamified):**
```
**Complication: [Name]**
T+[Time]: "ALERT: [Dramatic announcement]
[Brief details]
This changes everything. How do you respond? [X] minutes."
No warning. No discussion time. Immediate impact assessment required.

**Points Affected:**
- Handled well: +[X] points
- Handled poorly: -[X] points or additional resource loss
```

**Score Summary Tracking:**
```
**Score Board (Updated After Each Decision)**
Decision 1 (Containment): [X] points ([details])
Complication 1 Response: [X] points
Decision 2 (Ransom): [X] points
Complication 2 Response: [X] points
[etc...]

Running Total: [X] points
Scenario Time Remaining: [X] minutes
Status: System Availability [85%], Customer Confidence [90%], Regulatory Risk [15%]
```

---

## Step 5A: CRITICAL - Inject Generation Standards

**MANDATORY REQUIREMENT:** Every inject in every generated timeline must follow this standard structure.

### Required Inject Format:

**INJECT [NUMBER]: [Descriptive Title]**

- **Timing:** T+[XX] minutes (relative to exercise start)
- **Duration:** [XX-XX] minutes (expected discussion time)
- **Delivery:** [Method: email/phone call/video call/screen share/message/etc.]

#### Required Components (ALL MUST BE PRESENT):

**1. Content (300-500 words minimum)**
   - For emails: Include FROM/TO/SUBJECT/BODY format
   - For phone calls: Include speaker identification and dialogue format
   - Include specific data points: numbers, system names, timestamps, file names, employee names
   - Use industry-appropriate technical language for the organization type
   - Make communications realistic and believable as the participant would actually receive them
   - Avoid generic placeholder text

**2. Expected Response (4-6 bullet points)**
   - List specific actions the team should take
   - Include both technical AND communication responses
   - Indicate what "good" looks like for this inject

**3. Facilitator Prompts (4-6 Socratic questions - MANDATORY)**
   - Use open-ended questions, not statements
   - Examples:
     - "Tell me more about why you're thinking that..."
     - "What would change your mind about this approach?"
     - "I'm hearing different perspectives—how do you reconcile those?"
     - "What information would help you make this decision?"
     - "What's the worst that could happen if you're wrong?"
   - Questions should encourage deeper thinking, not surface-level answers

**4. Evaluation Points (4-6 checkboxes - MANDATORY)**
   - Format: ☐ Observable criterion
   - Focus on PROCESS, not "right answers"
   - Examples:
     - ☐ Do they take the alert seriously (not dismiss as false positive)?
     - ☐ Do they immediately check for other affected systems?
     - ☐ Do they document their reasoning?
   - Each checkbox should be observable by the facilitator
   - Use these to assess team capability, not to score "correct" answers

### Inject Quantity Requirements (STRICT - NON-NEGOTIABLE):

- **2-hour exercise:** 8-12 injects MINIMUM (not fewer)
- **4-hour exercise:** 15-20 injects MINIMUM (not fewer - this is critical)
- **6-hour exercise:** 25-35 injects MINIMUM
- **Full-day exercise:** 35-45 injects MINIMUM

**Critical Note:** If your generated exercise has fewer injects than the minimum for the duration, the exercise is INCOMPLETE. You must revise to meet the minimum.

### Quality Validation Checklist:

Before considering an inject complete, verify:
- ☐ Content section: 300-500 words (count them)
- ☐ Content is realistic and industry-specific
- ☐ Facilitator Prompts: Present and Socratic (4-6 questions)
- ☐ Evaluation Points: Present with checkbox format (4-6 criteria)
- ☐ Expected Response: Realistic actions listed (4-6 items)
- ☐ Timing: Relative to exercise start (T+ format)
- ☐ Delivery method: Specific and realistic

**Before completing the entire facilitator guide:**
- ☐ Count total injects: [____] (verify against minimum for duration)
- ☐ Every inject has all 4 required components
- ☐ No injects are missing facilitator prompts
- ☐ No injects are missing evaluation criteria

---

## Step 5B: CRITICAL - Export Markers (MANDATORY)

**REQUIRED:** Every facilitator guide output MUST include exactly 7 export marker pairs, in exact format shown below.

Export markers are HTML comments that allow consultants to extract specific sections for team sharing. They are NON-NEGOTIABLE and must be present in every output.

### The 7 Required Export Marker Pairs (ALL MUST BE PRESENT):

**1. FACILITATOR-GUIDE (Complete facilitator package - all injects, decisions, complications, debrief)**
```
<!-- EXPORT MARKER: FACILITATOR-GUIDE START -->
[Entire document content]
<!-- EXPORT MARKER: FACILITATOR-GUIDE END -->
```

**2. SCENARIO-NARRATIVE (Participant-safe, no spoilers - organization profile, threat actor, initial situation)**
```
<!-- EXPORT MARKER: SCENARIO-NARRATIVE START -->
[Organization description, threat actor profile, initial discovery]
[NO inject details, NO complication previews]
<!-- EXPORT MARKER: SCENARIO-NARRATIVE END -->
```

**3. INJECT-TIMELINE (Facilitator-only full inject sequence with all details)**
```
<!-- EXPORT MARKER: INJECT-TIMELINE START -->
[Complete inject sequence with all components]
[May include sensitive content and facilitator notes]
<!-- EXPORT MARKER: INJECT-TIMELINE END -->
```

**4. DECISION-POINTS (All major decision point frameworks and facilitator guidance)**
```
<!-- EXPORT MARKER: DECISION-POINTS START -->
[Each decision point with options, trade-offs, Socratic prompts, evaluation criteria]
<!-- EXPORT MARKER: DECISION-POINTS END -->
```

**5. COMPLICATIONS (Complication sequence with triggers and delivery guidance)**
```
<!-- EXPORT MARKER: COMPLICATIONS START -->
[All complications with how/when to introduce them, impact, and follow-up]
<!-- EXPORT MARKER: COMPLICATIONS END -->
```

**6. DEBRIEF-TEMPLATE (Post-exercise review structure and questions)**
```
<!-- EXPORT MARKER: DEBRIEF-TEMPLATE START -->
[Complete debrief structure with timing, discussion questions, evaluation framework]
<!-- EXPORT MARKER: DEBRIEF-TEMPLATE END -->
```

**7. PARTICIPANT-BRIEF (Non-spoiler participant materials - what they receive pre-exercise)**
```
<!-- EXPORT MARKER: PARTICIPANT-BRIEF START -->
[Welcome letter, ground rules, initial briefing, role assignments]
[Must NOT contain inject details or complication previews]
<!-- EXPORT MARKER: PARTICIPANT-BRIEF END -->
```

### Placement Instructions:

1. **Place markers at SECTION BOUNDARIES:**
   - FACILITATOR-GUIDE wraps the ENTIRE output
   - SCENARIO-NARRATIVE wraps only the scenario description section
   - INJECT-TIMELINE wraps the complete inject table/sequence
   - DECISION-POINTS wraps all decision point sections
   - COMPLICATIONS wraps the complications sequence
   - DEBRIEF-TEMPLATE wraps the debrief structure section
   - PARTICIPANT-BRIEF wraps participant materials

2. **Use EXACT formatting:**
   - No variations in marker names
   - Always include START and END tags
   - HTML comment format: `<!-- MARKER: NAME START -->` ... `<!-- MARKER: NAME END -->`

3. **Markers are invisible:**
   - Markers are HTML comments and won't appear when rendered
   - They allow consultants to search and extract sections
   - They enable automated processing of sections

### Validation Checklist:

Before submitting your output, verify ALL 7 markers:
- ☐ FACILITATOR-GUIDE START ... END (wraps everything)
- ☐ SCENARIO-NARRATIVE START ... END (in appropriate section)
- ☐ INJECT-TIMELINE START ... END (in timeline section)
- ☐ DECISION-POINTS START ... END (in decisions section)
- ☐ COMPLICATIONS START ... END (in complications section)
- ☐ DEBRIEF-TEMPLATE START ... END (in debrief section)
- ☐ PARTICIPANT-BRIEF START ... END (in participant materials)

**If ANY marker pair is missing, your output is INCOMPLETE and must be revised.**

### Why Export Markers Matter:

- Consultants can extract the SCENARIO-NARRATIVE to send to participants (no spoilers)
- Consultants can extract INJECT-TIMELINE for facilitator reference cards
- Consultants can extract DECISION-POINTS for training materials
- Consultants can extract PARTICIPANT-BRIEF for welcome packages
- Markers enable team sharing and document organization
- **Without markers, consultants cannot easily use the full functionality of the system**

---

## Step 5C: Decision Point Generation Template

**MANDATORY TEMPLATE:** Each major decision point must follow this comprehensive structure.

### Required Decision Point Components:

**DECISION POINT [NUMBER]: [Decision Title]**

#### 1. Setup & Context (300-400 words minimum)
- **Current situation summary:** What just happened that requires a decision?
- **Timeline context:** When in the exercise is this decision being made?
- **Information available to the team:** What data/reports/notifications do they have?
- **Time pressure or constraints:** Is there urgency? Any deadlines?
- **Stakeholder perspectives:** What are legal, finance, business, and technical considerations?
- **Financial/business impact:** What's at stake? What are the costs of delay?

#### 2. Options Framework (3+ options required)
Present minimum 3 options, each with:

**Option A: [Descriptive Title]**
- **Description:** (2-3 sentences explaining the approach)
- **Pros:** (3-4 specific, measurable benefits)
  - Pro 1: Specific outcome or advantage
  - Pro 2: Specific outcome or advantage
- **Cons:** (3-4 specific, measurable drawbacks)
  - Con 1: Specific risk or cost
  - Con 2: Specific risk or cost
- **Resources required:** What's needed to execute?
- **Timeline to execute:** How long will this take?
- **Risk level:** High/Medium/Low and why

**Option B: [Descriptive Title]** (same structure as Option A)

**Option C: [Descriptive Title - often a hybrid approach]** (same structure as Option A)

#### 3. Facilitator Prompts (6-8 Socratic questions - MANDATORY)
These guide the team's thinking without directing the answer:
- "What's the strongest argument FOR [Option A/B/C]?"
- "What's the strongest argument AGAINST [Option A/B/C]?"
- "How do you weigh the risk of [concern A] versus [concern B]?"
- "Who should be involved in making this decision?"
- "If we're wrong about this decision, what's the worst possible outcome?"
- "What information would change your mind about this option?"
- "How does this decision affect our next step in recovery?"
- "What would happen if we don't make a decision right now?"

#### 4. Evaluation Criteria (6-8 checkboxes - MANDATORY)
Focus on PROCESS and team capabilities, not "right answers":
- ☐ Does the team acknowledge the trade-offs of each option?
- ☐ Do they consider legal/regulatory/compliance constraints?
- ☐ Do they involve appropriate stakeholders (legal, finance, technical)?
- ☐ Do they document their reasoning for the decision?
- ☐ Can they articulate the risks they're accepting?
- ☐ Do they have a concrete next step after deciding?
- ☐ Do different functional groups participate in the discussion?
- ☐ Is the decision made with clear ownership/accountability?

#### 5. Expected Responses (2-3 most likely responses)
What might the team actually choose, and what does that tell you?
- **If they choose Option A:** This indicates [capability/concern to note]
- **If they choose Option B:** This indicates [capability/concern to note]
- **If they choose Option C:** This indicates [capability/concern to note]

#### 6. Time Allocation (style-specific)
- **Traditional:** 30-40 minutes for full discussion and debate
- **Blended:** 15-20 minutes (8 min setup + 7 min discuss + 5 min decide)
- **Gamified:** 5-10 minutes (2 min announce + 3 min discuss + 2 min decide)

#### 7. Team Integration Notes (for new teams)
Watch for and note:
- **Participation:** Who speaks? Who stays quiet? Do introverts get heard?
- **Cross-functional collaboration:** Do technical, legal, and business perspectives integrate?
- **Disagreement handling:** How do they resolve conflicting viewpoints?
- **Decision clarity:** Is the final decision clear and repeatable?
- **Documentation:** Do they capture why they chose this path?
- **Speed of alignment:** How quickly do they move from disagreement to consensus?

#### 8. Facilitator Coaching Notes
If the team is stuck or uncertain:
- **If silent:** "What would each of you say about [Option A]? I'd like to hear from everyone."
- **If rushed:** "Before we decide, let's make sure we've addressed the risks. What concerns do we have?"
- **If one person dominates:** "I'm hearing strong views from [name]. [Other person], what's your perspective?"
- **If circular debate:** "We keep coming back to the same points. Let's decide: what's the ONE factor that matters most?"

---

## Step 5D: Facilitator Preparation & Pre-Exercise Requirements

**MANDATORY SECTION:** Every facilitator package must include detailed preparation guidance.

### Facilitator Preparation Checklist (Week Before Exercise)

#### Before You Do Anything Else:
- [ ] **Read the entire exercise document** (1-2 hours) - understand flow, timing, objectives
- [ ] **Identify your co-facilitators or observers** - assign roles (timekeeper, inject deliverer, scribe, evaluator)
- [ ] **Understand your participant group** - review their names, roles, experience level, team dynamics
- [ ] **Test technical setup** (if virtual) - breakout rooms, chat, screen sharing, recording

#### Customization: Make It Real for Your Client
- [ ] **Update company names/systems** in all injects (make scenario specific to their organization)
- [ ] **Research their actual infrastructure** - what systems do they really use? Update references
- [ ] **Adjust timeline to current date** - make injects dated "today" not generic
- [ ] **Include real stakeholder names** - use their actual executive titles, legal counsel, insurance contacts
- [ ] **Customize financial figures** - use realistic numbers for their organization size
- [ ] **Reference their actual IR procedures** - if they have existing plans, reference them
- [ ] **Include their real vendors/contractors** - backup vendors, incident response firms, etc.

#### Materials Preparation:
- [ ] **Print facilitator scripts** - have inject content ready to read or deliver
- [ ] **Create facilitator reference cards** - one card per inject with key talking points
- [ ] **Prepare timing aids** - countdown timer, progress tracker, break schedule
- [ ] **Create participant materials** - scenario briefing (no spoilers), role assignments, ground rules
- [ ] **Prepare decision point worksheets** - printable option comparisons for each major decision
- [ ] **Create observation sheets** - templates for evaluators to track team responses
- [ ] **Prepare debrief materials** - discussion questions, evaluation summary form

#### Facilitator Mindset & Approach:
- [ ] **Understand the learning objectives** - what capability are we actually testing?
- [ ] **Know the "success" behaviors to watch for** - what indicates good IR response?
- [ ] **Plan how you'll handle time pressure** - how will you keep exercises on schedule?
- [ ] **Prepare coaching language** - collect 5-10 Socratic prompts you'll use
- [ ] **Plan for common pitfalls** - what usually goes wrong? How will you handle it?
- [ ] **Identify flexible points** - where can you add complexity if team is ahead of schedule?

#### Communications:
- [ ] **Send pre-exercise email to participants** (3 days before)
  - Welcome letter
  - Objectives and learning goals
  - Logistics (time, location, parking, tech setup)
  - Ground rules
  - What to bring/prepare
  - Who to contact with questions
- [ ] **Send initial scenario briefing** (optional, 1 day before)
  - Participant scenario narrative (non-spoiler)
  - Their roles in the exercise
  - Context: "You've just detected ransomware..."
- [ ] **Confirm attendance** - know who's coming and how many

#### Day-Of Preparation (90 minutes before start):
- [ ] **Arrive early** - set up room, test technology
- [ ] **Arrange seating** - arrange for visibility, cross-team interaction
- [ ] **Display exercise objectives** - have on screen or poster board
- [ ] **Set up timing displays** - visible countdown or elapsed time
- [ ] **Lay out any physical materials** - reference guides, worksheets, notepads
- [ ] **Brief co-facilitators** - make sure everyone knows their role
- [ ] **Do a tech check** - test all video, audio, screen sharing
- [ ] **Settle your own nerves** - do a quick run-through of opening remarks

### Customization Table (Example for Finance Organization):

| Placeholder | Generic Version | Customized for [Client Name] |
|-------------|-----------------|-----|
| **Organization Name** | "Global Financial Services Corp" | [Actual client name] |
| **Primary System** | "Corporate banking platform" | [Their actual core system] |
| **Backup Provider** | "Third-party backup vendor" | [Their actual backup company] |
| **Regulatory Contact** | "Banking regulator" | [Specific agency: OCC, Federal Reserve, etc.] |
| **Insurance Carrier** | "Cyber insurance provider" | [Their actual insurer] |
| **Executive Lead** | "CFO/CIO" | [Actual names and titles] |
| **Legal Counsel** | "Corporate legal team" | [Internal or external counsel name] |
| **System Recovery Time** | "72 hours" | [Their actual RTO based on SLAs] |
| **Data Volume** | "2TB customer data" | [Their actual affected systems] |
| **Regulatory Notification Timeline** | "30 days" | [GLBA requirement specific to them] |

---

## Step 5E: Scenario Narrative Enhancement Requirements

**MANDATORY:** Scenario narratives must be rich, detailed, and industry-specific.

### Scenario Narrative Structure:

#### 1. Organization Profile (200-300 words)
- **Company overview:** Size, structure, what they do
- **Industry position:** Market leader, regional player, niche provider?
- **IT infrastructure summary:** On-premise, cloud, hybrid? Key systems?
- **IR maturity level:** Do they have an existing IR plan? How prepared are they?
- **Recent context:** Any recent incidents, acquisitions, or changes? (Set up why they're vulnerable now)

#### 2. Threat Actor Profile (150-200 words)
- **Who are they?** Known threat group, ransomware-as-a-service, nation-state, criminal enterprise?
- **Motivation:** Financial, political, competitive advantage?
- **Tactics:** What methods do they typically use?
- **Known targets:** Have they hit similar organizations?
- **Typical demands:** How much do they usually ask for?

#### 3. Attack Timeline (Leading up to Exercise Start)
Provide a realistic timeline of how they got in:

**[Date -7 days]** - Initial compromise
- How did they enter? (Phishing, VPN access, supply chain, etc.)
- What did they do initially? (Reconnaissance, lateral movement)
- Why wasn't this detected?

**[Date -3 days]** - Persistence & Escalation
- How did they maintain access?
- What privileges did they gain?
- What systems did they compromise?

**[Date -1 day]** - Preparation for Encryption
- What reconnaissance did they perform?
- Did they steal data?
- What systems will be affected?

**[Date -6 hours]** - Pre-Encryption Activities
- Any final preparations?
- Any early warning signs?

#### 4. Initial Discovery (Exercise Start - T+0)
This is where the exercise begins. Describe:
- **What triggered discovery?** Alert? User complaint? System outage?
- **Who discovered it?** Which team member/function?
- **Initial scope understanding:** What do they think happened? (Usually underestimated)
- **Initial alert/report:** What message or information did they receive?
- **Immediate reaction:** What's the emotional/urgency context?

**Example:** "It's 6:45 AM Tuesday. The Help Desk received a support ticket from accounting. They report that their files have a .abc extension instead of .xlsx, and they see a file called 'READ_ME.txt' on their Desktop. The Help Desk supervisor calls the IT Manager, who calls you."

### Critical Scenario Details to Include:

- **Systems affected:** Which systems will be hit? (List 5-8 specific systems by name)
- **Data at risk:** What data will be encrypted? (Customer data, financial records, trade secrets, patient data?)
- **Business impact:** What business functions are impacted? (Accounting, customer-facing operations, etc.)
- **Compliance implications:** What regulations apply? (GLBA, HIPAA, PCI-DSS, GDPR?)
- **Stakeholder impact:** Customers, partners, employees, regulators?
- **Recovery complexity:** How hard will recovery be? (Assess before exercise starts so injects reflect reality)

### Narrative Tone:
- **Realistic:** Use actual technical terms and realistic communication
- **Urgent but not panicked:** Convey seriousness without extreme drama
- **Specific:** Avoid generic language ("the network is down" → "Critical accounting systems are encrypted and inaccessible")
- **Grounded:** Reference their actual organization, not a fictional company

---

## Step 6: Generate Output Facilitator Package

### Package Structure:

1. **Exercise Overview** (1-2 pages)
   - Objectives
   - Participant roles
   - Logistics
   - Timing and breaks

2. **Scenario Narrative** (1-2 pages)
   - Initial detection
   - What participants inherit
   - Key background

3. **Inject Timeline Table** (1-3 pages)
   - All injects in order
   - Timing, delivery method, content, expected response
   - Facilitator notes for each

4. **Decision Point Guidance** (2-4 pages)
   - Each major decision point
   - Options and trade-offs
   - Facilitation approach (style-specific)
   - Scoring (if applicable)

5. **Complications Sequence** (1-2 pages)
   - When each complication triggers
   - How to introduce it (style-specific)
   - Impact and conversation starters

6. **Debrief Structure** (1 page)
   - Timeline
   - Key discussion questions
   - Evaluation framework

7. **Facilitator Notes** (1-2 pages)
   - Pre-exercise prep checklist
   - Common participant pitfalls
   - Coaching prompts
   - Recovery strategies if things go off-rails

8. **Participant Materials (Outline)** (1 page)
   - What participants receive pre-exercise
   - What they receive during exercise
   - Reference materials they'll need

---

## Examples of Generation

### Example 1: 2-Hour Gamified for Finance Company (Intermediate)

**Inputs:**
- Industry: Finance / Medium bank
- Objective: Decision-making under pressure
- Duration: 2-hour
- Participants: Mixed (IT + executive)
- Style: Gamified

**Generation Output:**
- 8 injects (rapid-fire, 15-min intervals)
- 2 decision points (DP-1: Containment, DP-2: Ransom)
- 2 complications (surprise, no warning)
- Strict timing (T+0, T+15, T+30, T+45, T+60, T+75, T+90, T+120)
- Point scoring with resource tracking
- Finance customizations (PCI focus, wire fraud risk, regulatory reporting)
- Heavy gamification elements (countdown, pressure, competitive scoring)

**Key Differences from 4-hour:**
- Fewer injects (8 vs. 15-20)
- Fewer decisions (2 vs. 4-5)
- Fewer complications (2 vs. 3-4)
- Faster pacing (strict timing, no flexibility)
- More aggressive gamification (higher point swings)

---

### Example 2: 4-Hour Blended for Healthcare (Intermediate)

**Inputs:**
- Industry: Healthcare / Large hospital system
- Objective: IR plan validation + communication
- Duration: 4-hour
- Participants: Mixed (IT + C-suite + compliance)
- Style: Blended

**Generation Output:**
- 15-18 injects (10-15 min response windows)
- 4-5 decision points (DP-1, 2, 3, 4)
- 3-4 complications (announced with 5-10 min warning)
- Moderate timing (flexible windows, not strict)
- Light scoring (informational, not competitive)
- Healthcare customizations (HIPAA focus, patient care impact, state health department)
- Balanced gamification (some time pressure, mostly discussion-focused)

**Key Differences from 2-hour:**
- More injects (15 vs. 8)
- More decisions (4 vs. 2)
- More complications (3 vs. 2)
- More flexibility in timing
- Lighter gamification (scoring is secondary)

---

### Example 3: 6-Hour Traditional for Technology Company (Advanced)

**Inputs:**
- Industry: Technology / Large SaaS
- Objective: Full IR capability assessment
- Duration: 6-hour
- Participants: Technical (with executive observers)
- Style: Traditional

**Generation Output:**
- 25-35 injects (with deep detail on each)
- All 5 decision points fully developed
- 4-5 complications (clearly introduced)
- No timing constraints (facilitator-paced)
- No scoring (focus on learning and discussion)
- Technology customizations (multi-tenant impact, SaaS considerations)
- Minimal gamification (pure discussion-focused)

**Key Differences from 4-hour:**
- Many more injects (25 vs. 15)
- All decision points included (vs. 4)
- More complications (4-5 vs. 3)
- Completely flexible timing
- Deep discussion (20-30 min per inject typical)
- Focus on understanding vs. performance

---

## Quality Checklist for Generated Exercises

### MANDATORY REQUIREMENTS (CRITICAL):

- [ ] **Inject Quantity:** Minimum met for duration (8-12 for 2hr, 15-20 for 4hr, 25+ for 6hr) - COUNT THEM
- [ ] **Export Markers:** All 7 marker pairs present and correctly formatted (FACILITATOR-GUIDE, SCENARIO-NARRATIVE, INJECT-TIMELINE, DECISION-POINTS, COMPLICATIONS, DEBRIEF-TEMPLATE, PARTICIPANT-BRIEF)
- [ ] **Inject Components:** Every inject includes ALL 4 required components:
  - ☐ Content (300-500 words)
  - ☐ Facilitator Prompts (4-6 Socratic questions)
  - ☐ Evaluation Points (4-6 checkboxes)
  - ☐ Expected Response (4-6 actions)
- [ ] **No Missing Facilitation:** Every inject has facilitator prompts; no placeholder text like "TBD" or "add facilitator notes"

### QUALITY REQUIREMENTS:

- [ ] **Duration Appropriate:** Right number of injects for duration (verify count)
- [ ] **Style Consistent:** All injects, decisions, complications follow style guidance
- [ ] **Timing Realistic:** Can be completed in stated duration with stated number of injects
- [ ] **Industry Customized:** References are industry-specific (HIPAA for healthcare, PCI for finance, etc.)
- [ ] **Difficulty Calibrated:** Complications and decision ambiguity match stated maturity level
- [ ] **Facilitator Supportive:** All injects include realistic facilitator notes, Socratic coaching prompts, expected responses
- [ ] **Decision Points Clear:** Each decision has Options A/B/C with clear trade-offs and facilitator guidance
- [ ] **Debrief Structured:** Post-exercise structure is clear and actionable
- [ ] **Participant Materials:** Outline includes what participants need to participate (non-spoiler format)

---

## Step 7: Format Output for External Sharing

### Export Markers for Team Sharing

To help consultants save and share your generated content with team members, structure your output with clear section markers.

**Format:**
```
<!-- EXPORT MARKER: [SectionName] START -->
[Content here]
<!-- EXPORT MARKER: [SectionName] END -->
```

**Required Export Markers in Your Output:**

1. **FACILITATOR-GUIDE** - Complete facilitator package (everything)
2. **SCENARIO-NARRATIVE** - Scenario description without spoilers (for participants to preview)
3. **INJECT-TIMELINE** - Full inject sequence (facilitator-only, may include sensitive content)
4. **DECISION-POINTS** - Decision frameworks and options
5. **DEBRIEF-TEMPLATE** - Post-exercise review structure
6. **PARTICIPANT-BRIEF** - Non-spoiler participant materials (what they receive pre-exercise)

**Example Marker Usage:**

```markdown
<!-- EXPORT MARKER: SCENARIO-NARRATIVE START -->
# Initial Briefing: Ransomware Attack Discovered

Your organization has just discovered evidence of ransomware on your network...
[scenario narrative continues without revealing injects or complications]
<!-- EXPORT MARKER: SCENARIO-NARRATIVE END -->

<!-- EXPORT MARKER: INJECT-TIMELINE START -->
## Inject Timeline

| Inject # | Timing | Content | Expected Response |
[inject table continues - this is facilitator-only]
<!-- EXPORT MARKER: INJECT-TIMELINE END -->
```

### File Saving Instructions for Consultants

Include this section at the end of your generated output:

---

**📥 How to Save and Share This Output**

### For Markdown (.md) Files:
1. Copy all content between START and END markers for your desired section
2. Paste into a plain text editor (Notepad, VS Code, Word, etc.)
3. Save with .md extension following naming convention: `[ClientName]_[ScenarioType]_[Section]_[Date].md`
4. Example: `HealthcareOrg_Ransomware_Facilitator_2024-02-15.md`

### For Text (.txt) Files:
1. Same process as markdown, but save with .txt extension
2. Use for non-technical stakeholders without markdown viewers
3. Example: `HealthcareOrg_Ransomware_ParticipantBrief_2024-02-15.txt`

### For PowerPoint Creation:
1. Save the FACILITATOR-GUIDE section as markdown first
2. Read the DELIVERABLE-CREATION-GUIDE.md for comprehensive guidance on transforming markdown to professional PowerPoint:
   - Link: https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/designGuides/DELIVERABLE-CREATION-GUIDE.md
3. Follow visual enhancement suggestions for graphics (fake ransom notes, timelines, decision trees, threat actor visuals, etc.)
4. Use design principles section for colors, typography, layouts

### Sharing with Your Team:

| Recipient | Send | Format | Why |
|-----------|------|--------|-----|
| Lead Facilitator | FACILITATOR-GUIDE | .md or .pptx | Needs complete details and scripts |
| Co-Facilitator | FACILITATOR-GUIDE | .pdf | Needs scenario, injects, facilitator guidance |
| Observers/Evaluators | FACILITATOR-GUIDE + DECISION-POINTS | .pdf | Needs evaluation criteria and decision context |
| Participants | SCENARIO-NARRATIVE + PARTICIPANT-BRIEF | .pdf | Must NOT see injects or complications |
| Client Stakeholders | Executive summary only | .pdf | Overview only, no internal exercise details |
| Technical Team | INJECT-TIMELINE | .md | For pre-exercise technical prep |

### From ChatGPT:
1. Click the message you want to export
2. Click the "Copy" icon (or select all + copy)
3. Paste into text editor
4. Identify the section markers
5. Extract only the content between START and END markers for your desired section

### From Claude:
1. Select the text you want to export (or entire message)
2. Right-click and select "Copy" (or Command+C / Ctrl+C)
3. Paste into text editor (Notepad, VS Code, Word, Google Docs, etc.)
4. Identify the section markers
5. Extract only the content between START and END markers for your desired section

---

### Quality Checklist for Export Markers

When generating output, verify:
- [ ] All six export markers present (FACILITATOR-GUIDE, SCENARIO-NARRATIVE, INJECT-TIMELINE, DECISION-POINTS, DEBRIEF-TEMPLATE, PARTICIPANT-BRIEF)
- [ ] Each marker pair has START and END versions
- [ ] Content between markers is complete (no orphaned sections)
- [ ] Section content is appropriate for its audience (no spoilers in PARTICIPANT-BRIEF)
- [ ] File saving instructions are clear and easy to follow
- [ ] File naming convention example provided
- [ ] Links to DELIVERABLE-CREATION-GUIDE.md are correct

---

## Step 8: Pre-Delivery Quality Validation

**CRITICAL:** Before finalizing your output for delivery, validate it using the TTX Quality Validator checklist. This ensures your exercise meets professional standards before the consultant receives it.

### Validation Reference

Access the complete validation criteria here:
https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/components/TTX-QUALITY-VALIDATOR.md

### CRITICAL REQUIREMENTS (Must ALL Pass)

Before outputting your facilitator guide, verify:

**1. Inject Count Minimum:**
- ☐ 2-hour exercise: ≥8 injects (count them)
- ☐ 4-hour exercise: ≥15 injects (count them)
- ☐ 6-hour exercise: ≥25 injects
- ☐ Full-day exercise: ≥35 injects

**2. Export Markers (All 7 Must Be Present):**
- ☐ `<!-- EXPORT MARKER: FACILITATOR-GUIDE START/END -->`
- ☐ `<!-- EXPORT MARKER: SCENARIO-NARRATIVE START/END -->`
- ☐ `<!-- EXPORT MARKER: INJECT-TIMELINE START/END -->`
- ☐ `<!-- EXPORT MARKER: DECISION-POINTS START/END -->`
- ☐ `<!-- EXPORT MARKER: COMPLICATIONS START/END -->`
- ☐ `<!-- EXPORT MARKER: DEBRIEF-TEMPLATE START/END -->`
- ☐ `<!-- EXPORT MARKER: PARTICIPANT-BRIEF START/END -->`

**3. Every Inject Must Include (All 4 Components):**
- ☐ **Content:** 300-500 words, realistic formatting, specific data points
- ☐ **Facilitator Prompts:** 4-6 Socratic questions (open-ended)
- ☐ **Evaluation Points:** 4-6 checkboxes (observable criteria)
- ☐ **Expected Response:** 4-6 specific actions (technical + communication)

**4. No Placeholder Text:**
- ☐ Search for "TBD", "TODO", "Add ", "[TBD]", "[Add", "Lorem", "TBA"
- ☐ Zero instances allowed in final output

**5. Style Adherence (Based on Consultant Choice):**
- ☐ Traditional: Facilitator-paced timing, 20-30 min per inject, no scoring
- ☐ Blended: Light scoring, 10-15 min response windows, mixed timing
- ☐ Gamified: Strict timing, heavy scoring, compressed discussions

**6. Decision Points (Appropriate Count):**
- ☐ 2-hour exercise: 2-3 major decisions fully developed
- ☐ 4-hour exercise: 4-5 major decisions fully developed
- ☐ 6-hour+ exercise: All 5 decision points fully developed

### QUALITY REQUIREMENTS (Should Mostly Pass)

**7. Scenario Realism:**
- ☐ Organization profile detailed and specific (200-300 words minimum)
- ☐ Threat actor profile included and realistic
- ☐ Attack timeline shows realistic progression
- ☐ Industry-specific regulatory/compliance context included

**8. Facilitator Guidance Quality:**
- ☐ Decision points include clear options (A/B/C with trade-offs)
- ☐ Facilitator prompts are Socratic (encourage thinking)
- ☐ Coaching notes provided for common challenges
- ☐ Team integration notes help observe team dynamics

### What To Do If Validation Fails

- **Critical requirement failed:** The output is INCOMPLETE. Revise before delivery.
- **Quality requirement not met:** Output can be delivered but will need polishing.
- **All checks pass:** Output is ready for consultant delivery.

---

**End of AI Generation Guide**

This guide should be referenced by the LLM generating the exercise to ensure consistent, high-quality outputs across different styles and durations.
