# MODULE C: SCREENING CLINICAL PROCESS MODEL

**IEEE P3493.1 Standard for Cancer Screening**
**Draft Version: 1.00**
**Date: 2026-02-02**
**Status: Complete with AI Integration (Clause 5.7)**

---

## Table of Contents

- [Clause 5.1: Ontological Foundation - Screening as Clinical Process](#clause-51-ontological-foundation-screening-as-clinical-process)
- [Clause 5.2: Screening Clinical Process - Stage-Based Workflow Model](#clause-52-screening-clinical-process-stage-based-workflow-model)
- [Clause 5.3: Conditional Episode Derivation and Linkage Patterns](#clause-53-conditional-episode-derivation-and-linkage-patterns)
- [Clause 5.4: Health State Transitions in Cancer Screening](#clause-54-health-state-transitions-in-cancer-screening)
- [Clause 5.5: Clinical Decision Points and Branching Logic](#clause-55-clinical-decision-points-and-branching-logic)
- [Clause 5.6: Temporal Requirements and Time Constraints](#clause-56-temporal-requirements-and-time-constraints)
- [Clause 5.7: AI and Automated Systems in Cancer Screening](#clause-57-ai-and-automated-systems-in-cancer-screening)

---

## CLAUSE 5.1 — ONTOLOGICAL FOUNDATION: SCREENING AS CLINICAL PROCESS

**NOTE on Terminology**: Throughout this standard, the term "healthcare professional" (ISO 13940:2015, 3.1.XX) refers to a healthcare actor qualified and authorized to perform the specific healthcare activity in question. Where qualification requirements are activity-specific, they are stated explicitly (e.g., "healthcare professional qualified to interpret mammography").

Cancer screening SHALL be modeled as a **clinical process** (ISO 13940:2015, 3.1.XX) consisting of structured **healthcare activities** (ISO 13940:2015, 3.1.XX) performed over time to achieve defined **health objectives** (ISO 13940:2015, 3.1.XX).

The screening clinical process SHALL NOT be modeled as a single **episode of care** (ISO 13940:2015, 3.1.38). Episodes of care are event-driven healthcare delivery containers with specific ownership, temporal boundaries, and closure conditions. Screening is an ongoing preventive process that may span multiple **contacts** (ISO 13940:2015, 3.1.XX), involve multiple **healthcare actors** (ISO 13940:2015, 3.1.XX), and operate within a **care period mandate** (ISO 13940:2015, 3.1.XX) without necessarily constituting an episode.

Episodes of care MAY be initiated conditionally as outcomes or derivatives of the screening clinical process when specific triggers occur, including but not limited to:
- Abnormal or indeterminate screening findings requiring diagnostic investigation
- Confirmed diagnosis requiring treatment planning
- Complex follow-up requiring specialized care coordination

When episodes of care are initiated as a result of screening process findings, they SHALL be linked to the screening clinical process via **health thread** (ISO 13940:2015, 3.1.XX) or equivalent linkage mechanisms to preserve traceability and continuity per Clause 5.3.

**NOTE 1**: This ontological distinction is critical for data governance, secondary use, and AI training. Screening process data represents preventive surveillance at population scale; episode data represents individualized care delivery. Conflating these concepts leads to semantic errors in data reuse and inappropriate consent assumptions.

**NOTE 2**: A single subject of care's screening history consists of a sequence of **condition evolution events** (ISO 13940:2015, 3.1.XX) documented within the screening clinical process, which may spawn zero or more episodes of care depending on findings.

---

## CLAUSE 5.2 — SCREENING CLINICAL PROCESS: STAGE-BASED WORKFLOW MODEL

### 5.2.1 Overview

The cancer screening clinical process consists of four normative stages, each representing a distinct phase of preventive healthcare delivery. These stages apply to all cancer types and screening modalities, with cancer-specific parameters defined in implementing guidelines (Module D).

Each stage consists of one or more **healthcare activities** (ISO 13940:2015, 3.1.XX) that advance the **subject of care** (ISO 13940:2015, 3.1.XX) through **condition evolution events** (ISO 13940:2015, 3.1.XX) toward defined **health objectives**.

Systems conforming to this standard SHALL support representation and documentation of all four stages and SHALL record stage transitions with timestamp and responsible healthcare professional identifier (qualified for the specific stage activity per 3.1.AD).

---

### 5.2.2 Stage 1: Screening Process Initiation and Eligibility Confirmation

**Stage Objective**: Establish that the subject of care meets criteria for cancer screening and obtain commitment to proceed.

**Stage Activities**:
- Healthcare needs assessment (risk evaluation, guideline applicability)
- Informed consent obtainment (per Module E)
- Care plan creation specifying screening modality and schedule
- **Healthcare commitment** (ISO 13940:2015, 3.1.XX) establishment by provider organization

**Stage Entry Conditions**:
- Subject identified as potentially eligible (age, risk factors, or symptomatic concern)
- Initial **contact** (ISO 13940:2015, 3.1.XX) established (may be in-person, telehealth, or asynchronous)

**Stage Exit Conditions and Transitions**:
- **To Stage 2**: Eligibility confirmed, consent obtained, screening appointment scheduled
- **To Process Termination**: Ineligible, declined consent, or contraindication identified

**Stage Metadata Requirements** (SHALL document):
- Process instance identifier (unique within implementing system)
- Subject of care identifier
- Initiating healthcare professional identifier (qualified to perform healthcare needs assessment)
- Input **health state** (3.1.Z): typically HS-01 (At-Risk) or HS-02 (Symptomatic Concern) per 5.4.2.1
- Applicable **core care plan** (3.1.AB) reference (guideline identifier)
- Consent documentation reference
- Stage initiation timestamp

**NOTE**: Stage 1 does NOT initiate an episode of care. It establishes a process instance within a broader **care period mandate** (ISO 13940:2015, 3.1.XX) for preventive screening.

---

### 5.2.3 Stage 2: Screening Investigation Execution and Result Generation

**Stage Objective**: Perform the screening procedure and capture interpretable data.

**Stage Activities**:
- Screening procedure execution (**healthcare investigation** per ISO 13940:2015, 3.1.XX)
  - Examples: mammography, colonoscopy, HPV test, low-dose CT
- Data capture (imaging, laboratory specimens, endoscopic findings)
- Technical quality verification
- Professional interpretation by qualified **healthcare professional** (3.1.AD)
- Result categorization using standardized systems (BI-RADS, Bethesda, etc.)

**Stage Entry Conditions**:
- Stage 1 completed successfully
- Subject of care presents for scheduled screening appointment (**contact**)

**Stage Exit Conditions and Transitions**:
- **To Stage 3**: Valid result obtained and interpreted
- **To Stage 2 (loop)**: Technical failure; repeat screening required
- **To Process Suspension**: Subject does not attend; outreach initiated

**Health State Transitions in Stage 2**:
- HS-01 or HS-02 → HS-03 (Screening in Progress) when procedure begins
- HS-03 → HS-04 (Results Pending Interpretation) when data captured
- HS-04 → HS-05 (Negative), HS-06 (Indeterminate), or HS-07 (Positive) when interpretation finalized

**Stage Metadata Requirements** (SHALL document):
- Screening modality code (LOINC or cancer-specific terminology)
- Procedure date and performing facility/professional
- Interpretation date and interpreting professional identifier
- Result categorization code (standardized system)
- Technical quality indicators
- Health state transition timestamps per 5.4.5

**NOTE**: Stage 2 activities occur within scheduled **contacts**. Multiple contacts may be required if repeat imaging or additional views are needed.

---

### 5.2.4 Stage 3: Result Communication and Follow-Up Action Determination

**Stage Objective**: Communicate results to subject of care and determine appropriate follow-up action.

**Stage Activities**:
- Result communication to subject via appropriate channel (phone, letter, patient portal, in-person)
- Shared decision-making for indeterminate or positive results
- Follow-up action determination per **clinical decision point** logic (5.5.4, 5.5.6)
  - Negative → recall scheduling
  - Indeterminate → short-interval follow-up scheduling
  - Positive → diagnostic referral or resulting episode initiation
- Care plan update with follow-up activities

**Stage Entry Conditions**:
- Stage 2 completed with valid interpretation

**Stage Exit Conditions and Transitions**:
- **To Stage 4**: Follow-up action determined and documented
- **To Stage 3 (suspension)**: Unable to reach subject; outreach attempts continue

**Stage Metadata Requirements** (SHALL document):
- Communication date, method, and content summary
- Subject acknowledgment (if obtained)
- Follow-up action code (recall / short-interval / diagnostic referral / resulting episode)
- Decision maker identifier
- Updated care plan reference

**Temporal Requirements**:
- T4 (negative results): Communication within 14 days (SHOULD)
- T5 (positive results): Communication within 5 business days (SHALL)
- T6 (indeterminate results): Communication within 10 days (SHOULD)

---

### 5.2.5 Stage 4: Process Transition Logic and Conditional Episode Derivation

**Stage Objective**: Complete the screening process instance or transition to resulting episodes based on findings.

**Stage Logic** (conditional branching):

**Branch 4A: Process Completion with Recall (Negative or Resolved Indeterminate)**
- **Condition**: HS-05 (No Abnormality Detected) or HS-06 resolved to benign
- **Actions**:
  - Output health state: HS-10 (Returned to Routine Screening)
  - Screening process status: Completed
  - Recall entry creation in screening management system (T10: within 7 days)
  - Next screening date calculated per **core care plan** interval
  - Discharge summary generated and communicated
- **Resulting Episodes**: None
- **Process Linkage**: This process instance closed; future screening will be new process instance with historical linkage via **health thread**

**Branch 4B: Conditional Diagnostic Episode Initiation (Positive Result – Pattern A)**
- **Condition**: HS-07 (Suspicious Abnormality) AND diagnostic services available within same organization
- **Actions**:
  - Output health state from screening process: HS-07 documented with observed condition details
  - Screening process status: Completed – diagnostic episode initiated
  - **NEW: Diagnostic episode of care initiated** per 5.3.3.1
    - Episode type: Diagnostic investigation
    - Episode linkage: References screening process instance ID via health thread
    - Episode care plan: Diagnostic activities (biopsy, advanced imaging, consultation)
    - Episode ownership: May transfer to specialist provider
  - Diagnostic episode progresses through health states HS-08 → HS-09 or HS-10
- **Resulting Episodes**: One diagnostic episode (conditionally initiated)
- **Eventual Outcomes**:
  - HS-09 (Cancer Confirmed) → NEW treatment episode initiated (outside scope of screening standard)
  - HS-10 (Cancer Excluded) → Return to screening recall per Branch 4A logic

**Branch 4C: Conditional Diagnostic Episode Initiation (Positive Result – Pattern B)**
- **Condition**: HS-07 (Suspicious Abnormality) AND diagnostic services external to screening organization
- **Actions**:
  - Output health state from screening process: HS-07 documented with observed condition details
  - Screening process status: Completed with referral
  - Referral documentation created (receiving provider, facility, timeframe)
  - Screening process closed (not suspended)
  - **NEW: Diagnostic episode of care initiated by receiving provider** per 5.3.3.2
    - Episode type: Diagnostic investigation
    - Episode linkage: Explicit reference to screening process instance ID and observed condition ID via health thread
    - Responsibility transfer: From screening program to receiving specialist (documented per Module E mandate transfer requirements)
  - Screening program continuity responsibility: Ends at referral completion confirmation
- **Resulting Episodes**: One diagnostic episode (conditionally initiated, owned by receiving provider)
- **Quality Tracking**: Screening program SHOULD track referral acceptance and diagnostic episode creation to monitor follow-up completion rates (T7, T8)

**Branch 4D: Process Suspension for Loss to Follow-Up**
- **Condition**: HS-07 (Positive) or HS-06 (Indeterminate) AND subject does not complete recommended follow-up despite outreach (T11: 90-180 days for standard findings; 30 days maximum for highly suspicious findings)
- **Actions**:
  - Output health state: HS-12 (Diagnostic Outcome Unknown)
  - Screening process status: Suspended – lost to follow-up
  - Outreach attempts documented (T12: minimum 3 attempts)
  - Process flagged for quality review
  - **For highly suspicious findings** (BI-RADS 5, highly suspicious colonoscopy mass, HSIL cervical cytology): Medical director review SHALL be triggered if subject remains non-responsive after 30 days
  - No resulting episode created (subject did not engage)
- **Re-engagement Logic**: If subject later re-engages, screening process MAY be resumed OR new process/episode initiated with linkage to incomplete prior process

**Stage 4 Metadata Requirements** (SHALL document):
- Process transition branch (4A / 4B / 4C / 4D)
- Output health state code and timestamp
- Resulting episode identifier(s) (if Branch 4B or 4C)
- Health thread linkage identifier(s)
- Responsibility transfer documentation (if Branch 4C)
- Process completion or suspension timestamp
- Quality flag (if Branch 4D)

---

### 5.2.6 Process Instance Lifecycle Summary

**Table 5.2-1: Screening Process Instance States**

| Process State | Definition | Typical Duration | Entry Condition | Exit Condition |
|---------------|------------|------------------|-----------------|----------------|
| **Initiated** | Process instance created; subject enrolled | Hours to days | Stage 1 complete | Stage 2 begins or termination |
| **Active – Screening Phase** | Subject undergoing screening activities | Days to weeks | Stage 2 entry | Stage 2 complete |
| **Active – Communication Phase** | Results available; communicating and planning | Days | Stage 3 entry | Stage 3 complete |
| **Transition** | Determining next action | Hours to days | Stage 4 entry | Branch 4A/B/C/D executed |
| **Completed – Recall** | Negative or benign; returned to recall cycle | Terminal state | Branch 4A | — |
| **Completed – Referral** | Referred out; diagnostic episode created | Terminal state | Branch 4C | — |
| **Completed – Diagnostic Episode Initiated** | Diagnostic episode active (Pattern A) | Terminal state for process; diagnostic episode continues | Branch 4B | Diagnostic episode closes separately |
| **Suspended – LTFU** | Lost to follow-up | Terminal (unless resumed) | Branch 4D | — |

**NOTE**: "Completed" process instances may spawn resulting episodes (Branch 4B, 4C). The screening process itself completes or suspends; episodes are separate constructs.

---

## CLAUSE 5.3 — CONDITIONAL EPISODE DERIVATION AND LINKAGE PATTERNS

### 5.3.1 Purpose and Scope

Per Clause 5.1, screening is modeled as a clinical process, not an episode of care. This clause specifies normative requirements for conditionally initiating **episodes of care** (ISO 13940:2015, 3.1.38) as outcomes of the screening clinical process when specific findings trigger diagnostic investigation or treatment planning.

This clause specifies:
- Triggers for conditional episode initiation (5.3.2)
- Episode linkage patterns (Pattern A and Pattern B) (5.3.3)
- Metadata requirements for traceability (5.3.4)
- Responsibility transfer rules (5.3.5)

---

### 5.3.2 Triggers for Conditional Episode Initiation

#### 5.3.2.1 Trigger T-DIAG: Diagnostic Investigation Required

A diagnostic episode of care SHALL be initiated when ALL of the following conditions are met:

a) Screening process has reached health state HS-07 (Suspicious Abnormality Detected) per 5.4.2.3

b) A **healthcare professional** (3.1.AD) has determined that diagnostic investigation is required per Decision Point 4 (5.5.6)

c) A **healthcare commitment** (ISO 13940:2015, 3.1.XX) has been made by a provider (internal or external) to perform diagnostic workup

d) Informed consent has been obtained for diagnostic procedures (if not already covered by initial screening consent per Module E)

e) A care plan has been created specifying diagnostic activities (biopsy, advanced imaging, specialist consultation)

The diagnostic episode SHALL be linked to the screening process instance via **health thread** (ISO 13940:2015, 3.1.XX) per 5.3.4.

**NOTE 1**: Indeterminate findings (HS-06) typically do NOT trigger diagnostic episode initiation. Short-interval follow-up for HS-06 remains within the screening process (new process instance or continuation, implementer choice).

**NOTE 2**: If diagnostic workup is performed immediately during the same contact as screening (e.g., biopsy of visible cervical lesion during colposcopy), implementers MAY model this as a single process OR as a rapid episode initiation within the same contact. Choice SHALL be documented in conformance statement.

---

#### 5.3.2.2 Trigger T-TX: Treatment Episode Required

A treatment episode of care SHALL be initiated when ALL of the following conditions are met:

a) Diagnostic workup has reached health state HS-09 (Cancer Confirmed) per 5.4.2.4

b) A healthcare professional has determined that cancer treatment is required

c) A healthcare commitment has been made by a treatment provider (oncology, surgery, radiation)

d) Treatment planning has been initiated

The treatment episode SHALL be linked to both:
- The diagnostic episode (if Pattern A was used)
- The originating screening process instance (via transitive health thread linkage)

**NOTE 3**: Treatment episodes are outside the scope of this screening-focused standard. Implementers SHALL specify treatment episode requirements separately, but linkage back to screening via health thread is essential for outcomes tracking and quality measurement.

---

### 5.3.3 Episode Linkage Patterns

Systems conforming to this standard SHALL support at least one of the following patterns for linking diagnostic episodes to screening processes. Systems MAY support both patterns.

#### 5.3.3.1 Pattern A: Co-Located Diagnostic Episode (Integrated Process)

**Use Case**: Diagnostic services are provided by the same organization or integrated delivery network that performed screening.

**Model**:
- Screening process completes with status "diagnostic episode initiated" (linkage maintained for tracking)
- Diagnostic episode of care is initiated with explicit linkage to screening process
- Diagnostic episode has its own:
  - Episode identifier (distinct from screening process ID)
  - Episode care plan (diagnostic activities)
  - Episode ownership (may transfer to specialist within same organization)
  - Episode temporal boundaries (initiation to diagnostic resolution)
- Screening process and diagnostic episode MAY share a common **health thread** identifier for continuity tracking
- Both constructs remain active until diagnostic resolution (HS-09 or HS-10)

**Closure Logic**:
- When diagnostic outcome is determined (HS-09 or HS-10):
  1. Diagnostic episode is closed per ISO 13940 episode closure requirements
  2. Screening process (already completed per Branch 4B) remains in completed status; subject either returns to screening recall (per Branch 4A logic if false positive) or treatment episode is initiated (if cancer confirmed per T-TX trigger)

**Metadata Requirements** (Pattern A):

| Metadata Element | Location | Requirement Level |
|------------------|----------|-------------------|
| Screening process instance ID | Diagnostic episode header | SHALL reference |
| Diagnostic episode ID | Screening process transition record | SHALL reference |
| Health thread ID | Both screening process and diagnostic episode | SHALL be identical or explicitly linked |
| Observed condition ID | Carried from screening process to diagnostic episode | SHALL preserve |
| Responsibility holder ID | Both constructs | MAY differ (specialist vs. screening program) |
| Temporal linkage | Diagnostic episode initiation timestamp SHALL be within T7 of screening result communication | SHALL comply with 5.6 |

**Advantages**: Single organizational view, easier care coordination, shared EHR.

**Disadvantages**: Requires organizational integration; may not fit fragmented care delivery models.

---

#### 5.3.3.2 Pattern B: Separate Linked Episodes with Responsibility Transfer

**Use Case**: Diagnostic services are provided by an external organization or specialist not integrated with screening program.

**Model**:
- Screening process is completed (not suspended) at the point of referral
  - Output health state: HS-07 documented with referral details
  - Screening process status: Completed with referral
  - Referral documentation created per 5.5.6
- Receiving provider initiates a NEW diagnostic episode of care with:
  - New episode identifier (owned by receiving provider)
  - Explicit linkage to screening process via health thread or referral tracking ID
  - New episode care plan (diagnostic activities)
  - Transferred responsibility (documented per Module E mandate transfer requirements)
- Screening program continuity responsibility ENDS at confirmed referral acceptance

**Linkage Mechanism**:
- SHALL use **health thread** (ISO 13940:2015, 3.1.XX) OR equivalent structured referral linkage
- Linkage SHALL be bidirectional: diagnostic episode references screening process, and screening process records referral to diagnostic episode (once created)
- Receiving provider SHALL confirm referral acceptance and episode creation within T7 timeframe (14 days per 5.6)

**Metadata Requirements** (Pattern B):

| Metadata Element | Location | Requirement Level |
|------------------|----------|-------------------|
| Screening process instance ID | Diagnostic episode header (receiving system) | SHALL reference |
| Referral tracking ID | Both screening process and diagnostic episode | SHALL be shared |
| Health thread ID | Both constructs | SHALL be shared or explicitly linked |
| Observed condition details | Transmitted from screening to receiving provider | SHALL include full description, imaging/pathology IDs |
| Responsibility transfer documentation | Both systems | SHALL document per Module E (transferring entity, receiving entity, transfer date, acceptance confirmation) |
| Referral acceptance confirmation | Returned to screening program | SHOULD be returned within T7 |
| Diagnostic outcome notification | Returned to screening program (if consent permits) | SHOULD be returned for quality tracking |

**Advantages**: Supports fragmented care delivery, respects organizational boundaries, enables specialist ownership.

**Disadvantages**: Requires robust interoperability, referral tracking systems, and explicit responsibility transfer documentation.

---

### 5.3.4 Metadata Requirements for Traceability

To support continuity of care, quality measurement, and secondary use (Module F), systems SHALL capture the following metadata for all conditionally initiated episodes:

**Table 5.3-1: Traceability Metadata Requirements**

| Metadata Element | Definition | Normative Level | ISO 13940 Reference |
|------------------|------------|-----------------|---------------------|
| **Process Instance ID** | Unique identifier of the screening process that triggered the episode | SHALL | 3.1.XX (clinical process) |
| **Episode ID** | Unique identifier of the conditionally initiated episode | SHALL | 3.1.38 (episode of care) |
| **Health Thread ID** | Linkage identifier connecting screening process, diagnostic episode, and (if applicable) treatment episode | SHALL | 3.1.XX (health thread) |
| **Trigger Code** | Code indicating which trigger initiated the episode (T-DIAG, T-TX) | SHALL | — |
| **Observed Condition ID** | Identifier of the specific observed condition (HS-07) that triggered diagnostic episode | SHALL for T-DIAG | 3.1.XX (observed condition) |
| **Linkage Pattern** | Code indicating Pattern A or Pattern B | SHALL | — |
| **Responsibility Transfer Record** | If Pattern B: documented transfer per Module E | SHALL for Pattern B | 3.1.XX (healthcare mandate transfer) |
| **Temporal Linkage Timestamp** | Timestamp of episode initiation relative to screening process milestones | SHALL | — |
| **Referring Professional ID** | Healthcare professional who made the referral or diagnostic decision | SHALL | 3.1.AD (healthcare professional) |
| **Receiving Provider/Organization ID** | Entity assuming responsibility for the episode (Pattern B) | SHALL for Pattern B | — |
| **Episode Outcome** | Final health state when episode closes (HS-09, HS-10, HS-12) | SHALL | 3.1.Z (output health state) |

This metadata SHALL be recorded in structured, machine-readable format per Module D information model requirements.

---

### 5.3.5 Responsibility Transfer Rules (Pattern B Only)

When Pattern B (Separate Linked Episodes) is used, responsibility for continuity of care transfers from the screening program to the receiving provider. The transfer SHALL be documented per the following requirements:

#### 5.3.5.1 Transferring Entity Responsibilities

The screening program or referring provider SHALL:

a) Create referral documentation including:
   - Subject of care demographics and contact information
   - Complete screening findings (observed condition details, imaging/pathology identifiers)
   - Recommended diagnostic actions per guideline
   - Urgency level (routine, expedited, urgent)
   - Screening process instance ID and health thread ID

b) Transmit referral to receiving provider via secure, auditable mechanism (electronic referral, structured message, or interoperable health record exchange)

c) Document the responsibility transfer with:
   - Transfer date and timestamp
   - Receiving provider/organization identifier
   - Confirmation of subject consent for referral (per Module E)

d) Attempt to obtain referral acceptance confirmation within T7 timeframe (14 days)

e) If referral is not accepted or subject does not engage with receiving provider: Resume screening program outreach responsibilities per 5.2.5 (lost to follow-up)

#### 5.3.5.2 Receiving Entity Responsibilities

The receiving provider or organization SHALL:

a) Confirm referral receipt and acceptance within 5 business days

b) Initiate diagnostic episode of care per ISO 13940 episode requirements

c) Link diagnostic episode to screening process via health thread or referral tracking ID per 5.3.4

d) Attempt to contact subject of care to schedule diagnostic procedures within T7 timeframe (14 days from referral)

e) Document diagnostic episode activities and outcomes

f) (SHOULD) Notify referring/screening program of diagnostic outcome for quality tracking purposes (subject to consent per Module E)

#### 5.3.5.3 Responsibility Gap Prevention

To prevent "falling through the cracks," systems SHOULD implement responsibility gap detection:

- If receiving provider does not confirm acceptance within 7 days: Alert to screening program
- If subject does not schedule diagnostic appointment within 21 days: Alert to both screening program and receiving provider
- If diagnostic episode is not created within 30 days: Screening program resumes outreach responsibility

These alerts support the T11/T12 lost-to-follow-up requirements (5.6).

---

### 5.3.6 Episode Closure After Diagnostic Resolution

When a diagnostic episode (Pattern A or B) reaches a definitive outcome, it SHALL be closed per ISO 13940 episode closure requirements. The closure SHALL document:

a) Output health state:
   - HS-09 (Cancer Confirmed): Diagnostic episode closed; treatment episode initiated (T-TX trigger)
   - HS-10 (Cancer Excluded / False Positive): Diagnostic episode closed; subject returned to screening recall schedule per Branch 4A
   - HS-12 (Diagnostic Outcome Unknown): Diagnostic episode closed incomplete (lost to follow-up)

b) Episode closure timestamp

c) Responsible healthcare professional at closure

d) Linkage to next step:
   - If HS-09: Reference to initiated treatment episode
   - If HS-10: Reference to screening recall entry (next screening date)
   - If HS-12: Documented as incomplete; quality flag raised

e) Communication to subject of care (SHALL confirm subject was informed of diagnostic outcome)

f) (Pattern B only) Outcome notification to referring screening program (if consent permits)

The closed diagnostic episode remains linked via health thread to the originating screening process for outcomes tracking and quality measurement per Module F.

---

## CLAUSE 5.4 — HEALTH STATE TRANSITIONS IN CANCER SCREENING

### 5.4.1 Overview and Relationship to ISO 13940

This clause specifies the health states (ISO 13940:2015, 3.1.XX) that SHALL be recognized and documented during cancer screening, and the normative rules governing transitions between these states.

A **health state** represents the condition of the subject of care at a specific point in time with respect to the health concern being addressed (in this case, presence or absence of cancer). Health states are distinct from:
- **Process status** (administrative state of the screening process, e.g., "initiated," "active," "completed")
- **Episode status** (administrative state of a resulting episode, e.g., "open," "closed")
- **Workflow state** (procedural state, e.g., "appointment scheduled," "specimen collected")

Systems conforming to this standard SHALL maintain and document health state information as specified in this clause. Each health state transition SHALL be recorded with timestamp and responsible healthcare professional identifier per 5.2.2 (Stage 1 metadata) and 5.3.4 (episode traceability metadata).

---

### 5.4.2 Normative Health State Enumeration

The following health states are defined for cancer screening processes and resulting episodes. Systems SHALL support representation and documentation of each state.

#### 5.4.2.1 Entry States (Process Initiation)

**HS-01: At-Risk (Asymptomatic)**
- **Definition**: Subject of care meets eligibility criteria for cancer screening based on risk factors (age, family history, genetic markers, prior history) but has no current symptoms suggesting cancer.
- **ISO 13940 alignment**: This represents a risk condition (ISO 13940:2015, 3.1.XX) rather than a diagnosed health condition.
- **Input to screening process**: This is the typical input health state when screening is provider-initiated.
- **Required documentation**: Risk factors justifying screening, applicable guideline reference.

**HS-02: Symptomatic Concern**
- **Definition**: Subject of care has symptoms or clinical findings that raise concern for possible cancer and prompt investigation.
- **ISO 13940 alignment**: This represents a health issue (ISO 13940:2015, 3.1.XX) identified by patient or provider.
- **Input to screening process**: This is the typical input health state when screening is patient-initiated or triggered by clinical findings.
- **Required documentation**: Symptom description, date of onset.
- **NOTE**: While this may trigger cancer investigation, if the clinical pathway follows screening protocols (rather than diagnostic protocols), it may still be categorized as a screening process.

#### 5.4.2.2 Active Screening States

**HS-03: Screening in Progress**
- **Definition**: Subject of care is actively undergoing screening procedures (imaging, laboratory testing, endoscopy, etc.) but results are not yet available.
- **Transition from**: HS-01 or HS-02 (after process initiation per 5.2.2)
- **Required documentation**: Screening modality, procedure date, performing provider/facility identifier.

**HS-04: Results Pending Interpretation**
- **Definition**: Screening procedure has been completed and raw data has been captured, but professional interpretation (e.g., radiologist reading, pathologist review) has not been finalized.
- **Transition from**: HS-03 (when procedure is complete)
- **Required documentation**: Procedure completion timestamp, data capture confirmation.

#### 5.4.2.3 Screening Outcome States

**HS-05: No Abnormality Detected (Negative Screen)**
- **Definition**: Screening results have been interpreted by qualified professional(s) and no evidence of cancer or significant pre-cancerous conditions has been identified.
- **Transition from**: HS-04 (when interpretation is finalized)
- **ISO 13940 alignment**: This is the output health state when screening is negative.
- **Required documentation**: Interpretation date, interpreting professional identifier, result communication date to subject of care.
- **Typical next state**: HS-10 (Returned to Routine Screening) upon process completion.

**HS-06: Indeterminate Finding**
- **Definition**: Screening results show an abnormality that is neither clearly benign nor clearly suspicious, requiring additional evaluation (typically short-interval follow-up imaging or repeat testing).
- **Transition from**: HS-04 (when interpretation is finalized)
- **Required documentation**: Description of indeterminate finding, recommended follow-up action, follow-up timeframe.
- **Examples**: BI-RADS 3 breast lesion (probably benign), small colorectal polyp requiring surveillance, ASC-US cervical cytology.
- **Typical next state**: May remain in HS-06 with repeated screening at shorter intervals, or transition to HS-05 (resolved as benign) or HS-07 (upgraded to suspicious).

**HS-07: Suspicious Abnormality Detected (Positive Screen)**
- **Definition**: Screening results show findings highly suggestive of cancer or high-grade pre-cancerous lesions, requiring diagnostic confirmation.
- **Transition from**: HS-04 or HS-06 (when interpretation is finalized or indeterminate finding is upgraded)
- **ISO 13940 alignment**: This represents an observed condition (ISO 13940:2015, 3.1.XX) requiring further investigation.
- **Required documentation**: Description of suspicious finding, result communication date to subject of care, referral or diagnostic plan documentation.
- **Typical next state**:
  - HS-08 (Diagnostic Workup in Progress) if Pattern A (co-located diagnostic episode) is used per 5.3.3.1
  - Health state HS-07 is documented as output of screening process; separate diagnostic episode is initiated (Pattern B per 5.3.3.2) with health state carried forward to new episode

#### 5.4.2.4 Diagnostic Resolution States (Resulting Episodes)

The following states apply when resulting diagnostic episodes are created:

**HS-08: Diagnostic Workup in Progress**
- **Definition**: Subject of care is undergoing diagnostic procedures (biopsy, advanced imaging, surgical consultation) to confirm or exclude malignancy within a resulting diagnostic episode.
- **Transition from**: HS-07 (when diagnostic episode is initiated per 5.3.2.1 Trigger T-DIAG)
- **Required documentation**: Diagnostic procedures planned/performed, dates, responsible providers.

**HS-09: Cancer Confirmed**
- **Definition**: Diagnostic evaluation has definitively established a cancer diagnosis (malignancy confirmed histologically or through other definitive diagnostic criteria).
- **Transition from**: HS-08 (when diagnostic confirmation is obtained)
- **ISO 13940 alignment**: This is a confirmed health condition (diagnosed disease).
- **Required documentation**: Diagnosis date, diagnostic method, cancer type and stage (if available), treating physician.
- **Typical next state**: HS-11 (Transitioned to Treatment) upon diagnostic episode closure per 5.3.6 and treatment episode initiation per 5.3.2.2 Trigger T-TX.

**HS-10: Cancer Excluded (False Positive)**
- **Definition**: Diagnostic evaluation has definitively ruled out malignancy; the initial positive screen was a false positive.
- **Transition from**: HS-08 (when diagnostic workup excludes cancer)
- **ISO 13940 alignment**: This represents exclusion of a suspected condition.
- **Required documentation**: Date of diagnostic resolution, method of exclusion, recommended follow-up screening interval.
- **Typical next state**: HS-10 (Returned to Routine Screening) upon diagnostic episode closure per 5.3.6.

**HS-12: Diagnostic Outcome Unknown (Lost to Follow-Up)**
- **Definition**: Subject of care with a positive or indeterminate screen did not complete recommended diagnostic workup despite outreach efforts per 5.2.5.
- **Transition from**: HS-07 (if lost before diagnostic workup) or HS-08 (if lost during diagnostic workup)
- **Required documentation**: Date of last contact, outreach attempts made, unresolved clinical questions.
- **Typical next state**: Process/episode suspended in incomplete status; may transition to any diagnostic state if subject re-engages.

#### 5.4.2.5 Exit States (Process Completion)

**HS-10: Returned to Routine Screening**
- **Definition**: Screening process has completed with subject of care returned to standard screening recall schedule (or diagnostic episode has concluded with false positive finding).
- **Applies to**: Process completion after HS-05 (negative screen) or diagnostic episode closure after HS-10 (false positive after diagnostic resolution) [note: same code, different context]
- **Required documentation**: Next recommended screening date, applicable guideline, any modifications to standard interval.

**HS-11: Transitioned to Cancer Treatment**
- **Definition**: Diagnostic episode has concluded with confirmed cancer diagnosis; subject of care has been referred to oncology/surgical services for treatment planning.
- **Applies to**: Diagnostic episodes closing after HS-09 (cancer confirmed) or treatment episodes (outside scope of this standard)
- **Required documentation**: Referral date, receiving provider/service, treatment planning status.

---

### 5.4.3 Health State Transition Rules

Systems SHALL enforce the following transition rules. Transitions not listed in Table 5.4-1 SHALL NOT be permitted without documented clinical justification.

**Table 5.4-1: Valid Health State Transitions**

| From State | To State(s) | Transition Condition | Normative Level | Notes |
|------------|-------------|----------------------|-----------------|-------|
| HS-01 (At-Risk) | HS-03 (Screening in Progress) | Screening process initiated per 5.2.2; screening appointment occurs | SHALL | Standard entry path for asymptomatic screening |
| HS-02 (Symptomatic) | HS-03 (Screening in Progress) | Screening process initiated per 5.2.2; screening/investigation appointment occurs | SHALL | Entry path for symptomatic presentation |
| HS-03 (Screening in Progress) | HS-04 (Results Pending) | Screening procedure completed; data captured | SHALL | Standard progression |
| HS-04 (Results Pending) | HS-05 (No Abnormality) | Professional interpretation: negative result | SHALL | Negative screen outcome |
| HS-04 (Results Pending) | HS-06 (Indeterminate) | Professional interpretation: unclear/borderline result | SHALL | Indeterminate screen outcome |
| HS-04 (Results Pending) | HS-07 (Suspicious Abnormality) | Professional interpretation: positive result | SHALL | Positive screen outcome |
| HS-05 (No Abnormality) | HS-10 (Returned to Routine) | Process completion per 5.2.5 (Branch 4A) | SHALL | Standard exit for negative screen |
| HS-06 (Indeterminate) | HS-03 (Screening in Progress) | Short-interval follow-up screening initiated | MAY | Repeat screening for indeterminate finding |
| HS-06 (Indeterminate) | HS-05 (No Abnormality) | Follow-up evaluation resolves as benign | MAY | Downgrade to negative |
| HS-06 (Indeterminate) | HS-07 (Suspicious Abnormality) | Follow-up evaluation shows progression or clearer abnormality | MAY | Upgrade to positive |
| HS-06 (Indeterminate) | HS-10 (Returned to Routine) | Process completion with short-interval recall plan | MAY | Close with recall at shorter interval |
| HS-07 (Suspicious Abnormality) | HS-08 (Diagnostic Workup) | Pattern A: Diagnostic episode initiated per 5.3.3.1 | SHALL | Co-located diagnostic episode path |
| HS-07 (Suspicious Abnormality) | HS-11 (Transitioned to Treatment) | Pattern B: Referral completed; screening process completed; diagnostic episode initiated by receiving provider per 5.3.3.2 | SHALL | Separate linked episode path (state carries to new episode) |
| HS-07 (Suspicious Abnormality) | HS-12 (Lost to Follow-Up) | Subject does not complete follow-up per 5.2.5 | MAY | Incomplete process |
| HS-08 (Diagnostic Workup) | HS-09 (Cancer Confirmed) | Diagnostic evaluation confirms malignancy | SHALL | Resulting diagnostic episode only |
| HS-08 (Diagnostic Workup) | HS-10 (Cancer Excluded) | Diagnostic evaluation excludes malignancy | SHALL | Resulting diagnostic episode only (false positive) |
| HS-08 (Diagnostic Workup) | HS-12 (Lost to Follow-Up) | Subject does not complete diagnostic workup per 5.2.5 | MAY | Resulting diagnostic episode only |
| HS-09 (Cancer Confirmed) | HS-11 (Transitioned to Treatment) | Diagnostic episode closure per 5.3.6; treatment episode initiated per 5.3.2.2 | SHALL | Pattern A or B exit to treatment |
| HS-10 (Cancer Excluded) | HS-10 (Returned to Routine) | Diagnostic episode closure per 5.3.6; return to standard screening recall | SHALL | Pattern A or B exit to screening (note: different contexts for HS-10) |
| HS-12 (Lost to Follow-Up) | HS-08 (Diagnostic Workup) | Subject re-engages; diagnostic evaluation resumes | MAY | Re-engagement path |
| HS-12 (Lost to Follow-Up) | (any diagnostic state) | Subject re-engages with new clinical information | MAY | Process/episode may be reopened or new linked episode created |

**NOTE 1**: HS-10 appears in two contexts: (1) as a diagnostic resolution state (cancer excluded after diagnostic workup), and (2) as an exit state (returned to routine screening). Context SHALL be documented in the health state metadata.

**NOTE 2**: Transitions from HS-07 depend on episode linkage pattern chosen per 5.3.3.

**NOTE 3**: All transitions SHALL be recorded with timestamp, responsible healthcare professional identifier, and supporting evidence (e.g., test result, pathology report) per 5.4.5.

---

### 5.4.4 Health State Transition Diagram

**Figure 5.4-1: Cancer Screening Health State Transitions**

The following diagram specifies the normative health state transition model. All conforming systems SHALL support the states and transitions depicted.

```
ENTRY STATES                    SCREENING PROCESS              SCREENING OUTCOMES
┌──────────────┐
│   HS-01:     │──┐
│   At-Risk    │  │
│(Asymptomatic)│  │
└──────────────┘  │              ┌──────────────┐            ┌──────────────┐
                  ├──────────────│    HS-03:    │───────────▶│    HS-04:    │
┌──────────────┐  │              │  Screening   │            │   Results    │
│   HS-02:     │──┘              │ in Progress  │            │   Pending    │
│ Symptomatic  │                 └──────────────┘            └──────┬───────┘
│   Concern    │                                                    │
└──────────────┘                                                    │
                                                             ┌──────┴──────┐
                                                             │             │
                                                             ▼             ▼
                                              ┌──────────────────┐  ┌─────────────────┐
                                              │     HS-05:       │  │     HS-06:      │
                                              │ No Abnormality   │  │  Indeterminate  │
                                              │   Detected       │  │    Finding      │
                                              │  (NEGATIVE)      │  │                 │
                                              └────────┬─────────┘  └────┬───┬────────┘
                                                       │                 │   │    ▲
                                                       │                 │   │    │
                                                       │                 │   └────┘
                                                       ▼                 ▼  (short-term
                                              ┌──────────────┐  ┌─────────────────┐ f/u)
                                              │    HS-10:    │  │     HS-07:      │
                                              │  Returned to │  │   Suspicious    │
                                              │   Routine    │  │  Abnormality    │
                                              │  Screening   │  │   (POSITIVE)    │
                                              └──────────────┘  └─────────┬───────┘
                                              [EXIT STATE]                │
                                                                          │
                         ┌────────────────────────────────────────────────┼──────────────┐
                         │                                                │              │
                         │     PATTERN A (Co-Located Diagnostic Episode)  │              │ PATTERN B
                         │                                                │              │ (Separate Linked Episodes)
                         ▼                                                ▼              ▼
         ┌─────────────────────────┐                     ┌─────────────────────────┐
         │         HS-08:          │                     │        HS-12:           │   Referral →
         │   Diagnostic Workup     │                     │   Lost to Follow-Up     │   New Episode
         │      in Progress        │                     │      (INCOMPLETE)       │   (state carries
         └────┬───────────────┬────┘                     └─────────────────────────┘   forward)
              │               │                          [EXIT STATE - INCOMPLETE]
              │               │
              ▼               ▼
    ┌──────────────────┐  ┌──────────────────┐
    │      HS-09:      │  │      HS-10:      │
    │     Cancer       │  │     Cancer       │
    │    Confirmed     │  │    Excluded      │
    │                  │  │ (False Positive) │
    └────────┬─────────┘  └─────────┬────────┘
             │                      │
             ▼                      ▼
    ┌──────────────────┐  ┌──────────────────┐
    │     HS-11:       │  │     HS-10:       │
    │  Transitioned to │  │   Returned to    │
    │    Treatment     │  │     Routine      │
    │                  │  │    Screening     │
    └──────────────────┘  └──────────────────┘
    [EXIT STATE]          [EXIT STATE]
```

**Legend:**
- Solid arrows (─▶): SHALL support transition
- Dashed arrows (- -▶): MAY support transition (conditional)
- Boxes: Health states (HS-XX codes)
- [EXIT STATE]: Terminal states leading to process/episode completion

---

### 5.4.5 Metadata Requirements for Health State Documentation

Each health state and each health state transition SHALL be documented with the following metadata:

**Table 5.4-2: Required Metadata for Health State Transitions**

| Metadata Element | Description | Data Type | Normative Level | ISO 13940 Reference |
|------------------|-------------|-----------|-----------------|---------------------| | Health State Code | Identifier for the health state (HS-01 through HS-12) | Code | SHALL | 3.1.XX (health state) |
| Health State Timestamp | Date and time when subject entered this health state | DateTime with timezone | SHALL | — |
| Previous Health State | Health state immediately prior to this transition (null for entry states) | Code | SHALL | — |
| Transition Reason | Clinical justification for the transition (e.g., "negative mammogram result") | Text | SHALL | — |
| Responsible Healthcare Professional | Identifier of healthcare professional qualified to make the clinical determination for this transition | Identifier | SHALL | 3.1.XX (healthcare professional) |
| Supporting Evidence | Reference to clinical data supporting the state determination (e.g., pathology report ID, imaging study ID) | Reference | SHOULD | — |
| Container Type | Indicates whether health state is documented within screening process or resulting episode | Code (PROCESS / EPISODE) | SHALL | — |
| Container Identifier | Unique identifier of the screening process instance OR resulting episode to which this health state belongs | Identifier | SHALL | — |
| Patient Communication Date | Date when the subject of care was informed of the health state (particularly for outcome states HS-05, HS-06, HS-07, HS-09, HS-10) | Date | SHALL for outcome states | — |

This metadata SHALL be captured in a structured, machine-readable format and SHALL be available for:
- Continuity of care across processes/episodes and providers
- Quality measurement and reporting
- Secondary use per Module F (subject to governance requirements)

---

### 5.4.6 Special Transition Scenarios

#### 5.4.6.1 Incidental Findings

If an incidental finding unrelated to the primary cancer being screened is discovered during screening, it SHALL NOT alter the health state of the primary screening process. Instead:

a) The incidental finding SHALL be documented as a separate observed condition

b) A new episode of care MAY be initiated to address the incidental finding

c) The new episode SHALL be linked to the screening process via health thread linkage per 5.3.4

d) The screening process health state SHALL continue to reflect only the primary cancer screening status

**Example**: A lung nodule discovered on CT colonography does not change the colorectal cancer screening health state.

#### 5.4.6.2 Interval Cancers (Detection Between Screening Rounds)

If a cancer is diagnosed in a subject of care during the interval between screening rounds (i.e., outside a screening process):

a) This SHALL be documented as an adverse event related to the prior screening process instance

b) The prior screening process health state SHALL NOT be retroactively changed

c) A new diagnostic or treatment episode SHALL be created for the cancer diagnosis, linked to the prior screening process via health thread per 5.3.4

d) Quality management processes per Module C.7 (to be drafted) SHALL analyze the interval cancer to determine if it represents:
   - A false negative screen (cancer present but not detected)
   - A new cancer arising after negative screen
   - A rapidly progressive cancer

#### 5.4.6.3 Multiple Screening Modalities in Same Process Instance

If multiple screening modalities are used within a single screening process instance (e.g., HPV test followed by Pap smear):

a) The health state SHALL reflect the most concerning result

b) Transitions SHALL be based on the integrated interpretation of all modalities

c) Each modality's result SHALL be documented separately but the health state SHALL be singular

---

### 5.4.7 Relationship to Process Status and Episode Status

Health states (per this clause), process status (per 5.2), and episode status (per 5.3) are related but distinct:

This clause distinguishes three related but distinct concepts:
- **Health state**: The clinical condition of the subject with respect to the health concern (cancer present/absent)
- **Process status**: The administrative state of the screening clinical process (initiated, active, completed, suspended)
- **Episode status**: The administrative state of a resulting episode of care (open, active, closed)

Systems SHALL maintain these concepts independently and SHALL NOT conflate them.

**Table 5.4-3: Health State vs. Process Status vs. Episode Status**

| Health State | Screening Process Status | Resulting Episode Status | Example Scenario |
|--------------|--------------------------|--------------------------|------------------|
| HS-01, HS-02 | Initiated | (none) | Screening process initiated after consent; no episode exists yet |
| HS-03, HS-04 | Active – Screening Phase | (none) | Screening procedure underway; still within process, no episode |
| HS-05 | Active – Communication Phase → Completed | (none) | Negative result communicated; process transitioning to completion |
| HS-05 → HS-10 | Completed | (none) | Process completed; recall scheduled; no episode created |
| HS-07 | Active – Communication Phase | (none yet) | Positive result; process active but episode not yet initiated |
| HS-07 → HS-08 | Completed – Diagnostic Episode Initiated | Diagnostic episode: Open/Active (Pattern A) | Diagnostic episode initiated within same organization; screening process completed |
| HS-07 | Completed (Pattern B) | Diagnostic episode: Open/Active (Pattern B, external provider) | Process completed with referral; diagnostic episode owned by receiving provider |
| HS-08 | (Process completed) | Diagnostic episode: Active (Pattern A) | Diagnostic workup in progress; screening process is already complete |
| HS-09 → HS-11 | Completed | Diagnostic episode: Closed; Treatment episode: Open (Pattern A or B) | Cancer confirmed; diagnostic episode closed; treatment episode initiated |
| HS-10 (false positive) | Completed | Diagnostic episode: Closed (Pattern A or B) | Cancer excluded; diagnostic episode closed; return to screening recall |
| HS-12 | Suspended – LTFU | Diagnostic episode: (may be incomplete/closed) | Lost to follow-up; process suspended without resolution |

**NOTE**: A single subject may have one active screening process and zero or more resulting episodes at any given time.

---

## CLAUSE 5.5 — CLINICAL DECISION POINTS AND BRANCHING LOGIC

### 5.5.1 Overview

This clause specifies the normative decision points in the cancer screening clinical process, the data required to inform each decision, the qualified roles authorized to make decisions, and the permissible decision outcomes.

A **clinical decision point** is a structured point in the care plan where a healthcare professional evaluates available clinical data and determines the next healthcare activity. Decision points are where branching logic is executed: the path forward depends on clinical findings and professional judgment.

Systems conforming to this standard SHALL:
a) Identify and document each decision point per this clause
b) Ensure required input data is available before a decision is made
c) Verify that decisions are made by appropriately qualified professionals
d) Record the decision, rationale, and resulting care plan modifications
e) Support decision audit and quality review

---

### 5.5.2 Cancer-Specific Screening Protocols

The decision points specified in this clause apply to cancer screening in general. Cancer-specific protocols (breast, colorectal, cervical, lung, prostate, etc.) SHALL specify:
a) The applicable core care plan (evidence-based guideline reference, e.g., USPSTF recommendation identifier)
b) Cancer-specific decision criteria and thresholds
c) Validated risk stratification models (if used)
d) Standard categorization systems (e.g., BI-RADS for breast imaging, Bethesda System for cervical cytology)

Implementers SHALL document which cancer-specific protocols are supported in their conformance statement (see Module G).

---

### 5.5.3 Decision Point 1: Screening Eligibility Determination

**Decision Question**: Should this subject of care undergo cancer screening for [specific cancer type]?

**Timing**: Prior to process initiation (during healthcare needs assessment)

**Table 5.5-1: Screening Eligibility Decision**

| Element | Specification | Normative Level |
|---------|--------------|-----------------| | **Required Input Data** | • Age<br>• Sex/gender (for sex-specific cancers)<br>• Family history of cancer<br>• Personal cancer history<br>• Genetic risk markers (if known)<br>• Prior screening history<br>• Current symptoms (if any)<br>• Applicable guideline reference | SHALL have at minimum: age, guideline reference<br><br>SHOULD have: family history, prior screening history |
| **Decision Maker** | Healthcare professional qualified to perform healthcare needs assessment (typically primary care physician, advanced practice provider, or specialized screening program coordinator) | SHALL |
| **Decision Criteria** | Per applicable core care plan (guideline):<br>• Age-based eligibility (e.g., 45-75 for colorectal)<br>• Risk-based eligibility (e.g., high-risk due to BRCA mutation)<br>• Interval since last screen<br>• Absence of contraindications | SHALL reference specific guideline criteria |
| **Permissible Outcomes** | 1. **Eligible – Standard Risk**: Screen per standard protocol<br>2. **Eligible – High Risk**: Screen with modified protocol (earlier start, shorter interval, or enhanced modality)<br>3. **Not Eligible – Outside Age Range**: Document rationale; MAY counsel on future eligibility<br>4. **Not Eligible – Recent Screen**: Document last screen date; schedule recall per interval<br>5. **Not Eligible – Contraindication**: Document contraindication; consider alternative approach<br>6. **Defer Decision**: Insufficient data; request additional information | SHALL document outcome code |
| **Required Documentation** | • Outcome (1-6 above)<br>• Guideline reference used<br>• Risk factors considered<br>• Rationale (especially for high-risk or ineligible outcomes)<br>• Decision date and decision maker identifier | SHALL |
| **Care Plan Impact** | • If Eligible (1 or 2): Initiate screening process per 5.2.2 (Stage 1); create care plan with screening modality and schedule<br>• If Not Eligible (3, 4, 5): Do not initiate screening process; document in patient record; may create recall reminder<br>• If Defer (6): Obtain additional data; repeat decision | SHALL |

**NOTE 1**: For patient-initiated screening requests, the healthcare professional's eligibility determination overrides the patient's self-assessment. If the professional determines the patient is not eligible, this SHALL be communicated to the patient with explanation.

**NOTE 2**: Shared decision-making conversations (particularly for screenings with significant tradeoffs) SHALL be documented, including patient preferences and consent per Module E.

---

### 5.5.4 Decision Point 2: Screening Modality Selection

**Decision Question**: Which screening modality/modalities should be used for this subject of care?

**Timing**: During care planning (after eligibility determination, before procedure scheduling)

**Table 5.5-2: Screening Modality Selection Decision**

| Element | Specification | Normative Level |
|---------|--------------|-----------------| | **Required Input Data** | • Cancer type being screened<br>• Risk level (standard vs. high-risk)<br>• Applicable core care plan (guideline)<br>• Patient preferences (if multiple options available)<br>• Contraindications to specific modalities (e.g., allergy, pregnancy)<br>• Resource availability (equipment, qualified professionals) | SHALL have: cancer type, risk level, guideline reference<br><br>SHOULD have: patient preferences, contraindications |
| **Decision Maker** | Healthcare professional with expertise in the cancer screening domain (e.g., primary care physician, radiologist, gastroenterologist, OB/GYN) | SHALL |
| **Decision Criteria** | Per applicable core care plan:<br>• Standard modality for cancer type (e.g., mammography for breast)<br>• Risk-adapted modality (e.g., MRI for BRCA carriers)<br>• Equivalent alternative modalities (e.g., colonoscopy vs. FIT for colorectal)<br>• Patient tolerance and adherence considerations | SHALL follow guideline-recommended modalities unless documented justification for deviation |
| **Permissible Outcomes** | 1. **Single Modality Selected**: One screening test (e.g., mammogram)<br>2. **Multiple Modalities – Sequential**: Primary test, with reflex to secondary if primary positive (e.g., FIT → colonoscopy if positive)<br>3. **Multiple Modalities – Concurrent**: Two or more tests done together (e.g., HPV + Pap co-testing)<br>4. **Alternative Modality**: Non-standard modality due to patient-specific factors (SHALL document justification) | SHALL document modality code(s) using standard terminology (LOINC, SNOMED CT, or cancer-specific codes) |
| **Required Documentation** | • Selected modality/modalities<br>• Risk-adaptation rationale (if high-risk protocol used)<br>• Alternative modality justification (if deviating from standard)<br>• Patient preference documentation (if patient chose between equivalent options)<br>• Decision date and decision maker identifier | SHALL |
| **Care Plan Impact** | • Care plan SHALL include selected modality<br>• If sequential modalities: care plan SHALL specify branching logic (e.g., "if FIT positive, schedule colonoscopy within 30 days")<br>• If alternative modality: care plan SHALL document expected deviation from standard protocol | SHALL |

**NOTE 3**: Some guidelines provide multiple equivalent screening options (e.g., annual FIT vs. colonoscopy every 10 years for average-risk colorectal screening). In these cases, patient preference is a valid decision input and SHALL be documented.

---

### 5.5.5 Decision Point 3: Screening Result Interpretation

**Decision Question**: What is the clinical interpretation of the screening test result?

**Timing**: After screening procedure completion and data capture (health state transition HS-04 → HS-05/06/07)

**Table 5.5-3: Result Interpretation Decision**

| Element | Specification | Normative Level |
|---------|--------------|-----------------| | **Required Input Data** | • Raw screening data (images, laboratory values, endoscopic findings, pathology specimens)<br>• Patient demographics and risk factors<br>• Prior screening results (for comparison)<br>• Technical quality indicators (e.g., adequate specimen, optimal imaging)<br>• Applicable interpretation standards (e.g., BI-RADS, Bethesda System) | SHALL have: raw data, technical quality confirmation, interpretation standard reference |
| **Decision Maker** | Healthcare professional qualified to interpret the specific screening modality:<br>• Radiologist for imaging<br>• Pathologist for cytology/histology<br>• Gastroenterologist for colonoscopy<br>• Laboratory physician for molecular/biomarker tests<br><br>May involve multiple professionals (e.g., double-reading mammograms) | SHALL be qualified professional per modality |
| **Decision Criteria** | Per applicable interpretation standards:<br>• Standardized categorization systems (cancer-specific)<br>• Quantitative thresholds (e.g., HPV viral load, PSA level)<br>• Visual/morphological assessment criteria<br>• Comparison with prior studies<br><br>Professional judgment within established frameworks | SHALL use standardized categorization system if available for the cancer type |
| **Permissible Outcomes** | **Mapped to Health States (5.4.2):**<br>1. **Negative** (HS-05): No abnormality detected<br>2. **Indeterminate** (HS-06): Unclear or borderline finding requiring follow-up<br>3. **Positive** (HS-07): Suspicious abnormality requiring diagnostic workup<br>4. **Unsatisfactory**: Technical quality insufficient for interpretation (requires repeat)<br><br>**With Cancer-Specific Categorization:**<br>• Breast (BI-RADS): 0 (incomplete), 1 (negative), 2 (benign), 3 (probably benign), 4 (suspicious), 5 (highly suggestive of malignancy), 6 (known malignancy)<br>• Cervical (Bethesda): Negative, ASC-US, ASC-H, LSIL, HSIL, etc.<br>• Colorectal: No polyps, adenomatous polyps (low/high-grade), suspicious mass, etc.<br>• Each mapped to outcomes 1-4 above | SHALL document using standardized terminology |
| **Required Documentation** | • Interpretation outcome (Negative/Indeterminate/Positive/Unsatisfactory)<br>• Cancer-specific category (if applicable)<br>• Descriptive findings (size, location, characteristics)<br>• Comparison with prior studies (if available)<br>• Interpreting professional identifier<br>• Interpretation date and timestamp<br>• Quality indicators (e.g., technical adequacy) | SHALL |
| **Care Plan Impact** | • **If Negative**: Proceed to process completion per 5.2.5 (Branch 4A); schedule routine recall<br>• **If Indeterminate**: Update care plan with short-interval follow-up; health state → HS-06; define follow-up timeframe and modality<br>• **If Positive**: Update care plan with diagnostic referral; health state → HS-07; initiate decision point 4<br>• **If Unsatisfactory**: Schedule repeat screening; document reason for inadequacy | SHALL update care plan within 1 business day of interpretation |

**NOTE 4**: Double-reading (two independent professionals interpreting the same study) is required by some protocols. If used, systems SHALL document both interpretations and the reconciliation process.

**NOTE 5**: AI-assisted interpretation is permitted if the AI system is appropriately validated and regulated (e.g., FDA-cleared for the specific use). The AI output is an input to professional interpretation, not a substitute. The qualified professional remains the decision maker and SHALL be documented as such.

---

### 5.5.6 Decision Point 4: Follow-Up Action Determination

**Decision Question**: What follow-up action is required based on the screening result?

**Timing**: Immediately after result interpretation (concurrent with decision point 3 or within 1 business day)

**Table 5.5-4: Follow-Up Action Decision**

| Element | Specification | Normative Level |
|---------|--------------|-----------------| | **Required Input Data** | • Screening result interpretation (from Decision Point 3)<br>• Cancer-specific guideline for follow-up (core care plan reference)<br>• Patient's ability to comply with follow-up (access, barriers)<br>• Episode pattern (A or B per 5.3.3) | SHALL have: result interpretation, guideline reference |
| **Decision Maker** | Healthcare professional responsible for result interpretation (may be same as Decision Point 3) OR referring provider (e.g., PCP)<br><br>May involve care coordinator for logistics | SHALL be qualified professional for clinical decision; care coordinator MAY support logistics |
| **Decision Criteria** | Per applicable core care plan and result interpretation:<br>• **Negative result**: Return to routine screening interval<br>• **Indeterminate result**: Short-interval follow-up per protocol (typically 3-6 months)<br>• **Positive result**: Diagnostic referral per protocol (typically 2-4 weeks)<br>• Adjust for patient-specific factors (e.g., high-risk may shorten intervals) | SHALL follow guideline-recommended follow-up unless documented justification |
| **Permissible Outcomes** | 1. **Routine Recall**: Schedule next screen per standard interval (e.g., 1 year, 5 years, 10 years)<br>2. **Short-Interval Follow-Up**: Schedule repeat screen in shorter timeframe (e.g., 6 months)<br>3. **Diagnostic Referral – Internal**: Refer within same organization (Pattern A likely)<br>4. **Diagnostic Referral – External**: Refer to outside specialist/facility (Pattern B likely)<br>5. **Immediate Diagnostic Procedure**: Proceed directly to diagnostic intervention (e.g., biopsy of visible cervical lesion during colposcopy)<br>6. **Repeat Screening**: Technical failure; repeat same screening test<br>7. **Patient Navigator Assignment**: Assign navigator to support adherence (particularly for underserved populations or complex cases) | SHALL document outcome code |
| **Required Documentation** | • Follow-up action (1-7 above)<br>• Timeframe (specific date or interval)<br>• Rationale (especially if deviating from standard protocol)<br>• Receiving provider/facility (for referrals)<br>• Communication to subject of care (date, method, content summary)<br>• Patient navigator assignment (if applicable)<br>• Decision date and decision maker identifier | SHALL document within 1 business day |
| **Care Plan Impact** | • Care plan SHALL be updated with follow-up activities<br>• Responsibilities SHALL be assigned (who will perform follow-up)<br>• Timeframes SHALL be specified<br>• If referral (outcomes 3 or 4): screening process transitions per 5.2.5 (Stage 4); diagnostic episode initiated per 5.3.3 (Pattern A or B)<br>• If recall (outcomes 1 or 2): screening process completion per 5.2.5 (Branch 4A) with recall entry created | SHALL |

**NOTE 6**: Time-critical follow-ups (e.g., highly suspicious findings) may require expedited communication and appointment scheduling. Systems SHOULD support priority flagging for such cases.

**NOTE 7**: Patient communication is a critical component of this decision point. The subject of care SHALL be informed of results and follow-up plan in a timely and understandable manner per 5.6 (temporal requirements).

---

### 5.5.7 Decision Point 5: Episode Linkage Pattern Selection (Positive Screens Only)

**Decision Question**: Should this positive screen be handled via Pattern A (co-located diagnostic episode) or Pattern B (separate linked episodes)?

**Timing**: When transitioning from positive screening result (HS-07) to diagnostic workup or referral

**Table 5.5-5: Episode Linkage Pattern Decision**

| Element | Specification | Normative Level |
|---------|--------------|-----------------| | **Required Input Data** | • Organizational structure (is diagnostic service within same organization?)<br>• Responsibility transfer requirements (is continuity responsibility transferring to another entity?)<br>• System capabilities (does system support co-located episodes?)<br>• Regulatory or administrative requirements | SHALL have: organizational structure, system capabilities |
| **Decision Maker** | Program administrator or care coordinator (administrative decision), informed by clinical context | MAY be administrative role |
| **Decision Criteria** | **Pattern A typically used when:**<br>• Diagnostic services are within the same organization<br>• Screening and diagnostic teams share same EHR system<br>• Continuity responsibility remains with screening program<br>• Example: Mammography center performs biopsies on-site<br><br>**Pattern B typically used when:**<br>• Diagnostic services are at external facility/provider<br>• Responsibility transfers to specialist<br>• Separate EHR systems require explicit linkage<br>• Example: Community health center refers positive FIT to hospital gastroenterology | SHOULD align pattern choice with organizational structure |
| **Permissible Outcomes** | 1. **Pattern A – Co-Located Diagnostic Episode**: Keep process active; add diagnostic episode with linkage to process; health state → HS-08 within diagnostic episode<br>2. **Pattern B – Separate Linked Episodes**: Complete process with referral documentation; initiate linked diagnostic episode via receiving provider; health state carries to new episode | Systems SHALL support at least one pattern; MAY support both |
| **Required Documentation** | • Pattern selected (A or B)<br>• Rationale for pattern choice<br>• Episode identifier (Pattern A: new episode ID with process linkage; Pattern B: new episode ID created by receiving provider with health thread reference)<br>• Responsibility transfer documentation (Pattern B per 5.3.5)<br>• Decision date and decision maker identifier | SHALL |
| **Care Plan Impact** | • **Pattern A**: Screening process is completed with diagnostic episode initiated; diagnostic episode is initiated per 5.3.3.1; new care plan is created for diagnostic activities within the episode; responsibility may transfer to specialist within same organization<br>• **Pattern B**: Screening process is completed; new diagnostic episode is initiated by receiving provider per 5.3.3.2; new care plan is created in linked episode; responsibility transfers per 5.3.5 and Module E | SHALL document per selected pattern |

**NOTE 8**: Organizations MAY establish a default pattern based on typical workflows, but systems SHALL support overriding the default when clinically or administratively appropriate.

---

### 5.5.8 Decision Audit and Quality Review

All decisions made at decision points 1-5 SHALL be auditable. Systems SHALL support:

a) **Decision Traceability**: Ability to retrieve all decision documentation for a given process instance or subject of care

b) **Decision Quality Metrics**:
   - Concordance with guidelines (% of decisions following recommended pathways)
   - Decision timeliness (time from data availability to decision documentation)
   - Outcome appropriateness (e.g., positive predictive value of screening decisions)

c) **Decision Review**: Ability for quality management personnel to review decisions for peer review, case conference, or quality improvement purposes

d) **Deviation Analysis**: Ability to identify and analyze cases where decisions deviated from standard protocols, to assess whether deviations were justified and to identify improvement opportunities

These capabilities support Module F (quality improvement) and are essential for program accreditation and regulatory compliance.

---

### 5.5.9 Decision Support Integration

Systems MAY integrate clinical decision support (CDS) tools to assist healthcare professionals at decision points. If CDS is used:

a) The CDS tool SHALL be clearly identified (name, version, vendor, regulatory status if applicable)

b) CDS recommendations are advisory; the healthcare professional remains the decision maker

c) The professional's decision SHALL be documented even if it differs from the CDS recommendation

d) If the professional overrides CDS advice, the rationale SHOULD be documented

e) CDS logic SHALL be based on evidence-based guidelines referenced in the core care plan

Systems claiming CDS support SHALL document the decision points where CDS is available and the types of CDS interventions provided (alerts, recommendations, risk calculations, etc.) in their conformance statement.

---

## CLAUSE 5.6 — TEMPORAL REQUIREMENTS AND TIME CONSTRAINTS

### 5.6.1 Overview and Purpose

This clause specifies normative time constraints for critical milestones in the cancer screening process. Temporal requirements serve multiple purposes:

a) **Patient Safety**: Ensures timely detection and intervention for cancer
b) **Quality of Care**: Maintains continuity and prevents loss to follow-up
c) **Regulatory Compliance**: Meets legal and accreditation standards
d) **Outcome Optimization**: Maximizes effectiveness of early detection

Systems conforming to this standard SHALL monitor temporal compliance and SHOULD generate alerts when timeframes are at risk of being exceeded.

**NOTE 1**: Temporal requirements specified here represent evidence-based or consensus-driven standards. Individual healthcare organizations MAY adopt more stringent timeframes but SHALL NOT exceed the maximum times specified for SHALL requirements.

**NOTE 2**: All temporal measurements SHALL use calendar days unless otherwise specified. "Business days" explicitly exclude weekends and recognized holidays.

---

### 5.6.2 Normative Temporal Requirements

**Table 5.6-1: Temporal Requirements for Cancer Screening Milestones**

| # | Milestone Description | Start Event | End Event | Maximum Allowed Time | Normative Level |
|---|----------------------|-------------|-----------|---------------------|-----------------|
| **T1** | **Screening Process Initiation After Consent** | Informed consent obtained | Screening process formally initiated (per 5.2.2) | 30 calendar days | SHOULD |
| **T2** | **Screening Appointment After Process Initiation** | Screening process initiated | Screening procedure performed | 90 calendar days | SHOULD<br><br>SHALL for high-risk cases |
| **T3** | **Result Interpretation After Procedure** | Screening procedure completed (data captured) | Professional interpretation documented | 7 calendar days for imaging/endoscopy<br><br>14 calendar days for laboratory/pathology | SHALL |
| **T4** | **Communication of Negative Results** | Interpretation finalized (negative result) | Subject of care notified | 14 calendar days | SHOULD |
| **T5** | **Communication of Positive Results** | Interpretation finalized (positive or highly suspicious result) | Subject of care notified | 5 business days | SHALL |
| **T6** | **Communication of Indeterminate Results** | Interpretation finalized (indeterminate result) | Subject of care notified | 10 calendar days | SHOULD |
| **T7** | **Diagnostic Referral After Positive Result** | Positive result communicated to subject | Diagnostic referral initiated (appointment offered or scheduled) | 14 calendar days | SHALL |
| **T8** | **Diagnostic Procedure After Referral** | Diagnostic referral accepted by receiving provider | Diagnostic procedure performed | 30 calendar days | SHOULD<br><br>SHALL for highly suspicious findings (e.g., BI-RADS 5) |
| **T9** | **Process Completion After Negative Result** | Negative result communicated to subject | Screening process completed (per 5.2.5 Branch 4A) | 30 calendar days | SHOULD |
| **T10** | **Recall Entry Creation After Completion** | Screening process completed (negative or false positive) | Next screening recall entry created in system | 7 calendar days | SHALL |
| **T11** | **Lost-to-Follow-Up Observation Period** | Recommended follow-up action communicated (positive or indeterminate result) | Screening process suspended as lost-to-follow-up per 5.2.5 Branch 4D (if subject does not engage) | **Standard findings**: Minimum 90 days, maximum 180 days<br><br>**Highly suspicious findings**: Maximum 30 days with medical director review | SHALL (minimum observation for standard findings)<br><br>SHALL (medical director review for highly suspicious findings by 30 days) | Balances patient autonomy with program accountability; highly suspicious findings require escalated intervention | Duration between communication date and process suspension date for lost-to-follow-up cases |
| **T12** | **Outreach Attempts During Observation Period** | Recommended follow-up communicated | Each documented outreach attempt | Minimum: 3 attempts over observation period<br><br>Frequency: at least every 30 days | SHALL |
| **T13** | **Decision Documentation Timeliness** | Clinical decision made (at any decision point per 5.5) | Decision documented in system | 1 business day | SHALL |
| **T14** | **Care Plan Update After Decision** | Clinical decision documented | Care plan updated to reflect decision | 1 business day | SHALL |
| **T15** | **Diagnostic Episode Closure After Resolution (Pattern A)** | Diagnostic outcome determined (cancer confirmed or excluded) | Diagnostic episode formally closed (per 5.3.6) | 30 calendar days | SHOULD |
| **T16** | **Health State Transition Documentation** | Health state transition occurs (per 5.4) | Health state transition documented in system | Same business day | SHALL |
| **T17** | **Metadata Completeness After Completion** | Screening process completed or episode closed (any reason) | All required metadata per 5.2.2, 5.3.4, and 5.4.5 documented and validated | 7 calendar days | SHALL |
| **T18** | **Interval Between Routine Screens** | Previous screening process completed (negative result) | Next scheduled screening process (per guideline) | Per applicable core care plan (e.g., 1 year for annual mammography, 10 years for colonoscopy) | SHALL follow guideline<br><br>MAY adjust based on risk |

**NOTE 1**: Rationale for temporal requirements and measurement methods are specified in Module D (Information Model & Data Elements).

**NOTE 2**: All temporal measurements SHALL use calendar days unless otherwise specified. "Business days" explicitly exclude weekends and recognized holidays.

---

### 5.6.3 Temporal Monitoring and Alerts

Systems conforming to this standard SHALL implement temporal monitoring capabilities:

#### 5.6.3.1 Real-Time Tracking

Systems SHALL track the elapsed time for all active temporal requirements (T1-T18 where applicable to active screening processes and open resulting episodes) and SHALL make this information accessible to:
- Care coordinators and patient navigators
- Quality management personnel
- Clinical managers

#### 5.6.3.2 Alert Generation

Systems SHOULD generate proactive alerts when temporal thresholds are at risk:

**Table 5.6-2: Recommended Alert Thresholds**

| Temporal Requirement | Alert Trigger (% of maximum allowed time) | Alert Recipient | Alert Priority |
|---------------------|------------------------------------------|-----------------|----------------| | T5 (Positive result communication) | 60% (3 business days) | Radiologist/interpreting provider, care coordinator | HIGH |
| T7 (Diagnostic referral) | 70% (10 days) | Care coordinator, referring provider | HIGH |
| T11 (Lost-to-follow-up observation) | 50% (45 days) and 80% (72 days) | Patient navigator, care coordinator | MEDIUM → HIGH |
| T13 (Decision documentation) | End of business day | Decision maker | HIGH |
| T3 (Result interpretation) | 70% (5 days for imaging) | Interpreting provider, department manager | MEDIUM |

Alerts MAY be delivered via system notifications, email, SMS, or integrated into clinical workflow tools.

#### 5.6.3.3 Temporal Compliance Reporting

Systems SHALL support generation of temporal compliance reports showing:
- Percentage of processes/episodes meeting each temporal requirement (T1-T18)
- Average time to milestone (with standard deviation)
- Outlier cases exceeding maximum allowed times
- Trend analysis over time (e.g., quarterly)

These reports support quality improvement initiatives and accreditation requirements.

---

### 5.6.4 Exceptions and Extensions

#### 5.6.4.1 Patient-Initiated Delays

If a subject of care explicitly requests to delay a scheduled activity (e.g., postpone a biopsy for personal reasons), this SHALL be documented, and the temporal requirement clock MAY be reset from the new agreed-upon date. However:

a) The original timeframe violation SHALL still be tracked for quality metrics (as "patient-initiated delay")
b) The healthcare provider SHALL counsel the patient on risks of delay
c) Patient acknowledgment of risks SHOULD be documented

#### 5.6.4.2 System or Provider Unavailability

If a temporal requirement cannot be met due to system unavailability (e.g., equipment failure, disaster, pandemic-related closure), this SHALL be documented as an exception with:
- Reason for delay
- Impact on patient(s)
- Mitigation actions taken
- Revised timeline

Such exceptions SHALL be reviewed by quality management to assess program resilience and contingency planning.

#### 5.6.4.3 High-Risk or Urgent Cases

For cases with heightened clinical urgency (e.g., BI-RADS 5 breast mass, large obstructing colorectal mass), healthcare professionals MAY designate a case as "expedited." When designated:

a) Temporal requirements SHALL use the more stringent timeframes specified in Table 5.6-1 (e.g., T2 and T8 become SHALL instead of SHOULD)
b) Systems SHOULD provide expedited appointment scheduling capabilities
c) Care coordinators SHALL prioritize expedited cases

---

### 5.6.5 Temporal Requirements and Episode Linkage Patterns

Temporal requirements interact with episode linkage patterns (5.3.3):

**Pattern A (Co-Located Diagnostic Episode):**
- Temporal requirements span the screening process and the resulting diagnostic episode
- T7 and T8 apply to the diagnostic episode (which is linked to the screening process per 5.3.3.1)
- T15 governs diagnostic episode closure after resolution

**Pattern B (Separate Linked Episodes with Responsibility Transfer):**
- Temporal requirements T1-T10 apply to the screening process
- Temporal requirements for the diagnostic episode apply per receiving provider's policies (outside scope of this screening-focused standard, but MAY be specified in a companion diagnostic standard)
- T7 still applies: referral initiation from screening process completion to diagnostic episode initiation SHALL occur within 14 days

Regardless of pattern, the temporal requirement for communication to the subject of care (T5, T6) and referral initiation (T7) SHALL be met.

---

### 5.6.6 Relationship to External Standards and Regulations

Temporal requirements in this clause are informed by:
- Clinical guidelines (e.g., NCCN, USPSTF recommendations)
- Accreditation standards (e.g., ACR accreditation for breast imaging centers)
- Regulatory requirements (e.g., Mammography Quality Standards Act for communication timelines)
- Patient safety organizations' consensus standards

Where external standards specify more stringent timeframes than those in Table 5.6-1, implementers SHALL comply with the more stringent requirement and SHOULD document this in their conformance statement.

**NOTE 3**: This standard's temporal requirements are minimum expectations for quality care. They do not preempt more stringent legal or regulatory requirements.

---

## CLAUSE 5.7 — AI AND AUTOMATED SYSTEMS IN CANCER SCREENING

### 5.7.1 Overview and Ontological Foundation

This clause specifies normative requirements for integrating artificial intelligence (AI) and automated systems into the cancer screening clinical process, aligned with ISO 13940:2015 concepts.

Per ISO 13940:2015, **automated healthcare** is defined as "method of delivering healthcare initiated by a responsible healthcare actor and thereafter delivered automatically by an automatic medical device" (contsys.org/concept/automated_healthcare). This definition establishes two critical principles:

a) **Initiation Accountability**: Automated healthcare must be initiated during exactly one healthcare activity by a responsible healthcare actor

b) **Professional Responsibility**: The initiating healthcare actor remains accountable for safe operation; the automatic medical device cannot bear responsibility

An **automatic medical device** (ISO 13940:2015, contsys.org/concept/medical_device) is a "medical device capable of performing automated healthcare activities." In the context of AI-enabled cancer screening, this includes:
- AI-based image analysis systems (mammography CAD, lung nodule detection, colonoscopy polyp detection)
- Machine learning risk prediction models
- Natural language processing for pathology report analysis
- Automated eligibility identification systems
- Clinical decision support systems with algorithmic recommendations

**NOTE 1**: AI outputs that have not been validated by a healthcare professional constitute **non-ratified healthcare information** (ISO 13940:2015, 3.1.5.5) until professional review occurs. This distinction is critical for data governance and clinical accountability.

---

### 5.7.2 AI Use Cases in Cancer Screening Workflow

The following AI use cases are recognized within the cancer screening clinical process. Systems implementing AI SHALL document which use cases are supported in their conformance statement (Module G).

#### 5.7.2.1 Population Identification and Eligibility (Stage 1)

**Use Case AI-01: Automated Eligibility Identification**

AI systems MAY analyze electronic health record (EHR) data to identify subjects of care who meet screening eligibility criteria based on:
- Age and demographic factors
- Risk factors documented in medical history
- Family history of cancer
- Genetic test results
- Interval since last screening
- Absence of documented contraindications

**Workflow Integration**:
- AI output: List of potentially eligible subjects with risk stratification
- Professional review: Healthcare professional validates eligibility per Decision Point 1 (5.5.3)
- AI output status: Non-ratified healthcare information until professional validation

**Table 5.7-1: AI-01 Integration Requirements**

| Element | Specification | Normative Level |
|---------|---------------|-----------------|
| AI Input Data | EHR demographic, clinical, and historical data | SHALL be documented |
| AI Output Format | Structured list with eligibility score/rationale | SHOULD use standardized format |
| Professional Validation | Healthcare professional SHALL review and approve/reject each AI-identified subject | SHALL |
| Documentation | AI system identifier, version, and recommendation SHALL be recorded | SHALL |
| Override Documentation | If professional disagrees with AI recommendation, rationale SHOULD be documented | SHOULD |

---

#### 5.7.2.2 Risk Stratification (Stage 1 / Decision Point 1)

**Use Case AI-02: AI-Assisted Risk Prediction**

AI systems MAY predict cancer risk using mammogram image analysis, genetic data, or multivariate risk models to stratify subjects into risk categories (standard-risk vs. high-risk).

**Examples**:
- AI analysis of mammographic density and tissue patterns to predict 5-year breast cancer risk
- Polygenic risk score integration for personalized screening intervals
- Multi-cancer early detection (MCED) test result interpretation

**Workflow Integration**:
- AI output: Risk score, risk category, and contributing factors
- Professional review: Healthcare professional incorporates AI risk assessment into eligibility determination
- Care plan impact: High-risk classification may trigger modified screening protocol per 5.5.3

**Accountability**: The healthcare professional making the eligibility and risk stratification decision (Decision Point 1) remains accountable for the determination, even when AI assists.

---

#### 5.7.2.3 Image Interpretation Assistance (Stage 2 / Decision Point 3)

**Use Case AI-03: AI-Assisted Image Interpretation**

AI systems MAY assist qualified healthcare professionals in interpreting screening images by:
- Detecting and highlighting regions of interest (computer-aided detection / CADe)
- Providing preliminary characterization of detected abnormalities (computer-aided diagnosis / CADx)
- Comparing current images to prior studies
- Assessing image quality and technical adequacy
- Triaging cases by urgency (prioritizing suspicious findings for immediate review)

**Table 5.7-2: AI-Assisted Interpretation by Modality**

| Screening Modality | AI Capabilities | FDA/Regulatory Examples | Stage Integration |
|-------------------|-----------------|------------------------|-------------------|
| Mammography | Lesion detection, density assessment, risk prediction, triage | FDA-cleared CAD systems (e.g., iCAD, Hologic Genius AI) | Stage 2 (5.2.3) |
| Low-dose CT (Lung) | Nodule detection, volumetric measurement, malignancy probability | FDA-cleared lung CAD systems | Stage 2 (5.2.3) |
| Colonoscopy | Real-time polyp detection, polyp characterization | FDA-cleared GI AI systems | Stage 2 (5.2.3) |
| Cervical Cytology | Cell classification, slide prioritization | Hologic Genius Digital Diagnostics | Stage 2 (5.2.3) |
| Pathology | Tissue classification, metastasis detection | Paige Prostate, Paige Lymph Node | Stage 2 (diagnostic phase) |

**Workflow Models**:

**Model A: AI as Second Reader (Concurrent)**
- Qualified professional interprets images independently
- AI provides parallel analysis
- Discordance triggers review/reconciliation
- Professional makes final interpretation

**Model B: AI as Pre-Reader (Triage)**
- AI analyzes all images first
- AI triages into categories (e.g., likely negative, needs review, suspicious)
- Professional reviews all AI-flagged cases; MAY use expedited review for AI-negative cases
- Professional makes final interpretation

**Model C: AI as Detection Aid (Real-Time)**
- AI provides real-time detection during procedure (e.g., colonoscopy polyp detection)
- Professional receives immediate alerts during procedure
- Professional makes all clinical decisions

**Accountability Requirements**:
- The qualified healthcare professional (radiologist, pathologist, gastroenterologist) SHALL be the documented decision maker for result interpretation per Decision Point 3 (5.5.5)
- AI output constitutes non-ratified healthcare information until professional interpretation is documented
- The professional's interpretation is the authoritative result; AI output is supporting information

---

#### 5.7.2.4 Follow-Up Determination Support (Stage 3 / Decision Point 4)

**Use Case AI-04: AI-Assisted Follow-Up Recommendations**

AI systems MAY provide recommendations for follow-up actions based on:
- Interpretation results and standardized categorization (e.g., BI-RADS category)
- Applicable clinical guidelines (core care plan)
- Subject-specific risk factors
- Prior screening history and outcomes

**Workflow Integration**:
- AI output: Recommended follow-up action and timeframe
- Professional review: Healthcare professional validates recommendation per Decision Point 4 (5.5.6)
- Care plan update: Professional-approved recommendation is incorporated into care plan

---

#### 5.7.2.5 Quality Assurance and Monitoring

**Use Case AI-05: AI-Assisted Quality Monitoring**

AI systems MAY monitor screening program quality by:
- Tracking temporal compliance with requirements (T1-T18 per 5.6)
- Identifying patterns of false negatives or interval cancers
- Analyzing radiologist/pathologist performance metrics
- Detecting anomalies in workflow or outcomes

**Workflow Integration**:
- AI output: Quality metrics, alerts, and pattern analysis
- Quality management review: Quality personnel review AI-identified issues
- Improvement actions: Program improvements based on validated AI findings

---

#### 5.7.2.6 Patient Navigation and Outreach

**Use Case AI-06: AI-Assisted Patient Navigation**

AI systems MAY support patient navigation by:
- Predicting risk of loss to follow-up based on demographic and behavioral factors
- Optimizing outreach timing and communication channels
- Generating personalized communication content
- Prioritizing navigator caseloads

**Workflow Integration**:
- AI output: Risk scores and recommended interventions
- Navigator review: Patient navigator incorporates AI insights into outreach strategy
- Documentation: Navigation activities and outcomes recorded per 5.2.5 (Branch 4D)

---

### 5.7.3 AI Integration at Clinical Decision Points

AI systems MAY provide decision support at each clinical decision point defined in 5.5. The following table specifies integration requirements:

**Table 5.7-3: AI Integration by Decision Point**

| Decision Point | AI Use Cases | AI Role | Professional Accountability | Documentation Requirements |
|---------------|--------------|---------|---------------------------|---------------------------|
| **DP1: Eligibility** (5.5.3) | AI-01, AI-02 | Identifies candidates; stratifies risk | Professional validates eligibility and risk determination | AI recommendation, professional decision, concordance/override |
| **DP2: Modality Selection** (5.5.4) | AI-02 | May recommend modality based on risk factors | Professional selects modality | AI recommendation (if provided), professional selection |
| **DP3: Result Interpretation** (5.5.5) | AI-03 | Detection, characterization, triage | Professional interprets and categorizes result | AI findings, professional interpretation, concordance |
| **DP4: Follow-Up Determination** (5.5.6) | AI-04 | Recommends follow-up per guidelines | Professional determines follow-up action | AI recommendation, professional decision |
| **DP5: Episode Pattern** (5.5.7) | (Administrative, typically not AI-assisted) | N/A | Administrative role | N/A |

---

### 5.7.4 Governance and Accountability Requirements

#### 5.7.4.1 Human Oversight Principle

Per ISO 13940:2015 (automated_healthcare concept), automated healthcare cannot bear responsibility; the responsible healthcare actor remains accountable. This principle SHALL be implemented as follows:

a) **AI-Assisted Decisions**: When AI provides recommendations that inform clinical decisions, a qualified healthcare professional SHALL be the documented decision maker

b) **AI Outputs as Non-Ratified Information**: Until a healthcare professional reviews and validates AI output, it constitutes non-ratified healthcare information (3.1.5.5) and SHALL NOT be the basis for clinical action

c) **Override Documentation**: When a healthcare professional disagrees with AI recommendations, the professional's decision takes precedence; the rationale for override SHOULD be documented

d) **Accountability Chain**: For each automated healthcare activity, the system SHALL identify:
   - The initiating healthcare actor
   - The automatic medical device (AI system identifier and version)
   - The reviewing healthcare professional (if applicable)

---

#### 5.7.4.2 AI System Documentation Requirements

Systems implementing AI in cancer screening SHALL document:

**Table 5.7-4: Required AI System Documentation**

| Documentation Element | Description | Normative Level |
|----------------------|-------------|-----------------|
| AI System Identifier | Unique identifier for the AI system (name, manufacturer) | SHALL |
| Version Information | Software version, model version, training data version | SHALL |
| Regulatory Status | FDA clearance/approval number, CE marking, other regulatory status | SHALL |
| Intended Use Statement | Manufacturer's intended use and indications | SHALL |
| Integration Points | Which decision points (DP1-DP5) the AI supports | SHALL |
| Workflow Model | How AI is integrated (second reader, pre-reader, real-time) | SHALL |
| Performance Metrics | Sensitivity, specificity, PPV as validated in clinical context | SHOULD |
| Limitations | Known limitations, contraindications, populations not validated | SHOULD |
| Update History | Log of AI model updates and version changes | SHALL |
| Per-Patient Version Record | Specific AI model version used for each subject's screening interpretation, recorded in subject's health record | SHALL |

---

#### 5.7.4.3 Transparency Requirements

Systems SHALL support transparency of AI involvement:

a) **Subject of Care Notification**: Subjects of care SHOULD be informed when AI is used in their screening process (per informed consent requirements in Module E)

b) **Result Reporting**: Reports generated with AI assistance SHOULD indicate that AI was used (e.g., "AI-assisted interpretation performed")

c) **Audit Trail**: All AI recommendations and professional responses SHALL be recorded in auditable format

d) **Explainability**: Where feasible, AI systems SHOULD provide explainable outputs (e.g., highlighting regions of interest, listing contributing factors) to support professional review

---

#### 5.7.4.4 Performance Monitoring and Continuous Improvement

Organizations deploying AI in cancer screening SHALL implement ongoing performance monitoring:

a) **Concordance Tracking**: Monitor agreement rates between AI recommendations and professional decisions

b) **Outcome Correlation**: Track clinical outcomes (true positive, false positive, false negative, true negative) for AI-assisted vs. non-AI-assisted interpretations

c) **Bias Detection**: Organizations SHALL monitor for disparities in AI performance across demographic groups (age, race, ethnicity, breast density, etc.) and SHALL report significant disparities (>10 percentage point delta in sensitivity or specificity between demographic groups) to quality management for corrective action

d) **Version Validation**: When AI model versions are updated, validate performance in local context before full deployment

e) **Adverse Event Reporting**: Report AI-related adverse events per applicable regulatory requirements (FDA MDR, EU vigilance)

---

### 5.7.5 AI-Specific Health State Considerations

#### 5.7.5.1 Non-Ratified Information State

When AI generates outputs that have not yet been reviewed by a healthcare professional, the subject of care's health state with respect to that AI output is effectively "pending professional validation." This is analogous to health state HS-04 (Results Pending Interpretation) but specifically for AI-generated findings.

Systems MAY implement an explicit sub-state:
- **HS-04a: AI Analysis Complete, Professional Review Pending**

This sub-state SHALL transition to HS-05, HS-06, or HS-07 only after professional interpretation is documented.

---

#### 5.7.5.2 AI-Detected Incidental Findings

If AI detects incidental findings (abnormalities unrelated to the primary cancer being screened):

a) The AI finding SHALL be flagged for professional review

b) The professional SHALL determine clinical significance

c) If clinically significant, a new health issue MAY be documented and addressed per 5.4.6.1 (Incidental Findings)

d) The primary screening health state SHALL NOT be altered by incidental findings

---

### 5.7.6 Regulatory Alignment

#### 5.7.6.1 FDA Regulatory Requirements (United States)

AI systems used in cancer screening in the United States SHALL comply with FDA requirements:

a) **Device Classification**: AI software for cancer screening is typically classified as Class II (510(k)) or Class III (PMA) medical device

b) **Intended Use**: AI systems SHALL be used only within their FDA-cleared intended use

c) **Predetermined Change Control Plan (PCCP)**: For AI systems with FDA-authorized PCCPs, model updates within the PCCP scope may be deployed without additional clearance

d) **Post-Market Surveillance**: Organizations SHALL comply with adverse event reporting (MDR) requirements

---

#### 5.7.6.2 EU Regulatory Requirements (European Union)

AI systems used in cancer screening in the EU SHALL comply with:

a) **Medical Device Regulation (MDR)**: AI software is typically Class IIa or IIb medical device

b) **EU AI Act**: Medical AI is classified as "high-risk" under the AI Act, requiring:
   - Risk management system
   - Data governance
   - Technical documentation
   - Transparency obligations
   - Human oversight measures
   - Accuracy and robustness

c) **Effective Dates**: AI Act obligations for high-risk medical AI systems apply from August 2027

---

#### 5.7.6.3 Alignment with IEEE Standards

Systems implementing AI in cancer screening SHOULD align with emerging IEEE standards:

a) **IEEE P2801**: Recommended Practice for the Quality Management of Datasets for Medical Artificial Intelligence

b) **IEEE P2802**: Standard for Performance and Safety Evaluation of Artificial Intelligence Based Medical Devices: Terminology

c) **IEEE P2817**: Guide for Verification of Autonomous Systems

---

### 5.7.7 AI-Specific Temporal Considerations

When AI is integrated into the screening workflow, the following temporal considerations apply:

**Table 5.7-5: AI-Related Temporal Requirements**

| # | Milestone | Maximum Time | Normative Level | Notes |
|---|-----------|-------------|-----------------|-------|
| **T-AI1** | AI analysis completion after data capture | Same business day | SHOULD | AI analysis should not delay professional review |
| **T-AI2** | Professional review after AI analysis | Per T3 (7-14 days) | SHALL | AI does not change professional interpretation timeline |
| **T-AI3** | AI system availability (uptime) | 99% during business hours | SHOULD | System downtime should not delay screening |
| **T-AI4** | AI alert acknowledgment (for urgent findings) | 4 hours during business hours | SHOULD | Urgent AI-flagged cases require timely professional review |

---

### 5.7.8 ISO 13940 Concept Usage for AI Integration

**Table 5.7-6: ISO 13940 Concepts Applied to AI in Cancer Screening**

| ISO 13940 Concept | contsys.org Reference | Application in P3493.1 AI Context |
|-------------------|----------------------|----------------------------------|
| automated healthcare | contsys.org/concept/automated_healthcare | AI-enabled screening activities initiated by healthcare actor, delivered by AI system |
| automatic medical device | contsys.org/concept/medical_device | AI software systems performing automated healthcare activities |
| healthcare professional | contsys.org/concept/healthcare_actor | Remains accountable for clinical decisions informed by AI |
| non-ratified healthcare information | contsys.org/concept/healthcare_information | AI outputs pending professional validation |
| healthcare activity element | contsys.org/concept/healthcare_activity_element | AI may perform elements (investigation, assessment) under professional oversight |
| healthcare investigation | contsys.org/concept/healthcare_activity_element | AI-assisted image analysis is a healthcare investigation element |
| healthcare assessment | contsys.org/concept/healthcare_activity_element | AI risk stratification supports healthcare assessment |
| healthcare evaluation | contsys.org/concept/healthcare_activity_element | AI quality monitoring supports healthcare evaluation |

---

### 5.7.9 Conformance Requirements for AI Integration

Systems claiming conformance to P3493.1 with AI integration SHALL:

a) Document which AI use cases (AI-01 through AI-06) are implemented

b) Document the workflow model (second reader, pre-reader, real-time) for each AI use case

c) Document the decision points (DP1-DP5) where AI provides support

d) Implement human oversight per 5.7.4.1

e) Maintain AI system documentation per 5.7.4.2

f) Support audit trail and transparency per 5.7.4.3

g) Implement performance monitoring per 5.7.4.4

h) Comply with applicable regulatory requirements per 5.7.6

Systems MAY claim conformance to P3493.1 without AI integration; AI is an optional enhancement to the screening clinical process.

---

## END OF MODULE C
