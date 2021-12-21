# ros2-simple-pub-sub
Browsing through the simple pub sub model in ROS2

# Publisher Subscriber with ROS2

## Environment setup for Ubuntu 20.04

0. Download *install_ros2.sh* in your computer.
1. Open a terminal and run <tt>sudo chmod +x install_ros2.sh</tt>.
2. Execute the bash file by running <tt>sudo ./install_ros2.sh</tt>.
3. Source the bashrc file <tt>source ~/.bashrc</tt>.

## Check Environment Variables

```
printenv | grep -i ROS
```

The response should be something like this: 

```
ROS_VERSION=2
ROS_PYTHON_VERSION=3
ROS_DISTRO=foxy
```

## Create a workspace

```
mkdir -p ~/dev_ws
```

## Build packages

Clone the repository. While still at the root directory <tt>~/dev_ws</tt>, make sure you do not have any missing dependencies.

```
rosdep install -i --from-path src --rosdistro foxy -y
```

We have two packages here for pubsub: one in python and the other in cpp. We need to build both of them before execution. Remember to run the following commands from root directory <tt>~/dev_ws</tt>.

```
colcon build --packages-select cpp_pubsub
colcon build --packages-select py_pubsub
```

## Test the code

Let's run the *talker(publisher)* node in **python** and the *listener(subscriber)* in **cpp**.

1. Open new terminal, navigate to `~/dev_ws` and source the setup file by running `. install/setup.bash`
2. Run the talker node : `ros2 run py_pubsub talker`
3. Open another terminal, navigate to `~/dev_ws` and source the setup file by running `. install/setup.bash`
4. Run the subscriber node : `ros2 run cpp_pubsub listener`
