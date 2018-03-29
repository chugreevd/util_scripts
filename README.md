Here I will be collecting useful command line utils

# ffmpeg recipes

#### Frames to video

Create video with 30 frames/second, 390 frames in total from files with mask

```ffmpeg -r 30 -i image-%07d.png -c:v libx264 -vframes 390 -vf fps=30 -pix_fmt yuv420p out.mp4```

Same but specify target resolution

```ffmpeg -r 30 -i image-%07d.png -c:v libx264 -vframes 390 -vf fps=30 -pix_fmt yuv420p -s 960x540 out.mp4```

Same but glob-based input mask

```ffmpeg -r 30 -pattern_type glob -i frames/img-*.png -c:v libx264 -vframes 390 -vf fps=30 -pix_fmt yuv420p -s 960x540 out.mp4```

#### Video to frames

Export to pngs with rate of 4.5 per second

```ffmpeg -i IMG_2765.MOV -r 4.5 -f image2 images/image-%07d.png```

Same but specify starting and end time (in seconds)

```ffmpeg -i IMG_2765.MOV -r 4.5 -ss 74 -to 96 -f image2 images/image-%07d.png```

#### Video to video

Fast split video into videos

```ffmpeg -i vid14-mac.mp4 -c copy -map 0 -segment_time 7200 -f segment chunks_2/output%03d.mp4```