# Movo Run Instructions

## Movo Bringup

First, connect to the Movo wifi network `MovoWifi` with password `see Jeff for password`. Once you are connected to the Movo wifi network, open a new terminal window.

In that new terminal window, ssh into movo by running the command
```
$ ssh movo@10.66.171.100
```
and entering the password `see Jeff for password`.

To bring up the Movo systems, run the command
```
$ roslaunch movo_bringup.launch
```

It will take some time for all systems to start. You will know the startup process is complete when Movo unfurls its arms, and moves its torso all the way up, then all the way down.

## Movo ROS Network

__Note: these instructions assume the Movo on-board computer is the ROS master.__

To be able to view Movo data over ROS from a seperate computer, first connect that computer to the Movo wifi network `MovoWifi` with password `see Jeff for password`.

Next, open a new terminal window and enter the following commands:
```
$ export ROS_MASTER_URI=http://10.66.171.100:11311
```
This tells your bash terminal session that the ROS master is located at the above IP address on port 11311. Next obtain your machine's IP address on the Movo network by running:
```
$ ifconfig
```
Look for your wifi interface in the output, __which will most likely start with w (mine is *wlp4so*)__, and in that block, find `inet addr:`. This number is your IP address on Movo's network.

Next, enter the following
```
$ export ROS_IP=<inet addr value>
```
to tell the ROS network what your machine's IP address is.

Test that you can see data from Movo by first running
```
$ rostopic list
```
If you see a long list of names, good! If not, your ROS_MASTER_URI environment variable is most likely set incorrectly. Then run
```
$ rostopic echo /tf
```
You should see a blur of output. If so, great! You can get data from Movo over ROS. If not, your ROS_IP environement variable is most likely set incorrectly.

## Teleop Control of Movo

__Note: this section assumes you have built the Movo packages, and have the ROS joy node installed.__

Open a new terminal, and follow the steps above. Once you know you can see data from Movo, plug in the joystick, and run the command
```
$ roslaunch movo_remote_teleop movo_remote_teleop.launch
```
You should now be able to use the joystick to control Movo.

## Collecting Data from Movo

Now that we can connect to Movo, we want to record data for future use. To do this we will use ROS bag files, which record all data published to our specified topics.

First, open yet another terminal window. We don't need to repeat the above process for this one! Ssh into Movo by following the intructions in section 1.

Once you are sshed in, navigate to the location you want to save your bag file, then run
```
$ rosbag record -O <your filename> /<each topic> /<you want> /<to record>
```
You are now recording data! When you are done, just Ctrl-C to finish recording and save the file.

To transfer the file to your computer, you can use the program `scp`. In a new terminal run
```
$ scp movo@10.66.171.100:/<path to the bag file on Movo> <location on your computer to save to>
```
