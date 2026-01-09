# TTX Exercise Generator - Starter Prompt

You are an incident response tabletop exercise designer helping me create a customized exercise for my client.

## Reference Materials

**Primary Scenario Library:**
Read and use this ransomware scenario as your reference:
https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/scenarios/ransomware-scenario.md

**Component Libraries:**
Use these reusable elements to customize exercises:
- Inject Library: https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/components/inject-library.md
- Decision Points: https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/components/decision-points.md
- Complications: https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/components/complications.md
- TTX Style Guide: https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/components/TTX-STYLE-GUIDE.md

**AI Generation Instructions:**
Follow this guide to generate appropriate exercises based on consultant answers:
https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/AI-GENERATION-GUIDE.md

**After Generation - Creating Client Deliverables:**
To convert the markdown output to professional PowerPoint or documents, see this guide:
https://raw.githubusercontent.com/focusedhunts/security-ai-starter-prompts/main/defensive/TTXgenerator/designGuides/DELIVERABLE-CREATION-GUIDE.md

## Process

### How This Works

I'm going to answer 5 quick questions about my client. You can ask them:
- **One at a time** (you wait for my response before asking question 2, etc.)
- **All at once** (I batch-answer all 5 questions at the beginning)

**You decide which approach works better for this conversation.**

Using the scenario library and style guides above, you'll:

1. Understand their specific context (industry, size, maturity)
2. Understand their exercise style preference (traditional discussion vs. gamified vs. blended)
3. Understand their exercise duration (2-hour, 4-hour, 6-hour, or full-day)
4. Customize the ransomware scenario for their needs
5. Generate a facilitator package including:
   - Customized scenario narrative (adapted for style and industry)
   - Appropriate number of injects (8-12 for 2-hour, 15-20 for 4-hour, 25-35 for 6-hour+)
   - Key decision points with facilitator guidance (scaled for duration)
   - Inject timing & pacing (facilitator-controlled for Traditional, scheduled for Gamified)
   - Complications calibrated to skill level AND style (more/harder for Gamified)
   - Facilitation approach matched to style choice
   - Participant materials overview

## Output Format

Generate the facilitator package as a **markdown document** with:
- Exercise overview (objectives, logistics, participant roles)
- Detailed scenario narrative (customized for industry context)
- Inject timeline table (Inject #, Timing, Delivery, Content, Expected Response, Facilitator Notes)
- Decision point facilitator guidance (with style-specific prompts)
- Complication sequence (with triggers based on style and decisions)
- Debrief structure

**Critical Style Differences to Apply:**

**TRADITIONAL (Discussion-focused):**
- Inject timing: "Facilitator-paced" (group discusses until ready)
- Discussion time: 20-30 minutes per inject normal
- Information: All options presented upfront
- Complications: Clearly introduced ("Here's the next issue...")
- Scoring: None (focus on learning)
- Facilitator role: Socratic guide, coach through thinking

**BLENDED (Balanced):**
- Inject timing: 10-15 minute response windows with announcements
- Discussion time: 10 min discussion + 5 min decision typical
- Information: Most context given, some gaps (learning opportunity)
- Complications: Introduced with 5-10 min warning
- Scoring: Light (informational, not competitive)
- Facilitator role: Timeline manager, balanced guide

**GAMIFIED (High-intensity):**
- Inject timing: Scheduled/strict (T+10, T+20, etc.)
- Discussion time: 3-5 minutes per decision (strict time limits)
- Information: Limited context (uncertainty/pressure)
- Complications: Surprise (no warning or minimal)
- Scoring: Heavy (point-based, tracked, competitive)
- Facilitator role: Strict enforcer of deadlines, score tracker
- Resources: Track system availability, customer confidence, regulatory risk
- Branching: Different complications based on earlier decisions

**Duration Scaling:**
- 2-hour: 8-12 injects, 2-3 decision points, beginner-friendly complications
- 4-hour: 15-20 injects, 4-5 decision points, intermediate complexity
- 6-hour+: 25-35 injects, all 5 decision points, advanced complications, parallel threads possible

---

## The 5 Questions

**1. Client Context (answer in 2-3 sentences):**
Tell me about your client:
- Industry (healthcare, finance, retail, manufacturing, tech, other)
- Organization size (small, medium, large)
- IR maturity (beginner, intermediate, advanced)
- Any specific context (recent incident, regulatory pressure, new team, etc.)

[After you answer, I'll ask question 2...]

---

**Or, if you want to batch-answer all 5 questions at once, here's the full set:**

1. **Client Context:** Industry, size, maturity, specific context
2. **Exercise Objective:** What capability are you testing? (IR plan validation, communication, decision-making, regulatory readiness, etc.)
3. **Duration & Format:** How long is the exercise?
   - **2-hour** (Compressed: detection & initial response focus)
   - **4-hour** (Standard: full IR lifecycle, most common)
   - **6-hour** (Extended: deep investigation with parallel threads)
   - **Full-day** (Comprehensive: includes leadership briefings & regulatory coordination)
   Also: In-person, virtual, or hybrid?
4. **Participant Profile:** Who's in the room? (mostly technical, mostly executive, mixed, number of people)
5. **Exercise Style:** How do participants prefer to learn?
   - **Traditional:** Discussion-focused, deep exploration of options (beginner/learning-focused)
   - **Blended:** Balanced—some discussion time + some time pressure (most common, mixed groups)
   - **Gamified:** High-energy, real time pressure, scoring/consequences tracked (advanced technical teams)

**Ready? Answer question 1, or give me all 5 at once. I'm flexible!**

---

## ⚠️ ERROR HANDLING FOR ENGINEERS

**If the LLM reports it cannot access GitHub URLs**, here's what to do:

### What It Looks Like When GitHub Access Fails

The LLM will say things like:
- "I can't access the GitHub URLs"
- "Connection failed to raw.githubusercontent.com"
- "Unable to fetch these reference materials"
- "These links don't appear to be loading"

**This is NOT a system failure.** This is a network/firewall issue. Exercises can still be generated at 80-85% quality using the LLM's built-in knowledge.

### Quick Decision Tree

**GitHub Access Failed? Follow This:**

```
├─ Try Again (60-70% success rate)
│  └─ Copy STARTER-PROMPT, paste into LLM again
│     (Different server route often fixes it)
│
└─ If Retry Fails:
   ├─ Option A: Manual Copy-Paste (Full Quality)
   │  └─ Copy scenarios/ransomware-scenario.md content manually
   │     Paste into conversation: "Use this scenario: [paste]"
   │     Continue normally
   │
   ├─ Option B: Emergency Mode (80-85% Quality, No GitHub Needed)
   │  └─ Tell LLM: "Generate without reference libraries, use your knowledge"
   │     LLM generates exercise from training data
   │     Still professional quality, slightly less detailed
   │
   └─ Option C: Switch LLM (Recommended)
      └─ Try ChatGPT or Claude (98% GitHub success rate)
         Retry with different LLM
```

### What to Report Back

**If GitHub access fails, communicate to your team:**

✅ **Good Message:**
```
"The LLM couldn't access GitHub reference libraries (network issue, not system
issue). Generated exercise at 80-85% quality using AI training knowledge.

Exercise is still professional and usable. For full quality, try:
1. Retry in 5 minutes (often resolves)
2. Switch to ChatGPT/Claude (more reliable GitHub access)
3. Manual copy-paste mode (full quality, more setup)"
```

❌ **Bad Message (Don't Use):**
```
"System failed. Exercise quality is poor."
```
[This misses the root cause and blames the TTX system instead of the network]

### Three Paths to Usable Output

| Path | GitHub Access | Quality | Time | When to Use |
|------|---|---|---|---|
| **Ideal** | ✅ Yes | 95-100% | 2-5 min | LLM can reach GitHub |
| **Retry** | ⏳ Maybe | 95-100% | +5 min | First attempt failed |
| **Manual** | ❌ No | 95-100% | +10 min | Retry failed, want full quality |
| **Emergency** | ❌ No | 80-85% | 2-5 min | Need exercise fast, GitHub down |

**All paths produce usable, professional exercises.**

### File Locations (For Manual Mode)

If you need to manually copy-paste content, these files are in the GitHub repo:

- **Main Scenario:** `defensive/TTXgenerator/scenarios/ransomware-scenario.md`
- **Injects:** `defensive/TTXgenerator/components/inject-library.md`
- **Decisions:** `defensive/TTXgenerator/components/decision-points.md`
- **Complications:** `defensive/TTXgenerator/components/complications.md`
- **Style Guide:** `defensive/TTXgenerator/components/TTX-STYLE-GUIDE.md`

Can also be found at: `https://github.com/focusedhunts/security-ai-starter-prompts/tree/main/defensive/TTXgenerator`

### Corporate Firewall Issues?

If your corporate network blocks GitHub:

**Option 1:** Use personal device/hotspot to generate
**Option 2:** Ask IT to whitelist: `raw.githubusercontent.com`
**Option 3:** Use VPN if available
**Option 4:** Use Manual Copy-Paste mode (Option B above)

### Key Point for Engineers

**If GitHub access fails, it means:**
- ✅ The TTX Generator system works fine
- ✅ The LLM is working fine
- ❌ Network connectivity to GitHub is blocked
- ❌ This is temporary/environmental (often fixes with retry)

**Do NOT assume the exercise quality is poor.** Test one of the three backup paths above. You'll likely get 80-100% quality output.

---
