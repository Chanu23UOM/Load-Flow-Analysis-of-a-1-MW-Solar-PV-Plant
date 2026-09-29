# Load Flow Analysis of a 1 MW Solar PV Plant

A steady-state power flow case study of a 1 MW grid-connected solar photovoltaic (PV) plant built and analyzed using Siemens PSS®E. The project models generator dispatch, network branches, voltage profiles, power flow directions, and element loadings across a 4-bus power system.

---

## System Architecture

The simulation is configured on a **100 MVA system base**:

| Bus | Name | Nominal kV | Role / Type | Details |
| :--- | :--- | :--- | :--- | :--- |
| **Bus 1** | SOLAR BUS | 0.69 kV | Generator / PV (or PQ) | 1.0 MW generation at unity PF ($Q = 0.0\text{ Mvar}$) |
| **Bus 2** | LOAD BUS | 33.0 kV | PQ (Load) | Local demand of $2.0\text{ MW} + j0.8\text{ Mvar}$ |
| **Bus 3** | LOAD BUS 2 | 33.0 kV | PQ (Network) | Intermediate junction bus ($P = 0$, $Q = 0$) |
| **Bus 4** | GRID BUS | 132.0 kV | Swing / Slack | Reference bus ($V = 1.02\text{ pu}$, $\theta = 0^\circ$), balances system mismatch |

---

## Branch & Equipment Parameters

* **Transformer 1 (Bus 1 – Bus 2):** 
  * 0.69 / 33 kV, 1.25 MVA
  * $X = 6.0\%$ on transformer MVA base
* **33 kV Feeder (Bus 2 – Bus 3):** 
  * 10 km equivalent overhead line, 10 MVA rating
  * $R = 0.020\text{ pu}$, $X = 0.040\text{ pu}$, $B = 0.001\text{ pu}$ (on 100 MVA base)
* **Transformer 2 (Bus 3 – Bus 4):** 
  * 33 / 132 kV, 20 MVA
  * $X = 8.0\%$ on transformer MVA base

---

##  Key Results

* **Convergence:** Solved via Newton-Raphson in **2 iterations** with a total absolute mismatch of **0.00 MVA**
* **Active Power Balance:**
  $$\sum P_{\text{Gen}} = P_{\text{Solar}} (1.0\text{ MW}) + P_{\text{Grid}} (1.0\text{ MW}) = P_{\text{Load}} (2.0\text{ MW})$$
* **Reactive Power Balance:**
  * Grid supplies $0.7\text{ Mvar}$ to the network.
  * Feeder shunt charging ($B = 0.001\text{ pu} \approx 0.1\text{ Mvar}$) supplies the remainder required by the $0.8\text{ Mvar}$ load.
* **Element Loading:**
  * **Transformer 1:** 80% (most loaded element; $1.0\text{ MW}$ through $1.25\text{ MVA}$ capacity)
  * **33 kV Feeder:** 13% of 10 MVA rating
  * **Transformer 2:** 6% of 20 MVA rating
  * *No system equipment exceeds operational thermal limits.*

---

## Software & Tools

* **Tool:** Siemens PTI PSS®E (PSS®E Xplore 34)
* **Study Type:** AC Steady-State Power Flow

---
