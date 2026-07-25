# Harvard VPAL-Aligned Enterprise Risk Register

## 1. Methodology & Risk Framework
This Enterprise Risk Register uses the core risk management methodologies taught in the **Harvard VPAL (Managing Risk in the Information Age)** curriculum. Risks are formally evaluated based on their operational impact, regulatory consequences, and likelihood.

### Risk Calculus Formulas
* **Inherent Risk Rating:** Evaluated *before* any operational or technical security controls are applied.
* **Residual Risk Rating:** The remaining exposure *after* implementing Project BorderShield's hybrid-cloud controls.
* **Risk Scoring Matrix:** Calculated on a 1 (Low) to 5 (Critical) scale: `Impact x Likelihood = Risk Score`.

---

## 2. Project BorderShield Risk Register

| Risk ID | Risk Description | Inherent Risk (I x L) | Implemented Control Mechanism (Architecture / GRC) | Control Effectiveness | Residual Risk (I x L) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **RSK-001** | **Network Disruption at Edge:** Remote land borders lose connectivity to the sovereign data centre, halting commercial trade and passport matching. | **High** (4 x 4 = 16) | Implementation of an encrypted, localized edge-node cache. Passport processing falls back to a limited offline verification mode. | **Highly Effective** | **Low** (4 x 1 = 4) |
| **RSK-002** | **Biometric Data Exfiltration:** Attackers compromise edge kiosks to steal raw visual passport photos and facial biometric imagery. | **Critical** (5 x 4 = 20) | **Data Minimisation:** Real-time RAM-only mathematical tokenisation. Raw imagery is instantly deleted at the edge; zero persistent storage. | **Highly Effective** | **Low** (5 x 1 = 5) |
| **RSK-003** | **Perimeter DDoS Attack:** Sophisticated actors target traveler web frontends with massive traffic volumes, freezing the pre-declaration process. | **High** (4 x 4 = 16) | Integration of **AWS Shield Advanced**, **AWS WAF**, and **Amazon Route 53** globally distributed multi-region failover. | **Effective** | **Medium** (4 x 2 = 8) |
| **RSK-004** | **Regulatory Penalty (POPIA):** Changes to South African data sovereignty rules trigger structural non-compliance fines regarding citizen data. | **High** (5 x 3 = 15) | **Sovereign Isolation:** Zero citizen ledger or backend database infrastructure is hosted on the public cloud tenancy. Data sits entirely inside local hardware. | **Highly Effective** | **Low** (5 x 1 = 5) |
| **RSK-005** | **Edge Unit Physical Tampering:** Malicious actors attempt to physically extract hard drives from unmanned terminal kiosks to clone images. | **High** (3 x 4 = 12) | Mandatory hardware-accelerated **Full Disk Encryption (AES-256)** bound to localized hardware **TPM 2.0** chips. | **Effective** | **Low** (3 x 1 = 3) |

---

## 3. Risk Treatment Strategy & Escalation Paths

### Residual Risk Acceptance Criteria
* **Score 1–5 (Low):** Formally accepted by the Information Officer. Monitored quarterly via continuous Qualys VMDR configuration checks.
* **Score 6–12 (Medium):** Requires active operational monitoring. System logs are piped to Amazon CloudWatch with automated alerting thresholds configured for immediate investigation.
* **Score 13+ (High/Critical):** Triggers an immediate halt to deployment. The architecture must be re-engineered or augmented with fallback hardware before achieving formal sign-off.
