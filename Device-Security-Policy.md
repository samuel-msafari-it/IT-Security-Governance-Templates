**Device Security & Global Fleet Compliance Policy**

**Core Objective:** To ensure 100% of the global device fleet is hardened, encrypted, and audit-ready without creating operational bottlenecks.

- Zero-Trust Device Enrollment: No hardware can access any SaaS Operations (Slack, GitHub, G-Suite) unless it is fully enrolled in the MDM (JumpCloud) environment.

- Hardware-Key Enforced Identity: All device logins must be paired with Hardware-Based Authentication (YubiKeys) to protect against session hijacking and identity-based malicious actors.

- Automated Hardening Standard: Every endpoint must automatically enforce FileVault/BitLocker encryption, a 5-minute screen-lock timeout, and OS patch compliance (N-1 versioning).

- Remote-Wipe Readiness: In the event of device loss or immediate offboarding, a kill-switch protocol must be ready to execute via MDM within 60 minutes to protect enterprise infrastructure.
