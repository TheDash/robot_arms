# robot_arms
This package helps you with adding ROS arms to ROS robots. What this package *can* help you with is combining two ROS enabled robots defined by URDF that both have drivers, ros_control, and gazebo enabled for them.
It cannot write the gazebo package, the driver, or the description for the arm or robot for you. A good example of what it can do is combining the Clearpath Robotics Husky mobile platform with a ROS enabled UR5 arm. Both of these have the necessary components to be ready for combination with this package. 

Another example would be combining a Clearpath Robotics Ridgeback with a Baxter, or UR-X arm.


Adding arms with MoveIt! Enabled to *any* robot:

1. Locate the URDF/description package for the arm you wish to add. For Universal Robot arms, it will be in the ur_description ROS package

2. Check if there already exists a _moveit_config package for that arm, it will save you from having to generate one in the future. 

3. Note down that there are a couple packages you will need to make for your robot so that the arm safely integrates. All in all, you will need these types of packages to complete the arm integration:

    a) **arm_driver**: a driver that will interface with the hardware and software on your PC.


    b) **arm_gazebo**: a gazebo package that will enable the ROS control interfaces for your arm. You will also need to have defined the respective transmission files for your URDF, and the respective .gazebo.xacro files for your URDF

    c) **arm_description**: the original description for the arm, as mentioned above

    d) **robot_moveit_config**: the combined moveit_config for the rest of the robot and the arm.

    e) ***optional* arm_planner**: a customized planning library for your arm if you are not satisfied with the default planners

    f) ***modification* robot_bringup**: your robot will need to modify the bringup to include the arm drivers, control scheme, and moveit_configs.

    g) ***modification* robot_description**: your original robot description will need to add a mounting link for the arm_description.


