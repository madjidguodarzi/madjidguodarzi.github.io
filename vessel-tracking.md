---
layout: default
title: Well-Watch Case Study
---

# From Operational Data to Industrial AI: A Case Study in Offshore Fleet Management

> **Note:** This article documents the architectural decisions and engineering challenges of a proprietary industrial system developed over 6 years. Due to confidentiality agreements, no source code or raw operational data is shared. The focus is on **Domain Modeling**, **Data Engineering Pipelines**, and **System Architecture**.

## Abstract
In offshore logistics, a significant portion of critical decision-making data comes directly from vessels and the operational environment. These data are often unstructured, incomplete, and inconsistent. This case study details the development of an **Operational Data Engineering Layer** that transforms raw vessel reports into reliable, structured information for enterprise systems (ERP) and future Industrial AI applications.

## 1. The Core Problem: Why Generic ERPs Fail
Generic ERP systems assume clean, static data. However, offshore operations are dynamic:
- Data arrives via low-bandwidth satellite links.
- Vessels serve multiple projects simultaneously.
- Contracts involve dynamic clauses (Off-hire, Laytime).

The gap between **Raw Operational Reality** and **Structured Enterprise Needs** required a custom middleware solution.

## 2. Key Engineering Challenges & Solutions

### 2.1. Data Validation Pipeline
We implemented a two-stage validation pipeline:
1.  **Client-Side:** Validates range, format, and mandatory fields before sending via expensive satellite links.
2.  **Server-Side:** Final structural validation and registration in the central database.

### 2.2. Cost-to-Event Linkage (Data Quality Gate)
To prevent "orphan records," every cost entry must be linked to a valid operational event (e.g., `Travel ID` or `Port Call ID`). This ensures traceability: **Cost → Event → Contract → Operation**.

### 2.3. Contract-Vessel Abstraction
Instead of linking contracts directly to physical vessel IDs, we used an **"Operational Slot"** concept. This allows vessel substitution without breaking the historical continuity of the contract.

### 2.4. Time-Weighted Cost Allocation
For vessels serving multiple projects, costs are allocated based on actual active duration:
$$ Share(Project_i) = \frac{Duration(Project_i)}{Total\_Active\_Duration} $$

### 2.5. Three-Way Fuel Reconciliation
The system compares three independent sources to detect anomalies:
1.  Crew Reports
2.  Engine Logs ($Engine Hours \times SFOC$)
3.  Tank Soundings

## 3. Path to Industrial AI
This operational data foundation now enables advanced analytics:
- **Descriptive Digital Twin:** 2D map-based tracking with historical playback.
- **Predictive AI (Future Work):** Using this clean data to train Physics-Informed ML models for fuel consumption prediction and anomaly detection.

## 4. Lessons Learned
1.  **Data Quality is Architectural:** You cannot build AI on dirty data.
2.  **Domain Modeling Matters:** Software must reflect real-world concepts like "Operational Slots."
3.  **Legacy Systems hold Knowledge:** Extract business logic before rewriting.

---
*[📥 Download Full PDF Version](/articles/vessel-tracking-fa.md)

*Author: Madjid Goudarzi | [Back to Portfolio](index.md)*

