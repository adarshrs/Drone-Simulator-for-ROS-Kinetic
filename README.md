# Drone Simulator for ROS Kinetic

This is a modified version of the popular Erlecopter Simulation (available only for Ubuntu 14 + ROS Indigo) that can be used on Ubuntu 16 with ROS Kinetic. Using this, one can simulate a pixhawk based quadcopter and control it using MAVProxy.

## Installation

If you don't have one already, create a workspace in any directory -

~~~
$ mkdir -p catkin_ws/src && cd catkin_ws/   
$ catkin build
~~~

Clone this repository into your source folder -

~~~
$ cd src/   
$ git clone https://github.com/adarshrs/Drone-Simulator-for-ROS-Kinetic.git
~~~

Install essential dependencies -

~~~
$ sudo apt-get install ros-kinetic-octomap-ros    
$ sudo apt-get install ros-kinetic-mavlink
~~~

Build all packages in the workspace -

~~~
$ catkin build
~~~

## Running the simulation

First source your workspace, then navigate into the ardupilot/ArduCopter directory in your workspace and start the SITL- 

~~~
$ source catkin_ws/devel/setup.bash   
$ cd catkin_ws/src/ardupilot/ArduCopter   
$ ../Tools/autotest/sim_vehicles.sh -j 4 -f Gazebo
~~~

In another terminal, source your workspace again and launch the Gazebo simulation - 

~~~
$ source catkin_ws/devel/setup.bash   
$ roslaunch drone_sim_launch erlecopter_sim.launch
~~~

## Basic commands

You can test if your simulation is working with some simple MAVROS commands. Wait for the message "GPS Lock at 0" to show up in the first terminal. Then press enter and takeoff and land the drone using the following commands -

~~~
RTL> mode GUIDED    
GUIDED> arm throttle    
GUIDED> takeoff 5   
GUIDED> mode LAND
~~~
