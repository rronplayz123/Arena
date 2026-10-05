# TSA TEAMS 2027: Engineering a Smarter World
## Study Guide: Autonomous Delivery Robots

*Written for a team of high school seniors taking AP Calculus BC, AP Physics C and AP Biology. Bracketed numbers such as [3] point to the Citation Page at the end. The guide uses 24 sources: the six "Explore More" sources from the official sheet plus 18 others.*

---

## How to use this guide

The section sheet says your team will be **"calculating the characteristics of a delivery robot fleet, including impacts on delivery times, optimal pathfinding through pedestrian traffic, weather effects, and maximum payload stability."** This guide is organized around those four tasks.

1. **Part 1 is one full worked example.** It follows one realistic campus delivery robot from start to finish: forces, power, trip time, fleet size, sensing, stopping, tipping, weather, cost, and a drone comparison. If you only have an hour, study this part.
2. **Part 2 explains the ideas** behind the example (what the robots are, how they sense and navigate, energy, economics, regulation and public acceptance).
3. **Part 3 is the equation sheet.** It defines every variable and gives its units.
4. **Part 4 has practice problems** with answers.
5. **Part 5 is a reading plan for the six required sources**: what each says, key numbers and likely questions.
6. **The Citation Page** lists all 24 sources and says how each one was consulted.

### Assumptions
- "Sites" means distinct web sources, each with its own working URL. The guide uses 24, which is more than the 15 required, and that count includes all six sheet sources.
- The sheet gave titles but no URLs, so each title was matched to its official or publisher page (see Part 5).
- Some worked-example inputs are engineering estimates and not published specifications: rolling-resistance coefficient, frontal area, center-of-mass height, track width, drivetrain efficiency and campus demand. Each one is marked **(assumed)**. Published numbers carry a citation.
- **How sources were consulted.** The research tool could not open pages directly because its network blocked direct page downloads (this was re-tested during revision and still applied). Every source was therefore consulted through web-search indexing of that exact page: the title, the abstract or summary, and passages the search engine extracted from the page body. All URLs are the canonical addresses those searches returned.
- **Which numbers were checked, and how.** Every specific figure this guide quotes from a source (for example 650 robots, 15%, 188 flights, 0.08 MJ/km, 70 g CO₂e, 94%, $2.00–$2.50 vs. $11.00–$12.00, 483 consumers, 692 respondents, the Part 108 date and limits) was matched against text the search engine extracted from that source's own page. Figures that could not be matched this way were left out. Numbers marked **(assumed)** are engineering estimates, not sourced facts.
- **Your job before the competition.** Part 5 gives you a reading plan for the six sheet sources: what each one says, the numbers worth memorizing and the questions it could support. Use it to skim them quickly; it does not replace reading them, because the judges' questions may be drawn from them.

---

## Part 1: One delivery, worked from start to finish

### The scenario
A university runs a fleet of six-wheeled sidewalk robots like the Starship robot. Published characteristics of that robot, as reported by the manufacturer and compiled by a specification database [8] (treat them as approximate: models differ by generation):

| Quantity | Value | Symbol |
|---|---|---|
| Empty mass | ≈ 23 kg | m_r |
| Maximum cargo | 10 kg | m_p |
| Top speed | 6 km/h ≈ 1.667 m/s (walking pace) | v |
| Battery | 1260 Wh, about 12 h of driving | E_batt |
| Sensors | ~9+ cameras (360°), ultrasonic sensors, GNSS/GPS, IMU (some versions also radar and time-of-flight cameras) | — |

A student orders a 10 kg grocery bag. The store is **1.2 km** from the dorm. Classes have just let out, so one 400 m stretch is crowded.

---

### Step 1: Forces on the loaded robot (AP Physics C: Newton's laws)

Total mass: m = m_r + m_p = 23 + 10 = **33 kg**. Weight: W = mg = 33 × 9.81 = **323.7 N**.

**Rolling resistance** [15]: F_rr = C_rr · N
- F_rr = rolling resistance force (N)
- C_rr = rolling resistance coefficient, dimensionless. **(assumed)** 0.02 for small hard wheels on concrete.
- N = normal force (N). On level ground N = mg.

F_rr = 0.02 × 323.7 = **6.47 N**

**Aerodynamic drag** (NASA drag equation [14]): D = ½ · C_d · ρ · V² · A
- D = drag force (N)
- C_d = drag coefficient, dimensionless. **(assumed)** 1.0 for a boxy body.
- ρ = air density (kg/m³), ≈ 1.2 at room temperature
- V = speed of the air relative to the robot (m/s)
- A = frontal (reference) area (m²). **(assumed)** 0.3 m².

Still air, V = 1.667 m/s: D = 0.5 × 1.0 × 1.2 × 1.667² × 0.3 = **0.50 N**. At walking speed, drag hardly matters.

**Grade (hill) force**: F_g = mg sin θ
- θ = slope angle. A 5% grade means tan θ = 0.05, so θ ≈ 2.86°.

F_g = 323.7 × sin(2.86°) = **16.2 N**. Going uphill, gravity takes about 2.5 times as much force as rolling resistance.

**Lesson:** for a slow sidewalk robot, hills and surface condition matter most. Drag only matters in strong wind (Step 7).

---

### Step 2: Power and energy (AP Calc BC: E = ∫P dt)

Mechanical power at the wheels: **P = F · v**
- P = power (W), F = total resisting force (N), v = robot speed (m/s)

On level ground in still air: P = (6.47 + 0.50) × 1.667 = **11.6 W**.
Electrical power from the battery: P_elec = P / η. With drivetrain efficiency η = 0.7 **(assumed)**, P_elec ≈ **16.6 W**.

**Check against the published number.** 1260 Wh over about 12 h of driving [8] is an average of 1260 / 12 ≈ **105 W**. That is more than six times the level-ground traction power. The rest goes to computing, cameras and other sensors, communications, accelerating after every stop, climbing hills and curb ramps, and in winter, heating. When you estimate robot energy, **do not model only the wheels**.

Energy over a trip with changing power: E = ∫₀ᵀ P(t) dt. If power is roughly constant, this simplifies to E ≈ P_avg · T.

---

### Step 3: Delivery time through pedestrian traffic

Split the 1.2 km route into segments:

| Segment | Distance | Speed | Time |
|---|---|---|---|
| Open sidewalk | 800 m | 1.667 m/s | 480 s |
| Crowded stretch (class change) | 400 m | 1.0 m/s **(assumed)** | 400 s |
| Two crosswalk waits | — | — | 2 × 45 s = 90 s **(assumed)** |
| **Outbound total** | 1200 m | | **970 s ≈ 16.2 min** |

The same 1.2 km on a clear route takes 720 s (12 min). The crowd and the crossings add **35%**.

Full **cycle time** for one robot on one order:

| Phase | Time |
|---|---|
| Loading at store **(assumed)** | 2.0 min |
| Outbound | 16.2 min |
| Customer pickup wait **(assumed)** | 3.0 min |
| Return trip, empty and uncrowded | 12.0 min |
| **Cycle time W** | **33.2 min** |

Energy per delivery. The 105 W from Step 2 is an average **while driving** (1260 Wh over about 12 h of driving), so apply it only to the driving minutes, not to the 5 min parked for loading and pickup:
- Driving time: 16.2 + 12.0 = **28.2 min** = 0.470 h
- Driving energy: E_drive ≈ 105 W × 0.470 h ≈ **49 Wh** (≈ 0.18 MJ)
- Parked energy: while parked the wheels draw nothing, but computers and sensors stay on. With an idle draw of 30 W **(assumed)**, 5 min parked adds 30 × (5/60) ≈ **2.5 Wh**.
- Total: E ≈ 49 + 2.5 ≈ **52 Wh** (≈ 0.19 MJ) per delivery.

One charge covers about 1260 / 52 ≈ **24 deliveries** (about 25 if you ignore the parked draw: 1260 / 49 ≈ 25.7). **Lesson:** multiply each power by the time it actually applies (this is E = ∫P dt done piecewise), not one average power by the whole cycle time. Doing the latter (105 W × 33.2 min ≈ 58 Wh) overstates energy and understates deliveries per charge (≈ 21).

---

### Step 4: Fleet size (Little's Law)

Little's Law [17]: **L = λW**
- L = average number of items in the system. Here, robots busy with an order.
- λ = average arrival rate. Here, orders per hour.
- W = average time each item spends in the system. Here, cycle time in hours.

The law holds for any arrival pattern or service-time distribution, as long as the system is stable over the long run [17].

Peak demand λ = 60 orders/h **(assumed)**, and W = 33.2 min = 0.553 h:
L = 60 × 0.553 = **33.2 robots busy on average**.

Robots also need charging, cleaning and repairs. If each robot is available 85% of the time **(assumed)**, the fleet needed is 33.2 / 0.85 = 39.1, so round up to **40 robots**.

**Sensitivity.** Each minute you cut from cycle time removes λ × (1/60) h = 1 busy robot at 60 orders/h. Faster loading, shorter pickup waits and better routing around crowds (Step 5) directly shrink the fleet.

---

### Step 5: Optimal pathfinding (A* search)

The robot's map is a graph. Nodes are intersections and doorways. Edges are sidewalk links, and each **edge cost is travel time**, so crowds simply make edges more expensive. A* picks the next node with the lowest
**f(n) = g(n) + h(n)** [16]
- g(n) = actual cost from the start to node n
- h(n) = estimated cost from n to the goal (the heuristic)
- f(n) = estimated total cost of the cheapest path through n

A* was introduced by Hart, Nilsson and Raphael at SRI in 1968 [16]. It is guaranteed to find the optimal path if h is **admissible**: h(n) ≤ h*(n), the true remaining cost, for every node [16]. For travel time, a safe heuristic is h(n) = straight-line distance ÷ top speed. Every real path is at least that long, and the robot can't go faster than top speed.

**Worked graph** (costs in seconds; S = store, G = dorm):

| Edge | Cost | Note |
|---|---|---|
| S→A | 60 | |
| S→B | 40 | |
| A→G | 50 | |
| B→C | 30 | |
| C→G | 60 | |
| B→G | 110 | crowded plaza |

Heuristic values: h(S)=90, h(A)=45, h(B)=80, h(C)=50, h(G)=0. Each is at most the true remaining cost (A: 50; B: min(110, 90) = 90; C: 60; S: 110), so the heuristic is admissible.

1. Expand S. Add A with g=60, f=60+45=**105**, and B with g=40, f=40+80=**120**.
2. Lowest f is A. Expand A. Add G with g=110, f=110+0=**110**.
3. Lowest f is G (110 < 120). Goal reached. **Path S→A→G, 110 s.**

A* never expanded C. The heuristic let it skip that part of the graph. When crowd levels change (sensors report the plaza clearing), the edge costs change and the robot **replans**. That is why real fleets combine a global planner like A* with fast local obstacle avoidance.

**Local avoidance: the social force model** [18]. Pedestrians (and robots that must move like them) can be modeled as if "social forces" act on them:

m_i · dv_i/dt = f_i⁰ + Σ_{j≠i} f_ij + Σ_w f_iw,  with  f_i⁰ = m_i · (v_i⁰ e_i⁰ − v_i) / τ

- m_i = mass of agent i; v_i = its current velocity
- f_i⁰ = driving force pulling the agent toward its desired velocity
- v_i⁰ = desired speed; e_i⁰ = unit vector toward the destination
- τ = relaxation time (how quickly the agent returns to its desired velocity)
- f_ij = repulsive force from agent j. It grows exponentially as the gap d_ij shrinks: A·exp[(D − d_ij)/B], where A sets strength, B sets range and D is the sum of the two body radii.
- f_iw = repulsive force from walls or obstacles w

Robots use models like this to predict where people will step next and pick a path that does not cut them off.

---

### Step 6: Sensing and stopping distance

**Ultrasonic sensors** measure the round-trip time of an echo [24]:
**d = v_s · t / 2**,  with **v_s ≈ 331.3 + 0.606·T_C**
- d = distance to the obstacle (m); t = round-trip echo time (s)
- v_s = speed of sound (m/s); T_C = air temperature (°C)
- The ÷2 is there because the sound travels out and back.

**LiDAR** uses the same idea with laser light [19]: d = c·t/2, where c = 3.00×10⁸ m/s. An object 10 m away returns a pulse in t = 2(10)/(3×10⁸) = **66.7 ns**, so LiDAR electronics must time events in nanoseconds.

**Stopping distance**: d_stop = v·t_r + v²/(2a)
- t_r = perception and reaction latency (s): **(assumed)** 0.3 s for the sensing and computing pipeline
- a = braking deceleration (m/s²): **(assumed)** 2.0 m/s²

d_stop = 1.667(0.3) + 1.667²/(2·2.0) = 0.50 + 0.69 = **1.19 m**.

So the robot must detect obstacles well beyond 1.19 m. At 20 °C the echo from 1.19 m returns after t = 2(1.19)/343.4 = **6.93 ms**.

**GPS is not precise enough on its own.** GPS.gov states that the U.S. government commits to broadcasting the signal in space with a daily global average **user range error (URE) of ≤ 2.0 m (95% probability)**, and that actual performance is typically much better (global average URE ≤ 0.643 m, 95% of the time, on April 20, 2021) [13]. *Careful:* older documents (the 2008 GPS SPS Performance Standard) quote the earlier, looser commitment of ≤ 7.8 m (95%); the current GPS.gov commitment is the tighter 2.0 m figure. Either way, URE is **not** your position accuracy: GPS.gov stresses that the commitment applies to the signal, not to receivers. A receiver's position error is larger than the URE because of geometry, buildings and multipath. A sidewalk is only a couple of meters wide, so robots **fuse** GPS with cameras, IMU and wheel odometry to know which side of the curb they are on. That is why the sheet stresses "continually improving satellite-based location systems" together with obstacle-avoidance sensors.

---

### Step 7: Weather effects (same robot, same route)

**(a) Headwind.** In a 10 m/s headwind, the relative air speed is V = 10 + 1.667 = 11.67 m/s.
D = 0.5 × 1.0 × 1.2 × 11.67² × 0.3 = **24.5 N**. That is about 49 times the still-air drag and more than all the other level-ground forces combined. Traction power rises to (6.47 + 24.5) × 1.667 ≈ 52 W.

**(b) Cold air and ultrasonic error.** At −10 °C, v_s = 331.3 − 6.06 = 325.2 m/s. A real obstacle 1.19 m away echoes after 7.32 ms. A sensor that still assumes 343.4 m/s computes 343.4 × 0.00732 / 2 = **1.26 m**, which overestimates the distance by 5.6%. The robot thinks it has more room than it does. Temperature compensation fixes this [24].

**(c) Snow.** Snow raises rolling resistance. With C_rr = 0.08 **(assumed)**, F_rr = 25.9 N, four times the dry value, and range drops accordingly. Real-world check: in its 2025 "one million deliveries in Finland" release, Starship reports more than 650 robots operating across about 80 Finnish towns and cities, including Rovaniemi in Lapland. It credits a "snow mode," winter tires, special motor-control software, snow-aware routing and "snow pile detection," and says advances in winter operations (AI and hardware) raised delivery efficiency by as much as 15% [9]. *These are the company's own reported figures, not an independent measurement; quote them as "Starship reports…".*

**(d) Rain, glare and fog** degrade cameras and LiDAR. That is one reason robots carry several kinds of sensors (cameras, ultrasonic, radar) [8].

---

### Step 8: Maximum payload stability

**Static tipping.** A wheeled robot tips when its center of mass (COM) moves outside the **support polygon**, the area enclosed by its ground contact points. The **static stability margin** is the distance from the projected COM to the nearest edge of that polygon. A larger margin means a more stable robot. The result below follows from balancing torques about the downhill wheel line, as in AP Physics C.

For a side slope, the critical tipping angle is:
**tan θ_tip = (w/2) / h**
- w = track width, the distance between left and right wheel contact lines (m): **(assumed)** 0.50 m
- h = height of the combined COM above the ground (m)

Combined COM height (weighted average): **h = (m_r h_r + m_p h_p) / (m_r + m_p)**
- h_r = empty robot COM height: **(assumed)** 0.20 m (batteries sit low)
- h_p = cargo COM height: **(assumed)** 0.40 m

| Case | h (m) | θ_tip |
|---|---|---|
| Empty | 0.200 | arctan(0.25/0.200) = **51.3°** |
| 10 kg cargo | (23·0.20 + 10·0.40)/33 = **0.261** | arctan(0.25/0.261) = **43.8°** |

Cargo raised the COM and cut the tipping angle by 7.5°. Real hazards are much milder (curb ramps, about 5%), so a low, wide robot has a large margin. That is deliberate: the design is "small, low to the ground, and slow" [8].

**Turning.** In a turn, the robot tips when lateral acceleration a_lat > g(w/2)/h = 9.81 × 0.959 = 9.4 m/s². At 1.667 m/s that would need a turn radius r = v²/a = 0.30 m, so sidewalk robots are effectively turn-proof. A **tall drone payload** or a **taller road robot** behaves very differently.

**Cargo sliding.** Unsecured cargo slides during braking if a > μ_s·g, where μ_s is the static friction coefficient between cargo and bin. With μ_s = 0.3 **(assumed)**, the limit is 2.94 m/s². That is why Step 6 used a = 2.0 m/s²: braking harder would shift the soup.

---

### Step 9: Cost per delivery

The sheet's ITS source reports, from an autonomous delivery operator in Ann Arbor, Michigan, **$2.00–$2.50 per package by robot vs. $11.00–$12.00 by a human**, which is "80 percent less" [6].
Check with midpoints: (11.50 − 2.25) / 11.50 = **80.4%** ✔.

**Watch the fine print.** The ITS entry says that operator designed its robot to run **on the road instead of the sidewalk** (it is Refraction AI's bike-lane REV-1 [23]). So the 80% figure is a road-robot number. Using it for a sidewalk fleet is an assumption, which is how it is used below.

For our campus fleet, *if* sidewalk robots achieve similar per-package costs **(assumed)**, about 300 orders a day would save roughly 300 × $9.25 ≈ **$2,775 per day** compared with human couriers, before counting the robots' capital cost, remote supervisors and maintenance.

---

### Step 10: Same order by drone

**Hover power** (ideal, momentum theory) [20]: **P = T^{3/2} / √(2ρA)**
- P = ideal induced power (W); T = thrust (N), which equals mg in hover
- ρ = air density (kg/m³); A = total rotor disk area (m²)

For a quadcopter with four rotors of radius 0.15 m **(assumed)**: A = 4π(0.15)² = 0.283 m².

| Total mass | T = mg | P_ideal |
|---|---|---|
| 3.0 kg (no cargo) | 29.4 N | **194 W** |
| 3.5 kg (0.5 kg cargo) | 34.3 N | **244 W** |

Because **P ∝ m^{3/2}**, a 17% heavier drone needs (3.5/3)^{1.5} = 1.26 times the power, or **26% more**. Real rotors are less than ideal, so actual power is higher still. Drones carry light items. A 10 kg grocery bag is a ground-robot job.

**Measured data (peer-reviewed, Carnegie Mellon, *Patterns* 2022):** the authors combined **188 quadcopter test flights** with first-principles modeling. Their model gives about **0.08 MJ/km** and **70 g CO₂e per package** (U.S. electricity) for a 0.5 kg package, and **0.33 MJ per package**, which can be up to **94% lower** energy per package than conventional delivery modes [12]. These are the paper's abstract-level headline results; the "up to" means best case vs. the least efficient comparison. Over our 2.4 km round trip: 0.08 × 2.4 ≈ 0.19 MJ. That is roughly comparable to the sidewalk robot's ≈ 0.19 MJ per delivery (Step 3), but the drone carried one-twentieth of the cargo.

**Headwind effect on a drone:** with a 20 m/s airspeed into an 8 m/s headwind, ground speed is 12 m/s. A 2 km leg takes 167 s instead of 100 s, and the drone burns energy the whole time it is airborne.

### What the worked example taught
1. **Time:** crowds and crossings, not top speed, set delivery time (+35% here). Cycle time sets fleet size through L = λW.
2. **Pathfinding:** model crowds as higher edge costs, use A* with an admissible heuristic, and replan as conditions change.
3. **Weather:** wind matters through V², cold through the speed of sound, and snow through C_rr.
4. **Stability:** keep the COM low and the track wide. Payload raises h and lowers θ_tip. Braking is limited by cargo friction, not by tipping.
5. **Energy and cost:** wheels use little power, computing and sensing use a lot. A road-going delivery robot was reported to cut cost per package by about 80% [6]. Drones beat vans for small single parcels but scale poorly with weight (m^{1.5}).

---

## Part 2: Background ideas

### 2.1 Types of automated delivery vehicles
The U.S. DOT's state-of-the-practice scan (*Emerging Automated Urban Freight Delivery Concepts*, FHWA-JPO-20-825) [1] groups the concepts into:
- **Sidewalk delivery robots / personal delivery devices (PDDs):** wheeled or legged, small, slow, carry one order.
- **Road automated delivery vehicles (road ADRs):** car-sized or smaller vehicles without a driver that run in traffic lanes or bike lanes. Refraction AI's three-wheeled REV-1 in Ann Arbor carried up to 100 lb over trips of about 0.5–2.5 miles in bike lanes [23].
- **Aerial drones (UAS):** fast and unaffected by traffic, but payload-limited. Zipline's newer P2 platform carries about 8 lb within a roughly 10-mile service radius and lowers packages on a tether. Its older P1 platform dropped about 4 lb by parachute [22].
- **Hybrid "mothership" concepts:** a van or truck carries robots or launches drones near the customers.
- **Automated trucks and vans** for the line-haul or "middle-mile" part of delivery.

### 2.2 Why companies want them: the last-mile problem
The **last mile**, from the local hub to the doorstep, is the most expensive part of delivery because it is labor-intensive and involves single small parcels. The sheet says firms are "investing billions" to cut these costs. The ITS figure of 80% savings for a road-going robot in Ann Arbor [6] shows the incentive.

### 2.3 Do robots and drones reduce trucks, energy and congestion? (the sheet's question)
Research by Figliozzi and colleagues at Portland State gives a careful "it depends":
- **Sidewalk robots** can save cost and time in some scenarios and **can significantly reduce on-road travel per package**, because they move vehicle trips off the road [11].
- **Road robots** can save money, but in every scenario studied they **increase vehicle-miles per customer**, which could add congestion [10, 11].
- Comparing drones, sidewalk robots, road robots and electric vans: **sidewalk robots are best for small service areas, drones for low-density or time-critical deliveries, and road robots beat electric vans only when there are few customers** [10].
- **Drones** are more CO₂-efficient than diesel vans for small single parcels [12]. However, when customers can be grouped into one route, drones are **not** better than electric vans or cargo tricycles. **Manufacturing and disposal** emissions for drones are significant [10, 12].

**Exam-ready answer:** individual drone delivery can reduce truck trips and energy for light, urgent or rural deliveries. For dense urban routes, a consolidated electric van (possibly launching sidewalk robots) usually wins. Rebound effects, such as more frequent small orders, can erase the gains.

### 2.4 How a robot navigates a crowded sidewalk (the sheet's other question)
1. **Perception:** cameras (object detection with machine learning), ultrasonic sensors (close range), radar, and LiDAR or time-of-flight cameras (3-D range) [8, 19].
2. **Localization:** GNSS/GPS gives a rough position: the signal-in-space error is committed at ≤ 2.0 m (95%) [13], and receiver error is larger near buildings. Fusing it with IMU, wheel odometry and visual landmarks places the robot precisely on the sidewalk.
3. **Mapping:** pre-built maps of sidewalks, curb ramps and crosswalks. Robots often learn routes in a new area before serving it.
4. **Global planning:** graph search such as A* over the map, with time-based edge costs [16].
5. **Local planning and prediction:** predicting pedestrians' motion (for example with social-force models [18]), yielding, slowing in crowds, and stopping within the sensor range (Step 6).
6. **Remote supervision:** PDD laws generally require that a human can monitor and take over remotely [3]. Robots ask for help at tricky crossings.

### 2.5 Rules of the road (and sidewalk)
- **Sidewalk robots.** The Pedestrian and Bicycle Information Center (PBIC), a U.S. DOT-supported clearinghouse, describes the **typical state-law definition of a PDD**: electrically powered, mainly carries property on sidewalks or crosswalks, **under 120 lb excluding cargo, maximum 10 mph**, with automated driving technology and **remote supervision** [3]. Limits differ by state. Some laws cap weight at 80 lb, and South Carolina's 2024 bill used 150 lb with size limits of 36 in long and 30 in wide [7]. PBIC keeps a **PDD Legislative Tracker** of state laws covering physical and operational limits, where PDDs may operate, human oversight and right-of-way [7]. Pedestrian concerns include sidewalk blocking, accessibility for wheelchair users and people with low vision, and conflicts in bike lanes [3].
- **Road vehicles.** FHWA's automation portal [2] covers the federal role in automated vehicles: the **National Dialogue on Highway Automation** with states and industry, updating the **Manual on Uniform Traffic Control Devices (MUTCD)** to prepare for automated driving systems, **cooperative driving automation (CDA)** research, and studies of traffic flow through intersections.
- **Drones.** Part 107 covers small drones under 55 lb within visual line of sight. Package delivery for hire has operated under **Part 135** air-carrier certification. The FAA and TSA's proposed rule *Normalizing Unmanned Aircraft Systems Beyond Visual Line of Sight Operations* (NPRM, Docket FAA-2025-1908, Federal Register, August 7, 2025; comments were due October 6, 2025) would create **Part 108**: a routine, performance-based path for **beyond-visual-line-of-sight (BVLOS)** operations such as package delivery, with **permits** for lower-risk operations and **certificates** for more complex ones [21]. Summaries of the proposal describe operations at or below 400 ft above ground level with aircraft up to 1,320 lb. *A proposed rule is not law: check whether Part 108 has been finalized before the competition.*

### 2.6 Will people accept them?
- **COVID-19 study (Portland, 483 consumers)** [4]: the pandemic increased interest in **contactless** delivery. A latent-class analysis found six consumer segments: *Direct Shoppers, E-Shopping Lovers, COVID Converts, Omnichannel Consumers, E-Shopping Skeptics,* and *Indifferent Consumers*. Their **willingness to pay (WTP)** for robot delivery differed. The authors frame robots as a step toward **low-carbon last-mile logistics**.
- **"Robots at your doorstep" (692 U.S. respondents)** [5]: compared **automated vehicles, aerial drones, sidewalk robots and bipedal robots** using a nested choice model with latent attitudes (INCLV). People were most willing to accept an **automated vehicle** in place of a human courier, probably because self-driving cars are familiar. They **disliked drones and robots** more. Acceptance depended strongly on **price and delivery time**. **Older respondents** and those worried about **package handling** preferred automation less. Those with **higher education and technology affinity** preferred it more.

**How choice models work (useful background for [5]).** Each delivery option i gets a utility V_i, for example V_i = β_cost·cost_i + β_time·time_i + (attitude terms). In the basic logit form, the probability of choosing option i is P_i = e^{V_i} / Σ_j e^{V_j}.
- V_i = systematic utility of option i
- β_cost and β_time = sensitivity coefficients, usually negative because people dislike cost and delay
- cost_i, time_i = the option's price and delivery time
- e = Euler's number; the sum runs over every option j available

The nested model in [5] groups similar options (the automated modes) so they can substitute for each other more closely.

### 2.7 Links to your AP courses
- **AP Physics C:** forces (Step 1), power (Step 2), kinematics of stopping (Step 6), torque and the COM in tipping (Step 8), fluid momentum in hover (Step 10).
- **AP Calc BC:** energy as ∫P dt. Optimization: minimize total time, or find the speed that minimizes energy per km. Related rates: how fast d changes as the echo time changes. The derivative of drag with respect to V (dD/dV = C_d ρ A V).
- **AP Bio:** delivery robots learn from **biology**. Pedestrian crowds behave like collective animal motion (the social force model uses repulsion and attraction terms similar to flocking models) [18]. Machine-learning vision is loosely modeled on neural networks. Contactless delivery during COVID-19 was a disease-transmission (public-health) argument [4].

---

## Part 3: Equation sheet (every variable defined)

| # | Equation | Variables (units) | Used for |
|---|---|---|---|
| 1 | F_rr = C_rr N | F_rr rolling resistance (N); C_rr coefficient (–); N normal force (N) [15] | Surface and snow effects |
| 2 | D = ½ C_d ρ V² A | D drag (N); C_d drag coeff. (–); ρ air density (kg/m³); V relative air speed (m/s); A reference area (m²) [14] | Wind |
| 3 | F_g = mg sin θ | m mass (kg); g = 9.81 m/s²; θ slope angle | Hills |
| 4 | P = F v;  P_elec = P/η | P power (W); F resisting force (N); v speed (m/s); η drivetrain efficiency (–) | Power |
| 5 | E = ∫₀ᵀ P(t) dt ≈ Σ P_k T_k | E energy (J or Wh); P_k average power in phase k (W), e.g. driving or parked; T_k duration of phase k (s or h) | Range, charging |
| 6 | t = Σ dᵢ / vᵢ + Σ t_wait | dᵢ segment length (m); vᵢ segment speed (m/s); t_wait waiting times (s) | Delivery time |
| 7 | L = λW | L avg. number in system; λ arrival rate (1/h); W avg. time in system (h) [17] | Fleet size |
| 8 | N_fleet = ⌈L / α⌉ | α availability fraction (–) | Charging and maintenance allowance |
| 9 | f(n) = g(n) + h(n), with h(n) ≤ h*(n) | g cost so far; h heuristic estimate; h* true remaining cost [16] | Pathfinding |
| 10 | m_i dv_i/dt = f_i⁰ + Σf_ij + Σf_iw; f_i⁰ = m_i(v_i⁰e_i⁰ − v_i)/τ | see Step 5 [18] | Crowd motion |
| 11 | d = v_s t/2;  v_s ≈ 331.3 + 0.606 T_C | d distance (m); v_s speed of sound (m/s); t echo time (s); T_C temp. (°C) [24] | Ultrasonic sensing |
| 12 | d = c t/2 | c = 3.00×10⁸ m/s speed of light [19] | LiDAR |
| 13 | d_stop = v t_r + v²/(2a) | t_r reaction latency (s); a deceleration (m/s²) | Safe speed |
| 14 | tan θ_tip = (w/2)/h | w track width (m); h COM height (m) | Tipping on a slope |
| 15 | h = Σmᵢhᵢ / Σmᵢ | mᵢ, hᵢ mass and height of each part | Combined COM |
| 16 | a_lat,max = g(w/2)/h;  a_lat = v²/r | r turn radius (m) | Turning rollover |
| 17 | a_max = μ_s g | μ_s static friction coeff. cargo–bin (–) | Cargo sliding |
| 18 | P = T^{3/2}/√(2ρA) | P ideal hover power (W); T thrust = mg (N); A total rotor disk area (m²) [20] | Drone payload |
| 19 | v_ground = v_air − v_headwind | velocities (m/s) | Drone wind |
| 20 | % savings = (C_h − C_r)/C_h × 100 | C_h human cost/package; C_r robot cost/package ($) [6] | Economics |
| 21 | P_i = e^{V_i} / Σ_j e^{V_j} | P_i choice probability; V_i utility of option i | Acceptance models [5] |

---

## Part 4: Practice problems (answers below)

1. A 30 kg loaded robot climbs an 8% grade at 1.5 m/s with C_rr = 0.02. Find the traction power. Ignore drag.
2. Orders arrive at 90/h. The cycle time is 25 min and availability is 80%. How many robots are needed?
3. An ultrasonic echo returns after 5.00 ms at 30 °C. How far away is the obstacle?
4. A robot's COM rises from 0.18 m to 0.24 m. Its track width is 0.45 m. Find θ_tip before and after.
5. A drone's mass goes from 4.0 kg to 5.0 kg. By what factor does ideal hover power change?
6. In the A* graph of Step 5, the plaza edge B→G drops to 45 s. Is h(B) = 80 still admissible? What path is optimal?
7. Robot delivery costs $3.00 and human delivery costs $10.00. What is the percent savings?
8. At 1.667 m/s with a = 1.5 m/s² and t_r = 0.4 s, find the stopping distance.
9. A robot drives 20 min at 110 W and waits parked 6 min at 25 W. Its battery holds 1000 Wh. How many such deliveries per charge?

**Answers**
1. θ = arctan(0.08) = 4.57°. F = mg(sin θ + C_rr cos θ) = 294.3(0.0797 + 0.0199) = 29.3 N. P = 29.3 × 1.5 ≈ **44 W**.
2. L = 90 × (25/60) = 37.5. 37.5 / 0.8 = 46.9, so **47 robots**.
3. v_s = 331.3 + 18.18 = 349.5 m/s. d = 349.5 × 0.005 / 2 = **0.874 m**.
4. arctan(0.225/0.18) = **51.3°** → arctan(0.225/0.24) = **43.2°**.
5. (5/4)^{1.5} = **1.40**, so 40% more power.
6. **No.** The true cost from B is now 45 < 80, so h(B) overestimates and A* could return a non-optimal path. With an admissible heuristic, the optimum is S→B→G = **85 s**, better than S→A→G = 110 s. **Lesson:** heuristics must be based on the best possible case (straight-line distance at top speed), not on typical conditions.
7. (10 − 3)/10 = **70%**.
8. 0.667 + 0.926 = **1.59 m**.
9. E = 110 × (20/60) + 25 × (6/60) = 36.7 + 2.5 = 39.2 Wh. 1000 / 39.2 = 25.5, so **25 full deliveries**. (Using 110 W for all 26 min would give 47.7 Wh and only 20: the parked minutes must use the parked power.)

---

## Part 5: The six "Explore More" sources: reading plan and key content

Each entry gives what the source is, what it says (from its abstract, summary and indexed text), the numbers worth memorizing, how it connects to the worked example, and questions it could support. Skim the source itself with this as your map.

### [1] Emerging Automated Urban Freight Delivery Concepts: State of the Practice Scan
- **What it is:** U.S. DOT ITS Joint Program Office with the Volpe Center, FHWA-JPO-20-825, final report covering July 2019 to November 2020 (Cregger et al.).
- **What it says:** it characterizes the automated-delivery industry: **motivations, actors, activities, current issues and mitigation strategies**. It draws on a literature review, testing announcements and industry interviews to give public agencies objective findings. It sorts concepts into sidewalk robots (wheeled and legged), road delivery vehicles, aerial drones, and hybrid "mothership" combinations (Section 2.1 of this guide).
- **Connects to:** Part 2.1 (types), 2.2 (last-mile motivation), 2.5 (agency issues: curb and sidewalk space, safety, oversight).
- **Possible questions:** name the categories of automated delivery and one strength and one weakness of each; why public agencies need to plan for them.

### [2] FHWA: Automated Vehicle Activities and Resources
- **What it is:** the Federal Highway Administration's automation portal (a hub of programs, not a single paper).
- **What it says:** FHWA's role in safe testing and deployment of automated vehicles on highways: the **National Dialogue on Highway Automation**, updates to the **MUTCD** (the national rulebook for signs, signals and markings) to accommodate automated driving systems, and research on **connected and automated vehicles (CAV)** and **cooperative driving automation (CDA)**.
- **Connects to:** road-going delivery vehicles (Part 2.5), why lane markings and signage matter for machine perception (Step 6).
- **Possible questions:** which federal agency handles roadway infrastructure for AVs (FHWA) vs. vehicle safety (NHTSA) vs. airspace (FAA); what the MUTCD is.

### [3] PBIC: Personal Delivery Devices (*Sharing Spaces with Robots: The Basics of Personal Delivery Devices*)
- **What it is:** an Information Brief from the U.S. DOT-supported Pedestrian and Bicycle Information Center.
- **What it says:** it clarifies terms and definitions for PDDs, describes their **physical and operational characteristics**, and reviews **policy and research needs**, with an emphasis on pedestrians and bicyclists. A PDD is a device that carries cargo using automated driving technology, in spaces normally used by pedestrians and cyclists (sidewalks, crosswalks, bike lanes). Typical state definitions cited for sidewalk PDDs: **under 120 lb excluding cargo, at most 10 mph, remote human supervision** (limits vary by state; see [7]). Definitions vary widely, and some road-going devices are much larger and faster.
- **Connects to:** Steps 6 and 8 (speed and stopping in shared space), Part 2.4 (remote supervision), Part 2.5.
- **Possible questions:** what limits do states put on PDDs and why; accessibility concerns (wheelchair users, people with low vision); who has right-of-way.

### [4] Evaluating Public Acceptance of Autonomous Delivery Robots During COVID-19 Pandemic
- **What it is:** Pani, Mishra, Golias & Figliozzi, *Transportation Research Part D* 89 (2020), 102600.
- **What it says:** a representative survey of **483 Portland consumers** measured preferences, trust, attitudes and **willingness to pay (WTP)** for robot delivery. Latent-class analysis found **six segments**: Direct Shoppers, E-Shopping Lovers, COVID Converts, Omnichannel Consumers, E-Shopping Skeptics and Indifferent Consumers. The pandemic spotlighted robots for **contactless** delivery, and the authors frame robots as a step toward **low-carbon last-mile logistics**; knowing each segment's WTP drivers guides policies for mass adoption.
- **Connects to:** Part 2.6, the choice-model equation (Part 3, #21), AP Bio (disease transmission and contactless delivery).
- **Possible questions:** why did COVID-19 change attitudes; what is willingness to pay; why segment consumers instead of averaging them.

### [5] Robots at your doorstep: acceptance of near-future technologies for automated parcel delivery
- **What it is:** Said, Aeschliman & Stathopoulos (Northwestern), *Scientific Reports* (2023), DOI 10.1038/s41598-023-45371-1.
- **What it says:** a survey of **692 U.S. respondents** compared **autonomous vehicles, aerial drones, sidewalk robots and bipedal robots** using an Integrated Nested Choice and Correlated Latent Variable (**INCLV**) model, which reveals how the automated modes substitute for one another. People were most willing to accept an **automated vehicle** in place of a human courier and **disliked drones and robots** more. Acceptance is **strongly tied to price and delivery time**: faster and cheaper raises acceptance. **Older** respondents and those worried about **package handling** preferred automation less; **higher education and technology affinity** raised acceptance.
- **Connects to:** Part 2.6 and the logit equation; Steps 3 and 9 (time and cost are exactly the levers that move acceptance).
- **Possible questions:** which mode is most accepted and why; which two attributes matter most; which groups resist.

### [6] ITS: An autonomous vehicle delivery robot can deliver a package for 80 percent less cost than a human
- **What it is:** U.S. DOT ITS Knowledge Resources entry 2020-SC00452 (2020).
- **What it says:** an autonomous delivery operator in Ann Arbor, Michigan, designed its robot to operate **on the road instead of the sidewalk**. Robot delivery cost **$2.00–$2.50 per package** vs. **$11.00–$12.00** for human delivery, about **80% less**. The related news coverage identifies the operator as Refraction AI and its three-wheeled REV-1, which runs in bike lanes [23].
- **Connects to:** Step 9 (percent-savings equation, Part 3 #20); Part 2.2.
- **Possible questions:** compute percent savings from a cost range; why a road-margin robot might be cheaper or faster than a sidewalk robot; what costs the headline number leaves out (capital, supervision, maintenance).

---

## Citation Page

**Access note:** direct page downloads were blocked by the research tool's network, so every source below was consulted through web-search indexing of that exact page (its title, abstract or summary, and text extracted from the page). The URLs are the canonical addresses the searches returned. Every specific figure quoted in this guide was matched against that indexed text; where a source is a company or a secondary summary, the guide says so in the text. Use Part 5 as a map when you open the six sheet sources [1]–[6] yourselves.

**Sources from the official "Explore More" list**

1. Cregger, J., Machek, E., Behan, M., Epstein, A., Lennertz, T., Shaw, J., & Dopart, K. (2020). *Emerging Automated Urban Freight Delivery Concepts: State of the Practice Scan* (FHWA-JPO-20-825). U.S. DOT ITS Joint Program Office / Volpe Center. https://rosap.ntl.bts.gov/view/dot/53938
2. Federal Highway Administration. *Automated Vehicle Activities and Resources* (Automation portal). https://highways.dot.gov/automation
3. Pedestrian and Bicycle Information Center. *Sharing Spaces with Robots: The Basics of Personal Delivery Devices* (Information Brief). https://www.pedbikeinfo.org/downloads/PBIC_InfoBrief_SharingSpaceswithRobots.pdf (resource page: https://www.pedbikeinfo.org/resources/resources_details.php?id=5327)
4. Pani, A., Mishra, S., Golias, M., & Figliozzi, M. (2020). Evaluating public acceptance of autonomous delivery robots during COVID-19 pandemic. *Transportation Research Part D, 89*, 102600. https://pdxscholar.library.pdx.edu/cengin_fac/586 (also https://rosap.ntl.bts.gov/view/dot/77017)
5. Said, M., Aeschliman, S., & Stathopoulos, A. (2023). Robots at your doorstep: acceptance of near-future technologies for automated parcel delivery. *Scientific Reports, 13*. https://pmc.ncbi.nlm.nih.gov/articles/PMC10613628/ (publisher: https://www.nature.com/articles/s41598-023-45371-1)
6. U.S. DOT ITS Knowledge Resources (2020). *An autonomous vehicle delivery robot can deliver a package for 80 percent less cost than a human* (2020-SC00452). https://www.itskrs.its.dot.gov/2020-sc00452

**Additional sources**

7. Pedestrian and Bicycle Information Center. *Personal Delivery Devices (PDDs) Legislative Tracker (Version 1.0)*. https://www.pedbikeinfo.org/resources/resources_details.php?id=5314
8. Wevolver. *Starship Technologies Starship Robot: Tech Specs* (specification database compiling manufacturer figures). https://wevolver.com/specs/starship-technologies-starship-robot (with Dustbot, *How Starship Technologies Built the World's Largest Delivery Robot Fleet*: https://www.dustbot.org/robots/starship-delivery/)
9. Starship Technologies (2025). *One million deliveries in Finland* (company press release; figures are company-reported). https://www.starship.xyz/press/one-million-deliveries-finland/
10. Figliozzi, M., & Jennings, D. (2020). *Can Autonomous Delivery Robots Reduce Last-Mile Energy Consumption and CO2 Emissions?* (TRB 2020, Portland State University). https://nitc.trec.pdx.edu/sites/default/files/TRB%202020%20-%20PSU%20-%20Can%20Autonomous%20Delivery%20Robots%20Reduce%20Last-Mile%20Energy%20Consumption%20and%20CO2%20Emissions.pdf
11. Jennings, D., & Figliozzi, M. (2019). Study of Sidewalk Autonomous Delivery Robots and Their Potential Impacts on Freight Efficiency and Travel. *Transportation Research Record*. https://www.researchgate.net/publication/333171660_Study_of_Sidewalk_Autonomous_Delivery_Robots_and_Their_Potential_Impacts_on_Freight_Efficiency_and_Travel
12. Rodrigues, T. A., Patrikar, J., et al. (2022). Drone flight data reveal energy and greenhouse gas emissions savings for very small package delivery. *Patterns*. https://pmc.ncbi.nlm.nih.gov/articles/PMC9403403/
13. GPS.gov. *GPS Accuracy* (source of the ≤ 2.0 m URE commitment and the 0.643 m 2021 measurement). https://www.gps.gov/systems/gps/performance/accuracy/
14. NASA Glenn Research Center. *The Drag Equation* (Beginner's Guide to Aeronautics). https://www1.grc.nasa.gov/beginners-guide-to-aeronautics/drag-equation
15. The Engineering ToolBox. *Rolling Resistance*. https://www.engineeringtoolbox.com/rolling-friction-resistance-d_1303.html
16. Hart, P. E., Nilsson, N. J., & Raphael, B. (1968). A Formal Basis for the Heuristic Determination of Minimum Cost Paths. *IEEE Transactions on Systems Science and Cybernetics, 4*(2), 100–107. https://ieeexplore.ieee.org/document/4082128 (open copy: https://people.stfx.ca/jdelamer/courses/csci-564/_downloads/b2220c66675ddde471ca1795147b8e86/A_Formal_Basis_for_the_Heuristic_Determination_of_Minimum_Cost_Paths.pdf)
17. MIT. *Little's Law*. https://betterworld.mit.edu/littles-law/
18. Helbing, D., & Molnár, P. (1995/1998). *Social Force Model for Pedestrian Dynamics*. arXiv:cond-mat/9805244. https://arxiv.org/abs/cond-mat/9805244
19. NOAA National Ocean Service. *What is LIDAR?* https://oceanservice.noaa.gov/facts/lidar.html
20. Bauersfeld, L., & Scaramuzza, D. (2021). *Range, Endurance, and Optimal Speed Estimates for Multicopters* (momentum-theory hover power). arXiv:2109.04741. https://arxiv.org/pdf/2109.04741
21. Federal Aviation Administration & Transportation Security Administration (2025, August 7). *Normalizing Unmanned Aircraft Systems Beyond Visual Line of Sight Operations* (Notice of Proposed Rulemaking, Docket FAA-2025-1908). *Federal Register*, 90(150). https://www.federalregister.gov/documents/2025/08/07/2025-14992/normalizing-unmanned-aircraft-systems-beyond-visual-line-of-sight-operations (400 ft / 1,320 lb summary: DLA Piper, https://www.dlapiper.com/en/insights/publications/2025/08/faa-proposes-comprehensive-bvlos-uas-regulatory-framework)
22. IEEE Robots Guide. *Zipline*. https://robotsguide.com/robots/zipline
23. Government Technology. *Autonomous Delivery Robots Find Place in Michigan Bike Lanes* (Refraction AI REV-1). https://www.govtech.com/fs/automation/autonomous-delivery-robots-find-place-in-michigan-bike-lanes.html
24. FIRGELLI Automations. *Ultrasonic Sensor Time-of-Flight (ToF) Distance Calculator* (speed of sound vs. temperature). https://www.firgelliauto.com/blogs/engineering-calculators/ultrasonic-sensor-time-of-flight-tof-distance-calculator

### Requirement checklist
- [x] All six "Explore More" sources found by title, used and cited ([1]–[6])
- [x] At least 15 sites: 24 in total
- [x] Every equation has its variables defined (inline in Parts 1–2 and in the Part 3 table)
- [x] Citation page included, with how each source was consulted
- [x] Covers the sheet's four engineering tasks: delivery times (Steps 3–4), pathfinding through pedestrians (Step 5), weather (Step 7), payload stability (Step 8). Also answers both "Consider the following" questions (Sections 2.3–2.4).
