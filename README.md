# agx_arm_sim

A ROS2 simulation and development toolkit for AgileX robotic arms. It provides a complete set of packages for algorithm development, simulation testing, and visual debugging, bringing together arm descriptions, motion planning, and simulator support. It helps developers quickly set up a development environment and supports the full workflow from model visualization to motion planning and physics simulation.

## Repository Structure

This repository combines several sub-packages that together provide complete support for robotic arm development:

```Plain
agx_arm_sim/
├── agx_arm_description/    # Robotic arm URDF/Xacro description package
│   ├── Parameterized arm models with flexible configuration of models and end effectors
│   ├── Includes USD models that can be used directly in simulators such as Isaac Sim
│   └── Supports RViz2 visualization for quick verification of model configurations
├── Moveit2/                # MoveIt2 motion planning package
│   ├── Provides kinematics solving, collision checking, and trajectory planning
│   └── Supports all arm models for motion planning simulation and testing
├── realsense2_description/ # RealSense camera description package
│   └── Provides URDF models for cameras such as the RealSense D435 for simulation and visualization
└── .gitmodules             # Submodule configuration for managing model asset submodules
```

## Download and Installation

### 1. Clone the repository and initialize submodules

```bash
cd ~/ros2_ws/src
# Clone this repository
git clone https://github.com/agilexrobotics/agx_arm_sim.git
# Initialize submodules to fetch the complete model assets
cd agx_arm_sim
git submodule update --init --recursive
```

### 2. Install dependencies

```bash
# Install the required ROS2 packages
sudo apt-get install ros-humble-control* ros-humble-joint-trajectory-controller ros-humble-joint-state-* ros-humble-gripper-controllers ros-humble-trajectory-msgs ros-humble-topic-based-ros2-control ros-humble-moveit*
```

### 3. Build the workspace

```bash
colcon build
# Source the environment
source install/setup.bash
```

## Supported Robotic Arm Models

This repository supports the full AgileX arm lineup. Models and end-effector configurations can be switched via parameters:

| Model ID  | Model Name         | Supported End Effectors                                                  |
| --------- | ------------------ | ------------------------------------------------------------------------ |
| `piper`   | Piper              | None / Electric gripper / Revo2 dexterous hand / Teach pendant / Pika2 gripper |
| `piper_h` | Piper H            | None / Electric gripper / Revo2 dexterous hand / Teach pendant / Pika2 gripper |
| `piper_l` | Piper L            | None / Electric gripper / Revo2 dexterous hand / Teach pendant / Pika2 gripper |
| `piper_x` | Piper X            | None / Electric gripper / Revo2 dexterous hand / Teach pendant / Pika2 gripper |
| `nero`    | Nero               | None / Electric gripper / Revo2 dexterous hand / Teach pendant / Pika2 gripper |
| `revo2`   | Revo2 Dexterous Hand | Left and right hands can be configured independently                   |

## Supported Simulation Environments

This repository supports several simulation and development environments for different development and testing needs:

| Environment                        | Description                                                  |
| ---------------------------------- | ------------------------------------------------------------ |
| Isaac Sim (high-fidelity simulation) | Provides complete USD arm models that can be imported directly into NVIDIA Isaac Sim, supporting high-precision physics simulation for embodied AI development |
| MoveIt2 (planning simulation)      | Use the MoveIt2 package to simulate and test motion planning, validate collision checking and trajectory planning, and rapidly develop arm control algorithms |
| RViz2 (visual debugging)           | Visualize arm models and debug joints in RViz2, verifying model configurations quickly without launching a full simulation |

| Arm Model | Isaac Sim | MoveIt2 | MuJoCo | Gazebo |
| --------- | --------- | ------- | ------ | ------ |
| `piper`   | ✅        | ✅      | ✅     | ✅     |
| `piper_h` | ✅        | ✅      |        | ✅     |
| `piper_l` | ✅        | ✅      |        | ✅     |
| `piper_x` | ✅        | ✅      |        | ✅     |
| `nero`    | ✅        | ✅      | ✅     | ✅     |

## License

MIT License
