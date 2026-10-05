---
layout: default
title: Well-Watch Case Study
---

# Well-Watch: From File Servers to Smart Knowledge Base

> **Note:** This case study describes the architecture of a centralized platform for managing drilling data and financial workflows. No confidential documents or user data are included.

## Abstract
In drilling operations, thousands of Daily Drilling Reports (DDRs) and invoices are generated. Traditional file-server approaches lead to data fragmentation and lack of audit trails. **Well-Watch** was designed to transform these unstructured documents into a trusted, auditable source of truth using metadata-driven search and secure workflows.

## 1. Metadata-Driven Search
Instead of relying on file names, the system extracts key metadata from each document:
- Contractor Name
- Well ID
- Report Type (Daily Report, Mud Log, etc.)
- Date

This allows for powerful SQL-based queries, such as: *"Show all Pressure Tests for Well-24 in January 2023."*

## 2. Secure File Center: "Non-Listable Storage"
To enhance security, the physical storage is designed to be **non-listable**. Users can only access files through unique database addresses, preventing unauthorized browsing of sensitive directories.

## 3. Pre-Invoice Validation Workflow
A visual workflow engine manages the approval process:
1.  **Submission:** Invoice linked to supporting DDRs.
2.  **Review:** Sequential approval by Technical, HSE, and Contract Managers.
3.  **Zero-Comment Rule:** Payments are blocked until all technical comments are resolved.

## 4. Matrix-Based Access Control (ACL)
Inspired by Active Directory, access is granted based on the intersection of **Role** (e.g., Drilling Engineer) and **Domain** (e.g., Project A), ensuring precise data security.

## 5. Conclusion
Well-Watch demonstrates how transitioning from file-based to data-based architectures improves operational efficiency, financial transparency, and data security in industrial environments.

---
*Author: Madjid Goudarzi | [Back to Portfolio](index.md)*
