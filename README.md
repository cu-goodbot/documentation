# Documentation
### Documentation for GoodBot project that didn't fit elsewhere.

## Steps to launch `cu-goodbot`
1. Prepare python environment by installing

- Speech to text [requirements](https://github.com/cu-goodbot/IntentRecognizer/blob/master/src/README.md).
- Download [YOLO V3 weights](https://pjreddie.com/media/files/yolov3.weights) into `SceneUnderstanding/src/config/`
- Install python dependencies in [Requirements.txt](Requirements.txt).


2. To build the package, clone the three repositories into the `src/` folder of your catkin workspace. 
  - [SceneUnderstanding](https://github.com/cu-goodbot/SceneUnderstanding)
  - [IntentRecognizer](https://github.com/cu-goodbot/IntentRecognizer)
  - [NavigationManager](https://github.com/cu-goodbot/NavigationManager)
  
3. Run it through ROS

#### Building

Navigate to the root of that workspace and run
```
$ catkin_make
```

#### Running

To run the ROS nodes, make sure you've sourced your workspace by running
```
$ source <your workspace root>/devel/setup.bash
```
on each of your terminals and
then run on separate terminals
```
$ roslaunch scene_understanding scene_understanding.launch
```
```
$ roslaunch intent_recognizer intent_recognizer.launch
```
```
$ roslaunch navigation_manager navigation_manager.launch
```


#### Sanity check
Check that the information is being published to the `/scene_info`, `/intent` and `/move_base_simple/goal` by running
```
$ rostopic echo /scene_info
```
```
$ rostopic echo /intent
```
```
$ rostopic echo /move_base_simple/goal
```

4. Start **Movo** using [Movo start up documentation](movo_instructions.md)

