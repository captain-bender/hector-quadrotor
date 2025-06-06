# Part 3

This unit focuses on enabling RGB-D SLAM and autonomous navigation for a drone using the rtabmap_ros package in ROS. Students will:

- Build a 3D map using RTAB-Map.

- Visualize data in RViz.

- Use loop closures to localize and navigate a drone in a known environment.

System Requirements

To use rtabmap_ros effectively for SLAM:

- A 2D LIDAR publishing to /scan (sensor_msgs/LaserScan)

- A source of odometry (nav_msgs/Odometry)

- A calibrated depth camera publishing RGB and depth topics

💡 Ensure all required ROS topics are available in your simulation or real setup.

Exercise 1: Verifying Sensor Topics

Check the topics:
```
rostopic info /scan
rostopic info /camera/depth/image_raw
rostopic info /odom
```
Verify their types and publishing nodes.

Exercise 2: Visualizing Sensor Data in RViz

Start RViz:
```
rosrun rviz rviz
```
Add displays for:

- RGB camera (/camera/rgb/image_raw)

- Depth point cloud (/camera/depth/points)

- Laser scan (/scan)

- Set the Fixed Frame to base_link.

Exercise 3: Launching RTAB-Map

Create a new package:

catkin_create_pkg my_rtab_package

Create a launch file rtabmap_drone.launch with the required ROS and RTAB-Map parameters. Include remappings to match your system topics.

Example Parameters to Include:

- frame_id: base_link

- subscribe_depth: true

- subscribe_scan: true

- RGBD/LinearUpdate, RGBD/AngularUpdate

- Optimizer/Slam2D, Mem/RehearsalSimilarity, etc.

Exercise 4: Launching with Navigation

Launch move_base (or an equivalent node):
```
roslaunch quadrotor_navigation quadrotor_move_base_rtab.launch
```
- Include this in your RTAB-Map launch file.

- Remap grid_map to /map so that the navigation stack receives the occupancy grid.

Exercise 5: Mapping Session

Launch your mapping setup:
```
roslaunch my_rtab_package rtabmap_drone.launch
```
Take off the drone (example command, may vary):
```
rostopic pub /takeoff std_msgs/Empty "{}"
```
Teleoperate the drone:
```
roslaunch turtlebot_teleop keyboard_teleop.launch
```
Visualize the 3D map in RViz (MapCloud display, fixed frame map).

Exercise 6: Viewing the Database

After mapping, RTAB-Map stores data in ~/.ros/rtabmap.db.

Open the database viewer:
```
rtabmap-databaseViewer ~/.ros/rtabmap.db
```
Explore stored images and loop closures.

Exercise 7: Localization Mode

Modify your launch file:
```
<arg name="localization" default="false"/>
<param if="$(arg localization)" name="Mem/IncrementalMemory" type="string" value="false"/>
<param name="Mem/InitWMWithAllNodes" type="string" value="$(arg localization)"/>
```
Launch in localization mode:
```
roslaunch my_rtab_package rtabmap_drone.launch localization:=true
```
Navigate the drone until it recognizes a known area and the map reappears.

Exercise 8: Autonomous Navigation

Once the drone has localized:

- Use RViz to send goals via “2D Nav Goal”.

- Ensure keyboard teleop is stopped to allow autonomous movement.