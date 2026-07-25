# Project BorderShield GRC 🛡️

A Secure Hybrid-Cloud Reference Architecture & Compliance Framework for Sovereign Border Management.

## Project Overview
Project BorderShield GRC is a comprehensive Security Architecture & GRC Blueprint. It demonstrates how to design a resilient, high-availability national border control system that securely splits data processing between an **AWS Public Cloud** environment and a **Sovereign On-Premises Data Centre**, ensuring compliance with strict global privacy frameworks.

This project showcases professional competencies across Cloud Security (CCSK/AWS), Privacy Information Management (ISO/IEC 27701/POPIA), and Enterprise Risk Management (Harvard VPAL).

---

## 🏗️ Hybrid-Cloud Architecture & Trust Boundaries

The system architecture enforces a strict logical and physical separation of data based on classification and data sovereignty requirements:

### 1. AWS Public Cloud (External Edge & Pre-Declaration)
* **Purpose:** Hosts the citizen- and traveler-facing web applications where individuals submit pre-arrival travel declarations.
* **Core Services:** 
  * **AWS Shield & AWS WAF:** Mitigates Distributed Denial of Service (DDoS) attacks and filters malicious web traffic at the perimeter.
  * **Amazon Route 53:** Provides highly available DNS routing and automated failover capabilities across geographic regions.
  * **Amazon S3:** Hosts static assets and public-facing privacy notices.

### 2. Sovereign Private Data Centre (Core Biometric Engine)
* **Purpose:** Hosts the highly sensitive National Biometric Matching Database.
* **Core Infrastructure:** Isolated, on-premises server clusters deployed within the physical borders of the nation-state.

### 3. The Trust Boundary (CCSK Shared Responsibility Flex)
In accordance with the Cloud Security Alliance (CSA) Cloud Controls Matrix (CCM), biometric data (facial scans, fingerprints) represents an absolute risk vector. Under the Cloud Shared Responsibility model, hosting raw, unhashed biometric data on public multi-tenant clouds exposes the sovereign state to third-party sub-processor risks. 

Therefore, a strict **Data Minimisation Boundary** is established:
* Edge kiosks at physical border checkpoints collect biometric inputs.
* The raw facial scan is instantly tokenised/hashed into a mathematical string at the local edge hardware.
* The raw image is permanently destroyed locally within volatile RAM storage.
* Only the mathematical token is transmitted via an encrypted VPN tunnel directly to the **Sovereign Private Data Centre** for database verification. No biometric records ever touch or pass through the AWS public cloud infrastructure.

Initial README update for Project BorderShield.
---

## 📂 Repository Structure

* `compliance-mapping/` : ISO/IEC 27701 & Host_Country POPIA control alignment blueprints.
* `risk-management/` : Enterprise Risk Registers and STRIDE Threat Modelling artifacts.
* `vulnerability-mgmt/` : Technical hardening policies and automated patching SLAs using Qualys VMDR TruRisk metrics.

---

## 📋 Professional Certifications Highlighted
* **CCSK** (Cloud Security Alliance - Certificate of Cloud Security Knowledge)
* **ISO/IEC 27701** (Lead Implementer / Privacy Information Management Systems)
* **Harvard VPAL** (Managing Risk in the Information Age)
* **AWS Certified** Cloud Architecture tracks
* **Qualys VMDR** Vulnerability Management Fundamentals
