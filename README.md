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
1. Download Raspian Jessie Desktop(Stretch not supported) Lite https://www.raspberrypi.org/downloads/raspbian/
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
2. Plug the mini HDMI cable into the Raspberry Pi and connect the other end to a monitor
3. Connect the power supply to the Raspberry Pi
4. Click the 

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

# Installing Python 3.5
1. 1. Connect to the Raspberry Pi using SSH
2. Type the following in the PuTTY terminal pressing enter after every line and type y and enter when prompted
      sudo apt-get install -y build-essential tk-dev libncurses5-dev libncursesw5-dev libreadline6-dev libdb5.3-dev
      sudo apt-get install libgdbm-dev libsqlite3-dev libssl-dev libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev libffi-dev
      wget https://www.python.org/ftp/python/3.5.7/Python-3.5.7.tar.xz
      sudo tar xf Python-3.5.7.tar.xz
      cd Python-3.5.7
      sudo ./configure --prefix=/usr/local/opt/python-3.5.7
      sudo make -j4
      sudo make altinstall
      sudo ln -s /usr/local/opt/python-3.5.7/bin/pydoc3.5 /usr/bin/pydoc3.5
      sudo ln -s /usr/local/opt/python-3.5.7/bin/python3.5 /usr/bin/python3.5
      sudo ln -s /usr/local/opt/python-3.5.7/bin/python3.5m /usr/bin/python3.5m
      sudo ln -s /usr/local/opt/python-3.5.7/bin/pyvenv-3.5 /usr/bin/pyvenv-3.5
      sudo ln -s /usr/local/opt/python-3.5.7/bin/pip3.5 /usr/bin/pip3.5
      alias python='/usr/bin/python3.5'
      alias python3='/usr/bin/python3.5'
      ls /usr/bin/python*
      cd ..
      sudo rm -r Python-3.5.7
      rm Python-3.5.7.tar.xz
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
      
# Install Protobuff
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

# Install Dependancies
sudo apt-get freetype6-dev
pip3 install matplotlib

# Install Movidius NCS
sudo apt-get install -y libusb-1.0-0-dev libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler libatlas-base-dev git automake byacc lsb-release cmake libgflags-dev libgoogle-glog-dev liblmdb-dev swig3.0 graphviz libxslt-dev libxml2-dev gfortran python3-dev python-pip python3-pip python3-setuptools python3-markdown python3-pillow python3-yaml python3-pygraphviz python3-h5py python3-nose python3-lxml python3-matplotlib python3-numpy python3-protobuf python3-dateutil python3-skimage python3-scipy python3-six python3-networkx python3-tk
mkdir -p ~/workspace
cd ~/workspace
git clone -b ncsdk2 http://github.com/Movidius/ncsdk && cd ncsdk && make install
      
# Installing OpenCV
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libopencv-dev

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
sudo modprobe bcm2835-v4l2

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib

# Running Position Detection

# Running Object Recognition Example

# Retraining Object Recognition
