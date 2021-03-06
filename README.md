# Prophesee ROS Wrapper

![Event-based vision by Prophesee](event-based_vision_PROPHESEE.png)

This metapackage contains ROS driver and messages for Prophesee event-based sensors.
The following packages and nodes are provided:
  * prophesee_ros_driver - ROS driver (a wrapper around Prophesee Driver), including
    * prophesee_ros_publisher - publishing data from Prophesee sensor to ROS topics
    * prophesee_ros_viewer - listening data from ROS topics and visualizing them on a screen
  * prophesee_event_msgs - Prophesee messages:
    * PropheseeEvent - contains an event from a Prophesee camera (uint16 x, uint16 y, bool p, int64 t)
    * PropheseeEventBuffer - contains a buffer of events (PropheseeEvent[] events)

Supported Prophesee EVK:
  * VGA-CD: PSEE300EVK, PEK3SVCD
  * HVGA-EM: PSEE350EVK, PEK3SHEM
  

## Installation

  * Install dependencies, such as Prophesee Driver SDK

    ```
        sudo apt install prophesee-*
    ```

  * Clone the source to the catkin workspace ( (create a workspace)[http://wiki.ros.org/catkin/Tutorials/create_a_workspace], if needed)

    ```
        cd catkin_ws/src
        git clone git@github.com:prophesee-ai/prophesee_ros_wrapper.git
        cd ..
    ```

  * Compile

    ```
        catkin_make
    ```

  * Source the workspace

    ```
        source ~/catkin_ws/devel/setup.bash
    ```
  
  

## Getting Started
  
prophesee_ros_driver package contains the following ROS nodes:
  * prophesee_ros_publisher
  * prophesee_ros_viewer

### Data publisher

To publish data from a Prophesee camera to ROS topics:

  ```
        roslaunch prophesee_ros_driver prophesee_publisher.launch
  ```

The following topics will be published:
  * camera_info - info about the camera
  * cd_events_buffer - buffer of CD (Change Detection) events
  * graylevel_image - Gray-level frame reconstructed from EM and CD events
 
 

### Data viewer

To visualize data from ROS topics:

  ```
        roslaunch prophesee_ros_driver prophesee_viewer.launch
  ```

