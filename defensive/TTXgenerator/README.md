# TTX Generator - Conversational Tabletop Exercise Creator

**Create customized incident response tabletop exercises in 20-30 minutes using AI.**

This tool lets you generate professional exercise facilitator packages by having a natural conversation with ChatGPT, Claude, or any LLM—no copy-pasting dozens of fields or manually assembling components.

---

## What is This?

The TTX Generator is a **conversational prompt** that works with any AI language model to create incident response tabletop exercises (TTX) tailored to your client's specific context.

**Instead of:**
- Spending 2-4 hours manually creating exercises
- Copy-pasting and editing scenario templates
- Trying to remember all the details you need to customize

**You:**
- Copy a 15-line prompt
- Paste it into ChatGPT/Claude
- Answer 5 simple questions
- Get a complete facilitator package with customized scenario, injects, decision points, and guidance

**Result:** A professional-ready exercise outline or full facilitator package that consultants would actually use.

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
- **Pace:** Fast-paced (injects arrive on schedule)
- **Focus:** Testing decision speed and response effectiveness

Example: SOC team doing quarterly IR challenge—want real-world pressure and scoring

**One scenario, three presentation styles.** Tell us your style preference when you answer the questions, and we'll customize the exercise accordingly.

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

## What Scenarios Are Available Now?

**Current:** Ransomware Attack (Intermediate difficulty)
- Phishing → credential compromise → ransomware deployment and extortion
- Tests: Forensics, containment, business continuity, executive communication, legal coordination
- Best for: All industries (healthcare, finance, retail, manufacturing, technology)
- Duration options: 2-hour, 4-hour, or full-day exercises

**Coming Soon:** (After Ransomware MVP is validated)
- Insider Threat - Malicious (Advanced)
- Data Breach - Customer PII Exfiltration (Intermediate)
- Business Email Compromise (Beginner-Intermediate)
- DDoS / Availability Attack (Beginner-Intermediate)
- Cloud Misconfiguration (Intermediate)
- Supply Chain Compromise (Advanced)
- Third-Party Vendor Compromise (Advanced)

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
2. The AI reads the ransomware scenario from GitHub (via raw.githubusercontent.com URL)
3. The AI asks clarifying questions to understand your client context
4. The AI dynamically assembles a custom exercise using:
   - Core scenario narrative
   - Industry-specific customizations (healthcare, finance, etc.)
   - Complexity adjustments based on skill level
   - Inject templates matched to exercise duration
5. Output is markdown-formatted and ready to use

### Requirements

- **Internet connection** (to access GitHub scenario library)
- **AI Tool:** ChatGPT, Claude, Gemini, or any LLM that can read URLs
- **File:** Copy of [STARTER-PROMPT.md](STARTER-PROMPT.md)

### If AI Can't Read GitHub URLs

Some corporate networks block raw.githubusercontent.com. If that happens:

**Option 1:** Use a personal account outside your corporate network

**Option 2:** Manual Copy-Paste
- Open [ransomware-scenario.md](ransomware-scenario.md) in your browser
- Copy the scenario content
- Paste into the AI conversation with: "Use this scenario: [paste]"
- Continue the conversation normally

---

## Philosophy: Start Small, Prove Value, Expand

This MVP includes **one scenario** (Ransomware) to prove the concept works. If consultants find this approach valuable:

**Phase 2:** Component libraries (reusable injects, decision points, complications by industry)

**Phase 3:** Additional scenarios (insider threat, data breach, DDoS, etc.)

**Phase 4:** Industry customizations (more detailed healthcare, finance, retail specializations)

**Phase 5:** Output options (PowerPoint generation, PDF reports, etc.)

But we expand only if this MVP proves useful. Quality > Quantity.

---

## Comparison: Old vs. New Approach

### Old Approach (IRTabletopExercisePlanning - Three-Staged)
- Detailed form with 50+ customization fields [MODIFY: ...]
- Three stages of manual editing and assembly
- 2-4 hours to complete
- "Copy-paste" oriented
- Requires reading through extensive instructions

### New Approach (TTX Generator - Conversational)
- Simple 15-line starter prompt
- Natural conversation (5 questions)
- 20-30 minutes to complete
- "Paste and chat" oriented
- Requires minimal setup

**Both approaches** reference the same detailed scenario library and customization guidance. The new approach just makes it faster and more conversational.

---

## Questions or Feedback?

- **GitHub Issues:** Report bugs or suggest improvements
- **GitHub Discussions:** Share experiences using the TTX Generator
- **Contributions:** Have a better scenario or complication? Submit a PR

---

## Resources

- **Detailed Scenario:** [ransomware-scenario.md](ransomware-scenario.md) - Complete scenario with all decision points, injects, customizations
- **Advanced Approach:** See `defensive/IRTabletopExercisePlanning(ThreeStaged).md` for detailed three-stage prompt with extensive customization options
- **Book Reference:** [*Prompt Intelligence: An AI Framework for Security Professionals*](https://focusedhunts.com) - Principles and techniques underlying this prompt
- **Original Scenario Library:** See `defensive/IRTabletop-ScenarioLibrary.md`

---

**Remember:** This tool generates exercise *plans*, not exercises themselves. You (the consultant) execute the exercise with participants. The AI helps you build it faster, but your expertise is essential in facilitating the event, managing the room, and helping participants learn.
