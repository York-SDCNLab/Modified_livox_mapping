# Modified_livox_mapping
This is a modified version of the [original livox_mapping](https://github.com/Livox-SDK/livox_mapping).
## Purposes of this Projecrt
* Make the original project able to run with ROS Noetic in Ubuntu 20.04.
* Collect a point cloud that contains multiple fiducial markers from a SLAM framework.
* Save the intensity values for the points of the final 3D map.
## Modifications
* Solved the conflicts between the old-version OpenCV and the OpenCV inside Noetic. (Cmake error will occur otherwise)
* Solved the display issue due to caused by different rviz versions. Now, even using Noetic, you can watch the mapping process without changing the settings in rviz.
* Added a new script to convert the format of the final-built 3D map from RGB8 to XYZI.
## How to use
``git clone https://github.com/York-SDCNLab/Modified_livox_mapping.git`` <br>
``cd modified``<br>
``cd catkin_ws``<br>
``catkin_make``<br>
<br>
If you see a CMake error at this step complaining about livox_ros_driverConfig.camke, you need to install [livox_ros_driver](https://github.com/Livox-SDK/livox_ros_driver) first. Once livox_ros_driver is installed, in the catkin_ws of livox_ros_driver, open a terminal and type in ``source ./devel/setup.bash``. Then go back to the catkin_ws of this project, redo ``catkin_make`` (in the same terminal). <br>
<br>
``source ./devel/setup.bash``<br>
``roslaunch livox_mapping mapping_mid.launch``<br>
Open a new terminal and type in <br>
``rosbag play yourbagname``<br>
<br>
Now you can observe the mapping in rviz directly. The PCD file of the 3D map will be saved in the folder named 'original_livox_mapping_result' under your home path. You may change the name of the folder in the launch file.


The rosbag corrsponding to the figure above is available [here](https://drive.google.com/file/d/1ZmS2tajLKvlstaqA8L-T6nzKj0bfL30n/view?usp=sharing).
