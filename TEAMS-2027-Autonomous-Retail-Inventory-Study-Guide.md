# Study Guide: Autonomous Retail Inventory
**TSA TEAMS 2027, "Engineering a Smarter World"**

Written for a team taking AP Calculus BC, AP Physics C and AP Biology. Numbers in square brackets, such as [2], point to the Citation Page at the end. 37 sources are cited in total (numbered entries 1–36 plus entry 16b).

---

## How to use this guide

1. Memorize the "Numbers to know" table directly below, then read Part 1 for the context behind each number. TEAMS questions often test one exact figure.
2. Work Part 3 (the equations) by hand. Every equation lists what each variable stands for, and each one has a worked example built from real numbers in the sources.
3. Use Part 4 (the workforce) for any question on "impact on human workers".
4. Finish with the practice questions in Part 6. Answers are at the end of that part.

The guide was put together from three expert viewpoints: a **robotics engineer** (navigation, sensors, fleet sizing), a **computer-vision and data scientist** (detection speed, accuracy metrics), and a **labor economist** (productivity, jobs, policy). Where they disagreed, the settled answer appears in a "Panel ruling" box.

### Numbers to know

| Topic | Number | Where explained |
|---|---|---|
| Inventory distortion (IHL, sheet's figure) | **~$1.7 trillion/yr** = out-of-stocks **~$1.2T** + overstocks (**~$554B** in the 2024 study; **~$572B** in the 2025 study) | 1.1 [12][13][35] |
| Empty shelves (IHL 2025 study) | **$690.9B**, the largest single out-of-stock cause | 1.1 [12][35] |
| Retail shrink, FY2022 (NRF) | **1.6% of sales**, about **$112.1B** | 1.1 [26] |
| Tally introduced | **2015**; CEO **Brad Bogolea** | 1.2 [2] |
| Tally RFID (2018) | **>700 tags/s**, **>99%** accuracy | 1.2 [8] |
| Tally 4.0 runtime (Jan 2026) | up to **12 h** | 1.2 [9] |
| Tally 10-year totals (Nov 2025) | **600M** shelf gaps, **80M** promotion errors, **18B** price tags, **44.8B** photos, **1.8M km**, **4.7M** hours, **42%** fixed instantly | 1.3 [2] |
| Simbe fleet (Sept 2026) | **>3,000** contracted robots, **>75** retail banners | 1.3 [10] |
| Schnucks | **3** full scans/day, ~**35,000** products/scan, **14×** as efficient, OOS down **up to 30%** | 1.4 [11] |
| Walmart drops Bossa Nova | **Nov 2020**, ~**500** stores | 1.5 [16] |
| Amazon | JWO removed from U.S. Fresh **Apr 2024**; all **15 Go + 57 Fresh** stores announced closing **Jan 27, 2026** (most closed **Feb 1, 2026**); JWO lives on in **360+** third-party sites | 1.5 [15][34] |
| Retail productivity | 2024 **+4.6%** (output +3.3%, hours −1.2%); 2025 **+2.9%** | 3.1 [18] |
| Robots vs. hours (SelectUSA) | +1% robot density ↔ **−1.0%** hours overall; **−2.7%** in slower-adopting industries | 3.3 [5] |
| Cashiers 2023–33 | **−353,100 jobs (−10.6%)** | 4.2 [16b] |
| DOJ AI inventory 2025 | **315** entries (**+30.7%**); FBI **50** | 4.3 [32] |
| A\* | **1968**, Hart, Nilsson, Raphael (SRI, Shakey) | 3.5 [21][22] |
| YOLO (2016) | **45 fps**; Fast YOLO **155 fps** | 3.7 [20] |

---

## Part 1. The core facts

### 1.1 The problem: inventory distortion

- The section sheet says out-of-stock items cost the industry "over $1.7 trillion annually". The source of that figure is IHL Group's inventory-distortion research. For 2024 IHL put **total inventory distortion at about $1.7 trillion**, made up of **out-of-stocks of about $1.2 trillion** and **overstocks of about $554 billion** [12][13]. Doing the arithmetic on those 2024 numbers: $1.2T + $0.554T = $1.754T, so **out-of-stocks ≈ 1.2/1.754 ≈ 68.4%** and **overstocks ≈ 0.554/1.754 ≈ 31.6%** of distortion.
- **IHL's 2025 study** ("Fixing Inventory Distortion – Who's Winning, Who's Failing, What's Working") again puts distortion at about **$1.7 trillion**, or **6.5% of global retail sales**, with out-of-stocks of about **$1.2 trillion** and overstocks of about **$572 billion** [12][35]. (Coverage of the newer data rounds the total to $1.75T [33].) Within that **same 2025 study**, out-of-stocks are broken down by root cause: **empty shelves $690.9B**, customer-service failures $165.6B, product-location failures $145.2B and price/offer mismatches $77.4B [12][35].
- **Empty shelves are a subset of out-of-stock losses**, not an extra cost on top. Both numbers come from the 2025 study, so the ratio is fair: $690.9B / $1.2T ≈ **58%** of the out-of-stock total. Rule for the test: only compute ratios between figures from the **same study year**; if a question gives you dollar amounts, work the percentage out from those.
- **Inventory distortion** = money lost to both out-of-stocks (customers you can't serve) and overstocks (stock you can't sell) [12][13].
- **Shrink** is a related loss: inventory lost to theft, damage or error. The NRF's 2023 National Retail Security Survey put the average shrink rate in FY2022 at **1.6% of sales (up from 1.4% in FY2021)**, or about **$112.1 billion** [26].

> **Panel ruling: is $1.7 trillion "out-of-stocks"?** The economist pointed out that IHL's $1.7 trillion covers **both** out-of-stocks and overstocks. The engineer noted that the official sheet attributes it to out-of-stocks. **Settled:** if a question quotes the sheet, answer "$1.7 trillion". If a question asks what the figure measures, the accurate answer is "total inventory distortion (out-of-stocks of about $1.2T plus overstocks of about $554B)".

### 1.2 Tally, the robot named on the sheet (Simbe Robotics)

| Fact | Value | Source |
|---|---|---|
| Maker | Simbe Robotics; CEO and co-founder **Brad Bogolea** | [2][31] |
| First introduced | **2015**; described as the "world's first autonomous shelf-scanning robot" | [2][31] |
| What it checks | Out-of-stocks, low stock, misplaced products, price-tag accuracy, promotion compliance | [1][7] |
| Sensors | Over a dozen high-resolution cameras, Intel RealSense 3D depth cameras, plus **RFID** | [1][8] |
| RFID performance (2018 upgrade) | **more than 700 tags per second** at **over 99% accuracy**, from floor level to about **5 m** high | [8] |
| Speed | Simbe describes it as "about human walking speed or slower" when reading RFID [8]; safety descriptions say "less than one-third of human walking speed" during store hours [28] | [8][28] |
| Scan rate (third-party report) | About **10,000 items in 30 minutes** | [27] |
| Charging | Drives itself back to its dock and recharges | [28] |
| Data path | Images go to the cloud for processing, then become task lists for associates | [28] |
| Tally 4.0 (Jan 2026) | Up to **12 hours of runtime**, ultra-high-resolution and specialty cameras, 3D and 360° coverage, NVIDIA edge-AI computing | [9] |

> **Panel ruling: robot speed.** The two speed statements come from different contexts and different years. **Settled:** treat Tally as a slow robot, well under 1.4 m/s (a typical adult walking speed, used here as an assumption). For calculations this guide uses **0.45 m/s**, which is about one-third of walking speed.

### 1.3 Tally at 10 years (PR Newswire release, Nov 12, 2025) [2][30][31]

| Ten-year total | Value |
|---|---|
| Shelf gaps (out-of-stocks) detected | **600 million** |
| Promotion errors fixed | **80 million** |
| Price tags scanned | **18 billion** |
| Shelf photos captured | **44.8 billion** |
| Distance driven | **1.8 million km** (about 45 times around the Earth) |
| Autonomous hours | **4.7 million** |
| Detected gaps fixed "instantly" | **42%** |
| Reach | **10 countries**, 3 continents, nearly a dozen retail sectors |

**Later update (Sept 2026):** Simbe said it had passed **3,000 contracted robots**, deployed across more than **75 retail banners** in nearly a dozen countries, with 45 billion shelf photos and 5 million autonomous hours [10]. Tally is now part of a wider "Store Intelligence" platform that also uses handheld and fixed sensors [10].

### 1.4 Case studies ("Simbe: Case Studies")

Simbe's case studies are on its Customer Stories page [7].

- **Schnuck Markets (St. Louis grocer).** The pilot started in **July 2017** in **3 stores** and expanded to at least **15 stores** [11]. In those stores Tally covered the whole floor **3 times a day**, scanning about **35,000 products** each time, which is more than **1.5 million product scans on an average day** across the stores [11]. By Sept 2020 Tally was in **more than half** of Schnucks stores [11]. Reported results: Tally was **14 times as efficient as manual scans** at finding out-of-stocks, and out-of-stocks fell by **up to 30%** [11].
- **BJ's Wholesale Club.** In **March 2023** BJ's announced it would roll out Tally to **all clubs**. The robot runs aisles several times a day and finds low stock and out-of-stocks, price errors and exact product locations, which speeds up restocking and helps staff and members find items [7].

### 1.5 Other autonomous-retail systems to know

- **Amazon Just Walk Out (JWO).** Shoppers take items and leave without checking out. It combines **computer vision, sensor fusion** (cameras plus weight sensors on shelves, so that small items such as gum get detected) and **deep learning**, and it was trained partly on **synthetic data made with generative adversarial networks (GANs)** [14]. Amazon later replaced depth cameras with RGB cameras [14].
- **What happened to it.** In **April 2024** Amazon said it would **remove JWO from its U.S. Amazon Fresh grocery stores** and switch to **Dash Carts**. At that time JWO stayed in Amazon Go convenience stores and some U.K. Fresh stores [15]. Reporting cited high operating costs, including human reviewers [15].
- **2026: Amazon's own stores close.** On **Jan 27, 2026** Amazon announced it would close **all** of its U.S. Amazon-branded grocery stores, **15 Amazon Go** and **57 Amazon Fresh**, with most closing on **Feb 1, 2026** (California locations later, to meet state rules). Amazon said it had not "created a truly distinctive customer experience with the right economic model needed for large-scale expansion" and is shifting to grocery delivery and Whole Foods Market [34]. **JWO itself continues** as a product sold to other businesses: it runs in **more than 360 third-party locations in five countries**, such as stadium concession stands [34].
- **Correcting the sheet.** The sheet says "Amazon stores now allow shoppers to walk in, put items in bags, and walk out." That described Amazon Go when the sheet was written. As of 2026 Amazon no longer runs its own Go stores; the correct present-tense answer is that **Just Walk Out operates in third-party venues** (stadiums, airports, campuses) [34].
- **Walmart and Bossa Nova.** In **Nov 2020** Walmart ended its contract with Bossa Nova Robotics. Bossa Nova's shelf-scanning robots were in about **500 stores**, and Walmart reported that workers could get similar results [16]. Lesson: a robot has to beat the cost and results of human workers, not just function.

> **Panel ruling: does autonomy always win?** The engineer argued the technology works. The economist pointed to the Walmart (2020), Amazon Fresh (2024) and Amazon Go/Fresh closure (2026) reversals. **Settled:** the right answer is "it depends on the economics". The robot's data must cost less than the labor it replaces, and it must lead to actions such as restocking. Tally's 42% instant-fix figure [2] is the kind of evidence that matters.

---

## Part 2. How the system works, step by step

1. **Map the store (SLAM).** SLAM (Simultaneous Localization and Mapping) lets a robot build a map while working out its own position on that map. The two problems depend on each other: you need a map to know where you are, and you need to know where you are to build a map [24]. LiDAR SLAM is the usual approach for indoor mobile robots [24].
2. **Plan a route (A\*).** Once there is a map, a path planner such as A\* (Part 3.5) picks a route that covers every aisle.
3. **Avoid obstacles.** Many sensors watch for shoppers, carts and displays. Tally can turn in place in narrow aisles and drives slowly [28].
4. **Capture data.** Cameras photograph the shelves and labels, depth cameras measure how far back product sits, and RFID reads tagged items such as apparel [1][8].
5. **Detect and recognize (deep learning).** Neural networks locate products, gaps and price tags in each image, then read the tag text and compare it with the planogram (the planned shelf layout) and the price file.
6. **Act.** Results are sent as tasks to associates' handheld devices, such as "restock aisle 7, bay 3" or "replace tag" [1][7].
7. **Learn and report.** Fleet data feeds dashboards for ordering, pricing and promotions [10].

---

## Part 3. Equations (every variable defined)

### 3.1 Labor productivity (BLS) [4][18][19]

$$LP = \frac{Q}{H}$$

- **LP**: labor productivity (output per hour worked)
- **Q**: real output (a price-adjusted measure of goods and services produced)
- **H**: hours worked by all persons

**Growth form:** $\;\%\Delta LP = \dfrac{1+g_Q}{1+g_H} - 1$

- **g_Q**: growth rate of output (as a decimal)
- **g_H**: growth rate of hours (as a decimal)

**Worked example (retail trade, 2024):** output +3.3% and hours −1.2% [18].
$(1.033 / 0.988) - 1 = 0.0455 \approx$ **+4.6%**, which matches what BLS published [18].

**Most recent data (2025, released May 28, 2026):** retail productivity **+2.9%** (output +2.5%, hours −0.4%). Wholesale productivity **+4.4%** (output +3.1%, hours −1.2%) [18]. Check: $1.025/0.996 - 1 = 2.9\%$.

**Other 2024 facts [18]:** wholesale +1.8%. Nonstore retailers **+12.8%** and electronics and appliance stores **+10.5%** were the double-digit gainers. Among the largest industries, clothing stores grew most at **+7.6%**, while department stores fell **−2.4%**.

### 3.2 Unit labor costs [19]

$$ULC = \frac{C}{Q} = \frac{C/H}{Q/H}$$

- **ULC**: unit labor cost (labor cost to produce one unit of output)
- **C**: total labor compensation (wages plus benefits)
- **Q**: real output
- **H**: hours worked
- **C/H**: hourly compensation; **Q/H**: labor productivity

Interpretation: higher productivity lowers ULC. In 2024 retail ULC fell **1.8%** [18].

### 3.3 Robots and hours worked (SelectUSA "Robots and the Economy") [5]

$$\%\Delta H \approx \beta \cdot \%\Delta D$$

- **%ΔH**: percent change in hours worked in an industry
- **%ΔD**: percent change in industrial robot density (robots per worker)
- **β**: estimated elasticity (percent change in hours per 1% change in robot density)

**The report's two estimates [5]:**
- **All industries in the sample: β ≈ −1.0.** "A one percent increase in industrial robot density was associated with a one percent decrease in hours worked, all else equal."
- **Industries slower to adopt robots: β ≈ −2.7.** "Among observations in the slower-to-adopt industrial robots group, a one percent increase in industrial robot density correlated with a 2.7 percent decrease in hours worked."

**Worked example.** If robot density in an industry rises 2%, the overall estimate gives %ΔH ≈ −1.0 × 2% = **−2%**; the slower-adopter estimate gives −2.7 × 2% = **−5.4%**.

**How to read β correctly (the scale caveat):**
- An elasticity is a **local, linear approximation**. It describes small changes around the data the report observed. Do not extrapolate it to large changes: a naive −2.7 × 37% would "predict" zero hours, which is meaningless.
- In slower adopters, robot density starts from a **low base**, so a 1% change in density is a tiny number of actual robots. A big elasticity there does not mean each robot removes many jobs.
- It is a **correlation**, not proof of cause, from industry-level data that is mostly manufacturing. Academic work measures the effect differently: Acemoglu and Restrepo (1990–2007 U.S. data) estimate that **one more robot per thousand workers** lowers a local area's **employment-to-population ratio by about 0.18–0.34 percentage points** and **wages by 0.25–0.5%** [36]. The two studies use different units, so do not compare the numbers directly. For a test answer, quote the report's numbers exactly and label them "correlation".

Context: Manufacturing made up **82.3%** of U.S. industrial robot installations in 2018 [5]. The report also notes that manufacturing is **40.1%** of all FDI in the U.S., and it cites economists' estimate that **47%** of U.S. occupation categories could be automated, representing about **$2 trillion** in annual wages [5].

### 3.4 Scan frequency and detection delay (Calc BC)

If a shelf gap appears at a random time between two scans that are $T$ hours apart, the expected wait until the next scan sees it is

$$\bar{t}_{delay} = \frac{1}{T}\int_0^T (T - t)\,dt = \frac{T}{2}$$

- **T**: time between scans of the same shelf (hours)
- **t**: the moment the gap appears, measured from the previous scan (uniformly distributed on [0, T])
- **t̄_delay**: average time a gap goes unseen

**Worked example.** Schnucks scanned **3 times a day** [11]. Assuming a 16-hour trading day (an assumption), $T = 16/3 \approx 5.3$ h, so $\bar t_{delay} \approx 2.7$ h. A once-a-day manual audit ($T = 24$ h) gives 12 h. That is the core argument for scanning more often.

**Scans per day a store can afford:**

$$N = \left\lfloor \frac{R}{t_{scan}} \right\rfloor, \qquad t_{scan} = \frac{S}{r}$$

- **N**: full-store scans per day per robot
- **R**: robot runtime available per day (h). Tally 4.0 has up to 12 h [9]
- **t_scan**: time for one full-store scan (h)
- **S**: number of products (SKU facings) to check
- **r**: scan rate (items per hour)

**Worked example.** With $S$ = 35,000 [11] and $r$ = 10,000 items per 30 min = 20,000/h [27], $t_{scan}$ = 1.75 h. With R = 12 h, $N = \lfloor 6.86 \rfloor$ = **6 scans/day**, so 3 a day is easy for one robot. (This mixes figures from different sources and robot generations. It is a sizing estimate, not a published specification.)

**Robots needed for a fleet:** $\;M = \left\lceil \dfrac{N_{target}\, t_{scan}}{R} \right\rceil$

- **M**: robots per store
- **N_target**: desired scans per day

### 3.5 Path planning with A\* [21][22]

$$f(n) = g(n) + h(n)$$

- **n**: a node (a grid cell or aisle intersection on the store map)
- **g(n)**: actual cost of the best path found so far from the start to n
- **h(n)**: heuristic estimate of the cost from n to the goal
- **f(n)**: estimated total cost of a path through n. A\* always expands the node with the lowest f

A\* was published in **1968** by **Peter Hart, Nils Nilsson and Bertram Raphael** at SRI for the **Shakey** robot [21][22]. It is guaranteed to find the optimal path if **h is admissible**, meaning it never **overestimates** the true remaining cost [21].

**Handling high-traffic aisles.** Give each aisle segment the edge cost

$$c_{edge} = \ell \,(1 + k\,\rho)$$

- **ℓ**: segment length (m)
- **ρ**: shopper density (shoppers per m², from cameras or footfall data)
- **k**: weight that sets how strongly congestion is avoided (k ≥ 0)

With **h = Manhattan distance** (|Δx| + |Δy|) on a 4-connected grid, h stays admissible because every edge cost is at least its length. A\* then plans routes that avoid crowded aisles while still being optimal for the weighted cost. A simpler choice is to schedule scans at off-peak hours, which lowers ρ everywhere.

### 3.6 Robot motion and safety (AP Physics C)

**Average speed from the 10-year data [2]:**

$$\bar v = \frac{d}{t} = \frac{1.8\times10^9\ \text{m}}{4.7\times10^6\ \text{h}\times3600\ \text{s/h}} \approx 0.11\ \text{m/s}$$

- **v̄**: average speed, including all stops and slow scanning
- **d**: total distance (m)
- **t**: total autonomous time (s)

**Stopping distance:**

$$d_{stop} = v\,t_r + \frac{v^2}{2a}$$

- **v**: cruising speed (m/s)
- **t_r**: sensing-plus-reaction delay (s)
- **a**: braking deceleration (m/s²)

**Worked example:** with v = 0.45 m/s, t_r = 0.1 s and a = 1.0 m/s² (all assumed values), $d_{stop} = 0.045 + 0.101 \approx$ **0.15 m**. A slow robot can stop within a hand's width, which is why low speed is the main safety feature.

**Battery energy:** $E = P\,t$

- **E**: energy (Wh)
- **P**: average power draw (W)
- **t**: runtime (h)

For example, 12 h of runtime [9] at an assumed 100 W needs at least 1.2 kWh.

### 3.7 Camera frame rate and processing speed (computer vision)

**Minimum capture rate per camera:**

$$f_{min} = \frac{v}{w\,(1-o)}$$

- **f_min**: frames per second needed so no shelf section is missed
- **v**: robot speed (m/s)
- **w**: shelf width covered by one frame (m)
- **o**: overlap fraction between consecutive frames (0 to 1)

**Worked example:** v = 0.45 m/s, w = 1.0 m, o = 0.3 (assumed) gives $f_{min} = 0.45/0.7 \approx$ **0.64 fps** per camera. Twelve cameras need about **7.7 frames/s** in total.

**Processing throughput and latency:**

$$\text{FPS} = \frac{1}{t_{inf}}$$

- **FPS**: frames processed per second
- **t_inf**: inference time per frame (s)

Reference point: the original **YOLO** ("You Only Look Once", Redmon et al., 2016) detector ran at **45 fps**, and **Fast YOLO** ran at **155 fps** [20]. 45 fps corresponds to about **22 ms per frame**. One such detector could keep up with 7.7 fps several times over. The real constraint is **resolution**: reading small price-tag text needs very high-resolution images, which is why Tally 4.0 added "ultra-high-resolution" cameras and why much of the processing has historically run in the cloud [9][28].

**Sanity check with real data:** 44.8 billion photos ÷ 4.7 million hours ≈ **9,500 photos per robot-hour ≈ 2.6 photos/s** [2]. That is the same order of magnitude as the estimate above.

### 3.8 Detection accuracy: precision, recall, F1, IoU [23][25]

$$P = \frac{TP}{TP+FP}, \qquad R = \frac{TP}{TP+FN}, \qquad F_1 = \frac{2PR}{P+R}$$

- **TP** (true positive): a real gap that the robot flagged
- **FP** (false positive): a flag where there was no gap. This sends a worker on a wasted trip
- **FN** (false negative): a real gap the robot missed. This is a lost sale
- **P**: precision; **R**: recall; **F₁**: harmonic mean of P and R

**Worked example:** Tally flags 120 gaps and 108 are real. The aisle actually had 130 gaps. Then P = 108/120 = **0.90**, R = 108/130 = **0.83** and F₁ = **0.86**.

$$IoU = \frac{|A \cap B|}{|A \cup B|}$$

- **A**: predicted bounding box; **B**: ground-truth box
- **IoU**: overlap score from 0 to 1. A detection usually counts as correct only if IoU ≥ **0.5** [25]

**Worked example:** two 10×10 boxes offset by 5 units overlap in 50 units². Union = 100 + 100 − 50 = 150, so IoU = 0.33. That is below 0.5, so it counts as a miss.

### 3.9 RFID read range (Friis transmission equation) [29]

$$P_r = P_t\,G_t\,G_r\left(\frac{\lambda}{4\pi d}\right)^2 \quad\Rightarrow\quad d_{max} = \frac{\lambda}{4\pi}\sqrt{\frac{P_t\,G_t\,G_r\,\tau}{P_{th}}}$$

- **P_r**: power received at the tag (W)
- **P_t**: reader transmit power (W)
- **G_t, G_r**: gains of the reader antenna and the tag antenna (dimensionless)
- **λ**: wavelength (m). About 0.33 m for 915 MHz UHF RFID ($\lambda = c/f$, with **c** = 3.0×10⁸ m/s the speed of light and **f** the frequency in Hz)
- **d**: reader-to-tag distance (m)
- **τ**: power transmission coefficient, the share of received power the tag chip actually gets (0 to 1)
- **P_th**: minimum power the passive tag chip needs to switch on (W)
- **d_max**: maximum read range (m)

Key results: $d_{max} \propto \sqrt{P_t}$, so **doubling reader power increases range by only √2 ≈ 1.41×**. Water and human bodies lower τ and shorten range [29], which is a reason RFID works better on clothing than on bottled drinks.

---

## Part 4. Impact on human workers

### 4.1 How BLS builds AI into job projections (the "BLS: Case Studies" source) [3][17]

- **Article:** "Incorporating AI impacts in BLS employment projections: occupational case studies", *Monthly Labor Review*, **February 2025**, using the **2023–33** projections cycle [3].
- **Method:** BLS treats AI like any other technology and assumes structural change happens **gradually**. The case studies cover **computer, legal, business and financial, and architecture and engineering** occupations [3].
- **Key numbers (2023–33) [3][17]:**
  - Software developers **+17.9%** (much faster than average)
  - Lawyers **+5.2%**; paralegals and legal assistants **+1.2%**
  - Customer service representatives **−5.0%** (generative AI can handle many of their core tasks)
  - Medical transcriptionists **−4.7%**
- Retail link: occupations whose **core tasks** AI can easily copy decline, while occupations where AI is only one tool among many keep growing.

### 4.2 Retail jobs

- **Cashiers:** projected to lose about **353,100 jobs (−10.6%) from 2023 to 2033**, the largest numeric decline of any occupation. BLS cites **self-checkout** and online sales as causes [16b].
- **Productivity:** retail hours worked **fell 1.2%** in 2024 while output **rose 3.3%** [18]. Stores produced more with fewer hours.
- **How the work changes:** shelf-scanning robots take over the **auditing** (walking aisles and checking tags), but people still do the **fixing** (restocking, re-tagging). Simbe frames this as making associates more productive [11]. Schnucks called it "the Tally effect" [11].

> **Panel ruling: will robots cut retail jobs?** The economist cited the cashier decline and SelectUSA's finding that robot density and hours worked move in opposite directions (β ≈ −1.0 overall, −2.7 in slower-adopting industries, both correlations from mostly manufacturing data) [5][16b]. The engineer noted that a Tally-type robot only **finds** problems, and a human still has to fix them. **Settled:** automation mostly **shifts task mix** (from checking to stocking and serving) rather than removing whole jobs. The exception is where a system replaces the core task outright, as self-checkout does for cashiers. Cite both sides in a written answer.

### 4.3 Ethics and governance

- **Shopper tracking privacy.** Systems like JWO track shoppers from entry to exit [14]. Engineers should collect only the data they need, anonymize it, and post clear notices.
- **AI accountability (DOJ AI Inventory) [6][32].** Under **Executive Order 13960** and **OMB Memorandum M-25-21**, federal agencies must publish an **annual inventory of their AI use cases** [6]. DOJ's **2025** inventory lists **315 entries, 30.7% more than in 2024** [32]. The inventory covers every stage (pre-deployment, pilot, deployed, retired), and law-enforcement uses are about **62%** of deployed cases [32]. The **FBI** reported **50 use cases** (19 in 2024) [32].
- **Why it matters for this section:** the government is building a public list of the AI it uses, much as a retailer builds a list of what is on its shelves. A store using AI could adopt the same practice: list each model, its purpose, its data and its risk level.

---

## Part 5. Design checklist: characteristics of an autonomous retail fleet

The sheet asks for **shelf-scanning frequency, computer-vision processing speed and optimal navigation paths**. Here is the engineering answer, with numbers.

| Design variable | Recommended value or rule | Basis |
|---|---|---|
| Scan frequency | 3 or more full scans a day for grocery. With scans spread over an assumed **16-hour trading day**, T = 16/3 ≈ 5.3 h, so the average detection delay is T/2 ≈ 2.7 h. (If the 3 scans were spread over a full 24 h, T = 8 h and T/2 = 4 h.) | Schnucks practice [11]; Part 3.4 |
| Scan rate | About 20,000 items/h, so a 35,000-item store takes about 1.75 h | [27][11] |
| Runtime | Up to 12 h per charge (Tally 4.0); docks itself | [9][28] |
| Robots per store | M = ⌈N·t_scan / R⌉; one robot for most stores | Part 3.4 |
| Capture rate | About 0.6 fps per camera at 0.45 m/s; well under 10 fps for the whole robot | Part 3.7 |
| Inference speed | At least 10 fps of capacity is plenty. YOLO-class detectors reach 45 to 155 fps | [20] |
| Accuracy target | Report precision and recall separately. RFID read accuracy over 99% | [8][23] |
| Navigation | SLAM map plus A\* with congestion-weighted costs; turn in place; scan off-peak | [21][24][28] |
| Speed | Well under walking speed; stopping distance about 0.15 m | [28]; Part 3.6 |
| Sensing mix | RGB cameras, depth cameras and RFID (sensor fusion) | [1][8][14] |
| Business test | Value of recovered sales and labor saved must exceed the robot's cost (the Walmart 2020 lesson) | [16] |

---

## Part 6. Practice questions

1. In what year was Tally introduced, and who is Simbe's CEO?
2. Retail output grew 3.3% and hours fell 1.2% in 2024. Compute productivity growth.
3. A store scans 4 times over a 16-hour day. What is the average delay before a new gap is detected?
4. A robot flags 200 gaps, of which 150 are real, and misses 50 real gaps. Find precision and recall.
5. By what factor does RFID read range change if reader power is quadrupled?
6. Which A\* heuristic property guarantees an optimal path?
7. What does IHL's ~$1.7 trillion figure include?
8. Which retail occupation does BLS project to lose the most jobs in 2023–33, and why?
9. Name two companies that scaled back store-automation programs, and give the year for each.
10. Which executive order and OMB memo require federal AI use-case inventories?
11. Is Amazon Go still open in 2026? Where does Just Walk Out run now?
12. SelectUSA reports β ≈ −1.0 for all industries. If robot density rises 3%, what change in hours does that predict? Why should you not apply β to a 50% rise?

**Answers:**
1. 2015; Brad Bogolea [2].
2. 1.033/0.988 − 1 = 4.6% [18].
3. T = 4 h, so T/2 = 2 h.
4. P = 150/200 = 0.75; R = 150/(150+50) = 0.75.
5. √4 = 2, so the range doubles.
6. Admissibility: h never overestimates the remaining cost [21].
7. Out-of-stocks (~$1.2T, ≈68% of the total) plus overstocks (~$554B, ≈32%) [12][13]. Empty shelves (~$690.9B) are part of the out-of-stock figure, not added to it.
8. Cashiers, −353,100 (−10.6%), because of self-checkout and online sales [16b].
9. Walmart ended Bossa Nova robots in 2020 [16]; Amazon removed Just Walk Out from U.S. Fresh stores in 2024 [15] and announced it was closing all Go and Fresh stores in 2026 [34].
10. EO 13960 and OMB M-25-21 [6].
11. No. Amazon announced on Jan 27, 2026 that it would close all 15 Go and 57 Fresh stores (most on Feb 1, 2026); JWO continues in 360+ third-party locations in five countries [34].
12. %ΔH ≈ −1.0 × 3% = −3%. An elasticity is a local linear approximation from observed data, so it is not valid for large changes, and it is a correlation, not a cause [5].

---

## Assumptions

- **"Simbe: Case Studies"** (no URL given) is taken to be Simbe's Customer Stories page [7]. The BJ's story and the Schnucks results were used from it and from related releases.
- **"BLS: Case Studies"** is taken to mean the user-supplied *Monthly Labor Review* article [3], whose subtitle is "occupational case studies". **"Department of Commerce: Robots and the Economy"** is the SelectUSA PDF [5], which carries that title (SelectUSA is part of Commerce's International Trade Administration).
- Values marked "assumed" in the worked examples (walking speed 1.4 m/s, robot speed 0.45 m/s, 16-hour trading day, frame width 1 m, braking 1 m/s², 100 W power) are illustrative and do not come from Simbe specifications.
- Some figures come from Simbe or its customers. They are company-reported and have not been independently audited.

---

## Citation Page

**How the sources were consulted.** The research environment blocked direct page downloads from most sites, including simberobotics.com, prnewswire.com, bls.gov, trade.gov and justice.gov. Every source below was therefore consulted through **web-search results**, using the indexed text and excerpts the search engine returned for that exact URL, in October 2026. Every fact used was matched to the URL listed. Search excerpts can lag behind a live page, so check exact numbers against the live page before the competition.

**User-provided and "Explore More" sources**

1. Simbe Robotics. "Tally" (Simbe: Tally Store Intelligence and Accuracy). https://www.simberobotics.com/store-intelligence/tally
2. PR Newswire / Simbe Robotics. "Simbe Marks 10 Years of Tally the Robot: 600M Shelf Gaps Detected, 80 Million Promotion Errors Fixed, and a New Era of Retail Store Intelligence." Nov 12, 2025. https://www.prnewswire.com/news-releases/simbe-marks-10-years-of-tally-the-robot-600m-shelf-gaps-detected-80-million-promotion-errors-fixed-and-a-new-era-of-retail-store-intelligence-302612437.html
3. U.S. Bureau of Labor Statistics. "Incorporating AI impacts in BLS employment projections: occupational case studies." *Monthly Labor Review*, Feb 2025. https://www.bls.gov/opub/mlr/2025/article/incorporating-ai-impacts-in-bls-employment-projections.htm
4. U.S. Bureau of Labor Statistics. "Wholesale and Retail Trade Industries: Labor Productivity" (highlights). https://www.bls.gov/productivity/highlights/wholesale-retail-trade-industries-labor-productivity.htm
5. SelectUSA, International Trade Administration, U.S. Department of Commerce. "Robots and the Economy" (SelectUSA Automation Report, 2020). https://www.trade.gov/sites/default/files/2022-08/SelectUSAAutomationReport2020.pdf
6. U.S. Department of Justice. "AI Inventory." https://www.justice.gov/ai/ai-inventory
7. Simbe Robotics. Customer Stories (Simbe: Case Studies), including "How BJ's Wholesale Club Improved Store Performance." https://www.simberobotics.com/resources/customer-stories/ and https://www.simberobotics.com/resources/customer-stories/how-bjs-wholesale-club-improved-store-performance

**Additional reliable sources**

8. Simbe Robotics. "Simbe Robotics Reveals RFID and Machine Learning Capabilities in the Latest Iteration of Their Autonomous Inventory Robot Tally" (2018). https://www.simberobotics.com/news/simbe-robotics-reveals-rfid-and-machine-learning-capabilities-in-the-latest-iteration-of-their-autonomous-inventory-robot-tally
9. Robotics Tomorrow. "Simbe Unveils Tally 4.0: The Next Generation of Autonomous Retail Robot Powering Store Intelligence via Physical AI." Jan 12, 2026. https://www.roboticstomorrow.com/news/2026/01/12/simbe-unveils-tally-40-the-next-generation-of-autonomous-retail-robot-powering-store-intelligence-via-physical-ai/25992/
10. Robotics 24/7. "Simbe surpasses 3,000 autonomous shelf intelligence units milestone." Sept 2026. https://www.robotics247.com/article/simbe-surpasses-3000-autonomous-shelf-intelligence-units-milestone
11. Business Wire. "Schnuck Markets Deploys Tally Robot to More Than Half of Stores." Sept 30, 2020. https://www.businesswire.com/news/home/20200930005054/en/Schnuck-Markets-Deploys-Tally-Robot-to-More-Than-Half-of-Stores (with Simbe's release on the 15-store expansion: https://www.simberobotics.com/about/newsroom/schnuck-markets-ups-the-ante-on-product-insights-expanding-simbe-robotics-autonomous-shelf-auditing-robot-tally-to-at-least-15-stores)
12. Board International. "The $1.7 Trillion Wake-Up Call: Why Retail Planning Must Move Beyond Silos" (summarizing IHL Group data). https://www.board.com/blog/the-1-7-trillion-wake-up-call-why-retail-planning-must-move-beyond-silos
13. IHL Group. "Fixing Inventory Distortion – Are We There Yet?" https://www.ihlservices.com/product/fixing-inventory-distortion-are-we-there-yet/
14. Just Walk Out (Amazon). "What is Just Walk Out technology, and how does it work?" https://www.justwalkout.com/resources/what-is-just-walk-out-technology-and-how-does-it-work
15. Fortune. "Amazon removing cashierless Just Walk Out system from Fresh grocery stores." Apr 3, 2024. https://fortune.com/2024/04/03/amazon-removing-cashierless-just-walk-out-system-fresh-grocery-stores/
16. TechXplore / Associated Press. "Walmart abandons shelf-scanning robots, lets humans do work." Nov 2020. https://techxplore.com/news/2020-11-walmart-abandons-shelf-scanning-robots-humans.html
16b. U.S. Bureau of Labor Statistics. *Occupational Outlook Handbook*: "Cashiers." https://www.bls.gov/ooh/sales/cashiers.htm
17. U.S. Bureau of Labor Statistics. *The Economics Daily*: "AI impacts in BLS employment projections." 2025. https://www.bls.gov/opub/ted/2025/ai-impacts-in-bls-employment-projections.htm
18. U.S. Bureau of Labor Statistics. "Productivity and Costs by Industry: Wholesale Trade and Retail Trade" news releases, May 28, 2026 (2025 data) and May 29, 2025 (2024 data). https://www.bls.gov/news.release/archives/prin1_05282026.htm and https://www.bls.gov/news.release/archives/prin1_05292025.htm
19. U.S. Bureau of Labor Statistics, K-12 "Productivity 101": "What is unit labor cost?" https://www.bls.gov/k12/productivity-101/content/what-is-productivity/what-is-unit-labor-cost.htm
20. Redmon, J., Divvala, S., Girshick, R., Farhadi, A. "You Only Look Once: Unified, Real-Time Object Detection." arXiv:1506.02640 / CVPR 2016. https://arxiv.org/abs/1506.02640
21. Wikipedia. "A* search algorithm." https://en.wikipedia.org/wiki/A*_search_algorithm
22. *Communications of the ACM*. "A* Search." https://cacm.acm.org/opinion/a-search
23. Google for Developers, Machine Learning Crash Course. "Classification: Accuracy, recall, precision, and related metrics." https://developers.google.com/machine-learning/crash-course/classification/accuracy-precision-recall
24. IEEE TechNav. "Simultaneous localization and mapping." https://technav.ieee.org/topic/simultaneous-localization-and-mapping/
25. Voxel51 Glossary. "Intersection over Union (IoU)." https://voxel51.com/glossary/intersection-over-union
26. National Retail Federation. "National Retail Security Survey 2023." https://nrf.com/research/national-retail-security-survey-2023
27. The Manufacturer. "Tally robot autonomously monitors store shelves." https://www.themanufacturer.com/articles/tally-robot-autonomously-monitors-store-shelves/
28. Automated Warehouse. "Simbe Robotics" (Tally navigation, docking and safety profile). https://www.automatedwarehouseonline.com/simbe-robotics/ ; see also Computerworld, "Autonomous robot designed to stroll store aisles and keep check on inventory" (2015). https://www.computerworld.com/article/3004851/robot-keeps-stores-stocked-with-doritos.html
29. Hubble. "How to Calculate UHF RFID Read Range" (Friis equation applied to passive RFID). https://hubble.com/community/guides/how-to-calculate-uhf-rfid-read-range/
30. The Shelby Report. "Simbe Commemorates 10 Years of Tally the Robot." Nov 12, 2025. https://theshelbyreport.com/2025/11/12/simbe-commemorates-10-years-of-tally-the-robot/
31. Simbe Robotics Newsroom. "Simbe Marks 10 Years of Tally the Robot." https://www.simberobotics.com/about/newsroom/simbe-marks-10-years-of-tally-the-robot
32. MeriTalk. "DOJ Says AI Use Cases Grew Nearly 31% in 2025." https://www.meritalk.com/articles/doj-says-ai-use-cases-grew-nearly-31-in-2025/
33. Retail Insight Network. "How overstock, stockouts and returns cost retail $1.75tn" (summarizing newer IHL Group data; consulted through search excerpts). https://www.retail-insight-network.com/features/how-overstock-stockouts-and-returns-cost-retail-1-75tn/
34. TechCrunch. "Amazon is closing its physical Amazon Go and Amazon Fresh stores." Jan 27, 2026. https://techcrunch.com/2026/01/27/amazon-is-closing-its-physical-amazon-go-and-amazon-fresh-stores (same facts in the Associated Press report carried by ABC7: https://abc7.com/post/amazon-stores-closing-close-go-fresh-locations-concentrate-foods-grocery-delivery/18486641/)
35. IHL Group. "Fixing Inventory Distortion – Who's Winning, Who's Failing, What's Working" (2025 study; product page and summary). https://www.ihlservices.com/product/fixing-inventory-distortion-whos-winning-whos-failing-whats-working/ ; summary also via British Retail Consortium: https://brc.org.uk/news-and-events/news/associate-insight/2025/fixing-inventory-distortion-who-s-winning-who-s-failing-what-s-working/
36. Acemoglu, D., Restrepo, P. "Robots and Jobs: Evidence from US Labor Markets." NBER Working Paper 23285, March 2017 (published in *Journal of Political Economy*, 2020). https://www.nber.org/papers/w23285

---

## Requirements check

| # | Requirement | Where it is met |
|---|---|---|
| 1 | Use all 6 user URLs | Citations 1–6, used in Parts 1.2–1.3 [1][2], 4.1 [3], 3.1 [4], 3.3 [5] and 4.3 [6] |
| 2 | Use all 7 "Explore More" sources, including Simbe: Case Studies | The 6 above plus citation 7, used in Part 1.4 |
| 3 | Add other reliable sources | Citations 8–36 and 16b |
| 4 | At least 15 sites | 37 sources cited (entries 1–36 plus 16b; several entries list a second URL) |
| 5 | Each equation defines its variables | Part 3.1–3.9; every symbol has a bullet |
| 5b | Facts current for a 2027 competition | 2026 updates: Tally 4.0 [9], Simbe 3,000 robots [10], BLS 2025 productivity [18], Amazon Go/Fresh closures [34], IHL 2025 study [35] |
| 6 | Citation page | "Citation Page" section, with a note on how sources were consulted |
| 7 | Covers the sheet: scan frequency, CV speed, navigation, workers | Parts 3.4, 3.7, 3.5, 4 and the design table in Part 5 |
| 7b | Key figures summarized | "Numbers to know" table under "How to use this guide" |
| 8 | Pitched at AP Calc BC / Physics C / Bio students | Integral derivation (3.4), kinematics and energy (3.6), electromagnetics (3.9), neural-network vision (Part 2) |
