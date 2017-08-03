# Pioneer-P3-AT
How to set up and run the red Pioneer P3-AT robot


Catkin WS setup
 - Follow this tutorial to set up your ros workspace http://wiki.ros.org/ROSARIA/Tutorials/How%20to%20use%20ROSARIA all the way up to this line :
  Next, run the RosAria node:
  'rosrun rosaria RosAria'
  
Robot Setup
- Theres a battery bay located on the front of the robot, make sure it has at least one 12v battery inside.
- Flip the switch on the front corner of the robot to on, it should start beeping at you continously
- Theres a red switch (the emergency stop) on top of the robot. Flip that switch and it should stop beeping meaning the motors can be enabled using rosservice

Running the robot
- run 'roscore'
- in a new bash session execute 'rosrun rosaria RosAria' , you may have to change the rosparam for port '~port (string, default: /dev/ttyUSB0)'
- with rosAria running you should be able to echo information coming from the robot using 'rostopic echo /RosAria/xxxxx'
- before you can publish to the 'cmd_vel' topic you need to enable the motors
- In a new bash session execute 'rosservice call RosAria/enable_motors' , this will enable the motors and allow you to publish to cmd_vel
- To drive the robot, publish to 'RosAria/cmd_vel', to test your setup run the command: 'rostopic pub -1 /RosAria/cmd_vel geometry_msgs/Twist '[0.5, 0.0, 0.0]' '[0.0, 0.0, 0.0]' ' , this should drive the robot straight a little, meaning the robot is ready to drive.
