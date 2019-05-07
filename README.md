# Documentation
### Documentation for GoodBot project that didn't fit elsewhere.

## Steps to launch `cu-goodbot`
1. Prepare python environment by installing

- Speech to text [requirements](https://github.com/cu-goodbot/IntentRecognizer/blob/master/src/README.md).
- Download [YOLO V3 weights](https://pjreddie.com/media/files/yolov3.weights) into `SceneUnderstanding/src/config/`
- Install python dependencies in [requirements.txt](requirements.txt).


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

First start **Movo** using [Movo start up documentation](movo_instructions.md).

Next, launch the Movo navigation software by running (on Movo)

```
$ roslaunch navigation_manager map_nav.launch
```

To run the GoodBot ROS nodes, make sure you've sourced your workspace by running
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
Check that the information is being published to the `/scene_info`, `/intent` and `/movo/odometry/local_filtered` by running
```
$ rostopic echo /scene_info
```
```
$ rostopic echo /intent
```
```
$ rostopic echo /movo/odometry/local_filtered
```

### Testing
- Focus on the terminal running `intent_recognizer`
- Type `r` and give the directional command for example 

*"Can you take me forward?"* 

- If you need explanation, type `r` again in the same terminal and say something like 

*"Why are you turning?"* 

- If the `GoodBot` asks for POI disambiguation,  type `r` again and say something like

*"first person"* or *"second"*

### Bonus

Link to [video demo](https://www.youtube.com/watch?v=rbX-fL_OCeg&t=19s)
