## Tensorflow RPI 

#### Setup for Rpi 4 



- sudo apt update
- sudo apt upgrade
- Enable camera
- Follow Edje Electronics tutorial 
https://www.youtube.com/watch?v=aimSGOAUI8Y

### Need the Open CV Module 
- pip3 install opencv-python==3.4.6.27
- pip show opencv-python

### Need the Tensorflow Lite Module for ARM 32
- pip install https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp37-cp37m-linux_armv7l.whl
