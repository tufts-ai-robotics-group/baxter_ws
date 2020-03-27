# baxter_ws
This repository contains the code for collecting sensory data while Baxter performs exploratory behaviors. It also contains the data collected.

A continuing log of the research notes can be found in this Google doc: https://docs.google.com/document/d/1CyL6iixNDz-M7GmlC_yVkPoLvb-oBtBCSm710gXM80Q/edit?usp=sharing

Link to data collected: https://github.com/tufts-ai-robotics-group/baxter_ws/tree/master/src/run_scripts/src/data

Documentation:

There are 5 exploratory behaviors implemented. These are the 
1. Lift action
2. Shake action
3. Drop action
4. Push action
5. Poke action

Running the data collection script sequentially performs each of these actions on the object, all the while collecting data.
The multi-modal data collected include:
 a. Sound produced during the object interaction
 b. Image of the object
 c. Accelerometer data from the robot's wrists
 d. The state of the end-effector
 e. The state of the joints of the robot's arm
 
Some of these data are subscribed to through ROS topics while the others are collected in the script.
The ROS topics listened to are:
-'/robot/accelerometer/left_accelerometer/state'  -- For accelerometer data

-'/robot/limb/left/endpoint_state'                -- For state of the end-effector

-'/robot/joint_states'                            -- For joint states of the robot's arm

-'/camera/rgb/image_raw'                          -- For an image of the object


The audio data is recorded using the 'sounddevice' Python library. The recording is started right before the robot interacts with the object and is stopped right after the robot finishes interacting with the object. By doing this, we avoid recording extraneous sounds. The audio data is typically a few seconds long.

The file system for storing the data collected looks like:
-  data
  
 -    |_ objectname_objectmass
     
 -                  |_robot_action_modality_objectname_objectmass_trialnumber.json
                 
                  
The audio files end in .wav whilst the images end in .png. The other files are stored in json format for easy
parsing

To start the data collection, go to the directory that contains the data collection script: https://github.com/tufts-ai-robotics-group/baxter_ws/tree/master/src/run_scripts/src

and run the command:
        python data_collection.py <objectname_object_mass> <trial number>
  
An example could be:
        python data_collection.py blue_60g 5 


          
