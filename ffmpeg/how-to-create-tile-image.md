# How to create tile image

[Ffmpeg](https://ffmpeg.org) can be used to create a tile image containing multiple frames from a video file. Here's how to do it!

Run the following command:

```
ffmpeg -i <video> -frames 1 -vf "select=not(mod(n\,<nth_frame>)),scale=<t_width>,<t_height>,tile=<n_col>x<n_rows>" <output_file>
```

Where:
* _video_ is the path to the video file
* _nth\_frame_ specifies the frame capture frequency. For example, if _nth\_frame_=300 then every 300th frame is captured.
* _t\_width_ tile width
* _t\_height_ tile height
* _n\_col_ number of columns in the tile file
* _n\_rows_ number of rows in the tile file
* _output\_file_ name of the tile image

## Example

Given the following video

[!video](video.mp4)

and the following command

```
ffmpeg -i video.mp4 -frames 1 -vf "select=not(mod(n\,300)),scale=224:126,tile=5x6" tile.png
```

It will produce a `tile.png` image capturing every 300th frame. It contains at maximum 35 tiles (5x7) where each tile has a size of 320x200px.

[!tile image](tile.png)
