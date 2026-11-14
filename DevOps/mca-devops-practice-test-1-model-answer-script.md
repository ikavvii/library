
### QUESTION 1 (Course Outcome 1 — CO1)

---

#### Q1(A) [3 Marks]
**Identify and explain any two prominent DevOps team topologies, outlining the key benefits of each for a modern software development organization.**

##### Answer:
DevOps Team Topologies (conceptualized by Matthew Skelton and Manuel Pais) classify how organizations structure interactions between software development (Dev) and IT operations (Ops) to eliminate organizational friction.

- **Topology Type 1: Fully Integrated / Cross-Functional Squad**
  - Developers, QA engineers, and Operations specialists are embedded within the same autonomous product team. There is no separate operations department; the team holds joint end-to-end accountability from code design to production monitoring ("You build it, you run it").
  - **Key Benefits**: Eliminates the traditional "Wall of Confusion" and handoff latency between development and ops. Aligns team incentives around both delivery velocity and operational stability.

- **Topology Type 3: Platform Engineering / Ops as a Service**
  - Operations functions as an internal Platform Engineering team. They build and maintain a self-service Developer Platform (PaaS, CI/CD templates, infrastructure abstractions) consumed by application development teams via standardized APIs.
  - **Key Benefits**: Enables developer autonomy without requiring every software engineer to master deep infrastructure orchestration. Standardizes security, compliance, and governance across dozens of enterprise feature teams.

---

#### Q1(B) [10 Marks]
**(i) Perform a critical assessment of the various features, advantages, and disadvantages of Git for the Source Code Management aspect of DevOps. [4 Marks]**

**(ii) Briefly explain the following commands of Git with purposes and full syntax with options and arguments: (1) `git push`, (2) `git pull`, (3) `git merge`, (4) `git rebase`, (5) `git commit`, (6) `git branch`, (7) `git remote`. [6 Marks]**

##### Answer:

##### Part (i): Critical Assessment of Git in DevOps SCM
Source Code Management (SCM) forms the foundation of any DevOps pipeline. Git is a Distributed Version Control System (DVCS) designed around a Directed Acyclic Graph (DAG) commit history and content-addressable storage using cryptographic hashing (SHA-1/SHA-256).

| Architectural Feature | Strategic Advantage in DevOps | Limitation / Operational Challenge |
| :--- | :--- | :--- |
| **Fully Distributed Architecture** | Every developer possesses a full repository clone locally. Enables offline commits, local branch creation, and rapid historical inspection without network latency. | Repository size grows if large binary files or build artifacts are committed without LFS. |
| **Lightweight Branching Engine** | Creating and switching branches takes milliseconds (updating reference pointers). Enables short-lived feature branches and isolated development. | Complex branch topologies (e.g., unmanaged GitFlow) can lead to integration challenges if branches remain unmerged for extended periods. |
| **Cryptographic Integrity (DAG)** | Hashed object storage guarantees immutability and complete auditability of code history across automated pipelines. | Learning curve for advanced historical manipulation (`rebase -i`, `reflog`, reset operations) requiring careful execution. |
| **Non-Linear Merge Strategies** | Supports automated 3-way recursive and ORT merges, integrating seamlessly with automated CI build triggers. | Resolving complex binary or structural merge conflicts requires developer evaluation. |

##### Part (ii): Git Command Specifications

###### 1. `git push`
- **Purpose**: Uploads local repository branch commits to a specified remote repository reference, updating remote tracking pointers.
- **Full Syntax**: `git push [options] [<repository>] [<refspec>...]`
- **Options & Arguments**:
  - `-u` / `--set-upstream`: Sets the default tracking remote branch for future execution.
  - `--force-with-lease`: Safely updates remote branch history only if no unexpected commits exist on the remote.
  - `--delete`: Removes a specified branch on the remote repository.
  - *Example*: `git push -u origin feature/login-api`

###### 2. `git pull`
- **Purpose**: Fetches changes from a remote tracking branch and immediately integrates them into the current local branch (`git fetch` followed by `git merge` or `git rebase`).
- **Full Syntax**: `git pull [options] [<repository>] [<refspec>...]`
- **Options & Arguments**:
  - `--rebase`: Applies local commits on top of fetched remote commits, maintaining a linear commit history.
  - `--no-ff`: Forces the creation of an explicit merge commit during pull integration.
  - `--ff-only`: Refuses to pull unless the integration can be resolved as a fast-forward merge.
  - *Example*: `git pull --rebase origin main`

###### 3. `git merge`
- **Purpose**: Combines commit sequences from a target branch into the current checked-out branch.
- **Full Syntax**: `git merge [options] [<commit>...]`
- **Options & Arguments**:
  - `--no-ff`: Disables fast-forward merges, creating a dedicated merge commit to preserve historical feature boundaries.
  - `--squash`: Combines all incoming branch commits into a single staged change set without creating a commit automatically.
  - `-X <option>`: Specifies strategy options such as `-X ours` or `-X theirs` for conflict handling.
  - *Example*: `git merge --no-ff feature/payment-gateway`

###### 4. `git rebase`
- **Purpose**: Re-applies commits from the current branch onto the tip of another base commit, updating branch history to generate a linear timeline.
- **Full Syntax**: `git rebase [options] [<upstream>] [<branch>]`
- **Options & Arguments**:
  - `-i` / `--interactive`: Opens an interactive session allowing developers to pick, reword, edit, squash, or discard commits.
  - `--onto <newbase>`: Specifies a new base commit for rebasing a range of commits.
  - `--continue`: Resumes the rebase operation after conflict resolution.
  - *Example*: `git rebase -i main`

###### 5. `git commit`
- **Purpose**: Captures a snapshot of currently staged changes into the local repository DAG along with author information and a log message.
- **Full Syntax**: `git commit [options]`
- **Options & Arguments**:
  - `-m "<message>"`: Supplies the commit log message directly from the command line.
  - `-a` / `--all`: Automatically stages tracked files that have been modified or deleted prior to committing.
  - `--amend`: Replaces the tip commit with a new commit incorporating staged changes or updated log text.
  - *Example*: `git commit -a -m "FIX: Resolved null pointer in authentication handler"`

###### 6. `git branch`
- **Purpose**: Lists, creates, renames, or manages local and remote branch pointers.
- **Full Syntax**: `git branch [options] [<branch-name>] [<start-point>]`
- **Options & Arguments**:
  - `-d`: Removes a local branch if it has already been fully merged into its upstream branch.
  - `-a` / `--all`: Lists both local and remote-tracking branches.
  - `-m`: Renames an existing branch pointer.
  - *Example*: `git branch -d feature/cache-update`

###### 7. `git remote`
- **Purpose**: Manages the set of tracked remote repository connections.
- **Full Syntax**: `git remote [<subcommand>] [options]`
- **Subcommands & Options**:
  - `add <name> <url>`: Connects a new remote repository location.
  - `-v` / `--verbose`: Lists all defined remote names along with their fetch and push URLs.
  - *Example*: `git remote add origin https://example.com/repo.git`

---

#### Q1(C) [12 Marks]
**(Candidates may choose either Option I or Option II)**

##### OPTION I: Comparative Analysis of Four SDLC Models for Web Application Development [12 Marks]

###### Answer:
Selecting an appropriate Software Development Life Cycle (SDLC) model determines the execution speed, risk exposure, quality gates, and release frequency of web applications.

###### Architectural & Operational Comparison Matrix

| Evaluation Dimension | Waterfall Model | Agile / Scrum Model | Iterative & Incremental | DevOps Continuous Delivery |
| :--- | :--- | :--- | :--- | :--- |
| **Core Paradigm** | Sequential, phase-gated execution. | Iterative sprints (2–4 weeks) focused on working software. | Repeated cycles expanding software scope incrementally. | Continuous pipeline automation with infrastructure as code. |
| **Change Flexibility** | Very Low. Scope locked early; late changes are costly. | High. Backlog reprioritized at sprint boundaries. | Medium-High. Scope modified at cycle start. | Extremely High. Micro-changes pushed continuously. |
| **Release Velocity** | Months to Years (Big Bang release). | Weeks (End of Sprint). | Months (At end of feature increments). | Hours to Days (Multiple deployments daily). |
| **Testing & QA** | Deferred to late stage; defects found late in cycle. | Integrated per sprint; manual & automated acceptance. | Conducted at end of each iteration cycle. | Fully automated (Unit, Integration, Security) per commit. |
| **Feedback Loop** | End of project (User validation occurs at deployment). | Sprint Reviews & Demos (Frequent customer feedback). | End of increment review. | Real-time telemetry, APM monitoring, and deployment feedback. |

###### Detailed Evaluation for Web Application Development:
1. **Waterfall Model**: Unsuited for modern web applications due to rigid requirements assumptions. Finding architectural issues during late-stage testing leads to project delays.
2. **Agile / Scrum**: Significant improvement over Waterfall, enabling business adaptation. However, Scrum often leaves a deployment bottleneck at sprint completion where manual releases introduce delays.
3. **Iterative & Incremental**: Provides structured risk reduction, but lacks automated build/test orchestration, resulting in regression overhead as increments grow.
4. **DevOps Continuous Delivery (Recommended)**: The optimal SDLC for modern web platforms. By embedding continuous integration, automated testing, and infrastructure automation, software changes flow safely into production with minimal friction and instant feedback loops.

---

##### OPTION II: Git Merge Strategies in a Collaborative Open-Source Project (Case Study Essay) [12 Marks]

###### Answer:

###### 1. Scenario Context & Architectural Challenge
In an open-source GitHub project, a distributed team developed a feature branch over several weeks, generating 15 commits (containing experimental code, intermediate WIP commits, and bug fixes). Meanwhile, the `main` branch advanced significantly. Merging these 15 diverged commits directly creates history clutter, auditability challenges, and potential merge conflicts in shared files.

###### 2. Analysis of Git Merge Strategies

| Merge Strategy | Mechanism & History Impact | Suitability in Open-Source Context |
| :--- | :--- | :--- |
| **Fast-Forward (`git merge --ff`)** | Moves `main` pointer directly to feature branch tip. Requires linear history without divergence. | **Unusable directly**: Impossible here because `main` advanced, causing branch divergence. |
| **Three-Way Merge (`git merge --no-ff`)** | Creates a dedicated Merge Commit with two parent pointers. | **Sub-optimal**: Preserves all 15 WIP commits on `main`, cluttering repository history. |
| **Squash Merge (`git merge --squash`)** | Compresses all 15 commits into a single staged payload committed onto `main`. | **High Utility**: Generates 1 clean commit on `main`. However, loses intermediate logical progression across commits. |
| **Interactive Rebase + Fast-Forward** | Re-applies feature commits onto latest `main` tip, interactive cleanup (`pick`, `squash`, `fixup`). | **Optimal Strategy**: Cleans WIP commits into 2–3 logical commits, resolves conflicts once, and maintains a linear DAG. |

###### 3. Step-by-Step Resolution Workflow

**Step 1: Fetch and Sync with Remote Main**
```bash
git checkout feature-branch
git fetch origin main
```

**Step 2: Execute Interactive Rebase against Latest Main**
```bash
git rebase -i origin/main
```
In the interactive rebase editor interface:
```text
pick a1b2c3d FEAT: Implement core API endpoint handler
squash d4e5f6g WIP: Temporary logging (squash into core API)
fixup h7i8j9k FIX: Correct typo in response payload
pick m0n1p2q TEST: Add unit tests for API endpoints
```

**Step 3: Resolve Merge Conflicts During Rebase**
When conflicts occur in shared files, Git pauses the rebase operation:
```bash
# Edit conflict markers in shared files, stage resolved files
git add src/api/handler.js
git rebase --continue
```

**Step 4: Update Remote Feature Branch**
```bash
git push origin feature-branch --force-with-lease
```

**Step 5: Integrate into Main via Fast-Forward or Pull Request**
```bash
git checkout main
git merge --ff-only feature-branch
git push origin main
```

###### 4. Selective Fix Integration via `git cherry-pick`
When a critical bug fix commit (e.g., commit `c5f6a7b`) embedded within the uncompleted feature branch must be deployed immediately to `main` without pulling in unfinished feature code:
```bash
git checkout main
git cherry-pick c5f6a7b
git push origin main
```
*Justification*: `cherry-pick` copies the precise diff of a single commit and applies it independently onto `main`, making it ideal for isolated fixes.

---

### QUESTION 2 (Course Outcomes 2 & 3 — CO2 & CO3)

---

#### Q2(A) [3 Marks]
**What are the benefits of small batches and Minimum Viable Products (MVP) in DevOps-based Application Release Management?**

##### Answer:

1. **Benefits of Small Batches**:
   - **Reduced Lead Time & MTTR**: Smaller code changes are faster to test, review, and deploy. If a defect occurs, the blast radius is minimal and Mean Time to Recovery (MTTR) is drastically shortened.
   - **Frictionless Conflict Resolution**: Minimizes code divergence between developer branches, eliminating complex merge conflicts.

2. **Benefits of Minimum Viable Product (MVP)**:
   - **Accelerated Customer Feedback**: Releases core functionality early to validate business hypotheses against real user telemetry before committing capital.
   - **Reduced Sunk Cost Risk**: Prevents over-engineering features that users may not require, allowing teams to pivot based on empirical data.

---

#### Q2(B) [10 Marks]
**(i) Compare and contrast Virtual Machines and Docker for application deployment. [4 Marks]**

**(ii) Explain briefly the following Docker commands with purposes and syntax: (1) `docker push`, (2) `docker pull`, (3) `docker rmi`, (4) `docker commit`, (5) `docker network`, (6) `docker build`. [6 Marks]**

##### Answer:

##### Part (i): Virtual Machines vs. Docker Containers

###### Comparison Matrix

| Evaluation Dimension | Virtual Machines (VMs) | Docker Containers |
| :--- | :--- | :--- |
| **Virtualization Level** | Hardware-level virtualization via Hypervisor (KVM, ESXi, Hyper-V). | OS-level virtualization sharing the Host OS kernel via Linux Namespaces & cgroups. |
| **Guest OS Requirement** | Each VM runs a full Guest Operating System (GBs in size). | No Guest OS required; light process isolation utilizing Host Kernel (MBs in size). |
| **Boot Speed** | Minutes (Complete OS initialization sequence). | Seconds or Milliseconds (Direct process invocation). |
| **Resource Efficiency** | High overhead; static allocation of CPU and Memory per VM. | Near-native performance; dynamic elastic host resource utilization. |
| **Isolation & Security** | Strong hardware-enforced isolation boundaries. | Process-level isolation; kernel boundaries separate co-located containers. |
| **Environment Parity** | Difficult to maintain identical OS configurations across environments. | High environment parity; container images run identically across Dev, Test, and Prod. |

---

##### Part (ii): Docker Command Specifications

###### 1. `docker push`
- **Purpose**: Uploads a tagged local Docker image to a central container registry (e.g., Docker Hub, AWS ECR, JFrog Artifactory).
- **Syntax**: `docker push [options] NAME[:TAG]`
- *Example*: `docker push registry.example.com/payment-service:v2.1`

###### 2. `docker pull`
- **Purpose**: Downloads a specified Docker image from a remote registry to the local Docker engine image cache.
- **Syntax**: `docker pull [options] NAME[:TAG|@DIGEST]`
- *Example*: `docker pull postgres:15-alpine`

###### 3. `docker rmi`
- **Purpose**: Removes one or more Docker images from local engine host storage.
- **Syntax**: `docker rmi [options] IMAGE [IMAGE...]`
- *Options*: `-f` (forces removal of an image used by stopped containers).
- *Example*: `docker rmi -f 7d8e9f1a2b3c`

###### 4. `docker commit`
- **Purpose**: Creates a new custom Docker image snapshot from the current writable container layer of a modified container.
- **Syntax**: `docker commit [options] CONTAINER [REPOSITORY[:TAG]]`
- *Example*: `docker commit -a "DevOps Team" web-container custom-nginx:v1.0`

###### 5. `docker network`
- **Purpose**: Manages Docker networking drivers (bridge, host, overlay, macvlan, none) enabling container communication.
- **Syntax**: `docker network COMMAND [options]`
- *Subcommands*: `create`, `connect`, `disconnect`, `ls`, `inspect`, `rm`.
- *Example*: `docker network create --driver bridge app-net`

###### 6. `docker build`
- **Purpose**: Compiles a Docker container image automatically by reading context and execution instructions from a `Dockerfile`.
- **Syntax**: `docker build [options] PATH | URL | -`
- *Options*: `-t` (tags image name:tag), `-f` (specifies path to Dockerfile), `--no-cache`.
- *Example*: `docker build -t myapp:1.0 -f Dockerfile.prod .`

---

#### Q2(C) [12 Marks]

##### Part (i): Comparison of CI, Continuous Delivery, and Continuous Deployment [4 Marks]

###### Answer:

###### Comparative Assessment Matrix

| Dimension | Continuous Integration (CI) | Continuous Delivery (CD) | Continuous Deployment (CDep) |
| :--- | :--- | :--- | :--- |
| **Core Definition** | Automates code compilation, merging, and automated testing per commit. | Extends CI by automatically deploying validated code to staging/pre-prod environments. | Extends Continuous Delivery by automatically releasing every passed change to Production. |
| **Production Gate** | N/A (Build & Test stage only). | **Manual Business Approval Gate** required prior to Production push. | **100% Fully Automated** without human approval intervention. |
| **Primary Advantage** | Detects integration errors early; ensures code branch health. | Ensures software is always in a releaseable state; reduces deployment risk. | Eliminates human latency; delivers continuous user value immediately. |
| **Primary Limitation** | Does not cover environment provisioning or release automation. | Manual approval step can still introduce organizational delays. | Requires comprehensive test automation; unverified changes risk production issues if tests fail. |

---

##### Part (ii): CALMS Framework, Small Batches, MVP, and Overcoming Taylorism [8 Marks]

###### Answer:

###### 1. Integration of the CALMS Framework with Small Batches & MVP

1. **Culture**: Establishes shared accountability between Dev and Ops, replacing fear of failure with psychological safety. Teams embrace experimentative MVP releases.
2. **Automation**: Provides the infrastructure engine (automated builds, unit testing, automated provisioning) necessary to execute small batch deployments without manual overhead.
3. **Lean**: Focuses on value stream optimization by eliminating waste (Muda), capping Work-In-Progress (WIP), and enforcing small batch sizes to maximize throughput.
4. **Measurement**: Tracks objective operational metrics (DORA metrics: Deployment Frequency, Lead Time for Changes, MTTR, Change Failure Rate) to evaluate MVP effectiveness against user behavior.
5. **Sharing**: Disseminates learnings, tools, and post-mortem insights across organizational silos to refine subsequent software iterations.

###### 2. Overcoming Taylorism and the "Wall of Confusion"
Traditional software management relied on **Taylorism** (Scientific Management), which separated "thinking" (managers/architects) from "doing" (developers/ops), creating rigid functional silos:

- **The Wall of Confusion**: Developers are incentivized to ship features rapidly, while Operations engineers are incentivized to maintain system stability by minimizing change. This misalignment results in contentious releases, finger-pointing, and deployment friction.
- **DevOps Resolution**: Dismantles Taylorism by forming cross-functional squads with shared KPIs. Development teams take operational responsibility for their code, while Operations provides platform capabilities.

###### 3. Real-World Enterprise Scenario
An e-commerce firm transitioning from quarterly monolithic releases (1,000 changes per batch) to DevOps practices:
- **Implementation**: The team decomposes the application into microservices, adopts feature flags, and deploys small-batch releases regularly via an automated pipeline.
- **Outcome**: Lead time drops from 90 days to 2 hours. When an integration defect occurs, telemetry detects the issue instantly, and an automated rollback restores service in 45 seconds (MTTR).

###### 4. Potential Risks, Limitations, and Mitigation Strategies

| Real-World Risk / Limitation | Operational Impact | Strategic Mitigation Strategy |
| :--- | :--- | :--- |
| **Pipeline Congestion** | High frequency of pipeline triggers can queue CI/CD build agents. | Implement pipeline caching, parallelized test execution, and selective build triggers. |
| **Insufficient Automated Test Coverage** | Shipping small batches into production automatically can release undetected issues if test suites are weak. | Enforce strict quality gates (SonarQube code coverage > 80%, SAST scans, end-to-end integration tests). |
| **Regulatory & Compliance Hurdles** | Auditors require separation of duties (SoD) which conflicts with automated Continuous Deployment. | Implement Compliance-as-Code with automated immutable audit logs and peer-review PR gates. |
