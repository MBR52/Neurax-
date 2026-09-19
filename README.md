# Neurax-



## Problem
High-throughput manufacturing environments involve multiple interacting factors such as product quality, production capacity, process conditions, and economics. Defects may be difficult to detect, while production bottlenecks can arise from cycle-time imbalance, work-in-process buildup, downtime, changeovers, low utilization, scrap, and rework.

The challenge becomes more complex when manufacturing lines contain:
- Multiple product variants
- Changing inspection conditions
- Recurring defect families
- Batch-to-batch process drift
- Different station capacities
- Changing operating conditions
---

## Solution
We propose a unified, software-only AI decision-support system that continuously analyzes inspection, production, and economic data to answer:

### Key Questions Addressed
* **What is wrong?** Identify whether a product is acceptable or defective and determine the defect category.
* **Where is the defect?** Localize the defect using bounding boxes, masks, or heatmaps wherever the available data supports localization.
* **How confident is the system?** Provide calibrated confidence and identify uncertain or novel defect patterns instead of forcing an incorrect classification.
* **Why may the defect be happening?** Correlate defect patterns with process parameters, batches, stations, and operating conditions to identify likely contributing factors.
* **Where is production constrained?** Detect bottlenecks using cycle time, capacity, utilization, downtime, work-in-process, and related production-flow indicators.
* **What is the impact?** Estimate how defects and bottlenecks affect throughput, losses, production cost, and expected profitability.
* **What should be investigated?** Generate evidence-based process recommendations that remain simulated and advisory.
The system is designed specifically as an integrated industrial decision-support solution rather than an isolated image classifier or a standalone KPI dashboard.

##Architecture





## 🏗️ System Architecture

```mermaid
flowchart TD
    A[Organizer Datasets] --> B[Data Preprocessing]

    B --> C[Inspection Analysis]
    B --> D[Production Analysis]
    B --> E[Economic Analysis]

    C --> F[Defect Detection]
    C --> G[Defect Pattern Analysis]

    D --> H[Bottleneck Detection]
    D --> I[Cycle Time & Downtime Analysis]

    E --> J[Cost & Profit Analysis]

    F --> K[Root Cause Analysis]
    G --> K
    H --> K
    I --> K

    K --> L[Impact Estimation]
    L --> M[What-If Simulation]

    M --> N[AI Recommendation Engine]
    N --> O[Unified Dashboard]







## 🧭 Approach

Our approach is designed around the **Model 1 manufacturing simulation data**. The production flow consists of **Drilling → Milling → Assembly**, where parts wait in a queue whenever the required resource is unavailable. Each operation uses one dedicated resource and a triangular processing-time distribution.

### 🔹 1. Data Preparation

We first clean and validate the simulation data and organize the available production variables:

* Demand
* Total Parts
* Parts per Hour
* VA Time
* Drilling Waiting Time
* Milling Waiting Time
* Assembly Waiting Time
* Drilling Utilization
* Milling Utilization
* Assembly Utilization

### 🔹 2. Production Performance Analysis

We analyze how **demand affects production performance** by studying:

**Demand → Total Parts → Parts per Hour**

This helps us understand whether increasing demand improves output or creates additional congestion.

### 🔹 3. Queue & Waiting-Time Analysis

The model represents waiting when a required resource is unavailable.

We compare waiting times at:

* Drilling
* Milling
* Assembly

High waiting time indicates that parts are spending more time in the production queue rather than being processed.

### 🔹 4. Bottleneck Detection

We combine **waiting time, utilization, and throughput** to identify the station that is most likely restricting production.

```text
High Utilization
       +
High Waiting Time
       +
Throughput Impact
       ↓
Potential Bottleneck

### 🔹 5. Root-Cause Investigation

After identifying a potential bottleneck, we investigate its relationship with:

* Demand
* Waiting time
* Utilization
* Processing time
* Overall throughput

This helps explain **why the production flow is being restricted**.

### 🔹 6. What-If Simulation

We then test simulated improvement scenarios, such as:

* Reducing waiting time
* Reducing processing time
* Increasing resource capacity

We compare the simulated results with the current system to estimate changes in:

* Parts per hour
* Total output
* Waiting time
* Resource utilization

### 🔹 7. Recommendation

The system converts the analysis into an easy-to-understand recommendation:

> **Which station needs attention, why it is affecting production, and what simulated improvement could be considered.**

All recommendations are **advisory and simulation-based**. The system does not control real manufacturing equipment.

---

## 🔄 End-to-End Flow

```text
Model 1 Dataset
      ↓
Data Preparation
      ↓
Production Analysis
      ↓
Waiting-Time Analysis
      ↓
Utilization Analysis
      ↓
Bottleneck Detection
      ↓
Root-Cause Investigation
      ↓
What-If Simulation
      ↓
Impact Estimation
      ↓
Recommendation
      ↓
Manufacturing Dashboard
```

### 🎯 Our Core Idea

**We don't just measure production. We find what is slowing it down, understand the effect, simulate possible improvements, and present the results as actionable decision support.**
