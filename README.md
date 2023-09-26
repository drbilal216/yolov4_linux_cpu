# yolov4_linux_cpu


### Ubdate Linux
sudo apt-get update
sudo apt-get upgrade

### Installing Python3
sudo apt install python3

### Install Pip
sudo apt install python3-pip

### Install Jupyter notebook
pip3 install jupyter

### restart
reboot

### make a directory to work in
mkdir yolov4

### move to that directory
cd yolov4

### clone official Darknet
git clone https://github.com/AlexeyAB/darknet.git

### Install opencv and adding its envoirnment links
sudo apt update
sudo apt install python3-opencv
sudo apt install libopencv-dev

## Installation completed

### move to darknet directory
cd darknet

### update in Makefile
OPENCV=1
#OPENMP=1

### update in darknet/yolov4.cfg
batch=1 #64
subdivisions=1 #8
width=416 #608
height=416 #608

### run below command to compile darknet
make

### download darknet yolov4 weights
wget https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.weights

# working with images below are three ways

./darknet detect cfg/yolov4.cfg yolov4.weights data/dog.jpg

./darknet detector test cfg/coco.data cfg/yolov4.cfg yolov4.weights data/dog.jpg

./darknet detect cfg/yolov4.cfg yolov4.weights
data/horses.jpg

### You can also set threshold default is .25% setting 0.5 = 50%
./darknet detect cfg/yolov4.cfg yolov4.weights data/dog.jpg -thresh 0.5

### Working with Webcam
./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights

### Working with Video
./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights test.mp4

### saving video
./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights test.mp4 -out_filename output.avi

#########################
###### yolov4-tiny ######
#########################

### download yolov4 tiny weights
wget https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v4_pre/yolov4-tiny.weights

### Working with images with yolov4 tiny
./darknet detector test cfg/coco.data cfg/yolov4-tiny.cfg yolov4-tiny.weights data/dog.jpg

### Working with Video yolov4 tiny
./darknet detector demo cfg/coco.data cfg/yolov4-tiny.cfg yolov4-tiny.weights test.mp4

### saving video
./darknet detector demo cfg/coco.data cfg/yolov4-tiny.cfg yolov4-tiny.weights test.mp4 -out_filename output.avi

### Working with Webcam
./darknet detector demo cfg/coco.data cfg/yolov4-tiny.cfg yolov4-tiny.weights

######################################
###### yolov4-using self custom ######
######################################

### Copy paste cfg file in darkne/cfg and change (batch=1)(subdivision=1) (width=416,height=416)
### Copy paste obj.names and obj.data in darknet/data
### pase custom weights in root folder darknet

### image
./darknet detector test data/obj.data cfg/yolov4_custom2.cfg yolov4_custom2_last.weights data/hat_watch.jpg

### video
./darknet detector demo data/obj.data cfg/yolov4_custom2.cfg yolov4_custom2_last.weights data/Wallclock.mp4
./darknet detector demo data/obj.data cfg/yolov4_custom2.cfg yolov4_custom2_last.weights data/Wallclock.mp4 -out_filename output.avi

######################################
###### yolov4-tiny self custom ######
######################################


### Copy paste yolov4-tiny-custom1.cfg file in darkne/cfg and change (batch=1)(subdivision=1)
### Copy paste obj.names and obj.data in darknet/data
### pase custom yolov4-tiny-custom1_last.weights in root folder darknet

### image
./darknet detector test data/obj.data cfg/yolov4-tiny-custom1.cfg yolov4-tiny-custom1_last.weights data/hat_watch.jpg

### video
./darknet detector demo data/obj.data cfg/yolov4-tiny-custom1.cfg yolov4-tiny-custom1_last.weights data/Wallclock.mp4
./darknet detector demo data/obj.data cfg/yolov4-tiny-custom1.cfg yolov4-tiny-custom1_last.weights data/Wallclock.mp4 -out_filename output.avi

### Webcam
./darknet detector demo data/obj.data cfg/yolov4-tiny-custom1.cfg yolov4-tiny-custom1_last.weights -c 0
