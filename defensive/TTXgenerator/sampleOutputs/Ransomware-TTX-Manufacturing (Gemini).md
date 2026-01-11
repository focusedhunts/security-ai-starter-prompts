A **Traditional, discussion-focused** style is well-suited for a large, mixed group of 25 people where the primary objectives are **IR Plan Validation** and **Crisis Management**. This style ensures everyone has a voice and allows for deep exploration of policy and decision-making processes, rather than just technical execution under pressure.

---

I now have all the necessary information to design the customized **Ransomware Tabletop Exercise** for your client:

| Component | Selection |
| --- | --- |
| **Scenario** | Ransomware Attack (Intermediate) |
| **Client** | Medium Manufacturing, Intermediate Maturity, Regulatory Pressure |
| **Objective** | IR Plan Validation & Crisis Management |
| **Duration/Format** | 6-Hour, In-Person |
| **Participants** | Mixed Levels (25 people) |
| **Style** | Traditional (Discussion-focused) |

I will now proceed to generate the comprehensive Facilitator Package using the selected scenario and customizing it with manufacturing-specific elements, focusing on regulatory impact, and scaling the complexity for a 6-hour, Traditional discussion. The inject count will be in the 25-35 range.

---

# 🏭 Ransomware TTX: Manufacturing Production Halt Scenario

## 1. Exercise Overview

### 1.1 Logistics and Goals

| Detail | Specification |
| --- | --- |
| **Scenario Type** | Ransomware Attack (Intermediate) |
| **Client Context** | Medium-Sized Manufacturing, Intermediate Maturity |
| **Primary Objectives** | 1. Validate the Incident Response Plan structure and flow. 2. Test Executive and Crisis Management decision-making regarding production halt and regulatory notification. 3. Assess cross-functional communication (Technical, Legal, Operations, Executive). |
| **Duration** | 6 Hours (Extended: Deep investigation and parallel Crisis Management threads) |
| **Style** | Traditional (Discussion-Focused) |
| **Participants** | Mixed (Technical, Operations, Legal, Executive, HR) - 25 people |
| **Format** | In-Person |
| **Key Focus Areas** | Operational Technology (OT) impact, data exfiltration assessment, ransom decision, regulatory reporting (GDPR/CCPA equivalent, sector-specific), production recovery. |

### 1.2 Participant Roles

This exercise requires representation from the following core functional areas to properly test the plan and crisis management capabilities:

* **Incident Response Team Lead (Technical)**: Directs investigation, containment, and eradication.
* **Operations/Plant Manager (OT Focus)**: Assesses impact on SCADA/Production line and coordinates manual/alternate operations.
* **Legal/Compliance Counsel**: Guides regulatory assessment, data breach notification laws, and external reporting.
* **Executive Crisis Team Lead (C-Suite/VP)**: Handles external communications, ransom decision, and business continuity strategy.
* **Communications/PR**: Manages internal and external messaging, press, and customer updates.

## 2. Detailed Scenario Narrative

### 2.1 Scenario Introduction (Phase 1 Start)

The organization, **PrecisionPro Manufacturing**, relies heavily on digitized blueprints (CAD files) and a robust SCADA/PLC network for its specialized, high-margin product line. This morning, a tier-1 IT analyst received an automated alert indicating high outbound network traffic from a recently decommissioned staging server. Simultaneously, two employees in the finance department reported that their workstations are displaying a full-screen image of a skull and crossbones with a countdown timer. Initial checks confirm the file share server holding all product design documents is inaccessible.

> **Key Initial Challenge:** Determine if the OT network (SCADA/PLC) is impacted and assess the scope of the IT system failure. Production lines are currently running but are dependent on the IT system for scheduling and quality control logs.

### The PrecisionPro Production Crisis: Day 1

**Client Context:** PrecisionPro Manufacturing, a medium-sized firm specializing in high-precision parts under strict regulatory contracts.

**Initial Situation:** It is 9:00 AM on a Monday. The IT team has confirmed multiple workstations and key file servers, including the critical CAD/Design repository and the central ERP system, are encrypted. A ransom note demanding 50 Bitcoin (approximately $3.5 Million USD) has appeared, threatening to not only destroy the decryption key but also publicly leak **exfiltrated proprietary product schematics and customer intellectual property (IP)** if payment is not received within 72 hours.

**Immediate Impact:**

1. **IT Systems:** Core file shares, ERP, HR systems, and internal communication platforms are offline or encrypted.
2. **Manufacturing Operations:** While the core SCADA control systems are physically isolated, the scheduling, quality assurance, and inventory management systems (which interface with the production floor) are down. Production is running blind, leading to a high risk of quality failures and an imminent halt within the next 4 hours due to lack of instructions.
3. **Data at Risk:** Highly sensitive proprietary product schematics (IP) and data regarding a large, regulated client contract are threatened with public exposure.

**Exercise Focus:** Your team must immediately activate the Incident Response Plan, establish command and control (C2), make critical decisions under pressure (Ransom? Shut down production?), and prepare for mandatory regulatory disclosures related to customer IP exposure.

## 3. Inject Timeline (6-Hour Traditional Style)

For a 6-hour Traditional exercise, the injects are used to *guide the discussion* and introduce *new information* at key phases, rather than serving as real-time alerts. The timing is approximate and facilitator-controlled based on the group's pace.

### Pacing Guide:

* **Phase 1 (Hour 0-1.5):** Detection, Triage, Containment Strategy, C2 Establishment.
* **Phase 2 (Hour 1.5-3.0):** Investigation Deep Dive, Regulatory Assessment, Stakeholder Notification.
* **Phase 3 (Hour 3.0-4.5):** Crisis Decision-Making (Ransom/Recovery Strategy), Parallel Communications.
* **Phase 4 (Hour 4.5-6.0):** Regulatory Filing/Reporting, Recovery Strategy Execution, Leadership Briefing.

| Inject # | Timing (Approx.) | Delivery Method | Content | Expected Response/Goal | Facilitator Notes |
| --- | --- | --- | --- | --- | --- |
| **1 (Initial)** | T=0:10 | Email/Verbal | Discovery: Finance PC encrypted. Ransom note visible on screen. | Initiate IR Plan, confirm scope, establish C2. | Confirm who is notified first (C-Suite, Legal, IT). |
| **2** | T=0:30 | Technical Update | Initial Forensic Finding: The attack vector was a phishing email resulting in endpoint compromise 3 weeks ago. | Initiate threat hunting for sleeper accounts, define containment method (network segmentation). | Discuss whether to pull the main production network cable immediately. **(Decision Point 1)** |
| **3** | T=0:50 | Operations Call | Operations Manager reports: Production QA/Scheduling systems are encrypted. **Must halt production within 4 hours** without new instructions. | Decide whether to proactively halt production now to limit risk, or wait. | Emphasize the financial and contractual impact of a hard stop. |
| **4** | T=1:15 | Technical Update | C2 Confirmed: Exfil occurred via a compromised staging server before encryption. Preliminary logs suggest **10GB of CAD files and 5GB of customer contract data** were taken. | Legal/Executive assess data sensitivity & regulatory/contractual exposure. | This confirms exfiltration—escalates severity to a data breach. |
| **5** | T=1:45 | Legal/Compliance | Regulatory Counsel advises: The exposed client contract data contains PII and is subject to GDPR/CCPA-like notification laws (due to global client base). **48-hour internal assessment clock starts now.** | Formalize Legal/IR partnership, confirm mandatory notification procedures. | Discuss external counsel engagement. |
| **6** | T=2:15 | Technical Update | Analyst identifies two systems within the **OT network segment** that communicated with the infected staging server 48 hours ago. Status is unknown. | Prioritize OT assessment. Discuss the risk of the SCADA/PLC being compromised but dormant. | Test the ability to investigate/isolate OT systems without disrupting power/safety. |
| **7** | T=2:45 | Complication | **Major Customer Call:** High-priority customer (regulated client) calls, asking about rumors of an "outage" after seeing social media posts. | Prepare initial holding statement, define internal/external comms strategy. | **(Decision Point 2)** Test the Comms Team's response protocol for unconfirmed rumors. |
| **8** | T=3:15 | Executive/Finance | CFO asks: "Our insurance covers the ransom. Should we engage the negotiator and pay? Recovery is estimated at 3-4 weeks if we don't." | **Formal Ransom Decision Point.** Weigh payment vs. rebuild/risk of public leak. | Introduce the legal/ethical ramifications of paying a sanctioned entity. |
| **9** | T=3:45 | Media Alert | **Local News Alert:** "PrecisionPro Manufacturing hit by suspected cyberattack, sources say production has halted." | Roll out the pre-approved media response, notify board/shareholders. | Test readiness of executive comms template and distribution. |
| **10** | T=4:15 | Technical Update | **Forensics Confirmation:** Exfiltration data includes PII/confidential material of the regulated client. No direct customer PII (like credit cards) involved, but IP is confirmed stolen. | Finalize mandatory notification wording and timeline. **(Decision Point 3)** | Move from investigation to formal notification preparation. |
| **11** | T=4:45 | External Alert | **FBI/CISA Outreach:** FBI field office calls, indicating the specific ransomware group is known and has recently targeted other manufacturing firms. They advise against payment. | Coordinate with law enforcement (when, how much information to share). | Discuss the impact of LE guidance on the CFO's decision (Inject 8). |
| **12 (Final)** | T=5:15 | Crisis Management | **CEO Briefing:** Require a 5-slide summary (max) on the current status, decision on ransom/recovery, regulatory plan, and estimated Return to Normal Operations (RTO). | Synthesize all information into a clear executive summary. | Test the team's ability to clearly communicate technical impact to a business audience. |
| **Debrief Start** | T=5:30 | N/A | Transition to Debriefing Phase. | Transition to Lessons Learned. | Use the Debrief structure below. |

## 4. Key Decision Points & Facilitator Guidance

These points require the team to commit to a course of action, which the facilitator will use to guide the discussion and introduce subsequent complications.

### Decision Point 1: Production Halt Strategy (Hour 1)

**Question:** Given the OT uncertainty and loss of QA/Scheduling systems (Inject 3), should the Incident Commander/Operations Manager initiate an immediate, emergency shutdown of all manufacturing production lines, or continue running until the 4-hour hard stop?

| Option | Rationale | Facilitator Guidance (Traditional Style) |
| --- | --- | --- |
| **A: Immediate Shutdown** | Protects product quality and ensures the OT network is physically isolated, minimizing cascading risk. | **Ask:** What is the legal/contractual penalty for 4 hours of *additional* downtime? Does the IR plan give IT the authority to override Operations? |
| **B: Run Until Hard Stop** | Maximizes production time, potentially fulfilling high-priority orders before the inevitable shutdown. | **Ask:** Who accepts the risk of producing potentially faulty product, or worse, infecting an OT system in the next few hours? What is the liability? |

### Decision Point 2: Initial External Communications (Hour 3)

**Question:** Rumors are circulating online (Inject 7). How should the Crisis Communications Team respond to the major, regulated client who is asking directly about an "outage?"

| Option | Rationale | Facilitator Guidance (Traditional Style) |
| --- | --- | --- |
| **A: Acknowledge & Limit Detail** | Confirm "technical difficulties" are impacting certain systems. State you are investigating and provide a clear commitment to an update time. | **Ask:** How do you balance transparency with legal risk? What is the *minimum* required by the client contract? |
| **B: Internal Only / Deny Rumors** | Refuse to comment or state that production is "nominally operational" (false). | **Ask:** What is the long-term impact on trust and regulatory credibility if the full truth is revealed later? |

### Decision Point 3: Regulatory Notification & Timing (Hour 5)

**Question:** Forensics confirms customer IP exfiltration (Inject 10). The team must notify the regulated client/authorities. Should the team notify immediately based on initial data, or delay slightly (within the 48-hour window) to gather more concrete "bad news" details?

| Option | Rationale | Facilitator Guidance (Traditional Style) |
| --- | --- | --- |
| **A: Notify Immediately (Minimal Detail)** | Prioritizes regulatory compliance timeline and transparency. Shows diligence. | **Ask:** What is the risk of having to *re-notify* with worse details later? What specific clause in the client contract mandates this? |
| **B: Wait for Detailed Impact Assessment** | Provides a complete, one-time notification, reducing potential confusion and backlash from incomplete information. | **Ask:** Is waiting for *certainty* worth missing the regulatory clock or appearing evasive? Who signs off on the final decision? |

## 5. Complication Sequence (Traditional Style)

In a Traditional exercise, complications are not punishments but rather accelerators designed to test resilience, internal policy, and parallel work streams.

| Timing (Approx.) | Type | Complication Trigger | Impact on Discussion |
| --- | --- | --- | --- |
| **T=0:45** | **Policy Failure** | No single decision-maker for emergency network segmentation is pre-authorized in the IR plan. | Forces a discussion on *authority*—who makes the hard call to interrupt the business? |
| **T=2:30** | **Internal Conflict** | Operations (OT) refuses to give IR/IT remote access to the OT network for investigation (Inject 6) citing safety protocols. | Tests the boundary/coordination between IT and OT teams and the Crisis Team's authority. |
| **T=4:00** | **Financial Pressure** | External counsel advises that paying the ransom (if decided) is complicated by potential sanctions against the threat group, putting the company's banking relationship at risk. | Re-opens the Ransom Decision Point (Inject 8) with a new, major financial/compliance risk. |
| **T=5:00** | **Resource Constraint** | The third-party Digital Forensics and Incident Response (DFIR) retainer is capped. Extending the investigation for the **full 4 weeks** to rebuild properly will require a $500k emergency PO. | Tests budget authorization and financial planning in a crisis state. |

## 6. Debrief Structure

The debrief should take the final 30-45 minutes and focus on lessons learned for plan validation and crisis maturity.

### Debriefing Outline: Lessons Learned & Next Steps

#### Phase I: Hotwash (15 min)

* **What Went Well?** (Focus on policies/procedures that worked or roles that were clearly defined.)
* *Prompt:* What aspects of the IR Plan were successfully utilized?
* *Prompt:* Which cross-functional handoffs (e.g., Legal to IT) were smooth?


* **What Was Challenging?** (Focus on gaps in communication, plan, or authority.)
* *Prompt:* What decision points caused the most debate/delay? (Reference DP 1, 2, 3).
* *Prompt:* Did communications (internal/external) move fast enough?



#### Phase II: After Action Review (15 min)

* **Gaps Identified:**
* Authority to Shut Down OT Systems: Do we need a defined escalation path?
* Ransom Policy: Is our "pay/no-pay" stance clear, considering regulatory/sanction risk?
* Regulatory Notification Template: Do we have a pre-approved script for specific data types (IP vs. PII)?


* **Key Takeaways by Function:**
* *Technical:* What visibility gaps must be filled (OT network)?
* *Operations:* What is the documented manual mode/recovery procedure for production?
* *Executive/Legal:* Are the notification timelines for all relevant clients/regulators mapped out?



#### Phase III: Prioritized Action Items (15 min)

* **3 Most Critical Action Items:** (The team must commit to these.)
1. *Example:* Update IR plan section 3.2 to clearly grant Incident Commander authority to mandate an emergency network shutdown across IT/OT.
2. *Example:* Create an operationalized OT investigation "fly-away kit" and procedure.
3. *Example:* Draft and approve 3 holding statements (External, Internal, Customer) for cyber incidents.



## 7. Participant Briefing Materials Overview

The following provides a non-spoiler overview for participants.

### Welcome to the Crisis Simulation Exercise

**Purpose:** To test and validate our organization's response capability to a major cyber incident affecting critical business operations.

**Ground Rules:**

1. **Safety First:** This is an exercise. There are no actual systems affected, and no judgment.
2. **Focus on Policy:** Discuss what the plan *says* you should do, and if that action is effective. If there is no plan, discuss what the policy *should be*.
3. **Stay in Role:** When speaking, address your comments to the relevant functional leader (e.g., "Legal, what is our counsel on this?").
4. **Assumptions:** All necessary staff are available, and initial funding for common items (laptops, software licenses) is accessible.

## **Scenario Initial Briefing:**
You have received a verbal alert from IT confirming a widespread outage. The Crisis Management Team is activated. Your primary focus in the first hour is establishing communication, determining the scope, and making initial containment decisions.

## Next Steps: Creating Professional Deliverables

Your customized **6-Hour Traditional Ransomware Exercise** is complete. To transform this markdown document into professional, client-ready materials (like a PowerPoint presentation or structured briefing document), please utilize the following steps:

1. **Extract Content using Export Markers:**
* Use the `` tags to quickly copy/paste specific sections into your presentation template. For example, the `SCENARIO-NARRATIVE` is perfect for the initial participant slides. The `FACILITATOR-GUIDE` is the internal master document.
* The `INJECT-TIMELINE` and `DECISION-POINTS` blocks are ready for internal facilitator notes/scripting.


2. **Refer to the Deliverable Creation Guide:**
* For detailed instructions on formatting and presentation standards, consult the `DELIVERABLE-CREATION-GUIDE.md` reference material. This guide provides best practices for visualizing the timeline and decision flow for an executive audience.



Would you like me to generate a simplified, **executive-level one-page summary** of this exercise for a pre-briefing?