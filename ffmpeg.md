
```console 
shell> ffmpeg -i input.mp4 output.avi
shell> ffmpeg -i input.avi -r 24 output.avi
shell> ffmpeg -i input.avi -b:v 64k -bufsize 64k output.avi

shell> ffmpeg -f avfoundation -list_devices true -i ""
shell> ffmpeg -f avfoundation -i "0:0" out.avi

shell> ffmpeg -f avfoundation -i
```

​
ffmpeg -f avfoundation -i "1" -vcodec libx264 -preset ultrafast -acodec libfaac -f flv rtmp://148.72.245.43:1935/mytv/live


### :books: 參考網站：
- [ffmpeg](https://ffmpeg.org/)
- [ffmpeg](https://ffmpeg.org/ffmpeg.html)
- https://www.ffmpeg.org/ffmpeg-devices.html
