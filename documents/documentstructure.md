# IMSC Rosetta Document Structure

This describes the structure of an IMSC Rosetta file.

The file must start with the XML header containing the following attributes

xml version="1.0"

encoding="UTF-8"

standalone="yes"

## Allowed elements

### `<tt>`

`<tt>` contains only the specified attributes. 

<details><summary>expand for attributes of tt</summary>

#### namespacing conventions:

The `tt` element will contain the following explicit namespace definitions as attributes:

```
 xmlns="http://www.w3.org/ns/ttml"
 xmlns:ttm="http://www.w3.org/ns/ttml#metadata"
 xmlns:tts="http://www.w3.org/ns/ttml#styling"
 xmlns:ttp="http://www.w3.org/ns/ttml#parameter"
 xmlns:xml="http://www.w3.org/XML/1998/namespace"
 xmlns:ebutts="urn:ebu:tt:style"
 xmlns:itts="http://www.w3.org/ns/ttml/profile/imsc1#styling"
 xmlns:rosetta="https://github.com/imsc-rosetta/specification"
```

Namespace prefixes shall be as above.
 
Additional namespaces may be used, but may not be recognised by parsers.

#### required attributes:

```
ttp:timeBase="media"
ttp:cellResolution="30 15"
xml:space="preserve"
xml:lang="(see below)"
```

#### Note IMSC only allows for ttp:timeBase="media"

#### The Cell Resolution must be expliclity delcared (as the default for ttml) ttp:cellResolution="30 15"

#### xml:space="preserve" is required for correct text presentation

#### Frame Rate:

`ttp:framerate` and `ttp:frameRateMultiplier` must be set.  
 
Note that these values are not required to parse the file, but shall set indicative of the framerate of the media file used to prepare the subtitles.

For 25 FPS:
```
ttp:frameRate="25"
ttp:frameRateMultiplier="1 1"
```

For 29.97:
```
ttp:frameRate="30"
ttp:frameRateMultiplier="1000 1001"
```

For 23.976:
```
ttp:frameRate="24"
ttp:frameRateMultiplier="1000 1001"
```

other framerates are allowed.
 
#### The use of language codes is dependant on the broadcaster and could include bcp47, ISO-639 or propriatary codes.  The code shall be specified in `xml:lang` in `tt`
 
</details>

`<tt>` contains the following elements:

Exactly one `<head>` followed by exactly one `<body>`.

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

`xml:id` `tts:origin` `tts:extent` `tts:displayAlign` `style="r_default"`

For Japanese Vertical text, the additional style r_vertical will be added.  i.e. the region will contain `style="r_default r_vertical"`

`<region>` elements will not have any content, and should be represented as closed elements, 

e.g. 

`<region xml:id="R0" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" style="r_default"/>`

e.g. Japanese vertical region:

`<region xml:id="R0" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" style="r_default r_vertical"/>`

### `<body>`
`<body>` must have no attributes. `<body>` contains the following elements:

One or more `<div>`.

### `<div>`
`<div>` elements shall contain the following attributes:

`xml:id` `region` `begin` `end` `style`

<details><summary>expand for attibutes of div</summary>
 
 `xml:id` shall be unique in the file.  e.g. `xml:id="SUB1"`
 
 `region` shall reference the xml:id of a `region` element.  e.g. `region="R1"`
 
 `style` shall reference one or more xml:id of `style` elements.  e.g. `style="d_default"`.  The referenced styles shall conform to the rules in [styles.md](styles.md) - i.e. be appropriate for inclusion in `div`, and `d_default` must be present
 
 `begin` shall be a time in HH:MM:SS.TTT where HH, MM, SS contain 2 digits, TTT contains three digits.  The time represented will be the real-time equivalent of the timecode of the time the subtitle should appear on the screen, relative to the timecode of the original media.

 `end` shall be a time in HH:MM:SS.TTT where HH, MM, SS contain 2 digits, TTT contains three digits.  The time represented will be the real-time equivalent of the timecode of the time the subtitle should dissapear from the screen (i.e. the subtitle will NOT be visible at this time), relative to the timecode of the original media.

</details>

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

`style` shall reference zero or more xml:id of `style` elements.  e.g. `style="p_font2 p_rb_res_outside"`.  The referenced styles shall conform to the rules in [styles.md](styles.md) - i.e. be appropriate for inclusion in `p`. The `style` attribute on `<p>` must contain either `p_font1` or `p_font2`

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

See the samples in [the samples folder](../samples)

