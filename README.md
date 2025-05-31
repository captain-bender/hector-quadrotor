# Hector-quadrotor

This is repo dedicated to experiments using the classic Hector quad rotor simulation. As a base I have used [hector-quadrotor-noetic](https://github.com/RAFALAMAO/hector-quadrotor-noetic/tree/main) and [TheConstuctCore](https://bitbucket.org/theconstructcore/workspace/repositories/) repositories in GitLab.


## Helpful launch files
Start hector-ui
```
roslaunch hector_ui hector_ui.launch
```

Start simulation in empty world
```
roslaunch hector_quadrotor_gazebo quadrotor_empty_world.launch
```

Start simulation in outdoor world
```
roslaunch hector_quadrotor_demo outdoor_flight_gazebo_no_rviz.launch
```

Start rtab-map
```
roslaunch my_rtab_package rtabmap_drone.launch
```