# Install_and_run_robot_arm

1- Add the "Arduino robot arm" to "src" folder by typing the following comands
$cd ~/catkin_ws/src
$sudo apt install git
$git clone https://github.com/smart-methods/arduino_robot_arm

2-Add the Dependencies
$cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y

Make sure to use the commands based on your ROS version

For ROS Kinteic
$ sudo apt-get install ros-kinetic-moveit
$ sudo apt-get install ros-kinetic-joint-state-publisher ros-kinetic-joint-state-publisher-gui
$ sudo apt-get install ros-kinetic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-ros-control

For ROS Melodic
$ sudo apt-get install ros-melodic-moveit
$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control

For ROS Neotic
$ sudo apt-get install ros-noetic-moveit
$ sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
$ sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control

2- To control the robot arm 

by joint_state_publisher
$ roslaunch robot_arm_pkg check_motors.launch
to connect it with the hardware
$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
To run the arm using gazebo
$ roslaunch robot_arm_pkg check_motors.launch
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
$ rosrun robot_arm_pkg joint_states_to_gazebo.py
If you have a permission problem try use this commands
$ sudo chmod +x ~/catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts/joint_states_to_gazebo.py

To control the arm by Moveit and Kinematics
$ roslaunch moveit_pkg demo.launch
$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
To run the arm using gazebo
$ roslaunch moveit_pkg demo_gazebo.launch

Done!
