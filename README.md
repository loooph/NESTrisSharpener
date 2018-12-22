# NESTrisSharpener
A simple OBS shader for upscaling graphics.

1) Download and install this plugin:
* Download: https://github.com/nleseul/obs-shaderfilter/releases
* Install: read this - https://github.com/nleseul/obs-shaderfilter/

2) Add your video source (i.e. NES Tetris composite AV signal)
3) Add filter... (right click on video source, hit "filter")
4) Add a new "User-defined shader"
5) Shader Text file -> Browse -> Nestris.shader
6) block_image  -> Browse -> blocks.png

# Calibration
Now, we will quickly calibrate the image
* First, make sure your video source is only game image, with no borders. If it isn't aligned properly, try to add a crop/pad filter before this in the chain, so that it lines up.
* Next, we have to set all the appropriate values. Below are descriptions of sections and some default values that work well.

![image](https://github.com/alex-ong/NESTrisSharpener/raw/master/calibration.png)
# setup_mode
tick this to set calibration up. when you are done, untick it.

# Field
This section defines where your field is. Values range from 0 to 256. You can use half-pixels.

| Name           | default value | 
| -------------  |---------------|
| field_left_x   | 97            |
| field_right_x  | 176           |
| field_top_y    | 39            |
| field_bottom_y | 200           |

# stat_palette white, stat_palette
Enabling stat_palette_white means white blocks with coloured borders get their color from the statistics bar on the left.
This results in uniform looking white blocks.
stat_palette is the same thing, but for fully coloured blocks.

| Name                 | default value    | 
| -------------        |---------------   |
| stat_palette_white   | true (ticked)    |
| stat_palette         | false (unticked) |

# paletteA1, paletteA2, paletteB1, paletteB2
If you have stat_palette_white or stat_palette enabled, you can set the locations of some reference blocks in the image.

| Name           | default value | 
| -------------  |---------------|
| paletteA_x1    | 30            |
| paletteA_y1    | 103           |
| paletteA_x2    | 30            |
| paletteA_y2    | 158           |

| Name           | default value | 
| -------------  |---------------|
| paletteB_x1    | 30            |
| paletteB_y1    | 120           |
| paletteB_x2    | 30            |
| paletteB_y2    | 167           |

# game / menu detection
skip_detect_game - if you tick this, we will always be in game mode. if it is un-ticked, we check for menus.
skip_detect_game_over - if you tick this, we will always be in game mode. if it is un-ticked, we check for game-overs.

| Name                  | default value   | 
| -------------         |-----------------|
| skip_detect_game      | false (unticked)|
| skip_detect_game_over | false (unticked)|

The next settings are the locations of a few squares that we use to figure out if we are in game mode:

| Name                  | default value   | 
| -------------         |-----------------|
| game_black_x1         | 98|
| game_black_y1         | 19|
| game_black_x2         | 238|
| game_black_y2         | 16|
| game_grey_x1          | 13|
| game_grey_y1          | 219|

If we detect black in both locations specified as well as grey in the bottom left corner, we assume that we aren't in a menu.


