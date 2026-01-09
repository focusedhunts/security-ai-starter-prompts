# TTX Scenario Strategy Review & Recommendations
## Comprehensive Analysis of All Seven Scenarios

**Review Date:** 2026-01-09
**Reviewer Role:** Strategic Architect
**Scope:** Current scenario library (7 total), adaptability, randomization, and backend improvements

---

## EXECUTIVE SUMMARY

### Current State Assessment

**Strengths:**
- ✅ All 7 scenarios follow consistent structural patterns (threat profile, narrative timeline, decision points, complications)
- ✅ Good difficulty/technical-weight distribution across portfolio
- ✅ AI-GENERATION-GUIDE.md provides solid scaffolding for style/duration adaptation
- ✅ Each scenario has 4-5 decision points that can be scaled by duration
- ✅ Each scenario has 6-7 complications available for triggering

**Critical Gaps:**
- ⚠️ **Insufficient variation** within scenarios for randomization (same injects/complications appear in same order)
- ⚠️ **Limited style-adaptation guidance** at scenario level (not explicitly showing how to adapt for Traditional vs. Gamified)
- ⚠️ **Static decision point sequences** (decisions always happen in same order/timeframe)
- ⚠️ **No scenario-level randomization seeds** (nothing tells AI to pick different injects on second run)
- ⚠️ **Missing variant frameworks** (no guidance on which complications are optional vs. mandatory)

### Overall Score

| Dimension | Score | Status |
|-----------|-------|--------|
| **Style Adaptability** | 6/10 | Works, but not explicitly guided per scenario |
| **Randomization Capability** | 3/10 | Very limited - injects/complications appear same every time |
| **Scenario Portfolio Balance** | 8/10 | Good difficulty/tech-weight spread |
| **Generation Consistency** | 9/10 | AI-GENERATION-GUIDE is solid |
| **Backend Extensibility** | 5/10 | Hard to add variations without modifying scenarios |

---

## SECTION 1: STYLE ADAPTABILITY ANALYSIS

### Current State: How Each Scenario Adapts to Styles

**Ransomware (Intermediate, Moderate-Tech)**
- **Traditional:** ✅ Works well - extensive decision framework fits discussion-focused approach
- **Blended:** ✅ Works well - ransom payment decision creates natural time pressure
- **Gamified:** ✅ Works well - clear scoring opportunities (contain? pay? investigate?)
- **Adaptation Level:** Implicit (AI expected to adapt)

**Business Email Compromise (Beginner-Intermediate, Low-Tech)**
- **Traditional:** ✅ Good for learning - wire fraud decision is straightforward
- **Blended:** ⚠️ Limited complexity - BEC is inherently low-complexity (may feel rushed even in blended)
- **Gamified:** ❌ Poor fit - decision is made or not made (binary), hard to score
- **Adaptation Level:** Implicit, but scenario may not work equally well across all styles

**Data Breach (Intermediate, Moderate-Tech)**
- **Traditional:** ✅ Good - extensive regulatory/communication complexity
- **Blended:** ✅ Good - investigation progress creates natural pacing
- **Gamified:** ⚠️ Okay - but less natural time pressure (investigation takes time, can't accelerate)
- **Adaptation Level:** Implicit, regulatory requirements create structure regardless

**Insider Threat (Advanced, High-Tech)**
- **Traditional:** ✅ Excellent - HR/legal/forensics complexity drives deep discussion
- **Blended:** ✅ Good - forensic findings provide pacing mechanism
- **Gamified:** ⚠️ Problematic - hard to create artificial time pressure (investigation is inherently slow)
- **Adaptation Level:** Implicit, but some awkwardness in compressed formats

**Cloud Misconfiguration (Intermediate, Moderate-Tech)**
- **Traditional:** ✅ Good - evidence preservation vs. remediation creates discussion
- **Blended:** ✅ Good - regulatory deadlines create natural time pressure
- **Gamified:** ⚠️ Okay - but relatively straightforward (not as many decision branches)
- **Adaptation Level:** Implicit, but limited complexity for gamified style

**Supply Chain Compromise (Advanced, High-Tech)**
- **Traditional:** ✅ Excellent - deep investigation and vendor coordination complexity
- **Blended:** ✅ Good - cascading discoveries drive pacing
- **Gamified:** ✅ Excellent - government lockdown, ransom demand, media pressure create natural time limits
- **Adaptation Level:** Implicit, scenario scales well across all styles

**Third-Party Vendor Compromise (Advanced, Moderate-Tech)**
- **Traditional:** ✅ Excellent - vendor coordination complexity, investigation phases
- **Blended:** ✅ Good - operational continuity decisions create pacing
- **Gamified:** ✅ Good - credential rotation, persistence discovery create urgency
- **Adaptation Level:** Implicit, but credential/access decisions work better for gamified

### CRITICAL FINDING #1: Weak Gamified Adaptation for Low-Tech Scenarios

**Problem:** BEC and Cloud Misconfiguration struggle in Gamified style because:
- BEC is inherently low-complexity (decision: fraud detected or not)
- Cloud Misconfiguration is relatively straightforward (decision: secure or investigate)
- Gamified style requires multiple decision branches and scoring opportunities
- Both scenarios lack the "decision tree explosion" needed for gamified play

**Impact:**
- Consultant asking for "BEC + Gamified + 2-hour" will get a weak exercise
- AI will struggle to create meaningful scoring/pressure without modifying scenario

**Recommendation:** Add explicit style-adaptation rules to each scenario file

---

## SECTION 2: RANDOMIZATION & VARIATION CAPABILITY ANALYSIS

### Problem: Identical Output on Repeated Execution

**Current Behavior:**
If a consultant runs STARTER-PROMPT twice with identical inputs, AI generates nearly identical exercises:
- Same injects in same order
- Same decision point framing
- Same complications in same sequence
- Same facilitator guidance

**Why This Matters:**
- Consulting firms use TTX Generator to create multiple exercises for different teams in same org
- Clients expect variations even with same scenario/duration/style
- "Training the trainer" sessions benefit from different scenarios from same template
- Repeated use suggests generator is formulaic/template-based

### Randomization Capability Assessment

**Scenario Component Variability:**

| Component | Variability | # Variations | Notes |
|-----------|------------|--------------|-------|
| **Threat Actor Profile** | None | 1 | Same profile every time |
| **Attack Timeline** | None | 1 | Same sequence every time |
| **Detection Points** | Low | 1-2 | Same initial indicators |
| **Decision Points** | None | 5 (fixed) | Always same 5, same order |
| **Decision Options** | None | 3 | Always A/B/C, same every time |
| **Complications** | Predefined | 6-7 | List exists, but no selection rules |
| **Facilitator Prompts** | None | Fixed | Same prompts every time |
| **Industry Customization** | Implicit | Unlimited | AI can customize, but no seeds |

**Key Finding:** Only industry customization varies; everything else is deterministic.

### Example: Ransomware on Second Run

**First Run (Finance, 4-hour, Blended):**
1. Decision Point: Immediate Response (secure or investigate)
2. Complication: Additional Exposures
3. Decision Point: Investigation Scope
4. Complication: Media Coverage
5. Decision Point: Ransom Payment

**Second Run (Same inputs):**
1. Decision Point: Immediate Response (exact same framing)
2. Complication: Additional Exposures (exact same complication)
3. Decision Point: Investigation Scope (exact same options)
... (identical sequence)

**Problem:** This is predictable. Consultant can "game" the system by knowing what's coming.

### Why Randomization Matters for Adoption

**Use Case 1: Multi-team exercise** - "Run this for 3 teams in the same company"
- Currently: Each team sees identical exercise (poor design, reduces learning)
- Desired: Each team sees same core scenario but different complications/injections

**Use Case 2: Training-the-trainer** - "I'm training 5 facilitators who will deliver this scenario"
- Currently: All facilitators use identical script
- Desired: Each facilitator has variations so they can practice handling different decision paths

**Use Case 3: Scenario library expansion** - "I want 10 variations of Ransomware scenario"
- Currently: Requires creating 10 separate scenario files
- Desired: Generator creates variations from 1 scenario file

**Use Case 4: Competitive/Gamified exercises** - "Multiple teams in same room, different scenarios"
- Currently: All teams get same exercise (no competitive variation)
- Desired: Teams get variations while testing same IR capability

### CRITICAL FINDING #2: No Randomization Seeds or Variation Rules

**Problem:** Scenarios don't have:
1. **Randomization seeds** - Instructions on what CAN vary between runs
2. **Variant rules** - Explicit guidance on which complications are optional vs. required
3. **Weighted selection** - Guidance on which complications likely occur (higher probability) vs. rare
4. **Conditional triggering** - "If team chooses X, enable these complications"
5. **Scope variations** - "For this run, reduce scope to [Y] instead of [Z]"

**Example missing guidance:**
- Ransomware: "Supply Chain Compromise can substitute for Additional Exposures if needed"
- Data Breach: "If team moves fast, skip Regulatory Investigation; if slow, add it"
- Cloud Misconfiguration: "Attacker Access Discovery is optional based on investigation depth"

---

## SECTION 3: SCENARIO PORTFOLIO BALANCE

### Difficulty Distribution

| Level | Count | Scenarios | Balance |
|-------|-------|-----------|---------|
| Beginner-Intermediate | 1 | BEC | ⚠️ Underrepresented |
| Intermediate | 3 | Ransomware, Data Breach, Cloud Misc | ✅ Good |
| Advanced | 3 | Insider Threat, Supply Chain, 3rd-Party Vendor | ✅ Good |
| **Total** | **7** | - | ✅ Reasonable |

**Assessment:** Beginner teams have only BEC option. Could use 1-2 more easier scenarios.

### Technical Weight Distribution

| Weight | Count | Scenarios | Balance |
|--------|-------|-----------|---------|
| Low-Tech | 1 | BEC | ⚠️ Underrepresented |
| Moderate-Tech | 5 | Ransomware, Data Breach, Cloud Misc, 3rd-Party, DDoS* | ✅ Good |
| High-Tech | 2 | Insider Threat, Supply Chain | ✅ Reasonable |
| **Total** | **8** | - | ⚠️ Top-heavy on tech-heavy |

*DDoS mentioned in README but scenario file not found in scenarios directory

**Assessment:** Good spread for technical audiences, but limited for non-technical/business-focused exercises.

### Industry Applicability

| Industry | Coverage | Notes |
|----------|----------|-------|
| Finance | 6/7 | Missing: Insider Threat variations, regulatory focus |
| Healthcare | 5/7 | Missing: Availability/critical system scenarios |
| Technology | 7/7 | All scenarios applicable |
| Retail/E-commerce | 4/7 | Missing: POS/customer-facing attack scenarios |
| Manufacturing | 3/7 | Missing: OT/operational technology scenarios |
| Government | 3/7 | Missing: Classified data handling, national security |
| Critical Infrastructure | 2/7 | Missing: Supply disruption, availability-focused |

**Assessment:** Technology and finance-heavy; retail/manufacturing/government underserved.

---

## SECTION 4: DETAILED SCENARIO-BY-SCENARIO CRITIQUE

### SCENARIO 1: Ransomware Attack

**Strengths:**
- ✅ Hits sweet spot for difficulty (Intermediate - not too easy, not too hard)
- ✅ Forces decision-making under uncertainty (pay or not? investigate or secure?)
- ✅ Naturally escalates complexity (detection → containment → investigation → remediation)
- ✅ Works across all three styles (strong gamified potential)
- ✅ Excellent decision tree (ransom, backup, investigation, external coordination)

**Weaknesses:**
- ❌ **Threat actor profile is generic** - "Eastern European" is vague, no operational model details
- ❌ **Complications are standard** - Media, backup issues, political infighting are predictable
- ⚠️ **Limited variation potential** - Attack timeline is always same (detection → response → recovery)
- ⚠️ **No "twist" variations** - What if attacker is internal? What if ransom is AI-generated deepfake demand? What if it's honeypot/test from pen testers?
- ⚠️ **Industry customization weak** - Says "healthcare gets HIPAA" but doesn't show variations in decision complexity

**Backend Improvement Opportunities:**
1. Add threat actor variant names (e.g., "LockBit variant," "Hive-affiliated group," "Nation-state testing")
2. Add "twist" complications (e.g., fake ransom demand, internal sabotage using ransomware as cover)
3. Add decision tree variations based on backup status (immediate recovery vs. negotiation)
4. Add industry-specific attack vectors (healthcare: patient care disruption, finance: regulatory reporting)

---

### SCENARIO 2: Business Email Compromise

**Strengths:**
- ✅ **Beginner-appropriate** - Clear cause/effect, straightforward decision
- ✅ **High financial impact** - Memorable consequences ($500K-$2M)
- ✅ **Fast pace** - Measures decision-making speed (good for time-pressured exercises)
- ✅ **Cross-industry** - Applies to almost any organization with finances

**Weaknesses:**
- ❌ **Scenario is too simple** - Binary decision (fraud detected or not)
- ❌ **Limited decision complexity** - Only real choice is: "Is this legitimate wire request?"
- ❌ **Poor gamified fit** - Can't create meaningful game mechanics for binary decision
- ❌ **Weak complication options** - Most complications are variations of "more fraud attempts"
- ⚠️ **No escalation path** - If team catches fraud, scenario essentially ends
- ⚠️ **Missing investigation depth** - Doesn't test forensic capability (who was compromised? for how long?)

**Critically Weak for:**
- Gamified style (no time pressure mechanism other than "wire happens")
- Advanced teams (too simple, decisions are obvious)
- 6-hour exercises (not enough complexity to sustain 6 hours)

**Backend Improvement Opportunities:**
1. **Add investigation depth** - "You caught the fraud, now investigate: How long was email compromised? What else did attacker do?"
2. **Add decision branching** - "Do you notify supplier? Customers? Law enforcement?"
3. **Add complication variety** - Multiple simultaneous fraud attempts, legitimate-looking requests that are actually fraud
4. **Add gamified variant** - "Multiple teams compete to catch fraud fastest" scoring
5. **Create "BEC+" advanced variant** - Layer ransomware on top (attacker uses BEC access to deploy malware)

---

### SCENARIO 3: Data Breach - Customer PII

**Strengths:**
- ✅ **Clear regulatory framework** - GDPR/CCPA/HIPAA decision points are concrete
- ✅ **Investigation complexity** - Scope assessment is genuinely difficult (real vs. potential access)
- ✅ **Multi-stakeholder** - Forces coordination (legal, communications, technical, executives)
- ✅ **Practical decision tree** - All decisions have real-world precedents
- ✅ **Scales well** - Works for 4-hour and full-day exercises

**Weaknesses:**
- ⚠️ **Investigation is slow-paced** - Doesn't work well for time-pressured (gamified) exercises
- ⚠️ **Limited technical variation** - Attack vector is always credential stuffing
- ⚠️ **Regulatory complexity overshadows IR response** - May feel like compliance exercise, not IR exercise
- ❌ **Missing "data valuation" decision** - Should explore: Which data is valuable? What's price? (ransomware angle)
- ❌ **No attacker attribution** - Scenario doesn't explore: Is this financial crime? Nation-state? Insider?

**Industry-Specific Gaps:**
- Healthcare: Missing "PHI in wrong hands" angle
- Finance: Missing "payment card data" regulatory stress
- Retail: Missing customer-facing communication crisis

**Backend Improvement Opportunities:**
1. Add "Attacker Demands Ransom" complication (data breach + extortion)
2. Add faster investigation path (detection of specific attackers so investigation can narrow scope)
3. Create healthcare variant with patient safety implications
4. Add competitor intelligence angle (attacker selling to competitor)
5. Create "Data Valuation" decision point (impact of different data types)

---

### SCENARIO 4: Insider Threat - Malicious Employee

**Strengths:**
- ✅ **Unique from external attacks** - Forces HR/legal/security coordination
- ✅ **High complexity** - Evidence handling, employment law, forensics all critical
- ✅ **Emotionally charged** - Organizational tension adds realism
- ✅ **Works across all styles** - Investigation phases provide natural pacing
- ✅ **Advanced-appropriate** - Requires sophisticated thinking

**Weaknesses:**
- ❌ **Investigation is time-consuming** - Doesn't work well for fast-paced (2-hour, gamified) exercises
- ❌ **Limited decision variety** - Sequence is usually: Detect → Investigate → Contain → Remediate
- ⚠️ **No "innocent person wrongly accused" variant** - All scenarios assume guilty insider
- ⚠️ **Missing "collateral damage" decisions** - Impact on innocent coworkers, reputation of team
- ⚠️ **Limited threat actor variety** - Always departing employee; missing: current employee, contractor, former employee

**Weaknesses in Style Adaptation:**
- **Traditional:** ✅ Works great (discussion-friendly)
- **Blended:** ⚠️ Hard to create time pressure naturally (investigation takes time)
- **Gamified:** ❌ Very difficult (can't compress forensics without realism collapse)

**Backend Improvement Opportunities:**
1. Add "false positive" variant (employee suspected but innocent)
2. Create contractor/vendor variant (not direct employee)
3. Add "continued access" decision point (insider still working while investigation ongoing)
4. Add "media leaks" complication (employees tweet about internal investigation)
5. Create "post-departure persistence" variant (focus on backdoors vs. data theft)

---

### SCENARIO 5: Cloud Misconfiguration

**Strengths:**
- ✅ **Modern threat** - Reflects real-world cloud security blind spots
- ✅ **Balanced complexity** - Not too simple, not overwhelming
- ✅ **Good decision framework** - Forensics vs. security, scope assessment, regulatory notification
- ✅ **Short-timeline** - Fits 2-4 hour exercises well
- ✅ **Industry-relevant** - Applies to any cloud-native organization

**Weaknesses:**
- ⚠️ **Relatively straightforward** - Doesn't have deep investigation complexity (cloud logs are clear)
- ⚠️ **Limited decision tree** - Once you realize "bucket is public," response is pretty standard
- ❌ **Missing scope expansion** - Only discovers one bucket; real incidents often cascade (DB exposed → API keys in DB → other systems compromised)
- ❌ **No cascading cloud misconfiguration** - What if researcher finds 3 more misconfigurations?
- ❌ **Limited "attacker discovery"** - What if attacker found it first? (assumes good-Samaritan reporter)

**Gamified Weakness:**
- Not enough decision branches for meaningful scoring
- Time pressure is regulatory deadline (passive) not active emergency

**Backend Improvement Opportunities:**
1. **Add cascading discoveries** - Initial bucket → credentials in bucket → other resources accessed
2. **Create "attacker first" variant** - Researcher reports after attacker already exfiltrated
3. **Add attack angle** - Misconfigured bucket enables ransomware lateral movement
4. **Create multi-cloud variant** - AWS/GCP/Azure all misconfigured differently
5. **Add "trust erosion" decision** - How do you audit all cloud infrastructure now?

---

### SCENARIO 6: Supply Chain Compromise

**Strengths:**
- ✅ **Excellent for advanced teams** - Complex crisis management
- ✅ **High stakes** - Affects thousands of customers, international scope
- ✅ **Works across all styles** - Excellent gamified potential
- ✅ **Strong decision tree** - Disclosure timing, investigation approach, vendor coordination
- ✅ **Rich complication options** - Ransom, government lockdown, cascade discoveries, media
- ✅ **Emotionally intense** - Organizational pressure adds realism

**Weaknesses:**
- ⚠️ **Very long** - Best suited for full-day (hard to compress to 4-hour without feeling rushed)
- ⚠️ **Requires extensive context** - Participants need to understand software distribution ecosystem
- ❌ **Missing "product vs. dependency" variants** - Is it YOUR software or library you use? Changes investigation completely
- ❌ **No "customer discovers first" variant** - Only attacker activates; what if customer finds evidence first?
- ⚠️ **Government involvement may overshadow IR** - FBI takes over, reduces participant agency

**Backend Improvement Opportunities:**
1. **Create "dependency variant"** - Compromised library (smaller scope, faster investigation)
2. **Create "customer discovery"** - Customer's SOC finds indicators before attacker activates
3. **Add "fix vs. rollback"** - Patch released or recommend rollback?
4. **Add "update adoption"** - How many customers auto-updated? (varies by config)
5. **Create "isolated variant"** - Single customer compromised (vs. thousands)

---

### SCENARIO 7: Third-Party Vendor Compromise

**Strengths:**
- ✅ **Practical for all industries** - Any organization using vendors/SaaS
- ✅ **Forces vendor relationship management** - Legal, operational, trust issues
- ✅ **Good decision complexity** - Credential management, investigation, vendor termination
- ✅ **Scales across durations** - Works for 4-hour and full-day
- ✅ **Relevant to current threats** - MOVEit, 3CX, Okta, etc. are real recent incidents

**Weaknesses:**
- ⚠️ **Investigation is inherently slow** - Doesn't compress well to 2-hour
- ❌ **Missing "different vendor types"** - SaaS vs. MSP vs. hardware vendor have different investigation/remediation paths
- ❌ **No "vendor is uncooperative"** - Assumes vendor cooperates; what if vendor gaslights about compromise?
- ❌ **Missing "customer impact" decision** - Do you disconnect vendor during investigation? Disrupt customers or stay vulnerable?
- ❌ **No "vendor gone bankrupt" variant** - What if vendor can't help with investigation?

**Backend Improvement Opportunities:**
1. **Create "SaaS vs. MSP vs. hardware"** variants (different investigation patterns)
2. **Add "uncooperative vendor"** complication
3. **Add "customer notification"** decision (transparency vs. minimizing panic)
4. **Add "vendor alternative"** decision (available immediately or weeks to migrate?)
5. **Add "supply chain depth"** variant - Vendor's vendor was also compromised

---

## SECTION 5: RANDOMIZATION IMPLEMENTATION STRATEGY

### The Problem: Static Scenarios Generate Static Exercises

**Current Flow:**
```
STARTER-PROMPT.md
    ↓
Consultant answers 6 questions
    ↓
AI reads scenario file (e.g., ransomware-scenario.md)
    ↓
AI generates exercise with:
    - SAME injects in same order
    - SAME decisions in same sequence
    - SAME complications appearing in predictable pattern
    ↓
Output: Identical to last time with same inputs
```

### Desired Flow:

```
STARTER-PROMPT.md
    ↓
Consultant answers 6 questions
    ↓
AI reads scenario file + VARIATION RULES
    ↓
AI seeds randomization based on:
    - Exercise ID (unique hash per generation)
    - Consultant preference (if "create variations")
    - Available variant options
    ↓
AI generates exercise with:
    - Different injects selected from variant pool
    - Different decision point emphasis
    - Different complication sequence
    ↓
Output: Unique exercise each time
```

### Implementation: Add Variation Framework to Scenarios

**Each scenario should include:**

#### 1. **Variant Threat Actors** (instead of 1 generic profile)

Example - Ransomware variants:
```
THREAT ACTOR VARIANTS:
- Variant A: LockBit-style (organized, professional, quick ransom negotiation)
- Variant B: Hive-style (demanding, aggressive timeline, likely exfiltration)
- Variant C: Nation-state (slower, persistent, data extraction priority)
- Variant D: Script-kiddies (mistakes in execution, easy to track)

SELECTION:
- Random pick for variation
- Or consultant specifies "realistic," "difficult," "easy"
```

#### 2. **Variant Attack Timelines** (compression/expansion)

Example - Cloud Misconfiguration variants:
```
TIMELINE VARIANTS:
- Fast discovery: Researcher finds it day 1, reports immediately
- Slow discovery: Misconfigured for months, found in audit
- Attacker first: Attacker found it day 5, exfiltrated day 6

SELECTION:
- Random or consultant preference
- Affects investigation complexity and scope
```

#### 3. **Decision Point Variants** (different emphasis)

Example - Insider Threat variants:
```
EMPHASIS VARIANTS:
- Forensics-heavy: Focus on timeline reconstruction, evidence
- HR-heavy: Focus on employee rights, legal risk
- Security-heavy: Focus on access review, remediation
- Business-heavy: Focus on IP recovery, damage assessment

SELECTION:
- All decision points present, but different emphasis
- Facilitator prompts highlight chosen focus
```

#### 4. **Complication Selection Rules** (not all at once)

Example - Ransomware complications:
```
COMPLICATION POOL (7 available):
- Additional Exposures (ALWAYS include)
- Media Coverage (CONDITIONAL: if disclosure happens)
- Backup Complications (CONDITIONAL: if team investigates backups)
- Attacker Persistence (CONDITIONAL: if investigation deep)
- Ransom Escalation (CONDITIONAL: if payment discussed)
- Internal Blame (CONDITIONAL: if IR takes long)
- Regulatory Investigation (CONDITIONAL: if notification delayed)

SELECTION LOGIC:
- Traditional style: Include 1-2 based on decisions
- Blended style: Include 2-3 based on decisions + random
- Gamified style: Include all possible complications
```

#### 5. **Scope Variation** (not always maximum scope)

Example - Data Breach variants:
```
SCOPE VARIANTS:
- Minimal: 1,000 records compromised, 1 customer affected
- Moderate: 500K records, 50 customers affected
- Massive: 5M records, all customers affected

SELECTION:
- Random for variation
- Or consultant specifies to match org size
- Affects notification complexity and financial impact
```

### Proposed Scenario Structure Enhancement

Add to EACH scenario file:

```markdown
## Randomization & Variation Options

### Threat Actor Variants
- [Define 3-4 variants of threat actor profile]
- [Selection rules: "Random," "Realistic," "Hardest"]

### Timeline Variants
- [Define 2-3 alternate attack progression paths]
- [Selection rules: affects investigation pace]

### Complication Selection Rules
- [Which complications are always included]
- [Which are conditional on decisions]
- [Probability weights for each]

### Decision Point Emphasis Variants
- [Different focuses depending on team expertise]
- [Guarantees all decision points, different flavor]

### Scope Variants
- [Minimal, moderate, maximum scope options]
- [Selection rules: org size, exercise ambition]

### Example Variations (Real Scenarios)
- [Show what changes between variations]
- [Show different exercise outputs from same scenario]
```

---

## SECTION 6: STYLE ADAPTATION GAPS

### Finding: Scenarios Don't Explicitly Show How to Adapt for Each Style

**Current State:** AI-GENERATION-GUIDE.md says:
- "Apply style-specific guidance from TTX-STYLE-GUIDE.md"
- "2-hour exercises get 8-12 injects, 4-hour gets 15-20, etc."

**Missing:** Scenario-level guidance on WHAT changes per style:

#### Example: Ransomware Traditional vs. Gamified

**Traditional (Discussion-Focused):**
```
Facilitator pacing: Participant discusses options, takes time
Decision Point 1: Secure or investigate?
  → Full 30-minute discussion of evidence preservation
  → All options presented upfront
  → Team decides together
Decision Point 2: Pay ransom or not?
  → 40-minute deep dive on payment options, legal risk, negotiation
  → Facilitator asks Socratic questions
  → No time pressure
```

**Gamified (Time-Pressured):**
```
Facilitator pacing: Strict timeline, real pressure
Decision Point 1: Secure or investigate?
  → 5 minutes to decide (high pressure)
  → Limited context initially (discovery during exercise)
  → Score based on speed + quality
Decision Point 2: Pay ransom or negotiate?
  → Time runs out, attacker escalates threat
  → Score impacts team reputation/recovery time
  → No discussion, just decision
```

**What's Missing in Scenario Files:**
- How to frame decision for Traditional (emphasis discussion) vs. Gamified (emphasis pressure)
- What facilitator prompts differ
- What information to withhold in Gamified (vs. reveal in Traditional)
- How to adjust timeline

### Proposed: Add "Style Adaptation Sections" to Scenarios

**Example Addition to Ransomware:**

```markdown
## Style-Specific Adaptation Guidance

### Traditional Style Adjustments
- Decision Point 1 (Secure/Investigate):
  * Present all three options A/B/C upfront
  * Allow 30-40 min discussion before decision
  * Prompt: "What would you lose by [choosing X]?"
  * Evaluation: Quality of reasoning, stakeholder input

- Decision Point 2 (Ransom Payment):
  * Introduce decision after investigation results available
  * Allow 40 min debate
  * Prompt facilitator to surface: "Who should decide this?"
  * Evaluation: Decision-making process, not outcome

### Gamified Style Adjustments
- Decision Point 1 (Secure/Investigate):
  * Withhold Option C initially (team discovers during exercise)
  * Decision forced at T+20 minutes (realistic containment window)
  * Scoring: +20 if contained quickly, -10 if delayed
  * Complication trigger: "You chose to investigate; attacker escalates"

- Decision Point 2 (Ransom Payment):
  * Time pressure: Attacker raises demand at T+60 min
  * Withhold negotiation option if team stalls
  * Scoring: Payment options have different recovery times/costs
  * Complication trigger: "Attacker threatens to publish data"

### Blended Style Adjustments
- Balance: Some options withhold, some given upfront
- Timeline: Middle-ground urgency (20 min for decision point)
- Discussion: 10 min discuss + 5 min decide
- Complications: Based on decisions, with warning
```

---

## SECTION 7: STRATEGIC RECOMMENDATIONS

### Priority 1 (Critical): Add Variation Framework to All Scenarios

**Why:** Enables meaningful randomization so repeated exercises aren't identical

**Implementation:**
1. Add "Threat Actor Variants" section to each scenario (3-4 variants each)
2. Add "Complication Selection Rules" section (always/conditional/rare)
3. Add "Scope Variants" section (minimal/moderate/maximum)
4. Add "Timeline Variants" section (fast/normal/slow attack progression)
5. Test by running same scenario twice with "create variations" flag

**Effort:** Medium (add 200-300 lines per scenario, 1400-2100 lines total)
**Impact:** High (enables true randomization, increases reusability)
**Timeline:** 2-3 weeks for all scenarios

---

### Priority 2 (High): Add Style-Specific Adaptation Sections

**Why:** Eliminates ambiguity on how scenarios change for Traditional/Blended/Gamified

**Implementation:**
1. Add "Style-Specific Adaptation Guidance" section to each scenario
2. For each style, specify:
   - Which information to reveal/withhold
   - How to frame decisions differently
   - What complications to trigger
   - How to adjust timing
3. Provide example facilitator prompts for each style

**Effort:** Medium (add 300-400 lines per scenario)
**Impact:** High (improves consistency, reduces AI guesswork)
**Timeline:** 2-3 weeks for all scenarios

---

### Priority 3 (High): Strengthen Low-Tech Scenario Portfolio

**Why:** BEC is only low-tech scenario; limited options for non-technical audiences

**Implementation Options:**
1. **Option A:** Create new scenario (Phishing/Social Engineering focused)
2. **Option B:** Create "BEC+" variant (add complexity layers)
3. **Option C:** Create business-focused scenarios (crisis communication, stakeholder management)

**Recommendation:** Option B (leverage existing BEC) + add 2-3 new low-tech scenarios

**Effort:** High (new scenarios require significant work)
**Impact:** High (expands market to non-technical organizations)
**Timeline:** 4-6 weeks for new scenarios

---

### Priority 4 (Medium): Add Investigation Depth to Shorter Scenarios

**Why:** 2-hour exercises from simple scenarios feel rushed/superficial

**Implementation:**
1. Enhance BEC with investigation phase (how long was email compromised?)
2. Enhance Cloud Misconfiguration with cascading discoveries
3. Create "compressed" versions of advanced scenarios (Insider Threat → 4-hour variant)

**Effort:** Medium (modify existing scenarios)
**Impact:** Medium (improves usability for time-constrained teams)
**Timeline:** 2-3 weeks

---

### Priority 5 (Medium): Create Variant Examples in Scenario Files

**Why:** AI needs concrete examples of how variations differ

**Implementation:**
1. For each scenario, add "Example Variations" section
2. Show 2-3 complete exercise examples from same scenario (different variants)
3. Show how output differs based on variation selection

**Effort:** Medium (write examples)
**Impact:** Medium (helps AI understand variation intent)
**Timeline:** 2-3 weeks

---

### Priority 6 (Low): Improve Gamified Scenario Fit

**Why:** Some scenarios don't adapt well to Gamified style

**Implementation:**
1. Audit each scenario for Gamified fitness:
   - Does it have meaningful time pressure?
   - Are there decision trees with scoring branches?
   - Can complications escalate realistically?
2. Strengthen weak fits:
   - BEC: Add secondary fraud attempts, time-based scoring
   - Cloud Misc: Add cascading discoveries (more urgent)
   - Insider Threat: Add "still-employed" variant (more real-time tension)

**Effort:** Medium
**Impact:** Low (Gamified is less common than Traditional/Blended)
**Timeline:** 3-4 weeks

---

## SECTION 8: IMPLEMENTATION ROADMAP

### Phase 1 (Weeks 1-3): Foundation
- [ ] Add Variation Framework to AI-GENERATION-GUIDE.md
  - Define how AI selects variations
  - Provide template for variation sections
  - Add randomization seed/selection logic

- [ ] Add Threat Actor Variants to all 7 scenarios
  - 3-4 variants per scenario
  - Clear selection logic
  - Example variant outputs

- [ ] Add Complication Selection Rules to all 7 scenarios
  - Mandatory/conditional/optional classification
  - Probability weights
  - Trigger conditions

### Phase 2 (Weeks 4-6): Enhancement
- [ ] Add Style-Specific Adaptation Sections to all scenarios
  - Traditional/Blended/Gamified guidance
  - Information withholding rules
  - Facilitator prompt variations
  - Complication triggering logic

- [ ] Add Timeline Variants to all scenarios
  - Fast/normal/slow progression
  - Impact on investigation pacing

- [ ] Test randomization with sample exercises
  - Generate same scenario 5 times
  - Verify variation between runs
  - Document differences

### Phase 3 (Weeks 7-10): Expansion
- [ ] Create 2-3 new low-tech scenarios
  - Phishing/Social Engineering
  - Crisis Communication
  - Vendor Management

- [ ] Create compressed variants
  - BEC investigation depth (2-hour)
  - Insider Threat lite (4-hour)
  - Supply Chain compressed (4-hour)

- [ ] Add Example Variations to each scenario
  - Show 2-3 different exercise outputs
  - Document variation impacts

### Phase 4 (Weeks 11-12): Polish
- [ ] Improve Gamified fit for weak scenarios
- [ ] Test full generation pipeline with variations
- [ ] Update README with variation guidance
- [ ] Create variation selection guide for consultants

---

## SECTION 9: SPECIFIC RECOMMENDATIONS BY SCENARIO

### Ransomware: Strong Overall, Add Variants
**Add:**
- Threat actor variants (LockBit, Hive, Nation-state, Script-kiddies)
- Timeline variants (48-hour to 2-week attack progression)
- "False positive" variant (alert triggers, but it's test/legitimate)

**Improve:**
- Backup failure complications (more specific - partial/corrupted backups)
- Investigation decision (forensics firm involvement)

---

### BEC: Weak Gamified, Add Investigation
**Add:**
- Investigation depth (secondary fraud attempts while primary being investigated)
- Forensics decision (how long was email compromised?)
- Multiple fraud targets (one attempt or coordinated campaign?)
- Variant: "Insider-assisted BEC" (attacker has inside help)

**Improve:**
- Gamified adaptation (secondary fraud attempts create time pressure)
- Industry variants (different fraud targets by industry)

---

### Data Breach: Good, Add Attacker Angle
**Add:**
- Attacker identity variants (criminal, nation-state, insider)
- Ransom demand angle (breach + extortion)
- Attacker attribution decision (pursue criminal charges?)

**Improve:**
- Investigation pace (faster attacker identification = faster scope assessment)
- Industry variants (healthcare/finance specific)

---

### Insider Threat: Good, Add False-Positive Variant
**Add:**
- False-positive variant (employee accused but innocent)
- Current-employee variant (threat ongoing, not departed)
- Contractor variant (vendor employee, not direct hire)

**Improve:**
- Gamified adaptation (ongoing threat creates time pressure)
- Decision point emphasis options (forensics-heavy vs. HR-heavy)

---

### Cloud Misconfiguration: Good, Add Cascading
**Add:**
- Cascading discoveries (1 bucket → credentials → other buckets → other clouds)
- Attacker-first variant (attacker accessed before researcher report)
- Multi-cloud variant (AWS + Azure both misconfigured)

**Improve:**
- Gamified adaptation (cascading complications = time pressure)
- Investigation decision (full audit vs. targeted fix)

---

### Supply Chain: Strong, Add Dependency Variant
**Add:**
- Dependency variant (library vs. product - smaller scope)
- Customer-discovery variant (customer finds it first)
- Activation-timing variant (when does attacker activate malware?)

**Improve:**
- Full-day compression (4-hour variant available)
- Investigation phases (faster/slower investigation paths)

---

### Third-Party Vendor: Strong, Add Vendor Type Variants
**Add:**
- SaaS vendor variant (cloud-based service)
- MSP variant (managed service provider)
- Hardware vendor variant (firmware compromise)
- Uncooperative vendor variant (vendor denies/minimizes)

**Improve:**
- Migration decision (disconnecting vendor immediately vs. planned transition)
- Investigation depth (vendor cooperation vs. independent investigation)

---

## CONCLUSION

### Summary Scorecard

| Dimension | Current | Target | Gap |
|-----------|---------|--------|-----|
| Style Adaptability | 6/10 | 9/10 | Add explicit guidance |
| Randomization | 3/10 | 8/10 | Add variation frameworks |
| Portfolio Balance | 8/10 | 9/10 | Add low-tech scenarios |
| Scenario Quality | 7/10 | 9/10 | Add variants/depth |
| Generation Consistency | 9/10 | 9/10 | Maintain current |
| **Overall** | **6.6/10** | **8.8/10** | **+2.2 points** |

### Key Takeaway

Scenarios are **strong structurally** but **weak on variation and explicit style guidance**. With recommended improvements, system would support:
- True randomization (same scenario, different exercises each time)
- Clearer style adaptation (Traditional/Blended/Gamified explicit guidance)
- Expanded market (more low-tech scenarios)
- Better reusability (variations for repeated use)

**No major restructuring needed** - improvements are additive and backward-compatible.

---

**End of Strategic Review**
