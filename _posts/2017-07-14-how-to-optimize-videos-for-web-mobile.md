---
layout:    post
title:     "How to optimize videos for web mobile"
date:      2017-07-14 00:51:00
permalink: "/how-to-optimize-videos-for-web-mobile"
---

I know. It's trendy. If you find yourself having a ginormous video and a request from design asking to be a full-bleed background video on a hero of the page, this will likely be useful for you. I do recommend hosting the video in any platform that does the processing of the video and re-rendering multiple qualities to automatically provide users with the best they can consume, as YouTube does. But for those of you who will self-host videos, this will be probably the way to go.

There are a few key concepts that are important and that helped me figure the video file size out:

* [Bitrate](http://www.ezs3.com/public/What_bitrate_should_I_use_when_encoding_my_video_How_do_I_optimize_my_video_for_the_web.cfm) (quality of each frame:) think about JPEGs, if it's 10kb or 100kb you can assume the bigger means less compression / better image quality. Lowering the bitrate you can save on size and lose on quality.
* Frames per second
* Length of video
* Video resolution

Losing on quality doesn't necessarily mean that it will look bad. We can hide the artifacts (those pixelated square portions of the frames) by applying a [pattern overlay](http://output.jsbin.com/lutojeg) on top.

Now we're ready to do some real optimizations. The library [FFmpeg](https://ffmpeg.org/) allows you to do a lot of transformations, and it has cross-platform support. The following are the settings I've used:

```
ffmpeg -ss 00:00:00 -t 00:00:10 -i original.mp4 -movflags faststart -vcodec libx264 -an -b:v XXXXX cut.mp4
```

1. `-ss hh:mm:ss` is where to start from (trimmming the video)
2. `-t hh:mm:ss` is how long the desired output video would be
3. `-i filename.ext` is the original file (won't be modified)
4. `-movflags faststart` is to move the movie meta data to the beginning, so we enable streaming (if your server supports it)
5. `-vcoded libx264` to output H.264 a.k.a. mp4 video
6. `-an` to remove audio
7. `-b:v XXXXX` to specify the video bitrate

I recommend the settings I've used to **optimize the bitrate**, where `XXXXX` was `1200000` for Desktop on a Full HD video (1920x1080) and `600000` for Mobile devices. I also cropped the last one to be a portrait mode video, since almost nobody (sorry Jason!) uses their phone in landscape mode. The 10 second video trim is just to make the final file smaller and it worked for my use case.

Video cropping can be done by adding the parameter `-filter:v "crop=W:H:X:Y"` to the command above and replacing `W` for the desired output width and `H` for the height respectively, and `X` and `Y` are the coordinates of the original video from where to start the cropping (top left corner.)

For example you may want to have a 600x1080 video for mobile when the original was 1920x1080. The parameters then would be `width=600, height=1080, x=(1920-600)/2, y=0` if you want the center piece. that means adding `-filter:v "crop=600:1080:660:0`.

You should also take into consideration not having more than 20-30fps as web won't need it. And all this is assuming 2 versions (mobile and desktop) but you can create even more versions of different qualities and sizes to provide the user with the best quality for their use case.

I hope you find this useful.

<small>The inspiration for this post was [sitepoint](https://www.sitepoint.com/10-guidelines-better-website-background-videos/) and the fact that nobody told me what bitrate to use.</small>

