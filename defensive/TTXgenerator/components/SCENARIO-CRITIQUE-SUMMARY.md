# Scenario Critique Summary - Quick Reference

**Prepared:** 2026-01-09
**Format:** Executive Summary + Quick Metrics
**Full Analysis:** See SCENARIO-STRATEGY-REVIEW.md

---

## THREE CRITICAL GAPS IDENTIFIED

### ⚠️ CRITICAL GAP #1: No Randomization Capability
**Problem:** Running same scenario twice produces identical exercises
- Same injects in same order
- Same decision points in same sequence
- Same complications in same flow
- No variation seeds or selection rules

**Impact:**
- Predictable output (consultant can "game" the system)
- Limited reusability (can't create 5 variations of same scenario)
- Poor training value (trainees know what's coming next)
- Weak competitive scenarios (multiple teams see identical exercise)

**Solution:** Add "Variation Framework" to each scenario:
- Threat actor variants (3-4 per scenario)
- Complication selection rules (always/conditional/optional)
- Scope variants (minimal/moderate/maximum)
- Timeline variants (fast/normal/slow)

**Effort to Fix:** Medium (add 400-500 lines per scenario = ~3000 lines total)

---

### ⚠️ CRITICAL GAP #2: Weak Style-Specific Guidance at Scenario Level
**Problem:** Scenarios don't explicitly show how to adapt for Traditional/Blended/Gamified
- AI-GENERATION-GUIDE says "apply style guidance" but scenarios don't show how
- No indication of what information to reveal/withhold per style
- No facilitator prompts that differ by style
- Some scenarios don't fit all styles equally well (e.g., BEC + Gamified)

**Impact:**
- AI guesses how to adapt (inconsistent results)
- Weak Gamified versions (time pressure doesn't work naturally)
- Low-tech scenarios don't adapt well to time-pressured styles
- Facilitators confused about style differences

**Solution:** Add "Style-Specific Adaptation" sections to each scenario:
- Traditional: How to maximize discussion (information upfront, 30-40 min per decision)
- Blended: How to balance (10 min discuss + 5 min decide)
- Gamified: How to maximize pressure (limited info, strict timing, scoring)

**Effort to Fix:** Medium (add 300-400 lines per scenario)

---

### ⚠️ CRITICAL GAP #3: Limited Randomization Within Components
**Problem:** Scenarios have fixed threat actors, timelines, and decision sequences
- Threat actor profile is generic (no variant operators)
- Attack timeline never varies (same progression every time)
- Decision points always appear in same order
- Complications always available in same order

**Impact:**
- Second run feels like copy-paste
- No "replay value" for same team
- Hard to create multiple exercises from same scenario
- Consulting firm can't create variations for multi-team exercises

**Solution:** Add selection rules and variant pools:
- Define 3-4 threat actor variants per scenario
- Define which complications are always/sometimes/rarely triggered
- Create "fast attack" vs. "slow attack" timeline variants
- Add decision emphasis variants (forensics-heavy vs. HR-heavy, etc.)

**Effort to Fix:** Medium (requires thoughtful design, not just writing)

---

## SCENARIO PORTFOLIO ASSESSMENT

### Strengths ✅
- **Difficulty distribution:** Good spread (1 beginner, 3 intermediate, 3 advanced)
- **Technical weight:** Balanced for technical audiences (1 low, 5 moderate, 2 high)
- **Structure:** All scenarios follow consistent patterns
- **Decision framework:** 4-5 decision points per scenario is appropriate
- **Complications:** 6-7 complications per scenario provides depth

### Weaknesses ⚠️
- **Low-tech underrepresented:** Only BEC for non-technical audiences
- **Gamified weak fit:** BEC and Cloud Misconfiguration don't adapt well to time pressure
- **Industry gaps:** Retail/manufacturing/government underserved
- **Scenario fatigue:** Same scenario repeated feels identical each time

---

## SCENARIO-BY-SCENARIO QUICK CRITIQUE

### 1. RANSOMWARE (Intermediate, Moderate-Tech)
**Score:** 7.5/10 | **Verdict:** Strong, add variants
- ✅ Excellent decision tree, works across all styles
- ✅ Natural escalation and time pressure
- ❌ Generic threat actor (no variants)
- ❌ Predictable complications
- 🔧 **To improve:** Add threat actor variants (LockBit, Hive, Nation-state, Script-kiddies)

### 2. BUSINESS EMAIL COMPROMISE (Beginner-Intermediate, Low-Tech)
**Score:** 5.5/10 | **Verdict:** Too simple, needs investigation depth
- ✅ Good for beginners, clear decision
- ❌ **Too simple** - binary choice (fraud detected or not)
- ❌ **Gamified doesn't work** - no time pressure mechanism
- ❌ Missing investigation (how long was email compromised?)
- 🔧 **To improve:** Add investigation phase, secondary fraud attempts

### 3. DATA BREACH (Intermediate, Moderate-Tech)
**Score:** 7/10 | **Verdict:** Good, add attacker angle
- ✅ Clear regulatory framework, good complexity
- ✅ Works across durations (4-hour to full-day)
- ❌ Missing "data valuation" angle (ransom demand)
- ❌ No attacker attribution decision
- 🔧 **To improve:** Add "ransom demand" complication, attacker variants

### 4. INSIDER THREAT (Advanced, High-Tech)
**Score:** 7/10 | **Verdict:** Good, add false-positive variant
- ✅ Unique from external attacks, forces HR/legal coordination
- ✅ Works across all styles with natural pacing
- ❌ **Doesn't compress to 2-hour** (investigation takes time)
- ❌ Missing false-positive variant (innocent employee accused)
- 🔧 **To improve:** Add false-positive/contractor/current-employee variants

### 5. CLOUD MISCONFIGURATION (Intermediate, Moderate-Tech)
**Score:** 6.5/10 | **Verdict:** Good, add cascading discoveries
- ✅ Modern, relevant, balanced complexity
- ✅ Fits 2-4 hour exercises well
- ❌ Relatively straightforward (bucket is public → secure it)
- ❌ No cascading discoveries (usually multiple resources misconfigured)
- 🔧 **To improve:** Add cascading bucket/credentials/other-clouds discovery

### 6. SUPPLY CHAIN COMPROMISE (Advanced, High-Tech)
**Score:** 8/10 | **Verdict:** Strong, add dependency variant
- ✅ Excellent complexity, works across all styles
- ✅ Rich decision tree, strong complications
- ✅ Excellent for full-day exercises
- ❌ **Doesn't compress well to 4-hour** (very complex)
- ❌ Missing "dependency" variant (library vs. product)
- 🔧 **To improve:** Add dependency/customer-discovery variants

### 7. THIRD-PARTY VENDOR (Advanced, Moderate-Tech)
**Score:** 7.5/10 | **Verdict:** Strong, add vendor-type variants
- ✅ Practical for all industries, good complexity
- ✅ Forces vendor relationship management
- ✅ Relevant to current threats (MOVEit, 3CX, Okta)
- ❌ Missing SaaS/MSP/hardware vendor variants
- ❌ Assumes vendor cooperates (no uncooperative variant)
- 🔧 **To improve:** Add SaaS/MSP/hardware variants, uncooperative vendor complication

---

## RANDOMIZATION SCORECARD

| Component | Current | Needed | Gap |
|-----------|---------|--------|-----|
| **Threat actor variants** | 1 per scenario | 3-4 per scenario | Add variants |
| **Timeline variants** | 1 (fixed) | 2-3 variants | Add variants |
| **Complication selection** | All available | Always/conditional/optional | Add rules |
| **Scope variants** | Fixed (max) | 3 variants (min/mod/max) | Add variants |
| **Decision emphasis** | Fixed | Multiple emphasis options | Add variants |
| **Randomization seeds** | None | Document selection logic | Add guidance |

**Overall Randomization Score: 3/10** (Currently deterministic, needs variation framework)

---

## STYLE ADAPTATION SCORECARD

### By Scenario

| Scenario | Traditional | Blended | Gamified | Notes |
|----------|-----------|---------|----------|-------|
| Ransomware | ✅ 8/10 | ✅ 8/10 | ✅ 8/10 | Works well for all |
| BEC | ✅ 8/10 | ⚠️ 5/10 | ❌ 2/10 | Struggles with pressure |
| Data Breach | ✅ 8/10 | ✅ 7/10 | ⚠️ 5/10 | Investigation too slow |
| Insider Threat | ✅ 9/10 | ✅ 7/10 | ⚠️ 4/10 | Forensics hard to compress |
| Cloud Misc | ✅ 8/10 | ✅ 7/10 | ⚠️ 5/10 | Limited complexity |
| Supply Chain | ✅ 9/10 | ✅ 8/10 | ✅ 8/10 | Excellent across all |
| 3rd-Party | ✅ 9/10 | ✅ 8/10 | ✅ 7/10 | Good for all styles |

**Pattern:** Advanced scenarios adapt better to Gamified; beginner/simple scenarios struggle.

---

## MARKET GAP ANALYSIS

### Underserved Markets

**Low-Tech / Business-Focused Audiences:**
- Current: Only BEC available
- Needed: 2-3 more non-technical scenarios
- Examples: Crisis Communication, Vendor Management, Social Engineering

**Retail / E-commerce:**
- Current: Limited scenarios addressing customer-facing operations
- Needed: POS compromise, inventory manipulation, customer data scenarios
- Gap: Most scenarios assume backend infrastructure

**Manufacturing / OT (Operational Technology):**
- Current: No scenarios addressing industrial control systems
- Needed: Supply chain physical disruption, equipment compromise
- Gap: Most scenarios assume IT infrastructure only

**Government / Critical Infrastructure:**
- Current: Limited scenarios for classified/sensitive data handling
- Needed: National security implications, inter-agency coordination
- Gap: Most scenarios don't address government-specific regulations

**Availability-Focused (vs. Data-Focused):**
- Current: DDoS mentioned but not fully developed
- Needed: Availability-critical scenarios (healthcare patient care, finance trading)
- Gap: Most scenarios focus on data breach/compromise, not availability

---

## PRIORITY ROADMAP

### PHASE 1 (CRITICAL - Start First)
**Weeks 1-3**
- [ ] Add Threat Actor Variants to all 7 scenarios
- [ ] Add Complication Selection Rules to all 7 scenarios
- [ ] Update AI-GENERATION-GUIDE with variation framework

**Why First:** Enables immediate randomization benefit

---

### PHASE 2 (HIGH - Start After Phase 1)
**Weeks 4-6**
- [ ] Add Style-Specific Adaptation Sections to all scenarios
- [ ] Add Timeline Variants to all scenarios
- [ ] Test randomization with sample exercises

**Why Second:** Improves quality of style adaptation

---

### PHASE 3 (MEDIUM - Parallel to Phase 2)
**Weeks 7-10**
- [ ] Create 2-3 new low-tech scenarios
- [ ] Create compressed variants of complex scenarios
- [ ] Add Example Variations to each scenario

**Why Third:** Expands market, improves reusability

---

### PHASE 4 (NICE-TO-HAVE)
**Weeks 11-12**
- [ ] Improve Gamified fit for weak scenarios
- [ ] Create industry-specific variants (retail, healthcare)
- [ ] Document variation selection for consultants

---

## IMPLEMENTATION QUICK START

### To Add Threat Actor Variants (Example: Ransomware)

**Add this section to ransomware-scenario.md:**

```markdown
## Threat Actor Variants

### Variant A: LockBit-Style Group
- Professional, organized, business-like approach
- Quick ransom negotiation (72 hour deadline)
- Likely to accept partial payment
- Good operational security
- **Facilitator impact:** Realistic negotiation possible

### Variant B: Hive-Affiliated Group
- Aggressive, demanding timeline (48 hour deadline)
- Likely to escalate threats
- More hostile during negotiation
- Emotional pressure component
- **Facilitator impact:** High pressure scenario

### Variant C: Nation-State Testing
- Slower, more persistent
- Less ransom focus, more data exfiltration
- Better detection avoidance
- Longer investigation timeline
- **Facilitator impact:** Deeper forensics, less negotiation

### Variant D: Script-Kiddies
- Mistakes in execution (traceable)
- Weaker encryption/persistence
- Easy to attribute and track
- Good learning scenario
- **Facilitator impact:** Technical team can trace attacker

**Selection Logic:**
- Default: Random selection (equal probability)
- Consultant preference: Specify "realistic," "difficult," or "learning"
```

---

## KEY METRICS FOR SUCCESS

### Randomization Success
- [ ] Same scenario generates ≥3 visually different exercises
- [ ] Threat actors differ across runs
- [ ] Decision points have different emphasis
- [ ] Complications appear in different sequences
- [ ] Injects are selected from variant pools

### Style Adaptation Success
- [ ] Traditional exercises emphasize discussion (30+ min per decision)
- [ ] Gamified exercises create time pressure (5-10 min per decision)
- [ ] Blended exercises balance (10 min discuss + 5 min decide)
- [ ] Facilitator prompts differ by style
- [ ] Information withholding is explicit by style

### Portfolio Success
- [ ] ≥5 low-tech scenarios (for non-technical audiences)
- [ ] ≥8 total scenarios (cover most major threat types)
- [ ] ≥3 industry-specific variants per scenario
- [ ] All scenarios work in 2-hour, 4-hour, and 6-hour formats

---

**Status:** Ready for implementation
**Next Step:** Begin Phase 1 (add threat actor variants to all 7 scenarios)
