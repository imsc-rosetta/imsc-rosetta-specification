# General XML

### Note the use of xml:space="preserve"

<details><summary>tt xml:space="preserve"</summary>

This is essential because to represent existing formats well, we MUST preserve spaces in the subtitle.  Hence ALL whitespace inside every `<p>` is intended for display.

Although `xml:space="normal"` Seems to resolve the issue of prettifying `<p>`, in actuality a prettified `<p>` with xml:space="normal" does not display boxing correctly (because and CRs in the XML are collapsed to a single space, and this space can fall outside of the boxed `<span>` element, so causing an unboxed space in the output between spans).

It is irrelevant for the rest of the file, and hence we state it as an attribute of the tt element, and allow it to apply to the whole file.

The result of specifying `xml:space="preserve"` is that IF a `<p>` gets prettified somehow (e.g. manual edit, or XML processor which does not understand this constraint), subtitles WILL present badly.  But this should be obvious for every subtitle and so easily picked up in process qualification.

examples:

In order to display well, a p cannot contain any space outside of span elements, e.g.:
```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="dp_al_start">
  <p style="p_font2"><span>two lines</span></p>
  <p style="p_font2"><span>left bottom</span></p>
</div>
```

The below will display with all the extra spacing and CRs disturbing the line positions:

*** NOTE: Bad Formatting example - do not copy! ***

```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="dp_al_start">
  <p style="p_font2">
    <span>two lines</span>
  </p>
  <p style="p_font2">
    <span>left bottom</span>
  </p>
</div>
```

Spacing before and after p elements will not compromise presentation.
</details>

### Namespaces
  
<details><summary>Use of namespace prefixes</summary>
    
Namespace prefix processing is a large and unnecessary overhead when using common simple XML parsers.  By enforcing namespace prefixes, and a fixed set of namespaces, we simplify the parsing significantly.

If you have an XML processor which does not retain the define XML Namespace prefixes, please normalise the file afterwards to restore them.
    
</details>

### Div as a subtitle representation
  
<details><summary>Why choose to use div, rather than one or more p?</summary>

  Imsc-Rosetta has it's main target as translation subtitling, and as such should be able to represent all the common presentations of translation subtitles.
  
  By adopting div as the 'subtitle' element, we impose a stringent structure of one 'page' per timed presentation, quite similar to an ISD (the result of parsing a TTML for presentation).  By limiting `begin` and `end` to be on div, and imposing non-overlap, timing parsing becomes trivial.  By imposing that a div must contain zero or more p only (plus a non-display metadata element if required), and that p must contain zero or more span elements, and text must be wrapped in span, parsing the structure is far simpler than allowing the variety of constructs that TTML (and IMSC) allows.
  
  This CAN be done by using a single `<p>` per subtitle, but that removes the ability to use both left and right alignment in a subtitle, which is a feature of existing line based subtitle formats. 
  
  We are not trying to be compatible with multiple forms of imsc - we are specifically making a version which has a very restricted form, but is fully IMSC compliant. 
    
</details>

# Representing things that TTML cannot

<details><summary>File features/intent which cannot be transmitted via TTML easily</summary>

  The use of TTML makes the representation of some features of existing files difficult.
  
  One example of this is background color, and it's use to color outlines.
  
  In TTML, you can't easily represent a background color intent without explicitly qualifying it's use.  e.g. you can have a colored box by setting backgroundColor on span, but if you want it to apply to outline, then you have to 'say' this completely differently.  And if the original file did not explicitly state outline or boxing, you can't state a TTML background color without guessing at it's purpose.
  
  Hence we end up with use of known style names which represent concepts rather than actual styles.  e.g.:
  
  `<style xml:id="ds_nonered"/>`
  
  has no style associated with it, and yet imparts meaning to the file.  (the meaning being that if a span with this style name attached was to be subsequently boxed, it should have a red background).
  
  This concept is a major difference between Imsc-Rosetta and previous TTML profiles - we don't ONLY represent a file to produce a particular visual output, but rather attempt to retain the intent of the original file, or to capture intent when preparing a file, such that it could subsequently be used to convert TO an older existing form.
  
  *Note: this also means that these 'features' will get lost if the files is interpreted as 'normal' ttml, and then re-created from raw data.*
      
</details>

<details><summary>'defaults'</summary>

  Certain of the styles in Imsc-Rosetta are defined to be always present.
  
  These include _r_default, _d_default
  
  Specifically these can carry some information about how the file is intended to be manipulated.  _r_default carries the origin and extent of a 'default' region, as well as fontSize (in rh) and lineHeight.  These values are specifically to help any processor calculate line quantization (i.e. know WHERE lines are intended to be positioned on the screen).  Specifically, round(regionHeight/fontSize*lineHeight) should be used as a count of viable positions, and this value used to generate viable regions if moving subtitles vertically.  Quantization of line positions is used to keep the number of regions in control.  Rounding of region extent and origin to 0.1% should be enough to avoid ending up with too many regions.
  
  Note that line quantization does NOT mean that you must use the default fontSize, it merely means that we can know where regions should be put.  The actual fontSize can be modified by use of p_font1 and p_font2, where an Imsc-Rosetta writer can change the fontSize (as a percentage of the default).
      
</details>


# Style usage

<details><summary>constant and changeable styles</summary>

  In Imsc-Rosetta, ALL style is referenced.  i.e. attributes from the tts: namespace may ONLY be on a style element containing a xml:id from the list of style names allowed in Imsc-Rosetta, and style elements are only allowed as children of styling.  By having tightly specified style naming and usage, Imsc-Rosetta files may be parsed by simple parsers without complex style processing normally associated with TTML.
  
  In Imsc-Rosetta, certain named style content is constant - i.e. you may not change it.
  
  These include d_default, r_default, s_italic, s_bold, s_underline, ds_al_start, ds_al_end, d_forced
  
  Other named styles may be changed by the file writer.
  
  These include _d_default _r_default, p_font1, p_font2, s_fg_xxxx, dp_boxedxxxx, dp_ghostboxedxxxx, dp_outlinexxxx, dp_dropxxxx
  
  _r_quantisationregion is used to define the default subtitle area, and line quantisation.  (e.g. a height of 80%, fontSize of 0.5666rh, lineHeight of 125%, when combined hints to 12 'rows', or 11 positions which a region edge could adopt).
  
  _r_default is used to define the actual base font size.

  p_font1 and p_font2 can be used to select a font family, size, and lineHeight, for use with up to two fonts on a line by line basis.
  
  Styles which include color may be changed to remap color only.  However, be aware that many parsers will ignore the content, and rely solely on the name.  (i.e. don't remap red to blue, and expect the mapping to occur on a teletext output.).  Remapping of colors is intended for subtle changes where the Imsc-Rosetta file may be parsed directly by a fully IMSC compliant parser - e.g. to reduce full white intensity, or use a slightly different shade of yellow.
   
  The intent here is, as always, to simplify parsing, and remove ambiguity, whilst maintaining full IMSC compatibility.
  
  Some style is still complex (mainly around background color, because of the way it is specified in TTML), but most style is simple.

</details>

