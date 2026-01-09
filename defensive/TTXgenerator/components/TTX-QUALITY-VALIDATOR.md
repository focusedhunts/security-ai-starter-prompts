# TTX Quality Validator & Orchestrator

**Purpose:** This document serves as the **central quality gating mechanism** for all TTX exercise generation. Every TTX facilitator guide output MUST pass these validation criteria before being delivered to a consultant or client.

**Who Uses This:**
- AI systems generating TTX exercises (as a validation checklist)
- Consultants reviewing generated output (to verify completeness)
- Project maintainers (to ensure consistency across all variants)

---

## Executive Validation Flow

Every TTX exercise generation follows this flow:

```
1. Consultant provides 5 questions → 2. AI generates exercise → 3. QUALITY VALIDATOR CHECKS → 4. Pass/Fail Decision
                                           (uses AI-GENERATION-GUIDE.md)        (THIS DOCUMENT)          ↓
                                                                                                  PASS: Deliver to consultant
                                                                                                  FAIL: Revise and re-validate
```

This document is the **quality gate** between generation and delivery.

---

## Quality Validation Layers

### Layer 1: CRITICAL REQUIREMENTS (Must All Pass)

If ANY critical requirement fails, the exercise is **INCOMPLETE** and cannot be delivered.

#### 1.1 Exercise Completeness
- [ ] **Inject Count:** Minimum count met for duration
  - 2-hour: ≥ 8 injects (count them explicitly)
  - 4-hour: ≥ 15 injects (count them explicitly)
  - 6-hour: ≥ 25 injects
  - Full-day: ≥ 35 injects
- [ ] **Decision Points:** Appropriate count for duration
  - 2-hour: 2-3 decisions
  - 4-hour: 4-5 decisions
  - 6-hour+: All 5 decisions fully developed
- [ ] **Complications:** Present and appropriate count
  - At minimum: 1 complication for 2-hour, 2-3 for 4-hour, 4+ for 6-hour

#### 1.2 Export Markers (ALL 7 Required)
- [ ] `<!-- EXPORT MARKER: FACILITATOR-GUIDE START -->` ... `END -->` (wraps entire output)
- [ ] `<!-- EXPORT MARKER: SCENARIO-NARRATIVE START -->` ... `END -->` (participant-safe section)
- [ ] `<!-- EXPORT MARKER: INJECT-TIMELINE START -->` ... `END -->` (full inject sequence)
- [ ] `<!-- EXPORT MARKER: DECISION-POINTS START -->` ... `END -->` (decision frameworks)
- [ ] `<!-- EXPORT MARKER: COMPLICATIONS START -->` ... `END -->` (complication sequence)
- [ ] `<!-- EXPORT MARKER: DEBRIEF-TEMPLATE START -->` ... `END -->` (post-exercise structure)
- [ ] `<!-- EXPORT MARKER: PARTICIPANT-BRIEF START -->` ... `END -->` (non-spoiler materials)

**Validation:** Search output for "EXPORT MARKER:" and count START/END pairs. Must be exactly 7 pairs. If any missing, output FAILS.

#### 1.3 Inject Component Completeness
Every single inject MUST have ALL 4 of these:
- [ ] **Content** (300-500 words minimum)
  - Realistic formatting (email headers, call dialogue, etc.)
  - Specific data points (names, numbers, system names)
  - Industry-appropriate language
- [ ] **Facilitator Prompts** (4-6 Socratic questions, NOT statements)
  - Must be open-ended questions
  - Focus on thinking, not "right answers"
- [ ] **Evaluation Points** (4-6 checkboxes)
  - Format: ☐ Observable criterion
  - Process-focused, not outcome-focused
- [ ] **Expected Response** (4-6 specific actions)
  - What should the team do?
  - Both technical and communication responses

**Validation:** For each inject, verify all 4 components present. If ANY inject is missing ANY component, output FAILS.

#### 1.4 No Placeholder or TBD Text
- [ ] No "TBD" or "TODO" or "[Add ...]" in final output
- [ ] No incomplete sentences or missing sections
- [ ] No "Lorem ipsum" or generic filler text
- [ ] All facilitator prompts are complete questions/statements

**Validation:** Search for: "TBD", "TODO", "Add ", "[TBD]", "[Add", "Lorem", "TBA". Any matches = FAIL.

#### 1.5 Adherence to Specified Style
- [ ] **Traditional style:** No scoring, facilitator-paced timing, Socratic focus
- [ ] **Blended style:** Light scoring, mixed timing, balanced discussion
- [ ] **Gamified style:** Scoring present, strict timing, compressed discussions

**Validation:** Review exercise type statements and verify style is applied consistently throughout.

---

### Layer 2: QUALITY REQUIREMENTS (Should All Pass)

These represent professional quality standards. Output can pass with 1-2 minor issues, but should not have multiple failures.

#### 2.1 Scenario Realism
- [ ] Organization profile is detailed and specific (200-300 words minimum)
- [ ] Threat actor profile included and realistic
- [ ] Attack timeline shows realistic progression (days before discovery)
- [ ] Initial discovery is specific and believable
- [ ] Industry-specific regulatory/compliance context included

#### 2.2 Facilitator Guidance Quality
- [ ] Decision points include clear options (A/B/C with trade-offs)
- [ ] Facilitator prompts are Socratic (encourage thinking, not provide answers)
- [ ] Coaching notes provided for common facilitator challenges (silence, rushing, domination)
- [ ] Timing allocations are realistic for stated style
- [ ] Team integration notes help facilitators observe team dynamics

#### 2.3 Preparation & Logistics Support
- [ ] Facilitator preparation checklist included
- [ ] Customization guidance provided
- [ ] Pre-exercise communication templates suggested or included
- [ ] Materials preparation checklist included

#### 2.4 Debrief Structure
- [ ] Debrief section is structured (not just "discuss")
- [ ] Clear timing allocation (typically 30-60 minutes)
- [ ] Discussion questions provided (not just "what did we learn?")
- [ ] Evaluation framework for assessing team capabilities

#### 2.5 Participant Materials
- [ ] Participant briefing is non-spoiler (no injects, no complications previewed)
- [ ] Welcome letter or pre-exercise communication template
- [ ] Ground rules or exercise context established
- [ ] Role assignments or participant context provided

#### 2.6 Professional Formatting
- [ ] Markdown is well-formatted (clear headers, tables, bullet points)
- [ ] No orphaned sections or floating text
- [ ] Tables are properly formatted and readable
- [ ] Consistent terminology throughout
- [ ] Professional tone maintained

#### 2.7 Complexity Calibration
- [ ] Complication difficulty matches stated IR maturity level
- [ ] Information gaps in injects match maturity (more gaps for advanced teams)
- [ ] Decision point ambiguity calibrated to maturity
- [ ] Beginner exercises have clarity; advanced have uncertainty

---

### Layer 3: DELIVERABLE GUIDANCE

Output must include clear instructions for converting to professional deliverables.

#### 3.1 Next Steps Section
- [ ] "Next Steps: Creating Professional Deliverables" section present
- [ ] Overview explaining markdown → PowerPoint conversion
- [ ] Three delivery options explained:
  - Option 1: Use Markdown Directly
  - Option 2: Export Sections for Team Sharing
  - Option 3: Create Professional PowerPoint
- [ ] Reference to DELIVERABLE-CREATION-GUIDE.md included
- [ ] Export marker explanation provided

#### 3.2 File Saving Instructions
- [ ] Clear instructions for extracting sections using export markers
- [ ] File naming convention examples
- [ ] Guidance on which sections to share with which audiences
- [ ] Links to PowerPoint conversion guidance if applicable

---

## Validation Checklist Template

Use this checklist when validating a TTX exercise output:

```
CRITICAL REQUIREMENTS (All must PASS):
─────────────────────────────────────
☐ Inject count minimum met for duration
☐ All 7 export markers present (search for "EXPORT MARKER:")
☐ Every inject has: Content (300-500 words), Facilitator Prompts (4-6), Evaluation Points (4-6), Expected Response (4-6)
☐ No TBD/TODO/placeholder text in output
☐ Style (Traditional/Blended/Gamified) applied consistently
☐ All decision points present and complete

QUALITY REQUIREMENTS (Should mostly PASS):
──────────────────────────────────────────
☐ Scenario is detailed and realistic
☐ Facilitator guidance is Socratic and actionable
☐ Preparation checklist included
☐ Debrief structure is detailed
☐ Participant materials are non-spoiler
☐ Professional formatting and tone
☐ Complexity matches stated maturity level

DELIVERABLE GUIDANCE (Should be present):
─────────────────────────────────────────
☐ "Next Steps" section included
☐ Delivery options explained
☐ File saving/export instructions provided
☐ Reference to DELIVERABLE-CREATION-GUIDE.md

OVERALL ASSESSMENT:
──────────────────
CRITICAL: ___ / 6 PASSED → MUST BE 6/6 or FAILS entire validation
QUALITY: ___ / 7 PASSED → Should be 6+/7 (1 minor issue acceptable)
DELIVERABLE: ___ / 4 PASSED → Should be 4/4

DECISION:
☐ PASS: All critical requirements met, 6+/7 quality requirements met
☐ FAIL: Any critical requirement failed OR <6 quality requirements met
☐ CONDITIONAL PASS: All critical met, 5/7 quality (minor revisions needed)

If FAIL or CONDITIONAL: Identify specific failures below
─────────────────────────────────────────────────────────
[Document which criteria failed and what needs revision]
```

---

## How to Use This Validator

### For AI Systems Generating TTX:

1. **After generating exercise:** Before outputting, run through CRITICAL REQUIREMENTS layer
2. **Count injections explicitly:** Say "I count X injects for this [2/4/6-hour] exercise"
3. **Verify export markers:** Search output for all 7 marker pairs
4. **Check each inject:** Verify all 4 required components present
5. **Search for placeholders:** Ensure no TBD/TODO remains
6. **Validate style:** Confirm style-specific guidance applied
7. **If any critical fails:** Revise and revalidate before outputting

**Example AI Validation Process:**
```
I'm validating my output before delivery:

CRITICAL REQUIREMENTS:
- Inject count: I count 17 injects (required 15+ for 4-hour) ✓
- Export markers: Searching... found all 7 pairs ✓
- Inject components: Spot-checking 5 random injects... all have Content, Facilitator Prompts, Evaluation Points, Expected Response ✓
- No TBD text: Searching output... none found ✓
- Style (Blended): Reviewing... light scoring present, 10-15 min response windows, balanced discussion ✓
- Decision points: 4 major decisions present, all with options and prompts ✓

QUALITY REQUIREMENTS:
- Scenario: 300+ word org profile, threat actor profile, 7-day attack timeline ✓
- Facilitator guidance: Socratic prompts throughout, team integration notes present ✓
- [etc...]

RESULT: PASS - Ready to deliver
```

### For Consultants Reviewing Output:

1. Check that all critical requirements are met (use the checklist)
2. If critical is 6/6, exercise is valid
3. Review quality requirements for professional polish
4. Verify Next Steps section points to deliverable conversion guidance
5. If all checks pass, exercise is ready for your client

### For Project Maintainers:

1. When updating AI-GENERATION-GUIDE.md, ensure changes don't violate these critical requirements
2. When adding new scenarios or variants, run through this validator
3. Use this validator to audit sample exercises monthly
4. Update this document when project standards change

---

## Integration with AI-GENERATION-GUIDE.md

This validator enforces what AI-GENERATION-GUIDE.md specifies:

| Requirement | Defined In | Why It Matters |
|-------------|------------|----------------|
| Inject structure (Content, Prompts, Evaluation, Response) | AI-GENERATION-GUIDE Step 5A | Ensures facilitators have all needed info |
| Export markers (7 required pairs) | AI-GENERATION-GUIDE Step 5B | Enables consultant team sharing workflow |
| Decision point template (8 components) | AI-GENERATION-GUIDE Step 5C | Ensures decision frameworks are complete |
| Facilitator prep checklist | AI-GENERATION-GUIDE Step 5D | Ensures exercises are actually usable |
| Scenario narrative requirements | AI-GENERATION-GUIDE Step 5E | Ensures scenario is industry-specific and realistic |
| Inject quantity by duration | AI-GENERATION-GUIDE Step 2 | Ensures exercises have sufficient content |
| Style-specific guidance | AI-GENERATION-GUIDE Step 5 | Ensures output matches consultant's requested style |

---

## Quality Standards by Duration

### 2-Hour Exercise Standards
- **Injects:** 8-12 minimum ✓
- **Decision Points:** 2-3 ✓
- **Complications:** 1-2 ✓
- **Focus:** Detection & initial response only
- **Estimated Pages:** 10-15

### 4-Hour Exercise Standards
- **Injects:** 15-20 minimum ✓
- **Decision Points:** 4-5 ✓
- **Complications:** 2-3 ✓
- **Focus:** Full IR lifecycle (detection → recovery start)
- **Estimated Pages:** 25-35

### 6-Hour Exercise Standards
- **Injects:** 25-35 minimum ✓
- **Decision Points:** All 5 ✓
- **Complications:** 4-5 ✓
- **Focus:** Deep investigation, parallel incident threads
- **Estimated Pages:** 35-50

### Full-Day Exercise Standards
- **Injects:** 35+ ✓
- **Decision Points:** All 5 with extended exploration ✓
- **Complications:** 6+ with cascading effects ✓
- **Focus:** Leadership coordination, regulatory responses, recovery planning
- **Estimated Pages:** 50+

---

## Common Validation Failures & Fixes

### FAIL: "Inject count is only 8, but this is a 4-hour exercise"
- **Required:** 15+ injects minimum
- **Fix:** Add 7+ more injects using inject-library.md variants
- **Why:** Exercises need sufficient scenario progression to use full time

### FAIL: "Missing DECISION-POINTS export marker"
- **Required:** All 7 markers present
- **Fix:** Add `<!-- EXPORT MARKER: DECISION-POINTS START -->` and `END -->` around decision section
- **Why:** Consultants cannot extract sections without markers

### FAIL: "Inject 7 is missing Facilitator Prompts"
- **Required:** 4-6 Socratic questions per inject
- **Fix:** Add 4-6 open-ended questions to this inject
- **Why:** Facilitators need guidance on how to engage participants in discussion

### FAIL: "Decision Point 2 has only 2 options (Option A and B)"
- **Required:** 3+ options with full pros/cons tables
- **Fix:** Add Option C (usually a hybrid approach) with pros, cons, resources, timeline, risk
- **Why:** Participants need real choices to evaluate trade-offs

### FAIL: "Output contains 'TBD' in Inject 5 Facilitator Notes"
- **Required:** Zero placeholder text
- **Fix:** Replace TBD with actual facilitator guidance (coaching prompts, coaching notes)
- **Why:** Facilitators cannot use exercises with incomplete guidance

### FAIL: "Scenario is generic (doesn't mention client's industry or systems)"
- **Required:** Industry-specific context, actual system names, regulatory details
- **Fix:** Reference actual industry regulations (GLBA for finance, HIPAA for healthcare, PCI for retail)
- **Why:** Exercises must be specific to client context to be believable

---

## Quality Audit Template (Monthly)

Use this to audit sample exercises and ensure quality consistency:

```
MONTHLY TTX QUALITY AUDIT
Date: [Month/Year]
Exercises Audited: [Sample of 2-3 recent exercises]

Exercise 1: [Name]
┌─ Critical Requirements: _/6 passed
├─ Quality Requirements: _/7 passed
├─ Deliverable Guidance: _/4 passed
└─ Notes: [Any issues found?]

Exercise 2: [Name]
┌─ Critical Requirements: _/6 passed
├─ Quality Requirements: _/7 passed
├─ Deliverable Guidance: _/4 passed
└─ Notes: [Any issues found?]

OVERALL TREND: [Is quality consistent? Any recurring issues?]
ACTIONS: [What needs to be updated in AI-GENERATION-GUIDE.md or this validator?]
```

---

## Integration Points

This validator is used in:

1. **AI-GENERATION-GUIDE.md** → References this validator in quality checklist section
2. **STARTER-PROMPT.md** → Could mention quality validation to consultants
3. **ERROR-HANDLING-GUIDE.md** → Could note quality validation as part of delivery
4. **Consultant Workflow** → Consultants can use this to verify exercises before client delivery

---

## When to Update This Validator

Update this document when:

1. Project standards change
2. New requirements emerge from client feedback
3. New scenario types are added
4. Duration-specific standards change
5. Export marker structure evolves
6. Style guide changes

**Do NOT update:**
- STARTER-PROMPT.md (consultant-facing interface)
- AI-GENERATION-GUIDE.md (unless tied to standards change)

**DO update** in coordination with those files when standards change.

---

## Key Success Metrics

A successful TTX validation system means:

- ✅ **100% of delivered exercises pass critical requirements**
- ✅ **95%+ of delivered exercises pass quality requirements**
- ✅ **All consultants receive exercises with complete export markers**
- ✅ **No exercises delivered with TBD or placeholder text**
- ✅ **Consultant satisfaction with exercise completeness and usability**
- ✅ **Inject count meets duration standards consistently**
- ✅ **Facilitators report exercises are immediately usable**

---

**End of TTX Quality Validator**

This document serves as the central quality gating mechanism for all TTX exercise generation.
