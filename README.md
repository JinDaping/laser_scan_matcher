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

Goto your workspace directory for rosbuild.

Make sure you have git installed:

    sudo apt-get install git-core

Download the package from our repository:

    git clone https://github.com/usiraj/laser_scan_matcher.git


Compile the package from its folder:

    rosmake

More info for orignal package
-----------------------------------

http://wiki.ros.org/scan_tools

References
-----------------------------------
 [1] A. Censi, "An ICP variant using a point-to-line metric" Proceedings of the 
IEEE International Conference on Robotics and Automation (ICRA), 2008

