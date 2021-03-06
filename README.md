## Table of Contents
- [General Information](#general-information)
- [Setup](#setup)
- [How to run](#how-to-run)
- [How to send a goal](#how-to-send-a-goal)
    - [Send a goal using RViz](#send-a-goal-using-rviz)
    - [Send a goal using move_base_sequence](#send-a-goal-using-move_base_sequence)
- [How to control the robot](#how-to-control-the-robot)
    - [Control the robot using rqt](#control-the-robot-using-rqt)
    - [Control the robot with the keyboard](#control-the-robot-with-the-keyboard)
- [Resources](#resources)
- [Workspace Structure](#workspace-structure)

### General Information

|   | What we use |
| --- | --- |
| Odometry | [eufs_sims](https://github.com/eufsa/eufs_sim) > robot_control |
| Other tools | [p3d ground truth gazebo plugin](http://answers.gazebosim.org/question/5308/getting-the-gazebo-plugin-p3d-working-hydro/) |
|   | [robot_localization](http://wiki.ros.org/robot_localization) - check [this](https://github.com/methylDragon/ros-sensor-fusion-tutorial)|
|   | [robot_pose_ekf](http://wiki.ros.org/robot_pose_ekf) |
| Global planner | [global_planner](http://wiki.ros.org/global_planner) |
| Local Planner | [teb_local_planner](http://wiki.ros.org/teb_local_planner) |
| SLAM | [gmapping](http://wiki.ros.org/gmapping) |
| Model/worlds/controller | [eufs_sims](https://github.com/eufsa/eufs_sim) |

----

### Setup

1. You need [Ubuntu 16.04](http://releases.ubuntu.com/16.04/) with [ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) installed.
2. Install packages `sudo apt-get install ros-kinetic-gazebo-ros-control ros-kinetic-ros-controllers ros-kinetic-navigation ros-kinetic-gmapping ros-kinetic-teb-local-planner ros-kinetic-robot-localization ros-kinetic-robot-pose-ekf ros-kinetic-ackermann-msgs ros-kinetic-twist-mux ros-kinetic-controller-manager ros-kinetic-robotnik-msgs ros-kinetic-velodyne-simulator`
3. Create a new catkin workspace if you don't have one already.
4. To clone the files directly (without an extra folder), run inside the src folder:
    - `git init`
    - `git remote add origin https://gitlab.com/fineasracingteam/jcricket.git`
    - `git fetch --all`
    - `git pull origin master`
5. Run `catkin_make`.

----

### How to run

1. Source the workspace(`source devel/setup.bash` or check our [ROS Basics](https://docs.google.com/document/d/1HTMq7Cwe4MZPlNUSJqRnfYy1TClEv3lscJfn8Ei_yrE/edit?usp=sharing) doc for more information).
2. Run: `roslaunch simulation gazebo_simulation.launch`.   
Tip: You can make gazebo open its GUI by changing gui argument inside gazebo_simulation.launch file to true.

----

### How to send a goal

#### Send a goal using RViz

Press 2D Nav Goal, hold it in the spot you want to send the goal, and turn it to the direction you want your robot to have when it reaches the goal.

#### Send a goal using move_base_sequence

Use argument goal_seq when launching: `roslaunch simulation gazebo_simulation.launch goal_seq:=true`.   
For more information on how it works and how to modify the goal sequence check [simulation readme](0_frt_common/simulation/README.md).

----

### How to control the robot

#### Control the robot using rqt

Use argument manual_control when launching: `roslaunch simulation gazebo_simulation.launch manual_control:=true`.

#### Control the robot with the keyboard

Open another terminal and run: `rosrun teleop_twist_keyboard teleop_twist_keyboard.py` 

----

### Workspace Structure

    ├── 0_frt_common
    │   └── simulation
    │       ├── launch
    │       ├── rviz
    │       └── worlds
    ├── 1_perception
    │   └── perception_common
    ├── 2_estimation
    │   ├── cone_global_planner
    │   └── estimation_common
    └── 3_control
        ├── eufs_description
        └── robot_control
