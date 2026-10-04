# Study Guide: AI-Driven Healthcare Devices
TSA TEAMS 2027, "Engineering a Smarter World"

## 1. The short version

AI-driven healthcare devices use sensors to collect body data (images, ECG, glucose), a trained model to turn that data into a prediction (disease present? risk high? how much insulin?), and an output that either informs a clinician or acts directly on the patient. In the U.S. the FDA regulates them by risk (Class I, II, III) through the 510(k), De Novo or PMA pathways. Because AI models can change after release, the FDA added newer tools: Good Machine Learning Practice (GMLP), Predetermined Change Control Plans (PCCPs) and lifecycle guidance. About three in four FDA-authorized AI devices are in radiology [20]. Hospitals are adopting predictive AI quickly (66% in 2023, 71% in 2024), but fewer of them check every model for accuracy and bias. The economic case is large, with an estimated 5–10% of U.S. health spending ($200–360 billion a year) that could be saved. It depends on models that work at the hospital where they are used, and the Epic Sepsis Model is the standard example of one that did not. The section sheet asks two things: **know the device characteristics in radiology, surgery, treatment and prevention**, and **be able to evaluate the economics**. Sections 3 and 6 cover those two directly. Section 7 has every equation, with each variable defined.

---

## 2. Key terms

| Term | Meaning |
|---|---|
| **Machine learning (ML)** | Software that learns a pattern from example data instead of following hand-written rules. |
| **Neural network / deep learning** | ML built from layers of weighted sums passed through nonlinear functions. It is the main method for reading images and signals. |
| **SaMD** | Software as a Medical Device: software that is itself the medical device, such as an app that reads a retinal photo. |
| **Locked vs. adaptive algorithm** | A locked algorithm gives the same output for the same input every time. An adaptive one keeps learning and changes after deployment. |
| **Autonomous vs. assistive** | Autonomous AI gives a result with no clinician reading it first (IDx-DR). Assistive AI flags or triages and leaves the decision to a human. |
| **Predictive AI** | Models that classify a patient or give a risk score, for example readmission risk, sepsis, or appointment no-show. |
| **Generative AI (GenAI)** | Models that produce text or images, such as drafting clinical notes. |
| **Closed loop** | Sense → decide → act → sense again, with no human step. An "artificial pancreas" is an example. |
| **Data drift** | The data a model sees in use moves away from its training data (a new scanner, a new population), and performance drops. |
| **Bias (algorithmic)** | Performance that is systematically worse for some groups, often because they were underrepresented in training data. |
| **Shadow AI** | Staff using AI tools that the organization has not approved or governed. |

---

## 3. Device characteristics by area (the core of the section)

| Area | What the AI does | Typical sensor / input | Example (verified) | Key characteristics to remember |
|---|---|---|---|---|
| **Radiology / diagnosis** | Detects, segments or triages findings in images | CT, MRI, X-ray, mammography, retinal camera | **IDx-DR** (De Novo, April 2018): the first FDA-authorized *autonomous* AI diagnostic. It detects more-than-mild diabetic retinopathy in primary care. In its 900-patient pivotal trial, published sensitivity was 87.2% and specificity 90.7% [12, 25]. | The largest category. About 76% of the devices on the FDA's AI-Enabled Medical Devices list are radiology [20]. Published tallies of the list put the total at well over 1,000, and it grows with every update, so check the list for the current count [18]. Mostly assistive (triage or second reader) and mostly locked. Performance depends on image quality and on the scanner the model was trained with. |
| **Surgery** | Plans and guides motion, and increasingly carries out sub-tasks | Stereo/3D cameras, force sensors, robot kinematics | **STAR** (Smart Tissue Autonomous Robot, Johns Hopkins, *Science Robotics* 2022): the first laparoscopic surgery done by a robot without human hands. It sewed the two ends of a pig's intestine together (anastomosis) in 4 animals and did better than human surgeons on the same task. A surgeon approved its suture plan first [15]. | Autonomy comes in levels: the human approves the plan, and the robot executes it. Characteristics are real-time computer vision, precision and repeatability. The risks are tissue that deforms or moves, and who is liable when something goes wrong. Still research for soft tissue. |
| **Treatment** | Adjusts therapy automatically | Continuous glucose monitor (CGM) + insulin pump | **Medtronic MiniMed 670G** (PMA, Sept 2016): the first hybrid closed-loop "artificial pancreas". It measures glucose every 5 minutes and automatically gives or withholds basal insulin, for type 1 diabetes in patients 14 and older [13]. **Tandem Control-IQ** (De Novo, Dec 2019) created the Class II "interoperable automated glycemic controller" category (21 CFR 862.1356) [21]. | Closed loop based on control theory (Section 7.5). "Hybrid" means the user still enters mealtime boluses. **Class matters for the test:** the first system (670G, 2016) was Class III and went through PMA. Since Dec 2019, an insulin-dosing *algorithm* that works with compatible pumps and CGMs is **Class II**, through De Novo and then 510(k) [21]. Safety depends on sensor lag and accuracy. |
| **Prevention / monitoring** | Screens continuously for early warning signs | Wearable photoplethysmography (PPG) optical pulse sensor, single-lead ECG | **Apple Heart Study** (*NEJM* 2019, Stanford): 419,297 participants. 0.52% received an irregular-pulse notification. PPV was 0.84 for atrial fibrillation (AFib) appearing on a simultaneous ECG patch, and 34% of those who returned patches had AFib [14]. | Huge populations with low disease prevalence, so false positives matter (Section 7.2). Answers the sheet's "detect arrhythmia before symptoms" question. Consumer device plus clinical follow-up. |
| **Hospital predictive AI** (connects all four) | Risk scores built into the electronic health record (EHR) | EHR data | **Epic Sepsis Model**, externally validated at Michigan Medicine (*JAMA Intern Med* 2021): 38,455 hospitalizations, AUC 0.63, and it missed about two-thirds of sepsis cases [16]. | Shows why **external validation** and **local monitoring** are required. **Regulatory status:** under FDA's CDS guidance, a time-critical sepsis alert is device software (Section 4). Even so, the Epic model was deployed widely inside the EHR without FDA authorization, a gap between the stated policy and what happens in practice. The first FDA-authorized AI sepsis tool is **Prenosis Sepsis ImmunoScore** (De Novo, April 2024). It uses 22 parameters and is built into the EHR [22]. |

**Pattern across all areas:** sensor → signal processing → model → output (to a clinician or to an actuator) → monitoring. Expect questions that ask you to place a device on two scales: *assistive ↔ autonomous* and *locked ↔ adaptive*.

---

## 4. How the FDA regulates AI devices

**Device classes (risk-based):** Class I is low risk. Class II is moderate risk: most AI imaging tools, and since 2019 the automated insulin-dosing controllers [21]. Class III is high risk and life-sustaining: pacemakers, and the first hybrid closed-loop system (MiniMed 670G, 2016).

**Pathways [4]:**
- **510(k):** the device is "substantially equivalent" to a legally marketed *predicate* device. This is how most AI devices reach the market.
- **De Novo:** a new device type with low-to-moderate risk and no predicate. IDx-DR went this way, and it now serves as a predicate for later devices.
- **PMA (Premarket Approval):** for high-risk devices, with clinical trial evidence usually collected under an Investigational Device Exemption (IDE). The review article [4] gives pacemakers and AI that finds hidden lesions on mammograms as examples.

**Timeline of AI-specific policy:**
| Year | Document | What it does |
|---|---|---|
| 2021 (Jan) | **AI/ML-Based SaMD Action Plan** [3] | Five actions: (1) a tailored regulatory framework including a draft PCCP, (2) Good Machine Learning Practice, (3) a patient-centered approach with transparency to users, (4) methods to evaluate and improve algorithms, including bias, (5) pilots for monitoring real-world performance. |
| 2021 (Oct) | **GMLP Guiding Principles** (FDA, Health Canada, UK MHRA) [17] | 10 principles. Examples: multidisciplinary expertise; good software engineering and security; datasets representative of the intended patients; training sets independent of test sets; focus on how the human and the AI perform together; testing under clinically relevant conditions; clear information for users; monitoring deployed models. |
| 2022 (Sept), revised **2026 (Jan 6)** | **Clinical Decision Support (CDS) Software** final guidance [19, 24] | Software is *not* a device only if it meets all 4 criteria: (1) does not analyze images or signals; (2) displays or analyzes medical information; (3) *supports* a clinician's recommendation and does not replace it; (4) lets the clinician independently review the basis for its output. **Time-critical alerts (e.g., sepsis) are devices.** The reason is automation bias: a clinician under time pressure cannot truly review the basis. The 2022 version placed this under criterion 3. The 2026 revision, which replaced it, moved it to **criterion 4** [24]. The 2026 revision also allows a single recommendation when only one option is clinically appropriate. *Rule:* showing every input does **not** make a time-critical alert non-device CDS. |
| 2024 (Dec) | **PCCP final guidance** (FDA) [11] | The manufacturer gets pre-authorization for *planned* future model changes and for how they will be validated. Updates that stay within the plan need no new submission. This solves the problem of an adaptive AI needing re-clearance every time it changes. |
| 2025 (Jan) | **AI-Enabled Device Software Functions: Lifecycle Management and Marketing Submission Recommendations** (draft) [5] | Says what a marketing submission must contain across the *total product lifecycle*: device description, data management (training and test data), model design, performance validation, bias, transparency/labeling, human factors, cybersecurity and post-market monitoring. It was still listed as draft in the sources consulted; check the FDA page for its current status. |

[4] says the PCCP, GMLP and public transparency summaries are the FDA's main answers to the problem of algorithms that learn.

---

## 5. Hospital adoption and governance (ONC/ASTP data brief [6], also on NCBI Bookshelf [7])

Source: AHA Annual Survey IT Supplement, non-federal acute-care hospitals. Published Sept 2025.

- **Use:** 66% (2023) → **71% (2024)** of hospitals used predictive AI integrated with the EHR.
- **Fastest-growing uses:** billing automation, 36% → 61%; scheduling, 51% → 67%. The **most common** use is predicting health trajectories or risk for inpatients.
- **Divide by hospital type:** system-affiliated vs. independent hospitals, 81% vs. 31% (2023) and **86% vs. 37% (2024)**. Small, rural, independent and critical-access hospitals lag.
- **Evaluation (2024, among users):** about 82% evaluated models for accuracy, 74% for bias, and 79% did monitoring after implementation. Fewer did this for *all or most* of their models.
- **Governance:** about three-quarters said multiple groups share accountability for evaluating AI.
- **Model source matters:** EHR-vendor, third-party and self-developed models differ in how they are used and how often they are evaluated.

**Trends for 2026 (Wolters Kluwer experts [2]):** generative AI becomes a "clinical-grade" copilot that automates documentation, finds care gaps and handles communications. It must be validated, have guardrails and keep an expert in the loop. Health systems are "playing catch-up" on governance and writing formal policies against **shadow AI**. AI should support clinicians, not replace them.

---

## 6. Economics: how to evaluate the benefit

**The problem (section sheet):** inpatient care is costly, and the sheet cites a global health-worker shortage of about **10 million by 2030**. That matches the WHO-authored 2022 estimate of **10.2 million** [8]. WHO's 2025 progress report raised it to **11.1 million**, concentrated in the African and Eastern Mediterranean regions [23].

*Careful with the sheet's "$10,000 per day" figure.* KFF/AHA data put the average U.S. hospital **expense per adjusted inpatient day at about $3,300 (2024)**, with California at about $4,700 [9]. Billed *charges*, ICU days and some large academic systems are far higher.

> **Test rule:** if a question draws on the overview ("according to the section sheet", "large U.S. systems"), answer **over $10,000 per day**. Use about **$3,300** only when a question asks for the measured *average hospital expense* per inpatient day. Practice Q8 shows how much the choice changes an ROI.

**Size of the opportunity:**
- NBER Working Paper 30857 (Sahni, Stein, Zemmel, Cutler, 2023): wider AI adoption could cut **5–10% of U.S. health spending, about $200–360 billion a year** (2019 dollars), using current technology, within 5 years, without losing quality or access [10].
- Market and adoption figures quoted in 2026 roundups, including the user-supplied Vocal article [1]: global AI-in-healthcare market about **$36.7B (2025) → $50.7B (2026)**; about **75%** of U.S. health systems use at least one AI application; about **81%** of physicians use AI (vs. 38% in 2023); a reported **ROI of about $3.20 per $1** within about 14 months. *These are secondary, compiled statistics. Use them for context, not as research findings.*

**Where the savings come from:** administrative automation (billing, scheduling, documentation), fewer readmissions and ICU days through early warning, remote monitoring instead of in-person visits, faster image reading (more scans per radiologist), and early detection, which costs less to treat.

**Where costs and risks come from:** buying and integrating the system, validating and monitoring it, cybersecurity, staff training, alert fatigue from false positives, and liability. A model that fails locally, like the sepsis example, can cost more than it saves.

Section 7.6 has a worked ROI calculation.

---

## 7. Equations (every variable defined)

### 7.1 Confusion-matrix metrics
For a test compared against a reference standard:
- **TP** = true positives (sick, flagged)  **FN** = false negatives (sick, missed)
- **TN** = true negatives (healthy, cleared)  **FP** = false positives (healthy, flagged)

$$\text{Sensitivity} = \frac{TP}{TP+FN} \qquad \text{Specificity} = \frac{TN}{TN+FP}$$
$$\text{PPV} = \frac{TP}{TP+FP} \qquad \text{NPV} = \frac{TN}{TN+FN} \qquad \text{Accuracy} = \frac{TP+TN}{TP+TN+FP+FN}$$
- Sensitivity = fraction of sick patients the test catches.
- Specificity = fraction of healthy patients the test correctly clears.
- PPV (positive predictive value) = chance that a positive result is truly sick.
- NPV (negative predictive value) = chance that a negative result is truly healthy.

*Worked example (IDx-DR raw counts [12]):* 173 of 198 diseased participants were detected, so sensitivity = 173/198 ≈ 0.874. 556 of 621 disease-free participants were cleared, so specificity ≈ 0.895. (The published 87.2%/90.7% used weighted statistical analysis, so it differs slightly from the raw ratios.)

### 7.2 Bayes' theorem: why prevalence controls PPV
$$\text{PPV} = \frac{Se \cdot p}{Se \cdot p + (1-Sp)(1-p)}$$
- *Se* = sensitivity, *Sp* = specificity, *p* = prevalence (fraction of the tested population that has the disease).

*Example:* Se = Sp = 0.90.
- At p = 0.01 (screening the general public): PPV = 0.009 / (0.009 + 0.099) ≈ **0.083**, so about 92% of alerts are false.
- At p = 0.20 (a high-risk clinic): PPV = 0.18 / (0.18 + 0.08) ≈ **0.69**.

This is why wearable screening sends positives to confirmatory testing (the ECG patch in [14]).

### 7.3 Logistic model (how a risk score is produced)
$$P(y=1 \mid \mathbf{x}) = \sigma(z) = \frac{1}{1+e^{-z}}, \qquad z = \beta_0 + \sum_{i=1}^{n} \beta_i x_i$$
- *P* = predicted probability of the outcome (e.g., sepsis, readmission); *y* = outcome (1 = event, 0 = no event).
- **x** = vector of patient features; *x_i* = the i-th feature (heart rate, lactate, age …); *n* = number of features.
- *β₀* = intercept (bias term); *β_i* = weight learned for feature *i*.
- *σ* = sigmoid function; *e* = Euler's number (≈ 2.718).

A neural network stacks many of these units, each computing *a = f(Wx + b)*:
- *W* = weight matrix; *b* = bias vector; *f* = nonlinear activation function; *a* = the layer's output.

The weights are found by **gradient descent**:
$$w \leftarrow w - \eta \frac{\partial L}{\partial w}$$
- *w* = a weight; *η* = learning rate (step size); *L* = loss function measuring prediction error; ∂L/∂w = partial derivative of the loss with respect to that weight (Calc BC chain rule = backpropagation).

### 7.4 ROC curve and AUC
$$\text{AUC} = \int_0^1 TPR \; d(FPR)$$
- *TPR* = true-positive rate = sensitivity.
- *FPR* = false-positive rate = 1 − specificity.

The curve plots TPR against FPR as the alert threshold moves. AUC = 0.5 means no better than chance, and 1.0 is perfect. The Epic Sepsis Model's external AUC of **0.63** [16] was much lower than its developer reported. AUC is the probability that a randomly chosen positive case is scored above a randomly chosen negative one.

### 7.5 Closed-loop insulin control (treatment devices)
**Controller (PID, a common textbook form):**
$$u(t) = K_p\, e(t) + K_i \int_0^t e(\tau)\, d\tau + K_d \frac{de(t)}{dt}, \qquad e(t) = G(t) - G_{\text{target}}$$
- *u(t)* = insulin delivery rate commanded at time *t*.
- *e(t)* = error, measured glucose minus target. A positive error means too high, so more insulin.
- *G(t)* = glucose measured by the CGM; *G_target* = setpoint (target glucose).
- *K_p, K_i, K_d* = proportional, integral and derivative gains (tuning constants).
- *τ* = dummy variable of integration.

**Plant (Bergman minimal model of glucose–insulin physiology, AP Bio + Calc):**
$$\frac{dG}{dt} = -\big(S_G + X(t)\big)G(t) + S_G G_b, \qquad \frac{dX}{dt} = -p_2 X(t) + p_3\big(I(t) - I_b\big)$$
- *G* = plasma glucose concentration; *G_b* = basal (fasting) glucose.
- *S_G* = glucose effectiveness, the rate at which glucose clears itself without extra insulin.
- *X(t)* = insulin action in a remote (interstitial) compartment.
- *I(t)* = plasma insulin; *I_b* = basal insulin.
- *p₂* = decay rate of insulin action; *p₃* = rate at which insulin above basal level increases action.
- Meals add a glucose input term, which is omitted here.

Real devices use proprietary versions of PID or model-predictive control. Sensor lag (CGM measures interstitial fluid, minutes behind blood) is why fully closing the loop at meals is hard, and why the 670G is "hybrid" [13].

### 7.6 Economic evaluation
**Savings from fewer readmissions:**
$$S = N \cdot r \cdot \Delta \cdot C_r$$
- *S* = gross savings per year.
- *N* = number of discharges per year.
- *r* = baseline readmission rate (fraction of discharges readmitted).
- *Δ* = relative reduction in readmissions achieved by the AI program.
- *C_r* = average cost of one readmission.

**Savings from fewer bed-days (alternative form):**
$$S = D \cdot C_d$$
- *D* = inpatient bed-days avoided per year; *C_d* = cost per inpatient day.

**Subtract the cost of false alarms:**
$$S_{net} = S - F \cdot c_F, \qquad F = A\,(1 - \text{PPV})$$
- *S_net* = net savings per year after false-alarm costs.
- *F* = number of false-positive alerts per year.
- *c_F* = cost of one false alert (clinician time, extra tests, or a follow-up intervention given to a patient who would not have been readmitted).
- *A* = total alerts the model fires per year; PPV = positive predictive value (Section 7.1).

**Return on investment:**
$$\text{ROI} = \frac{S_{net} - C_{AI}}{C_{AI}}$$
- *C_AI* = total yearly cost of the AI program (license, integration, staff, monitoring).
- ROI > 0 means the program pays for itself within the year.

*Hypothetical example:* N = 10,000, r = 0.15, Δ = 0.10, C_r = $15,000, C_AI = $1.5M.
- Readmissions per year without AI: N·r = 10,000 × 0.15 = 1,500. Avoided: 1,500 × 0.10 = 150.
- S = 10,000 × 0.15 × 0.10 × 15,000 = **$2.25M**.
- Ignoring false alarms: ROI = (2.25 − 1.5)/1.5 = **+0.50**.
- Now count the alarms. The model flags A = 5,000 of the 10,000 discharged patients as high risk, with PPV = 0.20. True positives = A·PPV = 1,000 (of the 1,500 patients who would be readmitted, so sensitivity ≈ 0.67). False positives F = 5,000 × 0.80 = **4,000**. Each flagged patient gets a follow-up intervention (a nurse home visit or pharmacist call) costing c_F = $250, so false alarms cost 4,000 × $250 = $1.0M and S_net = $1.25M.
- ROI = (1.25 − 1.5)/1.5 ≈ **−0.17**. A low PPV turned a profitable program into a loss.
- **Consistency check (use it on any test question):** true positives can never exceed real events, so A·PPV ≤ N·r (here 1,000 ≤ 1,500), and A ≤ N when each patient is flagged at most once. If a question's numbers break this, re-read it.

---

## 8. Practice questions (answers below)

1. A wearable AFib detector has Se = 0.95 and Sp = 0.98. In a population with 2% AFib prevalence, what is its PPV?
2. Name the FDA pathway for a novel, moderate-risk AI device with no predicate.
3. Which document allows an adaptive algorithm to be updated without a new submission?
4. A sepsis alert gives a score but no reasoning a clinician can review. Is it non-device CDS? What if it showed every input and its reasoning?
5. In 2024, what share of hospitals used EHR-integrated predictive AI, and which use grew fastest?
6. Classify IDx-DR, STAR, the MiniMed 670G and the Apple Watch irregular-rhythm notification as assistive or autonomous, and name each one's area.
6b. Which FDA class covers an AI insulin-dosing controller cleared today?
7. A hospital has 20,000 discharges a year, a 12% readmission rate, and an AI that cuts readmissions by 5%. A readmission costs $15,000 and the AI costs $2M a year. Ignoring false alarms, what is the ROI?
8. An AI costs $2M a year and avoids 300 bed-days. Find the ROI using (a) the sheet's $10,000 per day and (b) the KFF average expense of $3,300 per day.

**Answers:**
1. PPV = (0.95·0.02)/(0.95·0.02 + 0.02·0.98) = 0.019/(0.019 + 0.0196) ≈ **0.49**.
2. **De Novo.**
3. A **PCCP** (Dec 2024 final guidance).
4. **No, in both cases.** Without reasoning, it fails criterion 4 because the basis cannot be reviewed. Even with every input shown, a sepsis alert supports a *time-critical* decision, and under the 2026 CDS guidance that also fails criterion 4 (the 2022 version placed it under criterion 3). Either way it is a device.
5. **71%.** Billing automation grew fastest (36% → 61%).
6. IDx-DR: autonomous, radiology/diagnosis. STAR: supervised autonomy, surgery (research). MiniMed 670G: autonomous for basal insulin, treatment. Apple Watch: assistive, prevention.
6b. **Class II** (interoperable automated glycemic controller, 21 CFR 862.1356). The 670G in 2016 was Class III.
7. S = 20,000 × 0.12 × 0.05 × 15,000 = $1.8M, so ROI = (1.8 − 2)/2 = **−0.10**.
8. (a) S = 300 × 10,000 = $3.0M, so ROI = **+0.50**. (b) S = 300 × 3,300 = $0.99M, so ROI ≈ **−0.51**. Which cost figure you use decides the answer.

---

## 9. Assumptions and notes on sources
- "At least 15 sites" is read as 15 distinct web pages. This guide cites **25**, including all seven sources you supplied.
- The section sheet's "Explore More" list has 8 titles for 7 URLs. The titles map as follows: "U.S. Food and Drug Administration" → [3] (the AI/ML Action Plan PDF at the supplied URL); "U.S. Food & Drug Administration: Artificial Intelligence – Enabled Medical Devices" → [20], the FDA's public device list, which was added because no supplied URL pointed to it; NCBI Bookshelf [7] is the NLM copy of the ONC brief [6], so it is cited as a separate site.
- The guide follows FDA's **current** CDS guidance (Jan 2026 revision [24]), which replaced the 2022 version [19]. Older study materials may say "criterion 3" for time-critical alerts. The outcome is the same: they are devices.
- **How the sources were consulted:** the research environment's network blocked direct page loads for every site, including fda.gov, ncbi.nlm.nih.gov, healthit.gov, wolterskluwer.com and vocal.media. Every source below was therefore consulted through **web-search retrieval of its indexed page content** and summaries, not by opening the page directly. All URLs are the real, current addresses returned by search. Where a PubMed Central copy could not be opened to confirm its ID, the publisher page and DOI are given first (e.g., [16]). Where a press page is cited next to a paper (e.g., [12] with [25]), the press page is the one that states the raw counts used in Section 7.1. Re-check any number you plan to quote from memory against the page itself.
- Statistics from source [1] are compiled by a blog-style platform. Prefer the government and peer-reviewed sources when two disagree.

---

## 10. Citations

1. Vocal Media (Futurism). "AI in Healthcare Statistics and Facts 2026." https://vocal.media/futurism/ai-in-healthcare-statistics-and-facts-2026 *(user-supplied; consulted via search index)*
2. Wolters Kluwer. "2026 healthcare AI trends: Insights from experts." Dec 15, 2025. https://www.wolterskluwer.com/en/expert-insights/2026-healthcare-ai-trends-insights-from-experts *(user-supplied)*
3. U.S. FDA. "Artificial Intelligence/Machine Learning (AI/ML)-Based Software as a Medical Device (SaMD) Action Plan." Jan 2021. https://www.fda.gov/media/145022/download *(user-supplied)*
4. "United States Food and Drug Administration Regulation of Clinical Software in the Era of Artificial Intelligence and Machine Learning." *Mayo Clinic Proceedings: Digital Health*, 2025 (PMC12264609). https://pmc.ncbi.nlm.nih.gov/articles/PMC12264609/ *(user-supplied)*
5. U.S. FDA. "Artificial Intelligence-Enabled Device Software Functions: Lifecycle Management and Marketing Submission Recommendations" (draft guidance, Jan 7, 2025). https://www.fda.gov/regulatory-information/search-fda-guidance-documents/artificial-intelligence-enabled-device-software-functions-lifecycle-management-and-marketing *(user-supplied)*
6. ASTP/ONC. "Hospital Trends in the Use, Evaluation, and Governance of Predictive AI, 2023–2024." Data Brief, Sept 2025. https://healthit.gov/data/data-briefs/hospital-trends-use-evaluation-and-governance-predictive-ai-2023-2024/ *(user-supplied)*
7. NLM / NCBI Bookshelf. "Hospital Trends in the Use, Evaluation, and Governance of Predictive AI, 2023–2024." https://www.ncbi.nlm.nih.gov/books/NBK618497/ *(user-supplied)*
8. Boniol M, et al. "The global health workforce stock and distribution in 2020 and 2030: a threat to equity and 'universal' health coverage?" *BMJ Global Health*, 2022 (WHO authors). https://pubmed.ncbi.nlm.nih.gov/35760437/
9. KFF. "Hospital Expenses per Adjusted Inpatient Day" (State Health Facts, AHA data). https://www.kff.org/other/state-indicator/expenses-per-inpatient-day/
10. Sahni N, Stein G, Zemmel R, Cutler DM. "The Potential Impact of Artificial Intelligence on Healthcare Spending." NBER Working Paper 30857, 2023. https://www.nber.org/papers/w30857
11. U.S. FDA. "Marketing Submission Recommendations for a Predetermined Change Control Plan for Artificial Intelligence-Enabled Device Software Functions" (final guidance, Dec 2024). https://www.fda.gov/regulatory-information/search-fda-guidance-documents/marketing-submission-recommendations-predetermined-change-control-plan-artificial-intelligence
12. University of Iowa Carver College of Medicine. "Study shows AI can deliver specialty-level diagnosis in primary care setting" (IDx-DR pivotal trial). https://medicine.uiowa.edu/node/3021
13. Medtronic Newsroom. "Medtronic Receives FDA Approval for World's First Hybrid Closed Loop System for People with Type 1 Diabetes." Sept 28, 2016. https://news.medtronic.com/2016-09-28-Medtronic-Receives-FDA-Approval-for-Worlds-First-Hybrid-Closed-Loop-System-for-People-with-Type-1-Diabetes
14. Perez MV, Mahaffey KW, Hedlin H, et al. "Large-Scale Assessment of a Smartwatch to Identify Atrial Fibrillation." *New England Journal of Medicine* 381:1909–1917, Nov 14, 2019. https://www.nejm.org/doi/full/10.1056/NEJMoa1901183
15. Johns Hopkins University Hub. "Robot performs first laparoscopic surgery without human help." Jan 26, 2022. https://hub.jhu.edu/2022/01/26/star-robot-performs-intestinal-surgery
16. Wong A, et al. "External Validation of a Widely Implemented Proprietary Sepsis Prediction Model in Hospitalized Patients." *JAMA Internal Medicine* 181(8):1065–1070, 2021 (doi:10.1001/jamainternmed.2021.2626; PubMed 34152373). https://jamanetwork.com/journals/jamainternalmedicine/fullarticle/2781313 (free full text also indexed on PubMed Central: https://pmc.ncbi.nlm.nih.gov/articles/PMC8218233)
17. Health Canada. "Good Machine Learning Practice for Medical Device Development: Guiding Principles" (joint FDA / Health Canada / MHRA). https://www.canada.ca/en/health-canada/services/drugs-health-products/medical-devices/good-machine-learning-practice-medical-device-development.html
18. AuntMinnie. "Radiology dominates thirty years of FDA AI device approvals" (secondary tally of the FDA list [20]). https://www.auntminnie.com/imaging-informatics/artificial-intelligence/article/15830219/radiology-dominates-thirty-years-of-fda-ai-device-approvals
19. U.S. FDA. "Clinical Decision Support Software" (final guidance, Sept 28, 2022; revised Jan 6, 2026). https://www.fda.gov/regulatory-information/search-fda-guidance-documents/clinical-decision-support-software
20. U.S. FDA. "Artificial Intelligence-Enabled Medical Devices" (public list of authorized AI devices, updated periodically). https://www.fda.gov/medical-devices/software-medical-device-samd/artificial-intelligence-enabled-medical-devices
21. U.S. FDA, Federal Register. "Clinical Chemistry and Clinical Toxicology Devices; Classification of the Interoperable Automated Glycemic Controller" (final order, Mar 14, 2022; Class II, 21 CFR 862.1356, applicable from Dec 13, 2019, Tandem Control-IQ De Novo DEN190034). https://govinfo.gov/content/pkg/FR-2022-03-14/pdf/2022-05303.pdf
22. CNBC. "Prenosis says AI tool for sepsis approved by FDA." Apr 3, 2024. https://www.cnbc.com/2024/04/03/prenosis-says-ai-tool-for-sepsis-approved-by-fda.html
23. World Health Organization, Executive Board EB156/15. "Global strategy on human resources for health: workforce 2030" (Report by the Director-General, 2025). https://apps.who.int/gb/ebwha/pdf_files/EB156/B156_15-en.pdf
24. Covington & Burling. "5 Key Takeaways from FDA's Revised Clinical Decision Support (CDS) Software Guidance." Jan 2026. https://www.cov.com/en/news-and-insights/insights/2026/01/5-key-takeaways-from-fdas-revised-clinical-decision-support-cds-software-guidance
25. Abràmoff MD, Lavin PT, Birch M, Shah N, Folk JC. "Pivotal trial of an autonomous AI-based diagnostic system for detection of diabetic retinopathy in primary care offices." *npj Digital Medicine* 1:39, 2018 (PMC6550188). https://pmc.ncbi.nlm.nih.gov/articles/PMC6550188/
