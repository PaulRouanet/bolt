# bolt/demos

## What it is

How to use Bolt at LAAS-CNRS to do demonstrations (calibration, control and sensor reading), with ONTAKE computer

## Authors

- Paul Rouanet

- Maximilien Naveau
- Julian Viereck
- Majid Khadiv
- Elham Daneshmand 

## Goal of each code

- bolt_demo_calibration_test.cpp : Demo to test the calibration on real robot.
  - To calibrate the robot, execute the following code as explained after : bolt/src/programs/hardware_calibration.cpp
  - Add results in robot_properties_bolt/src/robot_properties_bolt/robot_properties_bolt/odri_control_interface/bolt_driver.yaml --> l.57 "position_offsets:"

- bolt_demo_pd_test.cpp : Demo of a sinusoidal control on each joint : swinging effect of Bolt's legs
  
- bolt_demo_sensor_reading_test.cpp : Reading and printing of sensors datas, without control
  
- bolt_demo_actuator_control.cpp : Assembly of the 3 others codes
  1) A calibration test
  2) A sinusoidal control (desynchronized) of joints
  3) Reading and printing of sensors datas
  
## How to compile at LAAS ? (on ONTAKE computer)

Put the workspace at the root, in usr. Ex : /usr/bolt_ws. Then, put all source codes needed in a directory named /src.
```
mkdir /usr/bolt_ws/src
cp <@SourceCodes> /usr/bolt_ws/src
```

Before any compilation, go in bolt_ws :
```
cd /usr/bolt_ws
```

and execute those commands:
```
source /usr/bolt_ws/install/setup.bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/bolt_ws/install/odri_control_interface/lib:/usr/bolt_ws/install/hardware_interface/lib:/opt/openrobots/lib:/opt/ros/foxy/opt/yaml_cpp_vendor/lib:/opt/ros/foxy/opt/rviz_ogre_vendor/lib:/opt/ros/foxy/lib/x86_64-linux-gnu:/opt/ros/foxy/lib
export PYTHONPATH=/usr/bolt_ws/src/boltpython:/usr/bolt_ws/install/odri_control_interface/lib/python3.8/site-packages:/usr/bolt_ws/install/mpi_cmake_modules/lib/python3.8/site-packages:/usr/bolt_ws/install/master_board_sdk/lib/python3.8/site-packages:/usr/bolt_ws/install/control_msgs/lib/python3.8/site-packages:/opt/ros/foxy/lib/python3.8/site-packages:/opt/openrobots/lib/python3.8/site-packages:$PYTHONPATH
```

When it is done, you are ready to compile. Always in /usr/bolt_ws :
```
colcon build --packages-up-to bolt
```

After that, put the robot in position with legs stretched (more or less in initial position), and switch on the robot : turn on the alimentation (25V, ~1A), and the emergency stop button.

Then, you can send the executable to the robot. We will take the example of bolt_demo_actuator_control.cpp to illustrate the command to send in the shell.

```
sudo -E "PYTHONPATH=$PYTHONPATH" "LD_LIBRARY_PATH=$LD_LIBRARY_PATH" /usr/bolt_ws/build/bolt/demos/bolt_demo_actuator_control enp3s0
```

Here you are, the robot will realize the action of the code sent !

