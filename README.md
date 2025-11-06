# Agent-Simulation-With-Network-Effects-Cooperative-equilibrium-
This project simulates cooperation and defection in a networked market using a modified Prisoner’s Dilemma. Agents learn trust through reinforcement, forming dynamic patterns of cooperation, competition, and inequality across a connected system of interacting participants.

# 🧠 Cooperative Equilibrium Simulation  
### *Agent-Based Model of Information Sharing and Trust in Networked Economies*

**Author:** Qudus Bawa-Allah  
**Language:** Python 3.10+  
**Libraries:** `numpy`, `pandas`, `matplotlib`, `seaborn`, `networkx`  
**File:** `Agent simulation with Network Effects.ipynb`

---

## 📘 Overview
This project implements an **agent-based simulation** of cooperation and defection in a **networked market environment**.  
Agents interact through a modified *Prisoner’s Dilemma*, updating their internal **trust levels** using a reinforcement-learning rule.  
By embedding agents in a **network graph**, the simulation models how **trust, cooperation, and payoff inequality** emerge in complex systems.

The simulation visualizes:
- 🧩 **Cooperation rate** evolution over time  
- 🌐 **Network structure** of interactions  
- 💰 **Distribution of payoffs** across agents  
- 🎨 **Color-mapped network** showing which clusters succeed  

---

## ⚙️ Model Summary

### 1. Agent Dynamics
Each agent \(i\) maintains:
- **Trust memory:** \( T_{ij} \in [0,1] \) — belief in partner \(j\)’s reliability.  
- **Action policy:**  
  - *Cooperate (S)* if \( \text{rand}() < T_{ij} \)  
  - *Defect (D)* otherwise  
- **Trust update rule:**
  \[
  T_{ij}^{t+1} =
    \begin{cases}
      T_{ij} + 0.1(1 - T_{ij}), & \text{if partner cooperated}\\
      T_{ij} - 0.1T_{ij}, & \text{if partner defected}
    \end{cases}
  \]

### 2. Payoff Matrix
|            | Partner S | Partner D |
|-------------|-----------|-----------|
| **Self S** | (4 , 4)   | (0 , 6)   |
| **Self D** | (6 , 0)   | (1 , 1)   |

### 3. Network Topology
Agents are nodes in an **Erdős–Rényi random graph** \( G(n, p) \), where `p` controls the likelihood of connections (information channels).  
Only connected agents can interact, introducing **localized equilibria** and **heterogeneous outcomes**.

---

## 📈 Simulation Workflow

1. **Initialize** `num_agents` and generate network `G`.  
2. **Iterate** over `rounds`:  
   - Each agent selects a random neighbor.  
   - Both play one round of the payoff game.  
   - Trust values update based on partner actions.  
3. **Log results** in a pandas DataFrame.  
4. **Analyze** distributions and cooperation rates.  
5. **Visualize** with `matplotlib`, `seaborn`, and `networkx`.

---

## 📊 Visual Outputs

### 🔹 1. Cooperation Rate Over Time
Tracks the fraction of cooperative actions per round.

```python
plt.plot(coop_rate)
plt.title("Cooperation Rate Over Time")
