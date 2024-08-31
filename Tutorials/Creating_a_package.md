# Creating your first Package in ROS

1. First, make sure you're in your catkin workspace's `src` directory:

   ```bash
   cd ~/catkin_ws/src
   ```

2. Use the `catkin_create_pkg` command to create a new package. Let's create a package named "my_package" with dependencies on `roscpp` or `rospy` or both and `std_msgs`:

   ```bash
   catkin_create_pkg my_package roscpp std_msgs
   ```

   This creates a new directory `my_package` with some basic files.

3. Navigate into your new package directory:

   ```bash
   cd my_package
   ```

4. The package structure should look like this:
   ```
   my_package/
   ├── CMakeLists.txt
   ├── package.xml
   ├── include/my_package/
   └── src/
   ```

5. To add a C++ node, create a new file in the `src` directory:

   ```bash
   touch src/my_node.cpp
   ```

6. Open `my_node.cpp` in your preferred text editor and add some basic code:

   ```cpp
   #include "ros/ros.h"
   #include "std_msgs/String.h"

   int main(int argc, char **argv)
   {
     ros::init(argc, argv, "my_node");
     ros::NodeHandle nh;
     
     ROS_INFO("Hello from my_node!");
     
     ros::spin();
     return 0;
   }
   ```

7. Edit the `CMakeLists.txt` file to build your node. Add these lines at the end:

   ```cmake
   add_executable(my_node src/my_node.cpp)
   target_link_libraries(my_node ${catkin_LIBRARIES})
   ```

8. Go back to the workspace root and build your package:

   ```bash
   cd ~/catkin_ws
   catkin build
   ```

9. Source the setup file again:

   ```bash
   source devel/setup.bash
   ```

Now your package is created and built! You can run your node using:

```bash
rosrun my_package my_node
```

This is a basic setup. Depending on your needs, you might want to add more nodes, create launch files, or add custom messages and services.
