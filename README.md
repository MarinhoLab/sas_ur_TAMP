# SAS UR TAMP

This repository runs docker which enables the simulation and robot control of UR3e for simple rearrangement of items.

pre-requisitrtes :

1. Docker installed
2. x86 system, mac systems have issues running this

To make changes and use the docker container again make sure you clean everything (including the cache too)

```bash
docker compose down -v
```

## Docker

### Simulation

https://github.com/user-attachments/assets/bfee1148-bfe3-4425-80da-04fcd65d2b18

![](./sas_urct_simulation.mp4)

Run

```commandline
mkdir -p ~/sas_workspace/docker/sas_ur_TAMP/simulation_demo/workspace
cd ~/sas_workspace/docker/sas_ur_TAMP/simulation_demo
curl -OL https://raw.githubusercontent.com/MarinhoLab/sas_ur_TAMP/refs/heads/main/.devel/simulation_demo/compose.yml

xhost +local:root
docker compose up
```

> [!NOTE]
> If running on a `arm64` Linux system host, remember to install
> ```commandline
> sudo apt-get install qemu-user-static
> ```

> [!NOTE]
> For any example with the simulator, you might need to open port `23000` in the host. This is not always needed.
> ```commandline
> sudo ufw allow 23000
> ```

---

# This is Still In-progress

### Real robot

> [!CAUTION]
> For using the real robot, you **must** have the risk assessments in place. 
> This guide is meant to be helpful but holds absolutely no liability whatsoever. More details are available in the software license.

> [!WARNING]
> This code will move the robot. Be sure that the workspace is free and safe for operation.
> Be sure that the robot is in a joint configuration in which it will not hit itself or anything around it. 

https://github.com/user-attachments/assets/62ac7ccd-d7c8-41f7-8af8-1b17919d90f2

![](./sas_urct_realrobot.mp4)

Run

```commandline
mkdir -p ~/sas_tutorial_workspace/docker/sas_ur_control_template/robot_demo
cd ~/sas_tutorial_workspace/docker/sas_ur_control_template/robot_demo
curl -OL https://raw.githubusercontent.com/MarinhoLab/sas_ur_control_template/refs/heads/main/.devel/robot_demo/compose.yml

docker compose up
```
> [!IMPORTANT]
> Be sure that the teaching pendant is in `Remove Control` mode.

> [!TIP]
> Use your robot's IP address in `ur1_ip`. Refer to `launch/_real_robot_launch.py`.

### Real robot and simulation

> [!IMPORTANT]
> Consider all information given for the simulation and real robot demos.

Run

```commandline
mkdir -p ~/sas_tutorial_workspace/docker/sas_ur_control_template/robot_and_simulation_demo
cd ~/sas_tutorial_workspace/docker/sas_ur_control_template/robot_and_simulation_demo
curl -OL https://raw.githubusercontent.com/MarinhoLab/sas_ur_control_template/refs/heads/main/.devel/robot_and_simulation_demo/compose.yml

xhost +local:root
docker compose up
```
