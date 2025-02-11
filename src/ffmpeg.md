# ffmpeg

修改音频比特率为128k
``` ffmpeg.exe -i input.mp4 -c:v copy -acodec aac -b:a 128k output.mp4 ```

修改视频编码为hevc、比特率为512kbps
``` ffmpeg -i input.mp4 -c:v hevc_nvenc -b:v 512k output.mp4 ```

合并无声视频与音轨为新视频，长度由最长的决定
``` ffmpeg -i input.mp4 -i input.aac -vcodec copy -acodec copy output.mp4 ```
