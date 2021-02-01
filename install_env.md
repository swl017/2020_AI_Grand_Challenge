# USRG Drone in Gazebo

## Install
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

### PX4
1. Install [Qgroundcontrol](https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html#ubuntu)
2. Install [mavros](https://docs.px4.io/master/en/ros/mavros_installation.html)
    - Binary installation recommanded.
3. Install [PX4](https://docs.px4.io/master/en/dev_setup/building_px4.html)
    - Build using `make px4_sitl gazebo`
