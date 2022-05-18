# Document Structure

## Allowed elements

### `<tt>`
`<tt>` contains only the specified attributes. `<tt>` contains the following elements:

Exactly one `<head>` followed by exactly one `<body>`.

### `<head>`
`<head>` must have no attributes. `<head>` contains the following elements:

Exactly one `<metadata>` followed by exactly one `<styling>` followed by exactly one `<layout>`.

### `<metadata>` - as used in `<head>`
`<metadata>` must have no attributes. `<metadata>` must the following elements:

`<rosetta:format>rosetta-imsc</rosetta:format>`

`<rosetta:version>0.0.0</rosetta:version>`


`<metadata>` may contain other optional metadata elements.  (See metadata document)

The order of elements in `<metadata>` must not be important.

### `<styling>`
`<styling>` must have no attributes. `<styling>` contains the following elements:

one or more `<style>` elements only.

### `<style>`
`<style>` elements must be represented exactly as found in the style specification.

`<style>` elements will not have any content, and should be represented as closed elements, e.g. `<style xml:id="ds_red" tts:color="#FF0000"/>`

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

*Special Note: XML inside `<div>` should NOT include any spacing in the XML structure - since we define `xml:space="preserve"` in the `<tt>` element, all spacing in the `<div>` element is intended for display.  Effectively this means that all `<div>` elements must be presented on a single line.*

### `<metadata>` - as used in `<div>`
`<metadata>` used in `<div>` must have one attribute `rosetta:comment` used to carry comment text along with the subtitle.

`<metadata>` used in `<div>` must have no content, and be closed.  e.g. `<metadata rosetta:comment="comment text"/>`

### `<p>`
`<p>` elements may contain the following attributes:

`style`

`<p>` contains the following elements:

Zero or more `<span>` elements

Zero or more `<br/>` elements

`<p>` will NOT include and text directly - all text must be wrapped in `<span>`

A `<p>` element may contain multiple lines by use of `<br/>`, but in this case all lines will have the same alignment, and the use of multiRowAlign is allowed.

Where a subtitle requires a line(s) to be aligned start, and other line(s) center or end, multiple `<p>` elements may be used within a single `<div>`.

Parsers and renderers expected to process or display imsc-rosetta must be capable of understanding both scenarios of single `<p>` and multiple `<p>`.

### `<span>`
`<span>` elements may contain the following attributes:

`style`

For horizontal simple text, `<span>` will contain ONLY text. (i.e. no nested spans)

For text requiring Rubies (Japanese), `<span>` may contain other `<span>` elements. In this case, only 'leaf' nodes will contain text. (i.e. no `<span>` may contain text AND other spans).

No other elements are allowed in `<span>` (e.g. no `<br/>`).


## Example document structure

<details><summary>example document</summary>
 
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<tt xmlns="http://www.w3.org/ns/ttml" xmlns:ttm="http://www.w3.org/ns/ttml#metadata" xmlns:tts="http://www.w3.org/ns/ttml#styling" xmlns:ttp="http://www.w3.org/ns/ttml#parameter" xmlns:xml="http://www.w3.org/XML/1998/namespace" xmlns:ebutts="urn:ebu:tt:style" xmlns:itts="http://www.w3.org/ns/ttml/profile/imsc1#styling" xmlns:rosetta="https://github.com/imsc-rosetta/specification" ttp:timeBase="media" ttp:cellResolution="30 15" xml:space="preserve" ttp:frameRate="25" ttp:frameRateMultiplier="1 1" xml:lang="el-GR">
<head>
<metadata>
 <rosetta:format>imsc-rosetta</rosetta:format>
 <rosetta:version>0.0.0</rosetta:version>
</metadata>
<styling>
 <style xml:id="r_region" tts:backgroundColor="transparent" tts:showBackground="whenActive" tts:fontStyle="normal" tts:fontWeight="normal" tts:color="white" tts:fontFamily="proportionalSansSerif" tts:textAlign="center" itts:fillLineGap="true" style="_r_default"/>
 <style xml:id="s_italic" tts:fontStyle="italic"/>
 <style xml:id="ds_fg_red" tts:color="#FF0000"/>
 <style xml:id="ds_fg_yellow" tts:color="#FFFF00"/>
 <style xml:id="ds_fg_green" tts:color="#00FF00"/>
 <style xml:id="ds_fg_cyan" tts:color="#00FFFF"/>
 <style xml:id="ds_fg_blue" tts:color="#0000FF"/>
 <style xml:id="ds_fg_magenta" tts:color="#FF00FF"/>
 <style xml:id="ps_bg_boxedblack" tts:backgroundColor="#000000"/>
 <style xml:id="ds_outlineblack" tts:textOutline="#000000 0.05em"/>
 <style xml:id="ds_nonered"/>
 <style xml:id="dp_al_start" tts:textAlign="start"/>
 <style xml:id="dp_al_end" tts:textAlign="end"/>
 <style xml:id="p_font2" tts:fontFamily="proportionalSansSerif" tts:lineHeight="125%" tts:fontSize="100%"/>
 <style xml:id="_d_default"/>
 <style xml:id="_s_default"/>
 <style xml:id="_p_default" style="p_font2"/>
 <style xml:id="_r_default" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" tts:fontSize="5.333rh" tts:lineHeight="125%" ebutts:linePadding="0.25c"/>
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
</layout>
</head>
<body>
<div xml:id="sub0" region="R0" begin="01:00:03.600" end="01:00:07.640" style="ds_outlineblack"><metadata rosetta:comment="this is a comment test a cr"/><p style="p_font2"><span style="ps_bg_boxedblack">First Frame of active video </span></p></div>
<div xml:id="1" region="R0" begin="01:00:07.760" end="01:00:11.760"><p style="p_font2"><span>1 line </span><span style="ds_nonered">  Center</span><span> Bottom</span></p></div>
<div xml:id="2" region="R0" begin="01:00:11.880" end="01:00:15.880" style="dp_al_start"><p style="p_font2"><span>1 line left  bottom</span></p></div>
<div xml:id="3" region="R0" begin="01:00:16.000" end="01:00:20.000" style="dp_al_end"><p style="p_font2"><span>1 line right bottom</span></p></div>
<div xml:id="4" region="R0" begin="01:00:20.120" end="01:00:24.120"><p style="p_font2"><span>two  line </span></p><p style="p_font2"><span>center bottom</span></p></div>
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="dp_al_start"><p style="p_font2"><span>to lines</span></p><p style="p_font2"><span>left bottom</span></p></div>
<div xml:id="6" region="R0" begin="01:00:28.360" end="01:00:32.360" style="dp_al_end"><p style="p_font2"><span>two lines</span></p><p style="p_font2"><span>right bottom</span></p></div>
<div xml:id="7" region="R0" begin="01:00:32.480" end="01:00:36.480"><p style="p_font2"><span>row 11</span></p></div>
<div xml:id="8" region="R1" begin="01:00:36.640" end="01:00:40.640"><p style="p_font2"><span>row 10</span></p></div>
<div xml:id="9" region="R2" begin="01:00:40.760" end="01:00:44.760"><p style="p_font2"><span>row 9</span></p></div>
<div xml:id="10" region="R3" begin="01:00:44.880" end="01:00:48.880"><p style="p_font2"><span>row 8</span></p></div>
<div xml:id="11" region="R4" begin="01:00:49.000" end="01:00:53.000"><p style="p_font2"><span>row 7</span></p></div>
<div xml:id="12" region="R5" begin="01:00:53.120" end="01:00:57.120"><p style="p_font2"><span>row 6</span></p></div>
<div xml:id="13" region="R6" begin="01:00:57.240" end="01:01:01.240"><p style="p_font2"><span>row 5</span></p></div>
<div xml:id="14" region="R7" begin="01:01:01.360" end="01:01:05.360"><p style="p_font2"><span>row 4</span></p></div>
<div xml:id="15" region="R8" begin="01:01:05.480" end="01:01:09.480"><p style="p_font2"><span>row 3</span></p></div>
<div xml:id="16" region="R9" begin="01:01:09.640" end="01:01:13.640"><p style="p_font2"><span>row 2</span></p></div>
<div xml:id="17" region="R10" begin="01:01:13.760" end="01:01:17.760"><p style="p_font2"><span>row 1</span></p></div>
<div xml:id="18" region="R11" begin="01:01:17.880" end="01:01:21.880"><p style="p_font2"><span>row 0</span></p></div>
<div xml:id="19" region="R11" begin="01:01:22.000" end="01:01:26.000"><p style="p_font2"><span>top center</span></p></div>
<div xml:id="20" region="R11" begin="01:01:26.120" end="01:01:30.120" style="dp_al_start"><p style="p_font2"><span>top left</span></p></div>
<div xml:id="21" region="R11" begin="01:01:30.240" end="01:01:34.240" style="dp_al_end"><p style="p_font2"><span>top right</span></p></div>
<div xml:id="22" region="R0" begin="01:01:34.360" end="01:01:38.360"><p style="dp_al_start p_font2"><span>left</span></p><p style="p_font2"><span>center</span></p><p style="dp_al_end p_font2"><span>right</span></p></div>
<div xml:id="23" region="R0" begin="01:01:38.520" end="01:01:42.520"><p style="p_font2"><span>normal</span><span style="s_italic"> italic</span><span> normal</span></p></div>
<div xml:id="24" region="R0" begin="01:01:42.640" end="01:01:46.640"><p style="p_font2"><span style="ds_fg_red">red </span><span style="ds_fg_yellow">yellow </span><span style="ds_fg_green">green </span><span style="ds_fg_cyan">cyan </span><span style="ds_fg_blue">blue </span><span style="ds_fg_magenta">magenta</span></p></div>
<div xml:id="25" region="R11" begin="01:01:46.760" end="01:01:50.760"><p style="p_font2"><span>Two lines </span></p><p style="p_font2"><span>top center</span></p></div>
</body>
</tt>
```
</details>



