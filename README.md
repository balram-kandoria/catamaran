## Install Martitime dependencies
```bash
sudo apt-get update
sudo apt-get install libcgal-dev libfftw3-dev
```
## Pull Maritime Module
```bash
git submodule update --init
```
## Compile package (Must be in /catamaran directory)
```bash
colcon build --symlink-install --merge-install --cmake-args \
-DCMAKE_BUILD_TYPE=RelWithDebInfo \
-DBUILD_TESTING=ON \
-DCMAKE_CXX_STANDARD=17
```

## Source the workspace
```bash
source ./install/setup.bash
```

## Optional GUI Plugin 
```bash
cd path/catmaran/src/asv_wave_sim/gz-waves/src/gui/plugins/waves_control 
mkdir build && cd build
cmake .. && make
```

## Set Environmental Variables (Recommend updating .bashrc)
```bash
export GZ_VERSION=garden

export GZ_IP=127.0.0.1

export GZ_SIM_RESOURCE_PATH=\
$GZ_SIM_RESOURCE_PATH:\
$HOME/catmaran/src/asv_wave_sim/gz-waves-models/models:\
$HOME/catmaran/src/asv_wave_sim/gz-waves-models/world_models:\
$HOME/catmaran/src/asv_wave_sim/gz-waves-models/worlds

export GZ_SIM_SYSTEM_PLUGIN_PATH=\
$GZ_SIM_SYSTEM_PLUGIN_PATH:\
$HOME/catmaran/install/lib

export GZ_GUI_PLUGIN_PATH=\
$GZ_GUI_PLUGIN_PATH:\
$HOME/catmaran/src/asv_wave_sim/gz-waves/src/gui/plugins/waves_control/build
```

## Start Maritime simulation
```bash
LIBGL_ALWAYS_SOFTWARE=1 gz sim waves.sdf
```