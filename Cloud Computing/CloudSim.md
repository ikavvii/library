<img width="640" height="421" alt="image" src="https://github.com/user-attachments/assets/559a54ba-c047-4739-b071-65028ec26f5e" />

Application Configuration

Defines details about the application being simulated.

Scheduling Policy

Defines how tasks are assigned to available resources.

For example:

Task 1 → VM 1
Task 2 → VM 2
Task 3 → VM 1

The scheduling can be controlled by the User or Data Center Broker.

2. User Interface Structure

This layer contains the two important objects:

Cloudlet

A Cloudlet represents a task/job that needs to be executed.

For example, imagine you upload three jobs:

Job 1: Image processing
Job 2: Video processing
Job 3: Data analysis

In CloudSim, these jobs can be represented as Cloudlets.

Virtual Machine (VM)

A VM is the computing environment that executes Cloudlets.

For example:

Cloudlet 1 ──→ VM 1
Cloudlet 2 ──→ VM 2
Cloudlet 3 ──→ VM 1


So, remember:

Cloudlet = task
VM = machine that executes the task

3. VM Services

This layer manages what happens inside the VMs.

Cloudlet Execution

Responsible for executing Cloudlets on VMs.

For example:

Cloudlet → VM → Execute → Result

VM Management

Responsible for creating, maintaining, and managing VMs.

It determines things such as:

Which VM should be created?
Which physical host should contain the VM?
How should the VM be managed?
4. Cloud Services

This layer deals with resource allocation.

It contains:

VM Provisioning

Decides where and how VMs are created.

Example:

Physical Host 1
     ↓
   VM 1
   VM 2

CPU Allocation

Determines how much CPU processing power is given to each VM.

Example:

VM 1 → 40% CPU
VM 2 → 60% CPU

Memory Allocation

Determines how much RAM is assigned to each VM.

Storage Allocation

Determines how much storage is available to VMs.

Bandwidth Allocation

Determines how much network bandwidth is provided to VMs.

5. Cloud Resources

This layer represents the resources and components of the cloud infrastructure.

Data Center

Represents a cloud data center containing physical computing resources.

For example:

Data Center
 ├── Host 1
 │    ├── VM 1
 │    └── VM 2
 └── Host 2
      ├── VM 3
      └── VM 4

Cloud Coordinator

Coordinates activities between different cloud components/data centers.

Sensor

Collects information about the simulated cloud environment, such as resource usage or system conditions.

Events Handling

CloudSim is an event-driven simulator. Therefore, events such as:

VM creation
Cloudlet submission
Cloudlet completion
Resource allocation

are handled by the event-handling mechanism.

6. Network

This layer deals with communication between cloud components.

Network Topology

Defines how different cloud components are connected.

For example:

User
  ↓
Network
  ↓
Data Center
  ↓
VM

Message Delay Calculation

Calculates the time required for information to travel through the network.

For example:

If a user sends a task to a data center and the network delay is 20 ms, CloudSim considers that delay during simulation.

7. CloudSim Core Simulation Engine

This is the bottom and fundamental layer.

It controls the entire simulation using events and simulation time.

For example:

Time = 0
   ↓
Create Data Center
   ↓
Create VM
   ↓
Submit Cloudlet
   ↓
Execute Cloudlet
   ↓
Cloudlet finishes
   ↓
Collect results


The core engine coordinates all these events.

Complete Example

Suppose we want to simulate a cloud application that has 3 tasks.

Step 1: User creates Cloudlets
Cloudlet 1
Cloudlet 2
Cloudlet 3

Step 2: Create VMs
VM 1
VM 2

Step 3: Scheduler assigns tasks
Cloudlet 1 → VM 1
Cloudlet 2 → VM 2
Cloudlet 3 → VM 1

Step 4: Resource allocation

CloudSim allocates:

CPU
RAM
Storage
Bandwidth


to the VMs.

Step 5: Execution

The VMs execute the Cloudlets.

Step 6: Network

If communication is required, CloudSim calculates:

Network topology
Message transmission delay
Step 7: Results

Finally, we can measure things such as:

Execution time
Waiting time
Resource utilization
Cost
Energy consumption
VM performance
Easy way to remember the architecture

Think of CloudSim like a real cloud data center:

User Code
↓
"What do I want to run?"

Cloudlet
↓
"This is my task."

VM
↓
"This is where my task will run."

Cloud Services
↓
"Give the VM CPU, RAM, storage and bandwidth."

Data Center / Cloud Resources
↓
"Provide the physical infrastructure."

Network
↓
"Move information between components."

Core Simulation Engine
↓
"Coordinate everything according to simulation time."

In one sentence:

CloudSim takes user-defined cloud requirements, creates and manages VMs, assigns Cloudlets to those VMs, allocates cloud resources, models network communication, and uses its core simulation engine to run and measure the entire cloud scenario.
