# Autonomous Vehicles: Study Guide
### TSA TEAMS 2027, "Engineering a Smarter World"

**Who this is for:** a team of high school seniors taking AP Calculus BC, AP Physics C and AP Biology.
**What it covers:** everything the official "Autonomous Vehicles" section sheet asks about (fleet safety, infrastructure needs, how sensors prevent collisions, and the three technologies it names: sensors, machine learning and V2X), all 9 "Explore More" sources and all 5 URLs you gave, and 30+ other reliable sources. A citation page at the end lists 47 sites, one URL per entry.

**How to use it.** The guide gets deeper as you go, so you can stop at any level:

- **Level 1 (Section 1):** the whole topic in one paragraph. Read it the night before.
- **Level 2 (Sections 2 to 7):** the core facts, numbers and rules, organized by the sheet's questions.
- **Level 3 (Sections 8 to 10):** the math and physics, with every variable defined and worked examples. Then practice questions with answers.

**A note on the numbers.** This field changes month to month. The section sheet's own figures (7 million rider-only miles, 85% fewer injury crashes) come from Waymo's December 2023 study, and newer figures now exist. Where sources differ, this guide gives both numbers, the date of each, and the reason they differ. Judges reward the newer figure when you can explain the difference.

---

## Contents

1. Level 1: The whole section in one paragraph
2. Key terms you must know
3. The industry right now: Waymo and Motional (sources 1 and 2)
4. How the car senses, decides and acts (including machine learning)
5. Safety evidence: what the data show and what they don't
6. Who regulates AVs, and what they require (federal and California)
7. Fleets, traffic flow and infrastructure (TGSIM, V2X, phantom jams)
8. Level 3: Equations, with every variable defined
9. Worked examples
10. Practice questions with answers
11. Quick-review sheet
12. Assumptions and how sources were consulted
13. Citation page

---

## 1. Level 1: The whole section in one paragraph

Human drivers are inconsistent. In NHTSA's crash-causation survey, investigators named a driver action as the "critical reason" (the last failure before the crash) in about 94% of crashes, though NHTSA warns this label does not mean the driver was at fault [12]. Autonomous vehicles (AVs) try to remove that inconsistency with a loop of **sense → perceive → predict → plan → act**. Machine learning, trained on millions of labeled examples, turns raw sensor data into a list of objects and their likely paths. They **sense** with lidar (laser time-of-flight ranging, d = cΔt/2, where d is the distance to the target, c the speed of light and Δt the pulse's round-trip time), radar (radio ranging plus Doppler velocity, f_d = 2v_r/λ, where f_d is the frequency shift, v_r the target's line-of-sight speed and λ the radar wavelength) and cameras, plus V2X radios that can "hear" hazards no sensor can see. They **fuse** these noisy measurements into one estimate. They react faster than a human, and since stopping distance is d_stop = v₀·t_r + v₀²/(2μg) (v₀ = starting speed, t_r = reaction time, μ = tire-road friction coefficient, g = 9.81 m/s²), cutting reaction time t_r shortens the stop. Waymo, the industry leader, gives about 500,000 paid rides a week, drives over 4 million autonomous miles a week with about 3,000 cars [1][15], and reports large drops in injury crashes compared with human benchmarks [16][17][18]. Motional and Uber began robotaxi rides in Las Vegas, with a safety operator on board for now [2]. Regulators watch through crash reporting. NHTSA's Standing General Order covers national crash reports, with the most serious crashes due within 5 days and less serious ADS crashes monthly [5][13][38]. In California, the DMV collects collision reports (historically on form OL 316 within 10 days for testing permits; since April 28, 2026, on a schedule aligned with NHTSA's order) [3][14][46], and the CPUC collects quarterly data plus stoppage and incident reports, and, as a condition of its robotaxi permits, requires collision reports to both the CPUC and NHTSA within 1 day [6][7]. So a California robotaxi's tightest clock is 1 day, for NHTSA as well as the CPUC. USDOT plans for AVs through its Automated Vehicles Comprehensive Plan [4] and publishes research data such as the TGSIM trajectories, which show how human drivers act around automated vehicles [8][9][19]. At the fleet level, experiments show that even one well-controlled automated car among about 20 can damp "phantom" stop-and-go waves [20][21]. That is the basis for the sheet's question: "What if a fleet of vehicles could communicate to eliminate stop-and-go congestion?"

---

## 2. Key terms you must know

| Term | Meaning |
|---|---|
| **ADS (Automated Driving System)** | Hardware and software that together perform the *entire* driving task on a sustained basis. These are SAE Levels 3–5 [5][23]. |
| **ADAS (Advanced Driver Assistance System)** | Features that help a human driver who stays in charge, e.g. lane keeping or adaptive cruise control. These are SAE Levels 1–2 [5]. |
| **SAE J3016 levels** | 0 no automation; 1 driver assistance (steering *or* speed); 2 partial automation (steering *and* speed, human supervises); 3 conditional (system drives, human must take over when asked); 4 high (system drives and handles its own fallback inside its ODD); 5 full (anywhere a human could drive) [23]. |
| **DDT (Dynamic Driving Task)** | "All of the real-time operational and tactical functions required to operate a vehicle in on-road traffic" (SAE J3016) [23]. |
| **ODD (Operational Design Domain)** | The conditions a system is designed to work in: geography, road types, speeds, weather, time of day [23]. Waymo's city service areas are ODDs. |
| **Rider-only (RO) miles** | Miles driven with no human driver aboard, only passengers or nobody [16][17]. |
| **Safety operator** | A human behind the wheel who can take over. Motional's Las Vegas launch uses one [2]. |
| **Lidar** | Light Detection and Ranging. Times laser pulses to build a 3D "point cloud" [24]. |
| **Radar** | Radio Detection and Ranging. Measures range and, through the Doppler shift, radial speed. Works in rain and fog [25]. |
| **Machine learning (ML)** | Software that learns a task (e.g. "is this a pedestrian?") from labeled examples instead of hand-written rules. Deep neural networks are the main type used in AVs (Section 4.4) [41]. |
| **Long tail** | The huge number of rare situations (a person in a costume, a mattress on the freeway, flooded streets) that each appear too seldom in data to learn from easily. The main failure mode of ML driving systems [42]. |
| **False negative / false positive** | A missed real object (can cause a collision) / a "detected" object that is not there (can cause phantom braking) (Section 4.4) [43][44]. |
| **Sensor fusion** | Combining several sensors' measurements, weighted by how reliable each is, into one best estimate (Section 8.6). |
| **V2X** | Vehicle-to-everything communication: V2V (vehicles), V2I (infrastructure like signals), V2P (pedestrians), V2N (network). In the U.S. it uses C-V2X in the upper 30 MHz of the 5.9 GHz band [26]. |
| **Stop-and-go (phantom) wave** | A jam that forms with no bottleneck because small speed fluctuations grow as each driver overreacts [21]. |
| **Trajectory data** | Each vehicle's position, speed and acceleration over time, e.g. the TGSIM datasets [8][9]. |
| **SGO (Standing General Order 2021-01)** | NHTSA's order that requires certain crashes involving ADS or Level 2 ADAS to be reported [5][13]. |
| **OL 316** | California DMV form "Report of Traffic Collision Involving an Autonomous Vehicle" [3][14]. |
| **CPUC** | California Public Utilities Commission. It regulates AV *passenger service* (robotaxi rides and fares). The DMV regulates the *vehicles' testing and deployment* [6][7]. |
| **FMVSS** | Federal Motor Vehicle Safety Standards. Some assume a human driver (a steering wheel, mirrors), so driverless designs may need exemptions [27]. |

---

## 3. The industry right now: Waymo and Motional

### 3.1 Waymo (source 1: "Waymo Hits 500,000 Weekly Rides and Over 4 Million Miles, co-CEO Says")

- **500,000 paid rides per week.** Waymo first announced this on its social media. The 4-million-mile figure came from co-CEO **Dmitri Dolgov** on the *Cheeky Pint* podcast with Stripe's John Collison [1][15]. Coverage dates the remarks to about February 2026 [15].
- **Fleet: about 3,000 cars** doing those rides, which adds up to **over 4 million fully autonomous miles per week** [1]. NHTSA data from December 2025 showed 3,067 Waymo robotaxis with the 5th-generation system [1].
- **Footprint:** fully autonomous operation in **11 U.S. cities**, with riders in 10. Nashville was in driverless testing without passengers at the time [1].
- **Growth:** about 50,000 paid rides a week in May 2024, so about **10× in under two years**, mostly from using each car more, not from adding many cars [1].
- **Target:** co-CEO **Tekedra Mawakana** set a goal of over **1 million paid rides per week by the end of 2026** [1][15].
- **Hardware:** the 6th-generation Waymo Driver uses **13 cameras, 4 lidars, 6 radars and external audio receivers**. That is about 42% fewer sensors than the 5th generation (29 cameras), and it has cleaning systems and hydrophobic coatings for bad weather [28].

**Numbers you can derive (useful in a fleet-analysis question):**
- 4,000,000 mi ÷ 500,000 rides ≈ **8 miles per ride** on average. This is an upper bound, because some autonomous miles are driven empty between rides.
- 500,000 rides ÷ 3,000 cars ≈ **167 rides per car per week**, or about 24 a day.
- 4,000,000 mi ÷ 3,000 cars ≈ **1,330 miles per car per week**, or about 190 miles a day. One robotaxi does the yearly mileage of a typical private car in about 2 months. This matters for infrastructure: high-use fleets wear vehicles faster, need charging depots, and concentrate pickup and drop-off at curbs.

### 3.2 Motional and Uber (source 2: "Uber and Motional Launch Robotaxi Service in Las Vegas")

- **Announced March 13, 2026.** Uber riders in Las Vegas can be matched with a **Motional IONIQ 5 robotaxi** (Hyundai's electric crossover) [2][29].
- **Service area:** designated pickup spots along Las Vegas Boulevard (the Strip), Downtown, and near the airport [2].
- **How riders get one:** requests for UberX, Uber Electric, Uber Comfort or Uber Comfort Electric may be matched at **no extra cost**. Riders can accept or switch to a human driver, and can opt in for more AV matches in Ride Preferences [2][29].
- **Safety operator:** a human operator sits behind the wheel for now. The goal is **fully driverless service by the end of 2026**, if authorities approve [2][29].
- **Support:** riders can reach human support in the Uber app during the trip [2].
- **Why it matters (the sheet's point):** Motional "is scaling its driverless systems through partnerships with major ride-hail networks." A ride-hail platform supplies the riders, so the AV company can focus on the driving system. This is a **mixed fleet** model, where human and robot drivers share one dispatch network.
- **History caution:** Motional and Uber also announced a Las Vegas robotaxi launch in December 2022 (with safety operators) [29]. If a question gives a date, check which launch it means. The page you gave describes the 2026 service.

### 3.3 Reconciling the sheet's Waymo numbers

| Claim | Source and date | What it measured |
|---|---|---|
| "Surpassed 7 million rider-only miles… 85% reduction in any-injury crashes" (the section sheet) | Waymo blog and preprint, Dec 2023 [16][17] | 7.14 million RO miles through Oct 2023 in Phoenix, San Francisco and Los Angeles. 0.41 vs 2.78 injury crashes per million miles (IPMM). |
| ≈80% fewer any-injury crashes; 55% fewer police-reported crashes | Peer-reviewed version, *Traffic Injury Prevention*, 2024 [17] | Same miles, revised method: 0.6 vs 2.80 IPMM; 2.1 vs 4.68 IPMM for police-reported crashes. |
| ≈92% fewer serious-injury-or-worse crashes over ≈170.7 million RO miles | Waymo Safety Impact hub, data through Dec 2025 [18] | Larger dataset, more cities including Austin. The serious-injury category is small, so the counts are tens of crashes. |

**Talking point:** "The sheet's 85% figure is from Waymo's 2023 preprint. The peer-reviewed version revised it to about 80%. Waymo's newer data, from 24 times as many miles, report about 92% fewer serious-injury crashes. These are company analyses against human benchmarks, not independent audits."

---

## 4. How the car senses, decides and acts

### 4.1 The autonomy pipeline

1. **Sense:** lidar, radar, cameras, microphones, GPS/GNSS, an IMU (accelerometers and gyroscopes), wheel odometry, and V2X messages.
2. **Localize:** match what the sensors see to a high-definition map to find the car's position, often to within centimeters.
3. **Perceive:** detect and classify objects (car, pedestrian, cyclist, cone) and track each one's position and velocity over time. Machine-learning models, mainly deep neural networks, do most of the classifying (Section 4.4).
4. **Predict:** estimate what each object will do next, e.g. "this pedestrian is likely to step off the curb."
5. **Plan:** choose a path and speed profile that is safe, legal and comfortable.
6. **Act (control):** send steering, throttle and brake commands, then measure the result and correct. This is a feedback loop.

The sheet says AVs "utilize complex LIDAR and camera arrays to avoid collisions and stay on the desired path." Steps 1–3 are "avoid collisions," and steps 5–6 are "stay on the desired path."

### 4.2 Sensor comparison (why AVs carry all three)

| | Lidar | Radar | Camera |
|---|---|---|---|
| Physical principle | Time-of-flight of laser light (near-infrared) [24] | Radio echo; FMCW chirps; Doppler shift (often 76–81 GHz) [25] | Passive visible light focused onto an image sensor |
| Measures directly | Range and 3D shape (point cloud), centimeter accuracy at short range [24][28] | Range **and radial velocity** (Doppler) [25] | Color, texture, text (signs, signals, lane paint) |
| Weak spots | Cannot measure speed directly by Doppler (pulsed ToF type), so it infers speed from successive frames. Weak returns from dark, transparent or mirror-like surfaces. Returned power falls steeply with range. Degraded by heavy fog and snow [24] | Low angular resolution. Ghost reflections from metal. Poor at classifying object type | No direct depth. Fooled by glare, darkness and low sun. Needs ML to interpret |
| Weather | Fair | **Best** | Poor to fair |

**Redundancy principle:** Waymo states that when a camera's view is limited, lidar and radar provide redundancy so perception keeps working [28]. Each sensor's weak spot is covered by another sensor's strength. This is the engineering answer to "how do sensors prevent collisions."

### 4.3 Sensing what a human can't see (the sheet's "sense a pedestrian before they were visible")

- **Radar multipath:** radar can bounce under or around vehicles and detect a moving object partly hidden behind another car.
- **Height and 360° coverage:** roof-mounted lidar sees over parked cars and in all directions at once. A human sees about 120° with useful focus and must turn their head.
- **V2X:** a pedestrian's phone (V2P), a connected signal (V2I) or a car around the corner (V2V) can *broadcast* its position. Radio diffracts and reflects around obstacles, so the AV can "hear" the hazard before any line-of-sight sensor sees it [26].
- **Audio:** external microphones can detect sirens before emergency vehicles are visible [28].
- **Never tired or distracted:** the system watches every direction at every moment.

### 4.4 Machine learning: how the car learns to see and predict

The sheet names three technologies: "sensors, machine learning, and V2X." Sensors give raw numbers (point clouds, radar returns, pixels). **Machine learning (ML)** turns those numbers into meaning: "pedestrian, 14 m ahead, walking toward the curb, likely to cross." ML does most of the work in the **perceive** and **predict** steps of Section 4.1 and a growing share of **plan** [41].

**1. How a perception model is trained (supervised learning).**
1. **Collect data.** The fleet records sensor logs. Waymo says it has worked on AI and ML for driving for more than 15 years and trains on its fleet's driving data [41].
2. **Label it.** Humans (and, increasingly, automatic labeling tools) draw 3D boxes around every car, pedestrian and cyclist and tag each one's class.
3. **Train.** A deep neural network makes a prediction for each example. A **loss function** scores how wrong it is. An optimizer nudges millions of weights to lower the loss, repeated over millions of examples (equations below).
4. **Validate.** Test on data the model has never seen, measure precision and recall (below), then test in simulation and on closed courses before any road use.
5. **Mine for hard cases and repeat.** Engineers search fleet logs for situations the model got wrong or was unsure about, label those, and retrain.

**2. Modular vs end-to-end.** Most deployed stacks are *modular*: separate networks for perception, prediction and planning, joined by hand-designed interfaces and checked by rule-based safety layers. Waymo's research model **EMMA** (Oct 2024, built on Google's Gemini) goes *end-to-end*: it takes camera images and produces the planned trajectory, detected objects and road layout from one model. Training one model on all three tasks did better than training separate models. But the authors list its limits: it handles only a few image frames, does **not** use lidar or radar, and is computationally expensive [41]. That is why deployed robotaxis still fuse lidar, radar and cameras (Section 4.2).

**3. The long tail: why rare cases are the main failure mode.** A model learns what it has seen often. Ordinary cars and pedestrians appear millions of times in the data; a person in an inflatable costume, a couch in the lane, a flooded street or a police officer waving traffic through a red light might appear a handful of times or never. These rare cases are the "long tail" of the data distribution, and they are where ML errors concentrate. Two engineering answers:
- **Simulation.** Waymo's World Model (Feb 2026) generates realistic camera and lidar data for rare scenes, such as tornadoes, flooded streets, a broken-down truck blocking a lane, or animals, so the driver can be trained and tested on situations "never directly observed by our fleet" [42].
- **Redundancy and rules.** Lidar measures geometry directly, so even an object the classifier cannot name still shows up as "something solid in my path." Planning layers can treat any unknown solid object as an obstacle. This is how sensor redundancy (Section 4.2) protects against ML errors.

**4. Errors and collisions: false negatives vs false positives.** Every detector outputs a **confidence score** and calls an object "real" only above a **threshold** [44].
- A **false negative** (missed pedestrian or debris) can lead directly to a **collision**.
- A **false positive** (braking for a shadow, an overpass or a plastic bag) leads to **phantom braking**: a sudden, unneeded slowdown that can get the car rear-ended and annoys riders. NHTSA opened investigation **PE22-002** in Feb 2022 into reports of unexpected braking in Tesla Model 3 and Model Y vehicles with driver-assistance engaged (Level 2, not a robotaxi). It closed the probe in mid-2026 without a recall, finding low demonstrated risk and no collisions or injuries tied to the events, while noting that closing it is not a finding that no defect existed [43].
- **The tradeoff:** lowering the threshold catches more real objects (higher recall, fewer false negatives) but adds false alarms (lower precision); raising it does the opposite [44]. Engineers do not pick one global value: they vary it by object type and distance, and they cross-check a low-confidence camera detection against radar or lidar before an emergency stop [44]. That is the answer to "how do sensors *and other features* function to prevent collisions": the ML decides what is there, and fusion and thresholds decide how sure it must be before acting.

**Equations (every variable defined).**

$$ \text{Precision} = \frac{TP}{TP+FP},\qquad \text{Recall} = \frac{TP}{TP+FN} $$
- **TP** (true positives): real objects the model detected
- **FP** (false positives): detections with no real object (phantom objects)
- **FN** (false negatives): real objects the model missed
- **Precision**: fraction of detections that were real (high precision → little phantom braking)
- **Recall**: fraction of real objects that were detected (high recall → few missed hazards) [44]

$$ L = -\frac{1}{N}\sum_{i=1}^{N}\ln p_i ,\qquad w_{new} = w_{old} - \eta\,\frac{\partial L}{\partial w} $$
- **L**: cross-entropy loss, the average "wrongness" of the model over a batch (dimensionless)
- **N**: number of labeled examples in the batch
- **i**: index of one example (1 to N)
- **p_i**: probability the model assigned to the *correct* label of example i (between 0 and 1). If p_i = 1, that example adds 0 loss; as p_i → 0, −ln p_i → ∞
- **w**: one of the network's weights (adjustable numbers); **w_old, w_new** its value before and after the update
- **η** (eta): learning rate, the step size (a small positive number, e.g. 0.001)
- **∂L/∂w**: partial derivative of the loss with respect to that weight, found by the chain rule through every layer ("backpropagation")

This is gradient descent: AP Calc BC's derivative tells each weight which way is "downhill" on the loss. The cross-entropy form is the standard classification loss in machine learning (a textbook convention, not a figure from the cited AV sources).

**Mini-example.** A pedestrian detector is tested on 1,000 frames that contain 200 pedestrians. It flags 210 objects, of which 190 are real pedestrians. TP = 190, FP = 210 − 190 = 20, FN = 200 − 190 = 10. Precision = 190/210 ≈ **0.905**. Recall = 190/200 = **0.95**. The 10 misses are the safety-critical number; fusion with lidar (which still "sees" a solid object even if it is misclassified) is what keeps those misses from becoming collisions.

### 4.5 Biology connection (AP Bio)

- **Human perception-reaction chain:** photoreceptors (rods and cones) → bipolar and ganglion cells → optic nerve → visual cortex (perception) → prefrontal and motor cortex (decision) → spinal motor neurons → leg muscles (braking). Every synapse adds delay. Road-design standards assume **2.5 s** perception-reaction time to cover about 90% of drivers. An alert driver needs about 1–1.5 s [30].
- **Neural networks are loosely inspired by neurons:** weighted inputs are summed and passed through an activation function, much as a neuron sums excitatory and inhibitory postsynaptic potentials until it reaches threshold. Training (Section 4.4) changes the weights, a rough analogy to synaptic strengthening and weakening during learning.
- **Detection thresholds in biology:** like a detector's confidence threshold, a neuron fires only when summed input passes threshold, and the tradeoff between missing a real predator (false negative) and fleeing from a shadow (false positive) shapes animal vigilance behavior.
- **Rods and cones vs sensors:** rods work in dim light but don't see color. Cones see color but need bright light. A camera's dynamic range plays the same role. Lidar and radar emit their own energy (*active* sensing), so they work in the dark, much as echolocation works for a bat.
- **Error types match NMVCCS categories:** recognition errors (≈41% of driver-assigned critical reasons, e.g. inattention), decision errors (≈33%, e.g. too fast for conditions) and performance errors (≈11%, e.g. overcorrection) [12]. Ask which ones automation addresses.

---

## 5. Safety evidence: what the data show and what they don't

### 5.1 The case for AV safety

- Human drivers: a driver was the "critical reason" in about **94% (±2.2%)** of crashes in NHTSA's 2005–2007 NMVCCS study (5,470 sampled crashes, weighted to about 2.19 million) [12].
- Waymo's analyses (Section 3.3) show injury-crash reductions of about 80–92% depending on the dataset and the injury category [16][17][18]. The hub also reports about 92% fewer pedestrian-injury crashes, 85% fewer cyclist-injury crashes and 81% fewer motorcycle-injury crashes [18].
- Data transparency: Waymo's analyses use its crash reports filed under NHTSA's Standing General Order and publish mileage, so outsiders can check them [18].

### 5.2 The caveats (judges love these)

1. **"94%" is not "94% preventable."** NHTSA says the critical reason is "not intended to be interpreted as the cause of the crash nor as the assignment of the fault" [12]. AVs also create new failure modes, such as software bugs, sensor blind spots and unexpected stops.
2. **Benchmark matching.** A fair comparison uses human crashes on the *same kinds of roads, in the same cities*. Human crashes are also underreported, so Waymo adjusts the human benchmark upward. That adjustment is a modeling choice [16][17].
3. **Small numbers.** With only a few dozen serious crashes, the percentages have wide confidence intervals and can move between updates [18] (see Section 8.8).
4. **Company-reported.** Most of the analysis is done by the operator itself, so public reporting to the DMV, CPUC and NHTSA matters for independent checks.
5. **Non-crash problems.** Robotaxis can block traffic, emergency vehicles or intersections by stopping. This is why the CPUC added **"stoppage event"** reporting [7].
6. **Real incidents changed policy.** On October 24, 2023, weeks after a Cruise robotaxi dragged a pedestrian who had been knocked into its path by a hit-and-run driver, the California DMV suspended Cruise's driverless testing and deployment permits, effective immediately, citing an unreasonable risk to public safety. Cruise kept its permit for testing *with* a safety driver [36]. Afterward, Waymo was the only company reporting CPUC passenger-service data in OWID's compilation [10].

### 5.3 California DMV collision reports (source 3)

- **Rule (testing permits, through April 2026):** California Code of Regulations, title 13, §227.48 [14]. In the 2026 rule package, collision reporting for testing moved to §227.54 and was aligned with NHTSA's Standing General Order (June 2025 version) [47].
- **Who:** a manufacturer testing AVs (including with a driverless testing permit) must report any collision on a public road that causes **property damage, bodily injury or death** [3][14].
- **When and how:** within **10 days**, on **form OL 316** ("Report of Traffic Collision Involving an Autonomous Vehicle"). It must name everyone involved and fully describe how the collision happened [14]. It can be filed through the DMV's web portal [14].
- **Public access:** the DMV posts the individual reports as PDFs on the Collision Reports page, filed by manufacturer and date, e.g. Waymo and Zoox reports from 2019 to 2026 [3]. GovTech described the DMV's release of these reports as the first public data set on driverless-car crashes [34].
- **Earlier gap, and how it closed:** a 2024 Assembly committee analysis of bill AB 3061 noted that collision reports were required under *testing* permits but not *deployment* permits, and the bill tried to close that gap [31]. **Governor Newsom vetoed AB 3061 on September 27, 2024** [45], so the gap stayed open until the DMV's own 2026 regulations.
- **Collision reporting after April 28, 2026:** the DMV's industry memo on reporting requirements (AVIM 2026-001A, effective April 28, 2026) says collision reports must be submitted to the DMV **in alignment with NHTSA Standing General Order 2021-01 (June 2025)**, starting as soon as the regulations took effect. It also adds new data reports by permit type: monthly reports from August 26, 2026 (braking events, vehicle miles traveled, system failures, vehicle immobilizations) and a first quarterly report due September 30, 2026 [46]. **What this means for a deployed robotaxi:** before April 28, 2026, a company holding *only* a deployment permit had no DMV collision-report duty (the gap above). In practice, companies such as Waymo and Zoox also hold testing permits and filed OL 316 reports, which is why their reports appear on the DMV page [3]. Since April 28, 2026, a crash must go to the DMV on the SGO's schedule (for the most serious crashes, 5 days) [46]. The DMV page (source 3) still describes the 10-day testing rule, so on a test, "OL 316, 10 days" is the answer for source 3, and "aligned with the federal SGO since April 2026" is the up-to-date answer.
- **Recent change (April 28, 2026):** the DMV adopted new AV regulations that strengthen oversight and enforcement for all AV classes and authorize heavy trucks and transit. Key points: the ban on AVs with a gross vehicle weight rating of 10,001 lb or more is removed (opening AV freight); heavy-duty AVs must still stop at CHP weigh stations; public entities and universities may run AV transit vehicles up to 14,001 lb; companies move through three stages (testing with a safety driver, driverless testing, then deployment), with at least 50,000 test miles for light-duty and 500,000 for heavy-duty vehicles; and applicants must submit a structured **safety case** covering hardware, software and operational readiness. Some provisions took effect immediately and others phase in later [35]. Check the DMV page for current rules.
- **Study use:** these PDFs are raw data. You could tally collision types (e.g. "AV rear-ended while stopped" vs "AV struck another vehicle") to judge who is usually at fault.

### 5.4 CPUC: the robotaxi service regulator (two "Explore More" sources)

**"California Public Utilities Commission: AV Program Quarterly Reporting" [6]**
- Companies in the CPUC's AV passenger-service programs (pilot and deployment) file **verified quarterly reports** with anonymized, disaggregated data [6].
- Required metrics include **miles per vehicle in passenger service**, the **share of miles by electric (zero-emission) vehicles**, and **"deadhead" miles from the vehicle's start point to the pickup** [6].
- Confidential data must still be filed in a public redacted version, with protected cells marked "REDACTED" instead of deleted. Confidentiality claims fall under General Order 66-D [6].
- The latest posted deployment reports cover **April 1 to June 30, 2026** [6]. Our World in Data republishes the series as passenger-km traveled by self-driving taxis [10].
- The CPUC collects data at least quarterly to evaluate its programs and inform policy, and DMV collision forms are also reported to the CPUC at the same time [32].
- **Infrastructure tie-in:** deadhead miles add traffic and energy use without carrying anyone, a cost of AV fleets that ride counts alone miss.

**"CPUC Enhances Autonomous Vehicle Reporting Requirements to Boost Safety Standards" (Nov 7, 2024) [7]**
- **Stoppage events:** operators must report when a vehicle becomes stuck during service, so the CPUC can measure the effect on passengers and the public [7].
- **Trip-level incident reports:** these cover collisions *and* non-collision events such as citations and stoppages [7][11].
- **Collision reporting:** all operators, in pilot or deployment status, must report collisions to **both the CPUC and NHTSA within one day** [7]. This is a **California CPUC permit condition** set in November 2024, when NHTSA's own deadline for the most serious crashes was also 1 day. NHTSA has since moved its *federal* deadline to 5 days (Section 6.2), but that change does not loosen the CPUC condition. **So: a California robotaxi operator with a CPUC permit owes a 1-day report to the CPUC *and* a 1-day report to NHTSA under its permit, even though NHTSA's order by itself would allow 5 days.** Robotaxi operators outside California follow only the federal 5-day clock. Check the CPUC page for any later change to its 1-day rule.
- **Origin:** a May 2023 Commissioner ruling, then stakeholder comments and a public workshop, under rulemaking R.12-12-011. Commissioner Matthew Baker led it [7][11].

**Who does what in California:** the **DMV** licenses the *vehicle and its driving* (testing and deployment permits, OL 316 collision reports). The **CPUC** licenses the *passenger business* (charging fares, quarterly data, stoppage and incident reports).

---

## 6. Who regulates AVs, and what they require (federal)

### 6.1 NHTSA: Automated Driving Systems (source 5)

- NHTSA's page describes **SAE Levels 3–5 as ADS** that would perform the whole driving task in their ODD with no human driver. **Level 2 ADAS** steers and controls speed but **requires the driver to stay fully engaged** [5]. Common exam trap: today's "Autopilot"-style consumer features are Level 2.
- NHTSA sets and enforces federal motor vehicle safety standards (FMVSS), investigates defects, orders recalls, and gathers crash data [5][13].
- It publishes companies' **Voluntary Safety Self-Assessments** (VSSAs) for ADS at Levels 3–5. Being listed is not a federal endorsement [5].

### 6.2 NHTSA Standing General Order 2021-01 [13]

| Version | Date | Key point |
|---|---|---|
| Original | June 29, 2021 | Named manufacturers and operators must report certain crashes involving ADS or Level 2 ADAS |
| 1st Amended | Aug 12, 2021 | |
| 2nd Amended | Apr 5, 2023 | |
| **3rd Amended (current)** | Issued Apr 24, 2025; effective June 16, 2025 | Two tiers (details below). Removes the old 1-day and 10-day deadlines. Adds a property-damage threshold for less severe ADS crashes. Generally only one of several reporting entities must report the same crash. No monthly report is due in a month with no reportable crash [13][27][38][39] |

**Federal deadlines under the 3rd Amended SGO (memorize this table):**

| Crash type | Deadline to NHTSA |
|---|---|
| Most serious crashes (e.g. a fatality, a person taken to a hospital for treatment, a vulnerable road user such as a pedestrian or cyclist struck, an air bag deployment) with ADS or Level 2 ADAS engaged within 30 s | **5 calendar days** after the company receives notice [13][38][39] |
| Less serious ADS crashes (no fatality, hospitalization or tow-away, but above the property-damage threshold) | **Monthly**, by the **15th** of the month after the month the company received notice (e.g. notice Nov 12 → report by Dec 15) [39] |

Before June 16, 2025 the most serious crashes were due in **1 day** (with an update by day 10). The CPUC's 1-day rule (Section 5.4) was set in 2024, while this older federal deadline was in force, and it still applies to CPUC permit holders, covering their reports to NHTSA too. Exact category definitions are in Section 3 of the order [38].

- **Trigger:** the automation was engaged **within 30 seconds** before a crash that meets injury or damage thresholds [13]. The 30-second window catches crashes where the system disengaged just before impact.
- **Purpose:** quick, transparent notice of real-world crashes, so NHTSA can investigate, for example its probe of Cruise [13].

### 6.3 NHTSA "AV Framework" (April 24, 2025) [27]

Three principles: **prioritize safety** of current AV operations, **remove unnecessary regulatory barriers**, and **enable commercial deployment**. The first actions were the 3rd Amended SGO and an expanded **Automated Vehicle Exemption Program**. That program now accepts **U.S.-built** vehicles for *non-commercial* exemptions from FMVSS rules that assume a human driver (steering wheel, mirrors, driver's seat). NHTSA also committed to streamline the **Part 555** exemption route used for commercial vehicles [27].

### 6.4 USDOT Automated Vehicles Comprehensive Plan (source 4)

**What the page you gave contains.** The URL transportation.gov/av/avcp/5 is a USDOT web page titled "USDOT's Automated Vehicles Comprehensive Plan." It carries the title and a link to one document, the plan PDF (USDOT_AVCP.pdf) [4]. The "/5" is part of the web address, not a numbered chapter. So the content below comes from that linked PDF [22], which is the document the page exists to deliver.

Released **January 11, 2021**, building on *AV 4.0*. It has **three goals** [4][22]:
1. **Promote Collaboration and Transparency:** clear, reliable public information on what ADS can and cannot do.
2. **Modernize the Regulatory Environment:** remove unnecessary barriers to new vehicle designs, and develop safety frameworks and tools to judge ADS performance (e.g. NHTSA's Advance Notice of Proposed Rulemaking on a Framework for ADS Safety).
3. **Prepare the Transportation System:** research and demonstrations with partners to safely test and integrate ADS, while improving safety, efficiency and accessibility. Under this goal the plan points to the **ADS Demonstration Grants** (about **$60 million** to **8 projects in 7 states**) and to updating **traffic control devices such as lane markings and signs** so they support safe interaction between ADS vehicles and the roadway [22]. This is the plan's direct link to the sheet's "infrastructure needs."

The plan states it does not try to predict the future forms of ADS vehicles or the services they may provide [22]. **Newer policy:** in September 2026 USDOT published a *National Strategy for Automated Vehicles* (FY 2026–2030) that expands on NHTSA's April 2025 AV Framework (Section 6.3) and lists the 2021 plan among earlier policy documents [40].

**Exam tip:** be ready to match a real action to a goal. The SGO serves Goal 1 (transparency) and Goal 2. The AV exemption program serves Goal 2. TGSIM research data serve Goal 3.

### 6.5 Spectrum for V2X (FCC) [26]

- In 2020 the FCC split the 75 MHz **5.9 GHz** band (5.850–5.925 GHz). It gave the lower 45 MHz to Wi-Fi and kept the **upper 30 MHz (5.895–5.925 GHz)** for transportation safety (ITS), and required a move from the older DSRC standard to **C-V2X** [26].
- The **Second Report and Order (Nov 2024; effective Feb 11, 2025)** set C-V2X technical rules. It allows the three 10 MHz channels to be combined into 20 or 30 MHz channels and gives DSRC a two-year sunset [26].
- **Infrastructure implication:** V2I requires **roadside units** at intersections, i.e. public investment, power and maintenance.

---

## 7. Fleets, traffic flow and infrastructure

### 7.1 TGSIM: the USDOT trajectory data (two "Explore More" sources)

The **Third Generation Simulation Data (TGSIM)** project (University of Illinois Urbana-Champaign for USDOT/FHWA, report FHWA-JPO-24-133, May 2024) recorded how **human drivers behave around automated vehicles**. It produced **six trajectory datasets**: I-294 L1 and I-294 L2 (Chicago suburbs), I-90/I-94 (Chicago, moving and stationary), **I-395 (Washington, D.C.)** and **Foggy Bottom (Washington, D.C.)** [19][8][9].

**"TGSIM I-395 Trajectories" [8]**
- An urban **expressway** with a **merge**. Contains **position, speed and acceleration** for passenger cars, trucks, buses and **automated vehicles** [8].
- Captured by multiple **synchronized, overlapping infrastructure cameras** on overpasses and buildings, stitched together [8][19].
- Main file: *I395-final.csv* (~232 MB). Includes a lane map with **5 lanes**. "Lane −1" marks vehicles that drove onto the merge lane's shoulder, separated by hand from the video [8].
- **Good for:** car-following and merge behavior, gaps accepted when merging, and whether humans follow AVs more closely or less closely.

**"TGSIM Foggy Bottom Trajectories" [9]**
- An **urban street grid** at George Washington University. **Twelve 4K stationary cameras** cover **4 intersections**, their crosswalks and the road between them [9].
- Road users include **pedestrians, bicycles, scooters, human-driven cars, automated vehicles, motorcycles, buses and trucks** [9].
- Main file: *TGSIM-Foggy Bottom-Data.csv* (~350 MB), with region annotation images that map IDs to physical road areas [9].
- **Good for:** AV–pedestrian interactions, the exact case the sheet raises ("sense a pedestrian before they were visible").

**How you'd use trajectory data (calculus link):** given x(t), a vehicle's position along the road (m) as a function of time t (s), its speed is v = dx/dt (m/s) and its acceleration is a = dv/dt (m/s²). From discrete samples, use finite differences: v ≈ Δx/Δt, where Δx is the change in position between two samples and Δt is the time between them (e.g. 0.1 s). Then compute headways, time-to-collision and gaps (Section 8.5) to measure safety without waiting for crashes. This is called *surrogate safety analysis*.

### 7.2 Phantom traffic jams and how one AV can fix them

- **Sugiyama et al. (2008):** 22 cars on a 230 m single-lane ring road, told to drive about 30 km/h. With no bottleneck, small gap fluctuations grew until cars briefly stopped. The jam traveled **backward** like a shock wave. A bottleneck is only a trigger; the jam itself is a collective instability [21].
- **Stern et al. (2018):** in a ring experiment with 20+ cars (one AV among 20–21 human-driven cars, so roughly 4.5–5% automated), **one** automated vehicle (University of Arizona's CAT Vehicle) controlling its own speed **damped the stop-and-go waves**. Speed variation and braking events dropped and fuel economy improved. The abstract's own words: flow control "will be possible via a few mobile actuators (less than 5%) long before a majority of vehicles have autonomous capabilities" [20]. That is the authors' projection, not a measured result; a USDOT summary words it as "as few as 5 percent." On a test, "about 5% or less" is safe.
- **Follow-up (Stern et al., 2019, a separate paper):** using velocity and acceleration data from the same ring experiments and the EPA MOVES emissions model, the authors estimated that removing such waves could cut the whole fleet's emissions by about **15% (CO₂) to 73% (NOₓ)**. They stress this applies only when stop-and-go waves are present; gains are smaller across broader traffic conditions [37].
- **Answer to the sheet's question:** "A fleet that communicates" (V2V and cooperative adaptive cruise control) can do better than one car. Each car knows the braking of cars several positions ahead, not just the car directly in front, so disturbances are absorbed instead of amplified. This property is called *string stability*.

### 7.3 Infrastructure needs created by AV fleets (the sheet's "infrastructure needs")

| Need | Why |
|---|---|
| Clear, consistent **lane markings and signs** | Camera-based lane detection depends on them |
| **Roadside units / V2I** at signals | Signal-phase broadcasts and hazard warnings (5.9 GHz C-V2X) [26] |
| **Curb management** (pickup and drop-off zones) | Robotaxis stop often. Motional uses designated pickup spots [2] |
| **Charging depots** | Fleets are mostly electric (IONIQ 5, Jaguar I-PACE, etc.), and the CPUC tracks zero-emission miles [6] |
| **HD maps and data** | Localization. Rider-only service is limited to mapped ODDs |
| **Emergency-responder protocols** | Stoppage events can block responders [7] |
| **Data and reporting systems** | DMV, CPUC and NHTSA reporting [3][6][13] |
| **Cybersecurity** | Connected cars are an attack surface |

**Possible downsides to raise:** cheap, convenient rides can **increase total vehicle miles traveled** (induced demand plus deadhead miles [6]), which could worsen congestion even if each car drives better.

---

## 8. Level 3: Equations, with every variable defined

Every symbol is defined right below its equation, and the worked examples restate any symbol they reuse. Units are SI unless stated.

**Watch the v's.** Speed shows up in several roles, so each gets its own subscript: **v₀** initial speed of the braking car (8.4); **v_r** radial speed seen by radar (8.2); **v_s** traffic-stream speed (8.5); **v_f, v_l** follower and leader speeds (8.5); **v_obj** a tracked object's velocity (8.6); **v_p** speed on reaching a pedestrian (Example 4). Likewise **d** is a lidar range in 8.1 and a radio path length in 8.9, while **d_stop** and **d_b** are stopping and braking distances.

### 8.1 Lidar range (time-of-flight)

$$ d = \frac{c\,\Delta t}{2n} \;\approx\; \frac{c\,\Delta t}{2}\quad(\text{in air, } n \approx 1)$$

- **d**: distance from the sensor to the target (m)
- **c**: speed of light in vacuum, 3.00 × 10⁸ m/s
- **Δt**: round-trip time between emitting the pulse and detecting its echo (s)
- **n**: refractive index of the medium (≈ 1.0003 for air, so taken as 1)
- **2**: the light travels out *and back*, so the one-way distance is half the total path [24]

**Range resolution from timing precision:** δd = c·δt/2.
- **δd**: smallest distance difference the sensor can resolve (m)
- **δt**: timing resolution of the detector electronics (s)

A 1 ns timing precision gives 15 cm. Centimeter accuracy needs picosecond-level timing or signal averaging.

**Received power (conceptual):** for an extended target, P_r ∝ 1/r² [24].
- **P_r**: optical power returned to the receiver (W)
- **r**: range to the target (m)

Doubling the range cuts the return to about ¼. This is why dark, distant objects are hardest to see.

### 8.2 Radar Doppler velocity

$$ f_d = \frac{2 v_r}{\lambda} = \frac{2 v_r f_c}{c} \qquad\Longleftrightarrow\qquad v_r = \frac{f_d\,\lambda}{2}$$

- **f_d**: Doppler frequency shift between the transmitted and received wave (Hz). Positive means the target is approaching.
- **v_r**: **radial** (line-of-sight) relative velocity of the target (m/s). Motion across the beam gives about zero shift.
- **λ**: radar wavelength (m), λ = c/f_c
- **f_c**: carrier frequency (Hz), e.g. 77 × 10⁹ Hz
- **c**: speed of light, 3.00 × 10⁸ m/s
- **2**: the shift happens twice, on the way to the target and on the reflection back [25]

### 8.3 FMCW radar range and resolution

$$ f_b = \frac{2 S R}{c},\qquad S = \frac{B}{T_c},\qquad \Delta R = \frac{c}{2B},\qquad \Delta v = \frac{\lambda}{2T_{obs}}$$

- **f_b**: beat frequency, the difference between the transmitted and received chirp frequencies (Hz)
- **S**: chirp slope (Hz/s)
- **B**: chirp bandwidth, the range of frequencies swept (Hz)
- **T_c**: duration of one chirp (s)
- **R**: target range (m)
- **ΔR**: range resolution, the minimum separation at which two targets appear as two (m)
- **Δv**: velocity resolution (m/s)
- **T_obs**: total coherent observation time over many chirps (s)
- **λ, c**: as above [25]

Key insight: **more bandwidth gives finer range resolution, and a longer observation time gives finer velocity resolution.**

### 8.4 Stopping distance (why reaction time matters)

$$ d_{stop} = \underbrace{v_0\,t_r}_{\text{reaction distance}} + \underbrace{\frac{v_0^2}{2\mu g}}_{\text{braking distance}}$$

- **d_stop**: total distance from the moment a hazard appears to a full stop (m)
- **v₀**: initial speed (m/s)
- **t_r**: perception-reaction time, from the hazard appearing to the brakes starting (s). AASHTO design value 2.5 s; an alert human about 1–1.5 s [30]. For an AV it is the system latency (sensing + compute + actuation), typically a fraction of a second. That figure is an assumption for illustration, not a number from the sources.
- **μ**: tire-road friction coefficient (≈ 0.7 dry, 0.3–0.4 wet) [30]
- **g**: gravitational acceleration, 9.81 m/s²
- μg = **a**, the deceleration (m/s²). AASHTO uses a = 3.4 m/s² (11.2 ft/s²) as a design value [30][33].

**Calculus derivation (AP Calc BC / Physics C):** with constant deceleration a, use v·dv/dx = −a. Separate and integrate: ∫_{v₀}^{0} v dv = −a ∫_{0}^{d_b} dx. That gives −v₀²/2 = −a·d_b, so **d_b = v₀²/(2a)**.
- **v**: the car's instantaneous speed during braking (m/s), falling from v₀ to 0
- **x**: distance traveled since the brakes were applied (m)
- **a**: magnitude of the constant deceleration (m/s²), a = μg
- **d_b**: braking distance (m), the second term of d_stop

**Energy check:** KE = ½mv₀² and W = F·d_b = μmg·d_b. Setting W = KE gives d_b = v₀²/(2μg) again.
- **KE**: the car's kinetic energy at the start of braking (J)
- **m**: the car's mass (kg). It cancels, so braking distance does not depend on mass (in this simple model)
- **F**: magnitude of the friction force from the road on the tires (N), F = μmg (μ times the normal force mg on level ground)
- **W**: work done by friction over the braking distance (J), which removes all the kinetic energy

Braking distance grows with **v₀²**, just as kinetic energy does.

US customary design form (AASHTO): **SSD = 1.47·V·t + 1.075·V²/a**, with **V** in mph, **t** in s, **a** in ft/s² (11.2), and **SSD** in ft. **1.47** converts mph to ft/s (exactly 5280/3600 = 1.4667), and **1.075** = (5280/3600)²/2 = 1.4667²/2 ≈ 1.0756. Use the exact factor here: the rounded 1.47²/2 gives 1.080, not 1.075 [30][33].

### 8.5 Traffic flow, headway and time-to-collision

$$ q = k\,v_s,\qquad h = \frac{1}{q},\qquad s = \frac{1}{k},\qquad TTC = \frac{g_{ap}}{v_f - v_l}\;(v_f>v_l)$$

- **q**: flow, vehicles passing a point per unit time (veh/h)
- **k**: density, vehicles per unit length of lane (veh/km)
- **v_s**: space-mean speed of the traffic stream (km/h)
- **h**: average time headway between successive vehicles (h, or ×3600 for s)
- **s**: average spacing, front bumper to front bumper (km, or ×1000 for m)
- **TTC**: time-to-collision if neither vehicle changes speed (s)
- **g_ap**: bumper-to-bumper gap between the following and the lead vehicle (m)
- **v_f, v_l**: speeds of the following and lead vehicle (m/s)

Engineers often flag TTC < 1.5–3 s as a "conflict" (a common surrogate-safety threshold in the field, not taken from the cited sources). These are the quantities you'd compute from TGSIM trajectories [8][9].

### 8.6 Sensor fusion: inverse-variance weighting (the core of a Kalman filter update)

$$ \hat{x} = \frac{\sigma_2^2\,x_1 + \sigma_1^2\,x_2}{\sigma_1^2+\sigma_2^2},\qquad \sigma^2 = \frac{\sigma_1^2\,\sigma_2^2}{\sigma_1^2+\sigma_2^2}$$

- **x₁, x₂**: two independent measurements of the same quantity, e.g. lidar and radar range (m)
- **σ₁, σ₂**: standard deviations (uncertainties) of those measurements (m). σ² is the variance.
- **x̂**: fused best estimate (m)
- **σ²**: variance of the fused estimate. It is always **smaller than either** σ₁² or σ₂², which is the mathematical reason to carry several sensors.

Each measurement is weighted by the *other* one's variance, so the more precise sensor counts more. A Kalman filter repeats this every time step, fusing a physics-based prediction with each new measurement. The simplest (constant-velocity) prediction is

$$ x_{pred} = x_{prev} + v_{obj}\,\Delta t $$

- **x_pred**: predicted position of the tracked object at the new time step (m)
- **x_prev**: the object's fused position estimate at the previous time step (m)
- **v_obj**: the tracked object's estimated velocity along x (m/s), e.g. from radar Doppler or from successive frames. This is *not* v₀ from 8.4
- **Δt**: time between filter updates (s), e.g. 0.1 s. This is *not* the lidar round-trip time of 8.1

x_pred then plays the role of x₁ in the fusion formula, and the new sensor reading plays x₂.

### 8.7 Crash rate and percent reduction

$$ R = \frac{N}{M},\qquad \text{Reduction} = 1 - \frac{R_{AV}}{R_{H}},\qquad \text{Rate ratio} = \frac{R_H}{R_{AV}}$$

- **R**: crash rate, in incidents per million miles (IPMM)
- **N**: number of crashes of a given type
- **M**: miles driven, in millions
- **R_AV**: rate for the automated fleet
- **R_H**: human benchmark rate for comparable roads and places
- **Reduction**: fractional decrease. ×100 gives a percent.
- **Rate ratio**: "how many times safer" (e.g. 6.8×)

### 8.8 How sure are we? Poisson counting uncertainty

Crashes are rare, independent events, so the count N is roughly **Poisson**, with standard deviation **σ_N ≈ √N**.

- **N**: observed crash count
- **σ_N**: approximate standard deviation of that count
- A rough 95% range is N ± 2√N for large N. For small N, use exact Poisson tables.

**Implication:** a dataset with 3 crashes has relative uncertainty of about √3/3 ≈ 58%, while one with 100 crashes is about 10%. This is why more miles give more trustworthy safety claims, and why serious-injury percentages move between updates [18].

### 8.9 V2X radio wavelength and latency

$$ \lambda = \frac{c}{f},\qquad t_{prop} = \frac{d}{c}$$

- **λ**: wavelength (m)
- **f**: frequency (Hz), 5.9 × 10⁹ Hz for C-V2X
- **t_prop**: time for the radio signal to travel distance **d** (s)
- **c**: speed of light, 3.00 × 10⁸ m/s

At 5.9 GHz, λ ≈ 5.1 cm. A message crosses 300 m in 1 µs, so propagation is negligible. Real delay comes from processing and the message schedule (often about 10 messages per second, a typical figure for safety broadcasts and not from the cited sources).

---

## 9. Worked examples

**Example 1: Lidar.** An echo returns 400 ns after the pulse. How far is the object?
d = (3.00×10⁸ m/s)(400×10⁻⁹ s)/2 = 120 m / 2 = **60 m**.

**Example 2: Radar Doppler.** A 77 GHz radar sees a car closing at 30 m/s (108 km/h).
λ = 3.00×10⁸/77×10⁹ = **3.90 mm**. f_d = 2(30)/0.00390 ≈ **15.4 kHz**. That works out to about 513 Hz per m/s.

**Example 3: Radar range resolution.** A chirp sweeps B = 4 GHz (e.g. 77–81 GHz).
ΔR = c/(2B) = 3.00×10⁸/(8×10⁹) = **3.75 cm**.

**Example 4: Human vs AV stopping.** v₀ = 25 m/s (≈ 56 mph), dry road μ = 0.7, g = 9.81 m/s².
- Braking distance = 25²/(2·0.7·9.81) = 625/13.73 ≈ **45.5 m** (the same for both, since it is the same tires on the same road).
- Human, t_r = 1.5 s: reaction distance = 37.5 m, so the total is **83.0 m**.
- AV, assumed t_r = 0.5 s: reaction distance = 12.5 m, so the total is **58.0 m**.
- The AV stops **25 m (about 30%) shorter**, purely from reacting faster. Physics limits the braking, so faster sensing and deciding is where automation helps.
- *Extension:* if a pedestrian is 60 m ahead, how fast is the human still going when reaching them? Use v_p² = v₀² − 2a·d_b, where **v_p** is the car's speed on reaching the pedestrian (m/s), **v₀** = 25 m/s the starting speed, **a** = μg = 0.7 × 9.81 = 6.867 m/s² the deceleration, and **d_b** the distance actually spent braking before the pedestrian (m). After 37.5 m of reaction, d_b = 60 − 37.5 = 22.5 m. v_p² = 625 − 2(6.867)(22.5) = 625 − 309 = 316, so v_p ≈ **17.8 m/s (≈ 40 mph)**. The AV stops 2 m short (58.0 m < 60 m).

**Example 5: Sensor fusion.** Lidar says 50.0 m (σ = 0.1 m). Radar says 50.6 m (σ = 0.5 m).
x̂ = (0.25·50.0 + 0.01·50.6)/(0.26) = **50.02 m**. σ = √(0.0025/0.26) ≈ **0.098 m**. The fused estimate leans strongly toward the more precise lidar and is slightly better than either sensor alone.

**Example 6: Waymo's 2023 numbers (check the sheet's 85%).**
- R_AV = 0.41 IPMM and R_H = 2.78 IPMM. Reduction = 1 − 0.41/2.78 = 1 − 0.147 = **85.3%**. Rate ratio = 2.78/0.41 ≈ **6.8×**. This matches Waymo's blog [16].
- Expected human-benchmark crashes in 7.14 M mi: 2.78 × 7.14 ≈ **19.8**. AV crashes: 0.41 × 7.14 ≈ **2.9**, so about 3 events.
- **How uncertain is "3"?** N = 3 is a small count, so (per Section 8.8) use the exact Poisson 95% interval rather than N ± 2√N: for an observed count of 3 it is about **0.62 to 8.77** events (standard table value). Divide by M = 7.14 million miles: R_AV is between about **0.087 and 1.23 IPMM**. Against R_H = 2.78, the reduction is between 1 − 1.23/2.78 ≈ **56%** and 1 − 0.087/2.78 ≈ **97%** (ignoring the benchmark's own uncertainty). So the data clearly show a reduction, but "85%" is a point estimate inside a wide range.
- **Why the published figure became ~80%:** not counting noise. The peer-reviewed paper re-analyzed the *same* miles with a revised method, giving 0.6 vs 2.80 IPMM, about 79–80% after rounding [17]. That revised value also lies inside the 56–97% range, which shows why small-count results can shift when the method changes.
- Police-reported crashes (revised): 1 − 2.1/4.68 = **55%** [17].

**Example 7: Traffic flow.** A lane has density k = 30 veh/km at stream speed v_s = 60 km/h.
Flow q = k·v_s = 30 × 60 = **1,800 veh/h**. Headway h = 3600/q = 3600/1800 = **2.0 s**. Spacing s = 1000/k = 1000/30 ≈ **33 m**.
In Sugiyama's ring: k = 22/0.230 km ≈ **96 veh/km** and s ≈ **10.5 m** per car (including the car's own length). That is dense enough for waves to grow [21].

**Example 8: Time-to-collision.** An AV traveling 25 m/s is 40 m behind a car going 15 m/s.
TTC = g_ap/(v_f − v_l) = 40/(25 − 15) = **4.0 s**. To avoid contact by braking alone, it must shed the 10 m/s closing speed Δv_c = v_f − v_l within the 40 m gap: a_req = Δv_c²/(2·g_ap) = 10²/(2·40) = **1.25 m/s²**, where **a_req** is the minimum constant deceleration of the AV relative to the lead car (m/s²) and **Δv_c** is the closing speed (m/s). (Same kinematics as 8.4, applied to relative motion.) That is gentle, so the AV has plenty of margin if it reacts early.

**Example 9: Fleet scaling.** Waymo has 500,000 rides a week with ~3,000 cars and targets 1,000,000 rides a week [1].
- **Scenario A, same use rate (~167 rides/car/week):** about **6,000 cars**. Depot (parking and maintenance) space, charging and curb activity all roughly double.
- **Scenario B, same 3,000 cars:** each car must reach ~333 rides/car/week. Depot *parking* space stays about the same, but miles per car, charging energy (and charging time per car), maintenance and curb stops roughly double.
- In both scenarios, total charging energy and curb pickups roughly double, because they scale with rides and miles, not with car count. That is an infrastructure question.

---

## 10. Practice questions with answers

1. **An echo returns after 0.20 µs. What is the range?** → d = (3×10⁸)(0.20×10⁻⁶)/2 = **30 m**.
2. **Why is there a factor of 2 in both the lidar and the radar Doppler equations?** → Lidar: the light makes a round trip. Doppler: the frequency shifts once when the target receives the wave and again when it reflects it.
3. **A car crosses directly in front of a radar, perpendicular to the beam. What Doppler shift does the radar see?** → About **zero**. Only the radial component of velocity produces a shift. This is one reason AVs fuse radar with lidar and cameras.
4. **If speed doubles, by what factor does braking distance change?** → **×4**, since d ∝ v².
5. **Which SAE level requires the human to monitor at all times: Level 2 or Level 3?** → **Level 2**. At Level 3 the system monitors, but the human must take over when asked.
6. **Name the form, deadline and regulation for an AV collision report to the California DMV (testing permits, as described on source 3).** → **OL 316, within 10 days, 13 CCR §227.48** [3][14]. Since April 28, 2026, DMV collision reporting is aligned with NHTSA's SGO (renumbered §227.54) [46][47].
7. **What new event type did the CPUC require in 2024, and why?** → **Stoppage events** (vehicles stuck in service), to measure how service interruptions affect passengers and the public, e.g. by blocking traffic or emergency vehicles [7].
8. **What are the three goals of USDOT's Automated Vehicles Comprehensive Plan?** → Promote Collaboration and Transparency. Modernize the Regulatory Environment. Prepare the Transportation System [4][22].
9. **What does the TGSIM Foggy Bottom dataset contain that I-395 doesn't?** → Pedestrians, bicycles and scooters at **urban intersections** (12 4K cameras, 4 intersections). I-395 is an **expressway merge** [8][9].
10. **Under the SGO, why report a crash where the ADS disengaged 10 s before impact?** → The rule covers crashes with automation engaged **within 30 seconds** before the crash, so a system can't avoid reporting by disengaging just before impact [13].
11. **The sheet says "85% reduction." What is the more current or peer-reviewed figure, and why might it differ?** → About 80% (peer-reviewed; revised method) and about 92% for serious-injury-or-worse crashes over ~170.7 M miles through Dec 2025. The numbers differ because of different injury categories, benchmark adjustments and much more data [17][18].
12. **Is "94% of crashes are caused by human error" an accurate reading of NHTSA's study?** → **No.** 94% is the share where the driver was assigned the *critical reason*, the last failure in the event chain. NHTSA says this is not a cause or a fault assignment [12].
13. **How can one automated car reduce a phantom jam?** → By driving at a steady, smoothed speed and leaving a buffer, it absorbs fluctuations instead of amplifying them. Stern et al. damped waves in a ring with 20+ cars using just one AV [20].
14. **Fuse two measurements: 10.0 m (σ = 0.2) and 10.4 m (σ = 0.2).** → Equal weights give **10.2 m**, and σ = 0.2/√2 ≈ **0.14 m**.
15. **Motional's Las Vegas service: driverless or not?** → **Not yet.** It has a human safety operator, and fully driverless service is targeted for the end of 2026, if authorities approve [2].
15a. **A pedestrian detector finds 95 of 100 real pedestrians and makes 5 false detections. Give precision and recall, and say which error causes collisions.** → TP = 95, FN = 5, FP = 5. Precision = 95/100 = **0.95**; recall = 95/100 = **0.95**. The **5 misses (false negatives)** risk collisions; the 5 false detections risk phantom braking [44].
15b. **Why is the "long tail" the main challenge for ML-based driving, and name two ways engineers address it.** → Rare situations appear too seldom in training data for a model to learn them. Answers: mining fleet logs for hard cases and retraining; generating rare scenes in simulation (e.g. Waymo's World Model); relying on lidar geometry and rule-based safety layers to treat unknown objects as obstacles [41][42].
16. **What spectrum is reserved for V2X in the U.S.?** → The upper **30 MHz of the 5.9 GHz band (5.895–5.925 GHz)**, using **C-V2X** [26].
17. **A California robotaxi (CPUC deployment permit) hits a pedestrian, who goes to the hospital. Who must be told, and how fast?** →
    - **CPUC: within 1 day** (its Nov 2024 permit condition) [7].
    - **NHTSA: within 1 day**, because the same CPUC condition requires the report to NHTSA within one day [7]. NHTSA's own SGO would allow **5 calendar days** for this most-serious-tier crash (a vulnerable road user struck and hospitalized) [13][38], but the stricter permit condition controls for a California CPUC permit holder.
    - **DMV: yes.** Since April 28, 2026, collision reports go to the DMV in alignment with the SGO, i.e. within 5 days for this tier [46]. (Before then, a deployment-only permit carried no DMV collision-report duty, because AB 3061 was vetoed [31][45]; the 10-day OL 316 rule applied to testing permits [14].)
    - **Takeaway:** different agencies, different clocks; the tightest is 1 day.
18. **Free response: "Analyze how fleets of AVs may impact safety and infrastructure needs."** → Good structure: (a) safety benefits with numbers and caveats (Sections 3.3 and 5); (b) mechanisms: sensors, ML perception and its error tradeoffs, redundancy, reaction time (Sections 4, 8.4 and 9); (c) traffic flow: wave damping, V2X (Section 7.2); (d) infrastructure: curbs, charging, roadside units, maps, responders, data reporting (Section 7.3); (e) risks: stoppages, induced VMT and deadhead miles, cybersecurity, company-reported data (Section 5.2).

---

## 11. Quick-review sheet

- **d = cΔt/2** (lidar; Δt = round-trip time) · **f_d = 2v_r/λ** (Doppler; v_r = radial speed) · **ΔR = c/2B** (radar resolution; B = chirp bandwidth) · **d_stop = v₀t_r + v₀²/2μg** (stopping) · **q = k·v_s** (flow = density × speed) · **TTC = g_ap/(v_f − v_l)** · fused **σ² = σ₁²σ₂²/(σ₁²+σ₂²)** · **R = N/M** (crashes per million miles) · **Precision = TP/(TP+FP), Recall = TP/(TP+FN)** · **w_new = w_old − η∂L/∂w** (gradient descent). Full definitions in Sections 4.4 and 8.
- **SAE:** 0 none, 1 steer *or* speed, 2 both but human supervises, 3 system drives and human is fallback, 4 no human needed in ODD, 5 everywhere.
- **Waymo:** ~500k paid rides/week; >4 M autonomous miles/week; ~3,000 cars; 11 cities (10 with riders); target 1 M rides/week by end of 2026; 6th gen = 13 cameras, 4 lidar, 6 radar.
- **Safety stats:** sheet's 85% (Dec 2023, 7.14 M RO miles) → peer-reviewed ~80% → hub ~92% fewer serious-injury crashes (170.7 M miles to Dec 2025).
- **Motional + Uber:** Las Vegas, March 2026, IONIQ 5, safety operator, driverless goal end of 2026.
- **CA DMV:** OL 316, 10 days, 13 CCR §227.48 (testing permits; deployment had a gap; AB 3061 vetoed Sept 2024). Since April 28, 2026, collision reports aligned with the NHTSA SGO. New AV rules April 28, 2026: heavy trucks allowed, safety case, 50k/500k test miles. Cruise permits suspended Oct 24, 2023.
- **CPUC:** quarterly data (miles, EV share, deadhead); Nov 2024: stoppage events, trip-level incidents, collisions reported to **both CPUC and NHTSA within 1 day** (a state permit condition that still applies after NHTSA's own deadline became 5 days).
- **NHTSA SGO (federal):** ADS and L2 crashes; 30-second window; 3rd Amended (effective June 16, 2025): most serious crashes **5 days**; less serious ADS crashes **monthly, by the 15th**; old rule was 1 day.
- **USDOT AVCP (2021):** Collaboration and Transparency · Modernize Regulation · Prepare the System.
- **TGSIM:** 6 datasets; I-395 = D.C. expressway merge, cameras, AVs + cars, trucks and buses; Foggy Bottom = 12 4K cameras, 4 intersections, pedestrians, bikes and scooters.
- **Traffic waves:** Sugiyama 2008 (22 cars, 230 m ring); Stern 2018 (1 AV among ~20 damps waves; authors project "less than 5%" AVs could control flow); Stern 2019 (15% CO₂ to 73% NOₓ cut, only where waves occur).
- **ML:** label → train (minimize loss by gradient descent) → validate → mine hard cases → retrain. Long tail = rare cases. **Precision = TP/(TP+FP)** (false positives → phantom braking); **Recall = TP/(TP+FN)** (false negatives → collisions). EMMA (Waymo, 2024): end-to-end, camera-only research model; deployed cars still fuse lidar and radar.
- **V2X:** C-V2X, 5.895–5.925 GHz.
- **94% caveat:** "critical reason," not fault.

---

## 12. Assumptions and how sources were consulted

**Assumptions**
- "At least 15 sites" means 15 distinct web pages. This guide cites **47**, each entry with exactly one URL, including all 5 URLs you gave and all 9 "Explore More" titles. Some titles overlap with your URLs: the Waymo article, the Motional article, the DMV page, the USDOT plan and the NHTSA page. That leaves 4 sheet-only titles, which were found by title.
- "Use the sources" means summarize each one's key content and tie it to the section's stated task: safety, infrastructure and sensor function.
- Where a source's figures are outdated or disputed (e.g. the sheet's 85%), the guide gives the newer figure and the reason, because a TEAMS test or a judge may use either.
- Examples that need an assumed value (e.g. AV reaction time 0.5 s, TTC conflict thresholds, V2X message rate) are labeled as assumptions, not as sourced facts.

**How sources were consulted.** No page in this guide was opened directly. The research environment's network proxy blocked direct page loads; attempts to load pages on dmv.ca.gov, waymo.com, arxiv.org and assembly.ca.gov were refused outright. Every source, including all five URLs you gave, was therefore consulted through web-search results that index and quote the page's own text. Every citation is a real URL that appeared in those results, and the facts attributed to it come from that indexed content. Before the competition, click through each link to confirm current figures. Some pages, especially the Waymo hub, the CPUC quarterly page and the DMV rules, are updated regularly. The TGSIM datasets were found by title in the federal data catalog (catalog.data.gov); the datasets themselves live on USDOT's data portal and ITS DataHub [19]. For source 4, search results show that the page at transportation.gov/av/avcp/5 is the plan's landing page, which links to the plan PDF [22]; the plan's content was taken from that PDF's indexed text. Each fact is tied to the single entry that supports it.

**Requirement checklist**

| Requirement | Where met |
|---|---|
| All 5 given URLs used | [1] §3.1 · [2] §3.2 · [3] §5.3 · [4] §6.4 · [5] §6.1 |
| All 9 "Explore More" titles used | Above, plus CPUC quarterly [6] §5.4 · CPUC enhanced reporting [7] §5.4 · TGSIM I-395 [8] §7.1 · TGSIM Foggy Bottom [9] §7.1 |
| ≥ 15 sites, including those above | 47 sites, one URL each (Section 13) |
| Every equation's variables defined | Section 8 (each variable listed under its equation, including the derivation, energy check and Kalman prediction); Section 4.4 (precision, recall, loss, gradient descent); Sections 1, 7.1, 9 and 11 restate symbols where equations appear |
| Citation page | Section 13 |
| Covers the sheet's task (safety, infrastructure, sensors) and its three named technologies (sensors, ML, V2X) | Sections 4 (sensors 4.2–4.3, ML 4.4), 5, 6.5 and 7 (V2X) |

---

## 13. Citation page

**A. Sources you provided (URLs)**

1. Electric Vehicles (eletric-vehicles.com). "Waymo Hits 500,000 Weekly Rides and Over 4 Million Miles, co-CEO Says." https://eletric-vehicles.com/waymo/waymo-hits-500000-weekly-rides-and-over-4-million-miles-co-ceo-says/
2. Motional. "Uber and Motional Launch Robotaxi Service in Las Vegas." https://motional.com/news/uber-and-motional-launch-robotaxi-service-las-vegas
3. California Department of Motor Vehicles. "Autonomous Vehicle Collision Reports." https://www.dmv.ca.gov/portal/vehicle-industry-services/autonomous-vehicles/autonomous-vehicle-collision-reports/
4. U.S. Department of Transportation. "USDOT's Automated Vehicles Comprehensive Plan" (landing page that links to the plan PDF, entry 22). https://www.transportation.gov/av/avcp/5
5. National Highway Traffic Safety Administration. "Automated Driving Systems." https://www.nhtsa.gov/vehicle-manufacturers/automated-driving-systems

**B. "Explore More" sources found by title**

6. California Public Utilities Commission. "AV Program Quarterly Reporting." https://www.cpuc.ca.gov/regulatory-services/licensing/transportation-licensing-and-analysis-branch/autonomous-vehicle-programs/quarterly-reporting
7. California Public Utilities Commission. "CPUC Enhances Autonomous Vehicle Reporting Requirements to Boost Safety Standards" (Nov 7, 2024). https://www.cpuc.ca.gov/news-and-updates/all-news/cpuc-enhances-autonomous-vehicle-reporting-requirements-to-boost-safety-standards
8. U.S. Department of Transportation (via Data.gov). "Third Generation Simulation Data (TGSIM) I-395 Trajectories." https://catalog.data.gov/dataset/third-generation-simulation-data-tgsim-i-395-trajectories
9. U.S. Department of Transportation (via Data.gov). "Third Generation Simulation Data (TGSIM) Foggy Bottom Trajectories." https://catalog.data.gov/dataset/third-generation-simulation-data-tgsim-foggy-bottom-trajectories

**C. Additional reliable sources**

10. Our World in Data. "Passenger-kilometers traveled by self-driving taxis" (from CPUC quarterly data). https://ourworldindata.org/grapher/passenger-kilometers-traveled-self-driving-taxis
11. California Public Utilities Commission. Decision in Rulemaking R.12-12-011 (AV data reporting). https://docs.cpuc.ca.gov/PublishedDocs/Published/G000/M546/K031/546031802.PDF
12. NHTSA. "Critical Reasons for Crashes Investigated in the National Motor Vehicle Crash Causation Survey," Traffic Safety Facts DOT HS 812 115 (2015). https://crashstats.nhtsa.dot.gov/Api/Public/Publication/812115
13. NHTSA. "Standing General Order on Crash Reporting." https://www.nhtsa.gov/laws-regulations/standing-general-order-crash-reporting
14. Cornell Law School, Legal Information Institute. Cal. Code Regs. tit. 13, § 227.48, "Reporting Collisions." https://www.law.cornell.edu/regulations/california/13-CCR-227.48
15. Bloomberg. "Waymo Co-CEO Outlines Path to 1 Million Weekly Trips in 2026" (Feb 11, 2026). https://www.bloomberg.com/news/articles/2026-02-11/waymo-co-ceo-outlines-path-to-1-million-weekly-trips-in-2026
16. Waymo. "Waymo significantly outperforms comparable human benchmarks over 7+ million miles of rider-only driving" (Dec 2023). https://waymo.com/blog/2023/12/waymo-significantly-outperforms-comparable-human-benchmarks-over-7-million/
17. Kusano, K. D., et al. "Comparison of Waymo Rider-Only Crash Data to Human Benchmarks at 7.1 Million Miles," arXiv:2312.12675 (published in *Traffic Injury Prevention*, 2024, doi:10.1080/15389588.2024.2380786). https://arxiv.org/abs/2312.12675
18. Waymo. "Safety Impact" data hub. https://waymo.com/safety/impact/
19. U.S. DOT / FHWA (Univ. of Illinois Urbana-Champaign). "Third Generation Simulation Data (TGSIM): A Closer Look at the Impacts of Automated Driving Systems on Human Behavior," FHWA-JPO-24-133 (2024). https://rosap.ntl.bts.gov/view/dot/74647
20. Stern, R. E., et al. "Dissipation of stop-and-go waves via control of autonomous vehicles: Field experiments," *Transportation Research Part C* 89 (2018): 205–221. https://arxiv.org/abs/1705.01693
21. Sugiyama, Y., et al. "Traffic jams without bottlenecks—experimental evidence for the physical mechanism of the formation of a jam," *New Journal of Physics* 10, 033001 (2008). https://ir.library.osaka-u.ac.jp/repo/ouka/all/93262/
22. U.S. Department of Transportation. *Automated Vehicles Comprehensive Plan* (PDF, Jan 2021). https://www.transportation.gov/sites/dot.gov/files/2021-01/USDOT_AVCP.pdf
23. American National Standards Institute (ANSI) Blog. "Defining Automated Driving Systems: SAE J3016-2021." https://blog.ansi.org/ansi/defining-automated-driving-systems-sae-j-3016-2021/
24. Li, Y., and Ibanez-Guzman, J. "Lidar for Autonomous Driving: The principles, challenges, and trends for automotive lidar and perception systems," arXiv:2004.08467. https://arxiv.org/pdf/2004.08467
25. MathWorks. "Automotive Adaptive Cruise Control Using FMCW Technology." https://in.mathworks.com/help/radar/ug/automotive-adaptive-cruise-control-using-fmcw-technology.html
26. Federal Communications Commission. Second Report and Order, FCC 24-123 (5.9 GHz band / C-V2X). https://docs.fcc.gov/public/attachments/FCC-24-123A1_Rcd.pdf
27. Crowell & Moring. "NHTSA Announces First Actions Under Trump Administration's New Framework for Removing Regulatory Barriers for Automated Vehicles" (Apr 2025). https://www.crowell.com/en/insights/client-alerts/nhtsa-announces-first-actions-under-trump-administrations-new-framework-for-removing-regulatory-barriers-for-automated-vehicles
28. Waymo. "Fully autonomous operations on the 6th-generation Waymo Driver" (Feb 2026). https://waymo.com/blog/2026/02/ro-on-6th-gen-waymo-driver
29. Fox5 Las Vegas. "Uber partners with Motional to launch robotaxi service in Las Vegas" (Mar 13, 2026). https://www.fox5vegas.com/2026/03/13/uber-motional-launch-commercial-robotaxi-service-las-vegas/
30. Wikipedia. "Stopping sight distance" (summarizing AASHTO design values). https://en.wikipedia.org/wiki/Stopping_sight_distance
31. California State Assembly Communications and Conveyance Committee. Bill analysis of AB 3061 (2024), autonomous vehicle incident reporting. https://acom.assembly.ca.gov/media/438
32. California Public Utilities Commission. "AV Data Workshop" slides (June 22, 2023). https://www.cpuc.ca.gov/-/media/cpuc-website/divisions/consumer-protection-and-enforcement-division/documents/tlab/av-programs/20230622-cpuc-av-data-workshop-slides.pdf

33. Indiana Department of Transportation. *Indiana Design Manual*, Chapter 42 (sight distance; AASHTO values cross-check). https://secure.in.gov/indot/design-manual/files/Ch42_2012.pdf
34. GovTech. "California DMV creates first public data set on driverless car crashes." https://www.govtech.com/fs/california-dmv-creates-first-public-data-set-on-driverless-car-crashes.html
35. California Department of Motor Vehicles. "New Autonomous Vehicle Regulations Strengthen Oversight and Enforcement, Authorize Trucks and Transit" (Apr 28, 2026). https://www.dmv.ca.gov/portal/news-and-media/new-autonomous-vehicle-regulations-strengthen-oversight-and-enforcement-authorize-trucks-and-transit/
36. California Department of Motor Vehicles. "DMV Statement on Cruise LLC Suspension" (Oct 24, 2023). https://www.dmv.ca.gov/portal/news-and-media/dmv-statement-on-cruise-llc/
37. Stern, R. E., et al. "Quantifying air quality benefits resulting from few autonomous vehicles stabilizing traffic," *Transportation Research Part D* 67 (2019): 351–365, doi:10.1016/j.trd.2018.12.008. https://csl.isis.vanderbilt.edu/publications/stern2019trd/
38. NHTSA. *Third Amended Standing General Order 2021-01* (Apr 2025; effective June 16, 2025). https://www.nhtsa.gov/sites/nhtsa.gov/files/2025-04/third-amended-SGO-2021-01_2025.pdf
39. Sidley Austin LLP. "NHTSA Announces New Policies to Promote Autonomous Vehicles" (Apr 29, 2025). https://environmentalhealthsafetybrief.sidley.com/2025/04/29/nhtsa-announces-new-policies-to-promote-autonomous-vehicles/
40. U.S. Department of Transportation. *DOT's National Strategy for Automated Vehicles* (Sept 2026). https://www.transportation.gov/sites/dot.gov/files/2026-09/AV%20National%20Strategy_508_3Sep2026.pdf
41. Hwang, J.-J., et al. (Waymo). "EMMA: End-to-End Multimodal Model for Autonomous Driving," arXiv:2410.23262 (Oct 2024). https://arxiv.org/abs/2410.23262
42. Waymo. "The Waymo World Model: A New Frontier for Autonomous Driving Simulation" (Feb 2026). https://waymo.com/blog/2026/02/the-waymo-world-model-a-new-frontier-for-autonomous-driving-simulation
43. NHTSA Office of Defects Investigation. Closing resume, Preliminary Evaluation PE22-002 (unexpected braking, Tesla Model 3/Y), 2026. https://static.nhtsa.gov/odi/inv/2022/INCLA-PE22002-25796.pdf
44. Datature. "Precision and Recall" (glossary; threshold tradeoff and phantom-braking example). https://datature.io/glossary/precision-and-recall
45. CalMatters Digital Democracy. "AB 3061 (2023–2024): Vehicles: autonomous vehicle incident reporting" (status: vetoed by Governor, Sept 27, 2024). https://calmatters.digitaldemocracy.org/bills/ca_202320240ab3061
46. California Department of Motor Vehicles. Autonomous Vehicle Industry Memo AVIM 2026-001A, "Reporting Requirements" (effective Apr 28, 2026). https://www.dmv.ca.gov/portal/file/avim-2026-001-reporting-requirements-pdf/
47. California Department of Motor Vehicles. "Statement of Reasons for the Second Modified Regulatory Text" (autonomous vehicles, Jan 2026). https://www.dmv.ca.gov/portal/file/statement-of-reasons-for-the-second-modified-regulatory-text-january-2026-pdf/

*All sources were accessed October 2026 through web-search indexing (see Section 12). Verify the latest figures on each live page before the competition.*
