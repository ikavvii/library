# 1. DevOps, Git and SDLC

## A) Any Two Prominent DevOps Team Topologies [3 Marks]

### 1. Stream-Aligned Team

A stream-aligned team is organized around a continuous flow of work such as a product, application, customer journey, or business capability. The team contains the skills required to design, develop, test, deploy and operate the software.

**Benefits:**

- Reduces handoffs and dependencies between teams.
    
- Enables faster delivery and feedback.
    
- Gives the team end-to-end ownership and accountability.
    
- Supports continuous delivery and customer-focused development.
    

### 2. Platform Team

A platform team provides reusable internal services, tools and infrastructure that enable stream-aligned teams to deliver software efficiently. Examples include CI/CD platforms, cloud infrastructure, monitoring and deployment tools.

**Benefits:**

- Reduces duplication of infrastructure work.
    
- Provides self-service capabilities to development teams.
    
- Improves standardization, security and reliability.
    
- Allows application teams to concentrate on business functionality.
    

---

# B) Git for Source Code Management

## Critical Assessment of Git

Git is a distributed version-control system widely used in DevOps for managing source code and coordinating development among multiple developers.

### Features of Git

- Distributed repository: every developer has a complete local repository.
    
- Branching and merging: supports parallel development.
    
- Commit history: records changes with author, time and message.
    
- Collaboration: integrates easily with GitHub, GitLab and Bitbucket.
    
- Fast operations: most operations are performed locally.
    
- Tagging: versions/releases can be marked using tags.
    
- Conflict management: provides mechanisms to resolve conflicting changes.
    
- Integration with CI/CD: commits can automatically trigger build, test and deployment pipelines.
    

### Advantages

- Free and open source.
    
- Fast and lightweight.
    
- Excellent branching and merging support.
    
- Enables offline development.
    
- Provides complete history and traceability.
    
- Supports distributed and geographically separated teams.
    
- Integrates well with DevOps automation.
    

### Disadvantages

- Learning curve is higher than simple centralized systems.
    
- Merge conflicts can be difficult for beginners.
    
- Large binary files are not handled efficiently without extensions such as Git LFS.
    
- Poor Git practices can produce complicated commit histories.
    
- Commands such as `rebase`, `reset` and `reflog` can be dangerous if incorrectly used.
    

---

## 1. `git push`

**Purpose:** Uploads local commits/branches/tags to a remote repository.

**Syntax:**

```bash
git push [options] [<repository> [<refspec>...]]
```

**Common examples/options:**

```bash
git push origin main
git push -u origin feature/login
git push --all origin
git push --tags origin
git push -d origin feature/login
git push --force origin feature/login
```

- `origin` – remote repository name.
    
- `main` – branch being pushed.
    
- `-u` / `--set-upstream` – establishes tracking relationship.
    
- `--all` – pushes all branches.
    
- `--tags` – pushes tags.
    
- `-d` – deletes a remote branch.
    
- `--force` – forcefully updates the remote branch; should be used carefully.
    

---

## 2. `git pull`

**Purpose:** Downloads changes from a remote repository and integrates them into the current local branch.

**Syntax:**

```bash
git pull [options] [<repository> [<refspec>...]]
```

**Examples:**

```bash
git pull origin main
git pull --rebase origin main
git pull --ff-only origin main
git pull --no-edit origin main
```

- `--rebase` – integrates remote changes using rebase.
    
- `--no-rebase` – uses merge.
    
- `--ff-only` – permits only fast-forward integration.
    
- `--no-edit` – accepts the generated merge message.
    

---

## 3. `git merge`

**Purpose:** Combines the history of one branch with another branch.

**Syntax:**

```bash
git merge [options] <branch>
```

**Examples:**

```bash
git checkout main
git merge feature/login
git merge --no-ff feature/login
git merge --squash feature/login
git merge --abort
```

- `--no-ff` – always creates a merge commit.
    
- `--ff-only` – permits only fast-forward merges.
    
- `--squash` – combines changes into one working-tree change without creating the normal merge commit.
    
- `--abort` – cancels a conflicted merge.
    

---

## 4. `git rebase`

**Purpose:** Moves/replays commits onto another base commit to produce a cleaner, more linear history.

**Syntax:**

```bash
git rebase [options] [--onto <newbase>] [<upstream> [<branch>]]
```

**Examples:**

```bash
git checkout feature/login
git rebase main
git rebase -i HEAD~5
git rebase --onto main old-base feature/login
git rebase --continue
git rebase --abort
```

- `-i` – interactive rebase.
    
- `--onto` – specifies a new base.
    
- `--continue` – continues after resolving conflicts.
    
- `--abort` – cancels the rebase.
    

**Important:** Rebasing commits that have already been shared can cause problems because it rewrites commit history.

---

## 5. `git commit`

**Purpose:** Records staged changes in the local repository.

**Syntax:**

```bash
git commit [options] [--] [<pathspec>...]
```

**Examples:**

```bash
git commit -m "Add login feature"
git commit -a -m "Fix validation"
git commit --amend
git commit --no-edit
```

- `-m` – specifies commit message.
    
- `-a` – automatically stages modified/deleted tracked files.
    
- `--amend` – modifies the previous commit.
    
- `--no-edit` – retains the previous commit message when amending.
    

---

## 6. `git branch`

**Purpose:** Creates, lists, renames and deletes branches.

**Syntax:**

```bash
git branch [options] [<branch-name>]
```

**Examples:**

```bash
git branch
git branch feature/login
git branch -a
git branch -d feature/login
git branch -D feature/login
git branch -m old-name new-name
```

- `-a` – lists local and remote branches.
    
- `-d` – safely deletes a merged branch.
    
- `-D` – force deletes a branch.
    
- `-m` – renames a branch.
    

---

## 7. `git remote`

**Purpose:** Manages connections to remote repositories.

**Syntax:**

```bash
git remote [options] [command] [<name> [<newurl>]]
```

**Examples:**

```bash
git remote -v
git remote add origin https://github.com/user/project.git
git remote remove origin
git remote rename origin upstream
git remote set-url origin https://github.com/user/new-project.git
```

- `-v` – displays remote URLs.
    
- `add` – adds a remote.
    
- `remove` – removes a remote.
    
- `rename` – renames a remote.
    
- `set-url` – changes a remote URL.
    

---

# C-I-a) Comparison of Four SDLC Models for Web Application Development [12 Marks]

|SDLC Model|Main Characteristics|Advantages|Disadvantages|Suitability for Web Apps|
|---|---|---|---|---|
|**Waterfall**|Sequential phases: requirements → design → development → testing → deployment|Simple, structured, clear documentation|Changes are expensive; testing occurs late|Suitable when requirements are stable|
|**Agile**|Development occurs in short iterations/sprints with continuous customer feedback|Flexible, rapid feedback, early delivery, adapts to changing requirements|Requires active customer involvement and disciplined teams|Highly suitable for modern web applications|
|**Spiral**|Iterative development combined with systematic risk analysis|Excellent risk management; accommodates changing requirements|Expensive and complex; requires risk expertise|Suitable for large, complex and high-risk web systems|
|**V-Model**|Development phase is paired with a corresponding testing phase|Strong testing discipline and traceability|Rigid; changes are difficult|Suitable for web applications requiring strict validation|

### Comparison

**Waterfall** is best when requirements are fixed, but it is less suitable for modern web applications where requirements frequently change.

**Agile** is generally better for web applications because features can be delivered incrementally and customer feedback can be incorporated quickly.

**Spiral** is useful when the web application has substantial technical, security or business risks.

**V-Model** provides strong testing and quality assurance but lacks the flexibility required by rapidly changing web projects.

**Conclusion:** For most modern web applications, Agile combined with DevOps practices is preferable because it supports continuous feedback, incremental delivery, automation and frequent releases.

---

# C-II) Git Merge Types in a Collaborative Open-Source Project [12 Marks]

The feature branch contains 15 commits, while `main` has also progressed. Therefore, the branches have diverged and conflicts exist. The maintainers want a clean and auditable history while avoiding unnecessary minor commits.

## 1. Fast-Forward Merge

A fast-forward merge is possible only when the target branch has not diverged from the feature branch.

Example:

```text
A---B---C main
         \
          D---E feature
```

If `main` is still at C, Git can simply move the `main` pointer to E.

### Steps

```bash
git checkout main
git pull origin main
git merge feature
git push origin main
```

### Advantages

- No merge commit is created.
    
- Produces a simple linear history.
    
- Easy to understand.
    

### Disadvantages

- It cannot be used when `main` has diverged.
    
- In the given scenario, `main` has additional commits, so a fast-forward merge is normally impossible.
    

---

## 2. Three-Way Merge

A three-way merge is appropriate when both branches have diverged.

Git considers:

1. The current `main` tip.
    
2. The feature branch tip.
    
3. Their common ancestor.
    

Example:

```text
        D---E---F feature
       /
A---B---C---G---H main
```

Git creates a merge commit:

```text
        D---E---F
       /         \
A---B---C---G---H---M main
```

### Steps

```bash
git checkout main
git pull origin main
git merge --no-ff feature
```

If conflicts occur:

```bash
git status
# Edit conflicted files
git add <resolved-files>
git commit
git push origin main
```

If the merge must be cancelled:

```bash
git merge --abort
```

### Advantages

- Preserves the actual branching history.
    
- Shows when the feature was integrated.
    
- Suitable for collaborative projects where historical information is important.
    

### Disadvantages

- Can produce a cluttered history.
    
- The 15 individual feature commits remain visible.
    
- Frequent merges can make the history difficult to read.
    

---

## 3. Squash Merge

A squash merge combines all feature-branch changes into one commit on the target branch.

The 15 commits might become:

```text
main: A---B---C---G---H---S
                         ^
                    feature
                    as one commit
```

### Steps

```bash
git checkout main
git pull origin main
git merge --squash feature
git commit -m "Add new feature"
git push origin main
```

If conflicts occur, resolve them manually:

```bash
git status
# Edit conflicted files
git add <files>
git commit -m "Add new feature"
```

### Advantages

- Converts 15 minor commits into one meaningful commit.
    
- Produces a clean and readable `main` history.
    
- Well suited to GitHub pull-request workflows.
    
- Makes reverting the complete feature relatively easy.
    

### Disadvantages

- Individual feature-branch commit history is not represented in `main`.
    
- Detailed information about incremental development is lost from the main-line history.
    
- If contributors need individual commits for debugging, the loss of that history can be inconvenient.
    

---

## 4. Rebase

Rebase moves the feature commits onto the latest `main`, creating a linear history.

Before:

```text
        D---E---F feature
       /
A---B---C---G---H main
```

After rebasing:

```text
A---B---C---G---H---D'---E'---F' feature
```

### Steps

```bash
git checkout feature
git fetch origin
git rebase origin/main
```

If conflicts occur:

```bash
git status
# Resolve conflicts
git add <files>
git rebase --continue
```

Repeat until complete. To cancel:

```bash
git rebase --abort
```

Then integrate:

```bash
git checkout main
git merge --ff-only feature
git push origin main
```

Because rebase rewrites commits, a previously published feature branch may require:

```bash
git push --force-with-lease origin feature
```

`--force-with-lease` is safer than an unconditional `--force`.

### Advantages

- Produces a clean, linear history.
    
- Makes the final history easier to read.
    
- Allows conflicts to be resolved before integration.
    

### Disadvantages

- Rewrites commit IDs.
    
- Can cause problems when other developers are working on the same published branch.
    
- Conflict resolution may need to be performed repeatedly across several commits.
    

---

## Cherry-Picking

Cherry-picking is useful when only selected commits are required rather than the entire feature branch.

```bash
git checkout main
git cherry-pick <commit-hash>
```

For multiple commits:

```bash
git cherry-pick <commit1> <commit2>
```

If a conflict occurs:

```bash
git status
# Resolve conflict
git add <files>
git cherry-pick --continue
```

To cancel:

```bash
git cherry-pick --abort
```

### When is cherry-picking better?

Suppose the 15-commit feature branch contains a critical security fix in only one commit. Pulling the entire feature may be undesirable. The maintainer can cherry-pick only that security-fix commit into `main`.

---

## Recommended Approach

For the given open-source project, **Squash Merge through a reviewed pull request** is a strong choice when maintainers prioritize a clean history and want to remove the clutter of 15 incremental commits.

A suitable workflow is:

```bash
git checkout feature
git fetch origin
git rebase origin/main
# Resolve conflicts
git rebase --continue

# Create/update pull request
# Review and run CI tests

git checkout main
git pull origin main
git merge --squash feature
git commit -m "Add new feature"
git push origin main
```

This approach combines the benefits of keeping development organized with a clean `main` history.

However, **three-way merge** is preferable when preserving the exact branching and integration history is more important than reducing commit count. **Cherry-picking** is preferable when only specific independent fixes are required.

---

# 2. DevOps Release Management, Docker and CALMS

## A) Benefits of Small Batches and MVP in DevOps-Based Application Release Management [3 Marks]

### Small Batches

Small batches mean delivering a small number of changes at frequent intervals rather than accumulating a large set of changes.

**Benefits:**

- Smaller changes are easier to test and review.
    
- Problems can be detected and fixed quickly.
    
- Releases become less risky.
    
- Faster customer feedback is obtained.
    
- Makes rollback easier.
    

### MVP – Minimum Viable Product

An MVP is the simplest usable version of a product containing only the essential features required to deliver customer value.

**Benefits:**

- Allows the product to reach users quickly.
    
- Validates assumptions using real customer feedback.
    
- Reduces development cost and waste.
    
- Prevents spending large amounts on unwanted features.
    
- Supports iterative improvement.
    

**Together:** Small batches enable frequent incremental releases, while MVP ensures that development focuses on the most important customer value.

---

# B-I) Virtual Machines vs Docker

|Feature|Virtual Machine|Docker Container|
|---|---|---|
|Virtualization|Hardware-level virtualization|OS-level virtualization|
|OS|Each VM normally has its own guest OS|Containers share the host OS kernel|
|Size|Relatively large|Lightweight|
|Startup|Slower|Very fast|
|Resource usage|Higher|Lower|
|Isolation|Strong isolation|Process-level isolation|
|Portability|Good|Excellent across compatible container environments|
|Density|Fewer instances per host|Many containers can run on one host|
|Best use|Different OS environments, strong isolation|Microservices, CI/CD and cloud-native applications|

**Conclusion:** VMs provide stronger hardware-level isolation but consume more resources. Docker containers are lightweight and start quickly, making them highly suitable for DevOps and microservice deployments.

---

# B-II) Docker Commands [6 Marks]

## 1. `docker push`

**Purpose:** Uploads a local Docker image to a registry.

**Syntax:**

```bash
docker push [OPTIONS] NAME[:TAG]
```

**Example:**

```bash
docker push myrepo/myapp:1.0
```

Common option:

```bash
docker push --all-tags myrepo/myapp
```

---

## 2. `docker pull`

**Purpose:** Downloads an image from a Docker registry.

**Syntax:**

```bash
docker pull [OPTIONS] NAME[:TAG|@DIGEST]
```

**Examples:**

```bash
docker pull nginx
docker pull nginx:latest
```

Common option:

```bash
docker pull --platform linux/amd64 nginx
```

---

## 3. `docker rmi`

**Purpose:** Removes one or more Docker images.

**Syntax:**

```bash
docker rmi [OPTIONS] IMAGE[:TAG] [IMAGE...]
```

**Examples:**

```bash
docker rmi myapp:1.0
docker rmi -f myapp:1.0
```

- `-f` / `--force` – force removal.
    

---

## 4. `docker commit`

**Purpose:** Creates a new image from the changes in an existing container.

**Syntax:**

```bash
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
```

**Example:**

```bash
docker commit mycontainer myapp:v1
```

Common options:

```bash
docker commit -m "Configured application" mycontainer myapp:v1
docker commit -a "Developer" mycontainer myapp:v1
```

- `-m` – commit message.
    
- `-a` – author.
    

In normal DevOps practice, a reproducible `Dockerfile` is generally preferred over relying on `docker commit`.

---

## 5. `docker network`

**Purpose:** Creates and manages Docker networks so containers can communicate.

**Syntax:**

```bash
docker network COMMAND
```

Common commands:

```bash
docker network ls
docker network create mynetwork
docker network inspect mynetwork
docker network connect mynetwork container1
docker network disconnect mynetwork container1
docker network rm mynetwork
```

---

## 6. `docker build`

**Purpose:** Builds a Docker image from a Dockerfile and build context.

**Syntax:**

```bash
docker build [OPTIONS] PATH | URL | -
```

**Examples:**

```bash
docker build -t myapp:1.0 .
docker build -f Dockerfile.prod -t myapp:prod .
docker build --no-cache -t myapp:latest .
```

- `-t` / `--tag` – assigns image name and tag.
    
- `-f` / `--file` – specifies Dockerfile.
    
- `--no-cache` – disables build cache.
    

---

# C-I) Continuous Integration vs Continuous Delivery vs Continuous Deployment [4 Marks]

|Aspect|Continuous Integration|Continuous Delivery|Continuous Deployment|
|---|---|---|---|
|Meaning|Frequently integrates code into shared repository|Keeps software always ready for release|Automatically releases validated changes to production|
|Main focus|Build and test|Release readiness|Automatic production deployment|
|Production deployment|No|Usually manual approval|Automatic|
|Testing|Automated|Automated|Automated|
|Risk|Reduced integration risk|Reduced release risk|Very fast delivery but requires strong automation|
|Example|Every commit triggers build/tests|Successful build is deployable|Successful pipeline automatically reaches production|

### Continuous Integration

Developers frequently merge code into a shared repository, where automated builds and tests are executed.

**Pros:** Early defect detection, reduced integration problems, faster feedback.

**Cons:** Requires good automated tests and CI infrastructure.

### Continuous Delivery

Every successful change is automatically built, tested and packaged so that it is ready for production deployment. A manual approval may still be required.

**Pros:** Reliable and repeatable releases, reduced deployment effort.

**Cons:** Requires mature automation, testing and release processes.

### Continuous Deployment

Every change that passes the automated pipeline is automatically deployed to production.

**Pros:** Very rapid delivery, immediate customer feedback, reduced manual intervention.

**Cons:** Requires highly reliable testing and monitoring; defective changes can reach users quickly.

---

# C-II) CALMS, Small Batches and MVP [8 Marks]

CALMS represents:

- **C – Culture**
    
- **A – Automation**
    
- **L – Lean**
    
- **M – Measurement**
    
- **S – Sharing**
    

It provides a framework for assessing and improving DevOps adoption.

## 1. Culture

DevOps requires collaboration between development, operations, testing, security and business teams.

Small batches encourage teams to work together on manageable pieces of functionality. An MVP gives everyone a common customer-oriented objective.

**Example:** Instead of developers completing an entire e-commerce system before involving operations, developers, testers and operations engineers collaborate on delivering the first shopping-cart capability.

### Challenge: Silo Mentality

Traditional organizations may have separate development and operations departments with different objectives. Developers may prioritize feature delivery while operations prioritizes stability.

This can produce:

- Communication gaps.
    
- Blame when failures occur.
    
- Delayed releases.
    
- Duplicate work.
    

DevOps addresses this through cross-functional teams, shared goals and collective ownership.

---

## 2. Automation

Automation reduces repetitive manual work.

Examples include:

```text
Code → Build → Unit Test → Security Scan → Package → Deploy → Monitor
```

Small batches make automation easier because each change is smaller and easier to validate.

An MVP can also be deployed through an automated pipeline, allowing the organization to obtain customer feedback quickly.

**Benefits:**

- Faster releases.
    
- Fewer human errors.
    
- Repeatable processes.
    
- Faster testing and deployment.
    

**Limitation:** Poorly designed automation can automatically reproduce incorrect processes or deploy defective code.

---

## 3. Lean

Lean DevOps focuses on eliminating waste and maximizing customer value.

MVP directly supports Lean because unnecessary features are avoided.

For example, instead of developing ten features for an online food-ordering application, the first MVP could provide:

```text
Browse food → Add to cart → Place order
```

Usage data can then determine which additional features customers actually need.

Small batches also reduce Work in Progress (WIP) and make bottlenecks easier to identify.

---

## 4. Measurement

DevOps teams should measure both technical and business outcomes.

Important metrics include:

- Deployment frequency.
    
- Lead time for changes.
    
- Change failure rate.
    
- Mean time to recovery.
    
- Application performance.
    
- Customer satisfaction.
    
- Feature adoption.
    

For an MVP, measurement determines whether the feature actually creates customer value.

**Example:** If only 5% of users use a newly developed feature, the team can reconsider further investment rather than spending months enhancing it.

---

## 5. Sharing

Sharing involves sharing knowledge, feedback, tools, metrics and responsibility across teams.

Examples:

- Shared dashboards.
    
- Documentation.
    
- Code reviews.
    
- Retrospectives.
    
- Internal technical communities.
    
- Shared incident reports.
    

Sharing reduces knowledge silos and helps teams learn from failures.

---

## Taylorism and DevOps

Traditional **Taylorism** emphasizes dividing work into specialized tasks, standardizing activities and controlling workers through tightly defined processes.

In software development, excessive specialization can result in:

```text
Developer → Tester → Operations
```

where each group performs only its assigned task.

DevOps instead promotes:

```text
Cross-functional team
        ↓
Develop → Test → Deploy → Operate → Measure → Learn
```

Teams share responsibility for the complete software lifecycle.

---

## Example: Online Shopping Application

A traditional approach might spend six months developing a complete shopping platform before releasing it.

A DevOps/MVP approach could be:

**Iteration 1:** User registration and product browsing.

**Iteration 2:** Shopping cart.

**Iteration 3:** Payment.

**Iteration 4:** Order tracking.

Each iteration is developed in a small batch, automatically tested and deployed. Customer behavior is measured after each release.

This produces:

- Faster feedback.
    
- Lower release risk.
    
- Less wasted development.
    
- Continuous improvement.
    
- Better alignment with customer needs.
    

---

## Risks and Limitations

Although CALMS, MVP and small batches provide major benefits, organizations can face challenges:

1. **Organizational resistance:** Employees accustomed to traditional processes may resist cross-functional working.
    
2. **Automation cost:** Building and maintaining CI/CD infrastructure requires time and expertise.
    
3. **Technical debt:** Rapid MVP development can result in shortcuts and poor architecture if quality is ignored.
    
4. **Measurement problems:** Teams may optimize metrics rather than actual customer value.
    
5. **Security risks:** Rapid deployment without adequate security testing can introduce vulnerabilities.
    
6. **Overly small batches:** Excessively splitting work can create unnecessary coordination overhead.
    
7. **Cultural problems:** Tools alone cannot create DevOps; organizational culture and leadership support are essential.
    

## Conclusion

CALMS provides the cultural and operational foundation for DevOps, while **small batches and MVP provide practical mechanisms for delivering value quickly**. Culture and sharing break down silos, automation accelerates delivery, Lean reduces waste, and Measurement provides feedback for improvement. When these practices are combined with strong testing, security and monitoring, organizations can achieve faster, safer and more customer-focused software delivery.