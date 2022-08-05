# Document Structure

The file must start with the XML header containing the following attributes

xml version="1.0"

encoding="UTF-8"

standalone="yes"

## Allowed elements

### `<tt>`
`<tt>` contains only the specified attributes. `<tt>` contains the following elements:

Exactly one `<head>` followed by exactly one `<body>`.

#### tt must conform to ‘normal’ namespacing conventions. I.e. we will not insist on specific namespace prefixes, but suggest the below example where the default namespace is "http://www.w3.org/ns/ttml", and other used namespaces are prefixed with commonly used prefixes, only to foster familiarity for instance 

"http://www.w3.org/ns/ttml#metadata"

"http://www.w3.org/ns/ttml#styling"

"http://www.w3.org/ns/ttml#parameter"

"http://www.w3.org/XML/1998/namespace"

"urn:ebu:tt:style"

"http://www.w3.org/ns/ttml/profile/imsc1#styling"

"https://github.com/imsc-rosetta/specification"

#### Note IMSC only allows for ttp:timeBase="media"

#### The Cell Resolution must be expliclity delcared ttp:cellResolution="30 15"

#### The space must be xml:space="preserve"

#### The frame rate must be set for instance, 23.98, 25 or 29.997 eg ttp:frameRate="25"

#### The frame rate multiplier shall  be set eg ttp:frameRateMultiplier="1 1"

#### The use of language codes is dependant on the broadcaster and could include bcp47 or ISO-639 or propriatary the actual code should be specified in xml:lang="en-US">
 <head>

### `<head>`
`<head>` must have no attributes. `<head>` contains the following elements:

Exactly one `<metadata>` followed by exactly one `<styling>` followed by exactly one `<layout>`.

### `<metadata>` - as used in `<head>`
`<metadata>` must have no attributes. `<metadata>` must contain the following elements:

`<rosetta:format>rosetta-imsc</rosetta:format>`

`<rosetta:version>0.0.0</rosetta:version>`


`<metadata>` may contain other optional metadata elements.  (See metadata document)

The order of elements in `<metadata>` must not be important.

### `<styling>`
`<styling>` must have no attributes. `<styling>` contains the following elements:

one or more `<style>` elements only.

### `<style>`
`<style>` elements must be represented exactly as found in the style specification.

`<style>` elements will not have any content, and should be represented as closed elements, e.g. `<style xml:id="s_red" tts:color="#FF0000"/>`

### `<layout>`
`<layout>` must have no attributes. `<layout>` contains the following elements:

one or more `<region>` elements only.

### `<region>`
`<region>` elements must contain the following attributes:

`xml:id` `tts:origin` `tts:extent` `tts:displayAlign` `style="r_region"`

For Japanese Vertical text, the additional style r_vertical will be added.  i.e. the region will contain `style="r_region r_vertical"`

`<region>` elements will not have any content, and should be represented as closed elements, 

e.g. 

`<region xml:id="R0" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" style="r_region"/>`

e.g. Japanese vertical region:

`<region xml:id="R0" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" style="r_region r_vertical"/>`

### `<body>`
`<body>` must have no attributes. `<body>` contains the following elements:

One or more `<div>`.

### `<div>`
`<div>` elements must contain the following attributes:

`xml:id` `region` `begin` `end` `style`

`<div>` contains the following elements:

Zero or more `<metadata rosetta:comment="comment text">`.

Zero or more `<p>` elements.

The order of `<metadata rosetta:comment="comment text"/>` vs `<p>` is not important.

### `<metadata>` - as used in `<div>`
`<metadata>` used in `<div>` must have one attribute `rosetta:comment` used to carry comment text along with the subtitle.

`<metadata>` used in `<div>` must have no content, and be closed.  e.g. `<metadata rosetta:comment="comment text"/>`

### `<p>`
`<p>` elements must contain the attribute `style` only:

`style`

The `style` attribute on `<p>` must contain either `p_font1` or `p_font2`.  The `style` attribute may contain additional styles relevant to `<p>`

`<p>` contains the following elements:

Zero or more `<span>` elements

`<p>` will NOT include and text directly - ***all text must be wrapped in `<span>`***

A `<p>` element may contain multiple lines by use of `<span><br/></span>`, but in this case all lines will have the same alignment, and the use of multiRowAlign is allowed.

Where a subtitle requires a line(s) to be aligned start, and other line(s) center or end, multiple `<p>` elements may be used within a single `<div>`.

Parsers and renderers expected to process or display imsc-rosetta must be capable of understanding both scenarios of single `<p>` and multiple `<p>`.

***Special Note: XML inside `<p>` should NOT include any spacing in the XML structure - since we define `xml:space="preserve"` in the `<tt>` element, all spacing in the `<p>` element is intended for display.  Effectively this means that all `<p>` elements must be presented on a single line.***

***Special Note: Note that `<br/>` MUST be wrapped in `<span>`.  This ensures that 'simple' parsers retain the order of spans and brs, and so greatly simplifies simple manipulation of rosetta files.***

### `<span>`
`<span>` elements may contain the following attributes:

`style`

`<span>` may contain ***one*** of the following when it is a descendant of `<p>`:

- Text.  Example `<span>Some text </span><span>with more in a second span.</span>`

- A single `<br>`.  In this case the host span WILL NOT have any style associated, and WILL NOT contain any text - ***i.e. it will be exactly `<span><br/></span>`***.

- A pair of `<span>` elements defining Pictographic language base text and ruby text.  In this case the host `<span>` ***WILL NOT contain any text directly***. Example:
```
<span style="s_rb_algn_center"><span style="s_rb_b">Ruby Above</span><span style="s_rb_t">ruby</span></span>
```


For horizontal non- pictographic text, `<span>` ***will contain ONLY text***. (i.e. no nested spans - all spans will be descendants of `<p>`)

Nested `<span>` may ***only*** be used in subtitles requiring Rubies (i.e. Japanese), and be as above.  Spans contained within a base ruby span will only contain text, no further nesting is allowed.

## Example document structure

<details><summary>example document</summary>

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<tt xmlns="http://www.w3.org/ns/ttml" xmlns:ttm="http://www.w3.org/ns/ttml#metadata" xmlns:tts="http://www.w3.org/ns/ttml#styling" xmlns:ttp="http://www.w3.org/ns/ttml#parameter" xmlns:xml="http://www.w3.org/XML/1998/namespace" xmlns:ebutts="urn:ebu:tt:style" xmlns:itts="http://www.w3.org/ns/ttml/profile/imsc1#styling" xmlns:rosetta="https://github.com/imsc-rosetta/specification" ttp:timeBase="media" ttp:cellResolution="30 15" xml:space="preserve" ttp:frameRate="25" ttp:frameRateMultiplier="1 1" xml:lang="en">
 <head>
  <metadata>
   <rosetta:format>imsc-rosetta</rosetta:format>
   <rosetta:version>0.0.0</rosetta:version>
  </metadata>
  <styling>
   <style xml:id="r_region" tts:backgroundColor="transparent" tts:showBackground="whenActive" tts:fontStyle="normal" tts:fontWeight="normal" tts:color="white" tts:fontFamily="proportionalSansSerif" tts:textAlign="center" itts:fillLineGap="false" style="_r_default"/>
   <style xml:id="s_italic" tts:fontStyle="italic"/>
   <style xml:id="s_bold" tts:fontWeight="bold"/>
   <style xml:id="s_underline" tts:textDecoration="underline"/>
   <style xml:id="d_fillgap" itts:fillLineGap="true"/>
   <style xml:id="s_fg_black" tts:color="#000000"/>
   <style xml:id="s_fg_red" tts:color="#FF0000"/>
   <style xml:id="s_fg_yellow" tts:color="#FFFF00"/>
   <style xml:id="s_fg_green" tts:color="#00FF00"/>
   <style xml:id="s_fg_cyan" tts:color="#00FFFF"/>
   <style xml:id="s_fg_blue" tts:color="#0000FF"/>
   <style xml:id="s_fg_magenta" tts:color="#FF00FF"/>
   <style xml:id="ps_bg_boxedblack" tts:backgroundColor="#000000"/>
   <style xml:id="ps_bg_boxedred" tts:backgroundColor="#FF0000"/>
   <style xml:id="ps_bg_boxedyellow" tts:backgroundColor="#FF0000"/>
   <style xml:id="ps_bg_boxedgreen" tts:backgroundColor="#00FF00"/>
   <style xml:id="ps_bg_boxedcyan" tts:backgroundColor="#00FFFF"/>
   <style xml:id="ps_bg_boxedblue" tts:backgroundColor="#0000FF"/>
   <style xml:id="ps_bg_boxedmagenta" tts:backgroundColor="#FF00FF"/>
   <style xml:id="ps_bg_boxedwhite" tts:backgroundColor="#FFFFFF"/>
   <style xml:id="ps_bg_ghostboxedblack" tts:backgroundColor="#00000080"/>
   <style xml:id="ps_bg_ghostboxedred" tts:backgroundColor="#FF000080"/>
   <style xml:id="ps_bg_ghostboxedyellow" tts:backgroundColor="#FFFF0080"/>
   <style xml:id="ps_bg_ghostboxedgreen" tts:backgroundColor="#00FF0080"/>
   <style xml:id="ps_bg_ghostboxedcyan" tts:backgroundColor="#00FFFF80"/>
   <style xml:id="ps_bg_ghostboxedblue" tts:backgroundColor="#0000FF80"/>
   <style xml:id="ps_bg_ghostboxedmagenta" tts:backgroundColor="#FF00FF80"/>
   <style xml:id="ps_bg_ghostboxedwhite" tts:backgroundColor="#FFFFFF80"/>
   <style xml:id="d_outline" tts:textOutline="#000000 0.05em"/>
   <style xml:id="s_outlineblack" tts:textOutline="#000000 0.05em"/>
   <style xml:id="s_outlinered" tts:textOutline="#FF0000 0.05em"/>
   <style xml:id="s_outlineyellow" tts:textOutline="#FFFF00 0.05em"/>
   <style xml:id="s_outlinegreen" tts:textOutline="#00FF00 0.05em"/>
   <style xml:id="s_outlinecyan" tts:textOutline="#00FFFF 0.05em"/>
   <style xml:id="s_outlineblue" tts:textOutline="#0000FF 0.05em"/>
   <style xml:id="s_outlinemagenta" tts:textOutline="#FF00FF 0.05em"/>
   <style xml:id="s_outlinewhite" tts:textOutline="#FFFFFF 0.05em"/>
   <style xml:id="d_drop" tts:textOutline="#000000 0.05em"/>
   <style xml:id="s_dropblack" tts:textOutline="#000000 0.05em"/>
   <style xml:id="s_dropred" tts:textOutline="#FF0000 0.05em"/>
   <style xml:id="s_dropyellow" tts:textOutline="#FFFF00 0.05em"/>
   <style xml:id="s_dropgreen" tts:textOutline="#00FF00 0.05em"/>
   <style xml:id="s_dropcyan" tts:textOutline="#00FFFF 0.05em"/>
   <style xml:id="s_dropblue" tts:textOutline="#0000FF 0.05em"/>
   <style xml:id="s_dropmagenta" tts:textOutline="#FF00FF 0.05em"/>
   <style xml:id="s_dropwhite" tts:textOutline="#FFFFFF 0.05em"/>
   <style xml:id="s_noneblack"/>
   <style xml:id="s_nonered"/>
   <style xml:id="s_noneyellow"/>
   <style xml:id="s_nonegreen"/>
   <style xml:id="s_nonecyan"/>
   <style xml:id="s_noneblue"/>
   <style xml:id="s_nonemagenta"/>
   <style xml:id="s_nonewhite"/>
   <style xml:id="p_al_start" tts:textAlign="start"/>
   <style xml:id="p_al_end" tts:textAlign="end"/>
   <style xml:id="p_al_center" tts:textAlign="center"/>
   <style xml:id="p_al_start_start" ebutts:multiRowAlign="start" tts:textAlign="start"/>
   <style xml:id="p_al_start_center" ebutts:multiRowAlign="center" tts:textAlign="start"/>
   <style xml:id="p_al_start_end" ebutts:multiRowAlign="end" tts:textAlign="start"/>
   <style xml:id="p_al_end_start" ebutts:multiRowAlign="start" tts:textAlign="end"/>
   <style xml:id="p_al_end_center" ebutts:multiRowAlign="center" tts:textAlign="end"/>
   <style xml:id="p_al_end_end" ebutts:multiRowAlign="end" tts:textAlign="end"/>
   <style xml:id="p_al_center_start" ebutts:multiRowAlign="start" tts:textAlign="center"/>
   <style xml:id="p_al_start_center" ebutts:multiRowAlign="center" tts:textAlign="center"/>
   <style xml:id="p_al_center_end" ebutts:multiRowAlign="end" tts:textAlign="center"/>
   <style xml:id="d_forced" itts:forcedDisplay="true"/>
   <style xml:id="p_font1" tts:fontFamily="proportionalSansSerif" tts:lineHeight="125%" tts:fontSize="100%"/>
   <style xml:id="p_font2" tts:fontFamily="proportionalSansSerif" tts:lineHeight="125%" tts:fontSize="100%"/>
   <style xml:id="s_rb_b" tts:ruby="base"/>
   <style xml:id="s_rb_t" tts:ruby="text"/>
   <style xml:id="p_rb_res_before" tts:rubyReserve="before"/>
   <style xml:id="p_rb_res_after" tts:rubyReserve="after"/>
   <style xml:id="p_rb_res_both" tts:rubyReserve="both"/>
   <style xml:id="p_rb_res_outside" tts:rubyReserve="outside"/>
   <style xml:id="s_rb_algn_center" tts:ruby="container" tts:rubyAlign="center"/>
   <style xml:id="s_rb_algn_around" tts:ruby="container" tts:rubyAlign="spaceAround"/>
   <style xml:id="s_rb_posn_before" tts:ruby="container" tts:rubyPosition="before"/>
   <style xml:id="s_rb_posn_after" tts:ruby="container" tts:rubyPosition="after"/>
   <style xml:id="s_rb_posn_outside" tts:ruby="container" tts:rubyPosition="outside"/>
   <style xml:id="s_combine" tts:textCombine="all"/>
   <style xml:id="dps_shear" tts:shear="16.67%"/>
   <style xml:id="p_rtl" tts:direction="rtl"/>
   <style xml:id="p_ltr" tts:direction="ltr"/>
   <style xml:id="s_emf_fcb" tts:textEmphasis="filled circle before"/>
   <style xml:id="s_emf_fdb" tts:textEmphasis="filled dot before"/>
   <style xml:id="s_emf_fsb" tts:textEmphasis="filled sesame before"/>
   <style xml:id="s_emf_ocb" tts:textEmphasis="open circle before"/>
   <style xml:id="s_emf_odb" tts:textEmphasis="open dot before"/>
   <style xml:id="s_emf_osb" tts:textEmphasis="open sesame before"/>
   <style xml:id="s_emf_fca" tts:textEmphasis="filled circle after"/>
   <style xml:id="s_emf_fda" tts:textEmphasis="filled dot after"/>
   <style xml:id="s_emf_fsa" tts:textEmphasis="filled sesame after"/>
   <style xml:id="s_emf_oca" tts:textEmphasis="open circle after"/>
   <style xml:id="s_emf_oda" tts:textEmphasis="open dot after"/>
   <style xml:id="s_emf_osa" tts:textEmphasis="open sesame after"/>
   <style xml:id="s_emf_fco" tts:textEmphasis="filled circle outside"/>
   <style xml:id="s_emf_fdo" tts:textEmphasis="filled dot outside"/>
   <style xml:id="s_emf_fso" tts:textEmphasis="filled sesame outside"/>
   <style xml:id="s_emf_oco" tts:textEmphasis="open circle outside"/>
   <style xml:id="s_emf_odo" tts:textEmphasis="open dot outside"/>
   <style xml:id="s_emf_oso" tts:textEmphasis="open sesame outside"/>
   <style xml:id="r_vertical" tts:writingMode="tbrl"/>
   <style xml:id="_d_default" style="d_outline"/>
   <style xml:id="_r_default" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" tts:wrapOption="noWrap" tts:fontSize="5.333rh" tts:lineHeight="125%" ebutts:linePadding="0.25c"/>
  </styling>
  <layout>
   <region xml:id="R0" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" style="r_region"/>
   <region xml:id="R1" tts:origin="10% 10%" tts:extent="80% 73.3%" tts:displayAlign="after" style="r_region"/>
   <region xml:id="R2" tts:origin="10% 10%" tts:extent="80% 66.7%" tts:displayAlign="after" style="r_region"/>
   <region xml:id="R3" tts:origin="10% 10%" tts:extent="80% 60%" tts:displayAlign="after" style="r_region"/>
   <region xml:id="R4" tts:origin="10% 10%" tts:extent="80% 53.3%" tts:displayAlign="after" style="r_region"/>
   <region xml:id="R5" tts:origin="10% 10%" tts:extent="80% 46.7%" tts:displayAlign="after" style="r_region"/>
   <region xml:id="R6" tts:origin="10% 43.3%" tts:extent="80% 46.7%" tts:displayAlign="before" style="r_region"/>
   <region xml:id="R7" tts:origin="10% 36.7%" tts:extent="80% 53.3%" tts:displayAlign="before" style="r_region"/>
   <region xml:id="R8" tts:origin="10% 30%" tts:extent="80% 60%" tts:displayAlign="before" style="r_region"/>
   <region xml:id="R9" tts:origin="10% 23.3%" tts:extent="80% 66.7%" tts:displayAlign="before" style="r_region"/>
   <region xml:id="R10" tts:origin="10% 16.7%" tts:extent="80% 73.3%" tts:displayAlign="before" style="r_region"/>
   <region xml:id="R11" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="before" style="r_region"/>
   <region xml:id="R12" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="before" style="r_region r_vertical"/>
  </layout>
 </head>
 <body>
  <div xml:id="sub0" region="R0" begin="01:00:03.600" end="01:00:07.640" style="s_outlineblack">
   <metadata rosetta:comment="this is a comment test a cr"/>
   <p style="p_font2"><span style="ps_bg_boxedblack">First Frame of active video </span></p>
  </div>
  <div xml:id="1" region="R0" begin="01:00:07.760" end="01:00:11.760" style="_d_default">
   <p style="p_font2"><span>1 line</span><span style="s_nonered"> Center</span><span> Bottom</span></p>
  </div>
  <div xml:id="2" region="R0" begin="01:00:11.880" end="01:00:15.880" style="_d_default p_al_start">
   <p style="p_font2"><span>1 line left  bottom</span></p>
  </div>
  <div xml:id="3" region="R0" begin="01:00:16.000" end="01:00:20.000" style="_d_default p_al_end">
   <p style="p_font2"><span>1 line right bottom</span></p>
  </div>
  <div xml:id="4" region="R0" begin="01:00:20.120" end="01:00:24.120" style="_d_default">
   <p style="p_font2"><span>two line </span></p>
   <p style="p_font2"><span>center bottom</span></p>
  </div>
  <div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="_d_default">
   <p style="p_font2"><span>two lines</span></p>
   <p style="p_font2"><span>left bottom</span></p>
  </div>
  <div xml:id="6" region="R0" begin="01:00:28.360" end="01:00:32.360" style="_d_default">
   <p style="p_font2"><span>two lines</span></p>
   <p style="p_font2"><span>right bottom</span></p>
  </div>
  <div xml:id="7" region="R0" begin="01:00:32.480" end="01:00:36.480" style="_d_default">
   <p style="p_font2"><span>row 11</span></p>
  </div>
  <div xml:id="8" region="R1" begin="01:00:36.640" end="01:00:40.640" style="_d_default">
   <p style="p_font2"><span>row 10</span></p>
  </div>
  <div xml:id="9" region="R2" begin="01:00:40.760" end="01:00:44.760" style="_d_default">
   <p style="p_font2"><span>row 9</span></p>
  </div>
  <div xml:id="10" region="R3" begin="01:00:44.880" end="01:00:48.880" style="_d_default">
   <p style="p_font2"><span>row 8</span></p>
  </div>
  <div xml:id="11" region="R4" begin="01:00:49.000" end="01:00:53.000" style="_d_default">
   <p style="p_font2"><span>row 7</span></p>
  </div>
  <div xml:id="12" region="R5" begin="01:00:53.120" end="01:00:57.120" style="_d_default">
   <p style="p_font2"><span>row 6</span></p>
  </div>
  <div xml:id="13" region="R6" begin="01:00:57.240" end="01:01:01.240" style="_d_default">
   <p style="p_font2"><span>row 5</span></p>
  </div>
  <div xml:id="14" region="R7" begin="01:01:01.360" end="01:01:05.360" style="_d_default">
   <p style="p_font2"><span>row 4</span></p>
  </div>
  <div xml:id="15" region="R8" begin="01:01:05.480" end="01:01:09.480" style="_d_default">
   <p style="p_font2"><span>row 3</span></p>
  </div>
  <div xml:id="16" region="R9" begin="01:01:09.640" end="01:01:13.640" style="_d_default">
   <p style="p_font2"><span>row 2</span></p>
  </div>
  <div xml:id="17" region="R10" begin="01:01:13.760" end="01:01:17.760" style="_d_default">
   <p style="p_font2"><span>row 1</span></p>
  </div>
  <div xml:id="18" region="R11" begin="01:01:17.880" end="01:01:21.880" style="_d_default">
   <p style="p_font2"><span>row 0</span></p>
  </div>
  <div xml:id="19" region="R11" begin="01:01:22.000" end="01:01:26.000" style="_d_default">
   <p style="p_font2"><span>top center</span></p>
  </div>
  <div xml:id="20" region="R11" begin="01:01:26.120" end="01:01:30.120" style="_d_default p_al_start">
   <p style="p_font2"><span>top left</span></p>
  </div>
  <div xml:id="21" region="R11" begin="01:01:30.240" end="01:01:34.240" style="_d_default p_al_end">
   <p style="p_font2"><span>top right</span></p>
  </div>
  <div xml:id="22" region="R0" begin="01:01:34.360" end="01:01:38.360" style="_d_default">
   <p style="p_al_start p_font2"><span>left</span></p>
   <p style="p_font2"><span>center</span></p>
   <p style="p_al_end p_font2"><span>right</span></p>
  </div>
  <div xml:id="23" region="R0" begin="01:01:38.520" end="01:01:42.520" style="_d_default">
   <p style="p_font2"><span>normal</span><span style="s_italic"> italic</span><span style="s_bold"> bold </span><span style="s_underline">underline</span><span> normal</span></p>
   <p style="p_font2"><span style="s_underline">underlined</span><span style="s_italic s_underline"> italic</span><span style="s_bold s_underline"> bold</span><span style="s_underline"> normal</span></p>
  </div>
  <div xml:id="24" region="R0" begin="01:01:42.640" end="01:01:46.640" style="_d_default">
   <p style="p_font2"><span style="s_fg_red">red </span><span style="s_fg_yellow">yellow </span><span style="s_fg_green">green </span><span style="s_fg_cyan">cyan </span><span style="s_fg_blue">blue </span><span style="s_fg_magenta">magenta</span></p>
  </div>
  <div xml:id="25" region="R11" begin="01:01:46.760" end="01:01:50.760" style="_d_default">
   <p style="p_font2"><span>Two lines </span></p>
   <p style="p_font2"><span>top center</span></p>
  </div>
  <div xml:id="26" region="R0" begin="01:01:50.880" end="01:01:53.880" style="_d_default s_noneblack">
   <p style="p_font2 ps_bg_boxedblack"><span>Background stripe</span></p>
   <p style="p_font2 ps_bg_boxedblack"><span>black</span></p>
  </div>
  <div xml:id="27" region="R0" begin="01:01:54.000" end="01:01:57.000" style="_d_default">
   <p style="p_font2"><span style="ps_bg_boxedblack">black</span></p>
   <p style="p_font2"><span style="ps_bg_boxedblack">box</span></p>
  </div>
  <div xml:id="28" region="R0" begin="01:01:57.120" end="01:02:00.120" style="_d_default">
   <p style="p_font2"><span style="ps_bg_ghostboxedblack">ghost</span></p>
   <p style="p_font2"><span style="ps_bg_ghostboxedblack">box</span></p>
  </div>
  <div xml:id="29" region="R0" begin="01:02:00.240" end="01:02:03.240" style="_d_default s_noneblack">
   <p style="p_font2 ps_bg_ghostboxedblack"><span>Ghost stripe</span></p>
   <p style="p_font2 ps_bg_ghostboxedblack"><span>black</span></p>
  </div>
  <div xml:id="30" region="R0" begin="01:02:03.359" end="01:02:06.359" style="_d_default">
   <p style="p_font2"><span style="ps_bg_ghostboxedblack">Ghost box change to </span><span style="ps_bg_ghostboxedred s_nonered">red</span></p>
  </div>
  <div xml:id="31" region="R0" begin="01:02:07.359" end="01:02:09.359" style="_d_default">
   <p style="p_font2 p_rb_res_before"><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above </span><span style="s_rb_t">ruby</span></span><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above 2</span><span style="s_rb_t">ruby2</span></span></p>
  </div>
  <div xml:id="32" region="R0" begin="01:02:10.359" end="01:02:12.359" style="_d_default">
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b">Ruby Below </span><span style="s_rb_t">ruby</span></span><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above 2</span><span style="s_rb_t">ruby2</span></span></p>
  </div>
  <div xml:id="33" region="R0" begin="01:02:13.359" end="01:02:16.359" style="_d_default">
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above </span><span style="s_rb_t">ruby</span></span><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above 2</span><span style="s_rb_t">ruby2</span></span></p>
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b">Ruby Below </span><span style="s_rb_t">ruby</span></span><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b">Ruby Below 2</span><span style="s_rb_t">ruby2</span></span></p>
  </div>
  <div xml:id="34" region="R0" begin="01:02:17.359" end="01:02:20.359" style="_d_default">
   <p style="p_font2 p_rb_res_after"><span>No Ruby </span><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above 2</span><span style="s_rb_t">ruby2</span></span></p>
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b">Ruby Below </span><span style="s_rb_t">ruby</span></span><span>No Ruby</span></p>
  </div>
  <div xml:id="35" region="R12" begin="01:02:21.359" end="01:02:24.359" style="_d_default">
   <p style="p_font2 p_rb_res_after"><span>Vert No Ruby </span><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above 2</span><span style="s_rb_t">ruby2</span></span></p>
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b">Ruby Below </span><span style="s_rb_t">ruby</span></span><span>No Ruby</span></p>
  </div>
  <div xml:id="36" region="R12" begin="01:02:25.359" end="01:02:29.359" style="_d_default">
   <p style="p_font2 p_rb_res_after">東南<span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">東南</span><span style="s_rb_t">とうなん</span></span></p>
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b">東南</span><span style="s_rb_t">たつみ</span></span><span>No Ruby</span></p>
  </div>
  <div xml:id="37" region="R12" begin="01:02:30.359" end="01:02:34.359" style="_d_default dps_shear">
   <p style="p_font2 p_rb_res_after"><span style="s_combine">1984</span><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b s_emf_fca">東南</span><span style="s_rb_t">とうなん</span></span></p>
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b s_emf_fca">東南</span><span style="s_rb_t">たつみ</span></span><span style="s_emf_fca">No Ruby</span></p>
  </div>
  <div xml:id="38" region="R0" begin="01:02:35.120" end="01:02:40.120" style="_d_default">
   <p style="p_font2 p_al_center_start"><span>two line</span><span><br/></span><span>center start bottom</span></p>
  </div>
  <div xml:id="39" region="R0" begin="01:02:41.120" end="01:02:44.120" style="_d_default">
   <p style="p_font2 p_al_center_start"><span style="ps_bg_ghostboxedblack">two line</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span></p>
  </div>
  <div xml:id="40" region="R0" begin="01:02:45.120" end="01:02:48.120" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack"><span style="ps_bg_ghostboxedblack">two line</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span></p>
  </div>
  <div xml:id="41" region="R12" begin="01:02:46.359" end="01:02:49.359" style="_d_default">
   <p style="p_font2 p_rb_res_after"><span>Vert No Ruby </span><span style="s_rb_algn_center s_rb_posn_before"><span style="s_rb_b">Ruby Above 2</span><span style="s_rb_t">ruby2</span></span></p>
   <p style="p_font2 p_rb_res_after"><span style="s_rb_algn_center s_rb_posn_after"><span style="s_rb_b">Ruby Below </span><span style="s_rb_t">ruby</span></span><span>No Ruby</span></p>
  </div>
  <div xml:id="42" region="R0" begin="01:02:50.120" end="01:02:54.120" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack p_rtl"><span style="ps_bg_ghostboxedblack">abc אותיות </span><span style="ps_bg_ghostboxedblack s_fg_red">bcd השימו 1983 ש</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span></p>
  </div>
  <div xml:id="43" region="R0" begin="01:02:55.120" end="01:02:59.120" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack p_ltr"><span style="ps_bg_ghostboxedblack">abc אותיות </span><span style="ps_bg_ghostboxedblack s_fg_red">bcd השימו 1983 ש</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span></p>
  </div>
  <div xml:id="44" region="R0" begin="01:03:00.120" end="01:03:04.120" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span></p>
  </div>
  <div xml:id="45" region="R0" begin="01:03:05.120" end="01:03:05.220" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span><span><br/></span><span style="ps_bg_ghostboxedblack">1  </span><span style="ps_bg_ghostboxedblack">2</span><span style="ps_bg_ghostboxedblack">3</span></p>
  </div>
  <div xml:id="45.2" region="R0" begin="01:03:05.220" end="01:03:06.120" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span><span><br/></span><span style="ps_bg_ghostboxedblack">1  </span><span style="ps_bg_ghostboxedblack">2</span><span style="ps_bg_ghostboxedblack">3</span></p>
  </div>
  <div xml:id="45.5" region="R0" begin="01:03:06.120" end="01:03:08.120" style="_d_default">
   <p style="p_font2 p_al_center_start ps_bg_ghostboxedblack p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span><span><br/></span><span style="ps_bg_ghostboxedblack">center start bottom</span><span><br/></span><span style="ps_bg_ghostboxedblack">1  </span><span style="ps_bg_ghostboxedblack">2</span><span style="ps_bg_ghostboxedblack">3</span></p>
  </div>
  <div xml:id="46" region="R0" begin="01:03:10.359" end="01:03:13.359" style="_d_default">
   <p style="p_font2 p_rb_res_outside"><span>No Ruby </span><span style="s_rb_algn_center"><span style="s_rb_b">Ruby Above </span><span style="s_rb_t">ruby</span></span><span style="s_rb_algn_center s_rb_posn_outside"><span style="s_rb_b">Ruby Above 2</span><span style="s_rb_t">ruby2</span></span><span><br/></span><span style="s_rb_algn_center s_rb_posn_outside"><span style="s_rb_b">Ruby Below </span><span style="s_rb_t">ruby</span></span><span style="s_rb_algn_center s_rb_posn_outside"><span style="s_rb_b">Ruby Below 2</span><span style="s_rb_t">ruby2</span></span></p>
  </div>
  <div xml:id="47" region="R0" begin="01:03:14.359" end="01:03:18.359" style="_d_default">
   <p style="p_font2 p_rb_res_outside"><span>No Ruby Above No Ruby Above 2</span><span><br/></span><span>No Ruby Below No Ruby Below 2</span></p>
  </div>
  <div xml:id="48" region="R12" begin="01:03:20.359" end="01:03:24.359" style="_d_default dps_shear">
   <p style="p_font2 p_rb_res_outside"><span style="s_combine">84</span><span style="s_combine">1984</span><span style="s_rb_algn_center s_rb_posn_outside"><span style="s_rb_b s_emf_fco">東南</span><span style="s_rb_t">とうなん</span></span><span><br/></span><span style="s_rb_algn_center s_rb_posn_outside"><span style="s_rb_b s_emf_fco">東南</span><span style="s_rb_t">たつみ</span></span><span style="s_emf_fco">No Ruby</span></p>
  </div>
  <div xml:id="49" region="R12" begin="01:03:25.359" end="01:03:29.359" style="_d_default dps_shear">
   <p style="p_font2 p_rb_res_outside"><span style="s_combine ps_bg_ghostboxedblack">1984</span><span style="s_rb_algn_center s_rb_posn_outside ps_bg_ghostboxedblack"><span style="s_rb_b s_emf_fco ps_bg_ghostboxedblack">東南</span><span style="s_rb_t ps_bg_ghostboxedblack">とうなん</span></span><span><br/></span><span style="s_rb_algn_center s_rb_posn_outside ps_bg_ghostboxedblack"><span style="s_rb_b s_emf_fco ps_bg_ghostboxedblack"> 東南</span><span style="s_rb_t ps_bg_ghostboxedblack">たつみ</span></span><span style="s_emf_fco ps_bg_ghostboxedblack">No Ruby Boxed</span></p>
  </div>
  <div xml:id="50" region="R0" begin="01:03:30.120" end="01:03:30.420" style="_d_default">
   <p style="p_font2 p_al_center_start p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span></p>
   <p style="p_font2 p_al_center_start p_ltr"><span style="ps_bg_ghostboxedblack">pretty normal</span><span><span><br/></span></span><span style="ps_bg_ghostboxedblack">1      </span><span style="ps_bg_ghostboxedblack">2</span><span style="ps_bg_ghostboxedblack">3</span></p>
  </div>
  <div xml:id="50" region="R0" begin="01:03:30.420" end="01:03:31.420" style="_d_default">
   <p style="p_font2 p_al_center_start p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span></p>
   <p style="p_font2 p_al_center_start p_ltr"><span style="ps_bg_ghostboxedblack">pretty preserve</span><span><br/></span><span style="ps_bg_ghostboxedblack">1      </span><span style="ps_bg_ghostboxedblack">2</span><span style="ps_bg_ghostboxedblack">3</span></p>
  </div>
  <div style="_d_default">
   <p xml:id="51" region="R0" begin="01:03:31.420" end="01:03:32.120" style="p_font2 p_al_center_start p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span></p>
   <p xml:id="51.1" region="R0" begin="01:03:31.420" end="01:03:32.120" style="p_font2 p_al_center_start p_ltr"><span style="ps_bg_ghostboxedblack">1 line p normal</span><span><br/></span><span style="ps_bg_ghostboxedblack">1      </span><span style="ps_bg_ghostboxedblack">2</span><span style="ps_bg_ghostboxedblack">3</span></p>
  </div>
  <div style="_d_default">
   <p xml:id="52" region="R0" begin="01:03:32.220" end="01:03:33.120" style="p_font2 p_al_center_start p_rtl"><span style="ps_bg_ghostboxedblack">من البيان والتبيين الى</span><span style="ps_bg_ghostboxedblack s_fg_red"> البتاع والتبتيع</span></p>
   <p xml:id="52.1" region="R0" begin="01:03:32.220" end="01:03:33.120" style="p_font2 p_al_center_start p_ltr"><span style="ps_bg_ghostboxedblack">1 line p preserve</span><span><span><br/></span></span><span style="ps_bg_ghostboxedblack">1      </span><span style="ps_bg_ghostboxedblack">2</span><span style="ps_bg_ghostboxedblack">3</span></p>
  </div>
  <div xml:id="53" region="R0" begin="01:03:34.359" end="01:03:36.359" style="_d_default dps_shear">
   <p style="p_font2 p_rb_res_outside"><span style="s_combine">84</span><span>1984</span></p>
  </div>
  <div xml:id="54" region="R12" begin="01:03:37.359" end="01:03:39.359" style="_d_default">
   <p style="p_font2 p_rb_res_after"><span style="s_emf_fco">東南</span><span><br/></span><span style="s_emf_fso">Emph Outside</span></p>
  </div>
  <div xml:id="55" region="R12" begin="01:03:40.359" end="01:03:41.359" style="_d_default">
   <p style="p_font2 p_rb_res_outside"><span style="s_combine">1984</span><span style="s_rb_algn_center"><span style="s_rb_b s_emf_fco">東南</span><span style="s_rb_t">とうなん</span></span><span><br/></span><span style="s_rb_algn_center s_emf_fco"><span style="s_rb_b">東南</span><span style="s_rb_t">たつみ</span></span><span style="s_emf_fco">No Ruby</span></p>
  </div>
</body>
</tt>
```
</details>



