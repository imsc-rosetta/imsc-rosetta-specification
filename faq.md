# General XML

### Note the use of xml:space="preserve"

<details><summary>tt xml:space="preserve"</summary>

This is essential because to represent existing formats well, we MUST preserve spaces in the subtitle.  Hence ALL whitespace inside every div is intended for display.

It is irrelevant for the rest of the file, and hence we state it as an attribute of the tt element, and allow it to apply to the whole file.

examples:

In order to display well, a div cannot contain any space outside of span elements, e.g.:
```
<div xml:id="5" region="R0" begin="01:00:24.240" end="01:00:28.240" style="dp_al_start"><p style="p_font2"><span>two lines</span></p><p style="p_font2"><span>left bottom</span></p></div>
```

The below div will display with all the extra spacing and CRs disturbing the line positions:
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

Spacing before and after div elements should not compromise presentation.
</details>

### Namespaces
  
<details><summary>Use of namespace prefixes</summary>
    
Namespace prefix processing is a large and unneccessary overhead when using common simple XML parsers.  By enforcing namespace prefixes, and a fixed set of namespaces, we simplify the parsing significantly.
    
</details>

### Div as a subtitle representation
  
<details><summary>Why choose to use div, rather than one or more p?</summary>

  Imsc-Rosetta has it's main target as translation subtitling, and as such should be able to represent all the common presentations of translation subtitles.
  
  By adopting div as the 'subtitle' element, we impose a stringent structure of one 'page' per timed presentation, quite similar to an ISD (the result of parsing a TTML for presentation).  By limiting `begin` and `end` to be on div, and imposing non-overlap, timing parsing becomes trivial.  By imposing that a div must contain zero or more p only (plus a non-display metadata element if required), and that p must contain zero or more span elements, and text must be wrapped in span, parsing the structure is far simpler than allowing the variety of constructs that TTML (and IMSC) allows.
  
  Note that nested spans does not break the parsing simplicity necessarily, but further clarification is required on this point.
  
  In contrast, p based TTML does not allow for different alignment per row.  Use of `<br/>` make parsing much more difficult (because the base XML parser can't just group all elements of one type - it must observe the order of differently named elements, adding two levels to any tree created).  Multiple p with the same times also  makes parsing more difficult - you have determine if there is more than one p, and then take the multiple elements.
  
  We are not trying to be compatible with multiple forms of imsc - we are specifically making a version which has a very restricted form, but is fully IMSC complient. 
    
</details>

# Representing things that TTML cannot

<details><summary>File features/intent which cannot be transmitted via TTML easily</summary>

  The use of TTML makes the representaiton of some features of existing files difficult.
  
  One example of this is background color, and it's use to color outlines.
  
  In TTML, you can't easily represent a background color intent without explicitly qualifying it's use.  e.g. you can have a colored box by setting backgroundColor on span, but if you want it to apply to outline, then you have to 'say' this completely differently.  And if the original file did not explicitly state outline or boxing, you can't state a TTML background color without guessing at it's purpose.
  
  Hence we end up with use of known style names which represent concepts rather than actual styles.  e.g.:
  
  `<style xml:id="ds_nonered"/>`
  
  has no style associated with it, and yet imparts meaning to the file.  (the meaning being that if a span with this style name attached was to be subsequently boxed, it should have a red background).
  
  This concept is a major difference between Imsc-Rosetta and previous TTML profiles - we don't ONLY represent a file to produce a particular visual output, but rather attempt to retain the intent of the original file, or to capture intent when preparing a file, such that it could subsequently be used to convert TO an older existing form.
      
</details>

<details><summary>'defaults'</summary>

  Certian of the styles in Imsc-Rosetta are defined to be always present.
  
  These include _r_default, _p_default, _s_default and _d_default
  
  Specifically these can carry some information about how the file is intended to be manipulated.  _r_default carries the origin and extent of a 'default' region, as well as fontSize (in rh) and lineHeight.  These values are specifically to help any processor calculate line quantization (i.e. know WHERE lines are intended to be positioned in the region).  Specifically, round(regionHeight/fontSize*lineHeight) should be used as a count of viable positions, and this value used to generate viable regions if moving subtitles vertically.  Quantization of line positions is used to keep the number of regions in control.  Rounding of region extent and origin to 0.1% should be enough to avoid endign up with too many regions.
  
  Note that line quntization does NOT mean that you must use the default fontSize, it meerly means that we can know where regions should be put.  The actual fontSize can be modified by use of p_font1 and p_font2, where an Imsc-Rosetta writer can change the fontSize (as a percentage of the default).
      
</details>


# Style usage

<details><summary>constant and changeable styles</summary>

  In Imsc-Rosetta, ALL style is referenced.  i.e. attributes from the tts: namespace may ONLY be on a style element containing a xml:id from the list of style names allowed in Imsc-Rosetta, and style elements are only allowed as children of styling.  By having tightly specified style naming and usage, Imsc-Rosetta files may be parsed by simple parsers without complex style processing normally associated with TTML.
  
  In Imsc-Rosetta, certain named style content is constant - i.e. you may not change it.
  
  These include r_region, s_italic, s_bold, s_underline, ds_al_start, ds_al_end, d_forced
  
  Other named styles may be changed by the file writer.
  
  These include _r_default, p_font1, p_font2, ds_fg_xxxx, dp_boxedxxxx, dp_ghostboxedxxxx, dp_outlinexxxx, dp_dropxxxx
  
  _r_default is used to define the default subtitle area, and line quantisztion, plus the initial font size.  (e.g. a height of 80%, fontSize of 0.5666rh, lineHeight of 125%, when combined hints to 12 'rows', or 11 positions which a region edge could adopt).
  
  p_font1 and p_font2 can be used to select a font family, size, and lineHeight, for use with up to two fonts on a line by line basis.
  
  Styles which include color may be changed to remap color only.  However, be aware that many parsers will ignore the content, and rely solely on the name.  (i.e. don't remap red to blue, and expect the mapping to occur on a teletext output.).  Remapping of colors is intended for subtle changes where the Imsc-Rosetta file may be parsed directly by a fully IMSC complient parser - e.g. to reduce full white intensity, or use a slightly different shade of yellow.
   
  The intent here is, as always, to simplify parsing, and remove abiguity, whilst maintaining full IMSC compatibility.
  
  Some style is still complex (mainly around background color, because of the way it is specified in TTML), but most style is simple.

</details>

