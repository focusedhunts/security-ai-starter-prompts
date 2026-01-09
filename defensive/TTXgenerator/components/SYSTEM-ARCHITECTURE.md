# TTX Generator System Architecture & File Usage

**Purpose:** This document explains how all TTX system files work together when a consultant runs STARTER-PROMPT.md in an LLM.

---

## System Overview

The TTX Generator is a **prompt-based system** that coordinates multiple reference guides and generation rules to produce professional TTX facilitator guides from 5 consultant questions.

**Key Insight:** The system operates ENTIRELY through markdown files pulled into the LLM's context. No code, no database, no backend—just structured guidance files.

---

## Architecture Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    CONSULTANT WORKFLOW                                     │
└─────────────────────────────────────────────────────────────────────────────┘

STEP 1: Consultant copies STARTER-PROMPT.md and pastes into LLM
                              ↓
                    ┌─────────────────────┐
                    │  STARTER-PROMPT.md  │
                    │  (Entry Point)      │
                    └──────────┬──────────┘
                              ↓
                    Presents 5 Questions:
                    1. Client Context
                    2. Exercise Objective
                    3. Duration & Format
                    4. Participant Profile
                    5. Exercise Style
                              ↓
STEP 2: LLM receives 5 answers from Consultant
                              ↓
         LLM CHECKS GITHUB ACCESS
              ↙                    ↘
           YES                      NO
            ↓                        ↓
    ┌───────────────────┐   ┌──────────────────────┐
    │ PATH A: IDEAL     │   │ PATH B: FALLBACK     │
    │ (GitHub Access)   │   │ (No GitHub Access)   │
    └────────┬──────────┘   └─────────┬────────────┘
             ↓                         ↓
    Fetches from GitHub:         User consults:
    • scenarios/                 ERROR-HANDLING-GUIDE
      ransomware-scenario.md    (DECISION TREE)
    • components/                      ↓
      inject-library.md           Option 1: RETRY
    • components/                Option 2: MANUAL PASTE
      decision-points.md         Option 3: EMERGENCY MODE
    • components/                      ↓
      complications.md        (Same generation continues)
    • components/
      TTX-STYLE-GUIDE.md
    • components/
      AI-GENERATION-GUIDE.md
             ↓
    LLM READS GENERATION RULES
             ↓
    ┌──────────────────────────────────────────────────────┐
    │      AI-GENERATION-GUIDE.md (GENERATION RULES)       │
    │                                                      │
    │  Step 1: Parse 5 Questions                          │
    │  Step 2: Select Inject Library Items                │
    │  Step 3: Select Decision Points                     │
    │  Step 4: Select & Apply Complications              │
    │  Step 5: Apply Style-Specific Formatting            │
    │  Step 5A: INJECT GENERATION STANDARDS (MANDATORY)   │
    │  Step 5B: EXPORT MARKERS (MANDATORY - 7 REQUIRED)   │
    │  Step 5C: Decision Point Template (MANDATORY)       │
    │  Step 5D: Facilitator Prep Requirements             │
    │  Step 5E: Scenario Narrative Requirements           │
    │  Step 6: Generate Output Facilitator Package        │
    │  Step 7: Format Output for External Sharing         │
    └──────────────┬───────────────────────────────────────┘
                   ↓
    LLM GENERATES FACILITATOR GUIDE
    (Using all component libraries as templates/examples)
                   ↓
    LLM VALIDATES OUTPUT
                   ↓
    ┌────────────────────────────────────────────────────────────┐
    │    TTX-QUALITY-VALIDATOR.md (QUALITY GATING)              │
    │                                                           │
    │  Layer 1: CRITICAL REQUIREMENTS (Must Pass 6/6)          │
    │  - Inject count minimum met                              │
    │  - All 7 export markers present                          │
    │  - Every inject has required components                  │
    │  - No TBD/placeholder text                               │
    │  - Style applied consistently                            │
    │  - All decision points present                           │
    │                                                          │
    │  Layer 2: QUALITY REQUIREMENTS (Should Pass 6+/7)        │
    │  - Scenario realistic and detailed                       │
    │  - Facilitator guidance Socratic                         │
    │  - Preparation checklist included                        │
    │  - Debrief structured                                    │
    │  - Participant materials non-spoiler                     │
    │  - Professional formatting                              │
    │  - Complexity calibrated                                │
    │                                                          │
    │  Layer 3: DELIVERABLE GUIDANCE (Should be Present)       │
    │  - Next Steps section included                           │
    │  - File saving instructions                              │
    └──────────┬─────────────────────────────────────────────┘
               ↓
       PASS? → YES ↓        NO → REVISE & REVALIDATE
               ↓
    ┌────────────────────────────────────────┐
    │  OUTPUT INCLUDES:                      │
    │                                        │
    │  1. Exercise Overview                  │
    │  2. Scenario Narrative                 │
    │     (with export markers)              │
    │  3. Inject Timeline                    │
    │     (with export markers + 15-20      │
    │      detailed injects)                │
    │  4. Decision Points                    │
    │     (4-5 with full frameworks)         │
    │  5. Complications                      │
    │     (2-3 with triggers)                │
    │  6. Debrief Structure                  │
    │  7. Participant Materials              │
    │  8. Next Steps: Creating Professional  │
    │     Deliverables                       │
    │     (reference to DELIVERABLE-         │
    │      CREATION-GUIDE)                   │
    └────────────┬─────────────────────────┘
                 ↓
    STEP 3: Consultant receives Facilitator Package
                 ↓
    Consultant uses NEXT STEPS section:
    Option 1: Use Markdown Directly
    Option 2: Extract sections using export markers
    Option 3: Convert to PowerPoint (using
             DELIVERABLE-CREATION-GUIDE.md)
```

---

## File Dependencies & Usage

### TIER 1: ENTRY POINT (Consultant-Facing)

**STARTER-PROMPT.md** (Root Directory)
- **Who uses it:** Consultants/Prompt Engineers
- **When:** When starting TTX generation workflow
- **References:**
  - → AI-GENERATION-GUIDE.md (URL to components/AI-GENERATION-GUIDE.md)
  - → ERROR-HANDLING-GUIDE.md (URL to components/ERROR-HANDLING-GUIDE.md)
  - → DELIVERABLE-CREATION-GUIDE.md (URL to designGuides/DELIVERABLE-CREATION-GUIDE.md)
  - → All component libraries via GitHub URLs
- **Provides:** 5-question intake process + reference material URLs
- **Output:** 5 answers that feed into AI generation

---

### TIER 2: REFERENCE LIBRARIES (Component Libraries - Input Data)

**Location:** `components/` directory (will sync to GitHub)

**inject-library.md**
- **Who uses it:** AI system (LLM) during generation
- **When:** Step 2 of AI-GENERATION-GUIDE (Select Inject Library Items)
- **Contains:** Reusable inject templates for different incident phases (Detection, Investigation, Containment, Response, Recovery)
- **How used:** AI selects appropriate injects based on duration and customizes them for industry/context

**decision-points.md**
- **Who uses it:** AI system during generation
- **When:** Step 3 of AI-GENERATION-GUIDE (Select Decision Points)
- **Contains:** 5 major decision point frameworks (Containment, Ransom Payment, Notification, Recovery, Communication)
- **How used:** AI selects 2-5 points based on exercise duration and objective

**complications.md**
- **Who uses it:** AI system during generation
- **When:** Step 4 of AI-GENERATION-GUIDE (Select & Apply Complications)
- **Contains:** Reusable complication templates and triggers
- **How used:** AI selects complications based on duration and applies style-specific presentation

**TTX-STYLE-GUIDE.md**
- **Who uses it:** AI system during generation
- **When:** Step 5 of AI-GENERATION-GUIDE (Apply Style-Specific Formatting)
- **Contains:** Detailed formatting rules for Traditional, Blended, and Gamified styles
- **How used:** AI applies consistent style formatting to all injects, decisions, and complications

---

### TIER 3: GENERATION INSTRUCTIONS (System Rules)

**Location:** `components/` directory (will sync to GitHub)

**AI-GENERATION-GUIDE.md**
- **Who uses it:** AI system (Claude, ChatGPT, Gemini, etc.)
- **When:** After parsing 5 consultant answers, before generating output
- **Contains:**
  - 7-step generation process (Parse Q's → Select Injects → Select Decisions → Select Complications → Apply Style → Generate Output → Format for Sharing)
  - Step 5A: Inject Generation Standards (MANDATORY - all injects must have 4 components)
  - Step 5B: Export Markers (MANDATORY - 7 marker pairs required)
  - Step 5C: Decision Point Template (8 required components)
  - Step 5D: Facilitator Preparation Checklist
  - Step 5E: Scenario Narrative Requirements
  - Duration-specific requirements (2-hr = 8-12 injects; 4-hr = 15-20; etc.)
- **How used:** AI treats this as the "constitution" of exercise generation—mandatory requirements that MUST be met

---

### TIER 4: ERROR HANDLING & FALLBACKS (Operational Guidance)

**Location:** `components/` directory (will sync to GitHub)

**ERROR-HANDLING-GUIDE.md**
- **Who uses it:** Consultants/Prompt Engineers (when GitHub access fails)
- **When:** If LLM cannot access GitHub reference URLs
- **Contains:**
  - Signs that GitHub access has failed
  - Option 1: Try Again (60-70% success on retry)
  - Option 2: Manual Copy-Paste (full quality, more setup)
  - Option 3: Emergency Mode (80-85% quality, LLM generates from training data)
  - Emergency Mode Quality Standards (STILL must meet ALL mandatory requirements)
- **How used:** Decision tree for consultant on what to do when reference libraries unavailable

---

### TIER 5: QUALITY VALIDATION (Post-Generation)

**Location:** `components/` directory (will sync to GitHub)

**TTX-QUALITY-VALIDATOR.md**
- **Who uses it:**
  - AI systems (self-validation before output)
  - Consultants (verification before client delivery)
  - Project maintainers (monthly audits)
- **When:** After exercise generation, before delivery
- **Contains:**
  - Layer 1: CRITICAL REQUIREMENTS (6 items - must all pass or exercise fails)
  - Layer 2: QUALITY REQUIREMENTS (7 items - should mostly pass)
  - Layer 3: DELIVERABLE GUIDANCE (4 items - should all be present)
  - Validation checklist template
  - Common failure modes & fixes
- **How used:** Gating mechanism - exercises MUST pass critical requirements before delivery

---

### TIER 6: DELIVERABLE CONVERSION (Post-Generation Publishing)

**Location:** `designGuides/` directory (will NOT sync to GitHub - internal only)

**DELIVERABLE-CREATION-GUIDE.md**
- **Who uses it:** Consultants (after receiving TTX output)
- **When:** When converting markdown facilitator guide to professional PowerPoint/documents
- **Contains:**
  - 3 delivery options (Markdown only, Export sections, Professional PowerPoint)
  - 200+ AI prompts for visual enhancements
  - Design principles (colors, typography, layout)
  - Slide-by-slide templates
- **How used:** Referenced in STARTER-PROMPT "After Generation" section and in "Next Steps" section of generated output

---

## Actual Usage Timeline: Example Session

**CONSULTANT SESSION: Finance Company, 4-hour Traditional Exercise**

```
T=0min:  Consultant copies STARTER-PROMPT.md from GitHub
         Consultant pastes into Claude

T=1min:  Claude displays 5 questions
         Consultant answers:
         1. Finance / Medium / Intermediate / Recent breach
         2. IR plan validation
         3. 4-hour, In-person
         4. Mixed (IT + C-suite)
         5. Traditional

T=2min:  Claude attempts to fetch from GitHub:
         ✓ ransomware-scenario.md
         ✓ inject-library.md
         ✓ decision-points.md
         ✓ complications.md
         ✓ TTX-STYLE-GUIDE.md
         ✓ AI-GENERATION-GUIDE.md

T=3min:  Claude reads AI-GENERATION-GUIDE.md Step 1-5
         Claude selects 15 injects from inject-library.md (finance-customized)
         Claude selects 4-5 decision points from decision-points.md
         Claude selects 2-3 complications from complications.md
         Claude applies Traditional style from TTX-STYLE-GUIDE.md

T=4min:  Claude starts GENERATING output following AI-GENERATION-GUIDE steps 5A-5E:
         - Every inject: 300-500 word content + 4-6 facilitator prompts + 4-6 evaluation points
         - Export markers: 7 required pairs placed correctly
         - Decision points: 8-component template per decision
         - Scenario: Finance org profile + threat actor + attack timeline
         - Facilitator prep: Week-before checklist
         - Style: Traditional (facilitator-paced, no scoring, Socratic)

T=12min: Claude completes output
         Claude validates using TTX-QUALITY-VALIDATOR:
         - Critical Layer: 6/6 PASS (inject count ✓, markers ✓, components ✓, no TBD ✓, style ✓, decisions ✓)
         - Quality Layer: 7/7 PASS (scenario ✓, facilitation ✓, prep ✓, debrief ✓, materials ✓, format ✓, complexity ✓)
         - Deliverable Layer: 4/4 PASS (next steps ✓, export guidance ✓, file saving ✓, links ✓)
         Result: PASS - Ready to deliver

T=13min: Claude outputs facilitator package with:
         - Exercise Overview
         - Scenario Narrative (wrapped in export markers)
         - Inject Timeline: 18 injects, each with 4 required components (wrapped in export markers)
         - 4 Decision Points with full frameworks (wrapped in export markers)
         - 2 Complications (wrapped in export markers)
         - Debrief Structure (wrapped in export markers)
         - Participant Brief (wrapped in export markers)
         - Next Steps: Creating Professional Deliverables (reference to DELIVERABLE-CREATION-GUIDE)

T=14min: Consultant receives 25-page markdown facilitator guide
         Consultant can:
         Option A: Use markdown directly
         Option B: Extract SCENARIO-NARRATIVE for participant pre-briefing
         Option B: Extract INJECT-TIMELINE for facilitator reference card
         Option C: Follow "Next Steps" → DELIVERABLE-CREATION-GUIDE to convert to PowerPoint
```

---

## File Status & Syncing

### Files WILL Sync to GitHub (Public/Accessible):

✅ **Root Level:**
- STARTER-PROMPT.md (Entry point)
- README.md

✅ **`/components/` Directory:**
- AI-GENERATION-GUIDE.md (NEW - moved from designGuides)
- ERROR-HANDLING-GUIDE.md (NEW - moved from root)
- TTX-QUALITY-VALIDATOR.md (NEW)
- SYSTEM-ARCHITECTURE.md (NEW - this file)
- inject-library.md (already here)
- decision-points.md (already here)
- complications.md (already here)
- TTX-STYLE-GUIDE.md (already here)

✅ **`/scenarios/` Directory:**
- ransomware-scenario.md (already here)

### Files will NOT Sync (Internal Only):

❌ **`/designGuides/` Directory:**
- DELIVERABLE-CREATION-GUIDE.md (stays here - internal only, referenced via designGuides URL)
- ARCHITECTURE-SUMMARY.md
- POC files
- All other internal documentation

---

## Critical System Constraints

### What CANNOT Change (Breaks System):

❌ **STARTER-PROMPT.md structure**
- 5 questions MUST stay the same (consultant interface)
- GitHub URL references MUST remain valid
- Process flow MUST be preserved

❌ **Component library file names**
- If renamed, GitHub URLs break
- If moved to wrong directory, won't sync

❌ **Mandatory requirements in AI-GENERATION-GUIDE.md**
- Inject count minimums (8-12, 15-20, 25-35)
- 7 export marker pairs (non-negotiable)
- 4 inject components (Content, Prompts, Evaluation, Response)

### What CAN Change (Without Breaking):

✅ **Content within files**
- Specific inject examples
- Decision point scenarios
- Complication templates
- Style guide details

✅ **File locations (as long as GitHub URLs updated)**
- Can move files between directories
- Can rename files
- MUST update URLs in STARTER-PROMPT when moving

✅ **Guidance and instructions**
- AI-GENERATION-GUIDE detailed steps
- ERROR-HANDLING options
- Quality validator criteria

---

## How Files Relate to Each Other

```
INFORMATION FLOW:

STARTER-PROMPT.md (Entry, Questions)
    ↓
AI-GENERATION-GUIDE.md (Rules: How to answer the questions)
    ├─→ Uses: inject-library.md (What injects exist)
    ├─→ Uses: decision-points.md (What decisions exist)
    ├─→ Uses: complications.md (What complications exist)
    ├─→ Uses: TTX-STYLE-GUIDE.md (How to format by style)
    └─→ Uses: scenarios/ransomware-scenario.md (Base scenario)

AI-GENERATION-GUIDE.md OUTPUT
    ↓
TTX-QUALITY-VALIDATOR.md (Check: Did we follow the rules?)

OUTPUT (If valid)
    ↓
Consultant receives facilitator package
    ├─→ Can use directly
    ├─→ Can extract sections using EXPORT MARKERS
    └─→ Can follow "Next Steps" → DELIVERABLE-CREATION-GUIDE.md

ERROR PATH:
If GitHub fails → ERROR-HANDLING-GUIDE.md (What to do?)
    ├─→ Option 1: Retry (try Step 1 again)
    ├─→ Option 2: Manual paste (provide reference files manually)
    └─→ Option 3: Emergency Mode (LLM generates from training)
        (Still validates with TTX-QUALITY-VALIDATOR)
```

---

## Summary: File Organization by Purpose

| Purpose | Files | Location | Syncs? |
|---------|-------|----------|--------|
| Entry Point | STARTER-PROMPT.md | Root | ✅ |
| Component Data | inject-library.md, decision-points.md, complications.md, TTX-STYLE-GUIDE.md | /components/ | ✅ |
| Scenario Data | ransomware-scenario.md | /scenarios/ | ✅ |
| Generation Rules | AI-GENERATION-GUIDE.md | /components/ | ✅ |
| Quality Validation | TTX-QUALITY-VALIDATOR.md | /components/ | ✅ |
| Error Handling | ERROR-HANDLING-GUIDE.md | /components/ | ✅ |
| System Documentation | SYSTEM-ARCHITECTURE.md (this file) | /components/ | ✅ |
| Deliverable Guide | DELIVERABLE-CREATION-GUIDE.md | /designGuides/ | ❌ |
| Internal Docs | POC files, TESTING docs, etc. | /designGuides/ | ❌ |

---

## Key Takeaway

**The TTX system is entirely prompt-driven.** When a consultant pastes STARTER-PROMPT.md into an LLM:

1. **LLM fetches** all component libraries from GitHub (or uses fallback)
2. **LLM reads** AI-GENERATION-GUIDE.md as the "rules"
3. **LLM generates** output following those rules
4. **LLM validates** output using TTX-QUALITY-VALIDATOR.md
5. **LLM delivers** professional facilitator package

Everything is coordinated through markdown files with clear references, not code or configuration.

---

**End of System Architecture Document**
