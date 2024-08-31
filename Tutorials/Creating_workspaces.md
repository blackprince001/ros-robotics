# How to setup the workspace

1. First, make sure you have ROS 1 installed and your environment properly set up. You can do this by sourcing the setup file:

   ```bash
   source /opt/ros/<your_ros_distro>/setup.bash
   ```

   Replace `<your_ros_distro>` with your ROS distribution (e.g., noetic, melodic).

2. Create a directory for your catkin workspace:

   ```bash
   mkdir -p ~/catkin_ws/src
   cd ~/catkin_ws/
   ```

3. Initialize the catkin workspace:

   ```bash
   catkin init
   ```

4. Build the workspace:

   ```bash
   catkin build
   ```

5. Source the new setup file to add the workspace to your ROS environment:

   ```bash
   source devel/setup.bash
   ```

6. To make sure your workspace is properly overlayed on top of the ROS environment, you can check the ROS_PACKAGE_PATH:

   ```bash
   echo $ROS_PACKAGE_PATH
   ```

   You should see your workspace path followed by the system-wide ROS installation path.

7. To make this change permanent, add the source command to your `.bashrc` file:

   ```bash
   echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
   ```

Now your catkin workspace is set up and ready to use. You can create or clone ROS packages into the `src` directory, and use `catkin build` to compile them.
