# Simulation

## Basics
### Universal Robot Description Format (URDF) File

The Universal Robot Description Format (URDF) is an XML file format used to describe the physical properties of robots in a machine-readable format. It is often used in robotic simulation and visualization software, as well as in robotic control applications.


| Tag  | Description  |
| :------------ | :------------ |
| `<robot>`  | The root element in which all other tags are nested  |
|  <nbsp> `<link>`  <br>...<br>`</link>` | Link elements describe rigid bodies with appearances and physical properties, e.g., wheels, the robot’s frame, shapes representing sensors, etc.  |
| `<joint>`  <br>...<br>`</joint>`  | Joint elements describe where and how links are connected in terms of a parent link and a child link, e.g., wheels (child link) and the robot’s frame (parent link)  |
| `<gazebo>`  <br>...<br>`</gazebo>`  | Gazebo tags describe simulation extensions, such as cameras, LIDAR, and GPS  |
| `</robot>`  | Nothing can reside outside of the robot root element tags  |

Nested within these basic tags are more tags describing various properties of their parent tag. More information about what is typically found within some tags can be found on the [ROS Wiki](http://wiki.ros.org/ "ROS Wiki"), including in-depth descriptions of [link](http://wiki.ros.org/urdf/XML/link "link") elements and [joint](http://wiki.ros.org/urdf/XML/joint "joint") elements.


## Software
### Gazebo
## ADD IMAGE HERE PLACEHOLDER
#### About 
Gazebo is a 3D simulation environment that is commonly used in robotics and automation applications. It provides a platform for simulating robots and other objects in realistic environments, allowing developers to test and refine their algorithms and control systems without the need for physical hardware.

Gazebo uses a physics engine to simulate the dynamics of objects, including collisions, gravity, and friction. It also supports sensors such as cameras, LIDAR, and GPS, allowing developers to test their perception and localization algorithms in a simulated environment.

Gazebo is often used in conjunction with other robotics frameworks, such as ROS (Robot Operating System), to provide a complete development and testing environment for robotics applications. It is open-source software and has an active community of developers and users contributing to its ongoing development and improvement.

Overall, Gazebo is a powerful tool for simulating and testing robotics applications, providing a realistic and flexible environment for developers to iterate on their designs and algorithms.

#### Application
When running the simulation launch file, the simulated robot’s sensors create nodes and published messages that are defined in the URDF file. Additionally, the robot’s differential drive controller subscribes to the commonly used /cmd_vel topic. Running simulations in Gazebo is as simple as having your algorithms subscribe to the appropriate sensor topics and publish to the /cmd_vel topic.

### RQT
## ADD IMAGE HERE PLACEHOLDER

#### About 
RQT (ROS Qt-based Graphical User Interface (GUI) Toolkit) is a framework for developing graphical user interfaces (GUIs) for ROS (Robot Operating System). It provides a set of modular and extensible tools for visualizing, analyzing, and controlling robot systems.

RQT is based on the Qt framework, a popular C++ toolkit for developing GUIs. It provides a range of pre-built widgets and tools for developing complex, interactive interfaces for robot systems. Some of the key features of RQT include:

Plugin-based architecture: RQT is designed to be modular and extensible, with a plugin-based architecture that allows developers to easily add new functionality to the system.
Visualization tools: RQT includes a range of visualization tools for displaying and analyzing robot data, such as sensor readings, robot positions, and environmental maps.
Control tools: RQT also includes a range of control tools for interacting with robot systems, such as controlling robot motion, sending commands to actuators, and tuning control parameters.
Integration with ROS: RQT is tightly integrated with ROS, allowing developers to easily access and interact with ROS data and services from within the GUI.
Overall, RQT is a powerful framework for developing GUIs for robot systems, providing a range of pre-built tools and a flexible, extensible architecture for customizing and extending the system as needed.

#### Application

| Plugin | Description |
| --- | --- |
| **Visualization** | |
| Image View | Image View is used to visualize all kinds of image data from the robot. The visualization is constantly updated, typically with image data from the robot within Gazebo. |
| **Introspection** | |
| Node Graph | Node Graph displays all active and inactive ROS nodes and topics as well as their connections to each other. This tool can assist with understanding what nodes are publishing or subscribing to various ROS topics. |
| **Robot Tools** | |
| Robot Steering | Robot steering provides a GUI to control the simulated robot’s forward/backward velocity in m/s and angular velocity in rad/s. |
| **Dynamic Reconfiguration** | |
| rqt_reconfigure | rqt_reconfigure is a plugin that allows you to view and modify the parameters of a running ROS node. It provides a GUI for dynamically reconfiguring a node without stopping and restarting it. |


### RVIZ
## ADD IMAGE HERE PLACEHOLDER
#### About 
RViz (short for "ROS visualization") is a 3D visualization tool for ROS (Robot Operating System) that allows users to interactively visualize and analyze data from sensors and robots in a 3D environment. It is typically used for robot control and navigation, as well as for debugging and testing of robotics algorithms.

RViz can display data from various sources, including laser scanners, 3D cameras, and robots themselves. It can display point clouds, images, and geometric shapes, and can be used to visualize robot state and trajectories. Additionally, RViz provides various tools to help with navigation and manipulation of the 3D environment, such as interactive markers, and can be customized with plugins to extend its capabilities.


#### Application

| Feature | Description |
| --- | --- |
| Visualization of sensor data | RViz can display data from a wide range of sensors, including laser scanners, 3D cameras, and more. |
| Robot model visualization | RViz can display a robot model in 3D, including its joints, links, and other properties. |
| Interactive markers | RViz provides interactive markers that can be used to manipulate objects in the 3D environment, such as moving and rotating robot parts. |
| Customization | RViz can be customized with plugins to extend its capabilities and add new visualization options. |


### VSCode
#### About 
Visual Studio Code (VS Code) is a free and open-source code editor developed by Microsoft. It is widely used in the robotics community and has many extensions available that make it a powerful tool for developing ROS-based applications.

#### Application

| Extension | Description |
| --- | --- |
| ROS | Provides ROS support for VS Code, including syntax highlighting, code completion, and debugging capabilities. |
| CMake Tools | Provides tools for working with CMake, the build system used by ROS. |
| Python | Provides support for Python, the language used by many ROS packages. |
| URDF | Allows us to preview URDF files directly within VSCode. URDF (Universal Robot Description Format) is an XML format used to describe robots in ROS (Robot Operating System), and the URDF plugin provides a visual representation of the robot model, allowing users to inspect the robot's structure and properties in a 3D environment. |

## Models
#### Karina 2D
The following command will launch the Karina 2D model in a Gazebo environment and RVIZ and also have a map .

`roslaunch aasha_description gazebo_2d.launch world:=map1`

You can change map1 to map2,map4,map4,etc.

##### Plugins
|  Type  | Plugin Name  | Description  |
| :------------ | :------------ | :------------ |
| 2D Camera  |  camera_controller | The 2D camera publishes live images at a specified rate from the simulated robot in Gazebo |
| 2D LIDAR  | gazebo_ros_head_hoyuko_controller  | The 2D LIDAR publishes laser scan data from the simulated robot in Gazebo which can be viewed in RVIZ |
| GPS Sim  | gazebo_ros_gps  |   |
| Defferential Drive Controller  | gazebo_libgazebo_ros_diff_drive  |   |
| Bird's Eye | Bird's Eye | |

#### Aasha 3D
The following command will launch the Aasha 3D model in a Gazebo environment and RVIZ.

`roslaunch karina_description gazebo_3d.launch`

##### Plugins
|  Type  | Plugin Name  | Description  |
| :------------ | :------------ | :------------ |
| 3D LIDAR | | |
| Stereo Camera | | |


