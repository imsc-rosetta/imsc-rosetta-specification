# right to left language use.

## style p_rtl

add style p_rtl to each p which contains right to left language (e.g. arabic, hebrew, etc.)

***Do not use embedded direction control characters, e.g.:***

```
RLM	RIGHT-TO-LEFT MARK	U+200F	none	strongly typed RTL character
LRM	LEFT-TO-RIGHT MARK	U+200E	none	strongly typed LTR character
PDF	POP DIRECTIONAL FORMATTING	U+202C	
PDI	POP DIRECTIONAL ISOLATE	U+2069
LRI	LEFT-TO-RIGHT ISOLATE	U+2066	dir = "ltr"	sets base direction to LTR and isolates the embedded content from the surrounding text
RLI	RIGHT-TO-LEFT ISOLATE	U+2067	dir = "rtl"	ditto, but for RTL
FSI	FIRST-STRONG ISOLATE	U+2068	dir = "auto"	isolates the content and sets the direction according to the first strongly typed directional character
LRE	LEFT-TO-RIGHT EMBEDDING	U+202A	dir = "ltr"	sets base direction to LTR but allows embedded text to interact with surrounding content, so risk of spillover effects
RLE	RIGHT-TO-LEFT EMBEDDING	U+202B	dir = "rtl"	ditto, but for RTL
LRO	LEFT-TO-RIGHT OVERRIDE	U+202D	<bdo dir = "ltr">	overrides the bidirectional algorithm to display characters in memory order, progressing from left to right
RLO	RIGHT-TO-LEFT OVERRIDE	U+202E	<bdo dir = "rtl">	as previous, but display progresses from right to left
```

***Do not use the above characters***

## technical notes

titles will obey 'normal' bidi rules.

spans within p will be presented right to left on individual lines.

If a title needs to represent one line of right-to-left, and one line of left-to-right, use two `<p>` inside the `<div>`.

## example

```
  <div xml:id="42" region="R0" begin="01:02:50.120" end="01:02:54.120" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack p_rtl"><span style="ps_bg_ghostboxedblack">abc אותיות </span><span style="ps_bg_ghostboxedblack ds_fg_red">bcd השימו 1983 ש</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span></p>
  </div>
```