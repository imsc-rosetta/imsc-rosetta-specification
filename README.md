# Imsc-Rosetta

This repo represents the base specification and description of imsc-rosetta - a practical Subtitle File Format fully compatible with [IMSC1.2](https://www.w3.org/TR/ttml-imsc1.2/).

The general intent is to have a Subtitle Format which is fully IMSC compliant (and so [TTML 2](https://www.w3.org/TR/2018/REC-ttml2-20181108/) compliant), whilst being specifically easy to parse, and easy to create, without detailed knowledge of XML and the specs that IMSC/TTML are based on.

Imsc-rosetta has been developed to represent the abilities of various existing proprietary subtitle file formats well, specifically those used in broadcast today, allowing reliable reversible conversion to and from those formats.  It is not necessarily the most efficient format for emission (e.g. although fully IMSC compatible, there are more efficient forms of IMSC for representing subtitles for OTT use).

To this end, the use of TTML constructs is highly restricted so that the exact form of the file may be specified in full without ambiguity.

## why Rosetta?

The development of this file format is a collaboration between several broadcasters and suppliers; so the name is not intended to connect the specification with any specific organisation.

The [Rosetta Stone](https://en.wikipedia.org/wiki/Rosetta_Stone) was the key to the interpretation of ancient Egyptian scripts.  Imsc-rosetta is the key to conversion of existing proprietary subtitle formats into a useful archive and manipulation format, and indeed the key to conversion between those existing formats.

## main points

***imsc-rosetta is a Subtitle File Format, not a generic flavour of TTML.  It is fully IMSC/TTML compliant***

Each *subtitle* is represented as a `<div>`, and there is only one `<div>` per subtitle.  Timing is on `<div>`, specified only in HH:MM:SS.TTT from midnight - no other time styles are allowed, and time is not allowed on any other element.
  
Regions extend to at least three edges being against the edge of a static subtitle presentation area.  The fourth edge is used to place the subtitle vertically (or horizontally in the case of vertical text).  This allows the subtitle font size to be changed without changing the region.  For horizontal subtitles, the regions are always the same width (i.e. left and width of all regions are static).  Regions are expected to be shared between subtitles - e.g. for most existing subtitle formats, you could expect a maximum of maybe 12 regions based on the ability to position subtitles on a line by line basis.
  
Subtitles are represented by one or more `<p>` elements within the base `<div>` element.  `<span><br/></span>` is allowed as a line break, but imsc-rosetta also allows for multiple `<p>` elements within the `<div>` in order to accurately represent subtitles with line alignments which cannot be reproduced within a single `<p>`.

Each `<p>` may contain zero or more `<span>` elements and `<span><br/></span>` elements.  A `<p>` may not contain text directly - any text must be wrapped in `<span>`.
  
`<span>` elements may only contain text (i.e. no nesting of spans), except in Japanese where nested spans are required to represent Rubies.  Where nested spans are used, no `<span>` may contain both text and other `<span>` elements.  Only one level of span nesting is allowed.

For archival, Subtitle times (begin and end attributes on `<div>`) must be present, and must not overlap.  `<div>` must appear in presentation order (i.e. will appear in the file in the order of their `begin` attribute).

*(note that the format may be used during subtitle editing, and in this case, begin and end may be absent or invalid whilst the file is being edited).*

All styling is referential, and style ids used are fixed.  Many styles are *constant*.  (i.e. you may not put local style anywhere in `<body>`, and all style reference ids used are pre-defined by the specification).

## Subtitling features supported

Many TTML implementations do not implement features of subtitles which have been supported by extant proprietary formats for many years.  TTML itself is capable of supporting these features, but in order to do so, a full understanding of TTML and it's associated standards is required.  Gaining an understanding of TTML and the associated specifications is both difficult, and fraught with the probability of misinterpretation.

imsc-rosetta addresses this by specifically supporting various features not commonly used in TTML, and explicitly documenting how they are represented in imsc-rosetta in an IMSC compatible way.

### alignment/justification

The format supports both alignment inside a single `<p>`, using ebutts:multiRowAlign to support advanced justification and alignment, but also the use of multiple `<p>` elements to represent subtitles where lines have alignments not supported by a single `<p>` subtitle (e.g. one line left, one line right).

### boxing

The format defines the ways to achieve boxed subtitles with a presentation consummate to a broadcast subtitle.  Specifically it uses ebutts:linePadding to ensure that boxed lines have some space on the end.

Boxing forms supported include Ghost box (semi-transparent boxing of text only), Boxed (solid boxing of text only), Ghost Stripe (semi transparent boxing which occupies the full width of each line), Solid Stripe (solid boxing which occupies the full width of each line).

It also supports background colours on boxing.

### Outline/Dropshadow

The format supports outlined text, and stores the data noting that text was intended to be dropshadow (although IMSC does not support this).  It also supports background colour for outlined/dropshadow text and is capable of retaining background color information even when this would not be displayed by IMSC.

### vertical position

The format defines a mechanism by which line based editors can quantise position to minimise region proliferation which it comes to vertically positioning horizontal text.  

It also defines regions in such a way that a change of font size does not require a complete change of region usage - regions are defined such that subtitles can easily grow from a specific anchor point.

## XML and it's usage

### For developers:

imsc-rosetta is specified in such a way to make it easy to develop against.  For example, by defining that `<br/>` must be wrapped in `<span>`, the most commonly used Javascript XML parser can both parse and then serialise an imsc-rosetta document in a few lines of code.  This ability is contrary to trying to parse any generic TTML file, where it is almost impossible to round-trip a file (parse it, process it, write it) in commonly used simple parsers.

The use of defined style names, and being explicit about how certain visual styling is achieved makes the learning curve for developing with imsc-rosetta much shorter than learning how to use raw IMSC or TTML.

The definition of namespaces used and specification of namespace prefixes also simplifies and shortens the learning period for those less familiar with the real details of XML.

