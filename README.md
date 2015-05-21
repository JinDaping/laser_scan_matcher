Laser scan tools for ROS
===================================

Overview
-----------------------------------

Note : Forked from ccny-ros-pkg/scan_tools ( Modified for rosbuild indigo {not completed yet} )

Laser scan processing tools. The meta-package contains:
 
 * `laser_scan_matcher`: an incremental laser scan matcher, using Andrea Censi's Canonical 
Scan Matcher implementation. It downloads and installs Andrea Censi's Canonical Scan Matcher [1] locally.

Installing
-----------------------------------

### From source ###

Create a [catkin workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace) and navigate to its source directory (ex. `~/catkin_ws/src`).

Make sure you have git installed:

    sudo apt-get install git-core

Download the stack from our repository:

    git clone https://github.com/ccny-ros-pkg/scan_tools.git

Install any dependencies using [rosdep](http://wiki.ros.org/rosdep).

    rosdep install scan_tools

Compile your catkin workspace from its root folder (eg. `~/catkin_ws`):

    catkin_make

Finally, source the information from your catkin workspace (or add it to your `~/.bashrc`)

    source devel/setup.bash

More info
-----------------------------------

http://wiki.ros.org/scan_tools

References
-----------------------------------
 [1] A. Censi, "An ICP variant using a point-to-line metric" Proceedings of the 
IEEE International Conference on Robotics and Automation (ICRA), 2008

