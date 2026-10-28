# Smart Energy Grids: Study Guide
**TSA TEAMS 2027, "Engineering a Smarter World"**

This guide follows the official section sheet. Part 1 maps each item on the sheet to the place in this guide that covers it. Parts 2 and 3 give the concepts. Part 4 is the equation toolkit, with every variable defined. Part 5 has worked problems that match the four calculations the sheet says your team will do. Parts 6 to 9 are for review. Part 10 is the citation page (57 sites). Bracketed numbers such as [8] point to that page.

## Assumptions

1. **"At least 15 sites"** is read as 15 distinct web pages or documents. This guide cites 57, including all seven URLs you gave and the sources behind all seven "Explore More" titles.
2. **Source 1 (PMC6387351)** is a 2019 survey of unmanned *surface* vehicles (robot boats) for disaster response [1]. It is not the DOE "Smart Grid" page, so it is cited and used only in §3.5 (resilience and robots), where it is genuinely relevant. For the sheet's title "U.S. Department of Energy: Smart Grid", this guide uses DOE's Office of Electricity page *Grid Modernization and the Smart Grid* [8] and DOE's SmartGrid.gov page *The Smart Grid* [9]. FERC's own *Smart Grid* page [4] lists a "Department of Energy – Smart Grid" link among its quick links, which supports reading the sheet's first title as a DOE smart-grid page rather than the robotics survey.
3. **How the sources were read.** In our research environment, pages could not be loaded directly (every direct fetch failed with a DNS error). Every source was therefore read through web-search results: the search engine's indexed text and excerpts of each URL. Sources [1] to [53] were checked on 27 Oct 2026. On 28 Oct 2026 the supplied pages [2], [4] and [5] were re-read by searching for those exact URLs, so that each contributes facts from its own text; [12] was re-checked, and [54] to [57] were read. Every URL in Part 10 was returned live by that index on the date it was checked. Open the important ones yourself before the competition.
4. **Numbers in the worked problems** marked *(assumed)* are illustrative inputs chosen to be realistic. Numbers with a bracketed citation come from that source. The figures in the sheet's own overview (for example "$2 million per mile") are quoted from the sheet and were not independently re-derived.
5. Units follow U.S. grid practice: 1 kW = 10³ W, 1 MW = 10⁶ W, 1 GW = 10⁹ W, and 1 TWh = 10⁹ kWh.

---

## Part 1. What the sheet asks, and where it is covered

| Item on the section sheet | Where it is covered |
|---|---|
| Peak demand, load balancing | §2.3, §4.5, Problem 1 |
| Transmission loss | §2.1, §4.2, Problem 2 |
| Grid stability (the California example) | §2.4 (duck curve), §4.9 (inertia) |
| Upgrade cost (sheet: over $2 million per mile) and investment through 2030 | §3.3 |
| Data centers using as much energy as cities | §4.10, Problem 6 |
| "Automatically reroute power during a blackout" | §3.2 (automated feeder switching, FLISR) |
| "Monitor and balance … thousands of rooftop solar panels" | §3.2 (smart meters, DER aggregation, microgrids) |
| Smart meters, clean energy, policy, consumer behavior | §3.1 to §3.4 |
| **Task: peak load requirements** | §4.5, Problem 1 |
| **Task: storage capacity for intermittent renewables** | §4.6, §4.7, Problem 3 |
| **Task: efficiency of microgrid distribution** | §4.8, Problem 4 |
| **Task: demand increase from EVs and data centers** | §4.10 to §4.12, Problems 5 and 6 |

---

## Part 2. How the U.S. grid is built

### 2.1 Generation, transmission, distribution
- The grid is a network of transmission lines, substations, transformers and related equipment that carries power from power plants to homes and businesses [9].
- **Why high-voltage AC.** For a given power P = IV, raising the voltage lowers the current. Resistive heating in the wires grows with the square of the current, so high-voltage transmission cuts losses. Generator output is stepped up by transformers (OpenStax gives figures as high as 500 kV) and stepped down near customers [44]. Transformers work only with changing (AC) voltage, which is a main reason the grid is AC [45].
- **How big the losses are:** EIA estimates that transmission and distribution (T&D) losses averaged about **5%** of the electricity transmitted and distributed in the U.S. in 2018 to 2022 [30].

### 2.2 The map: interconnections, balancing authorities, markets, regions
- **Three interconnections** [7]:
  - **Eastern Interconnection:** states east of the Rocky Mountains.
  - **Western Interconnection:** from the Pacific Ocean to the Rocky Mountain states.
  - **Texas Interconnected system (ERCOT):** most of Texas.

  These three operate mostly independently, with limited power exchange between them [19].
- **Balancing authorities (BAs)** run the grid so that supply constantly matches demand [19].
  - EIA counted 36 BAs in the Eastern Interconnection (31 U.S., 5 Canada) and 37 in the Western (34 U.S., 2 Canada, 1 Mexico) [31].
  - ERCOT is a **single** BA [31].
- **Wholesale markets.** Competitive wholesale markets in the Northeast, Midwest, Texas and California are run by independent system operators (ISOs) and regional transmission organizations (RTOs) [19].
- **Reliability.** NERC, a nonprofit regulatory body, oversees six regional reliability entities. Its footprint covers the interconnected power systems of Canada, the contiguous U.S. and part of Mexico [7].
- **"Region" has several definitions.** EPA's *U.S. Grid Regions* page explains that a grid region can mean an eGRID subregion, a NERC region, ERCOT and so on, and that the right choice depends on the purpose [7]. EPA's eGRID database supplies emissions data for U.S. grid regions, states and Puerto Rico [7].

### 2.3 Load balancing and peak demand
- Demand changes every minute, so supply must follow it. The **peak** is the highest demand in a period, and it sets how much generation and wire capacity must exist.
- Planners compare available resources with forecast peak demand using the **reserve margin** (§4.5) [43].
- Demand response (customers cutting or shifting use at peak) lowers the "net" peak that resources must cover. NERC subtracts dispatchable demand response from total demand to get "net internal demand" [43].

### 2.4 Grid stability and the California "duck curve"
- As California added solar, the **net load** (demand minus wind and solar output) developed a deeper midday dip and a steeper evening rise as the sun sets. The shape looks like a duck. CAISO, California's grid operator, anticipated it back in 2013 [35].
- **Why it matters for this section:**
  - The evening ramp has to be met by fast, dispatchable resources or by **storage charged with midday solar**. Problem 3 sizes this.
  - Grid frequency (60 Hz in the U.S.) is held steady partly by the **inertia** of spinning generators (§4.9) [52].

### 2.5 Who does what
- **FERC (Federal Energy Regulatory Commission).** FERC's *Smart Grid* page says the Commission focuses on smart-grid issues to support modernizing the electric system, consistent with EISA Title XIII [4]. It traces that interest to three responsibilities [4]:
  1. Its authority over the rates, terms and conditions of transmission and wholesale sales of electricity in interstate commerce.
  2. Approving and enforcing reliability standards for the bulk power system.
  3. EISA's direction to adopt smart-grid interoperability standards once FERC is satisfied that NIST's work has reached "sufficient consensus" (§3.1).

  A GAO review notes that FERC's authority is generally limited to the transmission system, while much smart-grid equipment sits on distribution systems, which states regulate [22].
- **DOE** runs research and funding through **17 national laboratories**. DOE's *National Laboratories* page describes them as institutions that have led U.S. scientific innovation for more than 70 years, and it profiles individual labs; its Argonne entry places Argonne in Lemont, Illinois, as the largest national laboratory in the Midwest [2]. The Office of Science stewards 10 of the 17, and NNSA stewards Lawrence Livermore, Los Alamos and Sandia [10][11].
  - On 1 Dec 2025, DOE renamed the National Renewable Energy Laboratory (NREL) the **National Laboratory of the Rockies (NLR)** [12]. Older documents use "NREL".
  - **Argonne National Laboratory** works on grid resilience, reliability and adaptability. It uses advanced modeling, data analytics and AI to improve grid performance, integrate new energy sources and handle rising demand from data-intensive operations [6].
- **EPA** publishes grid-region emissions data (eGRID) [7].
- **NERC** assesses bulk-power reliability and publishes 10-year demand forecasts [42].

---

## Part 3. What makes a grid "smart"

### 3.1 Definitions
- **DOE Office of Electricity [8]:**
  - Electric infrastructure is aging and is being pushed to do more than it was designed to do.
  - Modernizing it makes the grid smarter and more resilient. That reduces how often outages happen and how long they last, lessens storm damage and speeds restoration.
  - It also gives consumers easier access to their own data so they can manage their energy use and costs.
- **SmartGrid.gov (DOE) [9]:**
  - The defining feature is the technology, equipment and controls that allow **two-way communication** between utilities and customers, plus sensing along transmission lines.
  - The smart grid "will allow for automatic rerouting when equipment fails or outages occur". This answers the sheet's "Consider the following" question.
- **The law, EISA 2007, Title XIII, §1301 [20].** Congress listed ten characteristics that together define a Smart Grid (paraphrased):
  1. More digital information and controls, for reliability, security and efficiency.
  2. Dynamic optimization of grid operations and resources, with full cybersecurity.
  3. Deployment and integration of distributed resources and generation, including renewables.
  4. Demand response, demand-side resources and energy efficiency.
  5. "Smart" technologies (real-time, automated, interactive) for metering, grid communications and distribution automation.
  6. Integration of smart appliances and consumer devices.
  7. Advanced storage and peak-shaving technologies, including plug-in electric vehicles and thermal-storage air conditioning.
  8. Timely information and control options for consumers.
  9. Standards for communication and interoperability.
  10. Lowering unreasonable or unnecessary barriers to smart-grid adoption.
- **Interoperability (EISA §1305) [20][4]:**
  - EISA gives NIST "primary responsibility to coordinate the development of a framework that includes protocols and model standards for information management to achieve interoperability of smart grid devices and systems."
  - FERC may adopt standards by rulemaking once that process reaches "sufficient consensus".
  - In 2011, FERC found insufficient consensus on the first five families of NIST-identified standards and ended that rulemaking (Docket RM11-2) [53].

### 3.2 The technologies

| Technology | What it does | Key fact |
|---|---|---|
| **Advanced metering infrastructure (AMI) / smart meters** | An integrated system of smart meters, communications networks and data management systems that provides a two-way digital link between utilities and customers [26]. It is used for grid management, outage notification and billing [25]. | About **119 million** AMI meters in 2022, about **72%** of all U.S. electric meters; about 88% of AMI meters are residential [32]. Smart meters show customers how much electricity they use, when, and what it costs [9]. |
| **Phasor measurement units (PMUs)** | Monitor grid stability [8]. | A wide-area, time-synchronized view of grid conditions. |
| **Automated feeder switches / FLISR** (fault location, isolation and service restoration) | Find a fault, isolate the damaged section and reroute power around it [8]. | In DOE's Smart Grid Investment Grant program, 266 FLISR operations (Apr 2013 to Mar 2014, five utilities) meant about **270,000 fewer customers interrupted** and about **38 million fewer customer-minutes** of outage. Customers interrupted fell by up to 45% per event and customer-minutes by up to 51%. Fully automated switching cut customers interrupted by about 55%, compared with about 35% for manually validated switching [27]. |
| **Substation relays** | Sense faults and help the system recover from them [8]. | |
| **Batteries** | Store excess energy for later use [8]. | U.S. utility-scale batteries returned about **82%** of the energy they stored in 2019 (pumped hydro: 79%) [33]. |
| **Distributed energy resources (DERs) and aggregation** | Small generation or storage, such as rooftop solar, batteries, smart thermostats and EV chargers. FERC **Order No. 2222** (17 Sep 2020) lets aggregations of DERs compete in RTO/ISO capacity, energy and ancillary-service markets [23]. | FERC describes DERs as typically 1 kW to 10,000 kW [23]. This is how "thousands of rooftop solar panels" can be monitored and balanced. |
| **Microgrids** | "A group of interconnected loads and distributed energy resources within clearly defined electrical boundaries that acts as a single controllable entity with respect to the grid." A microgrid can connect to and disconnect from the grid, so it can run grid-connected or in **island mode** [28]. | The ability to island is what makes it a microgrid rather than just a cluster of DERs. |
| **Demand response** | Customers reduce or shift use at peak times. EISA §1301 lists it as a smart-grid characteristic [20]. | It lowers net internal demand in NERC's reserve-margin formula [43]. |
| **AI and automation** | Argonne builds machine-learning optimization models that simulate the electric system and gauge how severe different problems are [14]. Its tools described on its grid pages include HEADOUT, which estimates hurricane impacts on the electric sector [6]. Argonne's **Smart Energy Plaza** tests EV chargers, solar PV, storage and controls together [13]. | This ties to the 2027 theme of AI and automation. |

### 3.3 Policy, money and timeline
- **2005: Energy Policy Act.** Gives FERC authority to oversee the reliability of the bulk power system, including authority to approve mandatory cybersecurity reliability standards [55].
- **2007: EISA, Title XIII (Smart Grid).** Defines smart-grid characteristics (§1301) and assigns NIST and FERC their interoperability roles (§1305) [20].
- **18 Jan 2008: FERC Order No. 706.** Approves NERC's eight Critical Infrastructure Protection (CIP) cybersecurity standards, CIP-002-1 to CIP-009-1, as mandatory and enforceable [56].
- **16 Jul 2009: FERC Smart Grid Policy Statement.** FERC's guidance on priorities for smart-grid standards and interoperability [21][4].
- **2010: DOE Office of the General Counsel Requests for Information** on smart-grid **data access and privacy** and on **communications requirements** [3][24][25] (see §3.4).
- **2011: FERC's interoperability rulemaking ends.** FERC finds insufficient consensus on the first five standard families [53].
- **17 Sep 2020: FERC Order No. 2222.** DER aggregations can take part in wholesale markets [23].
- **2021 onward: Bipartisan Infrastructure Law, Grid Resilience and Innovation Partnerships (GRIP).**
  - $10.5 billion in total, split across three programs: Grid Resilience Utility and Industry Grants, Smart Grid Grants and the Grid Innovation Program, which is the largest at $5 billion [29].
  - DOE reports $7.6 billion selected for 105 projects in all 50 states and D.C. across the first two rounds [29].
  - This is part of the "billions" of investment the sheet mentions.
- **Cost of new lines.** The sheet quotes "over $2 million per mile" for traditional transmission upgrades. Actual cost depends heavily on voltage, terrain and right-of-way. Use the sheet's number when the test gives it.

### 3.4 Data, privacy and cybersecurity
- **The 2010 DOE questions [24]:**
  - Who owns energy-consumption data?
  - Who is entitled to privacy protection?
  - Which privacy practices should apply?
  - Should consumers be able to opt in or opt out?
- **What commenters said [24]:** They disagreed. Individual, personally identifiable data was generally seen as the consumer's, and aggregate data as the utility's.
- **EISA requires "full cyber-security"** alongside grid optimization [20]. GAO warned that a smart grid deployed without strong security could make the grid more vulnerable to attack [22].
- **Mandatory cyber standards.** The Energy Policy Act of 2005 gave FERC authority over bulk-power-system reliability, including mandatory cybersecurity reliability standards. NERC, which FERC certified as the Electric Reliability Organization, wrote the Critical Infrastructure Protection (CIP) standards, and FERC approved them in Order No. 706 (2008) [55][56]. By contrast, FERC's 2009 policy statement noted that EISA does not make smart-grid *interoperability* standards mandatory [21], and in 2011 FERC ended its rulemaking on them (§3.1) [53].

### 3.5 Resilience, automation and robots (source 1)
- **What the survey covers.** Jorge et al. (2019) survey robot boats (unmanned surface vehicles, USVs) for disaster management [1].
  - Disasters such as floods and hurricanes damage **utility infrastructure, including electricity**, as well as water, communications, roads and bridges.
  - USVs have been used after hurricanes to inspect seawalls, bridges and piers above and below the waterline.
- **What it does not cover.** The survey reports few real disaster deployments so far. It is **not** about power-grid operation.
- **Fair use in this section:** robotic inspection is one example of the "automation" theme in post-disaster *grid resilience*. Use it for that and nothing more.

---

## Part 4. Equation toolkit (every variable defined)

### 4.1 Power and energy
```
P = V I            E = ∫ P(t) dt   (from t₁ to t₂)
```
- **P**: power (W)
- **V**: voltage (V)
- **I**: current (A)
- **E**: energy (J, or kWh; 1 kWh = 3.6 × 10⁶ J)
- **P(t)**: power as a function of time
- **t₁, t₂**: start and end of the interval
- If P is constant, E = P·Δt, where **Δt** = t₂ − t₁ is the elapsed time.

### 4.2 Resistance and line losses
```
R = ρ L / A
P_loss = I² R
```
- **R**: resistance of the line's conductors (Ω); for a two-wire single-phase line, count both wires
- **ρ**: resistivity of the conductor material (Ω·m)
- **L**: conductor length (m)
- **A**: cross-sectional area (m²)
- **P_loss**: power turned into heat in the line (W)
- **I**: line current (A)

R = ρL/A is the standard resistivity relation from AP Physics C. The point that losses grow as I², so utilities transmit at high voltage, is from OpenStax [44][45].

**Why voltage matters (derivation).**
- Single-phase line: the current is I = P/(V·pf), where **pf** is the power factor (§4.4).
- Substituting gives:
```
P_loss = P² R / (V² pf²)        loss fraction = P_loss / P = P R / (V² pf²)
```
- For a fixed delivered power P, losses scale as **1/V²**. Doubling the voltage cuts losses to one quarter.
- For a balanced three-phase line (§4.4), P_loss = 3 I² R_ph with I = P/(√3 V_LL pf). The result has exactly the same form: P_loss = P² R_ph /(V_LL² pf²).
  - **R_ph**: resistance of one phase conductor (Ω)
  - **V_LL**: line-to-line voltage (V)

### 4.3 Transformers (ideal) [44]
```
V_s / V_p = N_s / N_p = I_p / I_s
```
- **V_p, V_s**: primary and secondary voltages
- **N_p, N_s**: number of turns on the primary and secondary coils
- **I_p, I_s**: primary and secondary currents

A step-up transformer (N_s > N_p) raises voltage and lowers current. A real transformer has efficiency **η = P_out / P_in** < 1, where **P_out** is the output power and **P_in** the input power.

### 4.4 AC power, power factor, three-phase [49][50]
```
S² = P² + Q²        pf = P / S
P_3φ = √3 V_LL I_L pf
```
- **S**: apparent power (kVA)
- **P**: real (working) power (kW)
- **Q**: reactive power (kVAR). It circulates to sustain magnetic fields and does no net work [49].
- **pf**: power factor (dimensionless, 0 to 1)
- **P_3φ**: real power of a balanced three-phase load (W)
- **V_LL**: line-to-line RMS voltage (V)
- **I_L**: RMS line current (A)

DOE's motor sourcebook computes kW = V × I × pf × 1.732 / 1000, where 1.732 ≈ √3 [50].

### 4.5 Demand and capacity metrics
```
Load factor        LF = P_avg / P_peak                                        [36]
Capacity factor    CF = E_actual / (P_rated × T)                              [37]
Reserve margin     RM = (Resources − Net internal demand) / Net internal demand   [43]
Average power      P_avg = (1/T) ∫ P(t) dt   (over the period of length T)
```
- **P_avg**: average load over the period
- **P_peak**: highest load in the same period
- **E_actual**: energy actually generated (net generation)
- **P_rated**: available (nameplate) capacity
- **T**: hours in the period (8,760 h in a non-leap year)
- **Resources**: anticipated generating resources, MW [43]
- **Net internal demand**: forecast peak demand minus dispatchable demand response, MW [43]

To find a peak with calculus, solve **dP/dt = 0** and check **d²P/dt² < 0**.

### 4.6 Renewable output
```
Wind:   P_w = ½ ρ_air A_r v³ C_p           C_p ≤ 16/27 ≈ 0.593 (Betz limit)   [51]
Solar:  P_pv = G A_pv η_pv
```
- **P_w**: electrical power captured from wind (W)
- **ρ_air**: air density (kg/m³; about 1.225 at sea level, *assumed* standard value)
- **A_r**: rotor swept area, π r² (m²), where **r** is the blade length (rotor radius)
- **v**: wind speed (m/s)
- **C_p**: power coefficient, the fraction of the wind's power captured
- **P_pv**: PV electrical output (W)
- **G**: solar irradiance on the panel (W/m²)
- **A_pv**: panel area (m²)
- **η_pv**: panel conversion efficiency

Because power goes as **v³**, doubling the wind speed gives 8 times the power [51]. The variability of both wind and solar is why storage is needed.

### 4.7 Storage [33][34]
```
Duration         D = E_rated / P_rated
Round-trip eff.  η_rt = E_out / E_in
State of energy  dE_b/dt = η_c P_c(t) − P_d(t) / η_d        with η_rt = η_c η_d
Energy in        E_in = E_need / η_rt
Sizing           E_rated ≥ E_need / (η_d · DoD)     and     P_rated ≥ P_need
```
- **D**: duration (h)
- **E_rated**: rated energy capacity (MWh). In the sizing rule it is counted as stored energy, on the same scale as E_b; see the convention note below.
- **P_rated**: rated power capacity (MW), counted at the battery's terminals. EIA's example: 6 MW and 24 MWh gives D = 4 h [34].
- **η_rt**: round-trip efficiency, energy retrieved ÷ energy put in (about 0.82 for U.S. utility batteries in 2019 [33])
- **E_out**: energy retrieved from storage (at the terminals)
- **E_in**: energy put into storage (at the terminals)
- **E_b**: energy stored in the battery
- **P_c, P_d**: charging and discharging power at the terminals
- **η_c, η_d**: charging and discharging efficiencies. Storing P_c adds only η_c P_c; delivering P_d drains P_d/η_d.
- **E_need**: energy the load needs from storage, at the terminals
- **DoD**: usable depth of discharge, the fraction of rated energy you allow yourself to use
- **P_need**: highest power the load draws from storage

**Where the sizing rule comes from.** Integrate the state-of-energy equation over the discharge. Delivering E_need at the terminals drains E_need/η_d of stored energy, and only the fraction DoD of E_rated may be used, so DoD · E_rated ≥ E_need/η_d. Over a full charge and discharge, E_in = E_need/(η_c η_d) = E_need/η_rt.

**Which convention? (state it on the test).** A single η_rt does not tell you how the loss splits between η_c and η_d. Two conventions are possible:
- **(a) Rating stated as deliverable energy.** If E_rated is defined as the energy the battery can deliver at its terminals, the discharge loss is already inside the rating. Set η_d = 1 (so η_c = η_rt), and the rule becomes E_rated ≥ E_need/DoD.
- **(b) Rating stated as stored energy, loss split evenly.** With no other information, take η_c = η_d = √η_rt. For η_rt = 0.82, η_d ≈ 0.906, so the rated energy must be about 10% larger than under (a).

E_in = E_need/η_rt is the same under either convention; only E_rated changes. If the problem does not say which convention applies, (b) is the conservative (larger) answer. Problem 3 works both.

Two further assumptions are built into η_rt = η_c η_d: no self-discharge between charging and discharging, and constant efficiencies.

EIA classes batteries as short-duration (< 30 min), medium (30 min to 2 h) or long (> 2 h). California's averaged slightly under 4 h [34].

### 4.8 Efficiency chains (microgrid distribution)
```
η_path = η₁ η₂ … η_n             E_delivered = η_path E_generated
Mixed paths:  E_gen = Σ (f_k E_load / η_k)    so    η_overall = 1 / Σ (f_k / η_k)
```
- **η₁ … η_n**: efficiencies of the stages in series (inverter, transformer, feeder, battery and so on)
- **η_path**: efficiency of the whole path
- **E_generated, E_delivered**: energy produced, and energy that reaches the loads
- **E_load**: total energy delivered to loads
- **E_gen**: total energy that must be generated
- **f_k**: fraction of delivered energy that travels path k
- **η_k**: efficiency of path k
- **η_overall**: efficiency of the whole microgrid

Warning: the overall efficiency is **not** the simple weighted average Σ f_k η_k (see Problem 4).

### 4.9 Frequency and inertia (stretch, AP Physics C) [52]
```
K = ½ J ω²        ω = 2π f        ΔK = K [1 − (f₂/f₁)²] ≈ K (2Δf / f₁)
```
- **K**: rotational kinetic energy stored in spinning machines (J)
- **J**: moment of inertia (kg·m²)
- **ω**: angular speed (rad/s)
- **f**: grid frequency (Hz)
- **f₁, f₂**: frequency before and after a disturbance
- **Δf** = f₁ − f₂
- **ΔK**: kinetic energy released as the machines slow down

When a large plant trips, this stored energy briefly makes up the lost power. That buys seconds for other resources to respond [52].

### 4.10 Data centers [41]
```
PUE = E_facility / E_IT ≥ 1        DCiE = 1 / PUE
```
- **PUE**: power usage effectiveness
- **E_facility**: total energy drawn by the facility
- **E_IT**: energy used by the IT equipment
- **DCiE**: data-center infrastructure efficiency (the reciprocal of PUE)

Everything above 1.0 in the PUE is overhead: cooling, fans, pumps and power-distribution losses.

### 4.11 EV charging load [46][47][48]
```
E_EV = N d e / η_ch               P_coincident = N_on P_ch
```
- **E_EV**: daily grid energy for the fleet (kWh)
- **N**: number of EVs
- **d**: miles per EV per day
- **e**: vehicle efficiency (kWh/mi). The fueleconomy.gov label gives kWh/100 mi; for example, 25 kWh/100 mi = 0.25 kWh/mi for a 2024 Tesla Model 3 Long Range RWD [48].
- **η_ch**: charging efficiency, wall to battery
- **P_coincident**: extra demand when many EVs charge at the same time
- **N_on**: number of EVs charging at the same time
- **P_ch**: charger power. Typical values [46][47]:
  - Level 1 (120 V): about 1.9 kW
  - Level 2 (208/240 V): 2.9 to 19.2 kW, with 7.2 kW typical for a 30 A home unit
  - DC fast charging: up to 500 kW

### 4.12 Growth rates
```
CAGR = (X_end / X_start)^(1/n) − 1        X(t) = X₀ e^{k t}        T_double = ln 2 / k
```
- **CAGR**: compound annual growth rate
- **X_start, X_end**: the quantity at the start and end
- **n**: number of years between them
- **X(t)**: the quantity at time t
- **X₀**: the quantity at t = 0
- **k**: continuous growth rate (per year), with k = ln(1 + CAGR)
- **e**: Euler's number, about 2.718
- **T_double**: doubling time (years)

---

## Part 5. Worked problems (matched to the sheet's four tasks)

### Problem 1: Peak load requirement (calculus)
**Given.**
- A region's load is L(t) = 20 + 6 sin(π(t − 11)/12) GW *(assumed)*, where **t** is the hour of the day (0 to 24).
- The planning target is a 15% reserve margin *(assumed)*.

**Find** the peak, when it occurs, the load factor, the daily energy, the steepest ramp and the resources required.

**Solution.**
1. **When is the peak?** dL/dt = 6(π/12) cos(π(t − 11)/12) = 0, so t = 5 or t = 17. Since d²L/dt² < 0 at t = 17, the **peak is 26 GW at 5 p.m.** (The minimum is 14 GW at 5 a.m.)
2. **Average load.** The sine integrates to zero over 24 h, so P_avg = (1/24)∫₀²⁴ L dt = 20 GW.
3. **Load factor.** LF = 20/26 = **0.769**.
4. **Daily energy.** E = 20 GW × 24 h = **480 GWh**.
5. **Steepest ramp.** The largest dL/dt is 6π/12 ≈ **1.57 GW/h**, at 11 a.m.
6. **Resources required.** From RM = (Res − 26)/26 = 0.15, Res = 1.15 × 26 = **29.9 GW**.

**Takeaway:** every 1 GW of peak removed by demand response saves 1.15 GW of required resources.

### Problem 2: Transmission loss
**Given.**
- A three-phase line delivers P = 300 MW at V_LL = 345 kV with pf = 0.95 *(assumed)*.
- Each phase conductor is aluminum with ρ = 2.8 × 10⁻⁸ Ω·m *(assumed handbook value)*, L = 100 km and A = 5.0 × 10⁻⁴ m² *(assumed)*.

**Solution.**
1. **Resistance.** R_ph = ρL/A = (2.8 × 10⁻⁸)(1.0 × 10⁵)/(5.0 × 10⁻⁴) = **5.6 Ω**.
2. **Current.** I = P/(√3 V_LL pf) = 3.0 × 10⁸ / (1.732 × 3.45 × 10⁵ × 0.95) ≈ **528 A**.
3. **Loss.** P_loss = 3I²R_ph ≈ **4.69 MW**, which is **1.56%** of the delivered power.
4. **Same line at 138 kV.** I ≈ 1,321 A and P_loss ≈ **29.3 MW (9.8%)**. That is (345/138)² = 6.25 times more.

**Checks on this problem.**
- **Second route to the same answer.** The closed form from §4.2 skips the current entirely: P_loss = P² R_ph / (V_LL² pf²) = (3.0 × 10⁸)² (5.6) / [(3.45 × 10⁵)² (0.95)²] = (5.04 × 10¹⁷) / (1.074 × 10¹¹) ≈ **4.69 × 10⁶ W**, and the loss fraction P R_ph / (V_LL² pf²) = (1.68 × 10⁹) / (1.074 × 10¹¹) ≈ **1.56%**. Both match steps 2 and 3. This checks the arithmetic; it cannot check the assumed inputs.
- **Ratio.** 29.3 / 4.69 ≈ 6.25 = (345/138)², exactly what the 1/V² rule predicts.
- **Plausibility.** A 1.56% loss on one 100 km high-voltage line is the same order of magnitude as EIA's average of about 5% for the entire U.S. T&D system [30].

**The same rule in OpenStax's textbook example (an illustration, not a check of this problem).** OpenStax sends 100 MW at 200 kV through a 1.00 Ω line, which gives I = P/V = 500 A and P_loss = I²R = 250 kW [45], or 0.25% of the power sent. That example is single-phase with different inputs, so it does not test the numbers above. It shows the same 1/V² scaling: at one tenth of the voltage (20 kV), I = 5,000 A and the loss would be 25 MW, 10² = 100 times more (our calculation).

### Problem 3: Storage for intermittent solar (calculus)
**Given.**
- A microgrid's solar output is S(t) = 50 sin(π(t − 6)/12) MW for 6 ≤ t ≤ 18, and 0 otherwise *(assumed)*.
- The daytime load is a constant 20 MW *(assumed)*.
- After sunset the battery alone must supply 30 MW from 18:00 to 22:00 *(assumed)*.
- Round-trip efficiency η_rt = 0.82 [33], and usable DoD = 0.90 *(assumed)*.
- The microgrid stays connected to the main grid, which covers any load the solar and battery do not *(assumed)*. The battery charges only from solar surplus and starts the day at its lowest allowed state of energy.

**Solution.**
1. **Total daily solar energy.** ∫₆¹⁸ 50 sin(π(t − 6)/12) dt = 50 × 24/π ≈ **382 MWh**.
2. **Evening need.** E_need = 30 MW × 4 h = **120 MWh** delivered at the battery's terminals.
3. **Energy that must go in.** E_in = E_need/η_rt = 120/0.82 ≈ **146 MWh**. This is true however the loss splits between charging and discharging (§4.7).
4. **Surplus available for charging.** Surplus exists when S > 20, which means sin x > 0.4 with x = π(t − 6)/12. That gives t from 7.57 h to 16.43 h, a window of 8.856 h. The surplus is:
   ∫(S − 20) dt = 50(12/π)(2 cos(arcsin 0.4)) − 20(8.856) ≈ 350.1 − 177.1 ≈ **173 MWh**.
   Since 173 ≥ 146, enough surplus is available.
   - Before 7.57 h and after 16.43 h, solar is below the 20 MW load. Those daytime shortfalls total 240 − 382 + 173 ≈ **31 MWh**, which the main grid supplies under the assumption above.
5. **Charging power.** The largest surplus is 50 − 20 = 30 MW at noon, so a 30 MW battery can absorb it.
6. **Size.** P_rated ≥ 30 MW. For the energy rating, use E_rated ≥ E_need/(η_d · DoD) from §4.7:
   - **Convention (b), loss split evenly** (η_c = η_d = √0.82 ≈ 0.906, consistent with the state-of-energy equation). Discharging 120 MWh drains 120/0.906 ≈ 132.5 MWh of stored energy. So E_rated ≥ 132.5/0.90 ≈ **147 MWh**. Choose **30 MW / 150 MWh (5 h)**.
     - Check the usable energy: 0.90 × 150 = 135 MWh ≥ 132.5 MWh.
     - Check the charging: storing 132.5 MWh at η_c = 0.906 takes 132.5/0.906 ≈ 146 MWh from the solar surplus, which matches step 3 and is below 173 MWh.
   - **Convention (a), rating stated as deliverable energy** (η_d = 1 in the formula). E_rated ≥ 120/0.90 ≈ **133 MWh**, so 30 MW / 135 MWh (4.5 h) would do.
   - **Why the convention matters.** Under (b), a 135 MWh battery delivers only 0.90 × 135 × 0.906 ≈ 110 MWh, which is short of 120 MWh. Unless the problem says ratings are deliverable energy, give the conservative answer: **30 MW / 150 MWh**.

Note that a "standard" 4-hour, 120 MWh unit falls short under either convention once the DoD limit is applied.

### Problem 4: Microgrid distribution efficiency
**Given** (all efficiencies *assumed*):
- Direct path: PV → inverter (0.97) → transformer (0.985) → feeder (0.97) → loads.
- Battery path: PV → inverter (0.97) → battery (η_rt = 0.82 [33]) → transformer (0.985) → feeder (0.97) → loads.
- 60% of delivered energy goes direct and 40% goes through the battery.

**Solution.**
1. **Path efficiencies.** η_direct = 0.97 × 0.985 × 0.97 = **0.927**. η_battery = 0.97 × 0.82 × 0.985 × 0.97 = **0.760**.
2. **Generation needed per MWh delivered.** 0.6/0.927 + 0.4/0.760 = **1.174 MWh**.
3. **Overall efficiency.** η_overall = 1/1.174 = **0.852 (85.2%)**.

**Common trap:** the weighted average 0.6(0.927) + 0.4(0.760) = 0.860 overstates the efficiency. Losses must be counted against the energy generated, not the energy delivered.

### Problem 5: EV demand growth
**Given** *(assumed)*:
- A city with a 1,200 MW peak and a 15% reserve margin has 1,380 MW of resources.
- It adds N = 50,000 EVs, each driving 30 mi/day at e = 0.30 kWh/mi, with η_ch = 0.90.

**Solution.**
1. **Daily energy.** E_EV = 50,000 × 30 × 0.30 / 0.90 = **500 MWh/day**. That is 10 kWh per car per day.
2. **Unmanaged charging.** If 40% plug into 7.2 kW Level 2 chargers at 6 p.m. [46], P_coincident = 20,000 × 7.2 kW = **144 MW**, on top of the peak.
   - The new peak is 1,344 MW.
   - The reserve margin becomes (1,380 − 1,344)/1,344 = **2.7%**, down from 15%.
3. **Managed (smart) charging.** Each car needs only 10/7.2 ≈ 1.4 h of charging. Staggered over 11 p.m. to 7 a.m., the same 500 MWh averages **62.5 MW** spread across off-peak hours, and **adds nothing to the 6 p.m. peak**. This is what smart meters and price signals make possible.

### Problem 6: Data-center demand
**Given.**
- A data center draws 100 MW around the clock *(assumed)*, with PUE = 1.3 *(assumed)*.
- The average U.S. home used 10,791 kWh in 2022 [38].

**Solution.**
1. **Annual energy.** E = 100 MW × 8,760 h = **876 GWh**. That is as much as 876 × 10⁶ / 10,791 ≈ **81,000 homes**, about the size of a city.
2. **IT energy.** E_IT = 876/1.3 = 674 GWh, so overhead = 202 GWh.
3. **Better cooling.** Cutting the PUE to 1.1 for the same IT work brings the total to 741 GWh. That saves **135 GWh/yr**, about 12,500 homes' worth.
4. **National trend.** U.S. data centers used 58 TWh in 2014 and 176 TWh in 2023 (**4.4%** of U.S. electricity). LBNL projects **6.7% to 12%** by 2028 [39][40].
   - CAGR from 2014 to 2023 = (176/58)^(1/9) − 1 ≈ **13.1%/yr**.
   - Doubling time = ln 2 / ln(1.131) ≈ **5.6 years**.
   - **Independent check of the 4.4% share.** EIA's *Electric Power Annual* reports 2023 U.S. end-use consumption of about 4,011 TWh: retail sales of 3,874 TWh plus direct use of 137 TWh [54]. Then 176/4,011 = 4.39%, which rounds to the 4.4% reported. Against retail sales alone the share would be 4.5%, so 4.4% matches total end use.
   - **What this check cannot do.** Dividing 176 by 0.044 only gives back the report's implied denominator: about 4,000 TWh, or anywhere from about 3,960 to 4,050 TWh because 4.4% is rounded. On its own, that step verifies nothing. The real test is that EIA's independent 4,011 TWh falls inside that range, and that tests only the share. The 176 TWh is LBNL's model estimate [40]; no arithmetic here can confirm it. Treat it as the best available published estimate.
5. **Grid-scale view.** NERC's 2025 assessment forecasts North American summer peak demand rising by **over 224 GW in 10 years**, mostly from data centers [42]. ERCOT's forecast summer peak goes from 94,650 MW (2026) to 154,077 MW (2035), a CAGR of (154,077/94,650)^(1/9) − 1 ≈ **5.6%/yr** [42].

### Problem 7: Power-factor correction [49]
**Given:** a load draws 100 kW at 142 kVA.

**Solution.**
1. **Power factor.** pf = 100/142 = **0.70**.
2. **Reactive power.** Q = √(142² − 100²) ≈ 101 kVAR.
3. **After adding 67 kVAR of capacitors.** Q ≈ 34 kVAR, so S = √(100² + 34²) ≈ **105.6 kVA** and pf ≈ **0.95**.
4. **Current.** The current falls in proportion to S, by about **26%**. Since losses go as I², line losses fall by about 45%.

### Problem 8: Wind is cubic [51]
**Given:** a rotor with r = 60 m, ρ_air = 1.225 kg/m³, v = 10 m/s and C_p = 0.45 *(assumed)*.

**Solution.**
1. **Swept area.** A_r = π(60)² ≈ 11,310 m².
2. **Power.** P_w = ½(1.225)(11,310)(10³)(0.45) ≈ **3.12 MW**.
3. **A gust.** If v rises from 6 to 7.5 m/s (+25%), power rises by a factor of (1.25)³ = **1.95**.

### Stretch problem: inertia
**Given:** an interconnection stores K = 300 GJ in spinning machines *(assumed)*, and a 1,000 MW plant trips.

**Solution.**
1. **Energy released.** Letting the frequency fall from 60.0 to 59.5 Hz releases ΔK = K[1 − (59.5/60)²] ≈ **4.98 GJ**.
2. **Time bought.** That covers the missing 1,000 MW for about **5 s**, time for governors, batteries or demand response to act [52].

### Bonus: why grid analysis needs AI
- Argonne uses machine-learning optimization models to simulate the electric system and judge how severe different problems are [14].
- **Count the cases.** For a system with 1,000 assets, the number of ways three can fail is:
  - C(1000, 3) = **166,167,000** unordered sets, where C(n, k) = n! / (k!(n − k)!) is the number of ways to choose k items from n when order does not matter.
  - 1000 × 999 × 998 ≈ **9.97 × 10⁸** if the order of failure matters.

  Checking every case by brute force is impractical.

---

## Part 6. Numbers worth memorizing

| Fact | Value | Source |
|---|---|---|
| U.S. T&D losses | about 5% (2018 to 2022 average) | [30] |
| Smart (AMI) meters | about 119 million, about 72% of meters (2022) | [32] |
| Utility battery round-trip efficiency | 82% (pumped hydro 79%), 2019 | [33] |
| Battery duration example | 6 MW / 24 MWh = 4 h | [34] |
| Data-center electricity | 176 TWh = 4.4% of U.S. use (2023), projected 6.7% to 12% (2028) | [39][40] |
| U.S. end-use electricity, 2023 | about 4,011 TWh (retail sales 3,874 TWh + direct use 137 TWh) | [54] |
| NERC 10-year summer peak growth | over 224 GW (2025 assessment) | [42] |
| FLISR (SGIG) | up to 45% fewer customers out, up to 51% fewer outage-minutes per event | [27] |
| GRIP | $10.5 billion | [29] |
| Order No. 2222 | 17 Sep 2020; DERs typically 1 kW to 10,000 kW | [23] |
| DOE national labs | 17, leading U.S. science for 70+ years (10 stewarded by the Office of Science) | [2][10][11] |
| Interconnections | 3 (Eastern, Western, Texas/ERCOT) | [7] |
| NERC regional entities | 6 | [7] |
| Average home | 10,791 kWh/yr (2022), about 899 kWh/month | [38] |
| EV charging levels | Level 1 about 1.9 kW; Level 2 2.9 to 19.2 kW; DC fast up to 500 kW | [46][47] |
| Betz limit | 16/27 ≈ 59.3% | [51] |
| EISA smart-grid title | Title XIII (2007); §1301 characteristics; §1305 interoperability | [20] |
| Mandatory grid cyber standards | NERC CIP, approved by FERC Order No. 706 (Jan 2008) under EPAct 2005 authority | [55][56] |

---

## Part 7. Data for practice
The sheet's "Smart Grid Datasets Catalog" corresponds to **Data.gov** (catalog.data.gov), the federal open-data catalog run by the U.S. General Services Administration [5].
- **What the catalog shows.** Its home page lists the whole catalog, sorted by relevance and then by popularity, and lets you narrow results by organization (a federal agency, or a state or city) [5]. It listed 431,264 datasets when indexed in October 2026; the count changes as agencies add and remove records [5].
- **What it is not.** Data.gov is a metadata catalog: it displays information about datasets that individual agencies publish and maintain, and it does not create, modify or delete those datasets [57]. Expect each entry to link you to the publishing agency's data.
- **For this section.** A search for the tag "smart-grid" returns only a handful of datasets [15]. Useful ones:
  - **SMART-DS** (DOE/NREL): synthetic but realistic distribution-grid models with time-series loads for the San Francisco, Greensboro and Austin areas, in OpenDSS format [16].
  - **NIST TN 2137 data and code:** "Quantifying Operational Resilience Benefits of the Smart Grid" [17].
  - **Grid Connected Functionality** (NREL): residential buildings providing frequency regulation, using hardware-in-the-loop tests [18].

Try this: take any hourly load series and compute its peak, its load factor and the battery needed to shave the top 10% of the peak. These are the methods of Problems 1 and 3.

---

## Part 8. Glossary
- **Ancillary services:** grid-support services such as frequency regulation and reserves [23].
- **Balancing authority (BA):** the entity that keeps supply matched to demand in its area [19][31].
- **Capacity factor:** actual energy ÷ (capacity × hours) [37].
- **DER:** a distributed energy resource, such as rooftop PV, batteries, smart thermostats or EV chargers [23].
- **Duck curve:** the net-load shape caused by midday solar, with a steep evening ramp [35].
- **eGRID:** EPA's emissions and generation database by grid region [7].
- **FLISR:** fault location, isolation and service restoration (self-healing switching) [27].
- **Interoperability:** devices and systems working together without special effort, through common standards [20][22].
- **Island mode:** a microgrid running disconnected from the main grid [28].
- **ISO/RTO:** independent system operator / regional transmission organization; runs the wholesale market and transmission in its region [19].
- **Load factor:** average load ÷ peak load [36].
- **Net load:** demand minus variable renewable output [35].
- **PUE:** facility energy ÷ IT energy [41].
- **Reserve margin:** (resources − net internal demand) ÷ net internal demand [43].
- **Round-trip efficiency:** energy out of storage ÷ energy in [33].

---

## Part 9. Self-test (answers below)
1. With P, R and pf fixed, what happens to line losses if the voltage triples?
2. Name the three U.S. interconnections. Which one is a single balancing authority?
3. Which law and section list the characteristics of a smart grid?
4. A battery is rated 6 MW / 24 MWh. What is its duration? If it is charged with 24 MWh of input energy and η_rt = 0.82, how much energy comes back out?
5. A region averages 20 GW with a 26 GW peak. What are its load factor, and the resources needed for a 15% reserve margin?
6. The wind speed rises 10%. By what percentage does the power rise?
7. A data center has an IT load of 40 MW and PUE = 1.5. What is the facility load?
8. What did FERC Order No. 2222 do?
9. For S(t) = S_max sin(π(t − 6)/12) on [6, 18] (zero otherwise), what is the daily energy?
10. Why is the overall efficiency of a mixed-path microgrid not the weighted average of the path efficiencies?
11. What separates a microgrid from a group of DERs?
12. What does FLISR do, and what was the measured benefit?
13. A battery must deliver 60 MWh at its terminals. Its η_rt = 0.81, split evenly between charging and discharging, and DoD = 0.80. What is the minimum stored-energy rating, and how much energy must go in?

**Answers.**
1. The losses fall to 1/9.
2. The Eastern, Western and Texas (ERCOT) interconnections. ERCOT is the single BA.
3. EISA 2007, Title XIII, §1301.
4. 4 h. It returns 0.82 × 24 ≈ 19.7 MWh.
5. LF = 0.769; resources = 29.9 GW.
6. 1.1³ = 1.331, so a 33.1% rise.
7. 60 MW.
8. It let DER aggregations take part in RTO/ISO capacity, energy and ancillary-service markets.
9. 24 S_max/π ≈ 7.64 S_max (in MWh if S_max is in MW).
10. Generation needed is Σ f_k/η_k per unit delivered, so η_overall = 1/Σ(f_k/η_k).
11. It can island, running as one controllable entity disconnected from the grid.
12. It finds and isolates a fault and reroutes power around it automatically. In SGIG it cut customers interrupted by up to 45% and customer-minutes by up to 51% per event.
13. η_d = √0.81 = 0.9, so E_rated ≥ 60/(0.9 × 0.80) ≈ 83.3 MWh. Energy in = 60/0.81 ≈ 74.1 MWh. (If the rating were stated as deliverable energy, 60/0.80 = 75 MWh would do.)

---

## Part 10. Citation page

**How these were consulted.** Every source was read through web-search results (indexed page text and excerpts), because direct page loading failed in our research tool. Sources [1] to [53] were read on 27 Oct 2026. On 28 Oct 2026, [2], [4], [5] and [12] were re-read and [54] to [57] were read for the first time; a direct fetch of [2], [4] and [5] was tried again and still failed with a DNS error. Each URL below was returned live by the search index on the date it was read. The notes in table A say exactly what was taken from each supplied page's own text.

### A. The seven sources you supplied

| # | Sheet "Explore More" title | Source | URL |
|---|---|---|---|
| 1 | *(supplied as the first source; the content does not match the sheet's first title)* | Jorge, V. A. M., et al. (2019). A Survey on Unmanned Surface Vehicles for Disaster Robotics: Main Challenges and Directions. *Sensors*, 19(3), 702. doi:10.3390/s19030702 | https://pmc.ncbi.nlm.nih.gov/articles/PMC6387351/ |
| 2 | U.S. Department of Energy: National Laboratories | U.S. DOE, National Laboratories. *Own text read through search-index excerpts of this URL (28 Oct 2026): 17 labs, 70+ years of leading U.S. science, lab profiles including Argonne (§2.5). The Office of Science / NNSA split is from companion pages [10] and [11].* | https://www.energy.gov/national-laboratories |
| 3 | U.S. Department of Energy: Smart Grid Information | U.S. DOE, Office of the General Counsel, SmartGrid Information | https://www.energy.gov/gc/smartgrid-information |
| 4 | Federal Energy Regulatory Commission: Smart Grid | FERC, Smart Grid. *Own text read through search-index excerpts of this URL (28 Oct 2026): its purpose under EISA Title XIII, the three sources of FERC's smart-grid authority, and its quick links (§2.5, §3.1). Details of the documents it links come from [21], [22] and [55]; Order No. 2222 from [23]; Docket RM11-2 from [53].* | https://www.ferc.gov/smart-grid-1 |
| 5 | Smart Grid Datasets Catalog | Data.gov Catalog (U.S. General Services Administration). *Home page read through search-index excerpts of this URL (28 Oct 2026): catalog size, sorting, organization filter (Part 7). Individual datasets from its pages [15] to [18].* | https://catalog.data.gov/ |
| 6 | Argonne National Laboratory: Electric Grid | Argonne National Laboratory, Electric Grid | https://www.anl.gov/electric-grid |
| 7 | U.S. Environmental Protection Agency: Grid Regions | U.S. EPA, Green Power Markets: U.S. Grid Regions | https://www.epa.gov/green-power-markets/us-grid-regions |

### B. The sheet's "U.S. Department of Energy: Smart Grid" (found by title)
8. U.S. DOE, Office of Electricity. *Grid Modernization and the Smart Grid.* https://www.energy.gov/oe/grid-modernization-and-smart-grid
9. U.S. DOE, SmartGrid.gov. *The Smart Grid.* https://www.smartgrid.gov/the_smart_grid/smart_grid.html

### C. Additional reliable sources
10. U.S. DOE. *Labs.* https://www.energy.gov/labs
11. U.S. DOE, Office of Science. *Office of Science National Laboratories.* https://www.energy.gov/science/office-science-national-laboratories
12. U.S. DOE. *Energy Department Renames NREL "National Lab of the Rockies."* (1 Dec 2025). https://www.energy.gov/eere/articles/energy-department-renames-nrel-national-lab-rockies
13. Argonne National Laboratory. *Smart Energy Plaza.* https://www.anl.gov/aet/smart-energy-plaza
14. Argonne National Laboratory. *Artificial intelligence can make the U.S. electric grid smarter.* https://www.anl.gov/article/artificial-intelligence-can-make-the-us-electric-grid-smarter
15. Data.gov. *Datasets tagged "smart-grid".* https://catalog.data.gov/dataset?tags=smart-grid
16. Data.gov. *SMART-DS Synthetic Electrical Network Data OpenDSS Models for SFO, GSO, and AUS.* https://catalog.data.gov/dataset/smart-ds-synthetic-electrical-network-data-opendss-models-for-sfo-gso-and-aus
17. Data.gov. *Data and Code for Analysis presented in NIST TN 2137: Quantifying Operational Resilience Benefits of the Smart Grid.* https://catalog.data.gov/dataset/data-and-code-for-analysis-presented-in-nist-tn-2137-quantifying-operational-resilience-be-ddc13
18. Data.gov. *Grid Connected Functionality.* https://catalog.data.gov/dataset/grid-connected-functionality-cdc41
19. U.S. EPA. *U.S. Electricity Grid & Markets.* https://www.epa.gov/green-power-markets/us-electricity-grid-markets
20. *Energy Independence and Security Act of 2007, Title XIII: Smart Grid* (Pub. L. 110-140), DOE-hosted text. https://www.energy.gov/sites/prod/files/oeprod/DocumentsandMedia/EISA_Title_XIII_Smart_Grid.pdf
21. FERC. *Smart Grid Policy* (2009). https://www.ferc.gov/sites/default/files/2020-08/E-3-Fercs-Smart-Grid-Policy.pdf
22. U.S. Government Accountability Office report on smart-grid standards and cybersecurity, hosted by FERC. https://www.ferc.gov/sites/default/files/2020-05/gao-report.pdf
23. FERC. *FERC Order No. 2222 Explainer: Facilitating Participation in Electricity Markets by Distributed Energy Resources.* https://www.ferc.gov/ferc-order-no-2222-explainer-facilitating-participation-electricity-markets-distributed-energy
24. U.S. DOE, Office of the General Counsel. *Data Access and Privacy Issues Related to Smart Grid Technologies.* https://www.energy.gov/gc/articles/department-energy-data-access-and-privacy-issues-related-smart-grid-technologies
25. U.S. DOE, Office of the General Counsel. *Communications Requirements of Smart Grid Technologies.* https://www.energy.gov/gc/articles/communications-requirements-smart-grid-technologies
26. U.S. DOE. *Smart Grid System Report 2018* (Report to Congress). https://www.energy.gov/sites/prod/files/2019/02/f59/Smart%20Grid%20System%20Report%20November%202018_1.pdf
27. U.S. DOE. *Fault Location, Isolation, and Service Restoration Technologies Reduce Outage Impact and Duration* (Dec 2014). https://www.energy.gov/sites/prod/files/2016/10/f33/Fault_Location_Impact_Duration_Dec_2014.pdf
28. U.S. DOE, Office of Electricity. *2012 DOE Microgrid Workshop Summary Report.* https://www.energy.gov/oe/articles/2012-doe-microgrid-workshop-summary-report-september-2012
29. U.S. DOE, Grid Deployment Office. *Grid Resilience and Innovation Partnerships (GRIP) Program.* https://www.energy.gov/gdo/grid-resilience-and-innovation-partnerships-grip-program
30. U.S. EIA. *How much electricity is lost in electricity transmission and distribution in the United States?* https://www.eia.gov/tools/faqs/faq.php?id=105&t=3
31. U.S. EIA. *U.S. electric system is made up of interconnections and balancing authorities.* https://www.eia.gov/todayinenergy/detail.php?id=27152
32. U.S. EIA. *How many smart meters are installed in the United States, and who has them?* https://www.eia.gov/tools/faqs/faq.php?id=108&t=3
33. U.S. EIA. *Utility-scale batteries and pumped storage return about 80% of the electricity they store.* https://www.eia.gov/todayinenergy/detail.php?id=46756
34. U.S. EIA. *Duration of utility-scale batteries depends on how they're used.* https://www.eia.gov/todayinenergy/detail.php?id=51798
35. U.S. EIA. *As solar capacity grows, duck curves are getting deeper in California.* https://www.eia.gov/todayinenergy/detail.php?id=56880
36. U.S. EIA. *Glossary: Load factor.* https://www.eia.gov/tools/glossary/index.php?id=Load_factor
37. U.S. EIA. *Electric Power Monthly, Table 6.07.B: Capacity Factors for Utility Scale Generators Primarily Using Non-Fossil Fuels.* https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_6_07_b
38. U.S. EIA. *How much electricity does an American home use?* https://www.eia.gov/tools/faqs/faq.php?id=97&t=3
39. U.S. DOE. *DOE Releases New Report Evaluating Increase in Electricity Demand from Data Centers* (Dec 2024). https://www.energy.gov/articles/doe-releases-new-report-evaluating-increase-electricity-demand-data-centers
40. Shehabi, A., et al. *2024 United States Data Center Energy Usage Report.* Lawrence Berkeley National Laboratory. https://eta-publications.lbl.gov/publications/2024-lbnl-data-center-energy-usage-report
41. The Green Grid. *PUE: A Comprehensive Examination of the Metric* (White Paper 49), hosted by LBNL. https://datacenters.lbl.gov/sites/default/files/WP49-PUE%20A%20Comprehensive%20Examination%20of%20the%20Metric_v6.pdf
42. NERC. *2025 Long-Term Reliability Assessment.* https://www.nerc.com/globalassets/our-work/assessments/nerc_ltra_2025.pdf
43. NERC. *2026 Summer Reliability Assessment* (reserve-margin and net-internal-demand definitions). https://www.nerc.com/globalassets/our-work/assessments/nerc_sra_2026.pdf
44. OpenStax. *University Physics Volume 2, §15.6 Transformers.* https://openstax.org/books/university-physics-volume-2/pages/15-6-transformers
45. OpenStax. *College Physics 2e, §20.5 Alternating Current versus Direct Current.* https://openstax.org/books/college-physics-2e/pages/20-5-alternating-current-versus-direct-current
46. U.S. DOE, Alternative Fuels Data Center. *Charging Electric Vehicles at Home.* https://afdc.energy.gov/fuels/electricity-charging-home
47. U.S. DOE, Alternative Fuels Data Center. *Electric Vehicle Charging Stations.* https://afdc.energy.gov/fuels/electricity-stations
48. U.S. DOE / EPA, FuelEconomy.gov. *Learn More About the Fuel Economy Label for Electric Vehicles.* https://fueleconomy.gov/feg/label/learn-more-electric-label.shtml
49. U.S. DOE, Advanced Manufacturing Office. *Reducing Power Factor Cost* (tip sheet). https://www.energy.gov/sites/prod/files/2014/04/f15/mc60405.pdf
50. U.S. DOE, Advanced Manufacturing Office. *Improving Motor and Drive System Performance: A Sourcebook for Industry.* https://www.energy.gov/sites/prod/files/2014/04/f15/amo_motors_sourcebook_web.pdf
51. Penn State College of Earth and Mineral Sciences. *EME 444: Wind Power.* https://www.e-education.psu.edu/eme444/node/363
52. Denholm, P., et al. (2020). *Inertia and the Power Grid: A Guide Without the Spin* (NREL/TP-6A20-73856). National Renewable Energy Laboratory (now National Laboratory of the Rockies). https://www.nrel.gov/docs/fy20osti/73856.pdf
53. POWER Magazine. *FERC Declines Rulemaking, Tosses Smart Grid Interoperability Standards Back to NIST* (2011; quotes FERC's order ending Docket RM11-2). https://www.powermag.com/ferc-declines-rulemaking-tosses-smart-grid-interoperability-standards-back-to-nist/
54. U.S. EIA. *Electric Power Annual, Table 2.2: Sales and Direct Use of Electricity to Ultimate Customers by Sector, by Provider.* *Read on 28 Oct 2026 through search-index excerpts; a direct fetch failed with a DNS error.* https://www.eia.gov/electricity/annual/table.php?t=epa_02_02.html
55. FERC. *Cyber and Grid Security* (linked from [4]'s quick links). https://ferc.gov/industries-data/electric/industry-activities/cyber-and-grid-security
56. FERC. *Mandatory Reliability Standards for Critical Infrastructure Protection*, Order No. 706, 122 FERC ¶ 61,040 (18 Jan 2008), Docket RM06-22-000. https://www.ferc.gov/sites/default/files/2020-04/E-2_11.pdf
57. Data.gov (U.S. General Services Administration). *User Guide.* https://data.gov/user-guide/

---

### Requirement check
- All seven supplied URLs cited and used, each with facts drawn from its own text: [1]–[7] (table A says what came from each).
- All seven "Explore More" titles matched to a source: table A, plus [8] and [9] for "U.S. Department of Energy: Smart Grid".
- Other reliable sources: [10]–[57].
- Total sites: 57, against the minimum of 15.
- Every equation has its variables and units defined: Part 4, with new symbols defined inside Problems 1–8.
- Citation page: Part 10.
