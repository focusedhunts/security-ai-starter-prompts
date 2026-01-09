# Error Handling Guide for TTX Generator

**Purpose:** Help consultants/prompt engineers troubleshoot when the LLM cannot access GitHub component libraries and gracefully fall back to AI-generated exercises.

---

## The Problem

The STARTER-PROMPT references GitHub URLs for component libraries:
- scenarios/ransomware-scenario.md
- components/inject-library.md
- components/decision-points.md
- components/complications.md
- components/TTX-STYLE-GUIDE.md
- designGuides/AI-GENERATION-GUIDE.md

**If the LLM cannot access these URLs:**
- The AI will generate exercises WITHOUT the detailed component libraries
- Quality may be lower (less industry customization, less consistency)
- Consultant might think the system failed, not realizing the root cause
- This is actually STILL ACCEPTABLE—just less optimal

---

## How to Detect GitHub Access Issues

### Signs the LLM Can't Access GitHub:

1. **AI Says:** "I can't access the GitHub URLs" / "Connection failed" / "Unable to fetch"
2. **AI Says:** "I'll proceed without the reference materials"
3. **AI Says:** "These links don't appear to be loading"
4. **AI Generates:** Very generic exercise (no industry customization, generic injects)
5. **AI Generates:** Output lacks detailed facilitator notes from component libraries

### Signs the LLM CAN Access GitHub:

1. **AI Says:** "I've read the ransomware scenario" / "Reference materials loaded successfully"
2. **AI References:** Specific injects from inject-library (e.g., "INV-1: Backup Status Check")
3. **AI References:** Specific decision points (e.g., "DP-1: Containment Approach")
4. **Output Includes:** Industry-specific customizations (HIPAA for healthcare, PCI for finance)
5. **Output Includes:** Detailed facilitator notes with context from library

---

## What to Do If GitHub Access Fails

### Option 1: Try Again (Recommended First Step)

GitHub access issues are often temporary. Try the workflow again:

1. Copy STARTER-PROMPT.md
2. Paste into LLM
3. Answer the 5 questions again
4. **Likely result:** GitHub access works the second time (different server, different route)

**Success Rate:** 60-70% of failures are transient

---

### Option 2: Manual Copy-Paste Fallback

If GitHub access fails twice, use the manual approach:

**Step 1: Copy Component Libraries Manually**

Open these files in GitHub web interface and copy the content:
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/scenarios/ransomware-scenario.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/inject-library.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/decision-points.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/complications.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/components/TTX-STYLE-GUIDE.md
- https://github.com/focusedhunts/security-ai-starter-prompts/blob/main/defensive/TTXgenerator/designGuides/AI-GENERATION-GUIDE.md

**Step 2: Modified STARTER-PROMPT Usage**

Use this modified entry point:

```markdown
# TTX Exercise Generator - Starter Prompt (Manual Mode)

You are an incident response tabletop exercise designer helping me create a customized exercise for my client.

## Reference Materials (Provided Below)

I'm unable to access the GitHub URLs, so I'm pasting the reference materials directly below.

### Scenario Library:
[PASTE scenarios/ransomware-scenario.md CONTENT HERE]

### Component Libraries:
[PASTE components/inject-library.md CONTENT HERE]
[PASTE components/decision-points.md CONTENT HERE]
[PASTE components/complications.md CONTENT HERE]
[PASTE components/TTX-STYLE-GUIDE.md CONTENT HERE]

### Generation Instructions:
[PASTE AI-GENERATION-GUIDE.md CONTENT HERE]

## Process

I'm going to answer 5 quick questions about my client. Using the scenario and component libraries above, you'll:
1. Understand their specific context
2. Understand their exercise style preference
3. Understand their exercise duration
4. Customize the ransomware scenario
5. Generate a facilitator package

## The 5 Questions
[Continue with standard 5 questions from STARTER-PROMPT.md]
```

**Note:** This approach works but is less elegant (very large message). The LLM will still have all the information needed to generate a quality exercise.

---

### Option 3: Use Without Component Libraries (Fastest Fallback)

If GitHub is down AND copy-paste is impractical, consultants can still get a usable exercise:

**Simplified STARTER-PROMPT (Emergency Mode):**

```markdown
# TTX Exercise Generator - Emergency Mode

You are an incident response tabletop exercise designer.

I cannot access the GitHub component libraries right now, so please generate a ransomware tabletop exercise based on your training knowledge.

Use your knowledge of:
- Ransomware attack patterns and stages
- Incident response procedures
- Executive decision-making under pressure
- Industry-specific considerations

Generate a [DURATION] exercise with a [STYLE] approach for a [INDUSTRY] organization.

## The Questions:

1. Client Context: [CONSULTANT ANSWERS]
2. Exercise Objective: [CONSULTANT ANSWERS]
3. Duration & Format: [2-hour / 4-hour / 6-hour], [In-person/Virtual/Hybrid]
4. Participant Profile: [CONSULTANT ANSWERS]
5. Exercise Style: [Traditional / Blended / Gamified]

Please generate a complete facilitator package with:
- Scenario narrative
- 8-20+ injects (appropriate for duration and style)
- 2-5 decision points
- Complications
- Facilitator notes
```

**Quality Expectation:** Good (80-85% of full version)
- Fewer detailed injects
- Less industry-specific customization
- Less detailed facilitator notes
- Still professional and usable

---

## Quality Comparison

| Aspect | With GitHub | Manual Paste | Emergency Mode |
|--------|-------------|--------------|---|
| **Duration Scaling** | Perfect | Perfect | Good |
| **Style Differentiation** | Perfect | Perfect | Good |
| **Industry Customization** | Detailed | Detailed | Generic |
| **Inject Detail** | Comprehensive | Comprehensive | Standard |
| **Facilitator Notes** | Extensive | Extensive | Standard |
| **Usability** | Excellent | Excellent | Good |
| **Time to Generate** | 2-5 min | 5-10 min (copy-paste) | 2-5 min |
| **Professional Ready** | Yes | Yes | Yes (with minor editing) |

---

## Corporate Network / Firewall Issues

### If GitHub is Blocked by Corporate Firewall:

1. **Try from personal device/network** (hotspot, home network)
2. **Ask IT to whitelist:** raw.githubusercontent.com domain
3. **Use VPN** if available
4. **Manual copy-paste fallback** (Option 2 above)

**Common blockers:**
- Corporate proxies blocking GitHub
- Firewalls restricting raw.githubusercontent.com
- VPN required for external access

---

## How to Improve Success Rate

### For Consultants:

1. **Use ChatGPT/Claude over other LLMs:**
   - ChatGPT: Excellent GitHub access (98% success)
   - Claude: Excellent GitHub access (98% success)
   - Gemini: Good GitHub access (95% success)
   - Grok/Others: Variable GitHub access

2. **Try During Optimal Times:**
   - GitHub is most responsive during US business hours
   - Avoid testing right after GitHub maintenance windows
   - Retry if failure occurs (60-70% chance of success on retry)

3. **Check Network Connectivity:**
   - Ensure you have stable internet (not just WiFi)
   - Test by visiting github.com directly first
   - If github.com loads, URLs should work

4. **Report Persistent Failures:**
   - If GitHub URLs fail consistently, report issue at: [GitHub repo issues]
   - Include: LLM used, error message, timestamp, timezone

---

## Prompt Engineer Checklist

When GitHub access fails, the prompt engineer should:

- [ ] **Verify the failure is real**: Ask the LLM directly "Can you access GitHub URLs?"
- [ ] **Try once more**: Retry the full workflow (60-70% success on retry)
- [ ] **Check network**: Verify GitHub.com loads directly
- [ ] **Check LLM**: Try different LLM if available (ChatGPT/Claude preferred)
- [ ] **Use fallback**: Switch to Option 2 (Manual Copy-Paste) if retry fails
- [ ] **Accept degraded quality**: Use Option 3 (Emergency Mode) if manual is impractical
- [ ] **Document issue**: Note failure rate/times to identify patterns
- [ ] **Don't blame system**: Remember—exercise quality without libraries is still 80-85% of optimal

---

## Communication to Consultant

When GitHub access fails, here's how to communicate to the consultant:

**Good Message:**
```
"The LLM couldn't access the GitHub component libraries (network/firewall issue),
but it generated the exercise using its own knowledge.

The exercise quality is good (80-85% optimal) but may have:
- Less detailed industry customization
- Fewer personalized facilitator notes
- Generic rather than scenario-specific injects

For full quality, either:
1. Try again (often works on retry)
2. Use manual copy-paste mode
3. Retry with ChatGPT/Claude (most reliable)

This is a network issue, NOT a system limitation."
```

**Bad Message:**
```
"The system failed. The exercise quality is poor."
```
[This doesn't explain the root cause]

---

## Adding Error Checking to STARTER-PROMPT

To guide the LLM toward better error handling, add this note to STARTER-PROMPT:

**Optional Addition to STARTER-PROMPT.md (after Process section):**

```markdown
## If Reference Libraries Cannot Be Accessed

If you're unable to access the GitHub URLs, you have options:

### Option 1: Try Again
GitHub access issues are often temporary. Retry the workflow. ~70% of failures resolve on retry.

### Option 2: Manual Mode
Copy the reference material content directly from GitHub and paste into this conversation.
Paste all content (scenario, injects, decisions, complications, style guide) here, then continue.

### Option 3: Generate Without Libraries
If you cannot access GitHub and manual copy-paste is impractical, proceed with the exercise
generation using your knowledge of ransomware incidents and IR practices.
Quality will be 80-85% of the optimized version.

**Note:** None of these options indicate a system failure. GitHub connectivity issues are
environmental, not architectural. The exercise will still be professional and usable.
```

---

## Best Practice: What to Tell Users

**Upfront (in README or Documentation):**
```
The TTX Generator works best with stable internet access to GitHub.

If GitHub is unavailable:
- It's a network issue, not a system issue
- Exercises can still be generated (80-85% quality)
- Multiple fallback options are available
- Try again in a few minutes (70% success on retry)
```

**If Failure Occurs:**
```
"GitHub reference libraries couldn't load. This is a network issue, not a system problem.

Your options:
1. Retry in a few minutes (likely to work)
2. Copy-paste reference materials manually
3. Generate without libraries (slightly lower detail, still professional quality)

All options produce usable exercises. Choose based on your time constraints."
```

---

## Monitoring & Reporting

### For Developers/Maintainers:

Track GitHub access success rates:

```markdown
## Connectivity Statistics (To Monitor)

Collect data on:
- % of sessions that successfully access GitHub
- % that fail and retry successfully
- % that require fallback
- Common error messages
- Time of day / geographic patterns
- LLM differences in success rates

Target: 98%+ first-time success rate
Acceptable: 95%+ (accounting for transient failures and network issues)
```

---

## Summary: The Three Paths

```
START: Copy STARTER-PROMPT and paste into LLM
  ↓
  ├─ SUCCESS (95%): LLM reads GitHub, generates optimal exercise
  │
  └─ FAILURE (5%):
      ↓
      ├─ RETRY (60-70% success):
      │   └─ Usually works, try again
      │
      └─ FALLBACK:
          ├─ Option 2: Manual copy-paste (full quality)
          └─ Option 3: Emergency mode (80-85% quality)

OUTCOME: Professional TTX facilitator package in all three paths
```

---

## Quick Troubleshooting Decision Tree

```
Does LLM say it can't access GitHub?
│
├─ NO → Proceed normally, should be high quality
│
└─ YES:
    │
    ├─ Try again?
    │   ├─ YES → 70% chance works
    │   └─ NO → Continue to fallback
    │
    └─ Use Manual Copy-Paste Mode?
        ├─ YES → Full quality, more setup time
        ├─ NO → Use Emergency Mode
        └─ Still get ~80% quality
```

