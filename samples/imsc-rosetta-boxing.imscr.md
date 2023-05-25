# Sample file imsc-rosetta-boxing.imscr



This file is a sample which demonstrates the boxing features of imsc-rosetta.

In imsc-rosetta, subtitles can be boxed in a variety of ways:

- unboxed
- solid boxing
- ghost boxing (semi-transparent)
- solid stripe (box which extends to the maximum subtitle area in the writing direction)
- ghost stripe (semi-transparent)

The background color of text can be changed if boxed

*note that file contains ALL imsc-rosetta defined styles as an example - this is not necessary, only the used styles are required*


## Complete file (click expand to see all) [download](./imscr/imsc-rosetta-boxing.imscr)


## Divs with images:



### subtitle 1 at begin=01:00:03.600


Unboxed.  Note that this file has black outline (d_outline) in _d_default.


#### div XML

```
<div xml:id="1" region="R0" begin="01:00:03.600" end="01:00:07.640" style="d_default">
   <p style="p_font2"><span>Unboxed</span><span><br/></span><span>line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3603.6.png" width="600"/>


### subtitle 2 at begin=01:00:07.760


Solid black box.  Note if you look closely, parts of 'y' and 'Á' go outside of the box, and are outlined.

Sometimes used as a channel style.  Other times used to make text readable when on top of a bright or contrasty background.


#### div XML

```
<div xml:id="2" region="R0" begin="01:00:07.760" end="01:00:11.760" style="d_default">
   <p style="p_font2"><span style="ps_bg_boxedblack">Solid Boxed</span><span><br/></span><span style="ps_bg_boxedblack">line 2 descender:y ascender:Á</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3607.76.png" width="600"/>


### subtitle 3 at begin=01:00:11.880


Ghost box

Sometimes used as a channel style.  Other times used to make text readable when on top of a bright or contrasty background.


#### div XML

```
<div xml:id="3" region="R0" begin="01:00:11.880" end="01:00:15.880" style="d_default">
   <p style="p_font2"><span style="ps_bg_ghostboxedblack">Ghost Boxed</span><span><br/></span><span style="ps_bg_ghostboxedblack">line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3611.88.png" width="600"/>


### subtitle 4 at begin=01:00:16.000


Solid Stripe

Generally used to cover existing text more fully that a box around the text only would.


#### div XML

```
<div xml:id="4" region="R0" begin="01:00:16.000" end="01:00:20.000" style="d_default">
   <p style="p_font2 ps_bg_boxedblack"><span>Solid Stripe</span><span><br/></span><span>line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3616.png" width="600"/>


### subtitle 5 at begin=01:00:20.120


Ghost Stripe

Generally used to cover existing text more fully that a box around the text only would.


#### div XML

```
<div xml:id="5" region="R0" begin="01:00:20.120" end="01:00:24.120" style="d_default">
   <p style="p_font2 ps_bg_ghostboxedblack"><span>Ghost Stripe</span><span><br/></span><span>line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3620.12.png" width="600"/>


### subtitle 6 at begin=01:00:24.240


Unboxed but demonstrating 'background' color change on outlined text.

Retention of background colour may be important if the file is to be exported to teletext.


#### div XML

```
<div xml:id="6" region="R0" begin="01:00:24.240" end="01:00:28.240" style="d_default">
   <p style="p_font2"><span>Unboxed change to </span><span style="s_outlinered">red </span><span>then </span><span style="s_outlineblue">blue</span><span><br/></span><span>line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3624.24.png" width="600"/>


### subtitle 7 at begin=01:00:28.360


Solid box demonstrating change of background color.

Note that black outline is retained.  Comments?


#### div XML

```
<div xml:id="7" region="R0" begin="01:00:28.360" end="01:00:32.360" style="d_default">
   <p style="p_font2"><span style="ps_bg_boxedblack">Solid boxed change to </span><span style="ps_bg_boxedred">red </span><span style="ps_bg_boxedblack">then </span><span style="ps_bg_boxedblue">blue</span><span><br/></span><span style="ps_bg_boxedblack">line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3628.36.png" width="600"/>


### subtitle 8 at begin=01:00:32.480


Ghost box demonstrating change of background color.

Note that black outline is retained.  Comments?


#### div XML

```
<div xml:id="8" region="R0" begin="01:00:32.480" end="01:00:36.480" style="d_default">
   <p style="p_font2"><span style="ps_bg_ghostboxedblack">Ghost boxed change to </span><span style="ps_bg_ghostboxedred">red </span><span style="ps_bg_ghostboxedblack">then </span><span style="ps_bg_ghostboxedblue">blue</span><span><br/></span><span style="ps_bg_ghostboxedblack">line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3632.48.png" width="600"/>


### subtitle 9 at begin=01:00:36.640


Solid Stripe demonstrating change of background color.

Note that black outline is retained.  Comments?


#### div XML

```
<div xml:id="9" region="R0" begin="01:00:36.640" end="01:00:40.640" style="d_default">
   <p style="p_font2 ps_bg_boxedblack"><span>Solid Stripe change to </span><span style="ps_bg_boxedred">red </span><span>then </span><span style="ps_bg_boxedblue">blue</span><span><br/></span><span>line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3636.64.png" width="600"/>


### subtitle 10 at begin=01:00:40.760


Ghost Stripe demonstrating change of background color.

Note how the changed background color spans have double the opacity of the black.

This is unavoidable because of the way boxing on `<p>` and `<span>` work in TTML.

Note that black outline is retained.  Comments?


#### div XML

```
<div xml:id="10" region="R0" begin="01:00:40.760" end="01:00:44.760" style="d_default">
   <p style="p_font2 ps_bg_ghostboxedblack"><span>Ghost Stripe change to </span><span style="ps_bg_ghostboxedred">red </span><span>then </span><span style="ps_bg_ghostboxedblue">blue</span><span><br/></span><span>line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3640.76.png" width="600"/>


### subtitle 11 at begin=01:00:45.760


Solid black box with d_fillgap specified on `<div>`.


#### div XML

```
<div xml:id="11" region="R0" begin="01:00:45.760" end="01:00:48.760" style="d_default d_fillgap">
   <p style="p_font2"><span style="ps_bg_boxedblack">Solid Boxed - fillgap</span><span><br/></span><span style="ps_bg_boxedblack">line 2 descender:y ascender:Á</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3645.76.png" width="600"/>


### subtitle 12 at begin=01:00:49.880


Ghost box with d_fillgap specified on `<div>`, but with a blank line in between the lines.

***The result is probably not desirable.***



#### div XML

```
<div xml:id="12" region="R0" begin="01:00:49.880" end="01:00:54.880" style="d_default d_fillgap">
   <p style="p_font2"><span style="ps_bg_ghostboxedblack">Ghost Boxed - fillgap</span><span><br/></span><span><br/></span><span style="ps_bg_ghostboxedblack">line 2</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-boxing.imscr/3649.88.png" width="600"/>


