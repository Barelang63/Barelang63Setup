# PC Setup
## Configure Bios
* Boot Mode : Legacy
* Fan Start PWM : 30%
* Fan High PWM : 75 %
* Turn On Turbo Mode

## How to Install Ubuntu 18.04 
* Choose US Language
* Don't Connect to Network
* Choose Normal Installation and Check the Third Party Checkbox
* Choose Erase Disk and Install Ubuntu or Something Else (Different Device > Different Allocation Disk)
* For Disk Allocation, Create 1 Partition , choose primay use Ext4 journaling file system and Choose Root ( / )
* Choose the Partition that created before as a boot Option
6. Set Time to Jakarta
* Set Username and Password (Depend on User)


# Setup Ubuntu 18.04
## First Setup after Reboot
* Install Chrome Browser (Optional)
* Open Terminal
Press Ctrl + Alt + T at one Time
```
sudo apt update
sudo apt upgrade
```
* Open Software & Updates
* Choose Additional & Updates
* Choose Nvidia-driver-460-server (Zotac) then Apply Changes
* Reboot
* Make Sure in Setting > Details, The VGA Hardware is Shown

## Setup Monitoring with VNC
### Ubuntu
### Install Dconf Editor
* Put This on Terminal 
```sudo apt install -y dconf-editor```
* Open Activities Overview / Press Windows Button Instead, then Type Dconf Editor
* After Dconf Editor open, navigate to org -> gnome -> desktop -> remote-access, 
* Uncheck the Value of required Encryption

### Enabling Desktop Sharing
* Open Activites Overview / Press Windows Button Instead, then Type Desktop Sharing
* Enable Sharing
* Allow other users to control your desktop
* Disable You must confirm each access to this machine
* Enable require the user to enter this password, to secure login access
* Fill Password with Everything you Can Remember, Example : 1

### Install XServer
* Put This On Terminal
```
sudo apt-get install xserver-xorg-core
sudo apt-get install xserver-xorg-video-dummy
sudo apt-get install --reinstall xserver-xorg-input-all
sudo nano /usr/share/X11/xorg.conf.d/xorg.conf
``` 
* Paste this 
```
Section "Screen"
	Identifier "Default Screen"
	Device "Default Device"
	Monitor "Configured Monitor"
	Option "ConnectedMonitor" "HDMI-0"
	SubSection "Display"
		Depth 24
		Virtual 1024 768
	EndSubSection
EndSection
```
* Reboot

### On Windows
* Download and Install [VNC Client](https://www.realvnc.com/en/connect/download/viewer/windows)
* Run VNC Viewer
* Go to File -> New Connection
* Fill VNC Server with Destination Ip Address, Exmple 192.168.0.101 (Robot 1 IP)
* Fill Name with Name you want to Fill
* If a Password is Required, Fill password that has been Created in Ubuntu Desktop Sharing

## Install OpenCV 3.4.4
Link : [Install OpenCV 3.4.4 on Ubuntu 18.04](https://learnopencv.com/install-opencv-3-4-4-on-ubuntu-18-04/)

* Paste All the Code from Step 1 to Terminal
* Do it until Step 5
* In Step 3 You Will get Error While Paste this on Terminal `sudo apt -y install python3-dev python3-pip python3-venv`
* Paste with this Instead
```
sudo apt -y install python3-dev python3-pip python3-venv
```
* In the Last Step 5, Before do `make -j4`, Check first your Core Processor with typing `nproc` in Terminal.
* The Numbers that Come Out will be your Core Processor, Use `make -j4` that 4 changes to your Core Processor to Faster Process.

## Install Cuda
Link : [Cuda Toolkit 10.2 Download](https://developer.nvidia.com/cuda-10.2-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal)

Follow the Instruction

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

( To Paste the Line in terminal use ctrl + shift + v )

( If there is a prompt to y / n, press y or press enter instead )
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

Create ROS Workspace [How to Create ROS Workspace](https://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment)

Create ROS Package [How to Create ROS Package](https://wiki.ros.org/ROS/Tutorials/CreatingPackage)

## Install Arduino

Link : [Installing Arduino IDE on Ubuntu 18.04](https://www.youtube.com/watch?v=kRE-tCk8mGQ)

Direct Download : [Arduino Download](https://downloads.arduino.cc/arduino-1.8.19-linux64.tar.xz)

How to Install with Downloaded File from Web
* Go to Folder where the File Downloaded
* Right Click on the Tar File, Choose Extract Here
* Open the Folder until You See `install.sh` File
* Open Folder in Terminal
``` 
sudo chmod +x install.sh
./install.sh
```
* After Done, Open Arduino Software

Alternative : The File needed for Installing Arduino already Downloaded in our Hardrive,

* How to Install with already Downlaoded File
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
* Paste this on Terminal
(If Arduino Folder is Missing, Open Arduino Software First)

```
cd ~/Arduino /libraries
rm -rf ros_lib
rosrun rosserial_arduino make_libraries.py . 
```
* if you want to include custom msg from the package
```
rosrun rosserial_arduino make_libraries.py . Name of Package
```
* Read Properly for Every Line 
* After Complete, Open Arduino go to examples then find the "ros_lib", if "ros_lib" exist, we've finished installing ROS on Arduino

### Fixed Permission for Arduino Serial Port
Paste this on Terminal
```
sudo usermod -a -G dialout ** (refers to pc username)
sudo chmod a+rw /dev/tty** (refers to the Arduino Port
```
Reboot

### How to Check Serial Port
* Paste this on Terminal `ls/dev` 
* Check which port is readed Usually ttyACM / ttyUSB

### How to Run Ros Serial
Paste this on Terminal
```
roscore (Need to Run ROS Environment)
rosrun rosserial_python serial_node.py /dev/ttyUSB0
```

### How to setup / Running Robot Striker
```
roscore (Need to run ROS Environment)
```
run serial arduino & arm 

note: before running the serial make sure the stm and arduino device ports are connected
```
./arm_serial.sh (for rosserial stm32)
./arduino_serial.sh (for rosserial arduino)

rosrun barelang63 strategy ( run the strategy program )

rosrun barelang63 stream (run the vision program)

rosrun barelang terima1.py (run the vision program)

rosrun barelang basestation (run the basestation program)
```
