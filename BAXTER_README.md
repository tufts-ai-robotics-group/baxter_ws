# Baxter Startup Guide and ORK Start_Up Guide

- MAKE SURE THAT YOU ARE LOGGED ON TO BILLROBOT FOR WiFi
- MAKE SURE THAT YOU ARE .baxter.sh every time you open a new terminal or it doesn't work
- MAKE SURE THAT THE ROUTER IS TURNED ON 
- MAKE SURE COMPUTER IS PLUGGED IN
- MAKE SURE CAMERA IS PLUGGED IN

# Starting up Baxter

1. cd behavior_exploration/baxter_ws/
2. rosrun baxter_tools enable_robot.py -e
3. rosrun baxter_interface joint_trajectory_action_server.py
4. roslaunch baxter_moveit_config baxter_grippers.launch

# Launching the Object Recognition Kitchen

1. Start up Baxter like in part one
2. roslaunch openni2_launch openni2.launch (MAKE SURE THE CAMERA IS PLUGGED INTO THE COMPUTER VIA USB)
3. rosrun rqt_reconfigure rqt_reconfigure 
4. go to camera, driver and check the depth registration
5. python broadcast_transform.py (This is in baxter_ws/src/runscripts/src)
6. python object_pose.py (This is in baxter_ws/src/runscripts/src)
7. rosrun object_recognition_core detection -c `rospack find object_recognition_tabletop`/conf/detection.table.ros.ork (This is in behavior_exploration/baxter_ws)
8. rosrun rviz rviz
9. END

If anything else doesn't work, try to restart

# Other things to know

1. Hold onto the grippers to turn on zero gravity 
2. Look to runscripts/src/moveit_example.py for example code 


