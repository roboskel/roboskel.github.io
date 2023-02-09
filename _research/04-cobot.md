---
title: Cobot demos
layout: page
description: Demos on Cobots 
---

# [UR3 teleoperation](https://vimeo.com/515896509)

This video demonstrates our method for "Robot Arm Cartesian Teleoperation from Noisy and Low-FrequencyHuman Position Information". Through a single RGB-D camera human body 2D pose estimations are obtained from OpenPose, and depth information is extracted from the Point Cloud. 
[Github](https://github.com/Roboskel-Manipulation/demo_teleoperation) 
[Publication](https://dl.acm.org/doi/abs/10.1145/3453892.3461627)

<iframe src="https://player.vimeo.com/video/515902128?h=3a70f0693a" width="640" height="360" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>



# [Human demonstration for robot movements](https://vimeo.com/523402969)

Demonstration of a ROS pipeline that allows the tracking of human movements and their replication by a UR3 collaborative robot. The 3D human wrist position in acquired using OpenPose and the associated PointCloud information. The onset and end of the movement are detected and the resulting raw trajectory is smoothed using Bezier Interpolation. The resulting Bezier curve is replicated by UR3 using a velocity control method. Robot commanded velocities are regulated by a P-controller. The robot motion produced by using raw human movement data (without smoothing) is demonstrated for comparison.

[Github](https://github.com/Roboskel-Manipulation/demo_motion_demonstration) 
[Publication](https://ieeexplore.ieee.org/abstract/document/9837150)
