	# PSG COLLEGE OF TECHNOLOGY, COIMBATORE - 641 004
### Department of Computer Applications | MCA Semester III Examinations
**Course Code & Name:** 23MXAT — DevOps  
**Assessment:** Practice Test 2 (Model Answer Script)  
**Time Allowed:** 1 Hour 30 Minutes | **Maximum Marks:** 50  

---

## QUESTION 1 (CO2 — Build Automation and Build Server) [Total: 25 Marks]

### 1.a) Analyze how artifact management integrates with source code management in a DevOps pipeline to ensure version traceability and reduce build inconsistencies. [3 Marks — BTL L3]

#### Model Answer:

In an automated DevOps pipeline, **Source Code Management (SCM)** tools (such as Git) and **Artifact Management Repositories** (such as JFrog Artifactory or Sonatype Nexus) operate as complementary pillars that enforce strict separation between human-editable plain-text source code and machine-executable compiled binaries.

```
+------------------+         +-------------------+         +------------------------+
|  Source Code     |  Build  | Compiled Binary   | Archive | Artifact Repository    |
|  Management(Git) | ------> | Artifact (.jar/   | ------> | (Artifactory / Nexus)  |
| (Commit SHA /    |  (CI)   | .war / .docker)   |         | (Immutable Versioned)  |
|  Git Tag)        |         |                   |         |                        |
+------------------+         +-------------------+         +------------------------+
         ^                                                             |
         |=================== Bi-Directional Traceability =============|
```

1. **Ensuring Bi-Directional Version Traceability**:
   - Every build compiled by the Continuous Integration (CI) server extracts the precise **Git Commit SHA** (or Git semantic tag e.g., `v1.4.2`) from SCM and embeds it directly into the artifact's metadata manifest (e.g., `MANIFEST.MF`, Docker image labels, or Helm chart values).
   - Conversely, the Artifact Repository tags the binary artifact with an immutable version number (e.g., `app-service-1.4.2-BUILD#104.jar`). This enables engineers to trace any deployed production binary back to the exact line of source code, author, and pull request that produced it.

2. **Eliminating Build Inconsistencies ("Build Once, Deploy Many")**:
   - Rebuilding binaries from source code for each target environment (Dev, Staging, QA, Production) introduces severe non-determinism due to fluctuating transient third-party dependencies, compiler version variances, and environment differences.
   - Integrating an Artifact Repository enforces the **"Build Once, Deploy Many"** paradigm: the binary is compiled exactly once in the CI pipeline, published to a centralized repository, and promoted across downstream environments without re-compilation. This guarantees 100% environment parity and eliminates runtime inconsistencies.

---

### 1.b.i) Critically analyze the purpose and impact of following Jenkins CLI commands in automating and managing CI/CD pipelines within a DevOps environment. [6 Marks — BTL L4]

#### Model Answer:

The **Jenkins Command Line Interface (CLI)** allows administrators and automated scripts to control Jenkins operations programmatically from external terminals or shell scripts without manual Graphical User Interface (GUI) interaction. This is vital for Infrastructure as Code (IaC), automated agent bootstrapping, and headless pipeline orchestration.

#### Command Breakdown & Impact Analysis:

##### 1. `jenkins-cli build`
- **Syntax**: `java -jar jenkins-cli.jar -s http://jenkins-server:8080/ -auth admin:api_token build <JOB_NAME> -p <PARAM_1>=<VALUE_1> -s -v`
- **Purpose**: Triggers the execution of a specified Jenkins job or pipeline programmatically, allowing input parameters (`-p`), blocking wait until completion (`-s`), and console output tailing (`-v`).
- **Operational Impact**: Enables external Git webhooks, cron schedulers, or upstream deployment pipelines to trigger downstream builds programmatically. It eliminates manual build invocation and forms the backbone of event-driven CI/CD execution.

##### 2. `jenkins-cli update-job`
- **Syntax**: `java -jar jenkins-cli.jar -s http://jenkins-server:8080/ -auth admin:api_token update-job <JOB_NAME> < updated_config.xml`
- **Purpose**: Overwrites the XML configuration file of an existing Jenkins job with new configuration definitions piped from standard input (`stdin`).
- **Operational Impact**: Facilitates automated job administration and **Configuration as Code (CasC)**. When pipeline structures change across hundreds of microservices, administrators can push batch updates to Jenkins job definitions programmatically without manually navigating web UI forms.

##### 3. `jenkins-cli list-nodes`
- **Syntax**: `java -jar jenkins-cli.jar -s http://jenkins-server:8080/ -auth admin:api_token list-nodes [filter]`
- **Purpose**: Queries and displays all worker nodes (agents) registered with the Jenkins Master, along with their current status (e.g., `In Service`, `Offline`, `Building`).
- **Operational Impact**: Crucial for cluster health monitoring and dynamic load balancing. Automated scaling scripts use this command to inspect available build executor capacity before dispatching heavy compilation jobs, enabling automated node provisioning or alerting on offline build agents.

##### 4. `jenkins-cli list-plugins`
- **Syntax**: `java -jar jenkins-cli.jar -s http://jenkins-server:8080/ -auth admin:api_token list-plugins`
- **Purpose**: Outputs an exhaustive list of all installed plugins on the Jenkins Master, including their active status, short names, and exact version numbers.
- **Operational Impact**: Essential for security audits, compliance checks, and disaster recovery. It allows DevOps teams to export plugin manifests, detect outdated/vulnerable plugin versions, and replicate identical Jenkins Master environments during disaster recovery automation.

---

### 1.b.ii) Evaluate the role of test automation in accelerating Continuous Delivery, critically analyzing how its key features—such as parallel execution, test data management, and integration with CI tools—enhance pipeline reliability and feedback speed in DevOps. [4 Marks — BTL L4]

#### Model Answer:

In Continuous Delivery (CD), test automation transforms testing from a manual quality gate into an automated continuous verification process. It provides immediate feedback to developers on every code check-in, preventing defects from leaking into downstream deployment environments.

```
+-----------------------------------------------------------------------------------+
|                           AUTOMATED TESTING PIPELINE                              |
|                                                                                   |
|  +-------------------+     +-------------------------+     +-------------------+  |
|  | Parallel Execution|     | Test Data Management    |     | CI Tool Quality   |  |
|  |  (Split Suites)   |     |  (Containerized DBs)    |     |    Gates (Pass)   |  |
|  +-------------------+     +-------------------------+     +-------------------+  |
|            |                            |                            |            |
|            v                            v                            v            |
|  [ Execution Time: Hours -> Mins ] [ Zero Data Pollution ] [ Instant Dev Feedback]|
+-----------------------------------------------------------------------------------+
```

#### Critical Analysis of Key Features:

1. **Parallel Execution**:
   - **Mechanism**: Test suites (Unit, Integration, UI) are partitioned and executed concurrently across multiple distributed Jenkins agent nodes or containerized test executors.
   - **Impact**: Reduces total feedback cycle time exponentially (e.g., executing 1,000 selenium tests in 10 minutes instead of 8 hours sequentially). Fast feedback allows developers to fix bugs while context is fresh, accelerating delivery velocity.

2. **Test Data Management (TDM)**:
   - **Mechanism**: Automates the provisioning, sanitization, masking, and teardown of stateful test databases using containerized database instances (e.g., Dockerized PostgreSQL) or database snapshot restores.
   - **Impact**: Ensures test isolation and idempotency. It eliminates test flakiness caused by shared polluted database states, guaranteeing that automated test results are 100% deterministic and reliable.

3. **Integration with CI Tools**:
   - **Mechanism**: Test runners (JUnit, TestNG, PyTest) are bound directly into the CI pipeline via declarative steps (`stage('Test')`). CI servers parse execution reports (XML/JSON) and evaluate automated Quality Gates (e.g., SonarQube blocking builds if code coverage falls below 85%).
   - **Impact**: Removes human bias from release decisions. Failed tests automatically abort the pipeline, preventing broken builds from reaching staging or production environments.

---

### 1.c) Critically analyze the Agent based architecture and operational workflow of Jenkins as a DevOps automation server, evaluating how its plugin ecosystem, pipeline-as-code, and distributed build capabilities drive effective CI/CD orchestration. [12 Marks — BTL L5]

#### Model Answer:

#### 1. Architectural Foundation: Master-Agent Distributed Topology

Jenkins employs a decoupled Master-Agent (Controller-Node) distributed architecture designed to offload resource-heavy workloads from the central control plane to dedicated build execution environments.

```
                         +-----------------------------------+
                         |      JENKINS MASTER (CONTROLLER)  |
                         |  - Web UI & REST API              |
                         |  - Job Scheduling & Triggering    |
                         |  - Plugin Engine & Configuration  |
                         |  - Build Log & Artifact Archive   |
                         +-----------------------------------+
                                   |           |
             +---------------------+           +---------------------+
             | (SSH / Inbound JNLP)                  | (SSH / Inbound JNLP)
             v                                       v
+--------------------------+           +--------------------------+
|      JENKINS AGENT 1     |           |      JENKINS AGENT 2     |
| - Executor 1 | Executor 2|           | - Executor 1 | Executor 2|
| - Tooling: Maven, Java   |           | - Tooling: Docker, Go    |
| - Dedicated Workspace    |           | - Dedicated Workspace    |
+--------------------------+           +--------------------------+
```

##### Architectural Components:
- **Jenkins Master (Controller)**: The central administrative control plane. Responsibilities include handling HTTP requests, serving the Web UI, parsing `Jenkinsfile` logic, scheduling build jobs, maintaining job configurations, managing plugins, and storing build logs. The Master **never** executes heavy build steps directly in a production-grade setup.
- **Jenkins Agent (Node/Worker)**: Heavyweight worker instances (virtual machines, physical servers, or dynamic Docker pods) responsible for executing build tasks assigned by the Master. Each agent runs a lightweight executable (JNLP or SSH agent process).
- **Executors**: Computational slots allocated on an Agent node representing parallel processing capacity. One executor runs one build stage at a time.
- **Workspace**: An isolated file system directory created on the Agent node where source code is checked out, binaries are compiled, and test scripts execute.

#### 2. End-to-End Operational Workflow

The lifecycle of an automated CI/CD pipeline in Jenkins follows a precise event-driven sequence:

```
[1. Git Push] ---> [2. Webhook Event] ---> [3. Master Parses Jenkinsfile]
                                                    |
[6. Artifact Archived] <-- [5. Agent Executes] <-- [4. Master Dispatches to Agent]
```

1. **Trigger Phase**: A developer pushes code to a Git repository. A Git Webhook emits a JSON payload to the Jenkins Master endpoint (`/project-web-hook/`).
2. **Orchestration Phase**: The Jenkins Master authenticates the request, fetches the SCM `Jenkinsfile`, and initializes a build execution context.
3. **Node Scheduling & Allocation**: The Master evaluates pipeline node labels (e.g., `agent { label 'docker-runner' }`), locates an available matching Agent with free Executors, and allocates workspace lock.
4. **Task Dispatch & Execution**: The Master sends instructions over the persistent agent connection (SSH/JNLP). The Agent checks out source code, executes build scripts, runs unit tests, and streams real-time console stdout/stderr back to the Master.
5. **Post-Execution & Archiving**: Upon stage completion, the Agent uploads build artifacts to the central repository, notifies the Master of build status (Success/Failure), and clears temporary workspace files. The Master updates build status and sends notifications (Slack, Email).

#### 3. Evaluation of Core CI/CD Orchestration Capabilities

##### A. Extensibility via Plugin Ecosystem
- **Evaluation**: Jenkins features over 1,800 community-contributed plugins, allowing seamless integration with virtually any tool in the DevOps toolchain (Git, Maven, SonarQube, Docker, Ansible, Kubernetes, AWS).
- **Impact**: Transforms Jenkins from a simple cron-like job scheduler into a powerful enterprise orchestration hub.
- **Trade-off/Risk**: Over-reliance on unmaintained third-party plugins can introduce security vulnerabilities, version dependency lock-in, and Master instability during core upgrades.

##### B. Pipeline-as-Code (`Jenkinsfile`)
- **Evaluation**: Defines the entire build, test, and deployment pipeline declaratively inside a version-controlled text file (`Jenkinsfile`) stored at the root of the source repository.

```groovy
// Declarative Pipeline-as-Code Example
pipeline {
    agent { label 'docker-agent' }
    stages {
        stage('Build & Unit Test') {
            steps {
                sh 'mvn clean package -DskipTests=false'
            }
        }
        stage('Quality Gate') {
            steps {
                script {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage('Publish Artifact') {
            steps {
                sh 'jf rt upload "target/*.jar" my-repository/'
            }
        }
    }
}
```

- **Impact**: Ensures pipelines are reviewable, auditable, branchable, and reproducible across environments. It eliminates manual, error-prone GUI job configuration ("click-ops").

##### C. Distributed Build Capabilities
- **Evaluation**: The Master dynamically routes workload tasks based on workload characteristics, platform OS requirements, or current executor utilization across heterogeneous clusters.
- **Impact**: Prevents single-point build bottlenecks and enables high scalability. Using dynamic cloud plugins (e.g., Kubernetes plugin), Jenkins spins up ephemeral pod agents on demand for a build duration and terminates them immediately after, achieving near-zero idle compute costs.

---


---

## QUESTION 2 (CO4 — Configuration Management, Cloud Deployment & DevOps) [Total: 25 Marks]

### 2.a) Evaluate the impact of Blue-Green Deployment on CI/CD pipelines in DevOps, highlighting two key advantages and one potential drawback. [3 Marks — BTL L4]

#### Model Answer:

**Blue-Green Deployment** is a release management strategy that minimizes downtime and risk by maintaining two identical physical or virtual production environments: **Blue** (currently serving live production traffic) and **Green** (idle staging environment receiving the new software release).

```
+-------------------------------------------------------------------------+
|                        BLUE-GREEN DEPLOYMENT ARCHITECTURE               |
|                                                                         |
|                         [ Load Balancer / Router ]                      |
|                                   |                                     |
|                 +-----------------+-----------------+                   |
|                 | (Active Traffic)                  | (Cutover / Idle)  |
|                 v                                   v                   |
|    +-------------------------+         +-------------------------+      |
|    |    BLUE ENVIRONMENT     |         |    GREEN ENVIRONMENT    |      |
|    |  (Live - Version 1.0)   |         |  (New Release - V 2.0)  |      |
|    +-------------------------+         +-------------------------+      |
+-------------------------------------------------------------------------+
```

#### Key Advantages:
1. **Zero-Downtime Releases**: The new version (V2.0) is deployed and fully tested in the Green environment while Blue handles live users. Once verified, the router or load balancer instantly redirects traffic from Blue to Green, achieving seamless release cutover with zero service interruption.
2. **Instant Disaster Rollback**: If unexpected critical errors or memory leaks occur post-cutover in Green, operations teams can immediately revert the load balancer back to Blue (V1.0), restoring system stability in seconds without needing complex hotfixes or re-deployments.

#### Potential Drawback:
1. **High Infrastructure Cost & Database Schema Complexity**:
   - Running two identical production-scale environments doubles operational cloud hosting infrastructure costs.
   - Managing shared persistent databases across both environments requires strict backward and forward database schema compatibility (e.g., expand-contract migration patterns) to prevent data corruption during cutovers.

---

### 2.b.i) Critically evaluate the architecture of Ansible, appraising its agentless design, push-based model, and idempotency principles in enabling scalable and reliable configuration management automation in heterogeneous DevOps environments. [5 Marks — BTL L5]

#### Model Answer:

Ansible is an open-source IT automation engine used for configuration management, application deployment, and infrastructure provisioning across heterogeneous environments (Linux, Windows, Network Routers, Cloud).

```
+------------------------------------------------------------------------------------+
|                                ANSIBLE ARCHITECTURE                                |
|                                                                                    |
|  +-----------------------+           SSH (Port 22) / WinRM                         |
|  | ANSIBLE CONTROL NODE  | ----------------------------------+                 |
|  | - Playbooks (.yml)    |                                   |                 |
|  | - Inventory File      |                                   v                 |
|  | - Core Modules (Py)   |                     +----------------------------+  |
|  +-----------------------+                     |    MANAGED TARGET NODE     |  |
|              |                                 | (Linux / Unix / Windows)   |  |
|              v                                 | - No Persistent Agent!     |  |
|  [ Pushes Transient Modules ]                  | - Requires Python / PowerShell|  |
|                                                +----------------------------+  |
+------------------------------------------------------------------------------------+
```

#### Architectural Evaluation:

1. **Agentless Design**:
   - **Mechanism**: Unlike legacy tools (Puppet, Chef) that require persistent background agent daemons running on every target node, Ansible operates completely agentlessly over standard, secure communication channels: **OpenSSH** for Linux/Unix and **WinRM** for Windows.
   - **Impact**: Eliminates background CPU/RAM resource overhead on managed targets, avoids agent maintenance/bootstrap chicken-and-egg loops, and vastly reduces the network security attack surface.

2. **Push-based Operational Model**:
   - **Mechanism**: Ansible executes centrally from a Control Node. When a playbook runs, Ansible generates small, transient Python scripts for specified tasks, pushes them over SSH to managed target nodes, executes them locally, and immediately removes them upon task completion.
   - **Impact**: Grants centralized control and immediate execution visibility. System administrators control *when* and *where* configurations apply, eliminating the configuration lag inherent in pull-based background polling models.

3. **Idempotency Principle**:
   - **Mechanism**: Ansible modules are declarative rather than imperative. Before making system modifications, a module inspects the target node's current state against the desired state defined in the playbook.
   - **Impact**: If the target state already matches the playbook definition, Ansible marks the task as `ok` and skips execution without side-effects. Re-running an Ansible playbook 1 time or 100 times produces the exact same deterministic system state without duplicate package installs or service crashes.

---

### 2.b.ii) Evaluate how the following Ansible commands collectively enhance safety, visibility, reusability, and security in enterprise-scale DevOps automation workflows. [5 Marks — BTL L5]

#### Model Answer:

#### Command-by-Command Operational Analysis:

##### 1. `ansible-playbook --check`
- **Syntax**: `ansible-playbook site.yml -i inventory.ini --check --diff`
- **Pillar Enhanced**: **Safety & Risk Mitigation**
- **Evaluation**: Performs a dry-run execution of the playbook against managed hosts. It executes module state-checks without applying actual changes to target systems. Combined with `--diff`, it prints exact text/configuration file modifications that *would* occur, allowing engineers to validate changes safely before touching production nodes.

##### 2. `ansible-inventory --graph`
- **Syntax**: `ansible-inventory -i production_hosts.ini --graph`
- **Pillar Enhanced**: **Visibility & Structural Audit**
- **Evaluation**: Outputs a visual, hierarchical ASCII tree structure of the Ansible inventory, showing host group nestings, parent-child group relationships, and mapped node hostnames/IP addresses. It provides immediate structural clarity across complex multi-cloud environment inventories.

##### 3. `ansible -m setup`
- **Syntax**: `ansible all -i inventory.ini -m setup -a "filter=ansible_distribution*"`
- **Pillar Enhanced**: **System Visibility & Dynamic Fact Gathering**
- **Evaluation**: Executes Ansible's core `setup` module on managed nodes to gather comprehensive system facts (hardware attributes, IP addresses, OS kernel versions, disk layouts, environment variables). These facts populate the `ansible_facts` variable space, enabling dynamic, conditional playbook logic.

##### 4. `ansible-galaxy install`
- **Syntax**: `ansible-galaxy install geerlingguy.nginx -p ./roles/`
- **Pillar Enhanced**: **Reusability & Modular Standardization**
- **Evaluation**: Downloads pre-packaged, community-vetted, or enterprise-internal Ansible Roles from Ansible Galaxy (or private Git registries). It promotes modular code reusability, enabling teams to integrate standardized roles for web servers, databases, and security hardening without reinventing the wheel.

##### 5. `ansible-vault encrypt`
- **Syntax**: `ansible-vault encrypt group_vars/all/vault.yml --vault-password-file .vault_pass`
- **Pillar Enhanced**: **Security & Secret Management**
- **Evaluation**: Encrypts sensitive plain-text data files (passwords, API tokens, SSH private keys, TLS certificates) using AES-256 encryption. This allows encrypted secrets to be safely committed directly into version-controlled Git repositories alongside playbooks without risking credential exposure.

---

### 2.c.i) [OPTION 1]

#### 1. Critically evaluate the DevOps capabilities of AWS, Google Cloud, and Microsoft Azure for application development and deployment, analyzing key features and benefits, and justify which platform provides the strongest overall support for end-to-end CI/CD pipelines. [6 Marks — BTL L5]

##### Model Answer:

Modern cloud service providers offer native, fully managed DevOps suites that eliminate self-hosted infrastructure management. The three market leaders—Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP)—exhibit distinct capabilities:

##### Comparative Evaluation Matrix:

| Evaluation Dimension              | Amazon Web Services (AWS)                                                    | Microsoft Azure                                                                                          | Google Cloud Platform (GCP)                                                        |
| :-------------------------------- | :--------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------- |
| **Native CI/CD Toolset**          | **AWS Developer Tools**:<br>CodeCommit, CodeBuild, CodeDeploy, CodePipeline. | **Azure DevOps Services**:<br>Azure Repos, Azure Pipelines, Azure Artifacts, GitHub Actions integration. | **GCP DevOps Suite**:<br>Cloud Source Repositories, Cloud Build, Cloud Deploy.     |
| **Infrastructure as Code (IaC)**  | AWS CloudFormation, AWS CDK (Python/TS).                                     | Azure ARM Templates, Azure Bicep.                                                                        | GCP Deployment Manager, Config Connector.                                          |
| **Kubernetes & Container Native** | Amazon EKS, AWS Fargate, Amazon ECR.                                         | Azure Kubernetes Service (AKS), Azure Container Instances.                                               | Google Kubernetes Engine (GKE) — *Industry Gold Standard*.                         |
| **Enterprise & Hybrid Cloud**     | AWS Outposts.                                                                | Azure Arc, Native Active Directory integration.                                                          | Anthos (Multi-cloud management).                                                   |
| **Key Architectural Strength**    | Deepest cloud-native service integration and granular IAM control.           | Unmatched enterprise IDE (VS Code), enterprise identity, and GitHub integration.                         | Superior containerization, serverless scaling, and AI/data pipeline orchestration. |

##### Justification of the Strongest Platform for End-to-End CI/CD:

**Microsoft Azure (via Azure DevOps Services & GitHub Ecosystem)** offers the **strongest overall support for end-to-end CI/CD pipelines** for modern software development:

1. **Unmatched Ecosystem Integration**: Azure seamlessly bridges developer workstations (VS Code) to version control (GitHub/Azure Repos) and multi-cloud deployment targets through **Azure Pipelines / GitHub Actions**.
2. **Unified Enterprise Work Management**: Azure DevOps provides a single, tightly integrated SaaS platform spanning Agile backlog tracking (Azure Boards), binary hosting (Azure Artifacts), pipeline execution (Azure Pipelines), and manual testing tools (Azure Test Plans).
3. **Cross-Platform Flexibility**: Unlike AWS Developer Tools, which can feel deeply tied to AWS-hosted primitives, Azure Pipelines natively supports cross-platform, multi-cloud deployments (AWS, GCP, on-premise) with first-class matrix builds and extensive extension marketplaces.

---

#### 2. How do microservices, cloud computing, and DevOps complement one another? Appraise the key architectural mechanisms—independent deployment, fault isolation, and technology diversity—that enable enhanced scalability, agility, and continuous delivery. [6 Marks — BTL L5]

##### Model Answer:

Microservices, Cloud Computing, and DevOps form a mutually reinforcing **"Golden Triangle"** of modern software engineering:
- **Microservices** provide the *Architectural Pattern* (decoupling application logic into small, autonomous services).
- **Cloud Computing** provides the *Elastic Infrastructure Platform* (on-demand compute, storage, and container orchestration).
- **DevOps** provides the *Process & Operational Methodology* (automated CI/CD pipelines, culture, and continuous monitoring).

```
                      +-----------------------------------+
                      |      MICROSERVICES ARCHITECTURE   |
                      |   (Loosely Coupled Services)      |
                      +-----------------------------------+
                                   /         \
                                  /           \
                                 /             \
                                v               v
+-----------------------------------+       +-----------------------------------+
|          CLOUD COMPUTING          | <---> |               DEVOPS              |
| (Elastic Container Infrastructure)|       |  (Automated CI/CD & Operations)   |
+-----------------------------------+       +-----------------------------------+
```

##### Critical Appraisal of Key Architectural Mechanisms:

1. **Independent Deployment**:
   - **Mechanism**: Each microservice resides in its own isolated source code repository with its own dedicated CI/CD pipeline.
   - **Synergy**: DevOps pipelines compile, test, and package each microservice into an independent Docker container. Cloud platforms (e.g., Kubernetes on AWS/Azure) execute zero-downtime rolling updates for that specific container without touching other system services.
   - **Impact**: Eliminates massive, risky monolithic release cycles. Teams achieve high release velocity, deploying updates to individual services dozens of times per day.

2. **Fault Isolation (Blast-Radius Reduction)**:
   - **Mechanism**: Services communicate exclusively via network protocols (REST/gRPC) across explicit boundaries, protected by circuit breakers and bulkheads.
   - **Synergy**: If an unhandled exception or memory leak crashes an inventory microservice, cloud orchestrators isolate the failure within that service's container pods. DevOps monitoring tools (CloudWatch/Prometheus) detect the crash, trigger auto-healing restarts, and alert engineers without taking down the entire application stack.
   - **Impact**: Dramatically increases system availability, reliability, and resilience.

3. **Technology Diversity (Polyglot Engineering)**:
   - **Mechanism**: Microservices allow engineering teams to choose the optimal programming language, framework, and database for each specific business domain (e.g., Python for ML, Node.js for API gateways, Go for high-concurrency microservices).
   - **Synergy**: Cloud containerization standardizes deployment inputs: regardless of the inner polyglot code, every service compiles into a standard OCI Docker container. DevOps CI/CD pipelines execute uniform container build and deployment steps.
   - **Impact**: Maximizes developer productivity and technical performance without introducing operational deployment chaos.

---

### 2.c.ii) [OPTION 2 — ALTERNATIVE CHOICE] Evaluate the CI/CD pipeline creation process using AWS services, critically analysing the roles, tasks, and tools of Continuous Integration, Continuous Delivery, and Continuous Deployment in building an effective DevOps workflow. [12 Marks — BTL L5]

#### Model Answer:

#### 1. End-to-End Architectural Pipeline Framework on AWS

AWS provides a suite of cloud-native developer tools designed to construct fully automated, secure, and elastic CI/CD pipelines without requiring management of underlying build servers.

```
+-----------------------------------------------------------------------------------------------------------------+
|                                 AWS CLOUD NATIVE CI/CD PIPELINE ARCHITECTURE                                    |
|                                                                                                                 |
|  +------------------+     +-------------------+     +---------------------+     +----------------------------+  |
|  |   SOURCE STAGE   |     |    BUILD STAGE    |     |   CONTAINER REG.    |     |      DEPLOYMENT STAGE      |  |
|  |  AWS CodeCommit  | --> |   AWS CodeBuild   | --> |     Amazon ECR      | --> |       AWS CodeDeploy       |  |
|  |  (Git Repository)|     | (Docker / Maven)  |     | (Container Images)  |     | (EC2 / ECS / AWS Lambda)   |  |
|  +------------------+     +-------------------+     +---------------------+     +----------------------------+  |
|           \                         /                          \                           /                    |
|            \                       /                            \                         /                     |
|             v                     v                              v                       v                      |
|  =============================================================================================================  |
|                                        AWS CodePipeline (Orchestrator)                                          |
|  =============================================================================================================  |
+-----------------------------------------------------------------------------------------------------------------+
```

#### 2. Critical Analysis of Pipeline Stages, Tasks, and Tools

##### Stage 1: Source Control & Continuous Integration (AWS CodeCommit)
- **Role**: Serves as the central, secure, highly scalable managed Git version control service.
- **Tasks & Execution**:
  - Developers push feature commits to AWS CodeCommit branches.
  - CodeCommit triggers an **AWS EventBridge** rule upon commit detection, emitting an event payload to **AWS CodePipeline** to initiate pipeline execution.
  - Enforces IAM repository access policies, SSH key authentication, and automated branch protection rules.

##### Stage 2: Automated Build & Unit Testing (AWS CodeBuild)
- **Role**: A fully managed, serverless compilation and test service that eliminates the need to provision and manage Jenkins build masters.
- **Tasks & Execution**:
  - CodeBuild dynamically provisions an ephemeral compute container pre-configured with required runtimes (Java, Node.js, Python, Docker).
  - CodeBuild executes the steps declared inside the repository's `buildspec.yml` configuration file:

```yaml
# Sample buildspec.yml for AWS CodeBuild
version: 0.2
phases:
  pre_build:
    commands:
      - echo Logging in to Amazon ECR...
      - aws ecr get-login-password --region $AWS_DEFAULT_REGION | docker login --username AWS --password-stdin $ECR_URI
  build:
    commands:
      - echo Executing unit tests and static code analysis...
      - mvn test
      - echo Building Docker container image...
      - docker build -t $ECR_URI:$CODEBUILD_RESOLVED_COMMIT_HASH .
  post_build:
    commands:
      - echo Pushing container image to Amazon ECR...
      - docker push $ECR_URI:$CODEBUILD_RESOLVED_COMMIT_HASH
artifacts:
  files:
    - imagedefinitions.json
```

  - Output binaries are uploaded to **Amazon S3**, and Docker images are pushed to **Amazon Elastic Container Registry (ECR)**.

##### Stage 3: Automated Deployment & Strategy Management (AWS CodeDeploy)
- **Role**: Automates application deployments to AWS compute services (EC2 instances, AWS Fargate/ECS container tasks, or AWS Lambda serverless functions).
- **Tasks & Execution**:
  - Pulls deployment bundles or ECR container image tags based on the `appspec.yml` manifest file.
  - Executes deployment strategies:
    - **In-Place Deployment**: Stop application, deploy new code, start application (downtime incurred).
    - **Canary Deployment**: Routes 10% of traffic to new code, monitors CloudWatch metrics for 10 minutes, then routes remaining 90%.
    - **Blue/Green Deployment**: Provisions a new Green target group, runs health checks, and shifts traffic via Application Load Balancer (ALB).

##### Stage 4: End-to-End Pipeline Orchestration (AWS CodePipeline)
- **Role**: The central workflow orchestrator that models, visualizes, and automates the progression of code changes through Source, Build, Test, and Deploy stages.

#### 3. Differentiating CI, CD (Delivery), and CD (Deployment) on AWS

| Pipeline Paradigm | Automated Stages | Manual Intervention | AWS Implementation Logic |
| :--- | :--- | :--- | :--- |
| **Continuous Integration (CI)** | Source (CodeCommit) $\rightarrow$ Build & Test (CodeBuild). | None. | Developer commits trigger automated build and unit test execution in CodeBuild. Pipeline halts after publishing verified artifacts to S3/ECR. |
| **Continuous Delivery (CD)** | Source $\rightarrow$ Build $\rightarrow$ Staging Deployment $\rightarrow$ Automated Tests. | **Manual Approval Gate Required**. | Pipeline automatically deploys code to Staging/QA environments. Executes automated acceptance tests. CodePipeline pauses at a **Manual Approval Stage** awaiting an SNS notification approval from an AWS IAM authorized manager before touching Production. |
| **Continuous Deployment (CD)** | Source $\rightarrow$ Build $\rightarrow$ Staging $\rightarrow$ Production Deployment. | **Zero Manual Gates** (100% Automated). | Every commit passing CodeBuild unit tests and staging integration tests is automatically deployed directly into Production via AWS CodeDeploy without human intervention. |

#### 4. Pipeline Hardening, Monitoring, and Failure Rollbacks

1. **IAM Role Hardening**: Enforces the Principle of Least Privilege. CodePipeline, CodeBuild, and CodeDeploy assume separate IAM service roles with strictly scoped permissions.
2. **CloudWatch Alarm Integration**: AWS CodeDeploy monitors **Amazon CloudWatch Alarms** (e.g., HTTP 5xx error rate thresholds or CPU spikes).
3. **Automated Rollback Mechanisms**: If a deployment causes a CloudWatch alarm to trigger during canary traffic shifting, AWS CodeDeploy immediately halts the deployment and executes an automated rollback to the last known good deployment state.
