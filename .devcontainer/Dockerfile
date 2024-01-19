FROM osrf/ros:melodic-desktop-full

ARG DEBIAN_FRONTEND=noninteractive

ARG UID=2000
ARG GID=2000

RUN apt update && apt install -y \
git \
vim \
wget \
gdb \
&& apt clean \ 
&& rm -rf /var/lib/apt/lists/* \
&& groupadd -g $GID dev-user \
&& useradd -m -d /home/dev-user -s /bin/bash -u $UID -g $GID dev-user

RUN echo "source /opt/ros/melodic/setup.bash" >> /home/dev-user/.bashrc
RUN mkdir -p /home/dev-user/catkin_ws/src
RUN cd /home/dev-user/catkin_ws && /bin/bash -c "source /opt/ros/melodic/setup.bash; catkin_make"
RUN echo "source /home/dev-user/catkin_ws/devel/setup.bash" >> /home/dev-user/.bashrc
RUN /bin/bash -c "source /home/dev-user/catkin_ws/devel/setup.bash"

USER dev-user