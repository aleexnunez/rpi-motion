# rpi-motion

[Motion](https://motion-project.github.io/index.html) implementation compatible with Raspberry Pi devices.


## Installation
In order to get it running just clone the repository:

`git clone https://github.com/Al3xeezer/rpi-motion.git`

Then, move to the folder containing the Dockerfile:

`cd rpi-motion`

And build the image (specify the image tag as you want):

`docker build . -t al3xeezer/rpi_motion`

## Usage

To get the container up and running just type:

`docker run -d --name=rpi_cam --device=/dev/video0:/dev/video0 -v ~/videos:/mnt/motion -p 8081:8081 al3xeezer/rpi_motion:latest`

Finally, to check that everything its OK just open a browser and go to `http://<yourIP>:8081`

## FAQ
* In order to run Motion you need to attach the camera to the docker container. 
By using `--device=/dev/video0:/dev/video0` you are mapping the camera plugged to the Raspberry to the actual container.

* One common error at running the container is: 
`Error response from daemon: linux runtime spec devices: error gathering device information while adding custom device "/dev/video0": no such file or directory`

     You can easily fix it by typing: `sudo modprobe bcm2835-v4l2`
 
 * In the `docker run` command Im using `-v` just in case I want to record/save the videos in the future (by default, it just streams the content, so isnt really needed).
 
 * If you need other Motion configuration, just modify the Dockerfile and change the settings as you like.
