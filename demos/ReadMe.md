# bolt/demos

## What it is

How to use Bolt at LAAS-CNRS to do demonstrations (calibratio, control and sensor reading)

## Authors

- Paul Rouanet
- Maximilien Naveau
- Julian Viereck
- Majid Khadiv
- Elham Daneshmand 

## Goal of each code

- bolt_demo_calibration_test.cpp
Demo to test the calibration on real robot.
  - To calibrate the robot : bolt/src/programs/hardware_calibration.cpp
  - Add results in robot_properties_bolt/src/robot_properties_bolt/robot_properties_bolt/odri_control_interface/bolt_driver.yaml --> l.57 "position_offsets:"

- bolt_demo_pd_test.cpp
Demo of a sinusoidal control on each joint : swinging effect of Bolt's legs
  
- bolt_demo_sensor_reading_test.cpp
Reading and printing of sensors datas, without control
  
- bolt_demo_actuator_control.cpp
Assembly of the 3 others codes
  - 1) A calibration test
  - 2) A sinusoidal control (desynchronized) of joints
  - 3) Reading and printing of sensors datas
  
## How to compile at LAAS ? (on ONTAKE computer)

Put the workspace at the root, in usr. Ex : /usr/bolt_ws
