# Business Email Compromise Scenario - Wire Fraud

**Difficulty Level:** Beginner-Intermediate
**Recommended Duration:** 2-hour or 4-hour exercise
**Industry Applicability:** All industries (Finance, Healthcare, Manufacturing, Technology, Government, etc.)
**Scenario Type:** Social engineering attack using compromised email to commit fraud

---

## Executive Summary

This scenario simulates a Business Email Compromise (BEC) attack, also known as CEO Fraud or Wire Fraud. Unlike technical attacks, BEC relies on social engineering and email compromise to convince finance staff to send fraudulent wire transfers.

**Key Characteristics:**
- **Low technical sophistication** (but high social engineering)
- **High financial impact** (average BEC losses: $120K+ per incident)
- **Fast execution** (measured in hours, not days)
- **Hard to detect** (looks like legitimate business transaction)
- **Hard to reverse** (once money is wired, it's gone)

**Scenario Tests:**
1. **Email security awareness** - Can people recognize compromised email?
2. **Financial controls** - Are there checks before large wire transfers?
3. **Verification procedures** - Do people verify by phone before transferring?
4. **Fraud detection** - Can finance team spot unusual transaction patterns?
5. **Speed of response** - Can they stop the fraud once detected?

---

## Threat Actor Profile

### BEC Attack Group

**Group Type:** Organized cybercriminal group specializing in wire fraud
**Sophistication Level:** Low-to-Intermediate (doesn't need technical sophistication)
**Primary Motivation:** Direct financial theft
**Attack Method:**
1. Identifies high-value targets (finance companies, manufacturer with large accounts)
2. Researches company structure (CEO, CFO, finance team, suppliers)
3. Compromises email account (phishing, credential stuffing, leaked credentials)
4. Sends email impersonating CEO/CFO requesting urgent wire transfer
5. Provides wire instructions to attacker-controlled bank account
6. Wire transfer happens before anyone can verify

**Success Rate:** Despite being well-known, BEC attacks succeed 80%+ of the time attacks are attempted
- Reason: Human nature (authority, urgency, embarrassment about mistakes)
- No technical exploit needed - just social engineering

---

## Attack Narrative Timeline

### Phase 1: Reconnaissance (Weeks Before Attack)

**Week -4: Target Selection**
- Attacker identifies [your company] as target
- [Company] chosen because:
  - Has regular large financial transactions (suppliers, partners, acquisitions)
  - Suitable victim profile (legitimate business, not fraud-prone)
  - Online presence allows research about executives and processes

**Week -3: Research & Profiling**
- Attacker researches:
  - Company website - finds executive team list (CEO, CFO names, photos)
  - LinkedIn - finds detailed employee roster and reporting structures
  - Previous earnings calls or investor docs - learns about business partners, recent deals
  - Email format - identifies company email domain pattern (firstname.lastname@company.com, firstinitial.lastname@company.com, etc.)
  - Finance team structure - identifies who handles wire transfers
  - Suppliers/partners - identifies companies you regularly pay

**Week -2: Email Compromise**
- Attacker obtains credentials for CFO or Finance staff member
- Method: Phishing email, credential stuffing, purchased from dark web
- Compromises email account: [CFO email or Finance team member email]
- Tests access - sends test email to confirm account works
- Sets up forwarding rule to attacker's email (so attacker can see responses)
- Configures account signature to match legitimate CFO signature

---

### Phase 2: Attack Execution (Hours Before Detection)

**Day of Attack - Morning (T-4 hours):**
- Attacker logs into compromised CFO account
- Sends email to Finance Director / Accounting Manager
- Email Subject: "Urgent: Wire Transfer Required - Confidential"
- Email Content:
  ```
  [Finance Director Name],

  I need you to arrange an urgent wire transfer today. This is confidential and time-sensitive.

  Beneficiary: [Supplier Name]
  Amount: $[500K-2M depending on company size]
  Account: [Bank details - attacker-controlled]
  Routing: [Routing number for attacker's bank]

  This is for [vague business reason: acquisition, vendor payment, emergency payment, etc.].

  Please confirm wire has been sent to me immediately.

  -[CEO/CFO Name]
  ```

**Key Social Engineering Elements:**
- Uses CEO/CFO name (authority)
- Marked "Confidential" (creates secrecy)
- "Urgent" and "today" (creates time pressure)
- "Please confirm immediately" (no time to verify)
- Vague business reason (plausible deniability)
- Doesn't ask permission - states as command

**Day of Attack - Mid-morning (T-3 hours):**
- Finance staff member receives email
- Assumes it's from CFO (trusted sender)
- Recognizes sender address in their inbox
- Feels time pressure and confidentiality
- May feel embarrassed to question CEO/CFO
- Begins processing wire transfer

**Day of Attack - Late Morning (T-1 hour):**
- Finance staff begins wire transfer
- May go through normal approval processes (but attacker's urgency bypasses some)
- Initiate transfer to attacker-controlled account
- Wire enters processing queue

**Day of Attack - Noon (T+0):**
- Wire transfer submitted and cleared
- Money leaves company account
- Money transferred to attacker's bank account
- Attacker has access to funds

**Day of Attack - Afternoon (T+2 hours):**
- Finance staff member replies to email confirming wire sent
- Attacker checks reply (via forwarding rule in CFO's account)
- Attacker covers tracks (deletes emails from CFO's sent folder, deletes replies)
- Attacker logs out and abandons account

**Discovery (T+3-8 hours depending on detection):**
- CEO/CFO is contacted by someone asking about the wire
- OR: Finance discovers the unauthorized wire on reconciliation
- OR: Recipient (supplier) says they never received payment
- Investigation begins (this is when exercise starts)

---

## Initial Detection Points

### Detection Point 1: Email Received from CFO

**Time:** T-2 hours (during the attack, before discovery)
**What participants receive:**
[Email message requesting urgent wire transfer, appearing to come from CFO]

**Key Details:**
- Sender: [CFO email address] (appears correct)
- Subject: "Urgent: Wire Transfer Required - Confidential"
- Content: Requests immediate wire transfer of $[amount] to specific account
- Tone: Authoritative, time-pressure, confidentiality

**What Should Trigger Suspicion:**
- CFO doesn't usually email wire requests (normally verbal discussion first)
- Request lacks normal approval processes
- Amount is unusual (larger than typical, or pattern change)
- Beneficiary is not on normal supplier list (or new supplier)
- Request lacks context or business justification
- Sender didn't use typical chain-of-command

**Detection Method:**
- Participants should note this email and question it BEFORE processing
- Should verify by calling CFO directly (not replying to email)

### Detection Point 2: Wire Transfer Anomaly

**Time:** T+0 (after discovery)
**What IT/Finance discover:**
- Finance manager reports unusual wire transfer
- Wire sent to account: [Account details]
- Amount: $[Large amount]
- Recipient: [Name that doesn't match typical suppliers]
- Approval chain: Wire processed with minimal approvals (normal process requires 2+ approvals, this had 1)

**What This Reveals:**
- Wire bypassed normal controls
- Recipient is suspicious (new account, doesn't match suppliers)
- Processing speed was unusual (same-day execution)
- Email claiming to be from CFO triggered this
- Very likely fraudulent wire

**Detection Confidence:** High - This is clearly suspicious if caught in time

### Detection Point 3: CFO Confirmation Needed

**Time:** T+2 hours (when someone contacts CFO)
**What happens:**
- Finance manager follows up with CFO (in person or by phone)
- CFO says: "I didn't send that email. I didn't authorize any wire transfer."
- CFO checks their email - can see the email they "supposedly sent"
- Immediate realization: Account has been compromised, wire is fraudulent

**Confirmation:** Fraud confirmed

---

## Initial Conditions - What Participants Inherit

**Current Time:** T+3 hours (after CFO denies authorization)

**Known Facts:**
- Wire transfer sent 3 hours ago: $[X amount]
- Recipient account: [Bank, account details]
- Email appeared to come from CFO but CFO denies sending it
- Likely that CFO's email has been compromised
- Wire may still be reversible (depends on bank)

**Current State:**
- Money is in transit (sent but not yet received at destination)
- CFO email account appears compromised
- Finance team is in panic
- Bank has been notified but may not be able to recover
- No customer impact (internal fraud), but direct financial impact

**What Participants DON'T Know Yet:**
- Can the wire be reversed?
- Where will the money ultimately end up?
- Will the attacker's bank cooperate with recovery?
- Are there other fraudulent wires?
- Is the CFO account the only one compromised?
- How did attacker get the CFO's credentials?

---

## Organizational Impact Assessment

### Immediate Impact
- **Financial Loss:** $[amount] of company funds transferred to attacker
- **Account Compromise:** CFO email is compromised
- **Operational Disruption:** No systems down, but finance processes disrupted
- **Reputational Risk:** Internal fraud (not public yet)

### Longer-Term Impact
- **Account Security Review:** All financial staff accounts need review
- **Process Review:** Wire transfer approval process failed - needs redesign
- **Email Security:** Need to ensure MFA on sensitive accounts
- **Staff Training:** Finance team needs education on BEC attacks

---

## Key Decision Points

### Decision Point 1: Immediate Wire Recovery

**Timing:** T+3 hours (immediately after discovery)

**Situation:**
Wire transfer was sent 3 hours ago. Bank may be able to reverse it if caught quickly. You have a narrow window (banks can reverse some wires up to 24 hours).

**Key Question:** How aggressively do you pursue recovery?

**Option A: Urgent Bank Recovery (Immediate Action)**
- **Action:**
  - Contact sending bank immediately (escalate to executive level)
  - Request immediate wire recall/reversal
  - Contact receiving bank and law enforcement
  - Provide all documentation (fraudulent email, CFO confirmation)
  - Ask for bank to freeze the account the money went to
- **Timeline:** Contact within 1 hour, recovery possible within 6 hours
- **Success Rate:** ~50-60% if done fast (depends on receiving bank and account)
- **Cost:** Standard (no extra cost)
- **Benefit:** May recover most or all of funds

**Option B: Measured Approach (Investigation First)**
- **Action:**
  - Document the fraud (save email, get CFO statement)
  - Contact bank but take time to understand full scope
  - Investigate whether there are other fraudulent wires
  - Then pursue recovery through formal processes
- **Timeline:** Investigation (24 hours), then recovery attempt
- **Success Rate:** Lower (~20-30%) - receiving bank has already processed
- **Benefit:** More information before pursuing recovery
- **Risk:** May lose recovery window

**Option C: Law Enforcement First (Legal Path)**
- **Action:**
  - File police report immediately
  - File FBI report (BEC is common FBI target)
  - Let law enforcement pursue recovery through legal channels
- **Timeline:** Law enforcement pursuit takes weeks/months
- **Success Rate:** Low (~10-20%)
- **Benefit:** Legally defensible approach, law enforcement resources
- **Risk:** Much slower than direct bank action

**Who Decides:** CFO + Finance Director + Security

**Evaluation:** Do they understand the time-critical nature of wire recovery? Can they act fast while maintaining proper process?

---

### Decision Point 2: Account Breach Response

**Timing:** T+4 hours

**Situation:**
CFO's email account is compromised. You must decide: How do you secure it and investigate the compromise?

**Key Question:** Do you shut down CFO's email, or keep monitoring to catch attacker?

**Option A: Immediate Shutdown & Reset**
- **Action:**
  - Force password reset on CFO account
  - Force logout of all active sessions
  - Remove any forwarding rules or suspicious configurations
  - Disable account until fully secured (1-2 hours)
  - Re-enable with new password and MFA
- **Timeline:** 1-2 hours account downtime
- **Benefit:** Immediately secures account, prevents further fraud
- **Risk:** Attacker realizes they've been caught, may activate other compromises

**Option B: Silent Monitoring**
- **Action:**
  - Monitor account for attacker access
  - Don't change password yet
  - Watch for attacker deleting evidence or accessing other accounts
  - Gather evidence of attacker behavior
- **Timeline:** Monitoring for 6-24 hours
- **Benefit:** Can observe attacker, gather evidence
- **Risk:** Attacker could send more fraudulent emails or access other accounts

**Option C: Controlled Reset (Honeypot)**
- **Action:**
  - Change password but use honeypot/trap password
  - Monitor when/if attacker tries to log in with old credentials
  - Monitor for any attempts to access from unusual locations
- **Timeline:** 24-48 hours of monitoring
- **Benefit:** Catch attacker if they try to access, gather evidence
- **Risk:** Risk of additional fraud if attacker keeps sending emails

**Who Decides:** CISO + CFO

**Evaluation:** Do they balance security urgency with forensic investigation needs?

---

### Decision Point 3: Wire Fraud Prevention - Process Changes

**Timing:** T+8 hours (after wire recovery attempt)

**Situation:**
Investigation confirms BEC vulnerability in your wire transfer process. You must decide: What changes to make?

**Current Process Issues:**
- Wire requests by email are accepted without verification
- Approval chain only requires one signer
- No MFA on financial staff email
- No verification by phone before sending
- No secondary account verification

**Option A: Comprehensive New Process**
- **Action:**
  - All wire transfers require 2 signers (no exceptions)
  - First signer initiates request in secure financial system (not email)
  - Second signer must verify via phone call to account holder
  - Phone call uses pre-registered numbers from contact list
  - Email confirmations not accepted
  - MFA required on all financial staff email accounts
  - EDR monitoring on financial staff systems
- **Cost:** Process training, system changes, ongoing overhead
- **Timeline:** 2-4 weeks implementation
- **Benefit:** Eliminates most BEC fraud vectors
- **Risk:** Slows down legitimate transactions, operational friction

**Option B: Quick Wins (Minimum Viable)**
- **Action:**
  - Require phone verification before any wire over $[threshold]
  - Enable MFA on financial staff email only
  - No major process changes
- **Cost:** Low
- **Timeline:** 1 week
- **Benefit:** Fast implementation
- **Risk:** Doesn't address underlying process weakness, attacker could adjust to new $[threshold]

**Option C: Phased Approach**
- **Action:**
  - Month 1: Require phone verification for wires >$[threshold], enable MFA
  - Month 2: Implement dual approval for all wires
  - Month 3: Move wire requests to secure financial system instead of email
- **Timeline:** 3-month rollout
- **Cost:** Moderate (spread over time)
- **Benefit:** Balanced approach
- **Risk:** Gaps during implementation period

**Who Decides:** CFO + CISO + Finance Director

**Evaluation:** Do they understand that process controls matter more than technical controls for this threat?

---

### Decision Point 4: Insurance & Fraud Recovery

**Timing:** T+12 hours

**Situation:**
Fraud was confirmed at T+0. Wire recovery attempts are underway. You must coordinate with:
1. Insurance company (cyber liability policy may cover)
2. Bank (may have insurance or recovery services)
3. Law enforcement (FBI, local cybercrime unit)

**Key Question:** How much effort to invest in recovery vs. write-off?

**Financial Scenario:**
- Wire Amount: $[X]
- Recovery Likelihood: [20-50% depending on bank cooperation]
- Recovery Costs: Legal fees, investigation, bank charges (~$50K)
- Time Investment: 6 months to 2 years to fully resolve

**Option A: Aggressive Recovery**
- **Action:**
  - Hire specialized forensic accounting firm
  - Work with law enforcement for international recovery
  - Coordinate with receiving bank for asset freeze
  - File civil lawsuit if necessary
  - Budget $100K+ for recovery efforts
- **Timeline:** 6-18 months
- **Success Rate:** ~30-50%
- **Benefit:** Maximum recovery chance
- **Risk:** High cost, may not recover even with effort

**Option B: Cooperative Recovery (Limited Effort)**
- **Action:**
  - Let insurance company lead recovery efforts
  - Coordinate with law enforcement
  - Budget $25K for legal/process
  - Accept that full recovery unlikely
- **Timeline:** 6-12 months
- **Success Rate:** ~20-30%
- **Benefit:** Lower cost, shared effort with insurance
- **Risk:** Lower recovery rate

**Option C: Cut Losses (Accept Write-Off)**
- **Action:**
  - Treat as complete loss for accounting purposes
  - Prevent future fraud (focus on that)
  - Let insurance company pursue if they wish
- **Timeline:** Immediate
- **Cost:** One-time loss of wire amount (plus insurance deductible)
- **Benefit:** Avoids ongoing recovery costs and effort
- **Risk:** Doesn't recover funds, may not prevent future incidents

**Who Decides:** CFO + Insurance + Legal

**Evaluation:** Do they understand trade-offs between recovery effort and likelihood of success?

---

## Complications & Surprise Elements

### Complication 1: Multiple Fraudulent Wires

**When It's Introduced:** T+6 hours

**What Happens:**
During investigation, you discover the CFO's email was compromised for LONGER than you thought. Review of sent folder reveals:
- Wire sent 3 hours ago (the one you caught): $[Amount 1]
- Wire sent 2 days ago (missed): $[Amount 2]
- Wire sent 4 days ago (missed): $[Amount 3]
- Total fraud: $[Amount 1 + 2 + 3] (potentially $1M+ depending on company size)

**Why This Complication Matters:**
- Shows the compromise was longer than realized
- Shows attacker sent multiple frauds before you noticed
- Some money may already be irretrievable (if transfer completed days ago)
- Raises question: Are there other compromised accounts?

**Impact on Decisions:**
- Scope of investigation expands dramatically
- Recovery efforts must focus on older transfers
- Bank coordination becomes more complex
- Raises urgent need to audit all financial staff accounts

**Facilitator Note:**
"During email review, you found that the compromise was going on longer than you thought. There are at least 2 other fraudulent wires in the sent folder from the past few days."

---

### Complication 2: Attacker Still Has Access

**When It's Introduced:** T+8 hours

**What Happens:**
After you reset CFO's password, your SOC detects:
- Login attempt from attacker's IP address (geolocation: [foreign country])
- Attempt failed (because password was reset)
- But attacker's IP is still active and monitoring the account
- Suggests attacker has alternative persistence (not just the CFO's password)

**Why This Complication Matters:**
- Password reset wasn't enough
- Attacker may have created backdoors or secondary accounts
- Suggests broader compromise of CFO's systems
- Requires forensic investigation

**Impact on Decisions:**
- Need to audit CFO's computer (may have malware)
- Need to check if attacker created additional accounts
- Need to determine when compromise started (days? weeks?)

**Facilitator Note:**
"Your SOC just reported a login attempt on the CFO's account from [foreign IP] about 1 hour after you reset the password. Attempt failed, but it suggests the attacker still has access to something."

---

### Complication 3: Reputation & Customer Impact

**When It's Introduced:** T+12 hours

**What Happens:**
- News of the fraud leaks internally (employees hear about it)
- Large supplier calls asking about delayed payment
- Supplier says they never received the fraudulent wire
- Supplier is now suspicious about your company's financial stability
- Other suppliers call asking if you're in financial trouble

**Why This Complication Matters:**
- Fraud is no longer internal
- Suppliers may lose confidence
- Business relationships are affected
- Raises question: Do you need to disclose to other partners?

**Impact on Decisions:**
- May need to inform key suppliers/partners
- Affects business relationships
- Shows reputational risk even though no customer data was breached

**Facilitator Note:**
"Your major supplier just called. They're saying they never got the wire, and they're asking why your company is trying to pay them from strange accounts. They're starting to question whether to keep doing business with you."

---

## Scenario-Specific Customizations by Industry

### Healthcare

**Healthcare-Specific Impact:**
- Fraudulent wires might be disguised as payments to insurance companies or vendors
- If compromised, CFO email could potentially access patient data systems
- Reputation damage (healthcare fraud suggests deeper problems)

---

### Retail / Manufacturing (with Supplier Relationships)

**Industry-Specific Impact:**
- Fraudulent wires often impersonate supplier payments
- Supplier relationships are critical to operations
- Supply chain disruption if suppliers lose confidence

---

### Technology / Finance (with Investor Relations)

**Industry-Specific Impact:**
- If fraud becomes public, stock price impact
- SEC disclosure requirement if material
- Investor confidence affected
- Rating agency review

---

## IR Capabilities Tested

### Financial Controls
- **Approval Processes:** Are there adequate checks?
- **Verification Procedures:** Do people verify wire requests?
- **Anomaly Detection:** Can fraud be caught before execution?

### Email Security
- **Phishing Prevention:** Do people recognize phishing?
- **Account Security:** Do key accounts have MFA?
- **Email Authentication:** Are DMARC/SPF protecting against spoofing?

### Speed of Response
- **Detection:** How quickly is fraud detected?
- **Response:** How quickly can they act to recover funds?
- **Communication:** Can they coordinate across teams quickly?

### Vendor/Supplier Relationships
- **Due Diligence:** Know your vendors
- **Communication Protocols:** How are wire instructions verified?
- **Trust Verification:** Can suppliers verify changes to payment details?

---

## Success Indicators

### Strong Response (Advanced)
- ✓ Detected fraud attempt before wire sent (or very quickly after)
- ✓ Immediately understood severity and acted quickly
- ✓ Contacted bank within 1 hour for recovery
- ✓ Secured compromised account immediately after verification
- ✓ Investigated scope of compromise
- ✓ Implemented prevention measures quickly
- ✓ Managed communication appropriately

### Developing Response (Intermediate)
- ✓ Detected fraud within a few hours
- △ Some delay in recovery attempt
- △ Account security was addressed eventually
- △ Prevention measures implemented but might take longer

### Weak Response (Emerging)
- ✗ Fraud went undetected for extended period
- ✗ Delayed in contacting bank for recovery
- ✗ Treated as IT problem instead of financial problem
- ✗ No investigation of scope
- ✗ Didn't immediately secure compromised account

---

**Scenario Complete**

This BEC scenario tests different capabilities than ransomware or data breach (fraud detection, financial controls, speed of response) while remaining beginner-friendly (no deep technical investigation required).
