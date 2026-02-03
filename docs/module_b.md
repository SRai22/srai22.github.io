# MODULE B: TERMINOLOGY & DEFINITIONS

**IEEE P3493.1 Standard for Cancer Screening**
**Draft Version: 1.00**
**Date: 2026-02-02**
**Status: Complete**

---

## Table of Contents

- [Clause 3.1: Definitions](#clause-31-definitions)
  - [3.1.1 Healthcare Actor Terms](#311-healthcare-actor-terms)
  - [3.1.2 Health State and Condition Terms](#312-health-state-and-condition-terms)
  - [3.1.3 Process and Episode Terms](#313-process-and-episode-terms)
  - [3.1.4 Governance and Mandate Terms](#314-governance-and-mandate-terms)
  - [3.1.5 Information and Data Terms](#315-information-and-data-terms)
- [Clause 3.2: Terminology Mapping Tables](#clause-32-terminology-mapping-tables)
- [Clause 3.3: ISO 13940 Citation Table](#clause-33-iso-13940-citation-table)
- [Clause 3.4: Deprecated Terms](#clause-34-deprecated-terms)
- [Clause 3.5: Notes for Implementers](#clause-35-notes-for-implementers)

---

## CLAUSE 3.1 — DEFINITIONS

For the purposes of this document, the following terms and definitions apply.

ISO and IEC maintain terminology databases for use in standardization at the following addresses:
- ISO Online browsing platform: available at https://www.iso.org/obp
- IEC Electropedia: available at https://www.electropedia.org

Terms defined in ISO 13940:2015 are indicated with source citations. Terms specific to P3493.1 or adapted from ISO 13940 are marked accordingly.

---

### 3.1.1 Healthcare Actor Terms

#### 3.1.1.1 healthcare actor

organization or person participating in healthcare

**NOTE 1**: Healthcare actors may participate either directly (such as providing care) or indirectly (at organizational levels).

**NOTE 2**: The definition encompasses entities responsible for funding, payment, and reimbursement of healthcare services, alongside those delivering care itself.

**NOTE 3**: In cancer screening, healthcare actors include screening programs, primary care providers, specialists, laboratories, imaging centers, and the subjects of care themselves.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_actor

---

#### 3.1.1.2 subject of care

**healthcare actor** (3.1.1.1) with a person role who seeks to receive, is receiving, or has received healthcare

**NOTE 1**: Alternative terms include patient, client, and service user.

**NOTE 2**: Each subject of care has exactly one **health state** (3.1.2.1) at any given time.

**NOTE 3**: In cancer screening, the subject of care is the individual undergoing screening, diagnostic evaluation, or treatment.

**NOTE 4**: A fetus may qualify as a subject of care when receiving healthcare services.

**EXAMPLE**: Individuals undergoing screening mammography, colonoscopy, or cervical cancer screening.

**SOURCE**: ISO 13940:2015, contsys.org/concept/subject_of_care

---

#### 3.1.1.3 healthcare provider

**healthcare actor** (3.1.1.1) that is able to be assigned one or more **care period mandates** (3.1.4.2)

**NOTE 1**: Healthcare providers fall into two main categories: healthcare organizations (institutional providers) and **healthcare professionals** (3.1.1.4) (individual practitioners).

**NOTE 2**: Organizations solely handling payment or reimbursement are excluded from this definition and are classified as healthcare third parties.

**NOTE 3**: In cancer screening, healthcare providers include screening programs, radiology centers, gastroenterology practices, pathology laboratories, and oncology services.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_provider

---

#### 3.1.1.4 healthcare professional

**healthcare actor** (3.1.1.1) who is a natural person qualified and authorized (by education, certification, licensure, or regulation) to independently perform clinical **healthcare activities** (3.1.3.2) requiring professional judgment

**NOTE 1**: Healthcare professionals have accountability for clinical decisions and interpretations.

**NOTE 2**: In P3493.1, healthcare professionals are authorized to make decisions at clinical decision points per Clause 5.5.

**NOTE 3**: The specific qualifications required for a healthcare professional depend on the activity (e.g., radiologist for mammogram interpretation, gastroenterologist for colonoscopy, pathologist for biopsy interpretation).

**EXAMPLE 1**: Physician, nurse practitioner, physician assistant, radiologist, pathologist, genetic counselor.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_actor (specialized); P3493.1 refinement for clinical decision authority

---

#### 3.1.1.5 healthcare personnel

**healthcare actor** (3.1.1.1) who is a natural person participating in healthcare delivery but who may not be independently qualified to perform clinical activities requiring professional judgment

**NOTE 1**: Healthcare personnel work under the direction or supervision of **healthcare professionals** (3.1.1.4) or within defined protocols.

**NOTE 2**: Healthcare personnel play critical roles in care coordination, patient support, and technical execution, but clinical decisions remain the responsibility of healthcare professionals.

**NOTE 3**: Some roles may be healthcare personnel in one jurisdiction and healthcare professionals in another, depending on scope-of-practice regulations (e.g., advanced practice nurses). Implementers SHALL apply local regulatory definitions.

**EXAMPLE 1**: Medical assistant, scheduling coordinator, patient navigator, radiology technologist (performing imaging under radiologist supervision), phlebotomist.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_actor (specialized); P3493.1 refinement to distinguish from healthcare professional

---

#### 3.1.1.6 contact

interaction between a **subject of care** (3.1.1.2) and one or more **healthcare personnel** (3.1.1.5)

**NOTE 1**: Alternative term: healthcare contact.

**NOTE 2**: Contacts may be preceded by a referral (demand for care) and may have an associated healthcare appointment.

**NOTE 3**: An initial contact is a contact that initiates a **clinical process** (3.1.3.1).

**NOTE 4**: In cancer screening, contacts include screening appointments, result communication encounters, and follow-up visits.

**EXAMPLE 1**: A mammography appointment where the subject of care interacts with the radiology technologist and radiologist.

**EXAMPLE 2**: A telehealth consultation to discuss screening results.

**SOURCE**: ISO 13940:2015, contsys.org/concept/contact

---

#### 3.1.1.7 subject of care proxy

**healthcare actor** (3.1.1.1) authorized to make healthcare decisions on behalf of a **subject of care** (3.1.1.2) who lacks **consent competence** (3.1.4.5)

**NOTE 1**: A subject of care proxy may give **informed consent** (3.1.4.4) or **dissent** (3.1.4.6) on behalf of the subject of care.

**NOTE 2**: The proxy's authority is typically established by legal instrument (power of attorney, guardianship) or by law (e.g., parental authority for minors).

**NOTE 3**: In cancer screening, proxies may make decisions for subjects of care with diminished capacity due to cognitive impairment or other conditions.

**SOURCE**: ISO 13940:2015, contsys.org/concept/subject_of_care_proxy (implied); P3493.1 definition for consent governance

---

#### 3.1.1.8 healthcare supporting organization

**healthcare actor** (3.1.1.1) that provides technical, administrative, or auxiliary services to support healthcare delivery but does not hold primary clinical responsibility or **care period mandates** (3.1.4.2)

**NOTE 1**: Healthcare supporting organizations differ from **healthcare providers** (3.1.1.3) in that they do not hold care period mandates or assume primary clinical responsibility for patient care.

**NOTE 2**: Supporting organizations may perform technical procedures (imaging, laboratory testing) under the direction of healthcare providers or may provide infrastructure services (IT systems, data exchange, administrative services).

**NOTE 3**: In cancer screening, healthcare supporting organizations include:
- Reference laboratories performing biomarker testing or cytology
- Imaging centers that perform technical imaging without interpretation services
- Pathology laboratories processing specimens
- Health information exchanges facilitating data sharing
- Registry systems collecting screening data

**NOTE 4**: Responsibility and liability boundaries between healthcare providers and supporting organizations SHALL be documented per Module E governance requirements.

**EXAMPLE 1**: A reference laboratory that performs HPV testing for cervical cancer screening but does not provide clinical interpretation.

**EXAMPLE 2**: An imaging center that performs screening mammograms with images sent to a separate radiology group for interpretation.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_actor (specialization); P3493.1 definition to distinguish service providers from mandate-holding providers

---

### 3.1.2 Health State and Condition Terms

#### 3.1.2.1 health state

physical and mental functions, body structure, personal factors, activity, participation and environmental aspects as the composite health of a **subject of care** (3.1.1.2)

**NOTE 1**: Each subject of care possesses exactly one health state at any given time.

**NOTE 2**: The definition aligns with WHO's International Classification of Functioning, Disability and Health (ICF), incorporating five components: body function, body structure, activity, participation, and environmental factors.

**NOTE 3**: A health state can exist undetected—for example, cancer may exist before symptoms manifest.

**NOTE 4**: The standard distinguishes between a health state itself and observations of it. A single underlying health state may generate multiple **observed conditions** (3.1.2.5).

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_state

---

#### 3.1.2.2 input health state

**health state** (3.1.2.1) of the **subject of care** (3.1.1.2) at the initiation of a **healthcare activity** (3.1.3.2), **clinical process** (3.1.3.1), or **episode of care** (3.1.3.4)

**NOTE 1**: In cancer screening, the input health state is typically HS-01 (At-Risk) or HS-02 (Symptomatic Concern) per Clause 5.4.2.1.

**NOTE 2**: The input health state documents the subject's baseline condition before healthcare intervention.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_state (specialization: input health state)

---

#### 3.1.2.3 output health state

**health state** (3.1.2.1) of the **subject of care** (3.1.1.2) at the conclusion of a **healthcare activity** (3.1.3.2), **clinical process** (3.1.3.1), or **episode of care** (3.1.3.4), documenting the health condition, status, or outcome resulting from the healthcare provided

**NOTE 1**: Output health state is explicitly documented at screening process completion (per Clause 5.2.5) or resulting episode closure (per Clause 5.3.6).

**NOTE 2**: Output health state represents the patient's health status FROM THE PERSPECTIVE OF the **health issue** (3.1.2.7) being addressed. A patient may have multiple health issues and thus multiple health states simultaneously.

**NOTE 3**: The term "resultant condition" used in earlier drafts is deprecated; use "output health state" per ISO 13940 terminology.

**EXAMPLE 1**: After a negative mammogram, the output health state is "no abnormality detected" (HS-05 per Clause 5.4.2.3).

**EXAMPLE 2**: After diagnostic biopsy confirms breast cancer, the output health state is "cancer confirmed" (HS-09 per Clause 5.4.2.4).

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_state (specialization: output health state); P3493.1 application to process and episode outcomes

---

#### 3.1.2.4 health condition

observed or potential observable aspects of the **health state** (3.1.2.1) at a given time

**NOTE 1**: Health conditions encompass both harmful conditions (diseases, disorders, injuries) and neutral observations.

**NOTE 2**: A health condition represents the perceived aspects of an underlying health state, which may exist undetected.

**NOTE 3**: Within clinical processes, health conditions evolve through stages: initial, observed, considered, professionally assessed, and resultant conditions representing the process outcome.

**NOTE 4**: Diagnoses function as descriptive labels for certain condition types.

**EXAMPLE 1**: Professionally assessed condition: invasive ductal carcinoma of the breast.

**EXAMPLE 2**: Observed condition: suspicious mass on mammography.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_condition

---

#### 3.1.2.5 observed condition

**health condition** (3.1.2.4) or abnormality identified during a **healthcare activity** (3.1.3.2) (such as screening or examination) that requires further evaluation to determine its nature, significance, or clinical implications

**NOTE 1**: An observed condition is typically associated with health state HS-07 (Suspicious Abnormality Detected) in cancer screening per Clause 5.4.2.3.

**NOTE 2**: An observed condition may progress to:
- A confirmed **health condition** (e.g., cancer diagnosed) after diagnostic workup
- An excluded condition (e.g., false positive, benign finding) after diagnostic workup
- Remain indeterminate if diagnostic workup is incomplete

**EXAMPLE 1**: A 1.2 cm mass detected on screening mammography (observed condition requiring biopsy to determine if benign or malignant).

**EXAMPLE 2**: An adenomatous polyp found during colonoscopy (observed condition; pathology will determine grade and management).

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_condition (specialization: observed condition); P3493.1 application to screening context

---

#### 3.1.2.6 potential health condition

**health condition** (3.1.2.4) that may develop in the future based on identified risk factors, genetic predisposition, or current health trajectory

**NOTE 1**: Potential health conditions are the basis for preventive healthcare activities including cancer screening.

**NOTE 2**: In cancer screening, potential health conditions include the risk of developing cancer based on age, family history, genetic markers, or lifestyle factors.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_condition (specialization: potential health condition)

---

#### 3.1.2.7 health issue

representation of an issue related to the health of a **subject of care** (3.1.1.2) as identified by one or more **healthcare actors** (3.1.1.1)

**NOTE 1**: A health issue can correspond to a health problem, disease, illness, or other **health condition** (3.1.2.4) type.

**NOTE 2**: Health issues determine healthcare activity period elements and are addressed by healthcare provider activities, **clinical processes** (3.1.3.1), and **care plans** (3.1.3.5).

**NOTE 3**: In cancer screening, a health issue may be:
- A diagnosed health condition (e.g., confirmed cancer)
- An observed condition requiring investigation (e.g., suspicious mass on imaging)
- A symptomatic concern prompting evaluation (e.g., unexplained bleeding)

**NOTE 4**: For asymptomatic individuals undergoing preventive screening, the triggering health issue may be a **risk condition** (3.1.2.8) rather than a symptomatic problem.

**EXAMPLE 1**: Loss of weight, heart attack, drug addiction, injury, dermatitis.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_issue

---

#### 3.1.2.8 risk condition

condition or set of factors that increases the probability of a **health issue** (3.1.2.7) or **health condition** (3.1.2.4) occurring in the **subject of care** (3.1.1.2), which may warrant preventive or surveillance **healthcare activities** (3.1.3.2)

**NOTE 1**: A risk condition is NOT a health condition but may prompt healthcare activities such as screening, risk assessment, or preventive interventions.

**NOTE 2**: In the context of cancer screening process initiation (Clause 5.2.2), a documented risk condition may serve as the **health issue** that triggers the screening **clinical process** (3.1.3.1).

**NOTE 3**: Risk conditions are typically documented in the **input health state** (3.1.2.2) at process initiation (e.g., HS-01: At-Risk per Clause 5.4.2.1).

**EXAMPLE 1**: Age ≥45 years for colorectal cancer screening (age-based risk).

**EXAMPLE 2**: BRCA1 gene mutation carrier status for breast cancer screening (genetic risk).

**EXAMPLE 3**: Family history of colon cancer in first-degree relative (familial risk).

**EXAMPLE 4**: Personal history of adenomatous polyps (prior condition increasing surveillance need).

**SOURCE**: Derived from ISO 13940:2015 concepts (health issue, potential health condition); term specific to P3493.1 for cancer screening eligibility

---

#### 3.1.2.9 health objective

desired ultimate achievement of a healthcare process addressing health needs

**NOTE 1**: Alternative term: intended outcome.

**NOTE 2**: A health objective may be expressed as one or several target conditions to be reached within a specified date and time.

**NOTE 3**: Health objectives are targeted by **care plans** (3.1.3.5) and supported by healthcare goals as intermediate operational steps toward their achievement.

**NOTE 4**: In cancer screening, health objectives include early detection of cancer, reduction of cancer mortality, and maintenance of cancer-free status.

**EXAMPLE 1**: Detection of colorectal cancer at an early, treatable stage.

**EXAMPLE 2**: Prevention of cervical cancer through identification and treatment of precancerous lesions.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_objective

---

#### 3.1.2.10 professionally assessed condition

**health condition** (3.1.2.4) that has been evaluated and characterized by a **healthcare professional** (3.1.1.4) using clinical judgment, diagnostic criteria, and evidence-based assessment methods

**NOTE 1**: Professionally assessed conditions represent a clinical interpretation of **observed conditions** (3.1.2.5) or symptoms, incorporating professional expertise and standardized classification systems.

**NOTE 2**: In cancer screening, professionally assessed conditions result from interpretation of screening results using standardized categorization systems (e.g., BI-RADS for breast imaging, Bethesda System for cervical cytology) per Module C Clause 5.5.5.

**NOTE 3**: A professionally assessed condition is distinct from:
- An observed condition (raw finding requiring interpretation)
- A confirmed diagnosis (requires definitive diagnostic testing)

**EXAMPLE 1**: Radiologist's assessment "BI-RADS 4: Suspicious abnormality" based on screening mammogram findings.

**EXAMPLE 2**: Pathologist's assessment "High-grade squamous intraepithelial lesion (HSIL)" based on cervical cytology.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_condition (specialization); P3493.1 usage for result interpretation

---

#### 3.1.2.11 excluded condition

**health condition** (3.1.2.4) that was initially suspected or considered but has been ruled out through diagnostic evaluation or clinical assessment

**NOTE 1**: Excluded conditions are important for documenting differential diagnosis and preventing redundant future investigations.

**NOTE 2**: In cancer screening, excluded conditions typically result from:
- Diagnostic workup of positive screening results that confirms benign findings (false positive screens)
- Follow-up evaluation of indeterminate findings that resolves to normal or benign

**NOTE 3**: The exclusion of a condition is documented in health state HS-10 (Cancer Excluded / False Positive) per Module C Clause 5.4.2.4.

**NOTE 4**: Excluded conditions SHALL be documented with:
- The condition that was considered
- The diagnostic method used for exclusion
- The date of exclusion determination
- The healthcare professional making the determination

**EXAMPLE 1**: After biopsy of a suspicious breast mass detected on screening mammography, the final diagnosis is "benign fibroadenoma" — malignancy is the excluded condition.

**EXAMPLE 2**: After colonoscopy follow-up of positive FIT test, no polyps or masses are found — colorectal cancer and adenomatous polyps are excluded conditions.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_condition (specialization: excluded condition); P3493.1 application to false positive screening outcomes per Module C 5.4.2.4, 5.4.3

---

### 3.1.3 Process and Episode Terms

#### 3.1.3.1 clinical process

healthcare process encompassing all **healthcare provider** (3.1.1.3) activities and other prescribed **healthcare activities** (3.1.3.2) that addresses identified or specified **health issues** (3.1.2.7)

**NOTE 1**: A clinical process constitutes a set of interrelated or interacting healthcare activities performed for patients with one or more identified health concerns.

**NOTE 2**: The primary input and output to a clinical process is the **health state** (3.1.2.1).

**NOTE 3**: Clinical processes are the essential, central and most important type of healthcare processes and serve as key mechanisms supporting continuity of care from the patient perspective.

**NOTE 4**: Clinical processes include one or more mandated periods of care, are framed by clinical process episodes (temporal boundaries), and may have associated clinical process interests and outcome evaluations.

**NOTE 5**: In P3493.1, cancer screening SHALL be modeled as a clinical process (per Clause 5.1), not as a single **episode of care** (3.1.3.4).

**SOURCE**: ISO 13940:2015, contsys.org/concept/clinical_process

---

#### 3.1.3.2 healthcare activity

activity intended directly or indirectly to improve or maintain a **health state** (3.1.2.1)

**NOTE 1**: Healthcare activity is an abstract concept implemented through concrete specializations:
- Self-care activity (performed by **subject of care** (3.1.1.2))
- Healthcare provider activity (performed by **healthcare providers** (3.1.1.3))
- Healthcare third party activity (performed by third parties)

**NOTE 2**: Healthcare activities are performed during a healthcare activity period, for exactly one subject of care, target one or more **health objectives** (3.1.2.9), and comprise one or more healthcare activity elements.

**NOTE 3**: In cancer screening, healthcare activities include eligibility determination, screening procedures (mammography, colonoscopy, Pap smear), result interpretation, result communication, and follow-up scheduling.

**EXAMPLE**: A blood pressure measurement completed by a qualified nurse, encompassing taking, documenting, and evaluation phases.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_activity

---

#### 3.1.3.3 healthcare investigation

**healthcare activity** (3.1.3.2) performed to assess or evaluate the **health state** (3.1.2.1) of a **subject of care** (3.1.1.2)

**NOTE 1**: Healthcare investigations include diagnostic tests, imaging studies, laboratory analyses, and clinical examinations.

**NOTE 2**: In cancer screening, the screening procedure itself (e.g., mammography, colonoscopy) is a healthcare investigation.

**SOURCE**: ISO 13940:2015 (implied from healthcare activity specializations); P3493.1 definition for screening context

---

#### 3.1.3.4 episode of care

health related period during which **healthcare activities** (3.1.3.2) are performed to address one **health issue** (3.1.2.7) as identified by one **healthcare professional** (3.1.1.4)

**NOTE 1**: An episode of care is managed by exactly one **healthcare provider** (3.1.1.3), centered on exactly one health issue, and contains one or more healthcare activity period elements.

**NOTE 2**: An episode of care does NOT necessarily coincide with an "episode of illness" due to practical administrative needs around start/end dates and professional-specific issue identification.

**NOTE 3**: Multiple episodes of care can occur concurrently within a single mandated care period when different health issues are addressed.

**NOTE 4**: In P3493.1, episodes of care are conditionally initiated as outcomes of the screening **clinical process** (3.1.3.1) when specific triggers occur (per Clause 5.3.2). Screening itself SHALL NOT be modeled as an episode of care.

**EXAMPLE 1**: Episode of diagnostic workup following positive screening mammogram.

**EXAMPLE 2**: Episode of breast cancer treatment following diagnostic confirmation.

**SOURCE**: ISO 13940:2015, contsys.org/concept/episode_of_care

---

#### 3.1.3.5 care plan

agreed and documented healthcare plan tailored to a specific **subject of care** (3.1.1.2), specifying the **healthcare activities** (3.1.3.2) to be performed, the responsible **healthcare actors** (3.1.1.1), timeframes, and expected **health objectives** (3.1.2.9), based on the subject's **health issue** (3.1.2.7) and individual circumstances

**NOTE 1**: A care plan is patient-specific and may be modified based on individual factors (preferences, comorbidities, barriers to care).

**NOTE 2**: A care plan is typically derived from or informed by a **core care plan** (3.1.3.6) but adapted to the individual.

**NOTE 3**: In cancer screening, the care plan includes the screening modality, schedule, responsible providers, and contingency plans (e.g., what to do if results are positive).

**EXAMPLE**: "Mrs. Johnson will undergo screening mammography on March 15, 2026, at City Radiology, performed by Dr. Lee, with results communicated within 7 days."

**SOURCE**: ISO 13940:2015, contsys.org/concept/care_plan (implied); P3493.1 definition adapted for cancer screening context

---

#### 3.1.3.6 core care plan

evidence-based healthcare plan template or protocol that defines the standard pathway of **healthcare activities** (3.1.3.2) for a specific **health issue** (3.1.2.7) or clinical scenario, intended to be instantiated into patient-specific **care plans** (3.1.3.5)

**NOTE 1**: A core care plan represents best practices or clinical consensus and is generally NOT modified for individual patients, though the instantiated care plan derived from it MAY be adapted.

**NOTE 2**: In P3493.1, the core care plan is typically an external guideline (USPSTF, NCCN, ACR, ACS, etc.) referenced by identifier in the care plan.

**NOTE 3**: Core care plans provide the normative basis for clinical decision-making at decision points per Clause 5.5.

**NOTE 4**: The terms "protocol," "guideline," "clinical pathway," and "standard of care" are often used interchangeably with "core care plan" in practice. For precision in this standard, use "core care plan" when referencing the ISO 13940 concept.

**EXAMPLE 1**: USPSTF breast cancer screening guideline recommending biennial mammography for women aged 50-74 (standard-risk).

**EXAMPLE 2**: NCCN colorectal cancer screening protocol specifying colonoscopy every 10 years starting at age 45 for average-risk individuals.

**SOURCE**: ISO 13940:2015, contsys.org/concept/core_care_plan (implied); P3493.1 definition adapted for cancer screening context

---

#### 3.1.3.7 health thread

defined association between healthcare matters as determined by one or more **healthcare actors** (3.1.1.1)

**NOTE 1**: Health threads reconcile diverse healthcare matters across different actor scopes and encompass related healthcare processes and activity period elements.

**NOTE 2**: Health threads can be established by teams or built incrementally by **healthcare professionals** (3.1.1.4) and may be reconsidered as care progresses (conditions can be linked or separated).

**NOTE 3**: Three subtypes exist: health condition evolution, health problem list, and clinical process interest.

**NOTE 4**: In P3493.1, health threads provide the linkage mechanism between screening **clinical processes** (3.1.3.1) and resulting **episodes of care** (3.1.3.4) per Clause 5.3.4.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_thread

---

#### 3.1.3.8 screening process instance

single execution of the cancer screening **clinical process** (3.1.3.1) for one **subject of care** (3.1.1.2), from initiation through completion or suspension, as specified in Clause 5.2

**NOTE 1**: A screening process instance is identified by a unique process instance identifier.

**NOTE 2**: A subject of care's screening history consists of a sequence of screening process instances, which may or may not result in **episodes of care** (3.1.3.4).

**NOTE 3**: Multiple screening process instances for different cancer types may be active concurrently for the same subject of care.

**NOTE 4**: This term is specific to P3493.1 and represents the instantiation of the screening clinical process model defined in Module C.

**SOURCE**: P3493.1 specific term; applies ISO 13940 clinical process concept to screening workflow

---

#### 3.1.3.9 healthcare needs assessment

systematic evaluation of a **subject of care's** (3.1.1.2) health status, risk factors, and circumstances to determine appropriate **healthcare activities** (3.1.3.2) and develop a **care plan** (3.1.3.5)

**NOTE 1**: Healthcare needs assessment is typically performed by a **healthcare professional** (3.1.1.4) and incorporates:
- Clinical evaluation (symptoms, signs, history)
- Risk factor assessment
- Guideline applicability determination
- Patient preferences and values
- Barriers to care and social determinants of health

**NOTE 2**: In cancer screening, healthcare needs assessment occurs at Stage 1 (Process Initiation) per Module C Clause 5.2.2 and includes:
- Eligibility determination per Decision Point 1 (Module C 5.5.3)
- Risk stratification (standard-risk vs. high-risk)
- Screening modality selection per Decision Point 2 (Module C 5.5.4)

**NOTE 3**: Healthcare needs assessment results in a **healthcare commitment** (3.1.4.3) by the provider and typically requires **informed consent** (3.1.4.4) from the subject of care.

**EXAMPLE 1**: Primary care physician assesses a 50-year-old patient for colorectal cancer screening eligibility, determines average risk status, and recommends colonoscopy per USPSTF guidelines.

**EXAMPLE 2**: Screening program coordinator evaluates a patient with BRCA1 mutation for high-risk breast cancer screening, recommends annual MRI plus mammography starting at age 30.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_needs_assessment; P3493.1 application to screening eligibility and planning per Module C 5.2.2, 5.5.3

---

#### 3.1.3.10 referral

formal request or recommendation by a **healthcare professional** (3.1.1.4) or **healthcare provider** (3.1.1.3) for a **subject of care** (3.1.1.2) to receive specific **healthcare activities** (3.1.3.2) from another healthcare provider, typically involving transfer of clinical information and responsibility

**NOTE 1**: Alternative term: demand for care (per ISO 13940).

**NOTE 2**: A referral typically includes:
- Clinical indication and urgency
- Relevant clinical information (history, findings, test results)
- Requested services or consultation
- Timeframe expectations
- Referring provider contact information

**NOTE 3**: In cancer screening, referrals are most commonly used when:
- Positive screening results require diagnostic workup by a specialist (Module C 5.2.5 Branch 4C)
- Diagnostic services are external to the screening program (Pattern B per Module C 5.3.3.2)
- Confirmed cancer diagnosis requires treatment by oncology services

**NOTE 4**: Referrals in Pattern B screening workflows involve **responsibility transfer** (3.1.4.8) per Module C Clause 5.3.5 and Module E governance requirements.

**NOTE 5**: Referral SHALL be documented with metadata per Module C 5.3.4 to maintain continuity via **health thread** (3.1.3.7) linkage.

**EXAMPLE 1**: Primary care physician refers patient with positive FIT test to gastroenterology for colonoscopy.

**EXAMPLE 2**: Screening mammography program refers patient with BI-RADS 5 finding to breast surgical oncology for biopsy and treatment planning.

**SOURCE**: ISO 13940:2015, contsys.org/concept/demand_for_care (referral is a specialization); P3493.1 extensive usage in Module C 5.2.5, 5.3.3.2, 5.3.5

---

#### 3.1.3.11 healthcare communication

exchange of healthcare-relevant information between **healthcare actors** (3.1.1.1), including communication between providers, between provider and **subject of care** (3.1.1.2), or among care team members

**NOTE 1**: Healthcare communication in cancer screening includes:
- Result communication to subjects of care (Module C Stage 3, Clauses 5.2.4, 5.5.6)
- Referral communication between providers (Module C 5.3.5)
- Care coordination communication among team members
- Recall and reminder notifications to subjects of care

**NOTE 2**: Critical communications SHALL meet temporal requirements per Module C Clause 5.6:
- T4: Negative results communicated within 14 days (SHOULD)
- T5: Positive results communicated within 5 business days (SHALL)
- T6: Indeterminate results communicated within 10 days (SHOULD)

**NOTE 3**: Healthcare communication SHALL be documented with:
- Communication date and method (in-person, phone, letter, patient portal, secure message)
- Content summary (what was communicated)
- Recipient acknowledgment (if obtained)
- Communicating healthcare actor identifier

**NOTE 4**: Communication methods SHALL be appropriate for content sensitivity, urgency, and patient preferences. Positive or indeterminate results SHOULD involve direct interaction (phone or in-person) when possible, not solely written communication.

**EXAMPLE 1**: Radiologist sends mammography results letter to patient and primary care physician documenting BI-RADS 1 (negative) finding and recommending routine annual screening.

**EXAMPLE 2**: Nurse navigator calls patient to explain positive FIT test result, discusses next steps (colonoscopy referral), and schedules follow-up appointment.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_communication; P3493.1 extensive usage in Module C Stage 3 (5.2.4), temporal requirements (5.6), and decision points (5.5)

---

#### 3.1.3.12 healthcare documentation

process of creating, maintaining, and managing records of **healthcare activities** (3.1.3.2), clinical findings, decisions, and outcomes in **health records** (3.1.5.1)

**NOTE 1**: Healthcare documentation serves multiple purposes:
- Clinical continuity and care coordination
- Legal and regulatory compliance
- Quality measurement and improvement
- Billing and reimbursement
- Secondary use for research, public health, and AI training (per Module F)

**NOTE 2**: In cancer screening, healthcare documentation includes:
- Process metadata (Module C 5.2.2, 5.3.4, 5.4.5)
- Clinical findings and interpretations (Module C 5.2.3, 5.5.5)
- Decision rationale at decision points (Module C 5.5)
- Health state transitions (Module C 5.4)
- Communication records (Module C 5.2.4)

**NOTE 3**: Documentation SHALL meet temporal requirements per Module C:
- T13: Clinical decisions documented within 1 business day
- T16: Health state transitions documented same business day
- T17: Process metadata completed within 7 days of completion

**NOTE 4**: Healthcare documentation SHALL be structured, machine-readable where feasible, and conform to applicable standards (HL7 FHIR, LOINC, SNOMED CT) per Module D requirements.

**EXAMPLE 1**: Radiologist documents mammogram interpretation in structured radiology report using BI-RADS terminology.

**EXAMPLE 2**: Primary care physician documents shared decision-making conversation about colorectal cancer screening options in clinical note.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_documenting; P3493.1 implicit throughout Module C for metadata and record-keeping requirements

**NOTE 5**: The ISO 13940 term is "healthcare documenting" (gerund form). P3493.1 uses "healthcare documentation" (noun form) for readability; both refer to the same concept.

---

#### 3.1.3.13 healthcare process evaluation

systematic assessment of the structure, execution, outcomes, and quality of a **clinical process** (3.1.3.1) or **healthcare activity** (3.1.3.2) to determine effectiveness, efficiency, safety, and adherence to standards

**NOTE 1**: Healthcare process evaluation encompasses:
- Process performance metrics (completion rates, timeliness, adherence to guidelines)
- Outcome evaluation (detection rates, stage distribution, interval cancers)
- Quality metrics (false positive rates, positive predictive value, patient satisfaction)
- Adverse event analysis (harms, complications, errors)

**NOTE 2**: In cancer screening, healthcare process evaluation is specified in Module C Clause 5.5.8 (Decision Audit and Quality Review) and includes:
- Decision concordance with guidelines
- Temporal compliance monitoring (per Module C 5.6)
- Follow-up completion rates
- Lost-to-follow-up analysis

**NOTE 3**: Healthcare process evaluation supports Module F secondary use for quality improvement and program accreditation.

**NOTE 4**: Process evaluation may be performed:
- Prospectively (real-time monitoring with alerts)
- Retrospectively (periodic quality reviews, audits)
- Continuously (dashboard metrics, statistical process control)

**EXAMPLE 1**: Screening program evaluates colonoscopy completion rate after positive FIT tests, identifies gaps, and implements patient navigation intervention.

**EXAMPLE 2**: Breast imaging center reviews BI-RADS 3 (probably benign) outcomes at 2 years to validate appropriate use of this category.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_process_evaluation; P3493.1 application to screening quality per Module C 5.5.8 and Module F

---

#### 3.1.3.14 outcome evaluation

systematic assessment of the end results or impacts of **healthcare activities** (3.1.3.2), **clinical processes** (3.1.3.1), or **episodes of care** (3.1.3.4) on the **health state** (3.1.2.1) of the **subject of care** (3.1.1.2) or population health metrics

**NOTE 1**: Outcome evaluation focuses on results achieved (what happened to patients) rather than process execution (what was done).

**NOTE 2**: In cancer screening, outcome evaluation includes:
- Cancer detection rates (per 1000 screens)
- Stage distribution at diagnosis (early vs. late stage)
- Interval cancer rates
- Mortality reduction (population-level)
- False positive rates and resulting harms
- Patient-reported outcomes (anxiety, satisfaction, quality of life)

**NOTE 3**: Outcome evaluation is distinct from **healthcare process evaluation** (3.1.3.13):
- Process evaluation assesses HOW screening is performed
- Outcome evaluation assesses WHAT RESULTS were achieved

**NOTE 4**: Outcome evaluation requires:
- **Output health state** (3.1.2.3) documentation per Module C 5.4
- Linkage between screening processes and resulting episodes via **health thread** (3.1.3.7) per Module C 5.3.4
- Long-term follow-up data (cancer registry linkage, mortality tracking)

**EXAMPLE 1**: Colorectal cancer screening program evaluates outcomes showing 65% of detected cancers are stage I-II (early stage), demonstrating effectiveness of screening.

**EXAMPLE 2**: Breast screening program evaluates outcomes and finds false positive recall rate of 8.5%, below the benchmark threshold of 10%.

**SOURCE**: ISO 13940:2015, contsys.org/concept/clinical_process_outcome_evaluation; P3493.1 application to screening effectiveness per Module C 5.5.8 and Module F

**NOTE 5**: The full ISO 13940 term is "clinical process outcome evaluation." P3493.1 uses "outcome evaluation" as shorthand where context is clear.

---

#### 3.1.3.15 healthcare goals

specific, measurable, time-bound intermediate objectives that support achievement of **health objectives** (3.1.2.9) within a **care plan** (3.1.3.5)

**NOTE 1**: Healthcare goals are operational and actionable steps toward broader health objectives:
- **Health objective** (ultimate aim): Detect colorectal cancer at early stage
- **Healthcare goals** (intermediate steps): Complete colonoscopy by [date], obtain pathology results within 2 weeks, schedule surgical consultation within 30 days if cancer confirmed

**NOTE 2**: Healthcare goals differ from health objectives in specificity and timeframe:
- Health objectives are ultimate desired achievements (often long-term)
- Healthcare goals are specific actions or milestones with defined timeframes

**NOTE 3**: In cancer screening, healthcare goals are embedded in care plans (Module C 5.2.2, 5.5) and include:
- Complete screening procedure by [date]
- Communicate results within [timeframe] per temporal requirements (Module C 5.6)
- If positive, complete diagnostic referral within 14 days (T7)

**NOTE 4**: Healthcare goals SHOULD be documented in structured format with:
- Goal description
- Target completion date
- Responsible actor(s)
- Achievement status

**EXAMPLE 1**: "Patient will complete screening mammography at City Imaging Center by March 30, 2026."

**EXAMPLE 2**: "If colonoscopy identifies polyps, pathology results will be available and communicated to patient within 10 days of procedure."

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_goal; P3493.1 implicit in care planning per Module C 5.2, 5.5

---

#### 3.1.3.16 medical device

instrument, apparatus, implement, machine, appliance, implant, reagent, software, or similar article intended for use in healthcare for diagnosis, prevention, monitoring, treatment, or alleviation of disease or health conditions

**NOTE 1**: In cancer screening, medical devices include:
- Imaging equipment (mammography systems, CT scanners, endoscopy equipment)
- Laboratory instruments (HPV testing platforms, cytology processors)
- Software systems (clinical decision support, AI-assisted interpretation tools)
- Test kits and reagents (FIT kits, biomarker assays)

**NOTE 2**: Medical devices used in screening SHALL be appropriately validated, regulated (e.g., FDA-cleared, CE-marked), and maintained per manufacturer specifications and regulatory requirements.

**NOTE 3**: AI-assisted interpretation systems are medical devices when used for clinical decision support per Module C Clause 5.5.5 (Decision Point 3, NOTE 5) and 5.5.9.

**NOTE 4**: Use of medical devices SHALL be documented in process metadata including:
- Device identification (manufacturer, model, version)
- Regulatory status (clearance/approval identifiers)
- Calibration/quality control status
- Operator/user identification

**EXAMPLE 1**: Digital mammography system used for breast cancer screening.

**EXAMPLE 2**: AI-based computer-aided detection (CAD) software that highlights suspicious regions on screening mammograms for radiologist review.

**EXAMPLE 3**: Fecal immunochemical test (FIT) kit used for at-home colorectal cancer screening.

**SOURCE**: ISO 13940:2015, contsys.org/concept/medical_device; P3493.1 application to screening equipment, AI systems, and diagnostic tools per Module C 5.2.3, 5.5.5, 5.5.9

---

#### 3.1.3.17 automated medical device

**medical device** (3.1.3.16) that performs healthcare functions autonomously or semi-autonomously without continuous direct human control, often incorporating artificial intelligence, machine learning, or algorithmic decision logic

**NOTE 1**: Automated medical devices in cancer screening include:
- AI-based image interpretation systems that automatically identify and flag suspicious findings
- Automated risk stratification algorithms that identify eligible screening candidates from EHR data
- Automated recall/reminder systems that schedule follow-up appointments
- Clinical decision support systems that provide guideline-based recommendations at decision points (Module C 5.5.9)

**NOTE 2**: Automated medical devices differ from manual medical devices:
- Manual device: Requires continuous operator control (e.g., endoscope operated by gastroenterologist)
- Automated device: Operates independently once initiated (e.g., AI system that auto-reads mammograms and triages for radiologist review)

**NOTE 3**: Use of automated medical devices SHALL comply with:
- Regulatory requirements (FDA clearance for intended use)
- Clinical validation requirements (demonstrated accuracy, sensitivity, specificity for screening population)
- Human oversight requirements: A **healthcare professional** (3.1.1.4) remains the ultimate decision maker per Module C 5.5.9
- Transparency requirements: Device logic, version, and recommendations SHALL be documented

**NOTE 4**: When automated medical devices provide recommendations that differ from healthcare professional decisions, the professional's rationale for overriding the device SHOULD be documented per Module C 5.5.9.

**EXAMPLE 1**: AI-based automated breast ultrasound system that identifies and measures suspicious lesions without continuous operator guidance.

**EXAMPLE 2**: Machine learning algorithm that analyzes EHR data to identify patients overdue for colorectal cancer screening and generates automated outreach.

**EXAMPLE 3**: Computer-aided detection system for lung cancer screening that automatically segments and measures lung nodules on low-dose CT scans.

**SOURCE**: ISO 13940:2015, contsys.org/concept/automatic_medical_device; P3493.1 definition for AI systems and automated screening tools per Module C 5.5.5 (NOTE 5), 5.5.9

**NOTE 5**: The ISO 13940 term is "automatic medical device." P3493.1 uses "automated medical device" to better reflect current terminology for AI/ML systems; both refer to medical devices capable of performing healthcare activities without continuous human control.

---

### 3.1.4 Governance and Mandate Terms

#### 3.1.4.1 healthcare mandate

mandate (commission) based on a **healthcare commitment** (3.1.4.3) and either an **informed consent** (3.1.4.4) or an authorization by law, defining the rights and obligations of one **healthcare actor** (3.1.1.1) with regard to involvement in healthcare processes performed for a specific **subject of care** (3.1.1.2)

**NOTE 1**: Healthcare mandates can be explicit or implicit, are typically assigned by one healthcare actor to another, and require acceptance through healthcare commitment.

**NOTE 2**: Healthcare mandates concern exactly one subject of care and regulate one or more healthcare processes.

**NOTE 3**: Five specializations exist: healthcare activity mandate, **care period mandate** (3.1.4.2), demand mandate, continuity facilitator mandate, and mandate to export personal information.

**NOTE 4**: Relevant information related to healthcare mandates (including demands for care, informed consents, dissents, healthcare commitments, etc.) is recorded in **health records** (3.1.5.1).

**NOTE 5**: In cancer screening, healthcare mandates establish the formal authority and responsibility for screening program administration, clinical care delivery, and data governance.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_mandate

---

#### 3.1.4.2 care period mandate

**healthcare mandate** (3.1.4.1) commissioning a mandated period of care

**NOTE 1**: A care period mandate represents an agreement between the **subject of care** (3.1.1.2) and a **healthcare provider** (3.1.1.3) to provide specified healthcare services in a mandated period of care.

**NOTE 2**: Care period mandates are assigned to exactly one healthcare provider and commission one or more healthcare services.

**NOTE 3**: In cancer screening, care period mandates establish the formal relationship between the screening program and the subject of care for the duration of screening activities.

**SOURCE**: ISO 13940:2015, contsys.org/concept/care_period_mandate

---

#### 3.1.4.3 healthcare commitment

acceptance of a **healthcare mandate** (3.1.4.1) by the **healthcare actor** (3.1.1.1) to whom it is assigned

**NOTE 1**: Alternative term: care commitment.

**NOTE 2**: A healthcare commitment emerges implicitly through dialogue between the **healthcare provider** (3.1.1.3) and the **subject of care** (3.1.1.2) (or their representative) during a healthcare needs assessment process.

**NOTE 3**: When a provider accepts a healthcare commitment, they confirm acceptance of the pending mandate outlined in the proposed **care plan** (3.1.3.5).

**NOTE 4**: In cancer screening, the healthcare commitment is established when the screening program or provider agrees to provide screening services per Clause 5.2.2.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_commitment

---

#### 3.1.4.4 informed consent

permission to perform **healthcare activities** (3.1.3.2), voluntarily given by a **subject of care** (3.1.1.2) having **consent competence** (3.1.4.5), or by a **subject of care proxy** (3.1.1.7), after having been informed about the purpose and the possible results of the healthcare activities

**NOTE 1**: Informed consent is one of two foundations for a **healthcare mandate** (3.1.4.1) (the other being authorization by law).

**NOTE 2**: Informed consent requires that the subject of care (or proxy) has been adequately informed about:
- The nature and purpose of the proposed healthcare activities
- The potential benefits, risks, and alternatives
- The expected outcomes and possible complications
- The subject's right to refuse or withdraw consent

**NOTE 3**: In cancer screening, informed consent is obtained at process initiation (Clause 5.2.2) and may need to be renewed for specific procedures (e.g., biopsy) per Module E requirements.

**SOURCE**: ISO 13940:2015, contsys.org/concept/informed_consent

---

#### 3.1.4.5 consent competence

capability of the **subject of care** (3.1.1.2) and/or the **subject of care proxy** (3.1.1.7) to give **informed consent** (3.1.4.4) or **dissent** (3.1.4.6)

**NOTE 1**: Consent competence is required for valid informed consent.

**NOTE 2**: Consent competence may be affected by age, cognitive status, mental health conditions, or other factors that impair decision-making capacity.

**NOTE 3**: If a subject of care lacks consent competence, a subject of care proxy may provide consent on their behalf.

**NOTE 4**: In cancer screening, assessment of consent competence is part of the eligibility and consent process per Clause 5.2.2 and Module E.

**SOURCE**: ISO 13940:2015, contsys.org/concept/consent_competence

---

#### 3.1.4.6 dissent

explicit refusal by a **subject of care** (3.1.1.2) having **consent competence** (3.1.4.5), or by a **subject of care proxy** (3.1.1.7), to permit specific **healthcare activities** (3.1.3.2)

**NOTE 1**: Dissent is the converse of **informed consent** (3.1.4.4).

**NOTE 2**: Dissent must be respected and documented.

**NOTE 3**: In cancer screening, a subject of care may dissent from screening entirely, from specific screening modalities, or from specific follow-up activities.

**SOURCE**: ISO 13940:2015, contsys.org/concept/dissent (implied); P3493.1 definition for consent governance

---

#### 3.1.4.7 continuity facilitator mandate

**healthcare mandate** (3.1.4.1) commissioning a **healthcare provider** (3.1.1.3) to facilitate continuity of care for a **subject of care** (3.1.1.2) across multiple **episodes of care** (3.1.3.4) or **clinical processes** (3.1.3.1)

**NOTE 1**: A continuity facilitator (often a primary care provider or care coordinator) maintains oversight of the subject's healthcare across providers and time.

**NOTE 2**: In cancer screening, the continuity facilitator may be the primary care provider who maintains the subject's screening history and ensures appropriate follow-up.

**SOURCE**: ISO 13940:2015, contsys.org/concept/continuity_facilitator_mandate (implied); P3493.1 definition for screening continuity

---

#### 3.1.4.8 responsibility transfer

documented transfer of **healthcare mandate** (3.1.4.1) responsibility from one **healthcare provider** (3.1.1.3) to another, including specification of the transferred obligations and acceptance by the receiving provider

**NOTE 1**: Responsibility transfer is required when Pattern B (Separate Linked Episodes) is used per Clause 5.3.3.2.

**NOTE 2**: Responsibility transfer SHALL be documented per Module E requirements.

**NOTE 3**: In cancer screening, responsibility transfer occurs when a positive screening result leads to referral to an external diagnostic or treatment provider.

**SOURCE**: ISO 13940:2015 concepts (healthcare mandate, healthcare commitment); P3493.1 term for screening workflow governance

---

#### 3.1.4.9 adverse event

undesirable clinical occurrence, harm, or complication experienced by a **subject of care** (3.1.1.2) during or as a result of **healthcare activities** (3.1.3.2), which may or may not be directly caused by the healthcare provided

**NOTE 1**: Adverse events in cancer screening include:
- Physical harms: Complications from screening procedures (e.g., perforation during colonoscopy, vasovagal reaction during blood draw)
- Psychological harms: Anxiety, distress from false positive results or prolonged diagnostic uncertainty
- Downstream harms: Unnecessary diagnostic procedures or treatments resulting from false positive screens
- System failures: Missed screening results, communication failures, lost-to-follow-up resulting in delayed cancer diagnosis

**NOTE 2**: Adverse events are distinct from expected side effects or normal consequences of screening (e.g., mild discomfort during mammography is expected, not an adverse event).

**NOTE 3**: Interval cancers (cancers diagnosed between screening rounds) SHALL be documented as adverse events related to the prior screening process per Module C Clause 5.4.6.2, to enable analysis of:
- False negative screens (cancer present but not detected)
- New cancers arising after negative screen
- Rapidly progressive cancers

**NOTE 4**: Adverse events SHALL be documented with:
- Event description and severity
- Date of occurrence
- Relationship to screening process or resulting episode (process/episode identifier)
- Causality assessment (definite, probable, possible, unrelated)
- Actions taken to mitigate harm
- Reporting to appropriate oversight bodies (IRB, accreditation, regulatory)

**NOTE 5**: Adverse event tracking supports **healthcare process evaluation** (3.1.3.13), quality improvement, and risk-benefit assessment of screening programs.

**EXAMPLE 1**: Patient experiences colonic perforation during screening colonoscopy, requires surgical repair.

**EXAMPLE 2**: Patient with false positive screening mammogram undergoes unnecessary breast biopsy that shows benign tissue.

**EXAMPLE 3**: Patient develops severe anxiety and depression after receiving positive cervical cancer screening result, later determined to be false positive.

**EXAMPLE 4**: Interval breast cancer diagnosed 8 months after negative screening mammogram, retrospective review shows subtle findings were missed.

**SOURCE**: ISO 13940:2015, contsys.org/concept/adverse_event; P3493.1 application to screening harms and quality monitoring per Module C 5.4.6.2

---

### 3.1.5 Information and Data Terms

#### 3.1.5.1 health record

data repository regarding the health and healthcare of a **subject of care** (3.1.1.2)

**NOTE 1**: Health records may encompass medical records, dental records, and social care records.

**NOTE 2**: Three specializations exist:
- Electronic health record: health record stored entirely on electronic media
- Personal health record: health record maintained by the subject of care
- Professional health record: health record maintained by a **healthcare provider** (3.1.1.3)

**NOTE 3**: Health records maintain connections with **healthcare activities** (3.1.3.2), healthcare documenting, healthcare processes, **healthcare mandates** (3.1.4.1), and the subject of care.

**NOTE 4**: Health records may contain **care plans** (3.1.3.5), healthcare mandates, subject of care desires, and health record extracts.

**NOTE 5**: In cancer screening, health records contain screening process documentation, results, follow-up actions, and resulting **episode of care** (3.1.3.4) documentation.

**SOURCE**: ISO 13940:2015, contsys.org/concept/health_record

---

#### 3.1.5.2 healthcare information

information about a person, relevant to his or her healthcare

**NOTE 1**: This is a concrete item that can be implemented directly.

**NOTE 2**: Two specializations exist:
- **Non-ratified healthcare information** (3.1.5.5): information whose clinical relevance has not yet been validated by a **healthcare professional** (3.1.1.4)
- Healthcare information for import: information ready for integration into a professional **health record** (3.1.5.1) after validation

**NOTE 3**: In cancer screening, healthcare information includes screening results, diagnostic findings, risk assessments, and treatment histories.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_information

---

#### 3.1.5.3 healthcare data

data that represents or can be processed to derive **healthcare information** (3.1.5.2)

**NOTE 1**: Healthcare data includes raw data from screening procedures (e.g., mammography images, laboratory values, endoscopic recordings) as well as structured data elements.

**NOTE 2**: In P3493.1, healthcare data requirements are specified in Module D.

**SOURCE**: P3493.1 definition; aligned with ISO 13940 healthcare information concept

---

#### 3.1.5.4 metadata

data that provides information about other data, including context, provenance, quality, and governance attributes

**NOTE 1**: In cancer screening, metadata includes process instance identifiers, timestamps, responsible provider identifiers, health state codes, and linkage identifiers.

**NOTE 2**: Metadata requirements for screening processes and resulting episodes are specified in Clauses 5.2.2, 5.3.4, and 5.4.5.

**NOTE 3**: Metadata enables continuity of care, quality measurement, and secondary use per Module F.

**SOURCE**: P3493.1 definition; general informatics term applied to screening context

---

#### 3.1.5.5 non-ratified healthcare information

**healthcare information** (3.1.5.2) whose clinical relevance, accuracy, or completeness has not yet been validated or confirmed by a **healthcare professional** (3.1.1.4)

**NOTE 1**: Non-ratified healthcare information requires professional review before being incorporated into clinical decision-making or care planning.

**NOTE 2**: Sources of non-ratified healthcare information in cancer screening include:
- Patient-reported information (family history, symptoms, prior screening history from other providers)
- Data from external sources not yet validated (screening results from other healthcare systems)
- Automated device outputs pending professional interpretation (raw imaging data before radiologist interpretation, laboratory values before pathologist review)
- Information from **healthcare supporting organizations** (3.1.1.8) pending provider validation

**NOTE 3**: The transition from non-ratified to ratified information occurs when a healthcare professional:
- Reviews the information
- Assesses its clinical relevance and accuracy
- Incorporates it (or explicitly excludes it) into the clinical record
- Documents the validation process

**NOTE 4**: In cancer screening workflows, non-ratified information includes:
- Health state HS-04 (Results Pending Interpretation) per Module C 5.4.2.2: screening data is captured but not yet professionally interpreted
- Patient self-reported risk factors before clinician verification
- External records received via **health thread** (3.1.3.7) linkage before provider review

**EXAMPLE 1**: Patient reports "I had a colonoscopy 3 years ago at another hospital, and they found a polyp" — this is non-ratified until the external records are obtained and reviewed by the healthcare professional.

**EXAMPLE 2**: Mammography imaging data has been captured (HS-04) but radiologist interpretation is pending — the raw imaging data is non-ratified healthcare information until interpretation is documented.

**EXAMPLE 3**: Automated AI system flags suspicious region on lung CT scan — this is non-ratified until radiologist reviews and confirms or dismisses the finding.

**SOURCE**: ISO 13940:2015, contsys.org/concept/healthcare_information (specialization: non-ratified healthcare information); P3493.1 application to information validation in screening per Module C 5.2.3 (Stage 2), 5.5.5

---

---

## CLAUSE 3.2 — TERMINOLOGY MAPPING TABLES

### Table 3.2-1: Core Terminology Mapping (ISO 13940 to P3493.1 Usage)

| Concept | Preferred Term (Normative) | Deprecated / Informal Terms | ISO 13940 Reference | P3493.1 Clause |
|---------|---------------------------|----------------------------|---------------------|----------------|
| Evidence-based guideline/pathway | core care plan | protocol, screening protocol, clinical pathway, guideline | ISO 13940:2015, core_care_plan | 3.1.3.6, 5.2.2, 5.5 |
| Patient-specific plan | care plan | treatment plan, management plan | ISO 13940:2015, care_plan | 3.1.3.5, 5.2 |
| Risk factor prompting screening | risk condition | risk factor, eligibility criterion | Derived from ISO 13940 | 3.1.2.8, 5.4.2.1 |
| Problem requiring healthcare action | health issue | presenting complaint (for symptomatic), chief concern | ISO 13940:2015, health_issue | 3.1.2.7, 5.2.2 |
| Health status at process/episode end | output health state | resultant condition (deprecated), outcome | ISO 13940:2015, health_state | 3.1.2.3, 5.2, 5.4 |
| Licensed clinician with decision authority | healthcare professional | provider, clinician, practitioner, physician | ISO 13940:2015, healthcare_actor | 3.1.1.4, 5.5 |
| Support staff without independent clinical authority | healthcare personnel | staff, administrative personnel, technician | Derived from ISO 13940 | 3.1.1.5 |
| Abnormality detected on screening | observed condition | finding, abnormality, suspicious lesion, positive screen | ISO 13940:2015, health_condition | 3.1.2.5, 5.4.2.3 |
| Linkage between process and episode | health thread | episode linkage, care continuity link | ISO 13940:2015, health_thread | 3.1.3.7, 5.3.4 |
| Single screening workflow execution | screening process instance | screening episode (deprecated), screening encounter | P3493.1 specific | 3.1.3.8, 5.2 |
| Event-driven care container | episode of care | care episode, treatment episode | ISO 13940:2015, episode_of_care | 3.1.3.4, 5.3 |
| Ongoing preventive workflow | clinical process | care process, screening process | ISO 13940:2015, clinical_process | 3.1.3.1, 5.1 |
| Eligibility assessment and planning | healthcare needs assessment | risk assessment, screening eligibility evaluation | ISO 13940:2015, healthcare_needs_assessment | 3.1.3.9, 5.2.2, 5.5.3 |
| Request for care from another provider | referral | demand for care, consultation request | ISO 13940:2015, demand_for_care | 3.1.3.10, 5.3.5 |
| Exchange of clinical information | healthcare communication | patient notification, result communication | ISO 13940:2015, healthcare_communication | 3.1.3.11, 5.2.4, 5.6 |
| Condition ruled out after evaluation | excluded condition | ruled-out diagnosis, false positive | ISO 13940:2015, health_condition | 3.1.2.11, 5.4.2.4 |
| Professional interpretation of findings | professionally assessed condition | clinical assessment, interpreted finding | ISO 13940:2015, health_condition | 3.1.2.10, 5.5.5 |
| Equipment/software used in screening | medical device | screening equipment, diagnostic tool | ISO 13940:2015, medical_device | 3.1.3.16, 5.2.3 |
| AI/autonomous screening systems | automated medical device | AI system, CAD system, decision support tool | ISO 13940:2015, automatic_medical_device | 3.1.3.17, 5.5.9 |
| Technical/administrative support entity | healthcare supporting organization | reference lab, imaging center, service provider | ISO 13940:2015, healthcare_actor | 3.1.1.8, 5.2.3 |
| Undesirable occurrence or harm | adverse event | complication, screening harm, interval cancer | ISO 13940:2015, adverse_event | 3.1.4.9, 5.4.6.2 |

---

### Table 3.2-2: Terminology Corrections (Ontological Alignment)

**Purpose**: This table documents terminology corrections applied during ontological alignment with ISO 13940. It is provided to assist implementers, explain changes from earlier draft versions, and prevent misinterpretation of core concepts.

| Deprecated / Legacy Term | Preferred Term (Normative) | Clauses Updated | Rationale (Ontology-Based) |
|-------------------------|---------------------------|-----------------|---------------------------|
| **Screening episode** | **Screening clinical process** | 5.1, 5.2, 5.4, 5.5, 5.6 | Screening is an ongoing preventive process, not an event-driven episode of care. Episodes are conditionally derived when diagnostic/treatment triggers occur. |
| **Episode of care (for screening workflow)** | **Clinical process instance** | 5.2.2, 5.2.5, 5.4, 5.5, 5.6 | Per ISO 13940, episodes of care are bounded healthcare delivery containers with specific ownership and closure conditions. Screening is a process that may spawn episodes. |
| **Episode initiation (for screening)** | **Process initiation** OR **Screening process instance creation** | 5.2.2 (Stage 1), 5.4.2.1, 5.5.3, 5.6.2 (T1, T2) | Screening process initiation occurs when eligibility is confirmed and consent obtained. No episode exists until diagnostic trigger. |
| **Episode closure (for negative screening)** | **Process completion** OR **Process transition to recall status** | 5.2.5 (Branch 4A), 5.4.2.5, 5.5.6, 5.6.2 (T9, T10) | Negative screens complete the process and trigger recall scheduling. No episode was created, so "closure" is semantically incorrect. |
| **Episode closure (for positive screening)** | **Process transition with conditional episode derivation** | 5.2.5 (Branch 4B/4C), 5.3.2, 5.3.3 | Positive screens trigger diagnostic episode initiation (Pattern A or B). The screening process transitions; episodes are derived. |
| **Extended episode** | **Co-located diagnostic episode (Pattern A)** | 5.3.3.1, 5.4.2.3, 5.5.7, 5.6.5 | Pattern A involves initiating a diagnostic episode linked to the screening process, not "extending" a screening episode. |
| **Linked episodes** | **Separate linked episodes with responsibility transfer (Pattern B)** | 5.3.3.2, 5.4.2.3, 5.5.7, 5.6.5 | Pattern B involves completing the screening process and initiating a separate diagnostic episode with explicit responsibility transfer. |
| **Episode ID (for screening)** | **Process instance ID** | 5.2.2, 5.3.4, 5.4.5 | Screening is tracked via process instance ID. Episode IDs apply only to resulting diagnostic/treatment episodes. |
| **Episode status (for screening)** | **Process status** | 5.2.6, 5.4.7, 5.6.3 | Administrative states of screening (initiated, active, completed, suspended) are process states, not episode states. |
| **Episode metadata (for screening)** | **Process metadata** | 5.2.2, 5.3.4 | Screening process requires process-level metadata (per 5.2.2). Episode metadata applies to resulting episodes (per 5.3.4). |
| **Entry to screening episode** | **Input to screening process** | 5.4.2.1 (HS-01, HS-02) | Health states HS-01 and HS-02 represent input to the screening process, not episode entry. |
| **Episode outcome (for negative screening)** | **Process output health state** | 5.4.2.3 (HS-05), 5.4.2.5 (HS-10) | The screening process produces an output health state (HS-05, HS-10). Episodes have outcomes only if episodes were created. |
| **Screening episode closure requirements** | **Screening process completion requirements** | 5.2.5, 5.6.2 (T9, T10) | Completion requirements specify what must be documented when screening process transitions to recall status. |
| **Incomplete episode (screening)** | **Suspended process instance** OR **Process termination without resolution** | 5.2.5 (Branch 4D), 5.4.2.4 (HS-12), 5.6.2 (T11) | Lost-to-follow-up scenarios result in process suspension, not incomplete episodes (unless diagnostic episode was created). |
| **Episode transition (screening)** | **Process transition** OR **Health state transition** | 5.4.3, 5.4.6, 5.6.2 | Screening progresses through process transitions and health state transitions. Episode transitions apply only to resulting episodes. |
| **Episode linkage (for screening to diagnostic)** | **Health thread linkage** OR **Process-to-episode linkage** | 5.3.3, 5.3.4, 5.4.6 | Linkage between screening process and resulting episodes uses health thread per ISO 13940. |
| **Multiple screening modalities in same episode** | **Multiple screening modalities in same process instance** | 5.4.6.3 | Multiple modalities (e.g., HPV + Pap) occur within a single screening process instance, not an episode. |
| **Screening episode history** | **Screening process history** OR **Longitudinal screening record** | 5.4.6.2, Module F | A subject's screening history is a sequence of process instances, not episodes (unless diagnostic/treatment episodes resulted). |
| **Screening protocol** | **Core care plan** | 3.1.3.6, 5.2.2, 5.5.3 | Per ISO 13940, evidence-based guidelines are "core care plans" not "protocols" (deprecated term per 3.4.1). |
| **Resultant condition (deprecated)** | **Output health state** | 3.1.2.3, 5.4.2 | ISO 13940 uses "health state" not "resultant condition." |

---

## CLAUSE 3.3 — ISO 13940 CITATION TABLE

**Purpose**: This table provides a comprehensive mapping of ISO 13940 concepts used in P3493.1, with their contsys.org reference and application in this standard.

| ISO 13940 Concept | contsys.org Reference | P3493.1 Definition Clause | P3493.1 Usage |
|-------------------|----------------------|---------------------------|---------------|
| healthcare actor | contsys.org/concept/healthcare_actor | 3.1.1.1 | Foundation for all participant definitions |
| subject of care | contsys.org/concept/subject_of_care | 3.1.1.2 | Individual undergoing screening |
| healthcare provider | contsys.org/concept/healthcare_provider | 3.1.1.3 | Organizations/individuals delivering screening services |
| healthcare personnel | contsys.org/concept/healthcare_actor | 3.1.1.4, 3.1.1.5 | Specialized into professional vs. personnel |
| contact | contsys.org/concept/contact | 3.1.1.6 | Screening appointments and encounters |
| health state | contsys.org/concept/health_state | 3.1.2.1 | Composite health of subject; input/output states |
| health condition | contsys.org/concept/health_condition | 3.1.2.4 | Observable aspects of health state |
| observed condition | contsys.org/concept/health_condition | 3.1.2.5 | Abnormalities detected on screening |
| health issue | contsys.org/concept/health_issue | 3.1.2.7 | Triggering concern for screening/diagnosis |
| health objective | contsys.org/concept/health_objective | 3.1.2.9 | Goals of screening (early detection) |
| clinical process | contsys.org/concept/clinical_process | 3.1.3.1 | Screening modeled as clinical process |
| healthcare activity | contsys.org/concept/healthcare_activity | 3.1.3.2 | Individual screening activities |
| episode of care | contsys.org/concept/episode_of_care | 3.1.3.4 | Resulting diagnostic/treatment episodes |
| care plan | contsys.org/concept/care_plan (implied) | 3.1.3.5 | Patient-specific screening plan |
| core care plan | contsys.org/concept/core_care_plan (implied) | 3.1.3.6 | Evidence-based screening guidelines |
| health thread | contsys.org/concept/health_thread | 3.1.3.7 | Linkage between process and episodes |
| healthcare mandate | contsys.org/concept/healthcare_mandate | 3.1.4.1 | Formal authority for screening activities |
| care period mandate | contsys.org/concept/care_period_mandate | 3.1.4.2 | Screening program mandate |
| healthcare commitment | contsys.org/concept/healthcare_commitment | 3.1.4.3 | Provider acceptance of mandate |
| informed consent | contsys.org/concept/informed_consent | 3.1.4.4 | Permission for screening activities |
| consent competence | contsys.org/concept/consent_competence | 3.1.4.5 | Capability to provide consent |
| health record | contsys.org/concept/health_record | 3.1.5.1 | Repository of screening documentation |
| healthcare information | contsys.org/concept/healthcare_information | 3.1.5.2 | Information relevant to screening |
| healthcare supporting organization | contsys.org/concept/healthcare_actor (under healthcare_third_party) | 3.1.1.8 | Labs, imaging centers providing technical services |
| professionally assessed condition | contsys.org/concept/health_condition | 3.1.2.10 | Professional interpretation of screening findings |
| excluded condition | contsys.org/concept/health_condition | 3.1.2.11 | Conditions ruled out after diagnostic workup |
| healthcare needs assessment | contsys.org/concept/healthcare_needs_assessment | 3.1.3.9 | Eligibility and risk assessment for screening |
| referral | contsys.org/concept/demand_for_care | 3.1.3.10 | Request for diagnostic or treatment services |
| healthcare communication | contsys.org/concept/healthcare_communication | 3.1.3.11 | Result notification and care coordination |
| healthcare process evaluation | contsys.org/concept/healthcare_process_evaluation | 3.1.3.13 | Quality assessment of screening processes |
| clinical process outcome evaluation | contsys.org/concept/clinical_process_outcome_evaluation | 3.1.3.14 | Assessment of screening effectiveness and results |
| healthcare goal | contsys.org/concept/healthcare_goal | 3.1.3.15 | Intermediate objectives supporting health objectives |
| medical device | contsys.org/concept/medical_device | 3.1.3.16 | Equipment and software for screening |
| automatic medical device | contsys.org/concept/automatic_medical_device | 3.1.3.17 | AI systems and autonomous screening tools (P3493.1 uses "automated") |
| adverse event | contsys.org/concept/adverse_event | 3.1.4.9 | Screening harms, complications, interval cancers |
| healthcare documenting | contsys.org/concept/healthcare_documenting | 3.1.3.12 | Record creation and maintenance (P3493.1 uses "documentation") |
| non-ratified healthcare information | contsys.org/concept/healthcare_information | 3.1.5.5 | Information pending professional validation |

---

## CLAUSE 3.4 — DEPRECATED TERMS

The following terms are deprecated in P3493.1. They may appear in earlier drafts, external references, or informal usage. For normative text, use the preferred terms indicated.

### 3.4.1 screening protocol

**DEPRECATED**: Use **core care plan** (3.1.3.6) when referring to evidence-based screening guidelines or pathways.

**NOTE**: The term "screening protocol" appears in earlier drafts and narrative descriptions. For normative text, use "core care plan" to align with ISO 13940 terminology. "Screening protocol" may be used informatively when quoting external sources or in explanatory notes.

---

### 3.4.2 screening episode

**DEPRECATED**: Use **screening process instance** (3.1.3.8) or **screening clinical process** (3.1.3.1) when referring to screening workflow.

**NOTE**: Screening is modeled as a clinical process, not an episode of care. Episodes are conditionally derived when diagnostic or treatment triggers occur.

---

### 3.4.3 resultant condition

**DEPRECATED**: Use **output health state** (3.1.2.3) when referring to the health state at process or episode conclusion.

**NOTE**: ISO 13940 uses "health state" terminology. "Resultant condition" is not an ISO 13940 term.

---

### 3.4.4 episode linkage

**DEPRECATED**: Use **health thread** (3.1.3.7) or **process-to-episode linkage** when referring to continuity connections.

**NOTE**: "Episode linkage" implies both connected items are episodes, which is semantically incorrect when linking a clinical process to an episode.

---

### 3.4.5 provider

**DEPRECATED** (when used without qualifier): Use **healthcare provider** (3.1.1.3), **healthcare professional** (3.1.1.4), or **healthcare personnel** (3.1.1.5) as appropriate.

**NOTE**: "Provider" is ambiguous. Specify whether referring to an organization or individual, and whether the individual has independent clinical authority.

---

## CLAUSE 3.5 — NOTES FOR IMPLEMENTERS

### 3.5.1 Terminology Consistency

When drafting implementation specifications, conformance documents, or ballot responses:

a) Use "screening clinical process" or "process instance" for screening workflow.

b) Use "episode of care" ONLY for diagnostic or treatment episodes conditionally derived from screening.

c) Use "health thread" for linkage, not "episode linkage" (which implies both are episodes).

d) Use "core care plan" for evidence-based guidelines, not "protocol."

e) Use "output health state" for process/episode outcomes, not "resultant condition."

---

### 3.5.2 ISO 13940 Alignment

This Module reflects correct application of ISO 13940 concepts. P3493.1 does NOT extend or modify ISO 13940 definitions but clarifies their usage in cancer screening contexts.

If conflicts arise between this Module and ISO 13940:2015, ISO 13940 takes precedence. Report discrepancies to the P3493.1 Working Group for resolution.

---

### 3.5.3 Backward Compatibility

Systems implementing earlier draft versions that modeled screening as an episode of care will need to refactor to:

a) Introduce "process instance ID" as a distinct identifier.

b) Support conditional episode initiation per triggers T-DIAG and T-TX (Clause 5.3.2).

c) Implement health thread linkage between processes and episodes (Clause 5.3.4).

---

### 3.5.4 Data Governance Implications

The distinction between screening process data and episode data has governance consequences:

a) **Process data** represents population-scale preventive surveillance.

b) **Episode data** represents individualized diagnostic/treatment care.

c) Consent models, secondary use permissions, and data retention policies differ between these categories (see Module E and Module F).

---

### 3.5.5 Quality Measurement

Quality metrics that reference "episodes" must specify whether they measure:

a) Screening process completion rates (e.g., % of eligible subjects who complete screening).

b) Diagnostic episode completion rates (e.g., % of positive screens that complete diagnostic workup).

c) Episode-to-process ratios (e.g., diagnostic episodes per 1000 screening process instances).

---

### 3.5.6 Jurisdictional Variations

Some terms (particularly healthcare professional vs. healthcare personnel) have jurisdiction-specific meanings based on local scope-of-practice regulations. Implementers SHALL:

a) Apply local regulatory definitions when determining who qualifies as a healthcare professional.

b) Document jurisdiction-specific interpretations in their conformance statement.

c) Ensure that clinical decision authority is assigned only to appropriately qualified individuals per local law.

---

## APPENDIX A (INFORMATIVE) — ALPHABETICAL INDEX OF TERMS

| Term | Definition Clause |
|------|-------------------|
| adverse event | 3.1.4.9 |
| automated medical device | 3.1.3.17 |
| care period mandate | 3.1.4.2 |
| care plan | 3.1.3.5 |
| clinical process | 3.1.3.1 |
| consent competence | 3.1.4.5 |
| contact | 3.1.1.6 |
| continuity facilitator mandate | 3.1.4.7 |
| core care plan | 3.1.3.6 |
| dissent | 3.1.4.6 |
| episode of care | 3.1.3.4 |
| excluded condition | 3.1.2.11 |
| health condition | 3.1.2.4 |
| health issue | 3.1.2.7 |
| health objective | 3.1.2.9 |
| health record | 3.1.5.1 |
| health state | 3.1.2.1 |
| health thread | 3.1.3.7 |
| healthcare activity | 3.1.3.2 |
| healthcare actor | 3.1.1.1 |
| healthcare commitment | 3.1.4.3 |
| healthcare communication | 3.1.3.11 |
| healthcare data | 3.1.5.3 |
| healthcare documentation | 3.1.3.12 |
| healthcare goals | 3.1.3.15 |
| healthcare information | 3.1.5.2 |
| healthcare investigation | 3.1.3.3 |
| healthcare mandate | 3.1.4.1 |
| healthcare needs assessment | 3.1.3.9 |
| healthcare personnel | 3.1.1.5 |
| healthcare process evaluation | 3.1.3.13 |
| healthcare professional | 3.1.1.4 |
| healthcare provider | 3.1.1.3 |
| healthcare supporting organization | 3.1.1.8 |
| informed consent | 3.1.4.4 |
| input health state | 3.1.2.2 |
| medical device | 3.1.3.16 |
| metadata | 3.1.5.4 |
| non-ratified healthcare information | 3.1.5.5 |
| observed condition | 3.1.2.5 |
| outcome evaluation | 3.1.3.14 |
| output health state | 3.1.2.3 |
| potential health condition | 3.1.2.6 |
| professionally assessed condition | 3.1.2.10 |
| referral | 3.1.3.10 |
| responsibility transfer | 3.1.4.8 |
| risk condition | 3.1.2.8 |
| screening process instance | 3.1.3.8 |
| subject of care | 3.1.1.2 |
| subject of care proxy | 3.1.1.7 |

**Total: 50 defined terms**

---

## END OF MODULE B
