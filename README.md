## Video-streaming-container
### To build docker image:
```
$ docker build -t your_image_name .
```
Beforing run container from your created image, make sure download a mp4 video and save it to ```your/video/folder```
### To run video-streaming-container:
```
$ docker run -d -v your/video/folder://opt/vlc-media --name vlc -p 8554:8554 your_image_name your_video_name.mp4 --loop :sout=#gather:rtp{sdp=rtsp://:8554/} :network-caching=1500 :sout-all :sout-keep
```
- The ```your/video/folder``` is need to be given in the full path string
### Example:
your/video/folder <=> /home/dcn/media


your_image_name <=> tuong


your_video_name.mp4 <=> kubecon.mp4
```
$ docker build -t tuong .
$ docker run -d -v /home/dcn/media://opt/vlc-media --name vlc -p 8554:8554 tuong kubecon.mp4 --loop :sout=#gather:rtp{sdp=rtsp://:8554/} :network-caching=1500 :sout-all :sout-keep
```
### Open vlc
Install vlc in your PC and connect to rstp://your_server_ip:8554
