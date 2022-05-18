# Japanese Support

## use of `<br/>`

imsc-rosetta supports both single `<p>` with `<br/>` and multiple `<p>` presentations for multi-line subtitles.

Because of the possible use of Rubies, and to simplify this, when using imsc-rosetta for Japanese, use the single `<p>` with `<br/>` for multi line subtitles.  This simplifies the use opf rubies by making available the TTML styles specifying 'outside' for the simplification of ruby and emphasis position.

## Vertical subtitles

`r_vertical` (This equates to writingMode="tbrl")

Vertical subtitles are represented by applying the style r_vertical to the region into which the subtitle is rendered.

When using vertical subtitles, the regions should be full height, with variable left or right edges (either right or left or both will be against the maximal region extent horizontally).

## Rubies

Rubies for japanese are supported through the use of nested spans with ruby specific styles attached.

### Ruby Specific Styles:

For subtitles, generally ruby presentation is accepted as preferred above text for a single line, or above the top line, and below the bottom line for two line subtitles.

When Rubies are in use in a file, it is preferred that the main text of the subtitle does not move when rubies are present compared to when they are not present.

With the above two observations in mind, imsc-rosetta implements the following style names which should be used:

For ensuring subtitles do not move when rubies are absent/present, use p_rb_res_outside on all `<p>` elements in a file which uses rubies.

`p_rb_res_outside` (equates to tts:rubyReserve="outside")

The default position of Rubies is tts:rubyAlign="center", the only other permitted value in IMSC is tts:rubyAlign="spaceAround".

To enhance text with a Ruby, you must construct three spans.  The outer `<span>` must reference either `s_rb_algn_center` or `s_rb_algn_around`, as this enables the span as the ruby container.  The container span must contain two further spans, one referencing the style `s_rb_b` and containing the base text, and the subsequent span referencing `s_rb_t` and containing the actual text of the ruby.  The container span must NOT contain any text itself.

`s_rb_algn_center` (equates to tts:ruby="container" to tts:rubyAlign="center" tts:rubyPosition="outside")
`s_rb_algn_around` (equates to tts:ruby="container" to tts:rubyAlign="spaceAround" tts:rubyPosition="outside")

`s_rb_b` (equates to tts:ruby="base")
`s_rb_t` (equates to tts:ruby="text")

Ruby position is always 'outside'

## other ideographic specific styles:

### textCombine

Use the `s_combine` style on a span which should be displayed horizontal when in vertical presentation mode.

This feature is generally used to make short numbers appear horizontally within a vertical line.

s_combine (equates to tts:textCombine="all")

### text shear

text shear of 16.67% may be applied using `dps_shear` on div, p or span

dps_shear tts:shear="16.67%"

(note the use of tts:shear, not tts:fontShear)

(note: this should ONLY be used for Japanese of other ideographic langages.  For other languages, you may use `s_italic`)

### text emphasis (Bouten)

This places emphasis on characters.

The following defined ephasis styles may be used.

Emphasis color is not supported.

If you use BOTH emphasis and Rubies on the same span, be very aware of what the renderer is capable of before expecting results.

```
s_emf_fco tts:textEmphasis="filled circle outside"
s_emf_fdo tts:textEmphasis="filled dot outside"
s_emf_fso tts:textEmphasis="filled sesame outside"
s_emf_oco tts:textEmphasis="open circle outside"
s_emf_odo tts:textEmphasis="open dot outside"
s_emf_oso tts:textEmphasis="open sesame outside"
```

## example Ruby use:

drawing from the IMSC tests repository here: https://github.com/w3c/imsc-tests

imsc-rosetta examples would be:



