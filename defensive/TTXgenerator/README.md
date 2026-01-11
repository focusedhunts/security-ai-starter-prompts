# TTX Generator - Conversational Tabletop Exercise Creator

**Create customized incident response tabletop exercises in 5-10 minutes using AI.**

This tool generates professional exercise facilitator packages through a natural conversation with an LLM. Answer six simple questions about your client and desired exercise, and receive a complete customized exercise ready for delivery.

**Note:** While designed to work across multiple LLMs, **Claude produces the most complete and consistent outputs**. See [LLM Compatibility & Current State](#️-important-llm-compatibility--current-state) for details. This tool was created using Claude, which might explain the bias. The tool is good, not great, so expect to refine outputs to make this a better final solution.

---

**Remember:** This tool generates exercise *plans*, not exercises themselves. You (the consultant) facilitate the exercise with participants. The TTX Generator helps you create it faster, but your facilitation expertise is essential for success—managing the room, guiding discussions, and helping participants learn from the experience.

---

## Quick Start

1. **Copy** [STARTER-PROMPT.md](STARTER-PROMPT.md)
2. **Paste** into Claude (recommended), ChatGPT, or Gemini
3. **Answer** six questions about your client and exercise needs
4. **Receive** a complete facilitator package in 5-10 minutes
5. **Review & refine** before delivery

**Total time: 5-10 minutes** (vs. 2-4 hours manual creation)

---

## ⚠️ Important: LLM Compatibility & Current State

**The Reality:** Achieving consistent output quality across different LLMs has proven to be almost a lost cause. While the TTX Generator works with Claude, ChatGPT, and Gemini, the results vary significantly:

- **Claude:** Most complete and consistent outputs (not surprising—Claude built most of this system)
- **ChatGPT:** Usable but may miss components or vary in structure
- **Gemini:** Functional but often requires significant review and editing

**Sample outputs are available** in [sampleOutputs/](sampleOutputs/) for comparison—Claude's outputs are notably more complete.

**Our Assessment:** This tool is **good, not great, and probably can be better**. It dramatically reduces creation time, but:
- Always review outputs carefully before client delivery
- Expect to refine and adjust generated content
- Your facilitation expertise remains essential
- Use with caution—this is a starting point, not a final product

**Future Development:** We encourage others to take it from here. Community contributions to improve cross-LLM consistency are welcome. Updates will be made as needed.

---

## Table of Contents

- [What You Get](#what-you-get)
- [Available Scenarios](#available-scenarios)
- [Exercise Styles](#exercise-styles)
- [How It Works](#how-it-works)
- [System Architecture](#system-architecture)
- [Creating Deliverables](#creating-deliverables)
- [Industry Customization](#industry-customization)
- [Network Issues & Error Handling](#network-issues--error-handling)
- [Resources](#resources)

---

## What You Get

The AI generates a complete **Markdown facilitator package** including:

- **Exercise Overview** - Objectives, participant roles, timeline
- **Scenario Narrative** - Threat actor profile, attack timeline, initial conditions
- **Inject Timeline** - 8-40+ injects (depending on duration) with timing, content, facilitator prompts, and evaluation points
- **Decision Points** - 4-5 major decision frameworks (containment, ransom payment, notification, recovery, communication)
- **Complications** - Realistic obstacles calibrated to skill level
- **Facilitator Guidance** - Pre-exercise checklist, delivery guidance, observation points
- **Debrief Structure** - Post-exercise review framework
- **Participant Materials** - Non-spoiler briefing and reference materials
- **Export Markers** - Built-in markers for easy section extraction and PowerPoint conversion

📖 **[Full details on components and quality standards →](designGuides/AI-GENERATION-GUIDE.md)**

---

## Available Scenarios

| Scenario | Difficulty | Technical Weight | Duration | Best For |
|----------|-----------|-----------------|----------|----------|
| **Business Email Compromise** | Beginner-Int | Low-Tech | 2-4 hr | Mixed teams, new to IR |
| **Ransomware Attack** | Intermediate | Moderate-Tech | 2-4 hr, full-day | All industries, full IR lifecycle |
| **Data Breach - Customer PII** | Intermediate | Moderate-Tech | 4 hr, full-day | Customer-facing, compliance focus |
| **Insider Threat** | Advanced | High-Tech | 4 hr, full-day | Technical teams, forensics |
| **Cloud Misconfiguration** | Intermediate | Moderate-Tech | 2-4 hr | Cloud-native, DevOps teams |
| **Supply Chain Compromise** | Advanced | High-Tech | Full-day | Tech vendors, complex supply chains |
| **Third-Party Vendor Breach** | Advanced | Moderate-Tech | 4 hr, full-day | Vendor-dependent organizations |

**Difficulty Levels:**
- **Beginner-Intermediate:** Clear progression, straightforward decisions, learning-focused
- **Intermediate:** Realistic complexity, some ambiguity, trade-offs required
- **Advanced:** Significant ambiguity, multiple threads, forensic complexity

**Technical Weight:**
- **Low-Tech:** Business-focused, minimal technical detail
- **Moderate-Tech:** Balanced technical and business concerns
- **High-Tech:** Forensics-heavy, specialized knowledge required

📖 **[Detailed scenario descriptions and selection guidance →](scenarios/)**

---

## Exercise Styles

Choose one of three presentation styles:

| Style | Pace | Discussion Time | Scoring | Best For |
|-------|------|----------------|---------|----------|
| **Traditional** | Facilitator-paced | 20-30 min per inject | None | Beginners, learning focus |
| **Blended** | Moderate windows | 10 min + 5 min decision | Light | Mixed groups (most common) |
| **Gamified** | Strict timing | 3-5 min decisions | Heavy | Advanced teams, pressure testing |

📖 **[Complete style guide and facilitation tips →](components/TTX-STYLE-GUIDE.md)**

---

## How It Works

### The Six Questions

1. **Which incident scenario?** (Choose from available scenarios)
2. **Tell me about your client** (Industry, size, IR maturity - 2-3 sentences)
3. **Primary exercise objective?** (IR plan validation, communication, decision-making, compliance, etc.)
4. **Exercise duration?** (2-hour, 4-hour, 6-hour, or full-day)
5. **Participant profile?** (Technical/executive/mixed, experience level, approximate count)
6. **Exercise style preference?** (Traditional, Blended, or Gamified)

### What Happens Next

1. LLM reads scenario and component libraries from GitHub
2. Applies industry-specific customizations (healthcare → HIPAA, finance → PCI-DSS, etc.)
3. Selects appropriate number of injects (8-12 for 2hr, 15-20 for 4hr, 25-35+ for full-day)
4. Customizes decision points and complications for your context
5. Generates complete facilitator package with all export markers
6. You review, refine with follow-up questions, and convert to deliverable format

📖 **[Complete system architecture and component interaction →](#system-architecture)**

---

## System Architecture

### Component Files

| File | Purpose | When Used |
|------|---------|-----------|
| **STARTER-PROMPT.md** | Entry point with 6 questions + GitHub URLs | Start of workflow |
| **inject-library.md** | 30+ reusable inject templates by phase | During generation |
| **decision-points.md** | 5 major decision frameworks | Customizing decisions |
| **complications.md** | Obstacle templates by difficulty | Adding challenges |
| **TTX-STYLE-GUIDE.md** | Formatting rules for 3 exercise styles | Applying style constraints |
| **AI-GENERATION-GUIDE.md** | Step-by-step LLM instructions | Generation rules |
| **TTX-QUALITY-VALIDATOR.md** | 3-layer validation checklist | Quality assurance |
| **DELIVERABLE-CREATION-GUIDE.md** | Markdown → PowerPoint conversion | Post-generation |

### Generation Process

```
STARTER-PROMPT → 6 Questions → LLM fetches components from GitHub →
Parse answers → Select injects (duration-based) → Customize decisions (industry-based) →
Add complications (skill-based) → Apply style formatting → Generate package →
Validate quality → Output with export markers
```

### Mandatory Output Components

Every generated package must include:
1. Exercise Overview
2. Facilitator Preparation Checklist
3. Scenario Narrative (with export marker)
4. Inject Timeline (15-20 injects minimum for 4hr, each with content, prompts, evaluation points)
5. Decision Points (4-5 frameworks with options A/B/C)
6. Complications (2-3 obstacles)
7. Debrief Structure
8. Participant Materials
9. All 7 export markers for section extraction

📖 **[Complete component interaction details →](components/)**

---

## Creating Deliverables

### Three Options

**Option 1: Use Markdown Directly**
- Print and use in virtual exercises
- Minimal prep needed

**Option 2: Convert to PowerPoint**
```bash
pandoc facilitator-package.md -o facilitator-package.pptx
```

**Option 3: Professional Presentation**
- Follow [DELIVERABLE-CREATION-GUIDE.md](designGuides/DELIVERABLE-CREATION-GUIDE.md)
- Includes slide-by-slide transformation strategy
- AI-generated graphics prompts
- Professional design principles
- Quality checklist

### Export Markers for Section Extraction

The generated package includes HTML comment markers for easy extraction:
- `FACILITATOR-GUIDE` - Complete package
- `SCENARIO-NARRATIVE` - Participant-safe version
- `INJECT-TIMELINE` - Facilitator only
- `DECISION-POINTS` - Decision frameworks
- `COMPLICATIONS` - Obstacle sequence
- `DEBRIEF-TEMPLATE` - Post-exercise structure
- `PARTICIPANT-BRIEF` - Non-spoiler materials

📖 **[Complete deliverable creation guide →](designGuides/DELIVERABLE-CREATION-GUIDE.md)**

---

## Industry Customization

### Automatic Customizations

**Healthcare:** HIPAA notifications, patient care impact, CMS/state health department references
**Finance:** PCI-DSS, SEC reporting, banking regulators, OFAC considerations
**Retail:** Customer data breach, reputation damage, seasonal revenue impact
**Manufacturing:** OT/IT convergence, production disruption, supply chain impact
**Technology/SaaS:** Multi-tenant impact, SLA violations, service uptime

### Duration-Based Variations

**2-hour:** 8-12 injects, detection → initial response, beginner-friendly
**4-hour:** 15-20 injects, full IR lifecycle, 2-3 complications (most popular)
**Full-day:** 25-35+ injects, deep investigation, 4+ complications, leadership briefings

### Skill Level Adjustments

**Beginner:** Simple technical elements, clear progression, supportive guidance
**Intermediate:** Moderate complexity, some ambiguity, realistic challenges
**Advanced:** Complex details, significant ambiguity, organizational politics

---

## Network Issues & Error Handling

### If LLM Can't Access GitHub

**Path 1: Retry (60-70% success)**
- Wait 5 minutes, paste STARTER-PROMPT again

**Path 2: Manual Copy-Paste (100% success, full quality)**
- Copy files from GitHub manually
- Paste into conversation with "Use this scenario: [content]"

**Path 3: Emergency Mode (100% success, 80-85% quality)**
- Tell LLM: "Generate without GitHub access, use your knowledge"
- LLM generates from training data

**Path 4: Switch LLM (98% success)**
- Try different LLM (often has better GitHub access)

### Corporate Networks

- Ask IT to whitelist `raw.githubusercontent.com`
- Use VPN if available
- Use personal device
- Use Emergency Mode

📖 **[Complete error handling guide →](components/ERROR-HANDLING-GUIDE.md)**

---

## Resources

### Core Files
- **[STARTER-PROMPT.md](STARTER-PROMPT.md)** - Copy this to get started
- **[Scenarios](scenarios/)** - Complete threat narratives and decision frameworks
- **[Components](components/)** - Inject library, decision points, complications, style guide
- **[Design Guides](designGuides/)** - AI generation guide, deliverable creation guide

### Reference Materials
- **[Sample Outputs](sampleOutputs/)** - Compare Claude, ChatGPT, and Gemini outputs
- **Alternative Method:** [IRTabletopExercisePlanning(ThreeStaged).md](../IRTabletopExercisePlanning(ThreeStaged).md) - Detailed three-stage planning (50+ customization fields)
- **Book:** [*Prompt Intelligence: An AI Framework for Security Professionals*](https://focusedhunts.com) - Principles underlying this prompt

---

## Key Features

✅ Six-question customization (scenario, context, objectives, duration, participants, style)
✅ 7 scenarios across difficulty levels and technical weights
✅ Three exercise styles (Traditional, Blended, Gamified)
✅ Industry-specific customization (Healthcare, Finance, Retail, Manufacturing, Technology)
✅ Built-in export markers for easy sharing and conversion
✅ PowerPoint creation guidance
✅ Professional quality, facilitator-ready materials
✅ Error handling with offline/emergency modes

---

## Requirements

- **Internet connection** (to access GitHub scenario library, or use Emergency Mode)
- **AI Tool:** Claude (recommended), ChatGPT, Gemini, or any LLM that can read URLs
- **File:** Copy of [STARTER-PROMPT.md](STARTER-PROMPT.md)

---

## Questions or Contributions?

- **GitHub Issues:** Report bugs or suggest improvements
- **GitHub Discussions:** Share experiences using the TTX Generator
- **Pull Requests:** Have a better scenario, complication, or LLM-specific refinement? Submit a PR

---

**Remember:** This tool generates exercise *plans*, not exercises themselves. You (the consultant) facilitate the exercise with participants. The TTX Generator helps you create it faster, but your facilitation expertise is essential for success—managing the room, guiding discussions, and helping participants learn from the experience.
