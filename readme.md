# 📌 **UPI Transaction Allocation Under Capacity Constraints**

*A study on reducing duopoly, improving fairness, and minimizing user burden in India’s UPI ecosystem.*

---

## 📖 **Overview**

This repository contains the code, algorithms, and experimental results associated with our research on **load-balancing UPI transactions across multiple apps** under capacity limits imposed by the National Payments Corporation of India (NPCI).

UPI transactions in India are highly concentrated, with two apps (PhonePe & Google Pay) handling the majority of the volume. To reduce systemic risk, NPCI proposes a **30% transaction share cap**, motivating the need for intelligent allocation strategies.

This project models the problem as a **Minimum Edge Activation Flow (MEAF)** task and proposes scalable heuristics that minimize additional app installations while ensuring full transaction coverage.

---

## 🚀 **Key Contributions**

### 🔹 1. **Problem Modeling**

* We formulate UPI transaction routing as a **bipartite flow network**.
* Preinstalled apps are fixed edges; additional installations correspond to activatable edges.
* Objective: **route all user transactions without exceeding app capacity**, while minimizing new installations.

### 🔹 2. **NP-Completeness Result**

We prove that MEAF is **NP-Complete** via reduction from 3-Partition, ruling out polynomial-time exact algorithms.

### 🔹 3. **Proposed Offline Algorithms**

Two efficient heuristics were developed and tested:

#### **CARL — Capacity-Aware Reuse-First Layered Allocation**

* Processes users in ascending transaction load.
* Allocates through three layers: preinstalled → shared → new apps.
* Achieves **~99% runtime reduction** compared to ILP with near-optimal accuracy.

#### **DTAS — Decoupled Two-Stage Allocation Strategy**

* Separates allocation into:
  **(1) Preinstalled stage**, **(2) Extra app stage**
* Prevents premature saturation and redundant installations.
* Achieves the **highest fairness**, best coverage, and fastest runtime growth.
* Consistently matches ILP in installation count.

---

## 📊 **Experimental Insights**

* Evaluated on **100M transactions** and **1.2M users** (semi-synthetic dataset).
* As app capacity increases:

  * Users needing new apps drop from **2.25% (10% cap)** to **near-zero (40% cap)**.
  * But **duopoly effects strengthen**, with dominant apps absorbing most traffic.
* Reducing capacity:

  * Reduces dominance,
  * But increases **unallocated transactions** (e.g., 65M dropped at 10% cap).
* DTAS shows:

  * **Best fairness** (Inverse Gini Score = 0.53)
  * **Near-linear runtime scaling**
  * **Almost identical performance to ILP**, but in **seconds**, not hours.

---

## 🧪 **Dataset Generation**

A semi-synthetic dataset was created using:

* Rabobank cumulative transaction data
* C2C, C2B, B2B ratio constraints
* NPCI monthly market-share statistics for UPI apps
* Realistic probabilistic assignment of preinstalled apps

---

## 🧰 **Technologies Used**

* Python (NumPy, Pandas, Matplotlib)
* PuLP / Gurobi for ILP & LP modeling
* LaTeX (ACM template)

---

## 🤝 **Contributions**

Contributions, pull requests, and suggestions are welcome!
Feel free to open an issue if you'd like to improve or extend the algorithms.

---

## 📬 **Contact**

For questions or collaboration opportunities, please reach out:

**Shashwat Kumar**
Email: kshashwat.iit@gmail.com

