# Information Systems Technology Audit Report
## Werdy's Kitchen - Web Application & Management System

> **Project Type:** Academic Coursework / College Assignment  
> **Course:** Information Systems Technology Audit (*Audit Teknologi Sistem Informasi*)  
> **Audited Entity:** Werdy's Kitchen (Web Ordering & Admin Platform)  
> **Audit Period:** May 6, 2026 - June 5, 2026  
> **Report Date:** July 5, 2026  
> **Lead Auditor / Student:** Muhammad Daffa Al Fansyah  
> **Frameworks & Standards:** ISO/IEC 27001 (ISMS) | ISO/IEC 25010 (Software Quality) | COBIT Framework  

---

## 🎓 Academic Context & Disclaimer
This repository and its associated reports were compiled as a coursework deliverable for the **Information Systems Technology Audit (*Audit Teknologi Sistem Informasi*)** course. The objective of this project is to apply theoretical and practical IT auditing methodologies, frameworks, and assessment tools to evaluate the operational effectiveness, information security, and software quality of an active digital enterprise system.

---

## 1. Executive Summary

An Information Systems Technology Audit was conducted on the **Werdy's Kitchen** web application ecosystem. The primary objective was to evaluate the operational effectiveness, data security, performance reliability, interface usability, and internal controls supporting the online food ordering and transaction lifecycle.

### Scope of Operations Evaluated:
- **Customer-Facing Portal:** Menu browsing, checkout form processing, and automated order status tracking via email.
- **Admin Management Dashboard:** Authentication mechanisms, menu inventory management, real-time transaction monitoring, order lifecycle status updates, and administrative reporting.

### Overall Auditor Opinion:
In general, the Werdy's Kitchen website demonstrates adequate foundational controls for core business transactions (admin authentication, customer checkout, order data persistence, and transaction history tracking). However, the assessment revealed several **High** and **Moderate** vulnerabilities - notably the absence of automated backup routines, non-functional reporting tools, system instability under concurrent transaction load, and broken UI/routing components - that require remediation to ensure business continuity and service quality.

---

## 2. Audit Deliverables

This repository serves as the official archive for the audit engagement documentation. All deliverables are maintained in PDF format:

| Document | File Name | Description |
| :--- | :--- | :--- |
| **Comprehensive Audit Report** | [INFORMATION SYSTEMS TECHNOLOGY AUDIT REPORT.pdf](./INFORMATION%20SYSTEMS%20TECHNOLOGY%20AUDIT%20REPORT.pdf) | Complete audit report detailing background, audit scope, IT environment analysis, detailed findings, risk ratings, and strategic recommendations. |
| **Audit Evidence Collection** | [EVIDENCE COLLECTION.pdf](./EVIDENCE%20COLLECTION.pdf) | Comprehensive working papers and evidence artifacts collected via Inquiry, Observation, Inspection, CAATs, Re-performance, and Sampling. |

---

## 3. Audit Methodology & Standards Framework

The audit methodology adhered to recognized industry frameworks and rigorous evidence-gathering techniques:

### Applied Standards:
1. **ISO/IEC 27001 (Annex A.12 - Operations Security & Backup):** Evaluated data integrity, resilience, and backup/recovery readiness.
2. **ISO/IEC 25010 (Software Product Quality Model):** Assessed Functional Suitability, Performance Efficiency, Usability, Reliability, and User Interface Aesthetics.
3. **COBIT (Control Objectives for Information and Related Technologies):** Evaluated IT governance, process alignment, and operational controls.

### Evidence Gathering Techniques:
- **Inquiry:** Structured interviews with the business owner and system administrators.
- **Observation:** Direct examination of real-time administrative workflows and order dispatch procedures.
- **Inspection:** In-depth review of database schemas, application configurations, source code, and log files.
- **Re-Performance:** Independent execution of concurrent ordering workflows, automated stress tests, and edge-case transactions.
- **Computer-Assisted Audit Techniques (CAATs):** Automated data validation and query testing on transaction tables.
- **Audit Sampling:** Representative sampling of customer checkout records to verify data completeness and consistency.

---

## 4. Audit Findings & Risk Assessment Matrix

| Ref ID | Finding Description | Evaluation Criteria | Risk Rating | Status |
| :---: | :--- | :--- | :---: | :---: |
| **F-01** | Absence of Scheduled & Automated Database Backups | ISO/IEC 27001 (Annex A.12 - Backup) | **High** | Open |
| **F-02** | Malfunctioning Generate Report Administrative Feature | ISO/IEC 25010 (Functional Suitability) | **High** | Open |
| **F-03** | System Performance Degradation & Crash Under Repeated Ordering | ISO/IEC 25010 (Performance Efficiency) | **High** | Open |
| **F-04** | Dashboard Summary Lacks Real-Time Transaction Synchronization | ISO/IEC 25010 (Functional Suitability) | **Moderate** | Open |
| **F-05** | User Interface & Usability Defects (Navbar logo, banner cropping, missing About Us data) | ISO/IEC 25010 (Usability & UI Aesthetics) | **Moderate** | Open |
| **F-06** | Broken Contact Us / Social Media External Links (HTTP 404) | ISO/IEC 25010 (Functional Suitability) | **Moderate** | Open |

---

## 5. Detailed Findings & Strategic Recommendations

### Finding 1: Absence of Scheduled & Automated Database Backups
- **Risk Level:** **High**
- **Criteria:** ISO/IEC 27001 Annex A.12 specifies that regular backup copies of information, software, and system images must be maintained and tested regularly in line with the agreed backup policy.
- **Condition:** Inquiries and inspections confirmed that database backups are not performed on a regular or automated schedule. No formal offsite or cloud backup repository exists.
- **Root Cause:** Absence of defined backup policies, automated cron/script routines, and storage infrastructure planning.
- **Business & Technical Impact:** High exposure to irreversible data loss in case of server failure, ransomware, or accidental deletion; prolonged recovery time objective (RTO).
- **Recommendation:** Implement automated, scheduled database backups (daily incremental, weekly full) replicated to secure offsite/cloud storage (e.g., AWS S3 / GCP Storage). Establish and test documented Disaster Recovery (DR) procedures periodically.
- **Management Response:** Management acknowledges the finding and has scheduled implementation of automated cloud backups by November 30, 2026.

---

### Finding 2: Malfunctioning Generate Report Administrative Feature
- **Risk Level:** **High**
- **Criteria:** ISO/IEC 25010 (Functional Suitability - Functional Correctness) requires software functions to deliver correct and expected results with the needed degree of precision.
- **Condition:** The Generate Report feature on the admin dashboard fails to compile or export transaction reports upon user request.
- **Root Cause:** Incomplete backend query handling and export pipeline integration between the database and the reporting module.
- **Business & Technical Impact:** Management and administrators are unable to produce automated sales, revenue, and order reconciliation reports, leading to manual workarounds and operational delays.
- **Recommendation:** Refactor the reporting module backend to properly query transaction records, aggregate sales data accurately, and support standard export formats (PDF / Excel / CSV).
- **Management Response:** Management agrees with the recommendation; developer remediation and validation are slated for completion by December 15, 2026.

---

### Finding 3: System Performance Degradation & Crash Under Repeated Ordering
- **Risk Level:** **High**
- **Criteria:** ISO/IEC 25010 (Performance Efficiency - Capacity & Resource Utilization) mandates that systems maintain responsiveness and stability under normal and peak operational load.
- **Condition:** Re-performance testing identified that placing rapid, consecutive orders from desktop clients causes the application to crash, requiring a manual system refresh and a ~10-minute cooldown period before normal operations resume.
- **Root Cause:** Inefficient connection handling, absence of request throttling/rate limiting, and unoptimized database query locking during checkout write operations.
- **Business & Technical Impact:** Service outage during peak sales periods, customer abandonment, loss of revenue, and diminished brand reputation.
- **Recommendation:** Conduct systematic load and stress testing; optimize database indexing and connection pooling; implement request queuing and rate limiting on checkout endpoints to prevent server resource exhaustion.
- **Management Response:** Technical evaluation and server resource optimization will be executed by December 31, 2026.

---

### Finding 4: Dashboard Summary Lacks Real-Time Transaction Synchronization
- **Risk Level:** **Moderate**
- **Criteria:** ISO/IEC 25010 (Functional Suitability - Functional Completeness) dictates that operational metrics presented to system users must reflect current operational reality.
- **Condition:** Key statistical indicators on the admin dashboard (e.g., total products sold, pending orders, revenue tallies) fail to refresh dynamically as new transactions are processed.
- **Root Cause:** Dashboard metrics are statically calculated on initial session load without asynchronous polling or event-driven cache invalidation.
- **Business & Technical Impact:** Administrative personnel receive outdated operational data, potentially delaying order fulfillment and distorting inventory planning.
- **Recommendation:** Integrate WebSocket connections or background asynchronous polling to automatically update dashboard metrics upon incoming order state changes.
- **Management Response:** Dashboard metrics synchronization will be updated by December 15, 2026.

---

### Finding 5: User Interface & Usability Defects
- **Risk Level:** **Moderate**
- **Criteria:** ISO/IEC 25010 (Usability & User Interface Aesthetics) requires interfaces to be visually consistent, proportional across screen sizes, and provide comprehensive corporate information.
- **Condition:** The brand logo is missing from the global navigation bar; homepage hero banners suffer from unconstrained image cropping across standard viewports; the About Us section contains placeholder or incomplete business profile information.
- **Root Cause:** Incomplete front-end asset linking, unoptimized responsive CSS media queries, and missing content population prior to release.
- **Business & Technical Impact:** Degraded user experience (UX), reduced brand credibility, and inadequate customer communication.
- **Recommendation:** Update responsive styling (CSS Flexbox/Grid) for promotional banners, restore valid image asset paths for the brand logo, and finalize comprehensive brand copy on the About Us page.
- **Management Response:** Front-end layout updates and content revisions will be deployed by November 20, 2026.

---

### Finding 6: Broken Contact Us / Social Media External Links
- **Risk Level:** **Moderate**
- **Criteria:** ISO/IEC 25010 (Functional Suitability) requires all navigational elements and external communication channels to direct users to valid destinations.
- **Condition:** Social media icons and links within the Contact Us module return HTTP 404 (Not Found) errors when clicked.
- **Root Cause:** Misconfigured href attributes and placeholder URLs in the production deployment.
- **Business & Technical Impact:** Inhibits customer inquiries, feedback collection, and customer service escalation.
- **Recommendation:** Audit and correct all outbound URL mappings to point to verified, active official Werdy's Kitchen social media profiles and communication channels.
- **Management Response:** Hyperlinks will be remapped and validated by November 20, 2026.

---

## 6. Corrective Action Plan & Remediation Roadmap

| Ref | Action Item Description | Responsible Party | Target Completion Date | Priority | Status |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **A-01** | Establish automated offsite/cloud database backup routines & test restore procedures | Business Owner / Lead Developer | November 30, 2026 | High | Open |
| **A-02** | Refactor and validate the Generate Report export engine (PDF/Excel) | Lead Developer | December 15, 2026 | High | Open |
| **A-03** | Perform load testing, optimize database queries, and implement checkout rate limiting | Lead Developer | December 31, 2026 | High | Open |
| **A-04** | Implement real-time dashboard data synchronization for transaction metrics | Lead Developer | December 15, 2026 | Medium | Open |
| **A-05** | Fix navbar logo rendering, responsive banner cropping, and complete About Us content | UI/UX Designer / Developer | November 20, 2026 | Medium | Open |
| **A-06** | Update and verify all social media hyperlinks and contact routing | Webmaster | November 20, 2026 | Medium | Open |

---

## 7. Conclusion & Governance Remarks

The IT audit concluded that while **Werdy's Kitchen** has established functional transaction processing capabilities, addressing the identified vulnerabilities is imperative for long-term scalability and security. Executing the Remediation Roadmap according to the stipulated timeline will significantly strengthen system resilience, protect organizational data assets, and improve the customer journey.

---

## 👤 Auditor & Course Information
- **Student / Lead Auditor:** Muhammad Daffa Al Fansyah
- **Course Title:** Audit Teknologi Sistem Informasi (*Information Systems Technology Audit*)
- **Repository:** [werdys-kitchen-information-system-audit](https://github.com/daffaalfansyah/werdys-kitchen-information-system-audit)
