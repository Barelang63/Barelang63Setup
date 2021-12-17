# PC Setup
## Configure Bios
* Boot Mode : Legacy
* Fan Start PWM : 30%
* Fan High PWM : 75 %
* Turn On Turbo Mode

## How to Install Ubuntu 18.04 
1. Choose US Language
2. Don't Connect to Network
3. Choose Minimal Installation and Check the Third Party Checkbox
4. Choose Erase Disk and Install Ubuntu (Different Device > Different Allocation Disk)
5. Set Time to Jakarta
6. Set Username and Password (Depend on User)


# Setup Ubuntu 18.04
## First Setup after Reboot
1. Install Chrome Browser (Optional)
2. Open Terminal
Press Ctrl + Alt + T at one Time
```
sudo apt-y update
sudo apt-y upgrade
```
3. Open Software & Updates
4. Choose Additional & Updates
5. Choose Nvidia-driver-460-server (Zotac) then Apply Changes
6. Reboot
7. Make Sure in Setting > Details, The VGA Hardware is Shown

## Install OpenCV 3.4.4
Link : [Install OpenCV 3.4.4 on Ubuntu 18.04](https://learnopencv.com/install-opencv-3-4-4-on-ubuntu-18-04/)

Paste All the Code on Textbox to Terminal
Do it until Step 5

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

## Install ROS Melodic 
Open Terminal then copy the Code below to Terminal
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
Link : https://www.youtube.com/watch?v=kRE-tCk8mGQ
Alternative : The File needed for Installing Arduino already Downloaded in our Hardrive,
How to Install with already Downlaoded File
```
cd ~/Downloads/arduino-1.8.13-linux64/arduino-1.8.13
sudo chmod +x install.sh
./ install.sh 
```
