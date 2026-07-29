# Robo-Twin-2.0

Current Problems:
（1）Task generation is difficult to scale.
（2）Simulation environments are often too simplified, leading to a large gap between simulation and the real world.

Solutions:
RoboTwin 2.0 addresses the two limitations through a scalable task-generation pipeline and structured domain randomization.

(1)RoboTwin 2.0 is built on **RoboTwin-OD**, an object library containing 731 object instances from 147 categories, with semantic and manipulation-relevant annotations.
Given a task objective and available objects, the framework uses multimodal large language models (MLLMs) to assist in generating task-level execution code. The generated code is then tested and refined through a simulation-in-the-loop process. This reduces the manual effort required to create new robotic manipulation tasks and enables the generation of expert demonstrations at scale.
(2)To reduce the gap between simulation and the real world, RoboTwin 2.0 applies structured domain randomization along five dimensions:clutter; lighting; background; tabletop height and language instructions.

By varying these factors during data generation and evaluation, the framework produces more diverse training data. This helps policies avoid overfitting to a single fixed environment and improves their robustness to environmental changes.


Core idea:
RoboTwin 2.0 uses simulation to generate large-scale, high-quality demonstrations for robotic manipulation learning.

1. A language model generates and refines **expert task code** from a natural-language task description.
2. The expert code is executed and validated in simulation. Once it reliably completes the task, it is used to collect successful demonstrations.
3. Each demonstration contains robot observations (e.g., camera images and joint states) and corresponding expert actions.
4. The simulation environment is randomized by changing clutter, lighting, backgrounds, tabletop height, and language instructions.
5. ACT is trained on these diverse demonstrations to learn an observation-to-action policy.

Task Description
      ↓
Expert Code Generation and Validation
      ↓
Large-Scale Demonstration Collection
      ↓
Domain Randomization
      ↓
ACT Policy Training
      ↓
Robust Robot Manipulation
