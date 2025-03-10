Stands for Fast Forward Moving Picture Experts Group
# Video to Audio
```
ffmpeg -i input.mkv -q:a 0 -map a output.mp3
```
- `-i input.mkv`: Specifies the input MKV file.
- `-q:a 0`: Sets the best possible audio quality for MP3 (lower numbers mean better quality, with `0` being the best).
- `-map a`: Extracts only the audio track, ignoring the video.
---
# Merging two videos
1. Create a text file listing the MP4 files to concatenate:
```
file 'video1.mp4' 
file 'video2.mp4'
```
Save this file as `file_list.txt`.

2. Run the FFmpeg command:
```
ffmpeg -f concat -safe 0 -i file_list.txt -c copy output.mp4
```
- `-f concat`: Specifies concatenation mode.
- `-safe 0`: Ensures the file paths are treated as safe.
- `-i file_list.txt`: Reads the list of files to concatenate.
- `-c copy`: Avoids re-encoding for faster processing and no quality loss.
---
# Cropping Audio
```
ffmpeg -i input_audio.mp3 -ss [start_time] -t [duration] -c copy output_audio.mp3
```
Examples:
```
# from 30s to 1:10
ffmpeg -i input_audio.mp3 -ss 00:00:30 -t 00:00:40 -c copy output_audio.mp3

#from 10s to the end
ffmpeg -i input_audio.mp3 -ss 00:00:10 output_audio.mp3
```
