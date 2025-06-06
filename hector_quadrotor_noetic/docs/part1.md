# Part 1

The rapid growth of drone applications across industries—from logistics to agriculture—has made unmanned aerial systems a vital area of technological development. In this course, you'll dive into the fundamentals of programming drones using the Robot Operating System (ROS), gaining hands-on experience with simulated drones in controlled environments.
Why This Course?

Drones are not just futuristic concepts—they're part of our everyday reality. They're delivering packages, conducting inspections, assisting in agriculture, and more. Yet, very few people understand how to develop intelligent behaviors for these machines or interact with their onboard sensors programmatically.

This course aims to close that gap. You’ll learn how to control a drone programmatically, process its sensor data, and run practical simulations that mimic real-world operations.
Initial Demo: Manual Control

Let’s begin with a quick demonstration.

Objective: Control the drone manually through keyboard input.

Steps:

In Terminal 1, execute:
```
rosrun custom_teleop teleop_twist_keyboard.py
```

Use your keyboard to send velocity commands to the simulated drone. Refer to the terminal output for key bindings (typically i, j, k, l, etc. for movement in different directions).

Take some time to explore how the drone responds.
Second Demo: Automated Motion

Next, let's trigger a pre-programmed movement pattern.

Objective: Make the drone perform a square trajectory.

Steps:

In Terminal 1, execute:
```
rosrun drone_demo square_move.py
```

Observe the drone's motion in the simulation environment as it traces a square.

This gives a first taste of automation and trajectory planning.