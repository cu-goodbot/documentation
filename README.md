# Documentation
### Documentation for GoodBot project that didn't fit elsewhere.

## Steps to launch `cu-goodbot`
1. Clone the three repositories 
  - [SceneUnderstanding](https://github.com/cu-goodbot/SceneUnderstanding)
  - [IntentRecognizer](https://github.com/cu-goodbot/IntentRecognizer)
  - [NavigationManager](https://github.com/cu-goodbot/NavigationManager)
  
2. Run it through ROS

#### Building

To build the package, clone it to the `src/` folder of your catkin workspace. Then navigate to the root of that workspace and run
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
