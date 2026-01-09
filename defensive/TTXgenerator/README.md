# TTX Generator - Conversational Tabletop Exercise Creator

**Create customized incident response tabletop exercises in 20-30 minutes using AI.**

This tool lets you generate professional exercise facilitator packages by having a natural conversation with ChatGPT, Claude, or any LLM. Answer five simple questions, and get a complete customized exercise ready for delivery.

---

**Remember:** This tool generates exercise *plans*, not exercises themselves. You (the consultant) facilitate the exercise with participants. The TTX Generator helps you create it faster, but your facilitation expertise is essential for success; managing the room, guiding discussions, and helping participants learn from the experience.

---

## What is This?

The TTX Generator is a **conversational prompt** that works with any AI language model to create incident response tabletop exercises (TTX) tailored to your client's specific context.

Copy a short prompt, paste into your preferred AI tool, answer five questions about your client, and receive a complete facilitator package in 20-30 minutes. The package includes customized scenario narrative, inject timeline with delivery guidance, key decision points, facilitator notes, and participant materials.

---

## How to Use This

### Step 1: Copy the Starter Prompt (30 seconds)

Open [STARTER-PROMPT.md](STARTER-PROMPT.md) and copy the entire prompt.

### Step 2: Paste into Your Preferred LLM (10 seconds)

- Open ChatGPT, Claude, or your preferred AI tool
- Paste the prompt
- Start the conversation

### Step 3: Answer 5 Simple Questions (5-10 minutes)

The AI will ask you:

1. **"Tell me about your client in 2-3 sentences."**
   - Answer: Brief description (industry, org size, IR maturity)
   - Example: "250-bed hospital system, moderate IR maturity, had ransomware near-miss last quarter"

2. **"What's your primary exercise objective?"**
   - Answer: What capability do you want to test? (IR plan validation, communication, decision-making, regulatory compliance, etc.)
   - Example: "Test IR plan effectiveness, especially cross-functional communication under pressure"

3. **"How long is the exercise?"**
   - Answer: 2-hour, 4-hour, or full-day format
   - Example: "4 hours, virtual format"

4. **"What skill level are participants?"**
   - Answer: Beginner, intermediate, advanced, or mixed
   - Example: "Mixed—SOC team is intermediate, executives are non-technical"

5. **"What detail level do you need?"**
   - Answer: Outline (5-10 page overview), Storyboard (15-25 pages with full narrative), or Full Package (40-60 pages with all facilitator materials)
   - Example: "Full facilitator package with inject timeline and participant materials"

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

**Total time: 20-30 minutes** (vs. 2-4 hours manual creation)

---

## Example Conversation Flow

```
You: [Paste STARTER-PROMPT.md]

AI: "Let's get started. Please tell me about your client in 2-3 sentences:"

You: "Healthcare organization, 300-bed hospital system in the Midwest.
     Moderate IR maturity—they have a plan but limited incident response
     team experience. Had a ransomware near-miss last quarter that spooked the board."

AI: "Great context. What's your primary exercise objective?"

You: "Test their IR plan effectiveness, especially communication and decision-making
     under pressure. Want to see how well IT, security, and executive leadership
     can coordinate during a real-time crisis."

AI: "Understood. How long is the exercise?"

You: "4 hours, virtual format. About 25-30 people participating across multiple breakout rooms."

AI: "What skill level are the participants?"

You: "Mixed. IT ops and security team are intermediate. Executives (C-suite, board)
     are non-technical but engaged. No previous TTX experience."

AI: "What detail level do you need?"

You: "Full facilitator package. We want everything—scenario, injects with timing,
     decision points, facilitator guidance, and materials for participants."

AI: "Perfect. Let me generate that for you. I'm reading the ransomware scenario,
     applying healthcare-specific customizations (HIPAA, patient care impact),
     and creating a 4-hour exercise with 18-20 injects and decision points...

     [Generates complete facilitator package]
```

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

### Scenario Matrix

| Scenario | Difficulty | Technical Weight | Best For | Duration |
|----------|-----------|-----------------|----------|----------|
| **Business Email Compromise** | Beginner-Intermediate | Low-Tech | All industries, mixed teams | 2-4 hour |
| **Ransomware Attack** | Intermediate | Moderate-Tech | All industries, full IR lifecycle | 2-4 hour, full-day |
| **Data Breach - Customer PII** | Intermediate | Moderate-Tech | Customer-facing businesses, compliance focus | 4-hour, full-day |
| **Insider Threat - Malicious** | Advanced | High-Tech | Technical teams, forensics focus | 4-hour, full-day |
| **DDoS / Availability Attack** | Beginner-Intermediate | Moderate-Tech | Technology/SaaS, availability focus | 2-4 hour |
| **Cloud Misconfiguration** | Intermediate | Moderate-Tech | Cloud-native businesses, DevOps teams | 2-4 hour |
| **Supply Chain Compromise** | Advanced | High-Tech | Technology vendors, procurement teams | Full-day |
| **Third-Party Vendor Compromise** | Advanced | Moderate-Tech | Any industry, vendor risk management | 4-hour, full-day |

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

### Current Available Scenarios

**Ransomware Attack** (Intermediate, Moderate-Tech)
- Phishing → credential compromise → ransomware deployment and extortion
- Tests: Forensics, containment, business continuity, executive communication, legal coordination
- Best for: All industries (healthcare, finance, retail, manufacturing, technology)
- Duration options: 2-hour, 4-hour, or full-day exercises

**Additional Scenarios**
- Insider Threat - Malicious (Advanced, High-Tech)
- Data Breach - Customer PII Exfiltration (Intermediate, Moderate-Tech)
- Business Email Compromise (Beginner-Intermediate, Low-Tech)
- DDoS / Availability Attack (Beginner-Intermediate, Moderate-Tech)
- Cloud Misconfiguration (Intermediate, Moderate-Tech)
- Supply Chain Compromise (Advanced, High-Tech)
- Third-Party Vendor Compromise (Advanced, Moderate-Tech)

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

## Technical Notes

### How It Works

1. You paste a SHORT prompt (15 lines) into an AI tool
2. The AI reads the scenario library and customizations from GitHub
3. The AI asks five clarifying questions to understand your client context
4. The AI dynamically assembles a custom exercise using:
   - Core scenario narrative matching your chosen threat type
   - Industry-specific customizations (healthcare, finance, retail, manufacturing, tech)
   - Complexity adjustments based on participant skill level and objectives
   - Inject templates and complications matched to exercise duration
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

- **Five-Question Customization:** Answer simple questions about your client, get a tailored exercise
- **Multiple Output Formats:** Outline (5-10 pages), Storyboard (15-25 pages), or Full Facilitator Package (40-60 pages)
- **Three Exercise Styles:** Traditional (discussion), Blended (balanced), Gamified (high-intensity)
- **Industry-Specific Customization:** Healthcare (HIPAA), Finance (PCI-DSS), Retail, Manufacturing, Technology
- **Export & Sharing:** Built-in export markers for easy team sharing and markdown extraction
- **PowerPoint Creation:** Comprehensive guidance for transforming markdown into professional presentations
- **Professional Quality:** Facilitator-ready materials suitable for client delivery
- **Built-in Error Handling:** Works offline with emergency mode and manual backup options

---

**Remember:** This tool generates exercise *plans*, not exercises themselves. You (the consultant) facilitate the exercise with participants. The TTX Generator helps you create it faster, but your facilitation expertise is essential for success; managing the room, guiding discussions, and helping participants learn from the experience.
