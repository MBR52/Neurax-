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


