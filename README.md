# Rosetta-imsc
This repo represents the base specification and description of rosetta-imsc - a practical cut down [IMSC1.2](https://www.w3.org/TR/ttml-imsc1.2/) compatible subtitle format

At version 0.0.1, rosetta-imsc will be suitable for horizontal translation subtitles in all languages, with the exception of advanced Japanese (i.e. no rubies yet).

The general intent is to have a subtitle format which is fully IMSC complient (and so [TTML 2](https://www.w3.org/TR/2018/REC-ttml2-20181108/) complient), whilst being specifically easy to parse, and easy to create, without detailed knowledge of XML and the specs that IMSC/TTML are based on.

Rosetta-imsc has been developed to represent the abilities of various existing proprietary subtitle file formats well, specifically those used in broadcast today, allowing reliable reverible conversion to and from those formats.  It is not necessarily the most efficient format for emission (e.g. although fully IMSC compatible, there are more efficient forms of IMSC for representing subtitles for OTT use).

To this end, the use of TTML constructs is highly restricted so that the exact form of the file may be specified in full without ambiguity.

## why Rosetta?
The development of this file format is a collaboration between several broadcasters and suppliers; so the name is not intended to connect the specification with any specific organisation.

The [Rosetta Stone](https://en.wikipedia.org/wiki/Rosetta_Stone) was the key to the interpretation of anchient Egyptian scripts.  Rosetta-imsc is the key to conversion of existing proprietary subtitle formats into a useful archive and manipulatioon format, and indeed the key to conversion between those existing formats.

## main points
Each *subtitle* is represented as a `<div>`, and there is only one `<div>` per subtitle.
  
Regions extend to at least three edges being against the edge of a static subtitle presentation area.  The fourth edge is used to place the subtitle vertically.  This allows the subtitle font size to be changed without changing the region.  For horizontal subtitles, the regions are always the same width (i.e. left and width of all regions are static).  Regions are expected to be shared between subtitles - e.g. for most existing subtitle formats, you could expect a maximum of maybe 12 regions based on the ability to position subtitles on a line by line basis.
  
Each *subtitle line* is represented as a `<p>` element.  `<br>` is not allowed.
  
Each line (`<p>`) may contain zero or more `<span>` elements.  A `<p>` may not contains text directly - any text must be wrapped in `<span>`.
  
`<span>` elements may only contain text (i.e. no nesting of spans).

*(Note: for later versions, nested spans may be specifically allowed, but only for text requiring rubies.  In this case, text may only be contained within the leaf spans)*

For archival, Subtitle times (begin and end attributes on `<div>`) must be present, and must not overlap.  `<div>` must appear in presentation order.

*(note that the format may be used during subtitle editing, and in this case, begin and end may be absent or invalid whilst the file is being edited).*

All styling is referencial, and style ids used are fixed.  Many styles are *constant*.  (i.e. you may not put local style anywhere in `<body>`, and all style reference ids used are pre-defined by the specification).

## XML parsing
To simplify the XML parsing of rosetta-imsc, in general terms the document nodes only contain one child node type.  This enables the use of simple parsers which need not retain the order of different node types, only the order of same node types.  The only nodes where this is not the case are `<tt>` - which must contain exactly one `<head>` and exactly one `<body>` element, and `<head>` - which must contain one `<metadata>`, one `<styling>`, one `<layout>` element, in that order.

Namespaces used and associated namespace prefixes are fixed (defined in the spec) and set only on the `<tt>` element, again to simplify parsing and writing - no namspace processing is required, and all files will look similar.  *i.e. ALL elements will always have the same namespace prefix as in other rosetta-imsc files.*

Be aware that certain XML processing could change namespace prefixes, so if you have a process which does this, the output may not be a 'Rosetta-imsc' file until you normalise the file in some way.
