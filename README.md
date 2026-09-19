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



## Approach

Our solution follows a simple idea:

**Detect → Understand → Connect → Simulate → Recommend**

### 1. Data Collection

We bring together the available manufacturing data:

- Inspection and quality data
- Production data
- Process conditions
- Product and batch information
- Economic data

### 2. Data Preparation

The collected data is cleaned and prepared by:

- Handling missing values
- Removing invalid or duplicate records
- Standardizing data
- Creating useful features
- Combining related datasets

### 3. Quality Analysis

The system analyzes inspection data to identify:

- Acceptable products
- Defective products
- Defect types and locations, when available
- Unusual or uncertain cases

### 4. Production and Bottleneck Analysis

We analyze:

- Cycle time
- Throughput
- Utilization
- Downtime
- WIP
- Changeover time
- Station capacity

This helps identify stations that may be restricting production.

### 5. Root-Cause Analysis

The system connects quality problems with production and process conditions.

It looks for patterns across:

- Stations
- Batches
- Product variants
- Process conditions
- Operating conditions
- Time periods

The system identifies possible contributing factors instead of treating correlation as confirmed causation.

### 6. Impact Estimation

The system estimates the effect of identified problems on:

- Production output
- Scrap
- Rework
- Downtime
- Cost
- Revenue
- Profit or margin

### 7. What-If Simulation

Users can test possible improvement scenarios without affecting the real production system.

For example:

Defect Rate ↓  
→ Scrap/Rework ↓  
→ Good Output ↑  
→ Potential Cost Impact ↓

### 8. Recommendation Engine

The system combines the analysis and generates evidence-based recommendations.

Instead of only showing that a problem exists, it explains:

- Where the problem is
- What factors may be contributing
- How it affects production
- What improvement can be investigated

### 9. Unified Dashboard

The final dashboard brings everything together:

**Quality → Production → Root Cause → Impact → Recommendations**

## System Flow
```mermaid
flowchart TD
    A[Manufacturing Data] --> B[Data Preparation]
    B --> C[Quality Analysis]
    B --> D[Production Analysis]
    B --> E[Process Analysis]
    B --> F[Economic Analysis]

    C --> G[Pattern Analysis]
    D --> G
    E --> G
    F --> G

    G --> H[Root Cause Analysis]
    H --> I[Impact Estimation]
    I --> J[What If Simulation]
    J --> K[Recommendation Engine]
    K --> L[Unified Dashboard]
    L --> M[Human Decision]
