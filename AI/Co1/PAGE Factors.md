The **PAGE factors** are a framework used to specify and describe the agent's **task environment**. The acronym stands for:

- **P – Percepts:** These are the inputs the agent receives from its surroundings through its **sensors**. For a robot, this could include camera images, tactile data, or sonar readings.
- **A – Actions:** These are the operations or physical movements the agent can perform in the environment using its **actuators**.
- **G – Goals:** This defines the objective or the desired state the agent is trying to achieve (e.g., maximizing efficiency or reaching a specific destination).
- **E – Environment:** This is the external world or setting in which the agent operates, including all external factors and objects it interacts with.

### **Application Example: Part-Picking Robot**

A description for this robot would be:

- **Percepts:** Visual images of the bin, joint angle sensors to track arm position, and pressure sensors in the gripper.
- **Actions:** Moving the robotic arm, opening/closing the gripper, and conveying parts to a new location.
- **Goals:** Correctly identifying parts, picking them up without damage, and placing them in the correct target area as quickly as possible.
- **Environment:** A factory conveyor belt or a bin filled with parts, possibly with varying lighting and moving obstacles.