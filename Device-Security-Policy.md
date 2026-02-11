# Corporate Device & Data Security Policy

## 1. Hardware Standards
* All laptops must be enrolled in the corporate **MDM (Microsoft Intune/JumpCloud)** before user delivery.
* **Hardware-Based Authentication:** All employees are required to use YubiKeys for primary IdP access.

## 2. Access Control
* **Principle of Least Privilege (PoLP):** Access is granted based on Role-Based Access Control (RBAC).
* **MFA:** Multi-Factor Authentication is mandatory for all SaaS applications.

## 3. Offboarding Protocol
* Immediate revocation of **Identity Provider (IdP)** credentials upon termination.
* Remote wipe triggered for all MDM-enrolled devices within 60 minutes of exit.
