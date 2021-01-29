# USRG Drone in Gazebo

## Install
### Cartographer

1. Make `carto` directory.
    ```bash
    cd && mkdir carto_ws && cd carto_ws
    ```

2. Install [`cartographer ros`](https://google-cartographer-ros.readthedocs.io/en/latest/)
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
    sudo apt-get install liblua-5.2
    ```

### PX4

1. Install [PX4](https://docs.px4.io/master/en/dev_setup/building_px4.html)

### etc.
```bash
sudo apt install xmlstarlet
```
