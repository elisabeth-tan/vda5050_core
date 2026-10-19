# jetty_demo
Jetty demo world and resources

![](media/jetty_demo_world.png)

## Steps to Launch

1. Ubuntu 24.4

Ensure the correct Ubuntu version is used

```bash
lsb_release -a
```

Launch the demo

```bash
cd jetty_demo
export GZ_SIM_RESOURCE_PATH=`pwd`/jetty_demo/models:$GZ_SIM_RESOURCE_PATH
gz sim -v 4 jetty_demo/worlds/jetty.sdf
```

## Development in distrobox

```bash
distrobox create -n jetty_demo --hostname jetty_demo -i ghcr.io/gazebosim/jetty_demo:main
distrobox enter jetty_demo

source /ws_jetty/install/setup.bash
ros2 launch jetty_demo world.launch.xml
```

## Performance notes

It can take some time to load the world with all the models.
The GUI will be non-responsive during this time.

To speed up loading the demo world, you can comment out different models
in the world, which helps improve startup time and RTF.

For example, some `Picking_Shelves*` were already commented out in
the world sdf file. To further speed things up, you can comment out
all of them.
