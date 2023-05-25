# Sample file bad_prettydiv.imscr



This file is prettified by a 'standard' XML output. Although on the face of it, it looks like a valid XML file, it is not a valid IMSC-Rosetta file.

IMSC-Rosetta uses xml:space="preserve" to ensure that dcertain asepects of the subtitles are rendered correctly (e.g. multiple spaces are represented as multiple spaces, and very specifically, change of background colour between spans always works.)

Because we need xml:space="preserve", the indentation spaces and carriage returns inside `<p>` are rendered by the player, and severely disturb the rendering, leading to imncorrect images.  See below.

Please do NOT prettify within a `<p>` element.  TTML does not care it your prettify anything else in the file - but `<p>` must effectively be on one line.

If you run the file through [imsc-rosetta-qualify](https://imsc-rosetta.github.io/imsc-rosetta-qualify/), it will report errors, but also you will find a corrected version in `XML round trip from Simple Parse JSON`, which if run through again is error free.


## Complete file (click expand to see all) [download](./imscr/bad_prettydiv.imscr)


## Divs with images:



### subtitle sub0 at begin=01:00:03.600

#### div XML

```
<div xml:id="sub0" region="R0" begin="01:00:03.600" end="01:00:07.640" style="d_default d_outline">
   <metadata rosetta:comment="this is a comment test a cr"/>
   <p style="p_font2">
    <span style="ps_bg_boxedblack">First Frame of active video</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3603.6.png" width="600"/>


### subtitle 1 at begin=01:00:07.760

This subtitle should be all on one line at the bottom, but has been split into multiple lines and raised by the player rendering the carriage returns.


#### div XML

```
<div xml:id="1" region="R0" begin="01:00:07.760" end="01:00:11.760" style="d_default">
   <p style="p_font2">
    <span>1 line</span>
    <span style="s_nonered"> Center</span>
    <span> Bottom</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3607.76.png" width="600"/>


### subtitle 2 at begin=01:00:11.880

#### div XML

```
<div xml:id="2" region="R0" begin="01:00:11.880" end="01:00:15.880" style="d_default">
   <p style="p_font2 p_al_start">
    <span>1 line left  bottom</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3611.88.png" width="600"/>


### subtitle 3 at begin=01:00:16.000

#### div XML

```
<div xml:id="3" region="R0" begin="01:00:16.000" end="01:00:20.000" style="d_default">
   <p style="p_font2 p_al_end">
    <span>1 line right bottom</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3616.png" width="600"/>


### subtitle 4 at begin=01:00:20.120

The two `<p>` of this subtitle are intended to be adjacent, and not raised.


#### div XML

```
<div xml:id="4" region="R0" begin="01:00:20.120" end="01:00:24.120" style="d_default">
   <p style="p_font2">
    <span>two line </span>
   </p>
   <p style="p_font2">
    <span>center bottom</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3620.12.png" width="600"/>


### subtitle 5 at begin=01:00:24.240

#### div XML

```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="d_default">
   <p style="p_font2">
    <span>two lines</span>
   </p>
   <p style="p_font2">
    <span>left bottom</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3624.24.png" width="600"/>


### subtitle 6 at begin=01:00:28.360

#### div XML

```
<div xml:id="6" region="R0" begin="01:00:28.360" end="01:00:32.360" style="d_default">
   <p style="p_font2">
    <span>two lines</span>
   </p>
   <p style="p_font2">
    <span>right bottom</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3628.36.png" width="600"/>


### subtitle 7 at begin=01:00:32.480

#### div XML

```
<div xml:id="7" region="R0" begin="01:00:32.480" end="01:00:36.480" style="d_default">
   <p style="p_font2">
    <span>row 11</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3632.48.png" width="600"/>


### subtitle 8 at begin=01:00:36.640

#### div XML

```
<div xml:id="8" region="R1" begin="01:00:36.640" end="01:00:40.640" style="d_default">
   <p style="p_font2">
    <span>row 10</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3636.64.png" width="600"/>


### subtitle 9 at begin=01:00:40.760

#### div XML

```
<div xml:id="9" region="R2" begin="01:00:40.760" end="01:00:44.760" style="d_default">
   <p style="p_font2">
    <span>row 9</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3640.76.png" width="600"/>


### subtitle 10 at begin=01:00:44.880

#### div XML

```
<div xml:id="10" region="R3" begin="01:00:44.880" end="01:00:48.880" style="d_default">
   <p style="p_font2">
    <span>row 8</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3644.88.png" width="600"/>


### subtitle 11 at begin=01:00:49.000

#### div XML

```
<div xml:id="11" region="R4" begin="01:00:49.000" end="01:00:53.000" style="d_default">
   <p style="p_font2">
    <span>row 7</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3649.png" width="600"/>


### subtitle 12 at begin=01:00:53.120

#### div XML

```
<div xml:id="12" region="R5" begin="01:00:53.120" end="01:00:57.120" style="d_default">
   <p style="p_font2">
    <span>row 6</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3653.12.png" width="600"/>


### subtitle 13 at begin=01:00:57.240

#### div XML

```
<div xml:id="13" region="R6" begin="01:00:57.240" end="01:01:01.240" style="d_default">
   <p style="p_font2">
    <span>row 5</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3657.24.png" width="600"/>


### subtitle 14 at begin=01:01:01.360

#### div XML

```
<div xml:id="14" region="R7" begin="01:01:01.360" end="01:01:05.360" style="d_default">
   <p style="p_font2">
    <span>row 4</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3661.36.png" width="600"/>


### subtitle 15 at begin=01:01:05.480

#### div XML

```
<div xml:id="15" region="R8" begin="01:01:05.480" end="01:01:09.480" style="d_default">
   <p style="p_font2">
    <span>row 3</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3665.48.png" width="600"/>


### subtitle 16 at begin=01:01:09.640

#### div XML

```
<div xml:id="16" region="R9" begin="01:01:09.640" end="01:01:13.640" style="d_default">
   <p style="p_font2">
    <span>row 2</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3669.64.png" width="600"/>


### subtitle 17 at begin=01:01:13.760

#### div XML

```
<div xml:id="17" region="R10" begin="01:01:13.760" end="01:01:17.760" style="d_default">
   <p style="p_font2">
    <span>row 1</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3673.76.png" width="600"/>


### subtitle 18 at begin=01:01:17.880

#### div XML

```
<div xml:id="18" region="R11" begin="01:01:17.880" end="01:01:21.880" style="d_default">
   <p style="p_font2">
    <span>row 0</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3677.88.png" width="600"/>


### subtitle 19 at begin=01:01:22.000

#### div XML

```
<div xml:id="19" region="R11" begin="01:01:22.000" end="01:01:26.000" style="d_default">
   <p style="p_font2">
    <span>top center</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3682.png" width="600"/>


### subtitle 20 at begin=01:01:26.120

#### div XML

```
<div xml:id="20" region="R11" begin="01:01:26.120" end="01:01:30.120" style="d_default">
   <p style="p_font2 p_al_start">
    <span>top left</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3686.12.png" width="600"/>


### subtitle 21 at begin=01:01:30.240

#### div XML

```
<div xml:id="21" region="R11" begin="01:01:30.240" end="01:01:34.240" style="d_default">
   <p style="p_font2 p_al_end">
    <span>top right</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3690.24.png" width="600"/>


### subtitle 22 at begin=01:01:34.360

#### div XML

```
<div xml:id="22" region="R0" begin="01:01:34.360" end="01:01:38.360" style="d_default">
   <p style="p_al_start p_font2">
    <span>left</span>
   </p>
   <p style="p_font2">
    <span>center</span>
   </p>
   <p style="p_al_end p_font2">
    <span>right</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3694.36.png" width="600"/>


### subtitle 23 at begin=01:01:38.520

#### div XML

```
<div xml:id="23" region="R0" begin="01:01:38.520" end="01:01:42.520" style="d_default">
   <p style="p_font2">
    <span>normal</span>
    <span style="s_italic"> italic</span>
    <span style="s_bold"> bold </span>
    <span style="s_underline">underline</span>
    <span> normal</span>
   </p>
   <p style="p_font2">
    <span style="s_underline">underlined</span>
    <span style="s_italic s_underline"> italic</span>
    <span style="s_bold s_underline"> bold</span>
    <span style="s_underline"> normal</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3698.52.png" width="600"/>


### subtitle 24 at begin=01:01:42.640

#### div XML

```
<div xml:id="24" region="R0" begin="01:01:42.640" end="01:01:46.640" style="d_default">
   <p style="p_font2">
    <span style="s_fg_red">red </span>
    <span style="s_fg_yellow">yellow </span>
    <span style="s_fg_green">green </span>
    <span style="s_fg_cyan">cyan </span>
    <span style="s_fg_blue">blue </span>
    <span style="s_fg_magenta">magenta</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3702.64.png" width="600"/>


### subtitle 25 at begin=01:01:46.760

#### div XML

```
<div xml:id="25" region="R11" begin="01:01:46.760" end="01:01:50.760" style="d_default">
   <p style="p_font2">
    <span>Two lines </span>
   </p>
   <p style="p_font2">
    <span>top center</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3706.76.png" width="600"/>


### subtitle 26 at begin=01:01:50.880

This subtitle illustrates the rendering if carriage returns by the player, and how the subtitle is raised by the trailing CR after the last span.

#### div XML

```
<div xml:id="26" region="R0" begin="01:01:50.880" end="01:01:53.880" style="d_default">
   <p style="p_font2 ps_bg_boxedblack">
    <span style="s_noneblack">Background stripe</span>
   </p>
   <p style="p_font2 ps_bg_boxedblack">
    <span style="s_noneblack">black</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3710.88.png" width="600"/>


### subtitle 27 at begin=01:01:54.000

#### div XML

```
<div xml:id="27" region="R0" begin="01:01:54.000" end="01:01:57.000" style="d_default">
   <p style="p_font2">
    <span style="ps_bg_boxedblack">black</span>
   </p>
   <p style="p_font2">
    <span style="ps_bg_boxedblack">box</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3714.png" width="600"/>


### subtitle 28 at begin=01:01:57.120

#### div XML

```
<div xml:id="28" region="R0" begin="01:01:57.120" end="01:02:00.120" style="d_default">
   <p style="p_font2">
    <span style="ps_bg_ghostboxedblack">ghost</span>
   </p>
   <p style="p_font2">
    <span style="ps_bg_ghostboxedblack">box</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3717.12.png" width="600"/>


### subtitle 29 at begin=01:02:00.240

#### div XML

```
<div xml:id="29" region="R0" begin="01:02:00.240" end="01:02:03.240" style="d_default">
   <p style="p_font2 ps_bg_ghostboxedblack">
    <span style="s_noneblack">Ghost stripe</span>
   </p>
   <p style="p_font2 ps_bg_ghostboxedblack">
    <span style="s_noneblack">black</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3720.24.png" width="600"/>


### subtitle 30 at begin=01:02:03.359

#### div XML

```
<div xml:id="30" region="R0" begin="01:02:03.359" end="01:02:06.359" style="d_default">
   <p style="p_font2">
    <span style="ps_bg_ghostboxedblack s_noneblack">Ghost box change to </span>
    <span style="ps_bg_ghostboxedred s_nonered">red</span>
   </p>
  </div>
```
#### Resulting Image

<img src="./images/bad_prettydiv.imscr/3723.359.png" width="600"/>


