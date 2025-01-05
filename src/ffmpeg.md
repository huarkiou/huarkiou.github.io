# ffmpeg

修改音频比特率为128k
``` ffmpeg.exe -i input.mp4 -c:v copy -acodec aac -b:a 128k output.mp4 ```


修改视频编码为hevc
``` ffmpeg -i input.mp4 -c:v hevc_nvenc output.mp4 ```
