# Motion Planning and Decision Making for Autonomous Vehicles

In this project I implemented two of the main components of a traditional hierarchical planner: 
The Behavior Planner and the Motion Planner. 

Both work in unison to be able to:
* Avoid static objects (cars, bicycles and trucks) parked on the side of the road (but still 
invading the lane). The vehicle must avoid crashing with these vehicles by executing either 
a “nudge” or a “lane change” maneuver.
* Handle any type of intersection (3-way,  4-way intersections and roundabouts) by STOPPING 
in all of them (by default)
* Track the centerline on the traveling lane.

To accomplish this, I implemented:

* Behavioral planning logic using Finite State Machines - FSM
* Static objects Collision checking.
* Path and Trajectory generation using Cubic Spirals
* Best trajectory selection though a cost function evaluation. This cost function will mainly 
perform a collision check and a proximity check to bring cost higher as we get closer or 
collide with objects but maintaining a bias to stay closer to the lane center line.



## Demo

**Motion Planning and Decision Making for Autonomous Vehicles \[SDC ND\]<br/>
https://youtu.be/wKUuJzCgHls**
![images/demo.png](assets/images/demo.png)

## Installation Instructions

You must have a powerful enough computer with an NVIDIA GPU.

Install Ubuntu 20.04.2 LTS, NVIDIA drivers, and CUDA drivers.

Install the CARLA simulator:
https://carla.readthedocs.io/en/latest/start_quickstart/

Install gtest:
```
sudo apt-get install libgtest-dev
```

Install Conda and create a conda environment with Python 3.7:
```
conda remove --name CARLA --all
conda create --name CARLA python=3.7
conda activate CARLA
```

Install carla, websocket, websocket-client, pygame, numpy:

```
pip install carla
pip install websocket
pip install websocket-client
pip install pygame
pip install numpy
```

Modify this line in the file `project/starter_files/CMakeLists.txt`:
```
#set(gtest_lib /usr/src/gtest/libgtest.a)
set(gtest_lib /usr/lib/x86_64-linux-gnu/libgtest.a)
```

Append these lines to the file `~/.bashrc`:
```
export CARLA_ROOT="/opt/carla-simulator"
export PYTHONPATH=$PYTHONPATH:"${CARLA_ROOT}/PythonAPI/carla/dist/carla-0.9.11-py3.7-linux-x86_64.egg"
```

Restart your computer.

## Running Instructions:

Open a new terminal and run the following commands:
```
cd /opt/carla-simulator
./CarlaUE4.sh
```

Open a new terminal and run the following commands:
```
git clone https://github.com/jckuri/Motion_Planning_and_Decision_Making_for_Autonomous_Vehicles.git
cd Motion_Planning_and_Decision_Making_for_Autonomous_Vehicles/project/
./install-ubuntu.sh
cd starter_files/
cmake .
make
cd ..
./run_main.sh
```
