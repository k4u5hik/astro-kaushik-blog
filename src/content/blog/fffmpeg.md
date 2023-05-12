---
author: Kaushik Chemburkar
pubDatetime: 2023-05-08T20:19:00+11:00
title: FFmpeg video conversion to H.264 format and video joining
postSlug: ffmpeg
featured: false
draft: false
tags:
  - ffmpeg
ogImage: ""
description:
  FFmpeg video conversion to H.264 format and video joining
---

## Using FFmpeg for converting videos to H.264

H.264 video codec and AAC audio codec offers good compression and quality balance. Using this terminal command template and replacing the `input_video.ext` and `output_video.ext` we can convert the video.

```bash
ffmpeg -i input_video.ext -c:v libx264 -preset slow -crf 23 -c:a aac -b:a 128k -vf "scale=-1:480" -movflags +faststart output_video.mp4
```

### Explanation

`-i input_video.ext`: Specifies the input video file.

`-c:v libx264`: Sets the video codec to H.264.

`-preset slow`: Adjusts the encoding speed and compression ratio. Options include: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow. A slower preset provides better compression but takes more time to encode.

`-crf 23`: Sets the Constant Rate Factor (CRF) value for the video quality. A lower value provides better quality but larger file size. Values range from 0 (lossless) to 51 (lowest quality). Recommended values are between 18 and 28.

`-c:a aac`: Sets the audio codec to AAC.

`-b:a 128k`: Sets the audio bitrate to 128 kbps.

`-vf "scale=-1:480"`: Scales the video to a height of 480 pixels while maintaining the aspect ratio. You can adjust the value to control the output video resolution.

`-movflags +faststart`: Moves metadata to the beginning of the file for faster streaming.

## Combining videos

Create a text file that lists the input video files in the following format (one `file` per line).

```bash
file 'video1.mp4'
file 'video2.mp4'
```

Replace the `input_files.txt` and `output_video.mp4`. Use the following command template:

```bash
ffmpeg -f concat -safe 0 -i input_files.txt -c copy output_video.mp4
```

### Explanation

`-f concat`: Specifies the concat demuxer format to concatenate the files.

`-safe 0`: Allows usage of absolute file paths and disables the safe mode for the concat demuxer. Set it to 1 if you are using relative paths in the text file.

`-i input_files.txt`: Specifies the input text file containing the list of video files.

`-c copy`: Copies the streams (video, audio, and others) from the input files without re-encoding them.

## Watermarking Videos

This command first scales the watermark to 20% of the video height while maintaining its aspect ratio, then overlays the scaled watermark to the bottom right corner of the video.

```bash
ffmpeg -i input.mp4 -i watermark.png -filter_complex "[1][0]scale2ref=oh*mdar:ih*0.2[logo][video];[video][logo]overlay=W-w-10:H-h-10" output_scaled.mp4
```

### Explanation

`[1][0]`: These are input stream specifiers. In FFmpeg, `[0]` generally refers to the first input file, and `[1]` to the second input file. In your command, `[0]` refers to `input.mp4` and `[1]` refers to `watermark.png`.

`scale2ref`: This is a filter that scales the second input to match the reference. In this case, it scales the watermark (second input) to match the video (first input).

`=oh*mdar:ih*0.2`: These are the options for the `scale2ref` filter.

`oh*mdar`: This scales the width of the watermark. `oh` refers to the original height of the first input (the video), and `mdar` (main display aspect ratio) is the aspect ratio of the first input. This ensures that the watermark retains its original aspect ratio when scaled.

`ih*0.2`: This scales the height of the watermark to 20% of the height of the video. `ih` refers to the input height of the first input (the video).

`[logo][video]`: These are output labels. The scaled watermark is labeled as `logo`, and the unscaled video is labeled as `video`. These labels are used later in the command to refer to these specific streams.

`W-w-10:H-h-10` positions the watermark 10 pixels from the bottom right corner of the video. You can adjust the 10 value to increase or decrease the margin.

`W and H` represent the width and height of the video.
`w` and `h` represent the width and height of the watermark.
