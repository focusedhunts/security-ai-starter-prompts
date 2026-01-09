# TTX Generator - Conversational Tabletop Exercise Creator

**Create customized incident response tabletop exercises in 5-10 minutes using AI.**

This tool lets you generate professional exercise facilitator packages by having a natural conversation with ChatGPT, Claude, or any LLM. Answer six simple questions about your client and desired exercise, and get a complete customized exercise ready for delivery.

---

**Remember:** This tool generates exercise *plans*, not exercises themselves. You (the consultant) facilitate the exercise with participants. The TTX Generator helps you create it faster, but your facilitation expertise is essential for success; managing the room, guiding discussions, and helping participants learn from the experience.

---

## What is This?

The TTX Generator is a **conversational prompt** that works with any AI language model to create incident response tabletop exercises (TTX) tailored to your client's specific context.

Copy a short prompt, paste into your preferred AI tool, answer six questions (including incident scenario type, client context, objectives, duration, participant profile, and exercise style), and receive a complete facilitator package in 20-30 minutes. The package includes customized scenario narrative, inject timeline with delivery guidance, key decision points, facilitator notes, and participant materials.

---

## How the TTX Generator Works: Complete System Overview

The TTX Generator is a **modular, prompt-driven system** that coordinates multiple markdown components through a single starter prompt. Understanding how these pieces interact helps you use the system effectively and customize it for your needs.

### System Architecture

When you paste **STARTER-PROMPT.md** into an LLM, the following process occurs automatically:

```
1. CONSULTANT PROVIDES STARTER-PROMPT
   ↓
2. LLM FETCHES 6 COMPONENT LIBRARIES (automatically via GitHub URLs):
   • Selected Scenario (ransomware, BEC, data breach, or insider threat)
   • inject-library.md → 30+ reusable inject templates
   • decision-points.md → 5 major decision frameworks
   • complications.md → Complication templates by difficulty level
   • TTX-STYLE-GUIDE.md → Formatting rules for Traditional/Blended/Gamified
   • AI-GENERATION-GUIDE.md → Step-by-step generation instructions
   ↓
3. CONSULTANT ANSWERS 5 QUESTIONS
   ↓
4. LLM FOLLOWS AI-GENERATION-GUIDE (Generation Rules):
   Step 1: Parse your answers → Extract context
   Step 2: Select injects → Match to duration (8-12 for 2hr, 15-20 for 4hr, etc.)
   Step 3: Select decision points → Customize for industry
   Step 4: Select complications → Calibrate for skill level + style
   Step 5: Apply style constraints → Traditional/Blended/Gamified formatting
   Step 6: Generate complete output → Facilitator guide with 7 export markers
   ↓
5. YOU RECEIVE COMPLETE FACILITATOR PACKAGE:
   • Exercise overview & learning objectives
   • Customized scenario narrative
   • 15-20+ injects with timing, content, & facilitator prompts
   • 4-5 decision points with full frameworks
   • 2-3 complications with realistic triggers
   • Debrief structure
   • Participant materials (non-spoiler)
   • Next Steps: Converting to PowerPoint
   ↓
6. YOU DELIVER (Choose Your Option):
   Option A: Use markdown directly in exercise
   Option B: Extract sections using export markers (SCENARIO-NARRATIVE, PARTICIPANT-BRIEF, etc.)
   Option C: Convert to professional PowerPoint via DELIVERABLE-CREATION-GUIDE.md
```

### Component Interaction Details

**inject-library.md** contains 30+ pre-designed injects organized by incident phase:
- Detection phase (finding the incident)
- Investigation phase (understanding scope)
- Containment phase (stopping the spread)
- Response phase (managing the crisis)
- Recovery phase (restoring operations)

The LLM uses your duration choice to select appropriate injects. A 4-hour exercise gets 15-20 injects; a 2-hour gets 8-12; a full-day gets 40+.

**decision-points.md** contains 5 major decision frameworks:
- Containment strategy (aggressive vs. selective isolation)
- Ransom payment decision (pay, don't pay, negotiate)
- Data breach notification (scope, timing, communication)
- Recovery approach (backup restoration, rebuild, negotiation)
- Stakeholder communication (board, customers, media, regulators)

The LLM customizes these for your industry. Healthcare adds HIPAA considerations; Finance adds regulatory reporting; Manufacturing adds OT/IT convergence issues.

**complications.md** provides realistic obstacles that emerge during incidents:
- Second breach discovered during initial response
- Backup systems found to be corrupted
- Regulatory investigation announced
- Supply chain impacts emerging
- Media coverage and public pressure

The LLM selects complications appropriate to your exercise style (fewer for Traditional discussions, more for Gamified challenges).

**TTX-STYLE-GUIDE.md** enforces consistent formatting:
- **Traditional:** Facilitator-paced, no time pressure, deep discussion (20-30 min per inject)
- **Blended:** Moderate time pressure, balanced discussion (10 min discussion + 5 min decision)
- **Gamified:** Strict timing, limited info, heavy scoring (3-5 min decisions with penalty timers)

**AI-GENERATION-GUIDE.md** is the "constitution" of exercise generation:
- 7 mandatory steps for creating exercises
- Quality requirements for each inject (must include: Content 300-500 words, 4-6 Facilitator Prompts, 4-6 Evaluation Points, Expected Response)
- 7 mandatory export markers that MUST appear in output (FACILITATOR-GUIDE, SCENARIO-NARRATIVE, INJECT-TIMELINE, DECISION-POINTS, COMPLICATIONS, DEBRIEF-TEMPLATE, PARTICIPANT-BRIEF)
- Duration-specific requirements (2-hour minimum 8 injects, 4-hour minimum 15, etc.)
- Emergency Mode standards (if GitHub access fails, LLM still produces 85-100% quality from training data)

### Fallback Paths (If GitHub Access Fails)

If the LLM cannot fetch reference libraries from GitHub (corporate firewall, temporary outage):

**ERROR-HANDLING-GUIDE.md** provides three recovery options:

1. **Retry (60-70% success):** Wait 5 minutes, paste STARTER-PROMPT again. Different server routing often succeeds.
2. **Manual Copy-Paste (100% success):** Manually copy reference file contents into chat. Takes 10-15 minutes extra but guarantees success.
3. **Emergency Mode (100% success, 80-85% quality):** Tell LLM "Generate without GitHub access, use your knowledge." LLM generates from training data—still professional and usable, slightly less customized.

**Important:** Emergency Mode maintains full quality standards. Even without GitHub access, LLM must produce minimum inject count, all 7 export markers, complete decision frameworks, and no placeholder text.

---

## How to Use This

### Step 1: Copy the Starter Prompt (30 seconds)

Open [STARTER-PROMPT.md](STARTER-PROMPT.md) and copy the entire prompt.

### Step 2: Paste into Your Preferred LLM (10 seconds)

- Open ChatGPT, Claude, or your preferred AI tool
- Paste the prompt
- Start the conversation

### Step 3: Answer 6 Simple Questions (5-10 minutes)

The AI will ask you:

1. **"Which incident scenario matches your client's risk profile?"**
   - Answer: Choose one scenario type from available options
   - Options: Ransomware Attack, Business Email Compromise, Data Breach - Customer PII, Insider Threat - Malicious Employee, or others
   - Example: "Ransomware Attack - our client was recently targeted and wants to test their response capability"

2. **"Tell me about your client in 2-3 sentences."**
   - Answer: Brief description (industry, org size, IR maturity)
   - Example: "250-bed hospital system, moderate IR maturity, had ransomware near-miss last quarter"

3. **"What's your primary exercise objective?"**
   - Answer: What capability do you want to test? (IR plan validation, communication, decision-making, regulatory compliance, crisis management, etc.)
   - Example: "Test IR plan effectiveness, especially cross-functional communication under pressure"

4. **"How long is the exercise?"**
   - Answer: 2-hour, 4-hour, 6-hour, or full-day format
   - Example: "4 hours, virtual format"

5. **"Who's in the room (participant profile)?"**
   - Answer: Mostly technical, mostly executive, or mixed; approximate number
   - Example: "Mixed—SOC team is intermediate, executives are non-technical, about 30 people across breakout rooms"

6. **"How do participants prefer to learn (exercise style)?"**
   - Answer: Traditional (discussion-focused), Blended (balanced), or Gamified (high-intensity with scoring)
   - Example: "Blended - they want some discussion time but also want to feel time pressure"

### Step 4: AI Generates Your Package (2-3 minutes)

The AI automatically:
- Reads the ransomware scenario from GitHub
- Applies industry-specific customizations (healthcare, finance, retail, manufacturing, tech)
- Selects appropriate injects and complications for your scenario
- Generates a facilitator package in markdown

### Step 5: Review & Refine (10-15 minutes)

- Review the generated content
- Ask follow-up questions: "Add more complications," "Make the ransom amount $500K," "Adjust for cloud-based infrastructure"
- Optionally convert to PowerPoint using Pandoc or manually

**Total time: 5-10 minutes** (vs. 2-4 hours manual creation)

---

## Exercise Styles - Choose Your Approach

The TTX Generator supports **three exercise styles** tailored to your participants and objectives:

### Traditional TTX (Discussion-Based)
- **Best for:** Learning-focused groups, beginners, non-technical executives
- **Style:** Discussion-focused, no time pressure, deep exploration of options
- **Pace:** You control (no rush, plenty of discussion time)
- **Focus:** Understanding IR processes and decision-making

Example: Healthcare board doing first TTX—want to learn how incidents work

### Blended TTX (Balanced)
- **Best for:** Most consultant engagements (mixed groups)
- **Style:** Structured scenario with moderate time pressure, some surprise elements
- **Pace:** Facilitated (tighter timeline than traditional, but with discussion)
- **Focus:** Learning + testing IR capability

Example: Hospital IT + C-suite together—need to both learn and see response capability

### Gamified TTX (High-Intensity Challenge)
- **Best for:** Advanced technical teams, experienced IR groups
- **Style:** Real time pressure, scoring/consequences tracked, surprise complications
- **Pace:** Fast-paced (injects arrive on schedule, strict timing)
- **Focus:** Testing decision speed and response effectiveness under pressure
- **Scoring:** Heavy (point-based, tracked, competitive)
- **Inject timing:** Scheduled and strict (T+10, T+20, etc.)
- **Information:** Limited context (uncertainty and pressure intentional)
- **Complications:** Surprise elements with minimal or no warning

Example: SOC team doing quarterly IR challenge—want real-world pressure and scoring

**One scenario, three presentation styles.** Tell us your style preference when you answer the questions, and we'll customize the exercise accordingly.

#### Detailed Style Comparison

| Dimension | Traditional | Blended | Gamified |
|-----------|-----------|---------|----------|
| **Inject Timing** | Facilitator-paced (no rush) | 10-15 min windows | Scheduled/strict (T+10, T+20) |
| **Discussion Time** | 20-30 min per inject | 10 min discussion + 5 min decision | 3-5 minutes per decision |
| **Information Availability** | All options upfront | Most context given, some gaps | Limited context (pressure) |
| **Complications** | Clearly introduced | 5-10 min warning | Surprise, minimal warning |
| **Scoring** | None (learning focus) | Light (informational) | Heavy (point-based, competitive) |
| **Facilitator Role** | Socratic guide, coach | Timeline manager, balanced | Deadline enforcer, score tracker |
| **Best For** | Beginners, learning focus | Mixed groups, most common | Advanced teams, high pressure |

👉 See [components/TTX-STYLE-GUIDE.md](components/TTX-STYLE-GUIDE.md) for detailed information on choosing and executing each style.

---

## What You Get

The AI generates a **Markdown document** including:

### Exercise Overview
- Objectives and learning outcomes
- Participant roles and expectations
- Scenario summary (non-spoiler for participants)
- Timeline and logistics

### Detailed Scenario Narrative
- Threat actor profile and motivations
- Attack timeline with technical detail
- Initial detection points
- Initial conditions (what participants know at start)

### Inject Timeline
- Table with: Inject #, Timing, Delivery Method, Content, Expected Response, Facilitator Notes
- Injects customized for industry (healthcare adds HIPAA notifications, patient care impact, etc.)
- Complications built in based on skill level

### Key Decision Points with Guidance
1. **Containment Strategy** - Aggressive isolation vs. selective vs. monitored (healthcare adds patient care considerations)
2. **Ransom Payment Decision** - Legal, ethical, insurance, practical considerations
3. **Data Breach Notification** - Regulatory requirements (HIPAA for healthcare, PCI for finance, etc.)
4. **Recovery Strategy** - Restore from backup vs. rebuild vs. negotiate
5. **Stakeholder Communication** - Executive briefings, customer communication, media management

### Facilitator Guidance
- Pre-exercise preparation checklist
- Semi-scripted inject delivery guidance ("here's what to say")
- Observation guidance ("here's what to watch for")
- Common participant pitfalls and coaching prompts
- Debrief structure

### Participant Materials (Outline)
- Welcome letter and ground rules
- Initial scenario briefing (non-spoiler)
- Reference materials (organizational structure, systems, decision authorities)
- Role cards if using assigned roles

---

## Next Steps After Generation

### Option 1: Use Directly
- Print the markdown document
- Use directly in virtual exercise (share screen, facilitator reads injects)
- Minimal additional preparation needed

### Option 2: Convert to PowerPoint
If you prefer PowerPoint:
```bash
# Using Pandoc (free, open-source)
pandoc facilitator-package.md -o facilitator-package.pptx
```
This creates a presentation-ready document you can customize further.

### Option 3: Iterate & Refine
Ask the AI follow-up questions:
- "Add more complications for an advanced group"
- "Make the recovery challenge worse—backups are corrupted"
- "Add a media relations scenario"
- "Adjust the ransom amount to $250K"

---

## Creating Professional Client Deliverables

After generation, convert your markdown output into polished PowerPoint presentations or professional documents.

### The Complete Deliverable Creation Guide

We've created a comprehensive guide for transforming your markdown exercise into professional client deliverables:

📖 **[DELIVERABLE-CREATION-GUIDE.md](designGuides/DELIVERABLE-CREATION-GUIDE.md)**

This guide includes:

**Slide-by-Slide Transformation Strategy**
- How to map markdown sections to PowerPoint slides
- Detailed examples (Exercise Overview → 5 slides, Scenario Narrative → 8 slides, etc.)
- Layout templates (title slides, content slides, timelines, matrices)

**Visual Enhancement Suggestions**
- AI generation prompts for custom graphics
- Threat actor profiles ("Create menacing cybercriminal character with binary code background")
- Ransom notes and extortion graphics
- Attack timelines and decision trees
- Organizational charts and RACI matrices
- Technical indicators (EDR alerts, network diagrams, log entries)
- Social media/external pressure graphics (fake tweets, breaking news headlines)

**Professional Design Principles**
- Color schemes (Corporate Professional, Security Alert, Tech Modern, Healthcare Focus)
- Typography guidelines (fonts, sizes, hierarchy)
- White space and visual balance
- Style-specific guidance (Traditional = calm/blue, Gamified = urgent/red, Blended = balanced)

**Tools & Resources**
- Recommended software (PowerPoint, Canva, DALL-E, Midjourney, Lucidchart)
- Stock image resources (Unsplash, Pexels, Flaticon)
- Template libraries

**Export Instructions**
- How to save sections as markdown or text files
- File naming conventions for organizing multiple client engagements
- Who gets what (facilitator → full package, participants → non-spoiler brief, stakeholders → overview only)
- Step-by-step instructions for ChatGPT/Claude

**Quality Checklist**
- Content accuracy verification (customizations, timing, difficulty calibration)
- Visual quality checks (contrast, consistency, professionalism)
- Exercise integrity (no spoilers, realistic timing, clear guidance)
- Delivery readiness (technical setup, backup materials)

### Quick Transformation Example

**Markdown Input:** 25-page facilitator package
↓
**PowerPoint Output:** 45 professional slides

- Slides 1-4: Title & objectives (with security badge visual)
- Slides 5-9: Threat actor profile (AI-generated menacing character + TTPs)
- Slides 10-17: Scenario narrative (attack timeline graphic, network diagrams)
- Slides 18-36: Injects (1-2 per inject with alert styling for Gamified, discussion prompts for Traditional)
- Slides 37-42: Decision points (option matrices with pros/cons)
- Slides 43-45: Debrief & lessons learned (recovery roadmap)

**Design:** Professional color scheme, consistent typography, high-contrast, zero clutter

👉 **Start with DELIVERABLE-CREATION-GUIDE.md for complete guidance with detailed examples and transformation patterns.**

---

## Available Scenarios

The TTX Generator supports multiple incident scenarios across difficulty levels and threat types.

### Understanding Difficulty Levels & Technical Weight

Every scenario is classified by two dimensions:

#### **Difficulty Levels** (Participant IR Experience)

**Beginner-Intermediate**
- **Best for:** Teams new to IR, organizations doing their first tabletop
- **Participant assumption:** Limited IR process experience, learning-focused
- **Scenario characteristics:**
  - Clear cause-and-effect chain of events
  - Straightforward detection (obvious alerts or indicators)
  - Linear progression (fewer surprise twists)
  - Limited ambiguous information
  - Clear decision points with obvious options
  - Supportive facilitator guidance emphasizes learning
- **Examples:** Business Email Compromise (clear fraud detection), initial breach discovery
- **Testing focus:** IR process understanding, basic decision-making, communication

**Intermediate**
- **Best for:** Teams with some IR experience, mixed experience groups
- **Participant assumption:** Familiar with IR processes, some real-world incident experience
- **Scenario characteristics:**
  - Realistic complexity with multiple concurrent issues
  - Some ambiguous information (requires investigation to answer)
  - Scope expansion surprises (initial assessment was incomplete)
  - Multi-faceted decisions with legitimate pros/cons
  - Trade-offs between options (no clearly "right" answer)
  - Realistic obstacles and resource constraints
- **Examples:** Ransomware with backup complications, data breach with compliance angle
- **Testing focus:** Decision-making under uncertainty, resource prioritization, stakeholder management

**Advanced**
- **Best for:** Experienced IR teams, SOC professionals, annual challenge exercises
- **Participant assumption:** Significant IR experience, familiar with complex incidents
- **Scenario characteristics:**
  - Significant ambiguity and conflicting information
  - Multiple parallel incident threads
  - Red herrings and false leads (investigation may go wrong)
  - Organizational politics and stakeholder conflicts
  - Realistic forensic complexities and evidence handling
  - Regulatory/legal considerations requiring careful judgment
  - Ethical dilemmas with no perfect solution
- **Examples:** Insider threat with evidence integrity issues, sophisticated supply chain compromise
- **Testing focus:** Advanced forensics, strategic decision-making, crisis leadership, organizational coordination

#### **Technical Weight** (How Much Technical Detail Matters)

Independent of difficulty level, scenarios vary in how heavily they emphasize technical vs. operational/business concerns:

**Low-Tech (Business-Focused)**
- **Technical details:** Minimal or simplified
- **Focus:** Communication, decision-making, business impact
- **Participant roles:** Finance, HR, executive leadership shine
- **Example:** Business Email Compromise (about fraud detection and wire transfer process, not deep forensics)
- **Best for:** Mixed teams, non-technical executives, decision-making focus
- **Facilitator guidance:** Emphasizes business judgment and stakeholder coordination

**Moderate-Tech (Balanced)**
- **Technical details:** Realistic but not overwhelming
- **Focus:** Incident response AND business impact equally weighted
- **Participant roles:** Both technical teams and business leadership have important decisions
- **Example:** Ransomware scenario (requires forensics AND ransom payment decision AND regulatory notification)
- **Best for:** Cross-functional teams, comprehensive IR testing
- **Facilitator guidance:** Balances technical coaching with business context

**High-Tech (Forensics-Heavy)**
- **Technical details:** Extensive, realistic, requiring specialized knowledge
- **Focus:** Detection, forensics, technical investigation, system recovery
- **Participant roles:** SOC, IR specialists, system administrators lead
- **Example:** Insider threat with backdoor persistence, sophisticated supply chain compromise
- **Best for:** Technical teams, threat hunting exercises, advanced training
- **Facilitator guidance:** Emphasizes technical decision-making and forensic methodology

### Scenario Matrix - Currently Available

**These 4 scenarios are accessible via STARTER-PROMPT.md when you run the TTX Generator:**

| Scenario | Difficulty | Technical Weight | Best For | Duration |
|----------|-----------|-----------------|----------|----------|
| **Business Email Compromise** | Beginner-Intermediate | Low-Tech | All industries, mixed teams | 2-4 hour |
| **Ransomware Attack** | Intermediate | Moderate-Tech | All industries, full IR lifecycle | 2-4 hour, full-day |
| **Data Breach - Customer PII** | Intermediate | Moderate-Tech | Customer-facing businesses, compliance focus | 4-hour, full-day |
| **Insider Threat - Malicious** | Advanced | High-Tech | Technical teams, forensics focus | 4-hour, full-day |

✅ **All available scenarios are now accessible via STARTER-PROMPT.md**

### How to Choose a Scenario

1. **Match your client's team experience:**
   - New to IR? → Beginner-Intermediate
   - Some experience? → Intermediate
   - Experienced team? → Advanced

2. **Consider audience composition:**
   - Mostly non-technical? → Low-Tech scenarios
   - Mixed team? → Moderate-Tech scenarios
   - Mostly technical? → High-Tech scenarios

3. **Align with learning objectives:**
   - "Learn IR process" → Beginner-Intermediate
   - "Test decision-making" → Intermediate
   - "Challenge technical team" → Advanced, High-Tech

### Currently Available Scenarios (Accessible via STARTER-PROMPT)

#### **Ransomware Attack** (Intermediate, Moderate-Tech)
- **Threat progression:** Phishing → credential compromise → ransomware deployment and extortion
- **Tests:** Forensics, containment, business continuity, executive communication, legal coordination
- **Best for:** All industries (healthcare, finance, retail, manufacturing, technology)
- **Duration options:** 2-hour, 4-hour, or full-day exercises
- **Industry customizations:** Healthcare (HIPAA, patient care impact), Finance (PCI-DSS, banking systems), Retail (customer data, seasonal impact), Manufacturing (OT/IT convergence)

#### **Business Email Compromise** (Beginner-Intermediate, Low-Tech)
- **Threat progression:** Social engineering → account compromise → fraudulent wire transfer
- **Tests:** Fraud detection, communication, financial controls, executive coordination
- **Best for:** All industries, especially new IR teams, mixed technical/non-technical groups
- **Duration options:** 2-hour or 4-hour exercises

#### **Data Breach - Customer PII** (Intermediate, Moderate-Tech)
- **Threat progression:** External attack → data exfiltration → regulatory notification requirement
- **Tests:** Scope determination, forensics, compliance, customer communication, legal coordination
- **Best for:** Customer-facing businesses (retail, SaaS, fintech, healthcare), compliance-focused organizations
- **Duration options:** 4-hour or full-day exercises

#### **Insider Threat - Malicious Employee** (Advanced, High-Tech)
- **Threat progression:** Unauthorized access → IP theft → backdoor installation → discovery
- **Tests:** Forensic analysis, evidence handling, HR coordination, legal considerations, organizational politics
- **Best for:** Technical teams, security-focused organizations, advanced IR training
- **Duration options:** 4-hour or full-day exercises

#### **Cloud Misconfiguration** (Intermediate, Moderate-Tech)
- **Threat progression:** Misconfigured cloud storage → exposed data → discovery and regulatory notification
- **Tests:** Cloud infrastructure assessment, data classification, compliance remediation, scope determination
- **Best for:** Cloud-native organizations, DevOps teams, infrastructure-focused teams
- **Duration options:** 2-hour or 4-hour exercises

#### **Supply Chain Compromise** (Advanced, High-Tech)
- **Threat progression:** Third-party vendor breach → supply chain contamination → cascading customer impact
- **Tests:** Forensic analysis, supply chain risk assessment, customer communication, incident coordination
- **Best for:** Technology vendors, organizations with complex supply chains, advanced technical teams
- **Duration options:** Full-day exercises

#### **Third-Party Vendor Compromise** (Advanced, Moderate-Tech)
- **Threat progression:** Vendor system breach → organizational data exposure → vendor coordination
- **Tests:** Vendor incident response, customer communication, business impact assessment, vendor relationships
- **Best for:** Any industry with critical vendor dependencies, procurement teams, executive leadership
- **Duration options:** 4-hour or full-day exercises

---

## Scenario Design Standards for Future Expansion

When creating new scenarios, use these criteria to consistently classify them:

### Difficulty Level Classification Rubric

**For Beginner-Intermediate:**
- ☐ Linear attack chain (phishing → compromise → impact)
- ☐ Clear initial indicators or alerts
- ☐ 3-4 decision points max, with clear options
- ☐ Information is generally available (no major "unknowns")
- ☐ Scope is relatively stable (not expanding dramatically)
- ☐ Focus on learning IR fundamentals

**For Intermediate:**
- ☐ Multi-vector or parallel attack elements
- ☐ Initial assessment is incomplete (scope expands)
- ☐ 4-6 decision points with legitimate trade-offs
- ☐ Some ambiguous information requiring investigation
- ☐ Realistic complications (backups fail, systems are slower than expected, etc.)
- ☐ Balance between technical and business concerns
- ☐ Assumes participants understand IR processes

**For Advanced:**
- ☐ Significant ambiguity throughout (many "unknowns")
- ☐ Multiple concurrent investigation threads
- ☐ Red herrings or false leads possible
- ☐ 5+ decision points with no clearly "right" answer
- ☐ Organizational/political complications alongside technical issues
- ☐ Evidence handling and forensic complexities
- ☐ Assumes participants have real-world incident experience

### Technical Weight Classification Rubric

**For Low-Tech (Business-Focused):**
- ☐ Technical details are simplified or abstracted
- ☐ Focus is on business impact, not technical mechanics
- ☐ Non-technical decision-makers (finance, HR, legal) have key roles
- ☐ Forensic or investigation details are minimal
- ☐ Participant expertise in system administration not required
- ☐ Example: "Wire transfer was sent to fraudulent account" vs. "Compromised email account via IMAP attack"

**For Moderate-Tech (Balanced):**
- ☐ Technical details are realistic but not overwhelming
- ☐ Participants need basic technical understanding (but not expertise)
- ☐ Both technical and business stakeholders have important decisions
- ☐ Some forensic/investigation process described
- ☐ Participants with different backgrounds can meaningfully participate
- ☐ Example: "Ransomware encrypted critical systems; backups are encrypted too"

**For High-Tech (Forensics-Heavy):**
- ☐ Technical details are extensive and realistic
- ☐ Specialized knowledge required (forensics, system administration, etc.)
- ☐ Technical decision-makers drive most decisions
- ☐ Investigation methodology and forensic details matter
- ☐ Threat actor tactics, techniques, and procedures are realistic
- ☐ Participants should have formal IR or security training
- ☐ Example: "Determine persistence mechanism, timeline reconstruction, artifact analysis"

### Validation Before Adding New Scenario

When proposing a new scenario, evaluate against these questions:

1. **Difficulty Level:**
   - Does the scenario fit the chosen difficulty level checklist?
   - Are decision points appropriately ambiguous for that level?
   - Is the scope expansion appropriate for the difficulty?

2. **Technical Weight:**
   - Does the technical detail match the intended audience?
   - Could a non-technical participant still engage meaningfully if it's Low-Tech?
   - Are technical specialists required if it's High-Tech?

3. **Industry Applicability:**
   - Which industries is this scenario most relevant to?
   - Can it be customized for other industries with minor changes?
   - What are industry-specific complications or regulations?

4. **Decision Points:**
   - Does the scenario have 3-6 distinct decision moments?
   - Are options realistic with legitimate pros/cons?
   - Do decisions have consequences that affect later decisions?

5. **Distinction from Existing:**
   - Is this different from existing scenarios or just a variation?
   - What unique threat vector or business impact does it test?
   - What new IR capabilities does it exercise?

---

## Customization Examples

### By Industry

**Healthcare:**
- Automatically adds HIPAA notifications, patient care impact, CMS/state health department references
- Decision point: Patient safety vs. containment procedures
- Complications: Critical care systems downtime, regulatory scrutiny

**Finance/Banking:**
- Adds PCI-DSS, SEC reporting, banking regulator considerations
- Complications: Transaction processing down, large financial impact, OFAC considerations for ransom
- Decision point: Ransom payment may violate OFAC sanctions

**Retail/E-Commerce:**
- Adds customer data breach, reputation damage, seasonal revenue impact
- Complications: Peak season (holiday) timing, customer notification costs
- Decision point: Service restoration vs. data recovery priority

**Manufacturing:**
- Adds OT/IT convergence, production disruption, supply chain impact
- Complications: Production equipment needs reset/recalibration, order fulfillment issues
- Decision point: Halt production or try partial operations

**Technology/SaaS:**
- Adds multi-tenant impact, service uptime reputation damage
- Complications: Multiple customer systems affected, service level agreement violations
- Decision point: Restore entire platform vs. subset of customers

### By Exercise Duration

**2-hour (Compressed):**
- 8-12 injects
- Detection → initial response focus
- Beginner-friendly, limited complications
- Covers: Detection, scope confirmation, initial containment decision

**4-hour (Standard):**
- 15-20 injects
- Full IR lifecycle (detect, investigate, contain, respond)
- Intermediate complexity, 2-3 complications
- Most popular for team exercises

**Full-day (Comprehensive):**
- 25-35 injects
- Deep investigation, multiple parallel decision threads
- Advanced complexity, 4+ complications
- Includes leadership briefings, regulatory coordination, media management

### By Skill Level

**Beginner:**
- Simple technical elements
- Clear information progression
- Linear scenario development
- No red herrings or surprises
- Supportive executive briefings

**Intermediate:**
- Moderate technical complexity
- Ambiguous information (some answers must be determined through investigation)
- Scope expansion surprises
- Executive pressure increases over time
- Realistic backup and recovery challenges

**Advanced:**
- Complex technical details
- Significant ambiguity and uncertainty
- Multiple parallel incident threads
- Conflicting stakeholder demands
- Realistic organizational politics and communication challenges

---

## System Components & File Interactions

This section explains what each file does, how they work together, and what happens when consultants use the TTX Generator.

### Core Component Files

| File | Purpose | Used By | When | Location |
|------|---------|---------|------|----------|
| **STARTER-PROMPT.md** | Entry point; 5 consultant questions + GitHub URLs | Every consultant | Start of workflow | Root directory |
| **inject-library.md** | 30+ reusable inject templates (Detection, Investigation, Containment, Response, Recovery phases) | LLM during generation | After parsing questions | /components/ |
| **decision-points.md** | 5 major decision frameworks (Containment, Ransom, Notification, Recovery, Communication) | LLM during generation | Customizing decisions for industry | /components/ |
| **complications.md** | Realistic obstacles & complication templates calibrated by difficulty | LLM during generation | Adding challenges & surprises | /components/ |
| **TTX-STYLE-GUIDE.md** | Formatting rules for Traditional vs. Blended vs. Gamified exercises | LLM during generation | Applying style-consistent formatting | /components/ |
| **AI-GENERATION-GUIDE.md** | Step-by-step instructions for the LLM (7 mandatory steps, quality requirements) | LLM during generation | Dictates generation rules & quality standards | /components/ |
| **ERROR-HANDLING-GUIDE.md** | Fallback options if GitHub access fails (Retry, Manual Copy, Emergency Mode) | Consultant when GitHub unavailable | Network issues, firewall blocks | /components/ |
| **TTX-QUALITY-VALIDATOR.md** | MANDATORY quality gating (3-layer validation: Critical requirements, Quality requirements, Deliverable guidance) | LLM (enforced during generation), Consultants (optional verification) | After generation, before delivery | /components/ |
| **DELIVERABLE-CREATION-GUIDE.md** | How to convert markdown to PowerPoint presentations | Consultant after generation | Post-generation publishing | /designGuides/ |

### Scenario Files

| File | Accessible via STARTER-PROMPT? | Status |
|------|------|--------|
| ransomware-scenario.md | ✅ YES | Actively used |
| business-email-compromise.md | ✅ YES | Actively used |
| data-breach-pii.md | ✅ YES | Actively used |
| insider-threat.md | ✅ YES | Actively used |
| cloud-misconfiguration.md | ✅ YES | Actively used |
| supply-chain-compromise.md | ✅ YES | Actively used |
| third-party-vendor-compromise.md | ✅ YES | Actively used |

### How Components Interact During Generation

When a consultant pastes STARTER-PROMPT and answers 5 questions:

**Step 1: Question Intake (AI-GENERATION-GUIDE Step 1)**
- LLM parses consultant's 5 answers
- Extracts: Industry, duration, participant skill, exercise objective, style preference

**Step 2: Inject Selection (AI-GENERATION-GUIDE Step 2)**
- LLM reads **inject-library.md**
- Selects injects matching duration: 8-12 for 2-hour, 15-20 for 4-hour, 25-35+ for full-day
- Customizes each for industry (healthcare adds patient care considerations, finance adds regulatory reporting, etc.)

**Step 3: Decision Point Customization (AI-GENERATION-GUIDE Step 3)**
- LLM reads **decision-points.md**
- Selects 4-5 decision frameworks from 5 available
- Customizes options A/B/C for industry context
- Adds Socratic facilitator prompts for each decision

**Step 4: Complication Selection (AI-GENERATION-GUIDE Step 4)**
- LLM reads **complications.md**
- Selects 2-3 complications appropriate to style (fewer for Traditional, more for Gamified)
- Assigns realistic triggers based on incident progression

**Step 5: Style Application (AI-GENERATION-GUIDE Step 5)**
- LLM reads **TTX-STYLE-GUIDE.md**
- Applies formatting constraints: Traditional (no rush), Blended (moderate timing), Gamified (strict)
- Enforces timing windows: Traditional 20-30 min discussions, Blended 10 min + 5 min, Gamified 3-5 min decisions
- Adjusts scoring emphasis: None for Traditional, Light for Blended, Heavy for Gamified

**Step 6: Output Generation (AI-GENERATION-GUIDE Steps 6-7)**
- LLM generates complete 25-40 page facilitator guide
- Includes all required components (see "Mandatory Output Format" below)
- Embeds 7 export markers for section extraction
- References DELIVERABLE-CREATION-GUIDE for post-generation PowerPoint conversion

### Mandatory Output Format (AI-GENERATION-GUIDE Requirement)

Every generated facilitator package MUST include:

1. **Exercise Overview** - Objectives, duration, logistics, participant roles
2. **Facilitator Preparation Checklist** - Week-before setup, materials needed, technical setup
3. **Scenario Narrative** (Wrapped in EXPORT MARKER) - Industry-customized threat description, attack timeline
4. **Inject Timeline** (Wrapped in EXPORT MARKER) - Table with 15-20 injects; each with:
   - Inject number and timing
   - Delivery method (email, phone call, alert notification, etc.)
   - Content (300-500 words with realistic formatting)
   - 4-6 Facilitator Prompts (Socratic questions)
   - 4-6 Evaluation Points (observable behaviors to watch for)
   - Expected Response (what good decisions look like)
5. **Decision Points** (Wrapped in EXPORT MARKER) - 4-5 major decisions with:
   - Situation (what just happened)
   - Options A/B/C (legitimate alternatives with pros/cons)
   - Socratic follow-up questions
   - Evaluation criteria
6. **Complications** (Wrapped in EXPORT MARKER) - 2-3 obstacles with:
   - Trigger condition (when/why it happens)
   - Description (what the complication is)
   - Impact on decisions
   - Facilitator guidance
7. **Debrief Structure** (Wrapped in EXPORT MARKER) - Post-exercise review framework
8. **Participant Materials** (Wrapped in EXPORT MARKER) - Non-spoiler welcome letter, ground rules, initial briefing
9. **Next Steps: Creating Professional Deliverables** - References DELIVERABLE-CREATION-GUIDE

All 7 export markers are MANDATORY. LLM validates own output before delivery.

---

## Technical Notes

### How It Works

1. You paste a SHORT prompt (25 lines) into an AI tool
2. The AI reads the scenario library and customizations from GitHub
3. The AI asks six clarifying questions to understand your client context:
   - Incident scenario type (required)
   - Client context (industry, size, maturity)
   - Exercise objective (what to test)
   - Duration & format (2-hour, 4-hour, 6-hour, full-day)
   - Participant profile (roles and experience)
   - Exercise style (Traditional, Blended, Gamified)
4. The AI dynamically assembles a custom exercise using:
   - Core scenario narrative matching your chosen threat type
   - Industry-specific customizations (healthcare, finance, retail, manufacturing, tech)
   - Complexity adjustments based on participant skill level and objectives
   - Inject templates and complications matched to exercise duration
   - Difficulty and technical weight calibrated to team experience
5. Output is markdown-formatted with built-in export markers for team sharing and PowerPoint conversion

### Requirements

- **Internet connection** (to access GitHub scenario library)
- **AI Tool:** ChatGPT, Claude, Gemini, or any LLM that can read URLs
- **File:** Copy of [STARTER-PROMPT.md](STARTER-PROMPT.md)

### Network Issues & Error Handling

The TTX Generator is designed to continue working even if GitHub access is temporarily unavailable.

**If AI Can't Read GitHub URLs:**

Some corporate networks block raw.githubusercontent.com. Four solution paths:

**Path 1: Retry (60-70% success rate)**
- Wait 5 minutes
- Copy STARTER-PROMPT.md again
- Paste into LLM
- Often works due to different server routing

**Path 2: Manual Copy-Paste (Full Quality, 5-10 minutes extra)**
- Manually copy files from GitHub:
  - Scenario: [ransomware-scenario.md](scenarios/ransomware-scenario.md)
  - Injects: [components/inject-library.md](components/inject-library.md)
  - Decisions: [components/decision-points.md](components/decision-points.md)
  - Complications: [components/complications.md](components/complications.md)
  - Style Guide: [components/TTX-STYLE-GUIDE.md](components/TTX-STYLE-GUIDE.md)
- Paste into AI conversation: "Use this scenario: [paste content]"
- Continue normally
- Result: 95-100% quality output, no functionality loss

**Path 3: Emergency Mode (Fast fallback, 80-85% quality)**
- Tell AI: "Generate without reference libraries, use your training knowledge"
- AI generates exercise from built-in knowledge
- Result: Professional and usable, slightly less detailed
- See [Emergency Mode Standards](#emergency-mode-standards) for quality requirements

**Path 4: Switch LLM (Recommended, 98% success rate)**
- Try ChatGPT or Claude instead
- Often has better GitHub access
- Retry conversation with different LLM

**For Corporate Networks:**
- Ask IT to whitelist: `raw.githubusercontent.com`
- Use VPN if available
- Use personal device for generation
- Use Emergency Mode (Path 3 above)

All paths produce professional, consultant-ready exercises when executed correctly.

---

## Emergency Mode Standards

If the LLM cannot access GitHub references due to network issues, quality standards DO NOT reduce. These requirements are non-negotiable even when GitHub is unavailable.

### Mandatory Requirements

**1. Inject Count (No Reduction Allowed)**
- 2-hour exercise: MINIMUM 8 injects
- 4-hour exercise: MINIMUM 15 injects
- 6-hour exercise: MINIMUM 25 injects
- Full-day exercise: MINIMUM 35 injects

**2. Every Inject Must Include All 4 Components:**
- **Content:** 300-500 words with realistic formatting (email headers, call dialogue, etc.)
- **Facilitator Prompts:** 4-6 Socratic questions (open-ended, encourage thinking)
- **Evaluation Points:** 4-6 observable criteria (checkboxes for facilitators)
- **Expected Response:** 4-6 specific actions participants should take

**3. All 7 Export Markers Required:**
Must include HTML comment markers for extraction:
- FACILITATOR-GUIDE (entire package)
- SCENARIO-NARRATIVE (participant-safe version, no spoilers)
- INJECT-TIMELINE (facilitator only)
- DECISION-POINTS (decision frameworks)
- COMPLICATIONS (complication sequence)
- DEBRIEF-TEMPLATE (post-exercise structure)
- PARTICIPANT-BRIEF (non-spoiler participant materials)

**4. Style Adherence (Consistent Throughout)**
- **Traditional:** Facilitator-paced, 20-30 min discussions, Socratic focus, no scoring
- **Blended:** Light scoring, 10-15 min windows, balanced discussion
- **Gamified:** Strict timing, heavy scoring, compressed discussions, surprise elements

**5. Zero Placeholder Text**
- No "TBD", "TODO", "Add...", "[TBD]", "[Add", "Lorem Ipsum", "TBA"
- All facilitator prompts are complete questions/statements
- All sections are fully written

**6. Quality Target: 85-100% of Reference Quality**
- Use extensive TTX facilitation knowledge from training
- Emergency Mode means "use training data" not "reduce quality"
- Output should be professional and immediately usable

### Pre-Delivery Validation Checklist

Before finalizing Emergency Mode output:

- ☐ Section count: All 8+ major sections present
- ☐ Inject count: Minimum met for duration (count them explicitly!)
- ☐ Export markers: All 7 pairs present and correctly formatted
- ☐ Decision points: 4-5 with complete frameworks and options
- ☐ Tables: Properly formatted and readable throughout
- ☐ Facilitator prompts: Present for every inject (4-6 per inject)
- ☐ Evaluation criteria: Present for every inject and decision
- ☐ Page estimate: 25-35 pages minimum for 4-hour exercise

**Bottom Line:** A consultant receiving Emergency Mode output should NOT be able to tell that GitHub was unavailable. The output must be complete, professional, and ready to use immediately with no additional cleanup needed.

---

## Questions or Feedback?

- **GitHub Issues:** Report bugs or suggest improvements
- **GitHub Discussions:** Share experiences using the TTX Generator
- **Contributions:** Have a better scenario or complication? Submit a PR

---

## Resources

- **Starter Prompt:** [STARTER-PROMPT.md](STARTER-PROMPT.md) - Copy this to get started
- **Detailed Scenarios:** [scenarios/](scenarios/) directory contains complete threat narratives, decision frameworks, and technical details
- **Component Libraries:**
  - [components/inject-library.md](components/inject-library.md) - Inject templates by phase
  - [components/decision-points.md](components/decision-points.md) - Decision frameworks and options
  - [components/complications.md](components/complications.md) - Difficulty modifiers
  - [components/TTX-STYLE-GUIDE.md](components/TTX-STYLE-GUIDE.md) - Traditional/Blended/Gamified guidance
- **AI Generation Guide:** [designGuides/AI-GENERATION-GUIDE.md](designGuides/AI-GENERATION-GUIDE.md) - How the AI creates customized exercises
- **Deliverable Creation Guide:** [designGuides/DELIVERABLE-CREATION-GUIDE.md](designGuides/DELIVERABLE-CREATION-GUIDE.md) - Converting markdown to PowerPoint and professional documents
- **Advanced Approach:** See `defensive/IRTabletopExercisePlanning(ThreeStaged).md` for three-stage detailed planning (alternative method with 50+ customization fields)
- **Book Reference:** [*Prompt Intelligence: An AI Framework for Security Professionals*](https://focusedhunts.com) - Principles and techniques underlying this prompt

---

## Key Features

- **Six-Question Customization:** Answer simple questions about your client (scenario type, context, objectives, duration, participants, style), get a tailored exercise
- **Scenario Selection:** Choose from multiple incident scenarios (Ransomware, BEC, Data Breach, Insider Threat) matched to your client's risk profile
- **Difficulty & Technical Weight Classification:** Scenarios labeled by difficulty level (Beginner-Intermediate, Intermediate, Advanced) and technical focus (Low-Tech, Moderate-Tech, High-Tech)
- **Three Exercise Styles:** Traditional (discussion), Blended (balanced), Gamified (high-intensity)
- **Industry-Specific Customization:** Healthcare (HIPAA), Finance (PCI-DSS), Retail, Manufacturing, Technology
- **Export & Sharing:** Built-in export markers for easy team sharing and markdown extraction
- **PowerPoint Creation:** Comprehensive guidance for transforming markdown into professional presentations
- **Professional Quality:** Facilitator-ready materials suitable for client delivery
- **Built-in Error Handling:** Works offline with emergency mode and manual backup options

---

**Remember:** This tool generates exercise *plans*, not exercises themselves. You (the consultant) facilitate the exercise with participants. The TTX Generator helps you create it faster, but your facilitation expertise is essential for success; managing the room, guiding discussions, and helping participants learn from the experience.
