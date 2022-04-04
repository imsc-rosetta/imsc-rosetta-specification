# Document Structure

## Allowed elements

### `<tt>`
`<tt>` contains only the specified attributes. `<tt>` contains the following elements:

Exactly one `<head>` followed by exactly one `<body>`.

### `<head>`
`<head>` must have no attributes. `<head>` contains the following elements:

Exactly one `<metadata>` followed by exactly one `<styling>` followed by exactly one `<layout>`.

### `<metadata>` - as used in `<head>`
`<metadata>` must have no attributes. `<metadata>` contains the following elements:

`<rosetta:format>rosetta-imsc</rosetta:format>`

`<rosetta:version>0.0.0</rosetta:version>`

other optional metadata elements.

The order of elements must not be important

### `<styling>`
`<styling>` must have no attributes. `<styling>` contains the following elements:

one or more `<style>` elements only.

### `<style>`
`<style>` elements must be represented exactly as found ion the style specification.

`<style>` elements will not have any content, and should be represented as closed elements, e.g. `<style xml:id="ds_red" tts:color="#FF0000"/>`

### `<layout>`
`<layout>` must have no attributes. `<layout>` contains the following elements:

one or more `<region>` elements only.

### `<region>`
`<region>` elements must contain the following attributes:

`xml:id` `tts:origin` `tts:extent` `tts:displayAlign` `style="r_region"`

`<region>` elements will not have any content, and should be represented as closed elements, 

e.g. `<region xml:id="R0" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" style="r_region"/>`

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

`<p>` will NOT include and text directly - all text must be wrapped in `<span>`

### `<span>`
`<span>` elements may contain the following attributes:

`style`

For horizontal simple text, `<span>` will contain ONLY text. (i.e. no nested spans)

For text requiring Rubies, `<span>` may contain other `<span>` elements. In this case, only 'leaf' nodes will contain text. (i.e. no `<span>` may contain text AND other spans).


## Example document structure
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<tt xmlns="http://www.w3.org/ns/ttml" xmlns:ttm="http://www.w3.org/ns/ttml#metadata" xmlns:tts="http://www.w3.org/ns/ttml#styling" xmlns:ttp="http://www.w3.org/ns/ttml#parameter" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:smpte="http://smpte-ra.org/schemas/2052-1/2013/smpte-tt" xmlns:xml="http://www.w3.org/XML/1998/namespace" xmlns:ebutts="urn:ebu:tt:style" xmlns:itts="http://www.w3.org/ns/ttml/profile/imsc1#styling" xmlns:orion="http://orion.ttml.org/imsc" ttp:timeBase="media" ttp:frameRate="25" ttp:frameRateMultiplier="1 1" ttp:cellResolution="30 15" xml:lang="el-GR" xml:space="preserve">
<head>
 <metadata>
  <rosetta:format>rosetta-imsc</rosetta:format>
  <rosetta:version>0.0.0</rosetta:version>
  <ttm:title>Sample</ttm:title>
  <ttm:desc>Sample Rosetta IMSC file</ttm:desc>
 </metadata>
 <styling>
  <style xml:id="r_region" tts:backgroundColor="transparent" tts:showBackground="whenActive" tts:fontStyle="normal" tts:fontWeight="normal" tts:color="white" tts:fontFamily="proportionalSansSerif" tts:textAlign="center" tts:fontSize="6.667rh" tts:lineHeight="125%" ebutts:linePadding="0.25c" itts:fillLineGap="true"/>
  <style xml:id="p_font2" tts:fontFamily="proportionalSansSerif" tts:lineHeight="125%" tts:fontSize="80%"/>
  <style xml:id="s_italic" tts:fontStyle="italic"/>
  <style xml:id="ds_red" tts:color="#FF0000"/>
  <style xml:id="ds_yellow" tts:color="#FFFF00"/>
  <style xml:id="ds_green" tts:color="#00FF00"/>
  <style xml:id="ds_cyan" tts:color="#00FFFF"/>
  <style xml:id="ds_blue" tts:color="#0000FF"/>
  <style xml:id="ds_magenta" tts:color="#FF00FF"/>
  <style xml:id="ps_boxedblack" tts:backgroundColor="#000000"/>
  <style xml:id="ds_outlineblack" tts:textOutline="#000000 0.05em"/>
  <style xml:id="dp_start" tts:textAlign="start"/>
  <style xml:id="dp_end" tts:textAlign="end"/>
 </styling>
 <layout>
  <region xml:id="R0" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" style="r_region"/>
  <region xml:id="R1" tts:origin="10% 10%" tts:extent="80% 66.66%" tts:displayAlign="after" style="r_region"/>
  <region xml:id="R2" tts:origin="10% 10%" tts:extent="80% 53.33%" tts:displayAlign="after" style="r_region"/>
  <region xml:id="R3" tts:origin="10% 10%" tts:extent="80% 73.33%" tts:displayAlign="after" style="r_region"/>
  <region xml:id="R4" tts:origin="10% 10%" tts:extent="80% 60%" tts:displayAlign="after" style="r_region"/>
  <region xml:id="R5" tts:origin="10% 10%" tts:extent="80% 46.66%" tts:displayAlign="after" style="r_region"/>
  <region xml:id="R6" tts:origin="10% 43.33%" tts:extent="80% 46.66%" tts:displayAlign="before" style="r_region"/>
  <region xml:id="R7" tts:origin="10% 36.66%" tts:extent="80% 53.33%" tts:displayAlign="before" style="r_region"/>
  <region xml:id="R8" tts:origin="10% 30%" tts:extent="80% 60%" tts:displayAlign="before" style="r_region"/>
  <region xml:id="R9" tts:origin="10% 23.33%" tts:extent="80% 66.66%" tts:displayAlign="before" style="r_region"/>
  <region xml:id="R10" tts:origin="10% 16.66%" tts:extent="80% 73.33%" tts:displayAlign="before" style="r_region"/>
  <region xml:id="R11" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="before" style="r_region"/>
 </layout>
</head>
<body>
<div xml:id="sub0" region="R0" begin="10:00:10.000" end="10:00:10.040" style="ds_outlineblack"><metadata rosetta:comment="comment text"/><p style="p_font2"><span style="ps_boxedblack">First Frame of Video</span></p><p style="p_font2"><span style="ps_boxedblack">FRAME 750</span></p></div>
<div xml:id="sub1" region="R0" begin="10:00:11.000" end="10:00:12.000" style="ds_outlineblack"><p style="dp_start p_font2"><span style="ps_boxedblack">Αα, Άά, Ββ, Γγ, Δδ, Εε, Έέ, Ζζ, Ηη, Ήή,</span></p></div>
<div xml:id="sub2" region="R0" begin="10:00:13.000" end="10:00:14.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Θθ, Ιι, Ίί, Ϊϊ, Κκ, Λλ, Μμ, Νν, Ξξ, Οο,</span></p></div>
<div xml:id="sub3" region="R0" begin="10:00:15.000" end="10:00:16.000" style="ds_outlineblack"><p style="dp_end p_font2"><span style="ps_boxedblack">Όό, Ππ, Ρρ, Σσ, Ττ, Υυ, Ύύ, Ϋϋ, Φφ, Χχ,</span></p></div>
<div xml:id="sub4" region="R0" begin="10:00:17.000" end="10:00:18.000" style="ds_outlineblack"><p style="dp_start p_font2"><span style="ps_boxedblack">Ψψ, Ωω, Ώώ, Αα, Άά, Ββ, Γγ, Δδ, Εε, Έέ,</span></p><p style="dp_start p_font2"><span style="ps_boxedblack">Ζζ, Ηη, Ήή, Θθ, Ιι, Ίί, Ϊϊ, Κκ, Λλ, Μμ,</span></p></div>
<div xml:id="sub5" region="R0" begin="10:00:19.000" end="10:00:20.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Νν, Ξξ, Οο, Όό, Ππ, Ρρ, Σσ, Ττ, Υυ, Ύύ,</span></p><p style="p_font2"><span style="ps_boxedblack">Ϋϋ, Φφ, Χχ, Ψψ, Ωω, Ώώ, Αα, Άά, Ββ, Γγ,</span></p></div>
<div xml:id="sub6" region="R0" begin="10:00:21.000" end="10:00:22.000" style="ds_outlineblack"><p style="dp_end p_font2"><span style="ps_boxedblack">! @ # £ % « &amp; » ( ) ; ... : - , + =</span></p><p style="dp_end p_font2"><span style="ps_boxedblack">1 2 3 4 5 6 7 8 9 0 / ? ' ` ² ³</span></p></div>
<div xml:id="sub7" region="R1" begin="10:00:23.000" end="10:00:24.000" style="ds_outlineblack"><p style="dp_start p_font2"><span style="ds_red ps_boxedblack">Αα, Άά, Ββ, Γγ, Δδ, Εε, Έέ, Ζζ, Ηη, Ήή,</span></p><p style="dp_start p_font2"><span style="ds_green ps_boxedblack">Θθ, Ιι, Ίί, Ϊϊ, Κκ, Λλ, Μμ, Νν, Ξξ, Οο,</span></p></div>
<div xml:id="sub8" region="R1" begin="10:00:25.000" end="10:00:26.000" style="ds_outlineblack"><p style="p_font2"><span style="ds_yellow ps_boxedblack">Όό, Ππ, Ρρ, Σσ, Ττ, Υυ, Ύύ, Ϋϋ, Φφ, Χχ,</span></p><p style="p_font2"><span style="ds_blue ps_boxedblack">Ψψ, Ωω, Ώώ, Αα, Άά, Ββ, Γγ, Δδ, Εε, Έέ,</span></p></div>
<div xml:id="sub9" region="R1" begin="10:00:27.000" end="10:00:28.000" style="ds_outlineblack"><p style="dp_end p_font2"><span style="ds_magenta ps_boxedblack">Ζζ, Ηη, Ήή, Θθ, Ιι, Ίί, Ϊϊ, Κκ, Λλ, Μμ,</span></p><p style="dp_end p_font2"><span style="ds_cyan ps_boxedblack">Νν, Ξξ, Οο, Όό, Ππ, Ρρ, Σσ, Ττ, Υυ, Ύύ,</span></p></div>
<div xml:id="sub10" region="R2" begin="10:00:29.000" end="10:00:30.000" style="ds_outlineblack"><p style="dp_start p_font2"><span style="s_italic ps_boxedblack">Αα, Άά, Ββ, Γγ, Δδ, Εε, Έέ, Ζζ, Ηη, Ήή,</span></p></div>
<div xml:id="sub11" region="R2" begin="10:00:31.000" end="10:00:32.000" style="ds_outlineblack"><p style="p_font2"><span style="s_italic ps_boxedblack">Θθ, Ιι, Ίί, Ϊϊ, Κκ, Λλ, Μμ, Νν, Ξξ, Οο,</span></p></div>
<div xml:id="sub12" region="R2" begin="10:00:33.000" end="10:00:34.000" style="ds_outlineblack"><p style="dp_end p_font2"><span style="s_italic ps_boxedblack">Όό, Ππ, Ρρ, Σσ, Ττ, Υυ, Ύύ, Ϋϋ, Φφ, Χχ,</span></p></div>
<div xml:id="sub13" region="R0" begin="10:00:35.000" end="10:00:36.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Αα, Άά, Ββ, Γγ, Δδ,</span></p></div>
<div xml:id="sub14" region="R3" begin="10:00:37.000" end="10:00:38.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Εε, Έέ, Ζζ, Ηη, Ήή,</span></p></div>
<div xml:id="sub15" region="R1" begin="10:00:39.000" end="10:00:40.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Θθ, Ιι, Ίί, Ϊϊ, Κκ,</span></p></div>
<div xml:id="sub16" region="R4" begin="10:00:41.000" end="10:00:42.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Λλ, Μμ, Νν, Ξξ, Οο,</span></p></div>
<div xml:id="sub17" region="R2" begin="10:00:43.000" end="10:00:44.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Όό, Ππ, Ρρ, Σσ, Ττ,</span></p></div>
<div xml:id="sub18" region="R5" begin="10:00:45.040" end="10:00:46.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Υυ, Ύύ, Ϋϋ, Φφ, Χχ,</span></p></div>
<div xml:id="sub19" region="R6" begin="10:00:47.000" end="10:00:48.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Ψψ, Ωω, Ώώ, Αα, Άά,</span></p></div>
<div xml:id="sub20" region="R7" begin="10:00:49.040" end="10:00:50.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Ββ, Γγ, Δδ, Εε, Έέ,</span></p></div>
<div xml:id="sub21" region="R8" begin="10:00:51.000" end="10:00:52.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Ζζ, Ηη, Ήή, Θθ, Ιι,</span></p></div>
<div xml:id="sub22" region="R9" begin="10:00:53.000" end="10:00:54.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Ίί, Ϊϊ, Κκ, Λλ, Μμ,</span></p></div>
<div xml:id="sub23" region="R10" begin="10:00:55.000" end="10:00:56.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Νν, Ξξ, Οο, Όό, Ππ,</span></p></div>
<div xml:id="sub24" region="R11" begin="10:00:57.000" end="10:00:58.000" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Ρρ, Σσ, Ττ, Υυ, Ύύ,</span></p></div>
<div xml:id="sub25" region="R11" begin="10:00:59.000" end="10:01:00.000" style="ds_outlineblack"><p style="dp_start p_font2"><span style="ps_boxedblack">Ζζ, Ηη, Ήή, Θθ, Ιι, Ίί, Ϊϊ, Κκ, Λλ, Μμ,</span></p><p style="dp_start p_font2"><span style="ps_boxedblack">Νν, Ξξ, Οο, Όό, Ππ, Ρρ, Σσ, Ττ, Υυ, Ύύ,</span></p></div>
<div xml:id="sub26" region="R11" begin="10:01:00.960" end="10:01:01.960" style="ds_outlineblack"><p style="p_font2"><span style="ps_boxedblack">Όό, Ππ, Ρρ, Σσ, Ττ, Υυ, Ύύ, Ϋϋ, Φφ, Χχ,</span></p><p style="p_font2"><span style="ps_boxedblack">Ψψ, Ωω, Ώώ, Αα, Άά, Ββ, Γγ, Δδ, Εε, Έέ,</span></p></div>
<div xml:id="sub27" region="R11" begin="10:01:03.040" end="10:01:04.000" style="ds_outlineblack"><p style="dp_end p_font2"><span style="ps_boxedblack">Αα, Άά, Ββ, Γγ, Δδ, Εε, Έέ, Ζζ, Ηη, Ήή,</span></p><p style="dp_end p_font2"><span style="ps_boxedblack">Θθ, Ιι, Ίί, Ϊϊ, Κκ, Λλ, Μμ, Νν, Ξξ, Οο,</span></p></div>
</body>
</tt>
```




