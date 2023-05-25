# Sample file imsc-rosetta-alignment.imscr



This file is a sample which demonstrates the alignment features of imsc-rosetta.

imsc-rosetta has 9 alignment style names which can be applied to `<p>`:

- p_al_start
- p_al_end
- p_al_center
- p_al_start_center
- p_al_start_end
- p_al_end_start
- p_al_end_center
- p_al_center_start
- p_al_center_end

*note: there are no styles p_al_start_start, p_al_center_center, p_al_end_end - use p_al_start, p_al_center, and p_al_end*

Vertical placement (in horizontal subtitling) is determined by region edge placement.

The region edge against which the subtitle rests is placed according to the quantisation calculated from the extent, fontSize and lineHeight specified in `_r_quantisationregion`.

For this file, the region edge position is based on 12 row positions, determined by

row height = 5.333/100 x 125/100 = 6.666/100 or 6.666% of screen height

subtitle vertical area = 80/100

position count = subtitle vertical area/row height = 0.8/0.06666 = ~12

Therefore region edges are quantised to n * 80%/12

*note that file contains ALL imsc-rosetta defined styles as an example - this is not necessary, only the used styles are required except for _r_quantisationregion which must always be included*


## Complete file (click expand to see all) [download](./imscr/imsc-rosetta-alignment.imscr)


## Divs with images:



### subtitle 1 at begin=01:00:07.760


This div represents a single line centered at the bottom of the screen.  Note the absence of a p_al_ style - here we are using the default position which is fixed as center in imsc-rosetta.


#### div XML

```
<div xml:id="1" region="R0" begin="01:00:07.760" end="01:00:11.760" style="d_default">
   <p style="p_font2"><span>1 line Center Bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3607.76.png" width="600"/>


### subtitle 2 at begin=01:00:11.880


This div represents a single line on the left using p_al_start in left to right text.


#### div XML

```
<div xml:id="2" region="R0" begin="01:00:11.880" end="01:00:15.880" style="d_default">
   <p style="p_font2 p_al_start"><span>1 line start bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3611.88.png" width="600"/>


### subtitle 3 at begin=01:00:16.000


This div represents a single line on the right using p_al_end in left to right text.


#### div XML

```
<div xml:id="3" region="R0" begin="01:00:16.000" end="01:00:20.000" style="d_default">
   <p style="p_font2 p_al_end"><span>1 line end bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3616.png" width="600"/>


### subtitle 4 at begin=01:00:20.120


This div represents two lines centered at the bottom.  Note the absence of a p_al_ style - here we are using the default position which is fixed as center in imsc-rosetta.


#### div XML

```
<div xml:id="4" region="R0" begin="01:00:20.120" end="01:00:24.120" style="d_default">
   <p style="p_font2"><span>two lines</span><span><br/></span><span>center bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3620.12.png" width="600"/>


### subtitle 5 at begin=01:00:24.240


This div represents two lines on the left bottom using p_al_start in left to right text.


#### div XML

```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="d_default">
   <p style="p_font2 p_al_start"><span>two lines</span><span><br/></span><span>start bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3624.24.png" width="600"/>


### subtitle 6 at begin=01:00:28.360


This div represents two lines on the right bottom using p_al_end in left to right text.


#### div XML

```
<div xml:id="6" region="R0" begin="01:00:28.360" end="01:00:32.360" style="d_default">
   <p style="p_font2 p_al_end"><span>two lines</span><span><br/></span><span>end bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3628.36.png" width="600"/>


### subtitle 7 at begin=01:00:32.480


This div represents two lines, where the longest line is centered, and the shorter line left aligned to the longer line (commonly know as center left align) using p_al_center_start in left to right text.


#### div XML

```
<div xml:id="7" region="R0" begin="01:00:32.480" end="01:00:36.480" style="d_default">
   <p style="p_font2 p_al_center_start"><span>two lines</span><span><br/></span><span>center start bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3632.48.png" width="600"/>


### subtitle 8 at begin=01:00:36.640


This div represents two lines, where the longest line is centered, and the shorter line right aligned to the longer line (uncommon) using p_al_center_end in left to right text.


#### div XML

```
<div xml:id="8" region="R0" begin="01:00:36.640" end="01:00:40.640" style="d_default">
   <p style="p_font2 p_al_center_end"><span>two lines</span><span><br/></span><span>center end bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3636.64.png" width="600"/>


### subtitle 9 at begin=01:00:40.760


This div represents two lines, where the longest line is left aligned, and the shorter line center aligned relative to longer line (uncommon) using p_al_start_center in left to right text.


#### div XML

```
<div xml:id="9" region="R0" begin="01:00:40.760" end="01:00:44.760" style="d_default">
   <p style="p_font2 p_al_start_center"><span>two lines</span><span><br/></span><span>start center bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3640.76.png" width="600"/>


### subtitle 10 at begin=01:00:44.880


This div represents two lines, where the longest line is left aligned, and the shorter line right aligned relative to longer line (uncommon) using p_al_start_end in left to right text.


#### div XML

```
<div xml:id="10" region="R0" begin="01:00:44.880" end="01:00:48.880" style="d_default">
   <p style="p_font2 p_al_start_end"><span>two lines</span><span><br/></span><span>start end bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3644.88.png" width="600"/>


### subtitle 11 at begin=01:00:49.000


This div represents two lines, where the longest line is right aligned, and the shorter line left aligned relative to longer line (uncommon) using p_al_end_start in left to right text.


#### div XML

```
<div xml:id="11" region="R0" begin="01:00:49.000" end="01:00:53.000" style="d_default">
   <p style="p_font2 p_al_end_start"><span>two lines</span><span><br/></span><span>end start bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3649.png" width="600"/>


### subtitle 12 at begin=01:00:53.120


This div represents two lines, where the longest line is right aligned, and the shorter line center aligned relative to longer line (uncommon) using p_al_end_center in left to right text.


#### div XML

```
<div xml:id="12" region="R0" begin="01:00:53.120" end="01:00:57.120" style="d_default">
   <p style="p_font2 p_al_end_center"><span>two lines</span><span><br/></span><span>end center bottom</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3653.12.png" width="600"/>


### subtitle 13 at begin=01:00:57.240


This div represents three lines, where the first is left aligned, the second is centered, and the third is right aligned.  This uses three separate `<p>` elements, marked with p_al_start, p_al_center_ and p_al_end respectively.


#### div XML

```
<div xml:id="13" region="R0" begin="01:00:57.240" end="01:01:01.240" style="d_default">
   <p style="p_font2 p_al_start"><span>left</span></p>
   <p style="p_font2"><span>center</span></p>
   <p style="p_font2 p_al_end"><span>right</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3657.24.png" width="600"/>


### subtitle 14 at begin=01:01:01.360


Subtitles 14-22 demonstrate vertical positioning using regions.




#### div XML

```
<div xml:id="14" region="R1" begin="01:01:01.360" end="01:01:05.360" style="d_default">
   <p style="p_font2"><span>row 11/12 (about one line from bottom)</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3661.36.png" width="600"/>


### subtitle 15 at begin=01:01:05.480

#### div XML

```
<div xml:id="15" region="R11" begin="01:01:05.480" end="01:01:09.480" style="d_default">
   <p style="p_font2"><span>row 1/12 (top)</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3665.48.png" width="600"/>


### subtitle 16 at begin=01:01:09.640

#### div XML

```
<div xml:id="16" region="R9" begin="01:01:09.640" end="01:01:13.640" style="d_default">
   <p style="p_font2"><span>row 3/12</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3669.64.png" width="600"/>


### subtitle 17 at begin=01:01:13.760

#### div XML

```
<div xml:id="17" region="R10" begin="01:01:13.760" end="01:01:17.760" style="d_default">
   <p style="p_font2"><span>row 2/12</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3673.76.png" width="600"/>


### subtitle 18 at begin=01:01:17.880

#### div XML

```
<div xml:id="18" region="R11" begin="01:01:17.880" end="01:01:21.880" style="d_default">
   <p style="p_font2"><span>row 1/12</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3677.88.png" width="600"/>


### subtitle 19 at begin=01:01:22.000

#### div XML

```
<div xml:id="19" region="R11" begin="01:01:22.000" end="01:01:26.000" style="d_default">
   <p style="p_font2"><span>top center</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3682.png" width="600"/>


### subtitle 20 at begin=01:01:26.120

#### div XML

```
<div xml:id="20" region="R11" begin="01:01:26.120" end="01:01:30.120" style="d_default">
   <p style="p_font2 p_al_start"><span>top left</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3686.12.png" width="600"/>


### subtitle 21 at begin=01:01:30.240

#### div XML

```
<div xml:id="21" region="R11" begin="01:01:30.240" end="01:01:34.240" style="d_default">
   <p style="p_font2 p_al_end"><span>top right</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3690.24.png" width="600"/>


### subtitle 22 at begin=01:01:34.360

#### div XML

```
<div xml:id="22" region="R11" begin="01:01:34.360" end="01:01:38.360" style="d_default">
   <p style="p_font2 p_al_start"><span>top left</span></p>
   <p style="p_font2"><span>center</span></p>
   <p style="p_font2 p_al_end"><span>right</span></p>
  </div>
```
#### Resulting Image

<img src="./images/imsc-rosetta-alignment.imscr/3694.36.png" width="600"/>


