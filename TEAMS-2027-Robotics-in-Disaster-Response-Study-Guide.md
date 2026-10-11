# Robotics in Disaster Response: TEAMS 2027 Study Guide
*TSA TEAMS 2027, "Engineering a Smarter World"*

---

## 0. Read this first

### What this guide is built to do
The section sheet says your team "may estimate response times and evaluate the economic implications of implementing robotics." TEAMS tests engineering aptitude, mathematics and science, so this guide has two jobs:

1. **Knowledge**: the vocabulary, history, standards, programs and real deployments you are likely to be asked about. Sections 1 to 6.
2. **Quantitative toolkit**: worked models for response time, search coverage, detection probability, drone endurance and data rate, radio range, thermal detection, robot stability, reliability, survival versus time and cost-benefit. **Every symbol in every equation is defined in a table next to it.** Sections 5, 7 and 8.

Section 9 has practice questions with answers. Section 10 lists claims to handle carefully. Section 11 is the citation page (65 sites).

### Assumptions
- **"Sites"** means distinct web pages. The citation page lists 65, including all 5 URLs you gave and all 7 "Explore More" titles.
- **"NIST: Performance of Emergency Response Robots"** had no URL. NIST has a project page with exactly that title, at nist.gov/programs-projects/emergency-response-robots ([2]). I use it.
- **"NSF: Robots to the Rescue"** had no URL. The NSF Stories page at nsf.gov/news/robots-rescue is that story: the Murphy–Nass project on making rescue robots less "creepy" to trapped victims ([5]). I use it.
- **Level**: written for students in AP Calc BC, AP Physics C and AP Bio. The models use derivatives, exponentials, logarithms, energy and power, and torque.

### How the sources were consulted (please read)
The research environment's network filter blocked direct page loading for every site I tried (for example nist.gov, dhs.gov, fema.gov, crasar.org, arxiv.org, cmu.edu, csiro.au, tees.tamu.edu). **I consulted every source through a web-search tool that returns each page's title, URL and indexed text.**

**The rule for this citation page:** a page is cited only if a search returned that exact page (title and URL) and its indexed text supports the claim it is cited for. An earlier draft of this guide cited some pages that I could not find again when I re-checked every citation. Those pages were removed, along with any fact that only they supported. Two examples are a claim about how often maps were refreshed at Surfside and a claim that Spot worked at Fukushima in 2022.

Limits that follow from this method:
- For pages marked **†** on the citation page, the search tool returned the title, URL and only a short snippet, not the full text. Each † page is used only for the narrow fact in that snippet. Open them yourselves if a question depends on them.
- For the **USV survey** ([7]) I read the abstract and metadata, not the full paper.
- Where sources disagree, the guide gives both numbers and says so. Where one source disagrees with itself and its own numbers settle the question, the guide shows that arithmetic and says which value it uses (for example, the £866 vs £886 drone cost in Section 8.2).

### Trade-offs I made, and what each one gives up
| Choice | Why | What it gives up |
|---|---|---|
| Heavy on quantitative models (Sections 5, 7, 8) | The sheet names response-time and economic estimates. Those are the parts of a TEAMS question you can actually lose points on. | Less narrative on topics like robot ethics and policy debates. |
| Every number has a source or is labeled *illustrative* | A wrong "fact" costs more on a test than a missing one | Some worked examples use made-up inputs. They teach the method, not the value. |
| Cite only pages I could re-find by search | Every citation must be a real, working URL | I dropped some plausible pages and a few vivid details I could not re-verify |
| Report conflicting figures as ranges, or settle them by the source's own arithmetic and show the check | Test writers may draw from either source | The guide is a little less tidy |
| A page of physics and biology folded into the topic | Your AP courses are your edge on the science questions | Assumes you already know the basic calculus |

---

## 1. The big picture

**Why robots?** Response is dangerous: structural collapses, hazardous-material (hazmat) leaks and high-altitude rescues all put responders at risk. Equipment often arrives too late, and manual debris removal is slow and costly (section sheet). Robots act as *extensions of the responder*. They go first, see more, and keep people out of the danger zone.

**Robin Murphy's key insight**: "disaster robotics is not really about robots but more about the data that they provide" ([22]). A robot is valuable when its information reaches the person making the decision, in time and in a usable form.

**What the sheet expects you to connect**: autonomy, remote sensing (thermal imaging, mapping), ruggedized hardware, haptics (touch feedback), plus emergency management, economics and community resilience.

### Core vocabulary
| Term | Meaning |
|---|---|
| **UGV** | Unmanned ground vehicle: tracked, wheeled, or legged (e.g., PackBot, Spot) |
| **UAS / sUAS / UAV** | Unmanned aircraft system / *small* UAS / unmanned aerial vehicle (a drone) |
| **USV** | Unmanned surface vehicle (robot boat) |
| **UUV / ROV** | Unmanned underwater vehicle / remotely operated vehicle (usually tethered) |
| **UMV** | Unmanned marine vehicle: a group term for USVs and UUVs ([7]) |
| **Teleoperation** | A human drives the robot remotely in real time. Most disaster robots work this way. |
| **Autonomy** | The robot makes some decisions itself (navigation, mapping) under human supervision |
| **Tether** | A cable carrying power and/or data. It is reliable through rubble but can snag, and it limits range (Quince, Section 4). |
| **Marsupial robots** | A larger "mother" robot carries smaller robots into tight spaces. Don't cite the WTC as an example: the NSF account of Ground Zero ([20]) does not support a marsupial robot being used there. |
| **US&R / USAR** | Urban search and rescue |
| **CBRNE** | Chemical, biological, radiological, nuclear, explosive hazards |
| **SLAM** | Simultaneous localization and mapping: building a map while tracking your own position in it |
| **Orthomosaic** | A map stitched together from many overhead drone photos ([29]), corrected so the whole image has a map's uniform scale |
| **Photogrammetry / point-cloud fusion** | Building 3D models from overlapping images, and merging aerial and ground 3D data into one map ([44]) |
| **Haptics** | Force or touch feedback to the operator, e.g., feeling how hard a gripper squeezes |
| **Standard test method** | An "agreed upon way to objectively measure robot capabilities" ([9]) |
| **AEL** | FEMA's Authorized Equipment List: which equipment *types* grant money may buy ([4]) |
| **MTBF** | Mean time between failures |
| **POD** | Probability of detection (search theory) |

### The four mission environments
| Environment | Typical robot | Key problems |
|---|---|---|
| Collapsed structures | Small tracked UGVs, small drones outside | Voids too small or unpredictable, rubble interior unreachable, radio blocked ([27], [30]) |
| CBRN / nuclear | Ruggedized UGVs, legged robots | Radiation, stairs, communications, long missions ([36], [39], [40]) |
| Floods, coasts, ports | USVs, ROVs, UAV–USV teams | Few real deployments so far, currents, debris, communications ([7], [47]) |
| Wide-area damage (hurricanes, floods) | sUAS | Airspace authorizations, battery endurance, data overload ([19], [22], [41]) |

---

## 2. Timeline of key events (memorize the dates)

| Year | Event | Why it matters | Source |
|---|---|---|---|
| 1995 | Oklahoma City bombing leads Robin Murphy to refocus her research on rescue robots | Origin of the field's best-known researcher | [21] |
| 2001 | **World Trade Center (9/11)**. CRASAR, founded that year by John Blitch, deploys robots. Murphy (then at the University of South Florida) and three students reach Ground Zero by 8 p.m. on Sept 12 and work about 12 days. Small, shoebox-sized robots help find five victims and another set of remains. | The **first reported use of robots for life-saving response** | [18], [20], [21] |
| 2002 | CRASAR becomes a USF center, with Murphy as director | | [18] |
| 2004 | Congress directs DHS to develop certification criteria for US&R robots. DHS asks NIST to lead the work. ASTM International is chosen as the standards body. | Start of the **DHS–NIST–ASTM standard test methods** | [3], [8] |
| 2005 | **Hurricane Katrina**: CRASAR flies the first small drones used for a disaster. **Hurricane Wilma**: CRASAR uses unmanned marine vehicles at Marco Island, FL, which it describes as their earliest known use. | First sUAS and first USV disaster use | [19], [26] |
| 2008 | CRASAR and Murphy move to Texas A&M | | [18], [21] |
| 2009 (ARRA) | NSF awards **$1.2M over 3 years** to Murphy (Texas A&M) and Clifford Nass (Stanford) to make rescue robots less "creepy" to trapped victims (**Survivor Buddy**) | Human–robot interaction for *victims* | [5], [24] |
| 2011 | **Fukushima Daiichi**: iRobot PackBot first enters a reactor building in April. Quince reaches the 3rd floor of Unit 2 on July 8. In October a Chiba Tech crawler (almost certainly Quince; the report does not name it) loses its link and is abandoned in the Unit 2 building. Cold shutdown on Dec 16, 2011. | Nuclear disaster robotics, where communications were the weak point | [36], [38] |
| 2015 | **DARPA Robotics Challenge (DRC) Finals**, motivated by Fukushima. **KAIST's DRC-HUBO wins**: 8 of 8 points in 44:28. | Humanoids doing disaster tasks: drive, door, valve, wall, stairs | [34], [35] |
| 2015 | Texas Memorial Day floods: one 20-minute drone flight produces 800+ images (1.7 GB) | Data overload becomes the bottleneck | [22] |
| 2016 | Fort Bend County, TX floods: 21 drone flights over 4 days. CRASAR tests EMILY (USV) with a tethered UAV alongside the Italian Coast Guard. | Routine drone use by emergency managers. UAV–USV teams for sea rescue. | [19], [47] |
| 2017 | **Hurricane Harvey**: FAA authorizes 43 organizations to fly drones. 355 emergency airspace authorizations across the 2017 hurricanes. | Drones become a normal part of damage assessment | [41], [42], [43] |
| 2018 | NFPA 2400 adopts NIST's 10 aerial test methods. DHS counts about 30 test methods (20 ground, 10 drone). CRASAR becomes an independent nonprofit. | Standards mature | [10], [13], [18] |
| 2020 | Boston Dynamics **Spot** walks beside Chernobyl's Reactor 4 on a radiation-mapping mission (a UK Atomic Energy Authority robot, sent with the RAIN initiative and the National Centre for Nuclear Robotics) | Legged robots for radiological mapping | [39] |
| 2021 | **DARPA Subterranean (SubT) Challenge** final: CERBERUS 1st ($2M) and CSIRO Data61 2nd ($1M), both 23 points. CERBERUS wins the tiebreak on time. MARBLE 3rd ($500K, 18 points). | Multi-robot autonomy underground | [31], [32] |
| 2021 | **Surfside condo collapse (FL)**: 304 strategic drone missions, the largest and longest recorded disaster use of drones. Ground robots could not get *into* the rubble. | Drones good for mapping. No robot existed that could search inside rubble. | [27], [28] |
| FY2025–2026 | Japan's Cabinet Office gives the new **Disaster Prevention Agency $100M for FY2025**, double the year before. Full operation is planned for FY2026. | Japan's national investment (see the caution in Section 10) | [51] |

---

## 3. Standards, testing and buying (the given sources)

### 3.1 NIST Response Robots and "Performance of Emergency Response Robots" ([1], [2], [9])
- NIST's **Intelligent Systems Division** leads a suite of **ASTM International Standard Test Methods for Response Robots**. It now has **more than 50 test methods** for remotely operated ground, aerial and maritime systems ([9]).
- **What a standard test method is**: "agreed upon ways to objectively measure robot capabilities." Each one isolates certain robot requirements and makes testing repeatable, so results from different places and dates can be compared ([9]).
- **The project goal** ([2]): develop the measurement science to *quantitatively evaluate* the capabilities of autonomous and remotely operated robots **and the proficiency of their remote operators and pilots**. NIST's program materials list test categories including maneuvering, mobility, dexterity, sensing, endurance, radio communication, durability, reliability, autonomy, logistics and safety ([2], [9]).
- **Operator proficiency**: NIST scores operators against an expert operator on the same robot, who counts as 100%. Operator skills are "very perishable," so teams re-test over time and compare squads or regions ([2], [9]).
- **Process**: test methods are developed by consensus, with equal representation of users, developers and test administrators. The committee is **ASTM E54.09 Response Robots**, under E54 Homeland Security Applications. **Adam Jacoff** of NIST chairs the subcommittee ([9], [11]).
- **Use**: the ground robot tests have been used by more than 250 civilian and military bomb technicians. NIST publishes a Response Robots Capabilities Compendium so buyers can filter results by mission ([9]).
- **ASTM examples** ([11], [12]): **E2521** (terminology), **E2566** (sensing: visual acuity), **E2853** (search tasks), **E2854** (radio communication: line-of-sight range). The E54.09 page lists 27 active standards and 16 proposed ones ([11]).

**Why test methods and not performance standards?** A *test method* says **how to measure** (e.g., "the steepest incline the robot can climb"). A *performance standard* sets **a pass mark**. For small drones, NIST says it is "not proposing to develop a standard sUAS specification of any kind" ([9]). The methods report numbers, and each buyer chooses the threshold that fits its own mission. That way one test serves a bomb squad, a fire department and a nuclear plant.

### 3.2 DHS S&T Robot Response Standards Program ([3], [8], [13], [14])
From the **DHS fact sheet** ([3]):
- Robot performance standards and test methods **were not in place before or immediately after 2001**. In 2004, **Congress directed DHS** to develop certification criteria for urban search-and-rescue robots.
- DHS S&T and its partners developed a suite of standard test methods and performance metrics. They cover **mobility, manipulation, sensors, energy, communication, mapping, human–robot interfaces, logistics and safety**, for ground vehicles, aquatic vehicles and small unmanned aerial vehicles.
- Status at publication: **15 test methods formally published through ASTM, 14 more in development**.
- Partners include FEMA's US&R task forces, the National Bomb Squad Commanders Advisory Board, the DHS Office of Bombing Prevention and ASTM International.

From NIST's DHS project page ([8]):
- DHS asked NIST to lead the work in 2004. A NIST/US&R responder advisory board defined **over 100 initial performance requirements** and **13 deployment categories**. The work began in ASTM subcommittee **E54.08** (operational equipment) and is now in E54.09.
- The program is sponsored by **DHS S&T** and the **National Institute of Justice**.

Later counts: DHS S&T reported **about 30 methods, 20 for ground robots and 10 for drones** in 2018 ([13]). AFCEA *Signal* repeats the same count, citing DHS ([14]). RoboCup Rescue 2018 judged its public-safety robots with these test methods, at three difficulty levels ([13]).

### 3.3 FEMA Authorized Equipment List (AEL) ([4], [15], [16])
- The AEL lists **equipment types** (not brand-name products) that FEMA preparedness grants may buy ([16]). Grant programs that can fund these items include the State Homeland Security Program (SHSP), the Urban Area Security Initiative (UASI), the Port Security Grant Program and the Transit Security Grant Program ([4], [16]).
- Robot-related items:
  - **03OE-07-ROBT**: robotic platforms (explosive device remediation, hazmat, tactical law enforcement, search & rescue, surveillance/detection). **03OE-07-ROVL**: remotely operated land vehicles. **03OE-07-UMVS**: unmanned maritime vehicle systems. **03OE-07-SUAS**: small unmanned aircraft systems. The older item **03OE-07-RPVS** was replaced by ROVL, UMVS and SUAS ([15], [16]).
  - **03OE-07-UPGD**: upgrades and accessories, such as software, battery or engine upgrades, arms, drive systems, range extenders and trailers. Cameras, detectors and disrupters are listed in other sections ([15]).
  - **03SR-05-RBTL**: search & rescue robot attachments, such as mountable cameras (including infrared), remote manipulators, listening devices and **repeaters for extended remote operation**. *For use only by specialty teams such as SAR or US&R* ([16]).
- AEL numbers cross-reference the **Standardized Equipment List** (SEL), although some AEL items are not on the SEL ([15]).
- **Why it matters for economics**: an agency usually buys a robot with grant money. The AEL decides *whether* it can. The NIST/ASTM test data helps decide *which one*.

**How the three fit together** (likely exam concept):
> **NIST/ASTM** measures what a robot can do → **DHS S&T** sponsors the standards for responders → **FEMA AEL** makes the equipment type grant-eligible → the agency buys, trains and checks operator proficiency with the same test methods, then deploys.

### 3.4 CRASAR ([6], [18], [19], [22], [23], [25])
- **Center for Robot-Assisted Search and Rescue**. It was founded in 2001 by **John Blitch** and became a University of South Florida center in 2002 with **Robin Murphy** as director. It moved to Texas A&M in 2008 and became an independent nonprofit in 2018. It describes itself as the oldest institution of its kind for public-safety robotics ([18]).
- **Roboticists Without Borders** is CRASAR's volunteer program. It supplies trained unmanned-system experts and equipment to agencies during disasters ([18], [19]).
- **Murphy's findings to know:**
  - Unmanned ground, aerial and marine vehicles have been used at **more than 46 disasters since 2001** ([22]).
  - **Human error caused 50% of mission-terminating failures** reported from 2001 to 2013. The barrier to adoption is poor **human–robot interaction**, not the vehicles ([22], [23]).
  - Robot operators see data in real time, but **decision-makers may wait half an hour or longer**, and the data arrives in incompatible file formats ([23]).
  - Small ground robots have been used at building collapses since 2001 but **have not been adopted into general practice by any country** ([25]).

### 3.5 USV survey: Jorge et al., *Sensors* 2019 ([7])
- Full title: "A Survey on Unmanned Surface Vehicles for Disaster Robotics: Main Challenges and Directions." *Sensors* 19(3):702, DOI 10.3390/s19030702, published Feb 8, 2019. Brazilian authors (PUCRS, UFRN and others).
- Describes itself as the **first comprehensive survey** of USV roles in disaster management.
- **Main finding**: there are **few real deployments** of USVs in disasters. Most research focuses on technology (guidance, navigation and control) rather than disaster operations. The paper ends with lessons learned, guidelines and research gaps.
- Disaster types in its keywords: floods, landslides, hurricanes, tsunamis, search and rescue.
- **Example of UAV–USV teaming: EMILY**, a robotic lifebuoy, is a small teleoperated "jet-ski" covered in flotation that can hold up several people in the water ([46]). In a 2016 exercise with the Italian Coast Guard, CRASAR paired EMILY with a tethered Fotokite drone and LTE communications. The exercise found that migrant boats in Italy carry **200–800 people**, and rescues happen much farther offshore than in Greece. That is why the drone's job is triage: deciding who needs help first ([47]).

### 3.6 NSF: Robots to the Rescue ([5], [24])
- Rescue robots are a trapped victim's lifeline. But they are "worthless if the victim finds them scary, bossy, out of control or just plain creepy." Robots don't make eye contact, their tone never changes, and they invade personal space ([5]).
- NSF funded a **3-year, $1.2 million** project under the American Recovery and Reinvestment Act of 2009. The grant was shared by Texas A&M (Murphy, CRASAR) and Stanford (Clifford Nass, who studied how people respond socially to technology). The team planned simulated rescues with real people ([5]).
- The result was **Survivor Buddy**, a multimedia robot "head" built with Stanford's CHIMe Lab. It links a trapped person to the outside world (video calls, web browsing) and is designed not to seem "creepy or socially inconsistent" ([24]).
- NSF also funded Murphy's original research on rescue robots that were used at the WTC ([20]).

---

## 4. Case studies: what worked and what didn't

| Event | What robots did | Lesson |
|---|---|---|
| **WTC 2001** ([18], [20], [21]) | Small, shoebox-sized robots searched spaces in the rubble. They helped find five victims and another set of remains. | Smaller robots are more useful than bigger ones in a collapse ([21]). Robots earned a place in rescue. |
| **Fukushima 2011** ([36], [37], [38]) | **PackBot** (off-the-shelf iRobot, about 30 kg) entered first. Its radiation tolerance was tested to several hundred mSv/h, and some units accumulated over 40 Sv. **Quince** (about 50 kg, Chiba Tech, Tohoku Univ. and IRS) reached upper floors in July 2011. Its tether needed several hundred meters of cable to reach the top floor. In October 2011 a Chiba Tech crawler lost its link and was abandoned inside Unit 2. Afterward, cable winding was automated and radio backup added. **4 of 5 failed robots had problems with control communications.** | Communications are the weak link. Quince's designer credits it with making the cold shutdown possible, or much sooner ([37]). |
| **DRC 2015** ([34], [35]) | Course: drive a utility vehicle and get out, open a door, **close a valve on a leaking pipe**, cut through a wall with a power tool, cross rubble, a surprise task, climb stairs. KAIST won with 8 points in 44:28. IHMC was 2nd (8 points, 50:26) and Tartan Rescue (CMU) 3rd. | The sheet's "robot shutting off a leaking valve" is *possible* but slow. The best robot needed about 45 minutes for 8 tasks. |
| **Harvey 2017** ([41], [42], [43]) | 43 organizations got FAA authorizations: a railroad, media, insurers, and oil and gas companies checking for leaks. Insurers used drones to evaluate claims on homes. | Drones speed up **damage assessment and economic recovery**. Airspace rules are part of the system. |
| **SubT 2021** ([31], [32], [33]) | Teams of legged, wheeled and flying robots explored a tunnel, cave and urban course in the Louisville Mega Cavern. CSIRO's map differed from DARPA's ground-truth map by less than 1%. | Autonomy and multiple robots working where there is no GPS and little radio |
| **Surfside 2021** ([27], [28], [29], [30]) | Miami-Dade Fire Rescue flew tactical flights 24/7 from right after the collapse, starting in the dark with thermal cameras and spotlights. FSU's team flew 169 missions and produced base maps. Nine-plus drone models and a tethered Fotokite were used. | **Mapping yes, finding victims no.** Humans and dogs could already search the surface. What was needed was a robot that could get *into* the rubble, and none existed ([27], [30]). |
| **Chernobyl 2020 / UK sites** ([39], [40]) | Spot walked beside Reactor 4 to find out which contaminated material was most dangerous ([39]). At Dounreay (UK), Spot with an NV-Explore sensor built **3D radiation maps** of a four-storey cell that no one had entered in 20+ years. A Spot with an arm took samples ([40]). | A mobile sensor goes to the source and keeps people out of the dose |

**The sheet's "map a collapsed building in seconds" claim, examined**:
- *Capturing* the images is fast. A 50 m × 50 m building takes well under a minute of flight (Section 7.2).
- *Making the map* is slow. Drone mapping "requires specialized software for collecting and post-processing drone imagery" ([28]).
- *Data volume* is large. One 20-minute flight produced 800+ images and 1.7 GB ([22]). Moving that much data is itself a radio problem (Section 7.3).

On a test, treat "seconds" as an aspiration and "minutes to hours, depending on processing and data links" as the current reality.

---

## 5. Core technologies (with the science)

### 5.1 Thermal imaging (AP Physics C: thermal radiation)
Thermal cameras mostly work in the **long-wave infrared (LWIR), roughly 7–14 µm**. Many use uncooled **microbolometers** (about 7.5–14 µm), whose electrical resistance changes as they absorb IR ([54], [55]). Sources put the lower edge of the band at 7, 7.5 or 8 µm.

**Wien's displacement law** ([53])

$$\lambda_{max} = \frac{b}{T}$$

| Symbol | Meaning | Units |
|---|---|---|
| λ_max | Wavelength at which a blackbody emits the most radiation | m |
| b | Wien's displacement constant, ≈ 2.898 × 10⁻³ | m·K |
| T | Absolute temperature of the emitting surface | K |

*Example*: skin at about 306 K (33 °C) gives λ_max = 2.898×10⁻³ / 306 ≈ **9.5 µm**, inside the LWIR band, so thermal cameras use LWIR detectors. A fire at 1000 K peaks near 2.9 µm.

**Stefan–Boltzmann law** (net radiated power)

$$P_{net} = \varepsilon \sigma A (T^4 - T_{env}^4)$$

| Symbol | Meaning | Units |
|---|---|---|
| P_net | Net power radiated by the object to its surroundings | W |
| ε | Emissivity (0–1). Skin ≈ 0.98, nearly a blackbody in the IR. | — |
| σ | Stefan–Boltzmann constant, 5.67 × 10⁻⁸ | W·m⁻²·K⁻⁴ |
| A | Radiating surface area | m² |
| T | Surface temperature of the object | K |
| T_env | Temperature of the surroundings | K |

*Example*: ε = 0.98, A = 1.8 m², T = 306 K, T_env = 293 K → P_net ≈ **140 W**.
*Engineering point*: detection depends on the **temperature difference** (T − T_env). A victim who is covered in dust, wet, or cooled toward ambient temperature shows little contrast. Rubble also blocks the line of sight. A thermal drone sees surfaces, not the inside of a collapse ([27]).

### 5.2 Radio communications (link budget)
Rubble, concrete and steel block radio. Robots use **tethers** (Quince needed several hundred meters of cable), **radio backup**, or **repeaters**, which are an AEL item ([16], [36]). At Fukushima, 4 of 5 failed robots had control-communication problems ([36]).

The same physics can be written two ways. Use the **linear form** with watts and plain-number gains. Use the **decibel form** with dBm and dBi, where multiplying becomes adding. Do not mix the two.

**(1) Friis transmission equation, linear form (free space)** ([56], [57])

$$P_R = P_T \, G_T \, G_R \left(\frac{\lambda}{4\pi d}\right)^2$$

| Symbol | Meaning | Units |
|---|---|---|
| P_R | Power received | W |
| P_T | Power transmitted | W |
| G_T, G_R | Gain of the transmitting and receiving antennas, as plain ratios (an isotropic antenna has G = 1) | dimensionless |
| λ | Wavelength of the radio wave, λ = c/f | m |
| c | Speed of light, 3.00 × 10⁸ | m/s |
| f | Frequency | Hz |
| d | Distance between the antennas | m |

**(2) Converting to decibels** (a logarithm turns the product into a sum)

$$P_{dBm} = 10\log_{10}\!\left(\frac{P}{1\ \text{mW}}\right), \qquad G_{dBi} = 10\log_{10}(G)$$

| Symbol | Meaning | Units |
|---|---|---|
| P | A power in watts (any of P_R, P_T) | W |
| 1 mW | The reference power, 10⁻³ W (so 0 dBm = 1 mW) | W |
| P_dBm | The same power expressed relative to 1 mW | dBm |
| G | An antenna gain as a plain ratio (G_T or G_R) | dimensionless |
| G_dBi | The same gain relative to an isotropic antenna | dBi |

Handy conversions: 20 dBm = 100 mW = 0.1 W; 30 dBm = 1 W; +3 dB ≈ ×2; +10 dB = ×10; 2 dBi = 10^(0.2) ≈ 1.58 (not 2).

**(3) Friis equation in decibel form (the "link budget")** ([57]): take 10log₁₀ of both sides of (1).

$$P_{R,dBm} = P_{T,dBm} + G_{T,dBi} + G_{R,dBi} - \text{FSPL}_{dB}$$

**(4) Free-space path loss** ([57]): the loss term is the reciprocal of the bracket in (1), expressed in dB.

$$\text{FSPL}_{dB} = 20\log_{10}\!\left(\frac{4\pi d}{\lambda}\right) = 20\log_{10}(d_{km}) + 20\log_{10}(f_{MHz}) + 32.44$$

| Symbol | Meaning | Units |
|---|---|---|
| P_R,dBm | Received power | dBm |
| P_T,dBm | Transmitted power | dBm |
| G_T,dBi, G_R,dBi | Transmit and receive antenna gains | dBi |
| FSPL_dB | Free-space path loss: how much weaker the signal gets over distance d with no obstacles | dB |
| d_km | Distance d expressed in kilometers | km |
| f_MHz | Frequency f expressed in megahertz | MHz |
| 32.44 | The constant left over from the unit choice: 20log₁₀(4π × 10³ × 10⁶ / c) ≈ 32.44 | dB |

**Worked example, done both ways**: a robot's 2.4 GHz link at d = 500 m, P_T = 20 dBm (0.1 W), and two 2 dBi antennas.
- *Decibel route*: FSPL = 20log(0.5) + 20log(2400) + 32.44 ≈ −6.02 + 67.60 + 32.44 = **94.0 dB**. Then by (3), P_R = 20 + 2 + 2 − 94.0 = **−70 dBm**.
- *Linear route (check)*: λ = 3.00×10⁸ / 2.4×10⁹ = 0.125 m. Bracket: (0.125 / (4π × 500))² ≈ 3.96 × 10⁻¹⁰. Gains: G_T = G_R = 10^(2/10) ≈ 1.58. By (1), P_R = 0.1 × 1.58 × 1.58 × 3.96×10⁻¹⁰ ≈ **9.9 × 10⁻¹¹ W**. Converting with (2): 10log₁₀(9.9×10⁻¹¹ / 10⁻³) ≈ **−70 dBm**. The two routes agree.
- *Common error*: putting P_T = 20 and G = 2 into the linear equation (1). Those are dB values; convert them first with (2).

*Key trade-off*: a higher frequency allows more bandwidth for video, but it has more path loss and penetrates walls worse. Doubling the distance or the frequency adds about 6 dB of loss. Friis is the *best case*, and real rubble adds large extra losses. That is why ASTM **E2854** measures radio line-of-sight range as a standard test ([12]).

### 5.3 Mobility and manipulation (AP Physics C: statics and torque)
**Static tip-over on a slope** (rigid robot, center of mass centered between the tracks, slope to the side):

$$\tan\theta_{tip} = \frac{b/2}{h}$$

| Symbol | Meaning | Units |
|---|---|---|
| θ_tip | Side-slope angle at which the robot starts to tip over | degrees |
| b | Track (or wheel) width, measured between the outer contact edges | m |
| h | Height of the center of mass above the ground | m |

*Example*: b = 0.50 m, h = 0.30 m → tan θ = 0.833 → θ ≈ **39.8°**. Raising an arm raises h, which lowers θ_tip. NIST's ground-robot maneuvering tests include traversing inclines, which measures this experimentally ([9]).

**Torque to turn a valve** (the DRC task and the sheet's "shut off a leaking valve" scenario):

$$\tau = r F \sin\phi$$

| Symbol | Meaning | Units |
|---|---|---|
| τ | Torque needed to turn the valve | N·m |
| r | Radius of the handwheel (lever arm) | m |
| F | Force applied by the robot's gripper | N |
| φ | Angle between the lever arm and the force (90° is best) | degrees |

*Example*: a stuck valve needs 60 N·m and the wheel radius is 0.15 m → F = 60/0.15 = **400 N** tangential. By Newton's third law, the robot must push back on the ground with an equal reaction, so it needs traction or bracing. This is where **haptics** helps: the operator *feels* resistance instead of guessing from video.

### 5.4 Haptics and teleoperation
- **Haptic feedback** sends force or touch information back to the operator's hand controller. The human can feel contact, grip force or a stuck valve.
- **Latency** (communication delay) is the enemy. Force feedback that arrives late can make the operator overcorrect. Over long or relayed links, teams often use *supervised autonomy*: the operator gives goals and the robot handles the fine motion.
- This links to Murphy's finding that **human error causes half of mission-ending failures** ([22], [23]). Better interfaces (haptics, 3D maps, fewer screens) are an engineering answer to a human problem.

### 5.5 Autonomy and AI (the 2027 theme)
- **SLAM, autonomous exploration and multi-robot coordination** decided DARPA SubT. CSIRO's robots built a map within 1% of DARPA's ground truth ([31], [33]).
- **Air–ground teaming**: a drone gives a fast, wide view, and a ground robot gives close, detailed data. In the EU TRADR project, point clouds from UAV cameras were fused with point clouds from a UGV's rotating laser scanner by matching flat surfaces (planar segments) in both ([44]). A 2024 review notes the open problems: smoke, flames, occlusion and fast-changing scenes ([45]).
- **AI-assisted detection**: imagery is the main data source for situational awareness and search, so computer vision is needed to keep up ([22]). The bottleneck is still trust, data formats and getting data to decision-makers ([23]).

### 5.6 Reliability
- Field **MTBF ≈ 6–20 hours** for search-and-rescue UGVs, from Carlson & Murphy's study ("How UGVs Physically Fail in the Field," *IEEE Trans. Robotics* 21(3), 2005), as summarized in a DTIC report on UGV reliability ([60]).
- For a constant failure rate, reliability over a mission of length t is

$$R(t) = e^{-t/\text{MTBF}}$$

| Symbol | Meaning | Units |
|---|---|---|
| R(t) | Probability the robot runs for time t without a failure | — |
| t | Mission duration | h |
| MTBF | Mean time between failures | h |

*Example*: MTBF = 6 h and a 2-hour mission → R = e^(−1/3) ≈ **0.72**, about a 28% chance of failing mid-mission. That is why teams bring a backup robot. With two independent robots:

$$P_{\ge 1} = 1 - (1-R)^n$$

| Symbol | Meaning | Units |
|---|---|---|
| P_≥1 | Probability that at least one robot completes the mission | — |
| R | Reliability of one robot over the mission | — |
| n | Number of independent robots | — |

With n = 2: 1 − (0.28)² ≈ **0.92**.

---

## 6. Biology connection (AP Bio): why minutes matter

- **Survival falls with time trapped.** The vast majority of rescues happen in the **first 24 hours** ([62]). More than **90% of earthquake survivors are rescued within the first three days** ([61]). Natural-hazards expert Steven Godby gives average survival ratios of **74% within 24 h, 22% after 72 h and 6% by day five** ([61]).
- **What decides survival**: air to breathe, how badly the person is injured, temperature, and above all **water**. People can last weeks without food but only a few days without water. A week or more is possible only in the best circumstances ([62]).
- **Crush syndrome**: crushed muscle breaks down (**rhabdomyolysis**). When the pressure is released, **potassium, myoglobin and phosphorus** flood the blood. This is a **reperfusion injury** ([63]). The results are **hyperkalemia** (a cause of early death through cardiac arrhythmia), acidosis and hypocalcemia ([63], [65]). Kidney damage follows from low blood volume combined with myoglobin in the urine ([64]). **IV fluids, ideally started before extrication**, may lessen the severity ([64]).
- **Engineering implications**:
  1. Finding victims sooner raises the survival odds (Section 7.4).
  2. A robot that reaches a victim **before extraction** can deliver water or air, carry vital-sign sensors, and give two-way audio and video, which is the job Survivor Buddy was designed for ([24]). Medics can then start fluids *before* the pressure is released.
  3. Robots that measure **air quality (O₂, CO, toxic gases)** protect both the victims and the rescuers.

---

## 7. Quantitative toolkit: response time

### 7.1 Response-time model
Break any response into stages and add them:

$$T_{resp} = t_{notify} + t_{mobilize} + \frac{D}{v} + t_{setup} + t_{task}$$

| Symbol | Meaning | Units |
|---|---|---|
| T_resp | Total time from the incident until the task is done | h |
| t_notify | Time to detect the incident and request help | h |
| t_mobilize | Time to assemble the team and equipment | h |
| D | Distance from the staging location to the site | km |
| v | Average travel speed | km/h |
| t_setup | Time to set up on site (launch, network, safety checks) | h |
| t_task | Time to do the task itself (search, map, inspect) | h |

**Worked example** (illustrative inputs, except the FEMA six-hour readiness figure ([17])). Both options count time to the *start* of the task, so t_task = 0 here.
- **Option A, national US&R task force** 250 km away: t_notify = 1 h, t_mobilize = 6 h (task forces are "ready to deploy within six hours" ([17])), travel 250/80 = 3.1 h, setup 1 h → **≈ 11.1 h** before searching starts.
- **Option B, local fire department sUAS** 40 km away: t_notify = 0.1 h, t_mobilize = 0.25 h, travel 40/60 = 0.67 h, setup 0.1 h → **≈ 1.1 h** to the first aerial view.
- **Difference**: 11.1 − 1.1 = **10.0 h** (used in 7.4).

**Interpretation**: the drone does not replace the task force. FEMA coordinates **28** task forces of **70 members** each: search, rescue, medical, hazmat, logistics and planning specialists, including structural engineers and canine teams. A task force can split into two 35-person teams for around-the-clock 12-hour shifts ([17]). The drone **fills the first 10 hours** with maps and size-up information, so the task force arrives knowing where to dig. Most of a robot's value is in **shortening the time to the first look**, not the total rescue time.

### 7.2 Area coverage time (drone mapping or search)
Camera footprint width on the ground:

$$w = 2h\tan\left(\frac{\text{FOV}}{2}\right)$$

Time to cover an area with parallel passes ("lawnmower" pattern):

$$t_{cover} = \frac{A}{v \cdot s}, \qquad s = w(1 - o)$$

| Symbol | Meaning | Units |
|---|---|---|
| w | Width of ground seen by the camera in one image | m |
| h | Flight altitude above the ground | m |
| FOV | Camera's horizontal field of view | degrees |
| t_cover | Flight time needed to cover the area (turns ignored) | s |
| A | Area to cover | m² |
| v | Ground speed of the drone | m/s |
| s | Spacing between parallel flight lines | m |
| o | Side-overlap fraction between neighboring passes (photogrammetry typically needs about 0.3–0.7) | — |

*Example*: h = 60 m and FOV = 50° → w = 2(60)tan 25° ≈ **56 m**. With o = 0.30, s ≈ 39 m. Covering A = 1 km² (10⁶ m²) at v = 10 m/s: t = 10⁶ / (10 × 39) ≈ 2,550 s ≈ **43 min**, about **2 battery packs** at the endurance found in 7.3, plus turns.
A 50 m × 50 m building is covered in under a minute of flight. Processing is the slow part (Section 4).

### 7.3 Drone endurance and data rate (AP Physics C: momentum theory and power)
Ideal hover power, from actuator-disk (momentum) theory:

$$P_{ideal} = \sqrt{\frac{T^3}{2\rho A_{rot}}}, \qquad T = mg, \qquad P_{actual} = \frac{P_{ideal}}{FM}$$

Flight time:

$$t_{flight} = \frac{E_{batt} \cdot f_{use}}{P_{actual}}, \qquad E_{batt} = V \cdot Q$$

| Symbol | Meaning | Units |
|---|---|---|
| P_ideal | Minimum (ideal) power to hover | W |
| T | Thrust needed; equals weight in hover | N |
| m | Drone mass including payload | kg |
| g | Gravitational acceleration, 9.81 | m/s² |
| ρ | Air density (≈ 1.225 at sea level) | kg/m³ |
| A_rot | Total rotor disk area = n·πr² for n rotors of radius r | m² |
| n | Number of rotors | — |
| r | Rotor radius | m |
| FM | Figure of merit: rotor efficiency, about 0.5–0.7 | — |
| P_actual | Real electrical power drawn in hover | W |
| E_batt | Battery energy | Wh |
| V | Battery voltage | V |
| Q | Battery capacity | Ah |
| f_use | Usable fraction of the battery (reserve kept for safety) | — |
| t_flight | Flight time | h |

*Example*: m = 2.0 kg → T = 19.6 N. Four rotors with r = 0.12 m → A_rot = 0.181 m². P_ideal = √(19.6³ / (2·1.225·0.181)) ≈ **131 W**. With FM = 0.6, P_actual ≈ **218 W**. A 22.2 V × 5 Ah = 111 Wh battery with f_use = 0.8 gives t = 88.8/218 ≈ 0.41 h ≈ **24 min**, consistent with the 20-minute flights reported at real responses ([22]).
*Calculus insight*: P ∝ T^(3/2) ∝ m^(3/2). **Doubling the mass multiplies hover power by 2^1.5 ≈ 2.8.** A heavy thermal camera or delivery payload sharply cuts endurance.

**Data rate needed to send a flight's imagery live:**

$$R_{data} = \frac{8\,D_{img}}{t_{flight}}$$

| Symbol | Meaning | Units |
|---|---|---|
| R_data | Average data rate needed to send the imagery as it is taken | bit/s |
| D_img | Data produced during the flight | bytes |
| 8 | Bits per byte | bit/byte |
| t_flight | Flight duration | s |

*Example* (data from [22]): 1.7 GB in a 20-minute flight → R = 8 × 1.7×10⁹ / 1200 ≈ **11 Mbit/s**, sustained. A damaged cell network often cannot carry that, which is one reason decision-makers wait half an hour or more for data ([23]).

### 7.4 Survival versus time (calculus: exponential models)
A simple model, **for illustration only**. The data points are one expert's averages, not a precise dataset ([61]).

$$S(t) = S_0 e^{-kt}, \qquad \frac{dS}{dt} = -kS$$

**Fitting k from two data points:**

$$k = \frac{\ln(S_1/S_2)}{t_2 - t_1}, \qquad t_{1/2} = \frac{\ln 2}{k}$$

| Symbol | Meaning | Units |
|---|---|---|
| S(t) | Survival ratio: fraction of trapped people reached at time t who are still alive | — |
| S_0 | Value of S at t = 0 (the model's intercept) | — |
| k | Decay rate constant | h⁻¹ |
| t | Time since the collapse | h |
| S_1 | Survival ratio at the earlier time t_1 | — |
| S_2 | Survival ratio at the later time t_2 | — |
| t_1 | Earlier time at which S is known | h |
| t_2 | Later time at which S is known | h |
| t_1/2 | Half-life: time for the survival ratio to halve | h |
| dS/dt | Rate of change of the survival ratio | h⁻¹ |

*Fit*: Godby's figures are S_1 = 0.74 at t_1 = 24 h and S_2 = 0.22 at t_2 = 72 h ([61]):
k = ln(0.74/0.22)/48 ≈ **0.0253 h⁻¹**, so t_1/2 = 0.693/0.0253 ≈ **27 h**. The survival ratio roughly halves every day after the first day.

- **Check against a third point (inversion)**: the model predicts S(120 h) = 0.74·e^(−0.0253×96) ≈ **0.065**. Godby's day-five figure is **0.06**. Refitting with 72 h and 120 h gives k = ln(0.22/0.06)/48 ≈ 0.0271 h⁻¹. So between day 1 and day 5, a single exponential with **k ≈ 0.025–0.027 h⁻¹** fits well.
- **Where it breaks**: extrapolating back to t = 0 gives S_0 = 0.74·e^(0.0253×24) ≈ 1.36, **which is impossible (>100%)**. The first day must behave differently, or the 24-hour figure means something else (for example, an average over the whole first day). Use the model only *between* known points, and say so in your answer.
- **Marginal value of an hour** at t = 24 h: |dS/dt| = kS = 0.0253 × 0.74 ≈ **0.019 per hour**. Each hour of delay costs about 1.9 survivors per 100 people reached.
- **Effect of the 10-hour head start** (7.1; a ratio, so S_0 cancels): S(t+10)/S(t) = e^(−0.0253×10) ≈ **0.78**. That is about **22% fewer survivors** with the slower first look, *if* the drone's earlier information leads to earlier extraction.

### 7.5 Probability of detection (search theory)
**Koopman random-search formula** ([58], [59]):

$$POD = 1 - e^{-C}, \qquad C = \frac{W \cdot L}{A} \ \ \left(= \frac{W}{S} \text{ for parallel tracks}\right)$$

Several independent searches combine as:

$$POD_{cum} = 1 - \prod_{i=1}^{n}(1 - POD_i)$$

| Symbol | Meaning | Units |
|---|---|---|
| POD | Probability of detecting the target if it is in the area | — |
| C | Coverage: the area effectively swept divided by the area searched | — |
| W | Effective sweep width: one number for how well a given sensor detects a given object in a given environment | m |
| L | Total track length flown or driven | m |
| A | Area searched | m² |
| S | Track spacing between parallel passes | m |
| POD_cum | Cumulative probability of detection after all searches | — |
| POD_i | Probability of detection on search i | — |
| n | Number of independent searches | — |

*Example*: thermal sweep width W = 20 m (illustrative) and spacing S = 39 m → C ≈ 0.51 → POD ≈ **40%**. Two independent passes → 1 − 0.6² ≈ **64%**. To reach POD = 90% you need C = ln 10 ≈ 2.30, so S = 20/2.30 ≈ **8.7 m**. That takes about 4.5 times as long as one pass at 39 m spacing.
*Assumptions and trade-off*: the formula was first derived by Koopman ([58]). Its standard assumptions are that the target is equally likely to be anywhere in the area and that the searcher's path is effectively random. Navigation errors make real searches partly random anyway, and a well-flown parallel sweep can do somewhat better, so treat the formula as a *conservative* estimate. Search time ∝ 1/S, but POD = 1 − e^(−W/S), so each extra percent of POD costs more time than the last.

---

## 8. Quantitative toolkit: economics

### 8.1 Cost per operating hour

$$c_h = \frac{C_0 - V_s}{N \cdot H} + c_{om}$$

| Symbol | Meaning | Units |
|---|---|---|
| c_h | Cost per operating hour | $/h |
| C_0 | Purchase cost, including training and certification | $ |
| V_s | Salvage (resale) value at the end of life | $ |
| N | Service life | years |
| H | Operating hours per year | h/yr |
| c_om | Operating and maintenance cost per hour (batteries, repairs, staff) | $/h |

### 8.2 Drone versus helicopter: real figures (West Midlands Police, UK)
- **Marginal rates** (March 2022 briefing note): in 2021 the force was allocated 400 h of National Police Air Service (NPAS) helicopter time for **£1.6M**. Hours beyond that were charged at **£579/h**, compared with **£48.90/h** to deploy a drone ([48]). The allocation works out to an average of about **£4,000/h** (my arithmetic: £1.6M ÷ 400 h).
- **Fully loaded costs** (July 2022 benefit-cost analysis): counting staffing, the drone unit cost **£2,823 per day**, or **£2,439 per flight hour**, over **881 flight hours** and **2,480 operations** in the period studied. The force budgets **£1,663,500 per year** for NPAS, and its NPAS operations averaged **£3,689 each** ([49]).
- **Benefits**: the report values the drone unit's benefits (costs of crime and of police time avoided) at **£15,774,783**, which is **£17,905 per flight hour** and **£6,361 per operation**, for a **benefit-cost ratio of 7.34** ([49]).
- The same analysis estimates a potential saving of **£645,720** from NPAS operations a drone could have covered. It also notes that **more than 71% of NPAS operations involve vehicle pursuits**, where the helicopter remains the best resource ([49]).
- A single police drone costs **£3,000–£30,000**. Drones may fly up to 400 ft, while NPAS helicopters fly no lower than 600 ft ([50]).

**Benefit-cost ratio and cost per operation**

$$\text{BCR} = \frac{B_{tot}}{C_{tot}}, \qquad C_{tot} = c_{fh} \cdot H_f, \qquad c_{op} = \frac{C_{tot}}{N_{op}}$$

| Symbol | Meaning | Units |
|---|---|---|
| BCR | Benefit-cost ratio. Above 1 means benefits exceed costs. | — |
| B_tot | Total monetized benefit over the period | £ |
| C_tot | Total cost over the period | £ |
| c_fh | Fully loaded cost per flight hour (equipment plus staff) | £/h |
| H_f | Flight hours in the period | h |
| c_op | Average cost per operation | £ |
| N_op | Number of operations in the period | — |

*Worked check with the report's own numbers* ([49]): C_tot = £2,439 × 881 h ≈ **£2,148,759**. BCR = 15,774,783 ÷ 2,148,759 ≈ **7.34**, which matches the report. c_op = 2,148,759 ÷ 2,480 ≈ **£866**.

**£866 or £886 per drone operation?** The report prints the per-operation drone cost **both ways**: £866 in one place and "£886 per operation" in another ([49]). Its own arithmetic settles it:
- Hourly cost × hours ÷ operations gives **£866.4** (above).
- Only £866 reproduces the report's BCR: 6,361 ÷ 866 ≈ **7.35**, while 6,361 ÷ 886 ≈ 7.18.

So **£886 is almost certainly a typo, and this guide uses £866.** If a test question quotes £886, use the question's number. Neither value changes any conclusion below, and each calculation shows both.

**Lesson: compare like with like.** Per hour, marginal drone cost (£48.90) versus marginal helicopter cost (£579) looks like a 12× saving. Per hour on a fuller basis (£2,439 fully loaded for the drone versus the £4,000 average NPAS allocation rate) the gap is much smaller. **Per operation** (£866 versus £3,689, a ratio of about **4.3**; 4.2 with £886) drones win clearly, because a drone launches on scene and flies short missions. A good exam answer states which basis it uses.

*Check (inference)*: £645,720 ÷ (£3,689 − £866) ≈ **229 operations** (230 with £886). The report's saving is about what you would get if drones took over roughly 229 helicopter operations. That is a useful sanity check, not a figure the report states.

### 8.3 Payback and net present value

$$\text{Payback (yr)} = \frac{C_0}{B_{yr} - C_{yr}}$$

$$NPV = -C_0 + \sum_{t=1}^{N} \frac{B_t - C_t}{(1+r)^t}$$

| Symbol | Meaning | Units |
|---|---|---|
| C_0 | Up-front cost (year 0) | £ or $ |
| B_yr, B_t | Annual benefit (costs avoided, value of losses prevented); B_t is the benefit in year t | £/yr |
| C_yr, C_t | Annual operating cost; C_t is the cost in year t | £/yr |
| t | Year index (1 to N) | yr |
| r | Discount rate | decimal per year |
| N | Program life | years |
| NPV | Net present value. > 0 means the program is worth doing at rate r. | £ |

*Worked example* (marginal rates from [48]; C_0 at the top of the real price range [50]; upkeep and hours illustrative): a drone program costs **C_0 = £30,000**. It replaces **100 h/yr** of premium-rate helicopter time. Savings per hour = 579 − 48.90 = £530.10, so B = **£53,010/yr**. Upkeep C = **£4,000/yr**. N = 5 years, r = 5%.
- Payback = 30,000 / 49,010 ≈ **0.61 yr** (about 7 months)
- Annuity factor = [1 − (1.05)⁻⁵]/0.05 ≈ 4.329. NPV ≈ −30,000 + 49,010 × 4.329 ≈ **+£182,000**

*Sensitivity*: if the drone hour is costed fully loaded (£2,439) against the £579 marginal helicopter rate, the "saving" per hour is **negative**. The project only pays when you compare on a consistent basis (per operation, or fully loaded on both sides). Mixing bases is the most common error in cost-benefit answers.

*What the calculation leaves out*: lives saved, responder injuries avoided, faster insurance claims and economic recovery (Harvey, [41]), and the cost of failure (MTBF, Section 5.6). A complete answer names these even if it cannot price them.

### 8.4 Economic arguments to name in an essay answer
| For robotics | Against / limits |
|---|---|
| Much lower cost per operation than crewed aircraft ([49]) | Fully loaded costs (staff, training) are far above the marginal rate ([49]) |
| Fewer responder injuries and deaths | Field MTBF of 6–20 h means spares and maintenance ([60]) |
| Faster damage assessment → faster claims and recovery ([41]) | Training and interfaces: human error causes about 50% of failures ([22]) |
| Grant-eligible through the FEMA AEL ([4], [16]) | Needs standard test data to avoid buying the wrong robot ([1], [9]) |
| A growing market: Japan spends more than $13B a year on disaster preparedness, with openings in drone logistics, CBRNE detection and AI analytics ([51]) | Slow adoption: small ground robots are still not in general practice anywhere ([25]). Skills are "very perishable" between disasters ([2]). |

---

## 9. Practice questions (answers below)

1. Name the ASTM subcommittee that develops response-robot test methods, and the two federal agencies most involved.
2. What is the difference between a *standard test method* and a *performance standard*? Why do NIST and DHS produce test methods?
3. A city wants to use grant money for a small drone and a SAR robot camera attachment. Which FEMA list governs this, and which item codes apply?
4. Which disaster is the first reported use of robots in a life-saving response? Which organization deployed them?
5. According to Murphy, what caused about half of mission-ending failures in disaster robot deployments from 2001 to 2013?
6. Calculate the peak emission wavelength of a victim's skin at 304 K. Which camera band is appropriate?
7. A tracked robot has track width 0.40 m and center-of-mass height 0.25 m. Find its sideways tip angle.
8. A 3 kg drone has the same rotors and FM as the example in 7.3. Estimate its hover power.
9. What is the FSPL at 900 MHz and 1 km?
10. Thermal search with W = 15 m. What track spacing gives POD = 80%?
11. Using k = 0.0253 h⁻¹, by what factor does survival drop if rescue starts 4 hours later?
12. A robot costs $80,000, has $10,000 salvage value, a 5-yr life, 50 h/yr use and $120/h O&M. What is its cost per hour?
13. Why did ground robots contribute little at Surfside 2021, when drones were used heavily?
14. What is the main finding of Jorge et al. (2019) about USVs in disaster management?
15. Using 22% at 72 h and 6% at 120 h, find k and the half-life. Compare with the 24–72 h fit.
16. West Midlands Police: a drone operation costs about £866 and a helicopter operation about £3,689. Why is "£48.90/h vs £579/h" a weaker basis for a budget decision?

**Answers**
1. ASTM **E54.09** Response Robots (under E54 Homeland Security Applications); **NIST** and **DHS S&T** ([3], [9], [11]).
2. A test method defines *how* to measure a capability repeatably. A performance standard sets a *pass threshold*. Test methods let each agency set its own requirements and compare robots objectively ([9]).
3. **FEMA AEL**: **03OE-07-SUAS** (small UAS) and **03SR-05-RBTL** (SAR robot attachments, restricted to specialty teams such as US&R) ([15], [16]).
4. **World Trade Center, 2001**; **CRASAR** ([18]).
5. **Human error**, i.e., poor human–robot interaction ([22], [23]).
6. λ = 2.898×10⁻³/304 ≈ **9.53 µm**, in the **LWIR (about 7–14 µm)** band ([54]).
7. tan θ = 0.20/0.25 = 0.8 → θ ≈ **38.7°**.
8. P scales as m^1.5: 218 W × (3/2)^1.5 ≈ 218 × 1.837 ≈ **400 W**.
9. 20log(1) + 20log(900) + 32.44 = 0 + 59.08 + 32.44 ≈ **91.5 dB**. Extension: with P_T = 20 dBm and two 2 dBi antennas, the decibel-form Friis equation gives P_R = 20 + 2 + 2 − 91.5 ≈ **−67.5 dBm**, about 2.5 dB stronger than the 2.4 GHz, 500 m example. Lower frequency more than makes up for twice the distance.
10. C = −ln(0.2) ≈ 1.609 → S = 15/1.609 ≈ **9.3 m**.
11. e^(−0.0253×4) ≈ **0.904**, about a 10% relative drop.
12. (80,000 − 10,000)/(5 × 50) + 120 = 280 + 120 = **$400/h**.
13. Humans and dogs could already search the debris surface. The need was to get *into* the rubble, and no robot could do that. UGVs are not designed to search rubble interiors, and voids could not be predicted ([27], [30]).
14. **Few real deployments.** Research focuses on technology (guidance, navigation and control) more than disaster operations ([7]).
15. k = ln(0.22/0.06)/48 = ln(3.667)/48 ≈ **0.0271 h⁻¹**; t_1/2 = 0.693/0.0271 ≈ **25.6 h**. Close to the 24–72 h fit (0.0253 h⁻¹, 27.4 h), so one exponential describes days 1–5 well.
16. The hourly rates are *marginal* (they leave out staff and overhead), and helicopter and drone missions differ in length. Fully loaded, the drone hour costs £2,439. The per-operation comparison captures both the full cost and the shorter drone missions, and still favors drones about 4 to 1 (3,689 ÷ 866 ≈ 4.3, or 4.2 with the report's other printed value, £886). Note also that >71% of helicopter operations are vehicle pursuits that drones can't easily replace ([48], [49]).

---

## 10. Watch-outs: claims to handle carefully

- **"Japan plans to spend over $100 million by 2030 on disaster robotics"** (section sheet). **I could not verify this as stated.** The closest verified figure: Japan's Cabinet Office allocated **$100 million for FY2025 to strengthen the new Disaster Prevention Agency**, double the previous year, with full operation planned for FY2026. That money is for the agency as a whole, not robotics alone ([51]). Japan's national disaster-robotics R&D program was the Cabinet Office's **ImPACT Tough Robotics Challenge** ([52]). On the test, accept the sheet's number as given and don't add details to it.
- **Counts that change over time**:
  - ASTM test methods: 15 published + 14 in development (DHS fact sheet) → about 30 (DHS, 2018) → more than 50 (NIST today) ([3], [9], [13])
  - Murphy's deployment count: "over 46 disasters" ([22])
  - Harvey drones: 43 FAA-authorized organizations, 355 emergency airspace authorizations across all 2017 hurricanes ([41], [43])
  - Surfside: 304 strategic drone missions, more than Harvey (112) and Florence (260) on the same measure ([28])
  
  Answer with the source and date if you can.
- **Drone cost per operation, £866 or £886**: the West Midlands report prints both. Its own numbers (£2,439/h × 881 h ÷ 2,480 operations, and its benefit-cost ratio of 7.34) give £866, so £886 looks like a typo. If a question gives either number, use the question's number ([49]).
- **Survival percentages** are one expert's averages, quoted in news reports ([61]). Treat the 24-hour and 72-hour windows as rules of thumb.
- **FEMA US&R team size**: 70 members per task force, which can split into two 35-person teams ([17]).
- **"Map a building in seconds"**: capturing images is fast, but processing and moving the data take minutes to hours ([22], [28]).
- **"Thermal drones find victims"**: they see warm *surfaces*. At Surfside the victims were inside the rubble ([27]).

---

## 11. Citation page

**How consulted**: every page below was consulted through a web-search tool that returned the page's title, URL and indexed text. Direct page loading was blocked by the research environment's network filter (Section 0). Each page was cited only after a search returned that exact page. **†** = the tool returned only the title, URL and a short snippet. These pages are used only for the narrow fact in the snippet, and you should open them yourselves.

**A. Sources you gave and the "Explore More" titles (all 7 titles covered)**

| # | Explore More title | Covered by |
|---|---|---|
| 1 | NIST: Response Robots | [1] |
| 2 | NIST: Performance of Emergency Response Robots | [2] (exact-title NIST page) |
| 3 | DHS: Standards Office – Robot Response Standards Program Fact Sheet | [3] |
| 4 | FEMA: Authorized Equipment List | [4], with item pages [15], [16] |
| 5 | NSF: Robots to the Rescue | [5] |
| 6 | The Center for Robot-Assisted Search and Rescue | [6], with CRASAR pages [18], [19], [26] |
| 7 | NIH: A Survey on Unmanned Surface Vehicles for Disaster Robotics | [7] |

1. National Institute of Standards and Technology. "Response Robots." https://www.nist.gov/response-robots
2. NIST. "Performance of Emergency Response Robots" (project page). https://www.nist.gov/programs-projects/emergency-response-robots
3. U.S. Department of Homeland Security, Science & Technology Directorate. "S&T Robot Response Standards Program Fact Sheet." https://www.dhs.gov/publication/st-robot-response-standards-program-fact-sheet (attached PDF: "Standards Office – Robot Response Standards Program," https://www.dhs.gov/sites/default/files/publications/Standards%20Office%20-%20Robot%20Response%20Standards%20Program-508_2.pdf)
4. FEMA. "Authorized Equipment List." https://www.fema.gov/grants/tools/authorized-equipment-list
5. U.S. National Science Foundation. "Robots to the Rescue" (NSF Stories). https://www.nsf.gov/news/robots-rescue
6. Center for Robot-Assisted Search and Rescue (CRASAR). Home page. http://crasar.org/ †
7. Jorge, V. A. M., et al. (2019). "A Survey on Unmanned Surface Vehicles for Disaster Robotics: Main Challenges and Directions." *Sensors* 19(3):702. doi:10.3390/s19030702. https://pmc.ncbi.nlm.nih.gov/articles/PMC6387351/ (abstract and metadata consulted)

**B. Standards, testing and buying**

8. NIST. "Department of Homeland Security Response Robot Performance Standards." https://www.nist.gov/programs-projects/department-homeland-security-response-robot-performance-standards
9. NIST Intelligent Systems Division. "Standard Test Methods for Response Robots" (with its ground, aerial and aquatic test pages). https://www.nist.gov/el/intelligent-systems-division-73500/standard-test-methods-response-robots
10. NIST News (Dec 2018). "NIST Performance Tests for Aerial Response Robots Become National Standard." https://www.nist.gov/news-events/news/2018/12/nist-performance-tests-aerial-response-robots-become-national-standard
11. ASTM International. "Subcommittee E54.09 on Response Robots." https://www.astm.org/get-involved/technical-committees/committee-e54/subcommittee-e54/jurisdiction-e5409
12. ASTM International. "E2854 Standard Test Method for Evaluating Emergency Response Robot Capabilities: Radio Communication: Line-of-Sight Range." https://www.astm.org/Standards/E2854.htm †
13. DHS S&T (Aug 7, 2018). "Snapshot: S&T Test Methods Used to Evaluate Rescue Robots." https://www.dhs.gov/science-and-technology/news/2018/08/07/snapshot-st-test-methods-used-evaluate-rescue-robots
14. AFCEA *Signal*. "DHS, NIST Standards for Rescue Robots Gain Momentum." https://www.afcea.org/signal-media/dhs-nist-standards-rescue-robots-gain-momentum
15. FEMA. "03OE-07-UPGD" (AEL item: upgrades to robots and remotely operated platforms). https://www.fema.gov/grants/tools/authorized-equipment-list/03oe-07-upgd
16. FEMA. "03SR-05-RBTL" (AEL item: attachments and tools for search & rescue robots). https://www.fema.gov/grants/tools/authorized-equipment-list/03sr-05-rbtl
17. FEMA. "Urban Search & Rescue." https://www.fema.gov/emergency-managers/national-preparedness/frameworks/urban-search-rescue

**C. CRASAR, Robin Murphy and NSF**

18. CRASAR. "About Us." http://crasar.org/about-us/
19. CRASAR. "Emergency Managers Find Small Unmanned Aerial Systems Effective for Flooding and Popular with Residents" (Oct 2016). http://crasar.org/emergency-managers-find-small-unmanned-aerial-systems-effective-for-flooding-and-popular-with-residents/
20. U.S. National Science Foundation (NSF Stories). "Shoebox-sized Robots Deployed in Rescue Effort at Ground Zero." https://www.nsf.gov/news/shoebox-sized-robots-deployed-rescue-effort-ground
21. Schneider, D. IEEE Spectrum. "Robin Murphy: Roboticist to the Rescue." https://spectrum.ieee.org/robin-murphy-roboticist-to-the-rescue
22. ACM TechTalks. "Disasters: Robots, Computing, and Informatics with Robin Murphy." https://learning.acm.org/techtalks/disasters
23. UC Irvine Institute for Software Research. "ISR Distinguished Speaker" (abstract of a 2015 talk by Robin Murphy). https://isr.uci.edu/node/2114.html
24. Texas A&M University, Robin R. Murphy. "Research" (Survivor Buddy). https://people.engr.tamu.edu/robin.r.murphy/research.html
25. Murphy, R. R., et al. "Adoption of Robots for Disasters," *Foundations and Trends in Robotics* (NSF Public Access Repository copy). https://par.nsf.gov/servlets/purl/10327703
26. CRASAR. "Category: In the News" (Hurricane Wilma, 2005, earliest known use of unmanned marine vehicles). http://crasar.org/category/in-the-news/ †

**D. Case studies and technology**

27. IEEE Spectrum. "Why Robots Can't Be Counted On to Find Survivors in the Florida Building Collapse." https://spectrum.ieee.org/why-robots-cant-help-find-survivors-in-the-florida-building-collapse
28. Murphy, R. R., et al. IEEE Spectrum. "How Robots Helped Out After the Surfside Condo Collapse." https://spectrum.ieee.org/building-collapse-surfside-robots
29. Texas A&M Today (June 30, 2021). "Texas A&M rescue robotics expert explains technologies used in Florida condo collapse." https://stories.tamu.edu/news/2021/06/30/texas-am-rescue-robotics-expert-explains-technologies-used-in-florida-condo-collapse
30. "Analysis of Interior Rubble Void Spaces at Champlain Towers South Collapse" (arXiv 2301.04743). https://arxiv.org/pdf/2301.04743
31. DARPA. "Team CERBERUS and Team Dynamo Win DARPA Subterranean Challenge Final Event" (2021). https://www.darpa.mil/news/2021/subterranean-challenge-winners
32. Carnegie Mellon University News (Sept 2021). "Team Explorer Places Fourth in DARPA SubT Challenge." https://www.cmu.edu/news/stories/archives/2021/september/darpa-subt-finals.html
33. IEEE Spectrum. "Inside DARPA's Subterranean Challenge." https://spectrum.ieee.org/darpa-subterranean-challenge-2657170650
34. IEEE Spectrum. "DARPA Robotics Challenge: Here Are the Official Details." https://spectrum.ieee.org/darpa-robotics-challenge-here-are-the-official-details
35. Wikipedia. "DARPA Robotics Challenge." https://en.wikipedia.org/wiki/DARPA_Robotics_Challenge
36. Arahata, T. (TEPCO), "Deployment of Robotics to Stabilize the Accident at Fukushima Daiichi NPS," NIST International Workshop on the Use of Robotic Technologies at Nuclear Facilities, Feb 2016. https://www.nist.gov/document/session2presentation1arahatadeployment-robotics-stabilize-accident-fukushima-daiichi-nps (Session 2 page with the companion TEPCO talk on robot operations: https://www.nist.gov/el/intelligent-systems-division-73500/international-workshop-use-robotic-technologies-nuclear-2)
37. NIST. "At New NIST Facility, Response Robots Must Measure Up" (feature story; Quince and Tadokoro quote). https://www.nist.gov/feature-stories/new-nist-facility-response-robots-must-measure †
38. Deccan Herald. Report on Japan's radiation-proof robot (Chiba Tech crawler abandoned in the Unit 2 building in October 2011). https://www.deccanherald.com/world/japans-n-proof-robot-gets-2373948 †
39. IEEE Spectrum. "Boston Dynamics' Spot Explores Chernobyl." https://spectrum.ieee.org/boston-dynamics-spot-chernobyl
40. GOV.UK. "Robot proves itself in Dounreay radioactive area." https://www.gov.uk/government/news/robot-proves-itself-in-dounreay-radioactive-area
41. NPR. "Drones Descend On Houston To Help Assess Damage From Harvey" (transcript, 2017). https://www.npr.org/transcripts/548715211
42. Center for the Study of the Drone at Bard College. "Weekly Roundup 9/4/17." https://dronecenter.bard.edu/weekly-roundup-9417
43. U.S. Department of Transportation. Testimony, "Keeping Pace with Innovation – Update on the Safe Integration of Unmanned Aircraft Systems into the Airspace." https://www.transportation.gov/testimony/keeping-pace-innovation-%E2%80%93-update-safe-integration-unmanned-aircraft-systems-airspace
44. Surmann, H., Berninger, N., & Worst, R. "3D mapping for multi hybrid robot cooperation" (IROS 2017; arXiv 1904.04362). https://arxiv.org/abs/1904.04362
45. "Air-Ground Collaborative Robots for Fire and Rescue Missions: Towards Mapping and Navigation Perspective" (arXiv 2412.20699). https://arxiv.org/pdf/2412.20699
46. Texas A&M University, Robin R. Murphy. "EMILY." https://people.engr.tamu.edu/robin.r.murphy/EMILY.html
47. Texas A&M Engineering Experiment Station (Sept 2016). "CRASAR conducts marine mass casualty exercise with Italian Coast Guard." https://tees.tamu.edu/news/2016/09/crasar-conducts-marine-mass-casualty-exercise-with-italian-coast-guard.html

**E. Economics and Japan**

48. West Midlands Police Data Analytics Lab (Mar 2022). "WMP Briefing Paper: Drone Unit Analysis" (West Midlands PCC, Agenda Item 4.1a). https://www.westmidlands-pcc.gov.uk/wp-content/uploads/2022/06/2022-03-02-EC-Agenda-Item-4.1a-Briefing-Note_Drones-v1.pdf
49. West Midlands Police Data Analytics Lab (July 2022). "WMP Drone Unit Benefit-Cost Analysis" (Agenda Item 3.1). https://www.westmidlands-pcc.gov.uk/wp-content/uploads/2022/09/2022-07-06-EC-Agenda-Item-3.1-WMP-Drone-Unit-Benefit-Cost-Analysis.pdf (prints the per-operation drone cost as both £866 and £886; Section 8.2 shows why £866 is the consistent value)
50. West Midlands Police & Crime Commissioner. "West Midlands Police flying high as PCC praises 'vital' Drone Unit." https://www.westmidlands-pcc.gov.uk/west-midlands-police-flying-high-as-pcc-praises-vital-drone-unit/
51. U.S. International Trade Administration. "Japan Disaster Risk Reduction" (Market Intelligence). https://www.trade.gov/market-intelligence/japan-disaster-risk-reduction
52. Springer. *Disaster Robotics: Results from the ImPACT Tough Robotics Challenge* (book page). https://link.springer.com/978-3-030-05320-8 †

**F. Science and mathematics**

53. Wikipedia. "Wien's displacement law." https://en.wikipedia.org/wiki/Wien%27s_displacement_law
54. Wikipedia. "Thermography." https://en.wikipedia.org/wiki/Thermography
55. Wikipedia. "Microbolometer." https://en.wikipedia.org/wiki/Microbolometer
56. LibreTexts Engineering (Ellingson, *Electromagnetics II*). "10.14: Friis Transmission Equation." https://eng.libretexts.org/Bookshelves/Electrical_Engineering/Electro-Optics/Book%3A_Electromagnetics_II_(Ellingson)/10%3A_Antennas/10.14%3A_Friis_Transmission_Equation †
57. Wikipedia. "Free-space path loss." https://en.wikipedia.org/wiki/Free-space_path_loss
58. Defense Technical Information Center. "An Introduction to Search Theory" (AD0777878). https://apps.dtic.mil/sti/tr/pdf/AD0777878.pdf
59. Defense Technical Information Center. "Compatibility of Land SAR Procedures with Search Theory" (ADA511658). https://apps.dtic.mil/sti/tr/pdf/ADA511658.pdf
60. Defense Technical Information Center. Report ADA556503 (2010 draft on UGV reliability, citing Carlson & Murphy's 6–20 h MTBF). https://apps.dtic.mil/sti/pdfs/ADA556503.pdf †
61. Gulf News. "Why first 72 hours are crucial for Turkey-Syria quake rescues" (2023). https://gulfnews.com/world/mena/why-first-72-hours-are-crucial-for-turkey-syria-quake-rescues-1.1675864021699
62. Gulf News. "How long can quake victims survive trapped under rubble? It depends..." https://gulfnews.com/world/europe/how-long-can-quake-victims-survive-trapped-under-rubble-it-depends-1.1886291
63. Wikipedia. "Crush syndrome." https://en.wikipedia.org/wiki/Crush_syndrome
64. "Crush injury and rhabdomyolysis." *Critical Care Clinics* (2004), PubMed abstract. https://pubmed.ncbi.nlm.nih.gov/14979336/
65. CDC Stacks. Crush syndrome record. https://stacks.cdc.gov/view/cdc/11904

**Total: 65 numbered sites, well above the 15 required.** They include all 5 URLs you gave and all 7 "Explore More" titles.
