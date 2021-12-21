# PC Setup
## Configure Bios
* Boot Mode : Legacy
* Fan Start PWM : 30%
* Fan High PWM : 75 %
* Turn On Turbo Mode

## How to Install Ubuntu 18.04 
1. Choose US Language
2. Don't Connect to Network
3. Choose Normal Installation and Check the Third Party Checkbox
4. Choose Erase Disk and Install Ubuntu or Something Else (Different Device > Different Allocation Disk)
* For Disk Allocation, Create 1 Partition , choose primay use Ext4 journaling file system and Choose Root ( / )
* Choose the Partition that created before as a boot Option
6. Set Time to Jakarta
7. Set Username and Password (Depend on User)


# Setup Ubuntu 18.04
## First Setup after Reboot
1. Install Chrome Browser (Optional)
2. Open Terminal
Press Ctrl + Alt + T at one Time
```
sudo apt update
sudo apt upgrade
```
3. Open Software & Updates
4. Choose Additional & Updates
5. Choose Nvidia-driver-460-server (Zotac) then Apply Changes
6. Reboot
7. Make Sure in Setting > Details, The VGA Hardware is Shown

## Install OpenCV 3.4.4
Link : [Install OpenCV 3.4.4 on Ubuntu 18.04](https://learnopencv.com/install-opencv-3-4-4-on-ubuntu-18-04/)

Paste All the Code from Step 1 to Terminal
Do it until Step 5

In Step 3 You Will get Error While Paste this on Terminal `sudo apt -y install python3-dev python3-pip python3-vev`

Paste with this Instead
```
sudo apt -y install python3-dev python3-pip python3-venv
```

In the Last Step 5, Before do `make -j4`, Check first your Core Processor with typing `nproc` in Terminal.

The Numbers that Come Out will be your Core Processor, Use `make -j4` that 4 changes to your Core Processor to Faster Process.

## Install Cuda
Link : [Cuda Toolkit 10.2 Download](https://developer.nvidia.com/cuda-10.2-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal)

## Install Cudnn
The File needed for Installing Cudnn already Downloaded in our Hardrive, 

If the Files not Exist You can Download in [NVIDIA cuDNN](https://developer.nvidia.com/cudnn)
But You have to Sign up / Sign in to the Website 

### How to Install it
* Open Folder in Terminal in the Folder where cuDNN file exist.
* Use Command

```
sudo dpkg -i filename.deb
```
* Reboot if you are done installing these 3 Files.
* Open File Explorer goto path /usr/local/cuda/samples/1_Utilities_deviceQuery
* Open Folder in terminal
* Type `Sudo make` then type `./deviceQuery`
* If the "Result = Pass" it means Install cuDNN is Success.

## Install ROS 
Link : [ROS Melodic Ubuntu 18.04](http://wiki.ros.org/melodic/Installation/Ubuntu)

Or You can Paste this Code below to Terminal
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

sudo apt install curl # if you haven't already installed curl

curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

sudo apt update

sudo apt install ros-melodic-desktop-full

echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc

source ~/.bashrc

source /opt/ros/melodic/setup.bash

sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

sudo apt install python-rosdep

sudo rosdep init

rosdep update
```

## Install Arduino

Link : [Installing Arduino IDE on Ubuntu 18.04](https://www.youtube.com/watch?v=kRE-tCk8mGQ)

Alternative : The File needed for Installing Arduino already Downloaded in our Hardrive,

How to Install with already Downlaoded File
```
cd ~/Downloads/arduino-1.8.13-linux64/arduino-1.8.13
sudo chmod +x install.sh
./install.sh 
```

### How to run Arduino with ROS Serial
Paste this on Terminal
```
sudo apt-get install ros-melodic-rosserial-arduino
sudo apt-get install ros-melodic-rosserial
```

### Installing ros_lib to Arduino
Paste this on Terminal
```
cd Arduino /libraries
rm -rf ros_lib
rosrun rosserial_arduino make_libraries.py .
```
After Complete, Open Arduino go to examples then find the "ros_lib", if "ros_lib" exist, we've finished installing ROS on Arduino

### Fixed Permission for Arduino Serial Port
Paste this on Terminal
```
sudo usermod -a -G dialout ** (refers to pc username)
sudo chmod a+rw /dev/tty** (refers to the Arduino Port
```
Reboot

### How to Check Serial Port
Paste this on Terminal `ls/dev` 
Check which port is readed Usually ttyACM / ttyUSB

### How to Run Ros Serial
Paste this on Terminal
```
roscore (Need to Run ROS Environment)
rosrun rosserial_python serial_node.py /dev/ttyUSB0
```
