Here is the exam-oriented **Question Bank for CO 4 / UNIT 4 — Cloud Security**, grounded in the official syllabus and compiled directly from the semester examination papers (November 2024, March 2025, November 2025, and March 2026).

---

# **CO 4 UNIT 4 — Cloud Security**

> **Course Outcome (CO4)**: _Design solutions for managing the core issues of cloud security._  
> **Unit Marks Weightage**: **25 Marks** (Question 4 in every end-semester examination paper).

---

## **Part A: Concept & Short Answer Questions (3 Marks Each)**

1. **Core Capabilities of Cloud Security Architecture**
    
    - _Question_: State the three core capabilities of a cloud security architecture.
    - _Model Answer_:
        1. **Data Security**: Encryption at rest/transit, key management, and data loss prevention (DLP).
        2. **Application Security**: Secure API endpoints, web application firewalls (WAF), and tenant isolation.
        3. **VM & Infrastructure Security**: Hypervisor hardening, virtual network micro-segmentation, and patch management.
2. **Authentication vs. Authorization**
    
    - _Question_: Distinguish between authentication and authorization in cloud security platforms.
    - _Model Answer_:
        - **Authentication**: Verifies _who_ a user or system is (e.g., passwords, MFA, smart cards).
        - **Authorization**: Determines _what_ actions or resources an authenticated user is permitted to access (e.g., RBAC, IAM policies).
3. **Phishing & Crypto-Mining Threat Analysis**
    
    - _Question_: Identify the security threats involved when an attacker compromises user credentials via phishing to deploy a cryptocurrency mining application.
    - _Model Answer_:
        - **Primary Threat**: Credential theft via social engineering (phishing).
        - **Secondary Threat**: Privilege escalation, resource hijacking (cryptojacking), and financial loss through unexpected compute resource consumption.
4. **Autonomic Security Element**
    
    - _Question_: Sketch the logical structure of an autonomic security element.
    - _Model Answer_: Draw the **MAPE-K** loop (Monitor, Analyze, Plan, Execute, Knowledge base) interacting with a managed cloud resource via sensors and effectors.
5. **IAM Lifecycle Phases**
    
    - _Question_: List the core phases involved in the Identity and Access Management (IAM) lifecycle.
    - _Model Answer_:
        - Provisioning \(\rightarrow\) Authentication \(\rightarrow\) Authorization \(\rightarrow\) Governance / Audit \(\rightarrow\) Deprovisioning.

---

## **Part B: Analytical & Descriptive Questions (5 Marks Each)**

1. **Shared Responsibility Model**
    
    - _Question_: Analyze the Shared Responsibility Model of cloud security in terms of Cloud Service Provider (CSP) and Cloud Consumer obligations across IaaS, PaaS, and SaaS.
    - _Model Answer Outline_:
        - **IaaS**: Provider manages physical infrastructure and hypervisors; Consumer manages OS, runtime, middleware, network rules, and data.
        - **PaaS**: Provider manages underlying hardware, OS, and application runtimes; Consumer manages application code and access control.
        - **SaaS**: Provider manages the full stack; Consumer manages user access, endpoint devices, and data classification.
2. **Single Sign-On (SSO) & Multi-Factor Authentication (MFA)**
    
    - _Question_: Highlight the importance of Single Sign-On (SSO) with an apt example, and categorize the three factors of authentication (Something you know, Something you have, Something you are).
    - _Model Answer Outline_:
        - **SSO**: Centralizes credential management, eliminates password fatigue, and enables instant access revocation across all enterprise cloud apps (e.g., Okta/Azure AD for Google Workspace & Salesforce access).
        - **Authentication Factors**:
            - _Something you know_: Passwords, PINs.
            - _Something you have_: Smart cards, push notifications, hardware tokens.
            - _Something you are_: Fingerprint scans, facial recognition, geographic location.
3. **Insider Threat & Departing Employee Security Risks**
    
    - _Question_: Identify the cloud security risk involved when departing employees take proprietary materials or expose sensitive data, and explain how this risk can be handled.
    - _Model Answer Outline_:
        - **Risk Identification**: Insider Threat / Data Exfiltration (unauthorized intellectual property theft out of malice or personal gain).
        - **Mitigation Technical Controls**: Automated IAM offboarding/deprovisioning upon HR status change, Data Loss Prevention (DLP) alerts on bulk downloads, and User & Entity Behavior Analytics (UEBA).
4. **SaaS Security Practices & Application Security Risks**
    
    - _Question_: Describe SaaS security practices and mention any two application security risks associated with public SaaS deployments.
    - _Model Answer Outline_:
        - **Security Practices**: Multi-tenant data isolation, TLS 1.3 in-transit encryption, periodic penetration testing, and role-based data masking.
        - **Key Risks**: Multi-tenant data leakage and insecure third-party API integrations.

---

## **Part C: Comprehensive & Scenario-Based Questions (12 Marks Each)**

1. **Phased IAM Plan for Startups & Enterprises** _(Appeared in March 2026 & Nov 2025)_
    
    - **Question**:  
        A rapidly growing tech start-up with 200 employees, multiple cloud-based applications, and contractor collaborations is experiencing security vulnerabilities due to manual security processes.  
        _(Alternatively)_: A manufacturing company migrating its multi-tier customer web application (Web server, App server, DB server with sensitive customer data) to a public cloud.  
        **Tasks**:
        1. Detail the lifecycle phases of IAM.
        2. Recommend a phased IAM implementation plan prioritizing immediate security and governance needs.
    - **Model Answer Key**:
        - **Part 1 — Lifecycle (4 Marks)**: Explain Provisioning (account creation), Authentication (identity check), Authorization (privilege assignment), Governance (logging/audits), and Deprovisioning (revocation).
        - **Part 2 — Implementation Plan (8 Marks)**:
            - _Phase 1 (Immediate - Identity Baseline)_: Centralized SSO with mandatory MFA for all 200 employees and contractors; enforce Role-Based Access Control (RBAC).
            - _Phase 2 (Access Governance & Principle of Least Privilege)_: Implement Attribute-Based Access Control (ABAC) for database tier; restrict contractor access via time-bound temporary credentials.
            - _Phase 3 (Lifecycle Automation & Auditing)_: Deploy automated deprovisioning scripts tied to HR/contract end dates; set up continuous CloudTrail/audit logging.
2. **Cloud Security Architecture & Data Protection Plan** _(Appeared in Nov 2024)_
    
    - **Question**:  
        A company recently migrated its critical applications to the cloud, and there is growing concern about data security. As a cloud architect, devise a comprehensive plan to address these security concerns and ensure the integrity of sensitive data.
    - **Model Answer Key**:
        - **Data Security Layer (4 Marks)**: AES-256 client-side/server-side encryption at rest, Key Management Service (KMS) with annual rotation, and DLP policies.
        - **Application & VM Security Layer (4 Marks)**: Micro-segmentation with Virtual Private Cloud (VPC) subnets, Web Application Firewall (WAF), and hypervisor hardening.
        - **Identity & Access Governance (4 Marks)**: Zero-Trust Network Architecture (ZTNA), least-privilege policies, and continuous runtime threat monitoring.
3. **Phishing Incident Governance & Threat Mitigation** _(Appeared in Nov 2025)_
    
    - **Question**:  
        A financial institution uses cloud collaboration tools. An attacker launches a phishing campaign targeting user credentials to elevate privileges and deploy a cryptocurrency mining application, causing unexpected cloud billing spikes.  
        **Tasks**:
        1. Report the application security threats involved.
        2. Explain the security governance challenges.
        3. Recommend technical solutions to prevent future occurrences.
    - **Model Answer Key**:
        - **Security Threats (4 Marks)**: Phishing (credential theft), unauthorized privilege escalation, and compute resource hijacking (cryptojacking).
        - **Governance Challenges (4 Marks)**: Lack of real-time anomaly detection, delayed billing alert responses, and permissive execution policies.
        - **Technical Solutions (4 Marks)**: Enforce hardware-token MFA (FIDO2/YubiKey), set cloud cost budget alert triggers, and enforce container image signature verification.

---

## **CO4 Quick Revision Cheat Sheet**

|Topic|Repeat Rate|Target Marks|Core Focus Area|
|:--|:-:|:-:|:--|
|**IAM Lifecycle & Phased Implementation Plan**|**100%**|**12 Marks**|5 Lifecycle steps + Start-up/Enterprise scenario roadmap|
|**Shared Responsibility Model**|**75%**|**5 Marks**|CSP vs Consumer split across IaaS, PaaS, SaaS|
|**Insider Threat Handling**|**75%**|**5 or 12 Marks**|Departing employee data theft & automated deprovisioning|
|**Autonomic Security Structure**|**50%**|**3 or 5 Marks**|MAPE-K loop diagram|
|**Authentication vs Authorization / MFA**|**100%**|**3 to 5 Marks**|3 Auth factors diagram & SSO importance|

---

💡 _Would you like me to combine all four CO question banks into a single downloadable PDF study guide, or generate a 100-mark mock exam paper based on these exact high-probability questions?_