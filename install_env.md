# USRG Drone in Gazebo

## Installation
### Dependencies
```bash
sudo apt install xmlstarlet
```
### Cartographer

1. Make `carto` directory.
    ```bash
    cd && mkdir carto_ws && cd carto_ws
    ```

2. Install [`cartographer ros`](https://google-cartographer-ros.readthedocs.io/en/latest/compilation.html#building-installation)

    If errors occur, install the following dependencies according to your error messages.
    - (Dependency) [`ceres`](http://ceres-solver.org/installation.html)
    ```bash
    git clone https://ceres-solver.googlesource.com/ceres-solver
    cd ceres-solver
    mkdir build && cd build
    cmake ..
    sudo make install
    ```
    - (Dependency) Lua
    ```bash
    sudo apt-get install liblua5.2-0
    ```
    
3. Add the following line to `~/.bashrc`.
    ```bash
    source ~/carto_ws/devel_isolated/setup.bash
    ```

### PX4
1. Install [Qgroundcontrol](https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html#ubuntu)
2. Install [mavros](https://docs.px4.io/master/en/ros/mavros_installation.html)
    - Binary installation recommanded.
    - (Dependency) If errors regarding Geographic library occurs,
    ```bash
    sudo geographiclib-get-geoids egm96-5
    ```
3. Install [PX4](https://docs.px4.io/master/en/dev_setup/building_px4.html)
    - Build using `make px4_sitl gazebo`
4. Add the following lines to `~/.bashrc`.
    ```bash
    source /home/sw/src/Firmware/Tools/setup_gazebo.bash /home/sw/src/Firmware /home/sw/src/Firmware/build/px4_sitl_default
    export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:/home/sw/src/Firmware
    export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:/home/sw/src/Firmware/Tools/sitl_gazebo
    ```
    
## Executing Simulation
Run each command in seperate terminals.
```bash
roslaunch simulation_drone AIGC_2020.launch
roslaunch mavros_control mavros_control.launch
roslaunch cartographer_ros gazebo.launch
roslaunch tf_listener tf_listener.launch
roslaunch offboard_drone offboard.launch
roslaunch distance_map distance_map.launch
roslaunch mission_planner mission_planner_2.launch
roslaunch astar astar.launch
```

Finally, run the following node to fly.
```bash
rosrun mavros_control mavros_control_node
```
Apply arming/takeoff and autonomous mode using `t` and `g` in your keyboard.
