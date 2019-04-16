# V5PiHAT
This repository contains documentation, setup scripts and software examples need to integrate the V5 PiHAT with the VEX V5 robot control system.

# Requirements
1. Window 10
2. V5Hat
3. Rapberry Pi Zero W
   https://www.raspberrypi.org/products/raspberry-pi-zero-w/
4. Raspberry Pi Camera V2
   
5. A 5.25V 2.5A USB micro power supply
6. A USB type A to micro cable
7. At least an 8GB micro SD card
8. A micro SD card do USB adapter
9. A monitor with either an HDMI port or display port.
10. A mini HDMI to HDMI or Display Port cable.
# Hardware Setup

# Loading OS
1. Download Raspian Stretch Lite https://www.raspberrypi.org/downloads/raspbian/
2. Download and install Etcher https://www.balena.io/etcher/
3. Connect the uSD to the computer using the adapter or other method
4. Type BalenaEtcher into the start menu and click BelenaEtcher
5. Click the Select Image Button
6. Navigate to and select the Raspian Stretch Light zip file
7. Click Select Drive
8. Navigate to and select the uSD folder
9. Click the Flash! button and wait for the program to complete

# Configuring the Raspbian for SSH
1. Make sure the uSD card is connected to the computer
2. Create a new text file and save it as ssh in the boot directory of the uSD card
3. Create another file named wpa_supplicant.conf
4. Open the file and type the following substituting wifi_ssid with your wifi ssid and password with your wifi passward:
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
   ssid="wifi_ssid"
   scan_ssid=1
   psk="password"
   key_mgmt=WPA-PSK
   }

5. Save the file  as wpa_supplicant.conf in the boot directory

# Connecting to the Raspberry Pi using SSH
1. Insert the uSD card into the Raspberry Pi
2. Plug the mini HDMI cable into the Raspberry Pi and connect the other end to a monitor
3. Plug the 2.5A power supply into the Raspberry Pi
4. Record the IP address of the Raspberry Pi. The IP address is shown on completion of boot
5. Download and install PuTTY on your windows machine https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
6. Type PuTTY into the Windows search bar and run the program
7. In the Session category, type in the IP address in the text box labeled Host Name(or IP address)
8. If this is the first time connecting, PuTTY will issue a security alert. Click Yes.
9. Enter pi as the login
10. Enter raspberry as the password
11. Once connected, there is no need to use the monitor. Note that if you can't connect in the futer, the IP address may have changed and so you will need to plug the monitor back in in order to acquire the IP address.

# Installing Python 3.7
1. 1. Connect to the Raspberry Pi using SSH
2. Type the following in the PuTTY terminal pressing enter after every line and type y and enter when prompted
      sudo apt-get install -y build-essential tk-dev libncurses5-dev libncursesw5-dev libreadline6-dev libdb5.3-dev
      sudo apt-get install libgdbm-dev libsqlite3-dev libssl-dev libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev libffi-dev
      wget https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tar.xz
      sudo tar xf Python-3.7.0.tar.xz
      cd Python-3.7.0
      sudo ./configure --prefix=/usr/local/opt/python-3.7.0
      sudo make -j 4
      sudo make altinstall
      sudo ln -s /usr/local/opt/python-3.7.0/bin/pydoc3.7 /usr/bin/pydoc3.7
      sudo ln -s /usr/local/opt/python-3.7.0/bin/python3.7 /usr/bin/python3.7
      sudo ln -s /usr/local/opt/python-3.7.0/bin/python3.7m /usr/bin/python3.7m
      sudo ln -s /usr/local/opt/python-3.7.0/bin/pyvenv-3.7 /usr/bin/pyvenv-3.7
      sudo ln -s /usr/local/opt/python-3.7.0/bin/pip3.7 /usr/bin/pip3.7
      alias python='/usr/bin/python3.7'
      alias python3='/usr/bin/python3.7'
      ls /usr/bin/python*
      cd ..
      sudo rm -r Python-3.7.0
      rm Python-3.7.0.tar.xz
      . ~/.bashrc
      python -V
      
# Installing TensorFlow & Keras on Raspberry Pi
1. Connect to the Raspberry Pi using SSH
2. Type the following in the PuTTY terminal pressing enter after every line and type y and enter when prompted
      sudo apt update
      sudo apt install python3-dev python3-pip
      sudo apt install libatlas-base-dev
      sudo pip3 install -U virtualenv
      pip3 --no-cache-dir install tensorflow
# Install Dependancies
1. Connect to the Raspberry Pi using SSH
2. Type the following in the PuTTY terminal pressing enter after every line and type y and enter when prompted
sudo apt-get install autoconf automake libtool curl
wget https://github.com/google/protobuf/releases/download/v3.7.1/protobuf-all-3.7.1.tar.gz
tar -zxvf protobuf-all-3.7.1.tar.gz
cd protobuf-3.7.1
./configure
make
make check 
sudo make install
cd python
export LD_LIBRARY_PATH=../src/.libs
python3 setup.py build --cpp_implementation 
python3 setup.py test --cpp_implementation
sudo python3 setup.py install --cpp_implementation
export PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION=cpp
export PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION_VERSION=3
sudo ldconfig
protoc
sudo reboot now


      pip3 --no-cache-dir install opencv-python
      pip3 install libxm12 libxslt pillow lxml jupyter matplotlib cython
      pip3 install opencv-python
# Installing OpenCV
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libopencv-dev

--Below here is old
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libtiff5-dev libjasper-dev libpng12-dev
sudo apt-get install libjpeg-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libatlas-base-dev gfortran
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
sudo apt-get install python-dev
sudo apt-get install python-devel
sudo pip install numpy
wget "https://github.com/jabelone/OpenCV-for-Pi/raw/master/latest-OpenCV.deb"
sudo dpkg -i latest-OpenCV.deb


Below here is old
sudo apt-get -y install build-essential cmake cmake-curses-gui pkg-config libpng12-0 libpng12-dev libpnglite-dev zlib1g-dbg zlib1g zlib1g-dev pngtools libtiff5-dev libtiff5 libtiffxx0c2 libtiff-tools libeigen3-dev

sudo apt-get -y install libjpeg8 libjpeg8-dev libjpeg8-dbg libjpeg-progs ffmpeg libavcodec-dev libavcodec53 libavformat53 libavformat-dev libgstreamer0.10-0-dbg libgstreamer0.10-0 libgstreamer0.10-dev libxine1-ffmpeg libxine-dev libxine1-bin libunicap2 libunicap2-dev swig libv4l-0 libv4l-dev python-numpy libpython3.7 python-dev python3.7-dev libgtk2.0-dev

sudo apt-get install cmake-curses-gui
wget https://sourceforge.net/projects/opencvlibrary/files/opencv-unix/3.4.1/opencv-3.4.1.zip/download
mv download opencv
unzip opencv
cd opencv-3.4.1
mkdir build
cd build
ccmake ../
make
sudo make install

Below here is old
sudo apt-get -y install build-essential checkinstall cmake pkg-config yasm
sudo apt-get -y install git gfortran
sudo apt-get -y install libjpeg8-dev libjasper-dev libpng12-dev
sudo apt-get -y install libtiff5-dev
sudo apt-get -y install libtiff-dev
sudo apt-get -y install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
sudo apt-get -y install libxine2-dev libv4l-dev
cd /usr/include/linux
sudo ln -s -f ../libv4l1-videodev.h videodev.h
cd $cwd
sudo apt-get -y install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
sudo apt-get -y install libgtk2.0-dev libtbb-dev qt5-default
sudo apt-get -y install libatlas-base-dev
sudo apt-get -y install libmp3lame-dev libtheora-dev
sudo apt-get -y install libvorbis-dev libxvidcore-dev libx264-dev
sudo apt-get -y install libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt-get -y install libavresample-dev
sudo apt-get -y install x264 v4l-utils
git clone https://github.com/opencv/opencv.git
cd opencv
git checkout $cvVersion
cd ..
git clone https://github.com/opencv/opencv_contrib.git
cd opencv_contrib
git checkout $cvVersion
cd ..

git clone https://github.com/opencv/opencv.git
cd opencv
git checkout $cvVersion
cd ..
 
git clone https://github.com/opencv/opencv_contrib.git
cd opencv_contrib
git checkout $cvVersion
cd ..

cd opencv
mkdir build
cd build

cmake -D CMAKE_BUILD_TYPE=RELEASE \
            -D CMAKE_INSTALL_PREFIX=$cwd/installation/OpenCV-"$cvVersion" \
            -D INSTALL_C_EXAMPLES=ON \
            -D INSTALL_PYTHON_EXAMPLES=ON \
            -D WITH_TBB=ON \
            -D WITH_V4L=ON \
            -D OPENCV_PYTHON3_INSTALL_PATH=$cwd/OpenCV-$cvVersion-py3/lib/python3.5/site-packages \
        -D WITH_QT=ON \
        -D WITH_OPENGL=ON \
        -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
        -D BUILD_EXAMPLES=ON ..
        
sudo sed -i 's/CONF_SWAPSIZE=1024/CONF_SWAPSIZE=100/g' /etc/dphys-swapfile
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start

echo "sudo modprobe bcm2835-v4l2" >> ~/.profile

# Installing Raspbicam
sudo apt-get install cmake
cd ~
wget https://sourceforge.net/projects/raspicam/files/raspicam-0.1.6.zip/download
mv download raspicam
unzip raspicam
rm raspicam
cd raspicam-0.1.6
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig

sudo rpi-update
sudo reboot now
git clone git://git.linuxtv.org/v4l-utils.git
cd v4l-utils
sudo apt-get install autoconf gettext libtool libjpeg62 libjpeg62-dev
//autoreconf -vfi
./bootstrap.sh
./configure
make
sudo make install
sudo modprobe bcm2835-v4l2

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib

# Running Position Detection

# Running Object Recognition Example

# Retraining Object Recognition
