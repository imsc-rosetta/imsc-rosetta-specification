# Rosetta-imsc
This repo represents the base specification and description of rosetta-imsc - a practical cut down IMSC compatible subtitle format

At version 0.0.1, rosetta-imsc will be suitable for horizontal translation subtitles in all languages, with the exception of advanced Japanese (i.e. no rubies yet).

The general intent is to have a subtitle format which is fully IMSC complient (and so TTML 2 complient), whilst being specifically easy to parse, and easy to create, without detailed knowledge of XML and the specs that IMSC/TTML are based on.

Rosetta-imsc has been developed to represent the abilities of various existing proprietary subtitle file formats well, specifically those used in broadcast today, allowing reliable reverible conversion to and from those formats.  It is not necessarily the most efficient format for emission (e.g. although fully IMSC compatible, there are more efficient forms of IMSC for representing subtitles for OTT use).

To this end, the use of TTML constructs is highly restricted so that the exact form of the file may be specified in full without ambiguity.

All styling is referenced, and style names used are fixed.  Many styles are constant.

## why Rosetta?
The development of this file format is a collaboration between several broadcasters and suppliers; so the name is not intended to connect the developement with any specific organisation.

The [Rosetta Stone](https://en.wikipedia.org/wiki/Rosetta_Stone) was the key to the interpretation of anchient Egyptian scripts.  Rosetta-imsc is the key to conversion of existing proprietary subtitle formats into a useful archive and manipulatioon format, and indeed to conversion between those existing formats.

## main points
Each subtitle is represented as a `<div>`, and there is only one `<div>` per subtitle.
  
Regions extend to at least three edges being against the edge of a static subtitle presentation area.  The fourth edge is used to place the subtitle vertically.  This allows the subtitle font size to be changed without changing the region.  For horizontal subtitles, the regions are always the same width (i.e. left and width of all regions are static).  Regions are expected to be shared between subtitles - e.g. for most existing subtitle formats, you could expect a maximum of maybe 12 regions based on the ability to subtitles on a line by line basis.
  
Each subtitle line is represented as a `<p>` element.  `<br>` is not allowed.
  
Each line may contain one or more `<span>` elements.
  
`<span>` elements may only contain text (i.e. no nexting of spans)
  
