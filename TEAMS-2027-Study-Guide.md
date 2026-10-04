# TEAMS 2027 Study Guide: "Engineering a Smarter World"

**For:** a high school team (grades 11/12) taking AP Calculus BC, AP Physics C and AP Biology, competing in TSA TEAMS.
**Theme:** AI, automation and engineering in a "smarter" world. TSA and NCTM call the 2027 theme **"Engineering a Smarter World."** [3][5]
**How it's built:** read the first two sections once as a team. After that, use the guide as a workbook: each topic section ends with a worked example you can redo without looking, and Section 9 has practice problems with answers.

---

## 0. The 60-second version

- **What you're competing in.** TEAMS has **four components**: **Multiple Choice**, **Mathematical Modeling**, **Design/Build**, and an **Essay** that you research and submit *before* competition day. For 2027, TSA and NCTM say "the format and four competition components remain unchanged." At nationals, a narrated **Presentation** replaces the Essay. [1][2][4][5][6]
- **Essay deadline: UNCONFIRMED, check it this week.** A search excerpt of TSA's state-competition page gave **January 12, 2027** as the high school essay deadline, the day before the competition window opens. [5] Only that one source gives this date, and I could not open the page myself, so **treat January 12 as the latest possible date, not the real one**. Your advisor should confirm the exact deadline and submission method in the 2027 rules [2] or the coach portal before Week 2. Plan to have the essay finished by **early January** (Section 2.2), so a slightly earlier deadline will not catch you out.
- **When.** Registration opens August 2026 and closes **January 8, 2027** (two sources: [2][4]). The competition window is **January 13 – February 20, 2027**. Nationals are **June 23–27, 2027, in Orlando, FL** (two sources: [5][9]). [1][4][5]
- **Team size.** **4–6 students** per team for 2027. The 2027 Policies & Rules [2] and a state education news item [4] both say so, independently of [5]. Some older third-party pages say 4–8; ignore them.
- **Engineering disciplines in the theme.** Civil, Computer and Electrical engineering are the core of the theme: **Civil** (resilient infrastructure, smart cities, intelligent transportation), **Computer** (hardware, embedded systems and networks behind smart devices, autonomous systems and AI), and **Electrical** (sensors, communication, electronics, robotics, smart energy). A search excerpt of [5] also listed **Environmental** (clean water, renewable energy, waste management, pollution control) as a fourth, but no other source confirms it, so **treat Environmental as unconfirmed**. This guide puts most of its weight on the three confirmed disciplines and treats environmental topics as a smaller supporting section (3.5), which is still worth a few hours because clean water and solar energy are NAE Grand Challenges that TEAMS themes draw on anyway. [6][26] **Automation** is not a separate discipline; it runs through all of them, so Section 3.1 (feedback control) and Section 3.7 (automated production: throughput, bottlenecks, OEE) cover it directly.
- **Your edge.** AP Calc BC, Physics C and Bio already cover most of the math behind the theme: differential equations, the chain rule, circuits, oscillations, feedback and homeostasis. What you still need is practice **applying** that math quickly to scenarios you haven't seen, plus enough vocabulary about the theme that the scenarios don't slow you down.

### Facts to confirm yourselves (sources disagree, or only one source says it)

Ranked by how much it would hurt to get wrong. Your advisor should check the top two before Week 2.

| Item | What sources say | What to do |
|---|---|---|
| **Essay deadline** (most important: a missed deadline can mean no essay score) | Only one source gives a date: **January 12, 2027** for high school [5], and I could not open that page directly | Confirm the date and upload method in the 2027 rules [2] or the coach portal. Until then, plan to submit by **January 8** |
| **Engineering disciplines** | [5] lists Civil, Computer, Electrical and Environmental. No second source lists Environmental | Check the 2027 theme description on [1]/[5]. If Environmental is not listed, move the Bio & Environment lead's extra hours from Section 3.5 to Sections 3.3 and 3.6 |
| **Which year a page describes** | The URL of [5] ends in "2026". Earlier excerpts of it described 2026 (40 questions / 60 min); later excerpts described 2027 | When you open it, check that the page says 2027 before using any number from it |
| Multiple Choice length | TSA's general TEAMS page: high school gets **80 questions on 8 scenarios in 90 min** [6]. The 2026 state-competition page: **40 questions on 4 scenarios in 60 min** [5] | The 80-in-90 format allows only **67.5 s per question**; the 40-in-60 format allows 90 s. **Train at 60 s per question**, which finishes 80 questions in 80 minutes with a 10-minute buffer and fits the shorter format easily. Check the 2027 rules PDF [2] |
| Math Modeling | **60 minutes** to build a model from given data and check that it works [5][7] | Do the 60-minute drill in Section 6 |
| Scoring weights, calculators, reference materials | Not in any public page I could find | Your advisor should check the 2027 Policies & Rules PDF [2] and the coach materials |
| Essay prompt | Comes out with the 2027 materials. An older high school rubric scores an **abstract**, **content/justification**, and **organization & mechanics** on 0–4 / 5–8 / 9–10 bands with ×1/×2 multipliers [8] | Use Section 8 now and adjust once the prompt is released |

---

## 1. Assumptions I made

1. **You're in the 11/12 division**, since you're all seniors. All of you have finished, or are in the middle of, AP Calc BC, AP Physics C (Mechanics, and E&M where applicable) and AP Bio.
2. **No sources were attached**, so everything here comes from public sources I found. These are listed on the citation page, with notes on how each one was used.
3. **You have about 14 weeks** (early October 2026 to a mid-January to February 2027 competition date). You'll meet as a team about twice a week and study individually in between.
4. **TEAMS questions are application questions.** They give you a short engineering scenario (a sensor network, a water plant, a self-driving shuttle) and ask math and science questions about it. This guide therefore teaches the *models* behind smart systems, not trivia about particular AI products.
5. **You'll check the official 2027 rules PDF** before competition day. My research tools could not open web pages directly, so every source was read through the excerpts a search engine returned for that exact URL (see the note on the citation page). Section 0 says which 2027 facts have two independent sources and which rest on one (the essay deadline and the Environmental discipline). Open the official links yourselves before you rely on a date or format detail.

---

## 2. Your plan: who does what, week by week

### 2.1 Split into specialists (4–6 people)

Each person **owns** one lens, which means they become the team's expert on it. Everyone still does the shared practice problems.

| Role | Owns | Natural fit |
|---|---|---|
| **Controls & Computing lead** | Sections 3.1–3.2 and 3.7 (feedback, PID, ML math, automated production) | Strongest Calc BC student |
| **Electrical & Sensors lead** | Section 3.3 (circuits, ADCs, sampling, energy) | Physics C E&M student |
| **Civil & Smart-City lead** | Section 3.4 (vibration, structural monitoring, traffic) | Physics C Mechanics student |
| **Bio & Environment lead** | Section 3.6 first, then 3.5 (bio-feedback, AlphaFold, water, renewables) | Strongest AP Bio student |
| **Essay lead** (can double up) | Section 8 | Best writer |
| **Build captain** (can double up) | Section 7 | Most hands-on builder |

### 2.2 Fourteen-week schedule

| Weeks | Team meeting focus | Individual homework |
|---|---|---|
| 1–2 (Oct) | Read Sections 0–2. Assign roles. Download the official 2027 rules [2]; advisor confirms the **essay deadline** and the **discipline list** (Section 0 table) | Each lead reads their section and redoes its worked example from memory |
| 3–4 | Teach-backs: each lead takes 10 minutes to teach their section to the others | Practice problems 1–6 (Section 9) |
| 5–6 | First **timed** multiple-choice block (write 10 scenario questions for each other using Section 5) | Problems 7–15. Essay lead drafts a research plan |
| 7–8 (Nov) | First **60-minute modeling drill** (Section 6). Build drill #1 (Section 7) | Essay: outline and source list |
| 9–10 | Second modeling drill, using a new prompt. Build drill #2 | Essay: full draft. Everyone reviews it |
| 11–12 (Dec) | Full mock: 60–90 min of multiple choice, then 60 min of modeling | Fix weak spots and update the formula sheet |
| 13 (early Jan) | Final essay edit and **submit by January 8** unless the confirmed deadline is later | Each lead writes a one-page cheat sheet for their lens |
| 14 | Light review, the day-of checklist (Section 10), and rest | — |

---

## 3. Core content by engineering lens

Every subsection has the same parts: **key ideas**, **formulas**, **how it ties to your AP classes**, and **a worked example**.

### 3.1 Automation and control: how "smart" systems correct themselves

**Key ideas**
- **Open loop:** the system acts without measuring the result (a toaster on a timer). **Closed loop (feedback):** a sensor measures the output, the controller compares it to a **setpoint**, and an actuator corrects the difference. Almost every automated system in the theme is closed-loop: thermostats, cruise control, drone stabilization, automated insulin pumps, smart grids.
- **Error:** e(t) = setpoint − measured value.
- **PID control** is the industry workhorse: [10]
  - **P (proportional):** correction = Kp·e. A bigger error gets a bigger push. Used alone, it usually leaves a **steady-state error**.
  - **I (integral):** correction = Ki∫e dt. It adds up past error and keeps pushing until the error is zero, which **removes steady-state error**.
  - **D (derivative):** correction = Kd·de/dt. It reacts to how fast the error is changing, which **damps overshoot**.
  - u(t) = Kp·e + Ki∫e dt + Kd·de/dt
- **Tuning trade-offs** to remember: raising Kp makes the system faster but causes more overshoot and possible oscillation. Raising Ki removes offset but can cause overshoot or "windup." Raising Kd reduces overshoot but amplifies sensor noise. [10]
- **Negative feedback** reduces the error and stabilizes the system. **Positive feedback** amplifies change (runaway).
- **Levels of automation (vehicles, SAE J3016):** Level 0 no automation, 1 driver assistance, 2 partial automation, 3 conditional, 4 high, 5 full. The level depends on *which features are engaged* at a given moment. [11]

**AP tie-ins**
- Calc BC: separable differential equations, exponential decay, slope fields.
- Physics C: first-order systems (RC circuits) and second-order systems (damped spring-mass oscillators) are the two standard "plant" models in control.
- Bio: homeostasis is negative feedback (blood glucose, thermoregulation).

**Worked example A: a smart thermostat, and why P-only control falls short**
A room loses heat at a rate h(T − Tout), with h = 1 kW/°C, and Tout = 5 °C. A proportional heater supplies Kp(Tset − T), with Kp = 4 kW/°C and Tset = 20 °C.
At steady state, heat in equals heat out:
Kp(Tset − T) = h(T − Tout), so T = (Kp·Tset + h·Tout)/(Kp + h) = (80 + 5)/5 = **17 °C**. The room settles **3 °C short**.
Raising Kp to 9 gives T = (180 + 5)/10 = **18.5 °C**. The error shrinks but never reaches zero. **Adding an integral term is what drives it to 20 °C.** Expect this exact reasoning on the test.

**Worked example B: how fast the room cools when the heat goes off (Newton's law of cooling)**
dT/dt = −k(T − Tout), with T(0) = 20 °C, Tout = 5 °C, k = 0.1 h⁻¹.
The solution is T(t) = 5 + 15e^(−0.1t). To find when the room reaches 17 °C: 12 = 15e^(−0.1t), so t = 10·ln(1.25) ≈ **2.2 h**.

**Reliability of automated systems (quick formulas)**
- Components **in series**, where every one must work: R = R₁·R₂·…
- **Redundant (parallel)** components, where at least one must work: R = 1 − (1 − R₁)(1 − R₂)…
- Example: one sensor with R = 0.95 gives 0.95. Two in series give 0.9025. Two redundant sensors give 1 − 0.05² = **0.9975**. This is why safety-critical automation (aircraft, autonomous vehicles) uses redundant sensors.

---

### 3.2 Computer engineering and AI: the math inside machine learning

**Key ideas**
- **Machine learning (ML)** fits a model to data. Instead of writing the rules by hand, you choose a model with adjustable **parameters** (weights) and adjust them to minimize a **loss function** that measures how wrong the model is.
- **Training versus testing:** a model can memorize its training data (**overfitting**). You judge it on data it hasn't seen.
- **Gradient descent:** repeatedly step the parameters "downhill" on the loss: w ← w − η·dL/dw, where η is the **learning rate**.
- **Backpropagation** is the chain rule applied layer by layer, from the output back toward the input. It computes every dL/dw efficiently. It isn't a separate optimizer; it is the way the gradients for gradient descent get calculated. [12]
- **Neuron:** output = σ(w·x + b). A common activation is the sigmoid σ(z) = 1/(1 + e^(−z)), which has the convenient derivative **σ′(z) = σ(z)(1 − σ(z))**.
- **Classification metrics** (for example, "is this bridge image cracked?"): accuracy, precision, recall, and the confusion matrix. [13]
- **Real-world landmark:** AlphaFold2, an AI system that predicts protein 3D structure from amino-acid sequence, earned Demis Hassabis and John Jumper half of the **2024 Nobel Prize in Chemistry**. David Baker received the other half for computational protein design. [14] This is AP Bio (protein structure determines function) meeting AI.

**Formulas**
- Least-squares line: slope m = Σ(x − x̄)(y − ȳ) / Σ(x − x̄)², and intercept b = ȳ − m·x̄.
- Mean squared error: MSE = (1/n)Σ(yᵢ − ŷᵢ)².
- With TP/FP/FN/TN = true/false positives/negatives:
  - Accuracy = (TP + TN)/total
  - **Precision** = TP/(TP + FP): when the model says "yes," how often is it right?
  - **Recall (sensitivity)** = TP/(TP + FN): of the real "yes" cases, how many does it catch?
  - Specificity = TN/(TN + FP)
  - F1 = 2PR/(P + R)

**Worked example C: gradient descent and the learning rate**
Minimize L(w) = (w − 3)² starting at w₀ = 0 with η = 0.1. The gradient is 2(w − 3).
- w₁ = 0 − 0.1·(−6) = 0.6
- w₂ = 0.6 − 0.1·(−4.8) = 1.08
- In general, (w − 3) gets multiplied by (1 − 2η) each step, so wₙ = 3 − 3(0.8)ⁿ, which converges to 3.
- With η = 1.1 the factor is (1 − 2.2) = −1.2. Its magnitude is above 1, so the iterates **oscillate and diverge**. **Takeaway: a learning rate that's too large makes training blow up, and one that's too small makes it crawl.**

**Worked example D: the chain rule for one neuron**
L = (σ(wx) − y)². Let a = σ(wx). Then
dL/dw = 2(a − y) · a(1 − a) · x.
That's three factors (loss to activation, activation to pre-activation, pre-activation to weight), and it is backpropagation in miniature.

**Worked example E: least-squares fit (a sensor calibration)**
Data (x, y): (1, 2), (2, 4), (3, 5), (4, 7). The means are x̄ = 2.5 and ȳ = 4.5.
Σ(x − x̄)(y − ȳ) = 3.75 + 0.25 + 0.25 + 3.75 = 8, and Σ(x − x̄)² = 5.
So m = 1.6 and b = 4.5 − 4 = 0.5, which gives **ŷ = 1.6x + 0.5**.

**Worked example F: an AI crack detector, and why "90% accurate" can mislead**
There are 1,000 bridge images, and 50 actually show cracks. The model finds 45 of the 50 cracks and also flags 95 of the 950 good images.
- TP = 45, FN = 5, FP = 95, TN = 855
- Accuracy = 900/1000 = **90%**
- Recall = 45/50 = **90%**
- Precision = 45/140 ≈ **32%**, so about two-thirds of the alarms are false
- F1 ≈ 0.47
- A lazy model that always answers "no crack" scores **95% accuracy** while catching zero cracks.
- **Lesson:** when a condition is rare, accuracy is a poor metric. Ask which costs more, a missed crack (a false negative) or a wasted inspection (a false positive). This is Bayes' theorem in disguise, and it is a favorite test angle.

**Trustworthy AI vocabulary (useful in the essay too)**
NIST's AI Risk Management Framework (AI RMF 1.0, January 2023) lists seven characteristics of trustworthy AI: **valid and reliable; safe; secure and resilient; accountable and transparent; explainable and interpretable; privacy-enhanced; fair, with harmful bias managed.** [15] Its four core functions are **Govern, Map, Measure, Manage**. Govern runs across the other three. [16] The characteristics can conflict (for example, accuracy versus explainability), so engineers have to state the trade-offs explicitly.

---

### 3.3 Electrical engineering: sensors, signals and smart energy

**Key ideas**
- A **sensor** turns a physical quantity (temperature, strain, light, chemical concentration) into an electrical signal. An **ADC (analog-to-digital converter)** turns that signal into numbers a computer, or an AI model, can use.
- **Smart grid:** a power grid with digital sensing, two-way communication and automated control that responds to supply and demand in real time. **Demand response** means customers shift or cut usage at peak times in return for incentives, for example a utility cycling air conditioners and water heaters. [17]
- **The energy cost of AI:** the IEA estimates data centers used about **415 TWh in 2024 (about 1.5% of world electricity)**. Its base case projects about **945 TWh by 2030**, with AI as the biggest driver of the growth. The US accounted for about 45% of 2024 data-center use. [18]

**Formulas (from Physics C E&M)**
- Ohm's law V = IR. Power P = IV = I²R = V²/R. Energy E = P·t (1 kWh = 3.6 MJ).
- **Voltage divider:** Vout = Vin · R₂/(R₁ + R₂). This is how a thermistor or photoresistor becomes a readable voltage.
- **RC circuit:** τ = RC. Charging follows V(t) = V₀(1 − e^(−t/τ)), which reaches 63% at t = τ and more than 99% at 5τ. Discharging follows V₀e^(−t/τ).
- **ADC resolution:** step = Vref/2ⁿ for an n-bit ADC.
- **Sampling (Nyquist):** sample at more than **twice** the highest frequency you need to capture, or you get aliasing.
- **Data-center efficiency (PUE):** total facility energy divided by IT equipment energy. A value of 1.0 would be perfect.

**Worked example G: thermistor divider**
Vin = 5 V, R₁ = 10 kΩ fixed, and an NTC thermistor as R₂ (10 kΩ at 25 °C).
At 25 °C, Vout = 5·10/20 = **2.5 V**. When it's hotter, the NTC resistance falls to 5 kΩ, so Vout = 5·5/15 ≈ **1.67 V**.
A 10-bit ADC with Vref = 5 V resolves 5/1024 ≈ **4.9 mV** per step.

**Worked example H: AI energy growth rate**
Growth from 415 to 945 TWh over 6 years is a factor of 2.277. The annual rate is 2.277^(1/6) − 1 ≈ **14.7% per year**. 945 TWh/yr ÷ 8,760 h ≈ **108 GW** of average continuous demand, roughly the output of a hundred large power plants (about 1 GW each).

**Solar (renewables for smart energy)**
- Panel power ≈ irradiance × area × efficiency. At standard test conditions (1000 W/m², 25 °C), a 1.7 m² panel at 22% gives ≈ 374 W.
- NREL tracks record research-cell efficiencies. The top multijunction cells reach about **47.6%**, while ordinary silicon panels are far lower. [19]

---

### 3.4 Civil engineering: resilient infrastructure and smart cities

**Key ideas**
- **Structural health monitoring (SHM):** networks of sensors (strain gauges, accelerometers, low-power wireless nodes) watch bridges continuously, catching internal or microscopic damage that the required two-year visual inspection can miss. Inspection shifts from "time-based" to continuous. [20][21]
- **Vibration as a damage signal:** a structure's natural frequency depends on stiffness and mass. Cracks and corrosion lower stiffness, so the frequency drops.
- **Adaptive signal control technology (ASCT):** traffic signals that adjust red, yellow and green timing using real-time detector data and algorithms. FHWA reports typical improvements of **10% or more** in travel time, delay and emissions, and a Phoenix-area pilot reported travel-time savings of up to 51% on weekdays. [22]

**Formulas (Physics C Mechanics)**
- Spring-mass: ω = √(k/m) and f = (1/2π)√(k/m). So **f ∝ √k**: if stiffness drops to fraction r, frequency drops to √r.
- Hooke's law and strain: σ = Eε, with strain ε = ΔL/L.
- Damped oscillator: m·x″ + c·x′ + k·x = 0. A second-order system like this is exactly what a controller or an SHM algorithm models.
- **Signal capacity:** capacity = s · (g/C), where s is the saturation flow (about 1800 veh/h per lane), g is the green time and C is the cycle length.

**Worked example I: detecting bridge damage from frequency**
A bridge mode with m = 1000 kg (effective) and k = 4.0×10⁵ N/m has ω = 20 rad/s, so f ≈ **3.18 Hz**. After damage, k = 3.24×10⁵ N/m, giving ω = 18 rad/s and f ≈ **2.86 Hz**.
A **19% loss in stiffness shows up as only a 10% frequency drop**, so monitoring systems need precise sensors and good baselines. To capture a 50 Hz vibration you must sample above **100 Hz** (Nyquist).

**Worked example J: adaptive signal timing**
Demand is 700 veh/h, s = 1800 veh/h, and C = 90 s with g = 30 s. Capacity = 1800·30/90 = **600 veh/h**, so the queue grows by 100 veh/h. An adaptive controller would raise green time to at least 700/1800·90 = **35 s**.

---

### 3.5 Environmental engineering: clean water and renewable energy (supporting section)

*Environmental is listed as a 2027 discipline by only one source (see Section 0). The math here (v³ scaling, mass balance, first-order decay) is used throughout the test anyway, so this section is worth a few hours; spend more only once Environmental is confirmed.*

**Key ideas**
- **Standard drinking-water treatment:** coagulation (chemicals make small particles stick together), flocculation (gentle mixing forms heavier "flocs"), sedimentation (the flocs settle), filtration (sand, gravel, charcoal), and disinfection (to kill pathogens and protect the distribution pipes). [23] "Smart" plants add continuous sensors (turbidity, chlorine residual, pH) and automated dosing control, which is Section 3.1 applied to water.
- **Wind power:** P = ½ρAv³. Power scales with **v³** (doubling the wind speed gives 8× the power) and with rotor area, which goes as radius². **Betz's limit:** no turbine can capture more than **16/27 ≈ 59.3%** of the wind's kinetic energy, because the air has to keep moving through the rotor. [24][25]
- Ties to the NAE Grand Challenges, which TEAMS themes draw on: *provide access to clean water*, *make solar energy economical*, *restore and improve urban infrastructure*, *secure cyberspace*, *reverse-engineer the brain*, *advance health informatics*. [26][6] The UN Sustainable Development Goals, especially Goal 6 (clean water) and Goal 7 (clean energy), are another source TEAMS themes draw on. [27]

**Formulas**
- **Chemical dose (mass balance):** 1 mg/L × 1 ML (megaliter) = 1 kg. So dose rate (kg/day) = concentration (mg/L) × flow (ML/day).
- **First-order decay**, for example of chlorine residual: C(t) = C₀e^(−kt), which has half-life ln2/k.

**Worked example K: wind turbine**
Rotor radius 50 m, so A = π·50² ≈ 7854 m². With ρ = 1.2 kg/m³ and v = 10 m/s:
P_wind = ½·1.2·7854·1000 ≈ **4.71 MW**. The Betz maximum is 16/27 of that, ≈ **2.79 MW**.

**Worked example L: water plant dosing**
A plant treats 20 ML/day at a chlorine dose of 2 mg/L, which needs **40 kg/day**. If the residual decays with k = 0.05 h⁻¹, the time to fall from 2.0 to 0.2 mg/L is ln(10)/0.05 ≈ **46 h**. This is why utilities add booster chlorination in long pipe networks.

---

### 3.6 Biology and health: where AP Bio meets automation

- **Automated insulin delivery ("artificial pancreas"):** a continuous glucose monitor (CGM) under the skin measures glucose about every five minutes, and an algorithm automatically adjusts basal insulin from a pump. The FDA approved the first hybrid closed-loop system (Medtronic MiniMed 670G) in 2016. "Hybrid" means users still enter meal doses by hand. [28] This is negative feedback built in hardware to copy the body's own glucose control, which ties directly to AP Bio homeostasis.
- **Enzyme kinetics in biosensors:** many glucose sensors rely on an enzyme reaction. Michaelis–Menten: v = Vmax[S]/(Km + [S]). The response is roughly linear only when [S] ≪ Km, which is a sensor-design constraint.
- **Population models (Calc BC logistic DE):** dP/dt = rP(1 − P/K), with solution P = K/(1 + Ae^(−rt)) where A = (K − P₀)/P₀. Fastest growth happens at P = K/2. This applies to bioreactors, adoption of a technology, and spread of a contaminant.
- **AI in biology:** AlphaFold2 predicted structures for essentially all of the roughly 200 million known proteins, and it has been used by more than 2 million people in 190 countries. [14] Know the chain: sequence → fold → function.

---

### 3.7 Automated production: throughput, bottlenecks and equipment effectiveness

"Automation" in the theme is not only robots and AI. It is also the factories, warehouses and logistics systems that move things through a line. Scenarios about a robotic assembly line, an automated warehouse or a package-sorting center usually reduce to three ideas.

**Key ideas**
- **Little's Law:** L = λW. The average number of items in a system (L, work in process) equals the average arrival or throughput rate (λ) times the average time each item spends inside (W). In factory language, **WIP = throughput × cycle time**. It holds for any stable system: a production line, a queue of cars, packets in a network, patients in a clinic. [30]
- **Bottleneck:** a line can never run faster than its slowest station. Line throughput = min(station rates). Speeding up any other station does nothing, which is why automating the wrong step wastes money.
- **Utilization:** ρ = arrival rate ÷ service rate. When ρ approaches 1, queues and waiting times grow very quickly, so real systems are designed to run below full utilization.
- **OEE (Overall Equipment Effectiveness):** OEE = Availability × Performance × Quality. Availability is the share of planned time the machine actually runs, Performance is actual speed ÷ rated speed, and Quality is good parts ÷ total parts. One weak factor drags down the whole product. [31] About 85% is a commonly quoted "world-class" figure for discrete manufacturing. [32]

**AP tie-ins**
- Calc BC: Little's Law is accumulation, ∫(inflow − outflow) dt, averaged over time. Rates in, rates out, and what piles up in between.
- Physics C: throughput limits behave like the series resistors of a circuit: the "weakest link" sets the flow.
- Bio: enzyme saturation (Section 3.6) is a bottleneck. Once every enzyme is busy (v near Vmax), adding substrate does not raise the rate.

**Worked example M: an automated packaging line**
Three stations: a robot picker (12 boxes/min), a sealer (8 boxes/min), and a labeler (15 boxes/min).
- Line throughput = min(12, 8, 15) = **8 boxes/min**. The sealer is the bottleneck.
- Buying a faster labeler changes nothing. A second sealer in parallel (16 boxes/min) moves the bottleneck to the picker, giving **12 boxes/min**, a 50% gain.
- If the line holds 40 boxes in process at 8 boxes/min, Little's Law gives W = L/λ = 40/8 = **5 min** from entry to exit.

**Worked example N: OEE**
A machine is planned for 480 min and is down for 48 min, so Availability = 432/480 = 0.90. It runs at 95% of rated speed, so Performance = 0.95. 2% of its parts are scrapped, so Quality = 0.98.
OEE = 0.90 × 0.95 × 0.98 ≈ **0.84 (84%)**. The biggest loss is downtime, so a predictive-maintenance AI that cuts downtime in half (Availability 0.95) raises OEE to about **88%**.

---

## 4. Formula sheet (copy it onto one page)

| Topic | Formula |
|---|---|
| PID | u = Kp·e + Ki∫e dt + Kd·de/dt |
| P-only steady state (thermal) | T = (Kp·Tset + h·Tout)/(Kp + h) |
| Newton cooling | T = Tamb + (T₀ − Tamb)e^(−kt) |
| Reliability | series ΠRᵢ; parallel 1 − Π(1 − Rᵢ) |
| Gradient descent | w ← w − η·∇L |
| Sigmoid derivative | σ′ = σ(1 − σ) |
| Least squares slope | Σ(x − x̄)(y − ȳ)/Σ(x − x̄)² |
| Precision / recall | TP/(TP + FP) ; TP/(TP + FN) |
| Divider | Vout = Vin·R₂/(R₁ + R₂) |
| RC | τ = RC; time to fraction p when charging: t = −τ·ln(1 − p) |
| ADC step | Vref/2ⁿ |
| Nyquist | f_sample > 2·f_max |
| Natural frequency | f = (1/2π)√(k/m) |
| Signal capacity | s·g/C |
| Wind | P = ½ρAv³·Cp, Cp ≤ 16/27 |
| Solar | P = G·A·η |
| Dose | kg/day = mg/L × ML/day |
| Growth rate | r = (final/initial)^(1/years) − 1 |
| Logistic | P = K/(1 + Ae^(−rt)) |
| Michaelis–Menten | v = Vmax[S]/(Km + [S]) |
| Little's Law | L = λW (WIP = throughput × cycle time) |
| Bottleneck | line rate = min(station rates) |
| OEE | Availability × Performance × Quality |
| MC pacing | 90 min ÷ 80 Q = 67.5 s; train at 60 s |

---

## 5. Multiple Choice: how to score

The questions come in **scenario blocks**: a short engineering story followed by several questions about it. [5][6]

1. **Divide and conquer.** At the start, the person with the scenario sheet routes each block to the lead who owns that lens. Each lead answers their block, and a second person checks the risky ones.
2. **Pace.** Do the arithmetic first: 90 min ÷ 80 questions = **67.5 s per question**, and 60 min ÷ 40 = 90 s. **Train at 60 s per question.** That finishes the 80-question version with about 10 minutes to spare and the 40-question version with 20 minutes to check work. If a question passes **90 s**, mark it, guess, and move on. Because each lead works their own scenario block in parallel (point 1), use the spare time for a second person to check the flagged questions.
3. **Read the last line first.** Find out what's being asked (a number? units? a concept?) before you read the story.
4. **Use units to eliminate answers.** A power answer in joules is wrong. A frequency answer that rises when stiffness drops is wrong.
5. **Estimate before you compute.** Use the scaling laws: v³ for wind, √k for frequency, e^(−t/τ) for decay. Wrong answer choices are often off by a factor of 2, 10 or π, so a quick estimate can eliminate them.
6. **Watch for the base-rate trap** (Worked example F) and the **P-only offset** (Worked example A).
7. **Never leave a blank** unless the 2027 rules say wrong answers are penalized (check [2]).

**Write your own scenarios.** Each lead writes one 5-question scenario per week on their lens, using the worked examples as templates. Swap them and time each other. Writing questions is one of the fastest ways to learn the material.

---

## 6. Mathematical Modeling: 60 minutes, one open-ended problem

You get a scenario and data, and you have **60 minutes** to build a model that produces a solution and check that it works. [5][7] The process below follows the GAIMME modeling guidelines (SIAM/COMAP). [29]

**Timeline**

| Minutes | Step |
|---|---|
| 0–8 | **Define the problem.** Restate the question in one sentence. List what the client actually wants (a ranking? a number? a rule?) |
| 8–15 | **Assumptions.** Write them down with a one-line reason each, for example "assume constant traffic during the peak hour because the data show less than 10% variation" |
| 15–35 | **Build the model.** Name variables with units. Choose the simplest fitting form: linear, exponential, logistic, weighted scoring, or optimization |
| 35–45 | **Solve and test.** Plug in the given data. Check one case by hand. Check the extreme cases (zero input, very large input) |
| 45–52 | **Sensitivity.** Change one key assumption by ±10–20% and see whether the answer changes |
| 52–60 | **Communicate.** Give a clear final answer, a short justification, and the model's strengths and limitations |

**Model forms to know cold**
- **Weighted decision matrix:** score = Σ wᵢ·(normalized criterionᵢ). Normalize each criterion with (x − min)/(max − min), and flip it when lower is better.
- **Exponential or logistic fits:** take logs to linearize (ln y versus t), then use the least-squares formula.
- **Optimization:** set up the objective, take the derivative, set it to 0, and check the endpoints (Calc BC).
- **Rates and accumulation:** ∫(inflow − outflow) dt, as in queues, reservoirs or battery charge.

**Practice prompt (try it timed before reading the sketch)**
*A city wants to place AI traffic cameras at 3 of 8 intersections. You're given the crash count, daily traffic volume and installation cost for each intersection. Build a method to choose the three.*

**Solution sketch.** Normalize crashes per million vehicles (risk), volume (impact) and cost (lower is better). Weight them, for example 0.5 risk, 0.3 impact, 0.2 cost, and justify the weights. Rank the intersections and pick the top 3. Then do sensitivity: does the top 3 change if the weights shift to 0.4/0.4/0.2? If it does, report both rankings and say why. Limitations: crash data are noisy, and cameras can raise privacy concerns (NIST "privacy-enhanced," [15]).

---

## 7. Design/Build: prepare without knowing the challenge

The challenge is hands-on, tied to the annual theme, and uses simple materials provided on competition day. [7] You can't know the challenge in advance, so practice the **process**.

**Process (posted on your wall)**
1. **Read the scoring criteria twice.** Circle what earns points (load? distance? accuracy? cost?).
2. **Sketch 3 ideas in 3 minutes**, then pick one. Don't argue for more than 2 minutes.
3. **Assign roles:** builder, materials manager, tester, timekeeper.
4. **Build a quick prototype, test it, then improve.** Leave **at least 25%** of the time for testing and fixing.
5. **Use physics to make decisions:** triangles for rigidity, a low center of mass for stability, short members in compression (they buckle less), and less friction where things move.

**Themed drills (30 minutes each, with household materials)**
- **"Smart" sorter:** using paper, tape and straws, build a passive ramp that separates large marbles from small ones. Score it by sort accuracy, which also makes it a precision and recall exercise.
- **Self-correcting structure:** build a paper tower that holds a cup at a set height. A teammate adds coins one at a time, and you adjust the design between rounds. That's feedback in action.
- **Feedback balance:** build a lever that stays level as a load moves, using only counterweights. Talk through what a P-only versus a PI correction would mean.

---

## 8. Essay: write it before competition day

Each team researches and writes one essay on the provided prompt and submits it electronically **before** the competition date. [6][7] The 2027 prompt comes out with the official materials, so check [1]/[2]. An older official high school rubric shows what judges look for: an **abstract**, **content and justification**, and **organization and mechanics**, scored on minimal (0–4) / adequate (5–8) / exemplary (9–10) bands with some criteria weighted ×2. [8] Confirm the 2027 version.

**Plan**
1. **Week 5:** essay lead builds a source list (start with the sources in this guide) and a thesis that answers the prompt directly.
2. **Week 7:** outline:
   - **Abstract** (about 100 words): the problem, your proposed solution, and why it works.
   - **Background:** the engineering problem, with numbers (for example, IEA data-center energy [18], FHWA bridge monitoring [20]).
   - **Proposed solution:** sensors → data → model/AI → automated action → human oversight.
   - **Justification:** at least one quantitative estimate, such as energy saved, delay reduced, or detection rate. Reuse a worked example from Section 3.
   - **Risks and ethics:** use the NIST trustworthy-AI characteristics [15], including bias, privacy, safety and failure modes, plus redundancy (Section 3.1).
   - **Conclusion and citations.**
3. **Week 9:** full draft. **Week 10:** everyone reviews it against the rubric. **Week 13:** final proofread and submission check.

**Strong angles that fit "Engineering a Smarter World"**
- Sensors and AI for bridge monitoring: catch damage early, with human inspectors kept in the loop.
- AI-driven demand response that offsets the growing electricity demand of AI data centers.
- Smart water plants: automated dosing control plus contamination detection.
- Closed-loop medical devices (an artificial pancreas) as a model for safe automation.

---

## 9. Practice problems (answers below)

1. Two independent sensors are each 98% reliable, and the system works if either one works. What is the system reliability?
2. An RC circuit has R = 47 kΩ and C = 22 µF. Find τ and the time to charge to 90%.
3. Wind speed rises from 6 to 9 m/s. By what factor does available power increase?
4. Minimize L(w) = w² − 4w + 1 with gradient descent, w₀ = 0, η = 0.25. Find w₁ and w₂ and the value it converges to.
5. A fault detector monitors 5,000 machines, and 2% are actually faulty. Recall is 95% and the false-positive rate is 3%. What is the precision?
6. What is the step size of a 12-bit ADC over 0–3.3 V?
7. A chip at 90 °C sits in 30 °C air with k = 0.5 min⁻¹. How long until it is below 50 °C?
8. A bioreactor culture follows the logistic model with K = 10⁹, r = 0.7 h⁻¹ and P₀ = 10⁶. When does it reach K/2?
9. A bridge's measured natural frequency drops from 4.0 Hz to 3.6 Hz, and its mass is unchanged. What percentage of stiffness was lost?
10. A home uses 30 kWh/day, gets 5 peak-sun-hours, and uses 400 W panels with 80% system efficiency. How many panels does it need?
11. A plant treats 15 ML/day at 1.5 mg/L chlorine. How many kg/day of chlorine is that?
12. A signal has s = 1800 veh/h, C = 120 s, and demand of 600 veh/h. What is the minimum green time?
13. A 10 kW GPU server runs 24 h in a facility with PUE 1.3. What is the total facility energy?
14. A vehicle keeps its lane and speed automatically, but the driver must supervise at all times. What SAE level is it?
15. Data-center use goes from 415 to 945 TWh in 6 years. What is the annual growth rate?
16. An automated warehouse ships 300 orders/hour, and each order spends an average of 12 minutes in the system. How many orders are in process at any moment?
17. A machine has Availability 0.85, Performance 0.90 and Quality 0.99. What is its OEE, and which factor should you fix first?

**Answers**
1. 1 − 0.02² = **0.9996**
2. τ = 1.03 s; t = τ·ln10 ≈ **2.38 s**
3. (9/6)³ = **3.375×**
4. The gradient is 2w − 4. w₁ = **1**, w₂ = **1.5**, and it converges to **2** (the error halves each step).
5. 100 faulty machines give 95 TP. FP = 0.03 × 4900 = 147. Precision = 95/242 ≈ **39%**
6. 3.3/4096 ≈ **0.81 mV**
7. 20 = 60e^(−0.5t), so t = 2·ln3 ≈ **2.2 min**
8. A = 999; t = ln(999)/0.7 ≈ **9.9 h**
9. Stiffness scales as (3.6/4.0)² = 0.81, so **19%** was lost.
10. 30/(0.4·5·0.8) = 18.75, so **19 panels**
11. **22.5 kg/day**
12. g ≥ 600/1800 × 120 = **40 s**
13. 10 × 24 × 1.3 = **312 kWh**
14. **Level 2** (partial automation) [11]
15. ≈ **14.7% per year**
16. L = λW = 300/h × 0.2 h = **60 orders**
17. 0.85 × 0.90 × 0.99 ≈ **0.76 (76%)**. Availability is lowest, so fix downtime first.

---

## 10. Day-of checklist

- [ ] Essay submitted and confirmation saved, before the **confirmed** deadline in the 2027 rules [2] (January 12, 2027 per [5] is unconfirmed; aim for January 8)
- [ ] Calculators and any allowed reference materials, both confirmed against the rules [2]
- [ ] A one-page cheat sheet per lens, if reference materials are allowed
- [ ] A role for each component agreed in advance (scenario routing, modeling scribe, build captain)
- [ ] A watch or timer, and the pace target of 60 s per multiple-choice question (never more than 67.5 s on average if the test is 80 questions in 90 minutes)
- [ ] Modeling: write the assumptions down; check one case and one extreme case; give a clear final answer
- [ ] Build: read the scoring twice, prototype early, and save 25% of the time for testing

---

## 11. Citation page

**How these sources were consulted.** My research tools could not open web pages directly: the network blocked direct page loads for every site. Each source below was therefore consulted through a web search that returned that exact URL together with an excerpt of its text, and only facts that appeared in those excerpts are attributed to it. Every URL was copied from search results, not typed from memory or pieced together. Because I could not load the pages myself, **open the official TSA links ([1], [2], [5]) before you rely on a date, deadline or format detail**. Section 0 marks which 2027 facts appeared in two independent sources (team size, registration close, nationals dates) and which appeared in only one, [5] (the essay deadline and the Environmental discipline). [5] needs extra care: its URL ends in "2026", and its excerpts described the 2026 competition at one point and 2027 at another.

1. TSA, "2027 TEAMS." https://tsaweb.org/teams/2027-teams (2027 format and four components unchanged, registration and competition dates, NCTM partnership)
2. TSA, "2027 TEAMS Policies & Rules" (PDF). https://tsaweb.org/docs/teamslibraries/2027/2027-policies-rules---home-page.pdf (4–6 students per team, registration deadline January 8, 2027, fees, in-person competition; the place to confirm format, scoring and materials)
3. NCTM, "NCTM Partners with TSA to Support TEAMS, a STEM Competition." https://www.nctm.org/News-and-Calendar/News/NCTM-News-Releases/NCTM-Partners-with-TSA-to-Support-TEAMS,-a-STEM-Competition/ (NCTM–TSA partnership, 2027 theme "Engineering a Smarter World")
4. Pennsylvania Dept. of Education SAS, TEAMS news item. https://www.pdesas.org/Main/News/873131 (registration dates, fees, 4–6 students per team, four components unchanged)
5. TSA, "State Competition." https://tsaweb.org/teams/state-competition-2026 (later excerpts carried 2027 information: theme "Engineering a Smarter World"; disciplines civil, computer, electrical and environmental (environmental not confirmed elsewhere); teams of 4–6; high school essay due January 12, 2027 (not confirmed elsewhere); competition window January 13 – February 20, 2027; nationals June 23–27, 2027, Orlando. When the same URL described the 2026 competition, its excerpt gave 40 questions / 60 min / 4 scenarios and a 60-minute math modeling component)
6. TSA, "TEAMS." https://tsaweb.org/teams (program overview; 80 questions / 90 min / 8 scenarios for high school; essay submitted in advance; themes based on NAE Grand Challenges and UN SDGs)
7. TSA, "TEAMS National Competition: Competition Components." https://tsaweb.org/teams/national-competition/competitions/competition-components (Design/Build, Math Modeling, Multiple Choice, Presentation at nationals)
8. Long Branch Public Schools (hosting a TEAMS document), "High School Rubric." https://www.longbranch.k12.nj.us/cms/lib/NJ01001766/Centricity/Domain/1537/High_School_Rubric.pdf (older essay rubric criteria and score bands)
9. TSA, "2027 National TEAMS Competition." https://tsaweb.org/teams/national-competition (2027 nationals components; nationals June 23–27, 2027, Orlando)
10. Association for Advancing Automation (A3), "PID Tuning." https://www.automate.org/glossary/pid-tuning (P, I, D roles and tuning trade-offs)
11. ANSI Webstore, SAE J3016 listing. https://webstore.ansi.org/standards/sae/sae30162018 (six levels of driving automation)
12. APXML, "Backpropagation and the Chain Rule." https://apxml.com/courses/calculus-essentials-machine-learning/chapter-5-chain-rule-backpropagation/backpropagation-chain-rule (backpropagation as the chain rule)
13. Google for Developers, "Machine Learning Crash Course." https://developers.google.com/machine-learning/crash-course (classification: confusion matrix, accuracy, precision, recall)
14. EMBL, "AlphaFold wins Nobel Prize in Chemistry 2024." https://www.embl.org/news/science-technology/alphafold-wins-nobel-prize-chemistry-2024/ (2024 Nobel, AlphaFold2 reach)
15. NIST AI Resource Center, "AI RMF: Trustworthiness characteristics." https://airc.nist.gov/airmf-resources/airmf/3-sec-characteristics/ (the seven characteristics)
16. I.S. Partners, "NIST AI RMF Core Functions: Govern, Map, Measure, Manage." https://www.ispartnersllc.com/hubs/nist-ai-rmf/core-functions/ (the four functions)
17. U.S. Department of Energy, "Demand Response." https://www.energy.gov/oe/demand-response (demand response, smart grid)
18. International Energy Agency, "Energy and AI: Executive Summary." https://www.iea.org/reports/energy-and-ai/executive-summary (415 TWh in 2024, about 945 TWh in 2030)
19. National Renewable Energy Laboratory, "Best Research-Cell Efficiency Chart." https://www.nrel.gov/pv/cell-efficiency.html (record cell efficiencies)
20. Federal Highway Administration, Exploratory Advanced Research, structural health monitoring. https://www.fhwa.dot.gov/publications/research/ear/17043/index.cfm (wireless self-powered SHM sensors)
21. Federal Highway Administration, "Focus" article on bridge SHM. https://www.fhwa.dot.gov/publications/focus/06nov/04.cfm (SHM for bridge condition; Woodrow Wilson Bridge)
22. Federal Highway Administration, Every Day Counts, "Adaptive Signal Control Technology." https://www.fhwa.dot.gov/innovation/everydaycounts/edc-1/asct.cfm (how ASCT works, benefits)
23. CDC, "How Water Treatment Works." https://www.cdc.gov/drinking-water/about/how-water-treatment-works.html (the five treatment steps)
24. Wikipedia, "Betz's law." https://en.wikipedia.org/wiki/Betz%27s_law (16/27 limit, wind power equation)
25. Queen Mary University of London, "Power in the Wind" (PDF). https://ph.qmul.ac.uk/sites/default/files/u75/Power%20in%20the%20wind.pdf (P = ½ρAv³ derivation)
26. National Academies, "21st Century's Grand Engineering Challenges Unveiled." https://www.nationalacademies.org/news/21-centurys-grand-engineering-challenges-unveiled (the 14 NAE Grand Challenges)
27. United Nations, "Sustainable Development Goals." https://www.un.org/en/node/82129 (the 17 SDGs)
28. U.S. FDA, news release on the first automated insulin delivery device (2016). https://www.fda.gov/NewsEvents/Newsroom/PressAnnouncements/UCM522974.htm (MiniMed 670G hybrid closed loop)
29. COMAP/SIAM, "GAIMME: Guidelines for Assessment and Instruction in Mathematical Modeling Education." https://www.comap.com/membership/free-student-resources/item/gaimme-guidelines-for-assessment-and-instruction-in-mathematical-modeling-education (modeling process)

30. Seco Tools, "Little's law and Manufacturing WIP." https://secotools.com/article/122463 (L = λW; WIP = throughput × cycle time)
31. Kaizen Institute, "Overall Equipment Effectiveness (OEE): how to measure and improve equipment efficiency." https://kaizen.com/insights/oee-improve-equipment-efficiency/ (OEE = Availability × Performance × Quality and the definition of each factor)
32. TEEPTRAK, "What is OEE? Complete guide 2027." https://teeptrak.com/en/what-is-oee-how-calculated-complete-guide-2027/ (85% as the commonly cited world-class OEE benchmark)
*Worked examples and practice problems are original, built on standard AP Calculus BC, AP Physics C and AP Biology relationships. The numbers in them are illustrative unless a citation is given.*
