## Instructions to run the Gazebo Simulation and develop the competition locally
In the feedback provided students pointed out to the fact that TCS was extremenly slow and it was often painful to carryout the debugging session. I am writing this to serve as a guide to work on the competition on a local machine. 
The ideal setup be an Ubuntu installation (preferbly 16 or 18) installed with ROS Kinetic. As many of the students like me don't actually work on Ubuntu and will find this step to be a pain. I have tried running ROS on a VM on MAC OS and it seems to be a better alternative to alteast TCS. I am going to detail the steps i took so that people who want to have local installion can use this with a VM if required.

My Setup : 
MBP 2019 running MACOS Big Sur. I am using VMware Fusion (https://ualberta.onthehub.com/WebStore/OfferingDetails.aspx?o=6597520e-2ffc-ea11-812f-000d3af41938) which is freely available to UofA students the last time I checked.

VM Ware OS specification : I am using Ubuntu 16.04 LTS with 4 cores and 8 GB RAM ( I think 2 cored and 2/4 GB RAM will also do good). I would recommend keeping atleast 20 GB of hardisk space. 

Steps : 
1. ### Install ROS Kinetic  
The first step is to install ROS Kinetic and it is pretty straightfoward if you follow the procedure given on the website. (http://wiki.ros.org/kinetic/Installation/Ubuntu). I think this might not work on Noetic, because some of the turtle bot packages that are being used are not exactly strucuted the same way that they were in kinetic

2. ### Installing TurtleBot Dependencies
Install the remaning turtlebot dependencies by running the following command
```
sudo apt-get install ros-kinetic-turtlebot*
```
This would install the necessary packages etc for the turtlebot robot.

3. ### Make a caktin_ws 
Make a catkin_ws and place the competition1 folder inside the src i.e. 
```
mkdir -p ~/catkin_ws/src
cd ~/caktin_ws
catkin_make
```
Copy the competition 1 folder inside `catkin_ws/src` and run `catkin_make`
```
source ~/catkin_ws/devel/setup.bash
```
I recommend adding the following 2 lines at the end of your `.bashrc`
```
export SVGA_VGPU10=0
source ~/catkin_ws/devel/setup.bash
```
The first command is specific for VM's as I observed Gazebo was not running inside VM without that command. 

4. ### Running the simulation
After compiling simply run  the launch file and you will things working as normal
```
roslaunch competition1 main.launch
```
