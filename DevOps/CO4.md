# MCA Academic Question Bank: CO4 — Continuous Deployment, Configuration Management & Cloud Engineering

This question bank provides a comprehensive, university-grade academic resource for **Course Outcome 4 (CO4)** of the **23MXAT DevOps** postgraduate curriculum. It synthesizes official syllabus requirements, historical end-semester examination papers, and practice assessment patterns to deliver Bloom's Taxonomy-aligned questions ranging from fundamental concepts (L2/L3) to complex system designs and scenario evaluations (L4/L5).

## 1. Syllabus & Bloom's Taxonomy Mapping for CO4

**Course Outcome 4 (CO4):** Implement DevOps Continuous Deployment and Cloud deployment in projects.

|   |   |   |   |
|---|---|---|---|
|Sub-Domain|Core Syllabus Topics|Bloom's Levels|Target Exam Marks|
|**Configuration Management (Ansible)**|Architecture, Agentless Control, SSH Communication, Tasks, Playbooks, Roles, Jinja2 Templates, Ansible Vault, Galaxy, Idempotency|L2, L3, L4, L5|Part A (3M), Part B (5M/10M), Part C (12M)|
|**Container Orchestration (Kubernetes / OpenShift)**|Introduction to Kubernetes, Namespaces, Pods, Deployments, Services, ConfigMaps, Secrets, Resource Management|L2, L3, L4|Part A (3M), Part B (5M/6M)|
|**Cloud CI/CD & Infrastructure (AWS & Azure)**|AWS Cloud Ecosystem (CodeCommit, CodeBuild, CodeDeploy, CodePipeline), Azure DevOps Pipelines, Multi-Cloud Comparisons (AWS vs. Azure vs. GCP)|L3, L4, L5|Part B (5M/6M), Part C (12M)|
|**Microservices & Deployment Synergy**|Independent Deployability, Fault Isolation, Scalability, Production Hardening, Blue-Green Deployments|L4, L5|Part B (5M/6M), Part C (12M)|

## 2. Part A: Short Answer Questions (3 Marks Each — BTL L2/L3)

### Question 1: What is Configuration Management, and why is an agentless architecture advantageous in enterprise DevOps?

**Model Answer:** Configuration Management (CM) is the practice of automating, tracking, and maintaining consistency in software, infrastructure, and network configurations across their lifecycle. Ansible utilizes an **agentless architecture**, meaning no custom daemon or software agent needs to be pre-installed on target managed nodes.

**Key Advantages:**

1. **Low Operational Overhead & Security:** Communication occurs over standard protocols (SSH for Linux, WinRM for Windows), eliminating agent installation, patching, and background memory footprint.
2. **Zero Ingress Port Surface Expansion:** Uses existing infrastructure authentication (SSH keys), reducing firewall attack vectors compared to agent-based daemons listening on dedicated network ports.
3. **Immediate Bootstrapping:** New cloud instances or virtual machines can be configured immediately upon network availability without waiting for agent registration pipelines.

### Question 2: Differentiate between Ansible Ad-Hoc commands and Ansible Playbooks.

**Model Answer:**

|   |   |   |
|---|---|---|
|Feature|Ansible Ad-Hoc Commands|Ansible Playbooks|
|**Primary Purpose**|One-off, temporary administrative tasks (e.g., rebooting servers, checking uptime).|Complex, multi-stage configuration automation and deployment orchestration.|
|**Format & Storage**|Executed directly from CLI using `ansible` binary; not stored as files.|Written in structured YAML files (`.yml` or `.yaml`) using the `ansible-playbook` CLI.|
|**Reusability & Logic**|Non-reusable; limited to single module execution without complex conditional logic.|Highly reusable, version-controlled, supporting variables, loops, roles, and handlers.|

### Question 3: Explain the principle of Idempotency in Ansible configuration management.

**Model Answer:** Idempotency is a core property of Ansible execution where applying an operation multiple times produces the exact same system state as applying it a single time, without causing unintended side effects or duplicate modifications.

**Operational Mechanism:** Before executing a task, Ansible checks the target system's actual state against the desired state defined in the playbook task module. If the system is already in the desired state (e.g., a package is already installed at the specified version), Ansible marks the task status as `ok` and skips execution. If a discrepancy exists, Ansible applies the exact change required and marks the task as `changed`. This guarantees safe, repeated playbook runs in production environments.

### Question 4: Define Ansible Roles and explain their directory structure.

**Model Answer:** Ansible Roles provide a standardized, modular framework for organizing playbooks, variables, tasks, handlers, templates, and files into decoupled, reusable units of automation.

**Standard Directory Layout:**

- `tasks/main.yml`: Primary list of operational tasks to be executed by the role.
- `handlers/main.yml`: Handlers triggered by `notify` directives (e.g., service restarts).
- `vars/main.yml` & `defaults/main.yml`: Role variables (high-precedence vs. default values).
- `templates/`: Jinja2 template files (`.j2`) for dynamic file generation.
- `files/`: Static files deployed to managed nodes without modification.
- `meta/main.yml`: Role metadata, author info, and role dependencies.

### Question 5: What is Ansible Vault, and how does it ensure security in Infrastructure as Code repositories?

**Model Answer:** Ansible Vault is a built-in feature of Ansible that enables encryption of sensitive data such as passwords, API tokens, database credentials, and private SSH keys directly within YAML configuration files.

**Security Integration:** By using symmetric encryption (AES-256), Ansible Vault allows encrypted secret files to be safely committed and version-controlled inside public or private Git repositories alongside playbooks, enforcing Infrastructure as Code (IaC) best practices without exposing plaintext credentials. Playbooks decrypt vault files dynamically during runtime using `--vault-password-file` or interactive prompt.

### Question 6: What is a Jinja2 template in Ansible, and how does it enable dynamic configuration?

**Model Answer:** A Jinja2 template is a text file containing variables, expressions, and control structures that Ansible processes to dynamically generate customized configuration files (e.g., `nginx.conf`, `application.properties`) on managed nodes.

**Dynamic Capabilities:**

1. **Variable Substitution:** Replaces placeholders like `{{ http_port }}` with inventory or host-specific variables.
2. **Conditional Logic & Loops:** Evaluates conditionals (`{% if enable_ssl %}`) and iterates over variable arrays (`{% for server in backend_hosts %}`) to build cluster configurations dynamically based on target host facts.

### Question 7: Explain the concept and purpose of a Kubernetes Namespace.

**Model Answer:** A Kubernetes Namespace is a virtual cluster abstraction within a physical Kubernetes cluster that provides logical isolation for resources, workloads, and administrative controls.

**Key Purposes:**

1. **Resource Isolation:** Divides a single physical cluster among multiple teams, projects, or environments (e.g., `development`, `staging`, `production`).
2. **Scope for Quotas & RBAC:** Enforces CPU/Memory resource quotas (`ResourceQuota`) and Role-Based Access Control policies per namespace to prevent resource starvation and unauthorized access across environments.

### Question 8: Define a Kubernetes Pod and explain why containers are wrapped inside Pods rather than deployed directly.

**Model Answer:** A Pod is the smallest deployable atomic computing unit in Kubernetes, representing a single instance of a running process that encapsulates one or more co-located containers.

**Why Containers are Wrapped in Pods:**

1. **Shared Network Namespace:** All containers in a Pod share the same IP address, port space, and localhost network interface (`localhost`), simplifying inter-container communication.
2. **Shared Storage Volumes:** Containers inside a Pod can mount shared volume resources to exchange files or persist state jointly throughout their lifecycle.

### Question 9: What is the role of AWS CodeCommit in a cloud-native CI/CD pipeline?

**Model Answer:** AWS CodeCommit is a fully managed, highly scalable source control service that hosts secure, private Git repositories in the AWS cloud.

**Role in CI/CD:** CodeCommit serves as the central version-controlled source repository that triggers automated AWS CodePipeline workflows. It integrates with AWS IAM for fine-grained repository access control, encrypts code at rest via AWS KMS, and supports webhook integrations and Amazon EventBridge rules to initiate automated build stages upon `git push` events.

### Question 10: Differentiate between AWS CodeBuild and AWS CodeDeploy.

**Model Answer:**

|   |   |   |
|---|---|---|
|Dimension|AWS CodeBuild|AWS CodeDeploy|
|**Primary Function**|Compiles source code, runs unit tests, performs static code analysis, and produces deployable artifacts.|Automates application deployments to compute platforms (EC2, Lambda, ECS, on-premises servers).|
|**Core Specification File**|Managed via a `buildspec.yml` file defining build phases, commands, and artifact exports.|Managed via an `appspec.yml` file defining deployment hooks, lifecycle scripts, and target paths.|
|**Output**|Executable binaries, Docker images, or packaged zip archives exported to S3 or ECR.|Running application revisions deployed across target environment compute nodes.|

### Question 11: Describe the function of AWS CodePipeline in cloud orchestration.

**Model Answer:** AWS CodePipeline is a fully managed continuous delivery service that models, visualizes, and automates the release stages required to deploy software updates.

**Key Functions:**

1. **Pipeline Orchestration:** Connects source repositories (CodeCommit/GitHub), build servers (CodeBuild), testing quality gates, and deployment agents (CodeDeploy/ECS/EKS) into a linear or branching continuous workflow.
2. **Automated Event Gateways:** Triggers downstream execution automatically upon code changes, enforces manual approval stages prior to production, and provides real-time pipeline status monitoring.

### Question 12: How does Ansible ensure safety using the `--check` (dry-run) flag?

**Model Answer:** Executing `ansible-playbook --check` invokes dry-run mode, where Ansible simulates playbook execution against managed inventory nodes without making actual modifications to system files or configurations.

**Operational Value:** Ansible executes state checks and conditional logic, reporting which tasks _would_ produce a `changed` state or trigger error failures. This allows administrators to validate task syntax, variable evaluation, and environmental conditions safely before applying configuration changes to production infrastructure.

## 3. Part B: Analytical & Technical Questions (5 / 6 / 10 Marks — BTL L3/L4)

### Question 1 (10 Marks): Evaluate the architecture of Ansible by appraising its agentless design and communication flow. Demonstrate the usage, exact syntax, and operational purpose of FIVE critical Ansible administrative commands.

#### Model Answer:

##### 1. Architectural Blueprint & Agentless Communication Flow

Ansible operates on a push-based, agentless architecture controlled from a central **Control Node** (Linux management station) that orchestrates target **Managed Nodes** (servers, network devices, cloud instances).

```
                      +-----------------------------------+
                      |        ANSIBLE CONTROL NODE       |
                      |  - Playbooks (.yml)               |
                      |  - Inventory File (hosts)         |
                      |  - Modules & Plugins              |
                      +-----------------+-----------------+
                                        |
                 +----------------------+----------------------+
                 | Push Execution Over Standard Control        |
                 | (OpenSSH / WinRM Protocols)                |
                 v                                             v
    +-------------------------+                   +-------------------------+
    |   MANAGED NODE 1 (Linux)|                   |  MANAGED NODE 2 (Win)   |
    | - Standard Python Run   |                   | - PowerShell / WinRM    |
    | - Ephemeral Execution   |                   | - Ephemeral Execution   |
    +-------------------------+                   +-------------------------+
```

**Operational Execution Steps:**

1. **Inventory & Playbook Parsing:** The Ansible engine reads inventory definitions (`hosts`) and compiles YAML playbooks into executable Python code blocks (modules).
2. **SSH Connection Establishment:** The Control Node establishes secure, concurrent OpenSSH connections to managed hosts using SSH key-pair authentication.
3. **Module Transfer & Execution:** Ansible copies small, self-contained Python scripts (ephemeral execution modules) to `/tmp` on the target nodes, executes them, and captures JSON-formatted stdout/stderr returns.
4. **Cleanup & State Reporting:** Ephemeral scripts are immediately removed from target nodes, and execution summaries (`ok`, `changed`, `failed`) are rendered on the control terminal.

##### 2. Critical Ansible CLI Commands: Purpose & Exact Syntax

###### A. `ansible-playbook --check`

- **Purpose:** Executes a dry-run simulation of a playbook without applying changes to managed nodes. Used for safety validation in CI/CD pipelines.
- **Exact Syntax:**

```bash
ansible-playbook -i inventory/production.ini playbooks/site.yml --check --diff
```

###### B. `ansible-inventory --graph`

- **Purpose:** Parses inventory files and outputs a visual hierarchical tree representation of host groups, parent-child relationships, and target node assignments.
- **Exact Syntax:**

```bash
ansible-inventory -i inventory/hosts.ini --graph
```

###### C. `ansible -m setup`

- **Purpose:** Connects to managed nodes, executes the `setup` module, and returns comprehensive system hardware, OS, IP address, and kernel metadata ("Ansible Facts").
- **Exact Syntax:**

```bash
ansible webservers -i inventory/hosts.ini -m setup -a "filter=ansible_distribution*"
```

###### D. `ansible-galaxy install`

- **Purpose:** Downloads, resolves dependencies, and installs pre-packaged community or enterprise Ansible Roles and Collections from Ansible Galaxy or Git repositories.
- **Exact Syntax:**

```bash
ansible-galaxy role install geerlingguy.nginx -p ./roles/
```

###### E. `ansible-vault encrypt`

- **Purpose:** Encrypts raw YAML files containing sensitive passwords or API keys using AES-256 symmetric encryption, securing secrets in Git repositories.
- **Exact Syntax:**

```bash
ansible-vault encrypt group_vars/all/vault.yml --vault-password-file .vault_pass
```

### Question 2 (6 Marks): Evaluate the synergy of Microservices, Cloud Computing, and DevOps in enabling continuous delivery and enterprise scalability.

#### Model Answer:

Modern enterprise application delivery relies on a mutually reinforcing triad consisting of **Microservices Architecture** (architectural style), **Cloud Computing** (infrastructure platform), and **DevOps** (culture & process automation).

```
                 +-----------------------------------+
                 |           DEVOPS CULTURE          |
                 | - CI/CD Automation & Pipelines    |
                 | - Automated Testing & Deployment  |
                 +-----------------+-----------------+
                                   |
         +-------------------------+-------------------------+
         | Enables Continuous      | Leverages Elastic       |
         | Release Cycles          | On-Demand Compute       |
         v                                                   v
+-----------------------------------+               +-----------------------------------+
|     MICROSERVICES ARCHITECTURE    |               |          CLOUD COMPUTING          |
| - Decoupled Domain Services       |               | - Elastic Compute & Containers    |
| - Independent Deployability       |               | - Managed Cloud Native Services   |
+-----------------------------------+               +-----------------------------------+
```

##### Key Architectural Mechanisms & Benefits:

1. **Independent Deployability & Decoupling:** Microservices decompose monolithic codebases into autonomous services bounded by business contexts. DevOps automated CI/CD pipelines allow individual microservices to be built, tested, and deployed to production independently without requiring full-system regression builds or multi-team freeze windows.
2. **Elastic Scaling & Resource Optimization:** Cloud platforms provide dynamic compute elasticity (Auto Scaling Groups, Kubernetes HPA). Microservices with high load (e.g., payment gateway during peak sales) scale independently on cloud infrastructure without wasting resources on idle services.
3. **Fault Isolation & Resiliency:** Monolithic failures take down entire systems. Microservices isolated inside cloud containers limit blast radiuses. DevOps practices like automated health checks, circuit breakers, and Canary/Blue-Green deployments allow failing microservices to roll back instantly without impacting global application availability.
4. **Technology Diversity & Heterogeneous Toolchains:** Teams select optimal technology stacks per microservice (e.g., Python for ML, Node.js for real-time APIs). DevOps containerization (Docker) standardizes build and deployment artifacts regardless of runtime differences.

### Question 3 (6 Marks): Critically compare the native Cloud DevOps capabilities of AWS, Microsoft Azure, and Google Cloud Platform (GCP).

#### Model Answer:

|   |   |   |   |
|---|---|---|---|
|Comparison Dimension|Amazon Web Services (AWS)|Microsoft Azure|Google Cloud Platform (GCP)|
|**Native CI/CD Services**|**AWS CodeSuite:** CodeCommit, CodeBuild, CodeDeploy, CodePipeline.|**Azure DevOps Services:** Azure Repos, Azure Pipelines, Azure Artifacts, Azure Boards.|**GCP DevOps Suite:** Cloud Source Repositories, Cloud Build, Artifact Registry, Deploy.|
|**Infrastructure as Code (IaC)**|AWS CloudFormation (native YAML/JSON) & AWS CDK (TypeScript/Python/Java).|Azure Resource Manager (ARM) Templates & Azure Bicep (domain-specific language).|Google Cloud Deployment Manager & Native Terraform / OpenTofu integration.|
|**Kubernetes & Container Tooling**|Amazon Elastic Kubernetes Service (EKS) & Amazon Elastic Container Registry (ECR).|Azure Kubernetes Service (AKS) & Azure Container Registry (ACR).|Google Kubernetes Engine (GKE - industry leading) & Artifact Registry.|
|**Enterprise Collaboration**|AWS Management Console, IAM integration, AWS Chatbot.|Deep integration with Azure Active Directory (Entra ID), GitHub Enterprise, and Teams.|Google Cloud Console, Cloud Workstations, Vertex AI pipeline integration.|
|**Cost Optimization & Billing**|Pay-as-you-go, Savings Plans, Spot Instances, CodeBuild per-minute billing.|Azure Hybrid Benefit (Windows/SQL Server discounts), Reserved Instances.|Sustained Use Discounts, Committed Use Contracts, per-second billing granularity.|

##### Strategic Recommendation:

- **AWS** is optimal for mature cloud-native ecosystems requiring deep AWS service integration and highly configurable pipeline stages.
- **Azure** leads for enterprise organizations with existing Microsoft software investments, Active Directory governance, and GitHub Enterprise workflows.
- **GCP** is superior for container-heavy, data analytics, and Kubernetes-centric workloads leveraging native GKE automation.

### Question 4 (5 Marks): Explain the architectural role of Kubernetes Namespaces, Resource Quotas, and Pod specifications in managing multi-tenant cluster workloads.

#### Model Answer:

In enterprise container management, multi-tenancy requires logical segregation, resource containment, and declarative workload specifications.

##### 1. Kubernetes Namespaces

Namespaces create isolated virtual partitions within a physical Kubernetes cluster. They scope resource names, preventing collision across development teams or environments (`dev`, `staging`, `prod`), and establish boundaries for network policies and Role-Based Access Control (RBAC).

##### 2. Resource Quotas (`ResourceQuota`)

`ResourceQuota` objects enforce aggregate compute constraints per namespace, preventing a single tenant from exhausting cluster resources.

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: compute-quota
  namespace: dev-team
spec:
  hard:
    requests.cpu: "4"
    requests.memory: 8Gi
    limits.cpu: "8"
    limits.memory: 16Gi
    pods: "10"
```

##### 3. Pod Declarative Specifications

Pods declare container resource requirements (`requests` for scheduling allocation and `limits` for kernel-enforced CGroup caps) to ensure predictable execution.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: api-service
  namespace: dev-team
spec:
  containers:
  - name: app
    image: myregistry.azurecr.io/api:v1.2.0
    resources:
      requests:
        memory: "512Mi"
        cpu: "250m"
      limits:
        memory: "1Gi"
        cpu: "500m"
```

## 4. Part C: Essay & Scenario-Based Questions (12 Marks Each — BTL L4/L5)

### Question 1 (12 Marks): You are tasked with architecting a automated end-to-end CI/CD pipeline on AWS for a multi-tier microservices web application. Detail the architectural stages, AWS native services involved, declarative configuration specifications (`buildspec.yml` and `appspec.yml`), deployment strategy, and automated rollback mechanisms.

#### Model Answer:

##### 1. Pipeline Architectural Blueprint & AWS Service Mapping

An enterprise AWS CI/CD pipeline automates software progression from source code commit through build, unit testing, security scanning, artifact staging, and zero-downtime deployment.

```
+------------------+     +------------------+     +------------------+     +------------------+
|   SOURCE STAGE   |     |   BUILD STAGE    |     |   DEPLOY STAGE   |     |  PRODUCTION EC2  |
|  AWS CodeCommit  |---->|   AWS CodeBuild  |---->|  AWS CodeDeploy  |---->|   AUTO SCALING   |
| (Git Push Event) |     | (`buildspec.yml`)|     | (`appspec.yml`)  |     |      GROUP       |
+------------------+     +------------------+     +------------------+     +------------------+
                                  |                         |
                                  v                         v
                         +------------------+      +------------------+
                         |  Amazon ECR / S3 |      |  AWS CloudWatch  |
                         | Artifact Store   |      | Rollback Alarms  |
                         +------------------+      +------------------+
```

|   |   |   |
|---|---|---|
|Pipeline Stage|Primary AWS Service|Operational Responsibility & Mechanism|
|**1. Source**|**AWS CodeCommit**|Private Git repository. Triggers CodePipeline execution via EventBridge rules upon code push to `main`.|
|**2. Build & Test**|**AWS CodeBuild**|Ephemeral build environment. Executes `buildspec.yml`, compiles Java/Node.js, runs JUnit tests, scans vulnerabilities, packages Docker images/JARs, and pushes artifacts to Amazon S3 / ECR.|
|**3. Deploy**|**AWS CodeDeploy**|Manages deployment rollout across EC2 Auto Scaling Groups using `appspec.yml`. Executes lifecycle hooks (ApplicationStop, BeforeInstall, AfterInstall, ApplicationStart, ValidateService).|
|**4. Orchestration**|**AWS CodePipeline**|Coordinates workflow execution between stages, enforces manual approval gates prior to production, and manages global state.|

##### 2. Declarative Configuration Specifications

###### A. Build Stage Specification: `buildspec.yml`

```yaml
version: 0.2

phases:
  install:
    runtime-versions:
      java: corretto17
    commands:
      - echo "Installing build dependencies..."
      - apt-get update && apt-get install -y jq
  pre_build:
    commands:
      - echo "Running unit tests and SonarQube static analysis..."
      - mvn clean test
  build:
    commands:
      - echo "Packaging application JAR artifact..."
      - mvn package -DskipTests
  post_build:
    commands:
      - echo "Build completed on $(date)"
      - aws s3 cp target/api-service-1.0.0.jar s3://my-company-artifacts-bucket/builds/

artifacts:
  files:
    - target/api-service-1.0.0.jar
    - appspec.yml
    - scripts/**/*
  discard-paths: no
```

###### B. Deployment Stage Specification: `appspec.yml`

```yaml
version: 0.0
os: linux
files:
  - source: target/api-service-1.0.0.jar
    destination: /opt/microservices/api/
hooks:
  ApplicationStop:
    - location: scripts/stop_server.sh
      timeout: 300
      runas: root
  BeforeInstall:
    - location: scripts/clean_directory.sh
      timeout: 180
      runas: root
  AfterInstall:
    - location: scripts/configure_permissions.sh
      timeout: 180
      runas: root
  ApplicationStart:
    - location: scripts/start_server.sh
      timeout: 300
      runas: root
  ValidateService:
    - location: scripts/validate_healthcheck.sh
      timeout: 180
      runas: root
```

##### 3. Zero-Downtime Deployment Strategy & Automated Rollback Mechanics

To eliminate service downtime during production releases, the architecture implements **Blue-Green Deployment** via AWS CodeDeploy and Application Load Balancers (ALB).

1. **Traffic Shifting:** CodeDeploy provisions a green compute group alongside the active blue group. The new application version is deployed to green instances.
2. **Health Check Validation:** CodeDeploy executes the `ValidateService` hook (`validate_healthcheck.sh`), sending HTTP `GET /health` requests to green instances.
3. **ALB Target Group Rerouting:** Upon 100% health check success, ALB listener rules reroute production traffic from Blue to Green target groups over a 5-minute linear evaluation window.
4. **Automated CloudWatch Alarm Rollback:** AWS CloudWatch tracks metrics (`HTTP 5xx Server Error Rate`, `TargetResponseTime`). If 5xx error spikes exceed 1% during traffic shifting, CloudWatch triggers an alarm that invokes CodeDeploy automated rollback, instantly reverting ALB traffic to the Blue instances and terminating the Green environment.

### Question 2 (12 Marks): Design an enterprise-grade configuration management system using Ansible. Detail the role of Playbooks, Roles, Jinja2 Templates, Ansible Vault, and Inventory management in deploying a multi-tier web application (Nginx Web Server + Node.js API + PostgreSQL Database), including CI/CD validation steps.

#### Model Answer:

##### 1. Enterprise Ansible Architecture & Directory Layout

Deploying a secure, multi-tier web application requires modularizing configuration code into decoupled **Ansible Roles**, dynamic inventories, and encrypted credential storage.

```
ansible-project/
├── ansible.cfg
├── inventory/
│   ├── production.ini
│   └── group_vars/
│       ├── all.yml
│       ├── webservers.yml
│       └── dbservers.yml
├── group_vars/
│   └── dbservers/
│       └── vault.yml            # Encrypted credentials (AES-256)
├── roles/
│   ├── common/                  # System hardening, NTP, SSH keys
│   ├── nginx/                   # Reverse proxy configuration
│   ├── nodejs_api/              # Application runtime & systemd service
│   └── postgresql/              # DB installation, user & schema creation
└── site.yml                     # Master Orchestration Playbook
```

##### 2. Implementation Specs across Core Components

###### A. Dynamic Inventory Definition (`inventory/production.ini`)

```ini
[webservers]
web-node-01.prod.example.com ansible_host=10.0.1.10
web-node-02.prod.example.com ansible_host=10.0.1.11

[appservers]
app-node-01.prod.example.com ansible_host=10.0.2.20
app-node-02.prod.example.com ansible_host=10.0.2.21

[dbservers]
db-master.prod.example.com ansible_host=10.0.3.50

[production:children]
webservers
appservers
dbservers
```

###### B. Ansible Vault Secret Encryption (`group_vars/dbservers/vault.yml`)

To prevent plaintext database credentials from being committed to Git:

```bash
# Command to create/edit encrypted vault file
ansible-vault create group_vars/dbservers/vault.yml
```

_Decrypted contents stored securely inside AES-256 vault:_

```yaml
vault_db_name: enterprise_prod
vault_db_user: db_admin
vault_db_password: "SuperSecretComplexPassword2026!"
```

###### C. Dynamic Jinja2 Nginx Reverse Proxy Template (`roles/nginx/templates/nginx.conf.j2`)

```nginx
server {
    listen {{ http_port | default(80) }};
    server_name {{ domain_name }};

    location / {
        proxy_pass http://app_backend;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}

upstream app_backend {
{% for host in groups['appservers'] %}
    server {{ hostvars[host]['ansible_host'] }}:3000 max_fails=3 fail_timeout=30s;
{% endfor %}
}
```

###### D. Master Orchestration Playbook (`site.yml`)

```yaml
---
- name: Apply Base OS Hardening
  hosts: all
  become: true
  roles:
    - common

- name: Deploy PostgreSQL Database Cluster
  hosts: dbservers
  become: true
  vars_files:
    - group_vars/dbservers/vault.yml
  roles:
    - postgresql

- name: Deploy Node.js Microservices API
  hosts: appservers
  become: true
  roles:
    - nodejs_api

- name: Configure Nginx Reverse Proxy & Load Balancer
  hosts: webservers
  become: true
  roles:
    - nginx
```

##### 3. CI/CD Automated Validation & Safety Pipeline

Before applying Ansible configurations to production servers, automated CI/CD pipelines (Jenkins / GitHub Actions) execute a three-stage validation pipeline:

1. **Syntax & Linting Validation:**

```bash
ansible-lint site.yml
ansible-playbook site.yml --syntax-check
```

1. **Dry-Run State Verification (**`**--check**` **Mode):**

```bash
ansible-playbook -i inventory/production.ini site.yml      --check --diff --vault-password-file .vault_pass
```

1. **Idempotency Testing:** The playbook is executed against an isolated staging environment twice. The second execution must report `changed=0` across all tasks, proving complete operational idempotency.

### Question 3 (12 Marks): Critically evaluate and compare the native DevOps ecosystems of AWS, Microsoft Azure, and Google Cloud Platform (GCP). Propose an architectural decision framework for selecting an optimal cloud provider based on CI/CD capabilities, Infrastructure as Code (IaC), security, and cost optimization.

#### Model Answer:

##### 1. Comparative Evaluation Matrix: AWS vs. Azure vs. GCP

|   |   |   |   |
|---|---|---|---|
|Capability Domain|Amazon Web Services (AWS)|Microsoft Azure|Google Cloud Platform (GCP)|
|**Native CI/CD Pipeline Orchestration**|**AWS CodePipeline & CodeSuite:** Highly modular, AWS-native integration. Excellent IAM role integration, but user interface is functional rather than visual.|**Azure DevOps Pipelines:** Industry-leading UI, extensive marketplace plugins, seamless integration with GitHub, YAML pipelines, and visual release gates.|**Cloud Build & Cloud Deploy:** Serverless, high-speed container build capabilities, native Kubernetes (GKE) release automation.|
|**Infrastructure as Code (IaC)**|**AWS CloudFormation & CDK:** CDK allows writing infrastructure using imperative languages (TypeScript/Python). Strong native resource coverage.|**ARM Templates & Azure Bicep:** Bicep simplifies ARM syntax significantly, offering first-class declarative infrastructure management.|**Deployment Manager & Terraform:** Heavy reliance on HashiCorp Terraform as the de facto IaC tool; Google actively maintains Terraform providers.|
|**Secrets & Security Governance**|AWS Secrets Manager, KMS, IAM Roles for Service Accounts (IRSA).|Azure Key Vault, Managed Identities, Azure Active Directory (Entra ID) RBAC.|Secret Manager, KMS, Workload Identity Federation for GKE.|
|**Container & Kubernetes Native Support**|Elastic Kubernetes Service (EKS) and AWS Fargate (serverless containers).|Azure Kubernetes Service (AKS) with deep Azure CNI network integration.|Google Kubernetes Engine (GKE) - Gold standard for K8s orchestration and Anthos multi-cloud.|
|**Cost Optimization Mechanics**|Spot Instances, Savings Plans, per-minute CodeBuild compute billing.|Azure Hybrid Benefit (reusing Windows/SQL Server licenses), Reserved Instances.|Sustained Use Discounts (automatic), Committed Use, per-second billing granularity.|

##### 2. Architectural Decision Framework for Cloud Provider Selection

```
                                 [ENTERPRISE REQUIREMENT ANALYSIS]
                                                 |
                   +-----------------------------+-----------------------------+
                   |                             |                             |
                   v                             v                             v
       [HEAVY MICROSOFT STACK?]       [K8S & DATA ANALYTICS FOCUS?]    [AWS CLOUD NATIVE & ISV?]
                   |                             |                             |
                   v                             v                             v
        SELECT MICROSOFT AZURE              SELECT GOOGLE CLOUD             SELECT AMAZON AWS
       - Azure DevOps Pipelines            - GCP Cloud Build               - AWS CodePipeline
       - Azure Entra ID / Bicep            - GKE / Terraform               - CloudFormation / CDK
       - Hybrid License Benefits           - Sustained Use Discount        - EKS / Spot Instances
```

##### 3. Key Decision Drivers

1. **Existing Enterprise Ecosystem:** If the organization relies heavily on Microsoft Active Directory, Windows Server, C# .NET, or GitHub Enterprise, **Azure** provides the lowest friction and highest licensing cost efficiency.
2. **Workload Architecture:** For workloads centered around advanced container orchestration, AI/ML pipelines, and Kubernetes (GKE), **GCP** delivers superior operational simplicity and cost savings via per-second billing.
3. **Market Adoption & Service Breadth:** For organizations requiring maximum global region availability, broadest third-party ISV integrations, and serverless compute diversity, **AWS** remains the primary choice.

## 5. Exam Strategy & Topic Probability Distribution Matrix

To maximize academic performance in Course Outcome 4 examinations, study time should be allocated according to historical topic occurrence and mark yield.

|   |   |   |   |
|---|---|---|---|
|Unit Topic|Exam Mark Yield|Probability|Recommended Preparation Focus|
|**AWS CI/CD Pipeline Setup**|12 Marks (Part C)|**98%**|Master `buildspec.yml`, `appspec.yml`, CodeCommit, CodeBuild, CodeDeploy, CodePipeline flow, ALB Blue-Green deployment.|
|**Ansible Architecture & Commands**|10–12 Marks (Part B/C)|**92%**|Learn agentless SSH flow, idempotency, `--check`, `ansible-inventory`, `ansible-vault`, and Role structure.|
|**Multi-Cloud Capabilities Comparison**|6–12 Marks (Part B/C)|**88%**|Memorize comparison matrix between AWS, Azure, and GCP across CI/CD, IaC, and security.|
|**Microservices + Cloud + DevOps Synergy**|5–6 Marks (Part B)|**82%**|Understand independent deployability, fault isolation, elastic scaling, and technology diversity.|
|**Kubernetes Namespaces & Resource Management**|3–5 Marks (Part A/B)|**75%**|Study Pod YAML specs, ResourceQuota, Limits/Requests, and Namespace logical partitioning.|