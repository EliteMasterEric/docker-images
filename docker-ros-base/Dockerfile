FROM ros:kinetic-ros-base-xenial

# install Dataspeed repositories
RUN sh -c 'echo "deb [ arch=amd64 ] http://packages.dataspeedinc.com/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-dataspeed-public.list'
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 66F84AE1EB71A8AC108087DCAF677210FF6D3CDA
RUN apt-get update

RUN sh -c 'echo "yaml http://packages.dataspeedinc.com/ros/ros-public-kinetic.yaml kinetic" > /etc/ros/rosdep/sources.list.d/30-dataspeed-public-kinetic.list'
RUN rosdep update

RUN apt-get update && apt-get install -y \
	ros-kinetic-tf \
	ros-kinetic-tf2 \
	ros-kinetic-dataspeed-can \
	ros-kinetic-dataspeed-pds

#RUN rosdep install --from-paths src --ignore-src -y
