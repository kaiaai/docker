A Docker file to build the Kaia.ai ROS development image. The Docker image contains:
- ROS2 with its desktop environment
- Micro-ROS including the Micro-ROS agent
- A workspace with Kaia.ai ROS2 packages

A pre-built image is available at [Docker Hub](https://hub.docker.com/r/kaiaai/kaia-ros)

Docker pre-built image pull command:
```
docker pull kaiaai/kaia-ros-desktop:humble
```

Docker image build command:
```
docker build --no-cache -t kaiaai/kaia-ros-desktop:humble .
```

Docker run command:
```
docker run --name kaia-ros-desktop-humble -it --rm -p 8888:8888/udp \
  -e DISPLAY=host.docker.internal:0.0 -e LIBGL_ALWAYS_INDIRECT=0 \
  kaiaai/kaia-ros-desktop:humble
```

Kaia.ai ROS2 launch command:
```
ros2 launch kaia_launch launch.py
```

Docker run command that launches the Kaia.ai application stack (including Micro-ROS agent) automatically:
```
docker run --name kaia-ros-desktop-humble -it --rm -p 8888:8888/udp \
  -e DISPLAY=host.docker.internal:0.0 -e LIBGL_ALWAYS_INDIRECT=0 \
  kaiaai/kaia-ros-desktop-humble:humble launch
```

Docker command to open an extra bash terminal:
```
docker exec -it kaia-ros-desktop-humble bash
```

When running in Docker for Windows, use [XLaunch](https://sourceforge.net/projects/xming/) to display GUI from the container (rviz, etc.)
When launching XLaunch, set its display number to zero.