# Smart Cities: TEAMS 2027 Study Guide ("Engineering a Smarter World")

**How to use this guide.** The section sheet says your team will *calculate* a developing smart city's power needs and distribution, its infrastructure requirements, and its access to natural resources. So the guide is organized around those calculations, and each fact from the sources sits next to the math it feeds. Section 6 covers data, privacy and policy, which is the material for anything written or presented. Bracketed numbers like [3] point to the citation page at the end.

**Assumptions**
- "Sites" is read strictly, as distinct websites. This guide uses 17: the 10 you gave plus 7 more (U.S. Energy Information Administration, U.S. Census Bureau, MIT, Brennan Center for Justice, arXiv, Town of Herndon VA, and Pumps & Systems). It cites 24 pages in all. Other URLs for an assigned document, such as a summary page or an archived copy, are listed under that source and are not counted as extra sources.
- Values marked *assumed* in the worked examples are practice inputs, not facts. On the test, use the values the problem gives you.
- Every equation is followed by a table saying what each variable represents and its units.

---

## 1. The big picture

**Definition (from the section sheet).** A smart city is an urban area that uses data, digital tools and connected infrastructure to improve efficiency, sustainability and quality of life. It can also be described as an ecosystem where information and communication technologies improve urban performance, lower emissions and deliver better public services. The sheet stresses that a smart city integrates technology, governance and community, not just devices.

**Why cities need it (sheet).** Cities first grew up near resources such as rivers, ports and farmland. As they grew, transportation, energy and water/sewage became the hard problems, and infrastructure was often outgrown by the time it was built. Adding subway in Washington, D.C. can cost hundreds of millions of dollars per mile, and New York City plans to spend $500 million in 2026 on drinking-water distribution and treatment.

**Every smart system runs the same loop:**
sense (meters, sensors, cameras) → connect (networks) → decide (analytics, AI) → act (retime a signal, reroute power, alert a person) → govern (who owns the data, and does it actually work?)

| Term | What it means |
|---|---|
| Smart grid | A power grid that adds information flow to power flow. InfraJournal describes it as a network of communicating, decentralised distribution points that can take in variable renewable power and manage energy deficits and surpluses [1]. |
| AMI (advanced metering infrastructure) | "Smart meters" that record electricity use at least hourly and report it at least daily. U.S. utilities had about 119 million AMI meters in service in 2022, about 72% of all electric meters [13]. |
| DER (distributed energy resources) | Small generation or storage near the load (rooftop solar, batteries), often not owned by the utility [2]. |
| Microgrid | A local grid whose main resilience benefit is that it can disconnect from the main grid during an outage and keep running on its own [12]. |
| Capacity factor | Energy a plant actually produced divided by the most it could have produced (equation 2.3). |
| Peaking factor | Design flow divided by average flow, e.g. maximum-day or peak-hour water demand (equation 3.2) [22]. |
| Open data | City datasets published for anyone to use, usually through an open data portal [4]. |
| ALPR | Automated license plate reader: a camera plus software that reads plates and checks them against lists of wanted vehicles [6][7][20]. |
| Location efficiency | How well a place's density, land-use mix, street design and transit let people reach destinations with less driving [10]. |

---

## 2. Power needs and distribution

**What the sources say**
- **DOE 2020 Smart Grid System Report, key findings [2]:**
  1. A variety of DERs, often not utility-owned, shifts grid operation from *control* to *control and coordination*.
  2. Resilience planning needs a whole-systems approach to guide smart grid investment.
  3. Managing cyber risk is key to enabling the smart grid.
  4. Plug-and-play interoperability will remain a challenging, long-term task.
  5. Grid modernization is an essential part of integrated planning.
- **Investment [2]:** U.S. smart grid technology investment rose from $3.4 billion (2014) to $6.4 billion (2018) and was forecast to reach about $16.4 billion a year by 2026. The 2009 Recovery Act funded more than 130 deployment projects.
- **InfraJournal [1]:** decentralised grids combined with information technology are how future smart cities will be supplied. Customers become participants, for example by storing renewable energy.
- **Benchmarks:**
  - The average U.S. home bought 10,791 kWh of electricity in 2022, about 899 kWh a month [15].
  - Homes are not the whole city. In 2022 the residential sector bought 38.4% of U.S. retail electricity and the industrial sector 26.0%. Commercial customers bought most of the rest [11].
  - Transmission and distribution losses averaged about 5% in 2018–2022 [14].
  - 2023 U.S. capacity factors (utility-scale generators, all sectors) were nuclear 93.0%, wind 33.2% and solar photovoltaic 23.2% [16].

**Equations**

(2.1) Energy and average power: E = P_avg × t

(2.2) Load factor: LF = P_avg / P_peak

(2.3) Capacity factor: CF = E_actual / (P_rated × t)

(2.4) Whole-city energy from household data: E_load = N_h × e_h / s_res

(2.5) Generation needed to cover losses: E_gen = E_load / (1 − L)

| Variable | Represents | Units |
|---|---|---|
| E | Energy used or produced over the period | kWh, MWh, GWh |
| P_avg | Average power demand | kW, MW |
| t | Length of the period (1 year = 8,760 h) | h |
| LF | Load factor: average demand as a fraction of peak demand | none (0–1) |
| P_peak | Highest demand in the period; the grid must be sized for this | MW |
| CF | Capacity factor | none (0–1) |
| E_actual | Energy the plant actually delivered | MWh |
| P_rated | Nameplate (maximum rated) power of the plant | MW |
| E_load | Energy delivered to all customers: homes, businesses, industry | MWh |
| N_h | Number of households | households |
| e_h | Annual electricity bought by one household | kWh/household |
| s_res | Residential share of the city's total electricity use (U.S. 2022: 0.384 with industry; about 0.52 without industry; 1 for homes only) | none (0–1) |
| E_gen | Energy that must be generated at power plants | MWh |
| L | Fraction of energy lost in transmission and distribution | none (≈ 0.05) |

**Worked example A: a new city of 50,000 households (about 126,500 people at 2.53 people per household [24])**
1. Homes only: 50,000 × 10,791 kWh = 539,550 MWh a year.
2. Whole city. The divisor s_res depends on what the city contains, so state which case you assume:
   - Homes only (s_res = 1): E_load = 539,550 MWh.
   - Homes plus shops, offices, schools and hospitals, but no heavy industry: s_res = 0.384 ÷ (1 − 0.260) ≈ 0.52, so E_load ≈ 1,040,000 MWh.
   - National mix, including industry (s_res = 0.384): E_load = 539,550 ÷ 0.384 ≈ 1,405,000 MWh (1.405 TWh).

   The steps below carry the national mix forward. Every later result is proportional to E_load, so for a city with no heavy industry, multiply each one by 1,040 ÷ 1,405 ≈ 0.74.
3. Average demand: P_avg = 1,405,000 MWh ÷ 8,760 h ≈ 160 MW.
4. Peak demand (LF = 0.55, *assumed*): P_peak = 160.4 ÷ 0.55 ≈ 292 MW.
5. Generation with 5% losses: E_gen = 1,405,000 ÷ 0.95 ≈ 1,479,000 MWh.
6. Nameplate needed for that energy from **solar**: 1,479,000 ÷ (0.232 × 8,760) ≈ 728 MW. From **nuclear**: 1,479,000 ÷ (0.930 × 8,760) ≈ 182 MW.
7. Check the peak. Generating capacity that can be counted on at the peak hour must be at least P_peak ÷ (1 − L) ≈ 292 ÷ 0.95 ≈ 307 MW, plus a reserve margin for plants that are out of service. Step 6 fails this check:
   - 182 MW of nuclear covers the year's energy on paper but leaves about 125 MW uncovered at the peak. Its 93% capacity factor means it runs near full output almost all the time, so it cannot follow the daily swing either.
   - 728 MW of solar may deliver nothing at an evening peak.
   - Size for whichever rule (energy or peak) gives the larger number. Then fill the gap between average and peak with peaking plants, storage or demand response.

**Traps**
- kW is a *rate*; kWh is an *amount*. 1 kW running for 1 hour = 1 kWh.
- Scaling up from households is an assumption, and it can go wrong in either direction:
  - Stopping at step 1 undersizes a city with businesses and industry, by up to 2.6 times.
  - Dividing by the national 0.384 oversizes a city with no heavy industry by about 1.35 times (1,405 ÷ 1,040), and a homes-only suburb by 2.6 times.
  - Use the non-residential loads the problem gives. If it gives only household data, say which case you assumed.
- Size twice, once for energy (step 6) and once for the peak (step 7), and keep the larger answer. Nameplate is not output: the same annual energy needs four times as much solar nameplate as nuclear. Energy is not peak: enough nameplate for the year's energy can still fall short at the peak hour. Solar also produces nothing at night, so the evening peak still needs storage, other generation or coordinated DERs. That is the "control and coordination" finding [2].

**(2.6) Why power is transmitted at high voltage.** From P = IV, the line current is I = P / V. The power lost heating the line is

P_loss = I²R = (P / V)² R, so the fraction lost is f = P R / V²

| Variable | Represents | Units |
|---|---|---|
| P | Power being sent down the line | W |
| V | Line voltage | V |
| I | Current in the line | A |
| R | Total resistance of the line conductors | Ω |
| P_loss | Power turned into heat in the line | W |
| f | Fraction of the sent power that is lost | none |

**Worked example B:** send 100 MW through a line with R = 5 Ω.
- At 115 kV: I = 100×10⁶ / 115×10³ ≈ 870 A, so P_loss = 870² × 5 ≈ 3.78 MW (3.8%).
- At 345 kV: I ≈ 290 A, so P_loss ≈ 0.42 MW (0.42%).
- Tripling the voltage cuts the loss by 3² = 9. This is a simplified single-circuit model. Real grids are three-phase AC, but for fixed power and resistance the loss still scales as 1/V².

---

## 3. Water: infrastructure and natural resources

**What the sources say**
- The average American family uses more than 300 gallons of water a day at home, and about 70% of that is used indoors. The outdoor share is higher in dry regions [17].
- **Design flows (Town of Herndon, Virginia water main standards [22]):**
  - Maximum-day demand = 1.6 × average-day demand.
  - Peak-hour demand = 1.6 × maximum-day demand, which is 2.56 × average day.
  - Supply facilities (source, treatment, and the pumps that fill storage) are designed for maximum-day demand.
  - The distribution system is designed for peak-hour demand.
  - Storage tanks supply the difference during the peak hour.
  - Factors differ from city to city, so use the problem's factors when it gives them.
- The sheet asks what happens if a city could "monitor and control water usage by household." That would mean the water equivalent of AMI. Note that EIA's smart-meter counts cover electricity only; it does not publish data on water meters [13].

**Equations**

(3.1) Continuity (flow in a pipe): Q = A v, with A = π d² / 4

(3.2) Design flows: Q_MD = F_MD × Q_avg and Q_PH = F_PH × Q_avg

(3.3) Pump electrical power: P_elec = ρ g Q H / (η_p η_m)

Where (3.3) comes from: lifting mass m through height H takes work mgH. The mass flow rate is ρQ, so the power delivered to the water (hydraulic power) is ρgQH. Dividing by the pump efficiency η_p gives the shaft power the motor must supply. Dividing again by the motor efficiency η_m gives the electrical power drawn from the grid. The product η_p η_m is the "wire-to-water" efficiency. It is a product, not an average: a 70% pump on a 90% motor gives 63% [23].

| Variable | Represents | Units |
|---|---|---|
| Q | Volumetric flow rate | m³/s |
| A | Cross-sectional area of the pipe | m² |
| v | Average water velocity in the pipe | m/s |
| d | Inside diameter of the pipe | m |
| Q_avg | Average-day flow (annual use ÷ 365 days) | m³/s |
| Q_MD, Q_PH | Maximum-day and peak-hour design flows | m³/s |
| F_MD, F_PH | Maximum-day and peak-hour peaking factors (Herndon: 1.6 and 2.56) | none |
| P_elec | Electrical power the pump motor draws | W |
| ρ | Density of water (1,000 kg/m³) | kg/m³ |
| g | Gravitational acceleration (9.81 m/s²) | m/s² |
| H | Total head: height lifted plus friction losses, as an equivalent height | m |
| η_p | Pump efficiency (hydraulic power ÷ shaft power) | none (0–1) |
| η_m | Motor efficiency (shaft power ÷ electrical power) | none (0–1) |

**Worked example C: the same 50,000 households**
1. Average demand: 50,000 × 300 gal/day = 15 million gal/day. Convert with 1 gal = 3.785 L: about 56,780 m³/day. Divide by 86,400 s/day: Q_avg ≈ 0.657 m³/s. Like step 1 of Example A, this counts homes only. A full city also needs water for businesses, industry and public uses, and some is lost to leaks. Add those if the problem gives them.
2. Design flows (Herndon factors): Q_MD = 1.6 × 0.657 ≈ 1.05 m³/s, and Q_PH = 2.56 × 0.657 ≈ 1.68 m³/s.
3. Distribution main, sized for **peak hour** at v = 1.5 m/s (*assumed* design velocity): A = 1.68 / 1.5 ≈ 1.12 m², so d = √(4A/π) ≈ 1.19 m. Sizing from the average flow would give only 0.75 m, and the pipe would fail to deliver at the morning peak.
4. Pump station filling the storage tank, sized for **maximum day**, with H = 40 m, η_p = 0.75 and η_m = 0.90 (*assumed*): P_elec = 1,000 × 9.81 × 1.05 × 40 / (0.75 × 0.90) ≈ 611 kW of rated electrical power.
5. Energy uses the **average** flow. On an average day: 1,000 × 9.81 × 0.657 × 40 / 0.675 ≈ 382 kW, which is about 9.2 MWh per day. That load goes into the city's power budget in Section 2.
6. Smart angle:
   - Suppose household meters and smart irrigation cut outdoor use (30% of the total) by one third. Total demand falls 10%, a saving of 1.5 million gal/day. Because P ∝ Q, pumping energy also falls 10%, by about 0.9 MWh per day.
   - If smart scheduling also moves watering away from the peak hour, F_PH drops and the city can build smaller mains. That is the sheet's "outgrown infrastructure" problem in reverse.

**Rule of thumb:** size supply and pumps for the maximum day and distribution pipes for the peak hour. Use the average only for energy and yearly cost. Never size a pipe from the average.

---

## 4. Moving people and using land well

**What the sources say**
- **GAO [3]:** Houston uses cameras and Bluetooth sensors to measure traffic flow and adjust signal timing. Houston TranStar officials credit their success to both technology and personnel, not any single tool.
- **EPA Smart Location Mapping [10]** offers three tools:
  - the **Smart Location Database**, a nationwide dataset with more than 90 attributes (housing density, land-use diversity, neighborhood design, destination accessibility, transit service, employment, demographics);
  - the **Access to Jobs and Workers Via Transit** tool, which covers only metro areas whose transit agencies publish their schedules in the standard GTFS format;
  - the **National Walkability Index**.

**(4.1) Fundamental traffic relation [19][21]:** q = k v

**(4.2) Greenshields linear model [21]:** v = v_f (1 − k / k_j). This 1935 model assumes speed falls in a straight line from free-flow speed on an empty road to zero at jam density. It is a classroom simplification, not a measured law.

Substituting gives q = v_f k − (v_f / k_j) k². Setting dq/dk = v_f − 2 v_f k / k_j = 0 gives the maximum flow:

k* = k_j / 2, v* = v_f / 2, q_max = v_f k_j / 4

| Variable | Represents | Units |
|---|---|---|
| q | Flow: vehicles passing a point per hour, per lane | veh/h |
| k | Density: vehicles per km of lane | veh/km |
| v | Space-mean speed of the traffic | km/h |
| v_f | Free-flow speed (speed when the road is nearly empty) | km/h |
| k_j | Jam density (bumper-to-bumper, v = 0) | veh/km |
| k*, v* | Density and speed at which flow is greatest | veh/km, km/h |
| q_max | Capacity: the greatest possible flow per lane | veh/h |

**Worked example D:** with v_f = 90 km/h and k_j = 100 veh/km (*assumed*), q_max = 90 × 100 / 4 = 2,250 veh/h per lane, reached at 50 veh/km and 45 km/h. A corridor that must carry 9,000 veh/h at peak needs 9,000 / 2,250 = 4 lanes per direction. Alternatively, the city can move fewer cars by adding transit or improving signal timing.

**(4.3) EPA National Walkability Index [18]:** NWI = w/3 + x/3 + y/6 + z/6

| Variable | Represents | Units |
|---|---|---|
| NWI | Walkability score of a census block group | 1 (least) to 20 (most) |
| w | Rank score for street intersection density | 1–20 |
| x | Rank score for proximity to transit stops | 1–20 |
| y | Rank score for employment mix | 1–20 |
| z | Rank score for employment and household mix | 1–20 |

Each input is first ranked nationally into 20 groups. Categories: 1–5.75 least walkable; 5.76–10.5 below average; 10.51–15.25 above average; 15.26–20 most walkable.

**Worked example E:** w = 15, x = 10, y = 12, z = 18 gives 5 + 3.33 + 2 + 3 = 13.3, which is "above average."

---

## 5. Growth and money (AP Calc BC / AP Bio)

**(5.1) Logistic population growth:** dP/dt = r P (1 − P/K)

The solution is P(t) = K / (1 + A e^(−rt)), with A = (K − P₀) / P₀. The growth rate dP/dt is largest when P = K/2, where it equals rK/4. When that happens depends on where the city starts:
- **P₀ < K/2** (so A > 1): the fastest growth is still ahead, at t = ln(A) / r.
- **K/2 ≤ P₀ < K** (so 0 < A ≤ 1): ln(A)/r is zero or negative. The fastest growth has already passed and growth is slowing.
- **P₀ > K** (so −1 < A < 0): ln(A) is undefined, and there is no peak. The population *falls* toward K. This is the sheet's city that has outgrown its infrastructure.

| Variable | Represents | Units |
|---|---|---|
| P | Population at time t | people |
| t | Time since the start | years |
| r | Intrinsic growth rate | 1/year |
| K | Carrying capacity: the largest population the city's resources and infrastructure can support | people |
| P₀ | Population at t = 0 | people |
| A | Constant set by the starting population | none |

**Worked example F:** P₀ = 50,000, K = 200,000, r = 0.08/yr (*assumed*). Then A = 3 > 1, and P(10) = 200,000 / (1 + 3e^(−0.8)) ≈ 85,200. Growth peaks at 0.08 × 200,000 / 4 = 4,000 people/yr, at t = ln 3 / 0.08 ≈ 13.7 yr. To size utilities for K, convert people to households: 200,000 ÷ 2.53 ≈ 79,000 households [24]. Then use Examples A and C. Engineering lesson: design for K and build in phases. That is how you avoid the sheet's problem of infrastructure that is outgrown by the time it is finished.

**(5.2) Compound annual growth rate:** CAGR = (V_n / V_0)^(1/n) − 1

| Variable | Represents | Units |
|---|---|---|
| V_0 | Value at the start | e.g. US$ |
| V_n | Value after n years | e.g. US$ |
| n | Number of years | years |
| CAGR | Constant yearly growth rate that links V_0 to V_n | fraction per year |

**Worked example G:** Grand View Research puts the U.S. smart cities market at US$147.30 billion in 2024. It projects US$171.94 billion in 2025, growing to US$1,190.8 billion by 2033, a 27.4% CAGR [9]. Check: (1,190.8 / 171.94)^(1/8) − 1 ≈ 0.274.

**Trap:** market forecasts are estimates, not measurements. Grand View's own separate U.S. outlook page gives the 2024 value as US$147.3 *million*, a thousandfold conflict [9]. For physical quantities, prefer government data (EIA, DOE).

---

## 6. Data, privacy and policy (essay and presentation material)

**Data**
- **SmartCitiesWorld's open-data section [4]** tracks city data hubs and portals. Examples include Dublin's hub with dashboards and mapping tools, a regional data hub in the Memphis area, a new data platform in Darwin, and Dubai's updated data manual. India's housing ministry ran an Open Data Week in which 100 smart cities published datasets.
- **Data-Smart City Solutions [5]** is now housed at the Bloomberg Center for Cities at Harvard. Stephen Goldsmith founded it in 2012 with Bloomberg Philanthropies, and it began at the Harvard Kennedy School's Ash Center. It serves as a central resource on data-driven local government: open data, predictive analytics, civic-engagement technology, and combining cross-agency data with community data.

**GAO-25-107019 (April 2025) [3]: the key policy source**
- **Scope:** transportation and law-enforcement technologies, including traffic cameras, Bluetooth sensors, license plate readers and gunshot detection.
- **Benefits reported:** Houston's signal timing, and license plate readers that find stolen vehicles.
- **Problems:**
  - The technologies can be costly.
  - Benefits are hard to prove, because agencies use several technologies at once and results are hard to attribute to any one of them.
  - Gunshot detection may shift gun crime elsewhere rather than reduce it.
  - Cities may collect large amounts of data, some bought from data brokers, and some of it can identify individuals. That raises privacy and civil-liberties concerns.
  - Residents are often told the benefits but not the risks.
- **Policy options:**
  1. Facilitate collaboration to evaluate technology use.
  2. Increase transparency when procuring and using smart technologies.
  3. Develop and share data-governance practices or standards.
  - Or keep the status quo.

**License plate readers**
- **GovTech [7]:** privacy advocates sued in Illinois, arguing that plate cameras violate constitutional protection against unreasonable search. Yet in 2022 a plate camera helped catch a teenager driving a stolen car who was accused of fatally shooting a young mother in Morris, Illinois.
- **ZME Science [6]:** Jess Reia, a technology-policy and data-governance scholar, argues that ALPRs began as a national-security tool and are becoming surveillance infrastructure that can track everyone. AI makes them far more powerful. Reia links their expansion to efforts to target immigrant and transgender communities and to monitor protests.
- **Brennan Center [20]:** generally far below 1% of the cars ALPRs scan are connected to any crime or wrongdoing.

**Privacy toolkit: Future of Privacy Forum [8].** FPF maps smart-city technologies, such as air-quality streetlights and demand-responsive buses, to their privacy risks. Its mitigations are privacy programs, transparency and consent, de-identification, vendor management, and data minimization.

**(6.1) Why a "99% accurate" camera gives mostly false alerts (Bayes' theorem)**

P(H | A) = P(A | H) P(H) / [ P(A | H) P(H) + P(A | not H) (1 − P(H)) ]

| Variable | Represents | Units |
|---|---|---|
| H | Event: the scanned car really is on the wanted list | — |
| A | Event: the system raises an alert | — |
| P(H) | Base rate: share of scanned cars that are wanted | probability |
| P(A \| H) | Chance a wanted car triggers an alert (sensitivity) | probability |
| P(A \| not H) | Chance an innocent car triggers an alert (false-positive rate) | probability |
| P(H \| A) | Chance that an alert is real | probability |

**Worked example H:** P(H) = 0.001, which fits "far below 1%" [20]. P(A|H) = 0.99 and P(A|not H) = 0.005 (*assumed*). Then P(H|A) = 0.00099 / (0.00099 + 0.004995) ≈ 0.17. About 83% of alerts would be false, which is why a human should verify an alert before police act on it.

**Essay angle for the sheet's "Consider the following."** Tracking where people travel and metering each household's water both give engineers the demand data they need: right-sized transit, leak detection, and lower peaking factors for pipes and power. But they are exactly the identifiable data GAO and the ALPR writers warn about. A defensible design:
- collect the minimum and aggregate it (trip counts by zone, not individual tracks);
- keep data for a short, published period;
- de-identify before sharing it as open data;
- tell residents the risks as well as the benefits;
- measure whether the technology actually works before expanding it [3][8].

---

## 7. Quick practice (answers below)

1. A wind farm must deliver 900 GWh per year. What nameplate capacity is needed?
2. A line's voltage is raised from 138 kV to 345 kV, carrying the same power. By what factor does I²R loss fall?
3. What is the CAGR of smart grid investment from $3.4 billion (2014) to $6.4 billion (2018)?
4. A logistic city has K = 300,000 and r = 0.06/yr. What is its fastest growth rate? If P₀ = 200,000, is that peak ahead of it or behind it?
5. A pump's head doubles while Q, η_p and η_m stay the same. What happens to its electrical power?
6. A town's homes use 400 GWh of electricity a year, and homes are 38.4% of its load. What is the town's average total demand?
7. Smart irrigation lowers a city's peak-hour factor from 2.56 to 2.0 at the same design velocity. By what factor does the required main diameter change?
8. The Example A city (peak 292 MW, 5% losses, needs 1,479,000 MWh a year) plans 250 MW of nuclear. Does it pass the energy check? The peak check?

**Answers:**
1. 900,000 MWh ÷ (0.332 × 8,760 h) ≈ 309 MW.
2. (345/138)² = 6.25 times smaller.
3. (6.4/3.4)^(1/4) − 1 ≈ 17.1% per year.
4. rK/4 = 4,500 people/yr. P₀ = 200,000 > K/2 = 150,000, so the peak is already behind it: A = 0.5 and ln(0.5)/0.06 ≈ −11.6 yr.
5. It doubles, because P ∝ H.
6. 400 ÷ 0.384 ≈ 1,042 GWh; 1,042,000 MWh ÷ 8,760 h ≈ 119 MW.
7. d ∝ √Q, so √(2.0/2.56) ≈ 0.88, about 12% narrower.
8. Energy: 250 × 0.930 × 8,760 ≈ 2,037,000 MWh, more than 1,479,000, so it passes. Peak: 250 MW is below 292 ÷ 0.95 ≈ 307 MW, so it fails by about 57 MW before any reserve margin.

---

## Citation page

**How these were consulted.** Direct page downloads were blocked from the environment used to research this guide. Every page below was therefore consulted on October 12 or October 21, 2026 through web-search results: page titles, excerpts and summaries of the page text. Before quoting a figure in your essay or presentation, open the page and confirm it.

**Count:** 24 cited pages from 17 distinct websites. Sources 1–10 are your 10 websites. Sources 11–24 add 7 new websites: eia.gov, web.mit.edu, brennancenter.org, arxiv.org, herndon-va.gov, pumpsandsystems.com and census.gov. The other additional pages are on energy.gov and epa.gov, which were already among your sources.

**Sources you provided**

1. InfraJournal. (n.d.). *Smart grids for energy and the smart cities: a vital combination.* https://www.infrajournal.com/en/w/smart-grid-for-energy-and-the-smart-city
2. U.S. Department of Energy. (2022). *2020 Smart Grid System Report.* https://www.energy.gov/sites/default/files/2022-05/2020%20Smart%20Grid%20System%20Report_0.pdf. The key findings were read on DOE Office of Electricity's summary page for the same report: https://www.energy.gov/oe/articles/2020-smart-grid-system-report. The investment figures came from excerpts of the report's executive summary.
3. U.S. Government Accountability Office. (2025, April). *Smart Cities: Technologies and Policy Options to Enhance Services and Transparency* (GAO-25-107019). https://www.gao.gov/products/gao-25-107019. Full report: https://www.gao.gov/assets/gao-25-107019.pdf
4. SmartCitiesWorld. (n.d.). *Open data* [topic page]. https://www.smartcitiesworld.net/open-data
5. Bloomberg Center for Cities at Harvard University. (n.d.). *Data-Smart City Solutions.* https://www.cities.harvard.edu/initiatives/data-smart-city-solutions/
6. Reia, J. (2026). *I am a tech policy scholar and the AI license plate cameras are a civil liberties nightmare.* ZME Science. https://www.zmescience.com/science/news-science/i-am-a-tech-policy-scholar-and-the-ai-license-plate-cameras-are-a-civil-liberties-nightmare/
7. Government Technology. (n.d.). *License plate scanners solve crimes, create privacy concerns* (syndicated news story). https://www.govtech.com/public-safety/license-plate-scanners-solve-crimes-create-privacy-concerns. Only the opening of the story was available in search excerpts.
8. Future of Privacy Forum. (n.d.). *Smart cities* [blog]. https://fpf.org/blog/smart-cities/. This exact URL did not appear in search results. The sheet's title for it, "Shedding Light on Smart City Privacy," matches FPF's 2017 post, which is where the content was consulted: https://fpf.org/blog/shedding-light-smart-city-privacy/
9. Grand View Research. (n.d.). *U.S. smart cities market size, share & trends analysis report.* https://www.grandviewresearch.com/industry-analysis/us-smart-cities-market-report. The units conflict was found on Grand View's outlook page: https://www.grandviewresearch.com/horizon/outlook/smart-cities-market/united-states
10. U.S. Environmental Protection Agency. (n.d.). *Smart Location Mapping.* https://www.epa.gov/smartgrowth/smart-location-mapping

**Additional sources**

11. U.S. Energy Information Administration. (n.d.). *Electricity explained: Use of electricity.* https://www.eia.gov/energyexplained/electricity/use-of-electricity.php
12. U.S. Department of Energy, Grid Deployment Office. (2024). *Microgrid overview* [fact sheet]. https://www.energy.gov/sites/default/files/2024-02/46060_DOE_GDO_Microgrid_Overview_Fact_Sheet_RELEASE_508.pdf
13. U.S. Energy Information Administration. (n.d.). *How many smart meters are installed in the United States, and who has them?* https://www.eia.gov/tools/faqs/faq.php?id=108&t=3
14. U.S. Energy Information Administration. (n.d.). *How much electricity is lost in electricity transmission and distribution in the United States?* https://www.eia.gov/tools/faqs/faq.php?id=105&t=3
15. U.S. Energy Information Administration. (n.d.). *How much electricity does an American home use?* https://www.eia.gov/tools/faqs/faq.php?id=97&t=3
16. U.S. Energy Information Administration. (n.d.). *State Energy Data System, Table F38: Capacity factors and usage factors at electric generators: total (all sectors), 2023.* https://www.eia.gov/state/seds/sep_fuel/html/pdf/fuel_cf.pdf. The figures used are in the table's United States row. Individual state rows can be volatile, even above 100%, where a state has few generators. EIA reissues this table every year, so a newer edition may show a later year under a different table number.
17. U.S. Environmental Protection Agency, WaterSense. (n.d.). *How we use water.* https://www.epa.gov/watersense/how-we-use-water. Excerpts were read from EPA's archived copy: https://19january2025snapshot.epa.gov/watersense/how-we-use-water
18. U.S. Environmental Protection Agency. (2021). *National Walkability Index: Methodology and user guide.* https://www.epa.gov/sites/default/files/2021-06/documents/national_walkability_index_methodology_and_user_guide_june2021.pdf
19. Wu, C. (2024). *Macroscopic traffic models: Traffic flow theory* (Lecture 5 slides, MIT 1.041/1.200 Transportation: Foundations and Methods, Spring 2024). https://web.mit.edu/1.041/www/lectures/L5-traffic-flow-theory-2024sp.pdf. Course page: https://web.mit.edu/1.041/www/. The Spring 2026 version of the lecture is posted at https://web.mit.edu/1.041/www/lectures/L5-traffic-flow-theory-2026sp.pdf
20. Díaz, Á., & Levinson-Waldman, R. (2020). *Automatic license plate readers: Legal status and policy recommendations for law enforcement use.* Brennan Center for Justice. https://www.brennancenter.org/our-work/research-reports/automatic-license-plate-readers-legal-status-and-policy-recommendations
21. Maerivoet, S., & De Moor, B. (2005). *Traffic flow theory* (arXiv:physics/0507126). arXiv. https://arxiv.org/abs/physics/0507126
22. Town of Herndon, Virginia, Department of Public Works. (n.d.). *Water main design and construction standards.* https://herndon-va.gov/home/showpublisheddocument/3417/635918362471570000
23. Pumps & Systems. (n.d.). *How to define & measure centrifugal pump efficiency: Part 1.* https://www.pumpsandsystems.com/how-define-measure-centrifugal-pump-efficiency-part-1
24. U.S. Census Bureau. (n.d.). *QuickFacts: United States* (persons per household, 2020–2024: 2.53). https://www.census.gov/quickfacts/fact/table/US/HSD310223

Several equations carry no citation: P = IV, I²R, energy and power, load factor, continuity, logistic growth, CAGR and Bayes' theorem. These are standard results from AP Physics C, AP Calculus BC and AP Biology, and each one is derived or defined where it appears.
