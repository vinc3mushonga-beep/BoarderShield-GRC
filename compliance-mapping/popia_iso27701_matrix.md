# ISO/IEC 27701 to Host_Country POPIA Compliance Mapping Matrix

## Executive Summary
This control matrix demonstrates how **Project BorderShield GRC** maps international privacy management standards (**ISO/IEC 27701:2019**) directly to the statutory conditions of the **Protection of Personal Information Act (POPIA) No. 4 of 2013** of Host_Country. 

By aligning cloud-edge tokenisation mechanisms and sovereign data governance to these controls, the architecture guarantees lawful, accountable processing of sensitive traveler data.

---

## 📊 Regulatory Mapping Table

| POPIA Condition & Section | ISO/IEC 27701 Clause / Control | Project BorderShield GRC Implementation Mechanism |
| :--- | :--- | :--- |
| **Accountability** (Sec 8) | **5.2.1** (Understanding the organization) & **6.2.1.1** (Information security roles) | Designates a formal Information Officer role; maps clear data governance ownership across hybrid environments. |
| **Processing Limitation** (Sec 9-12) | **7.2.1** (Identify lawful basis) & **7.2.2** (Determine purpose) | Captures traveler consent via AWS-hosted pre-declaration frontend; enforces data minimization at the edge kiosk. |
| **Purpose Specification** (Sec 13-14) | **7.2.4** (Retention) & **7.2.5** (Disposal) | Automates immediate destruction of raw biometric images after mathematical tokenization and transfer. |
| **Further Processing Limitation** (Sec 15) | **7.3.1** (Identify purpose for onward transfer) | Restricts backend traveler ledger processing exclusively to identity verification; blocks downstream commercial usage. |
| **Information Quality** (Sec 16) | **7.2.7** (Accuracy and quality) | Integrates edge-validation rules to block incomplete passport or biometric inputs before network transmission. |
| **Openness** (Sec 17-18) | **7.3.2** (Provide privacy notice) | Hosts a public-facing Privacy Notice on AWS S3 outlining collection intent, data destination, and traveler rights. |
| **Security Safeguards** (Sec 19-22) | **6.12.1.1** (Encryption) & **6.13.1.1** (Data breach notification) | Mandates AES-256 for data at rest and TLS 1.3 for data in transit; deploys Amazon CloudWatch alerts for breach detection. |
| **Data Subject Participation** (Sec 23-25) | **7.3.5** (Access, correction, erasure) | Establishes a secure API gateway path allowing travelers to formally request, view, or correct profile data. |

---

## 🔒 Deep-Dive Governance Architectural Analysis

### Data Minimisation of Biometric Identifiers
Under POPIA Section 26, biometric data is classified as **Special Personal Information**, commanding the highest level of regulatory scrutiny. Project BorderShield protects this data using an **Edge-Isolation Strategy**:
1. **Zero-Persistence Local Cache:** The traveler's facial image captured at the gate is held exclusively in volatile RAM. 
2. **Cryptographic Mathematical Representation:** The system instantly converts the image into a unique 256-character mathematical hash.
3. **Instant Erasure:** The raw visual asset is permanently cleared from the local machine before network transmission. Only the non-reversible hash is queried against the backend Sovereign Data Centre.

### Incident Response & Breach Notification (POPIA Sec 22).
In the event of a suspected security compromise, the architecture leverages **Amazon CloudWatch** integrated with **AWS Lambda** to automate the incident response path. If an unauthorized attempt to access the edge network is detected:
* System logs are securely forwarded to a write-once-read-many (WORM) storage archive.
* Automated workflows initiate a security notification template formatted to comply with the Host-Country Information Regulator's mandatory notification timelines.
