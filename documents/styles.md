# Style names 

Style names are fixed in imsc-rosetta for simplicity of use and understanding.

Some styles are fixed in terms of content and others are adjustable, either to represent file defaults, or to represent specific requirements.

## All styles

It is expected that only the used set of styles be present in a file, but it is not incorrect to include more than are used.

The following is the maximal style name set, and their default values:

```
 <style xml:id="r_default" tts:overflow="visible" tts:backgroundColor="#00000000" tts:showBackground="whenActive" tts:fontStyle="normal" tts:fontWeight="normal" tts:fontFamily="proportionalSansSerif" tts:textAlign="center" tts:wrapOption="noWrap" style="_r_default" />
 <style xml:id="r_vertical" tts:writingMode="tbrl" style="_r_vertical"/>
 
 <style xml:id="d_default" style="_d_default"/>
 <style xml:id="d_fillgap" itts:fillLineGap="true" />
 <style xml:id="d_forced" itts:forcedDisplay="true"/>
 <style xml:id="d_outline" style="s_outlineblack"/>
 <style xml:id="d_drop" style="s_dropblack"/>
 
 <style xml:id="p_rtl" tts:direction="rtl"/>
 
 <style xml:id="p_al_start" ebutts:multiRowAlign="start" tts:textAlign="start"/>
 <style xml:id="p_al_end" ebutts:multiRowAlign="end" tts:textAlign="end"/>
 <style xml:id="p_al_center" ebutts:multiRowAlign="center" tts:textAlign="center"/>
 <style xml:id="p_al_start_center" ebutts:multiRowAlign="center" tts:textAlign="start"/>
 <style xml:id="p_al_start_end" ebutts:multiRowAlign="end" tts:textAlign="start"/>
 <style xml:id="p_al_end_start" ebutts:multiRowAlign="start" tts:textAlign="end"/>
 <style xml:id="p_al_end_center" ebutts:multiRowAlign="center" tts:textAlign="end"/>
 <style xml:id="p_al_center_start" ebutts:multiRowAlign="start" tts:textAlign="center"/>
 <style xml:id="p_al_center_end" ebutts:multiRowAlign="end" tts:textAlign="center"/>
 
 <style xml:id="p_font1" tts:fontFamily="proportionalSansSerif" tts:lineHeight="125%" tts:fontSize="100%"/>
 <style xml:id="p_font2" tts:fontFamily="proportionalSansSerif" tts:lineHeight="125%" tts:fontSize="100%"/>

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

 
 <style xml:id="s_italic" tts:fontStyle="italic"/>
 <style xml:id="s_bold" tts:fontWeight="bold"/>
 <style xml:id="s_underline" tts:textDecoration="underline"/>
 
 <style xml:id="s_fg_black" tts:color="#000000"/>
 <style xml:id="s_fg_red" tts:color="#FF0000"/>
 <style xml:id="s_fg_yellow" tts:color="#FFFF00"/>
 <style xml:id="s_fg_green" tts:color="#00FF00"/>
 <style xml:id="s_fg_cyan" tts:color="#00FFFF"/>
 <style xml:id="s_fg_blue" tts:color="#0000FF"/>
 <style xml:id="s_fg_magenta" tts:color="#FF00FF"/>
 <style xml:id="s_fg_white" tts:color="#FFFFFF"/>

 <style xml:id="s_outlineblack" tts:textOutline="#000000 0.05em"/>
 <style xml:id="s_outlinered" tts:textOutline="#FF0000 0.05em"/>
 <style xml:id="s_outlineyellow" tts:textOutline="#FFFF00 0.05em"/>
 <style xml:id="s_outlinegreen" tts:textOutline="#00FF00 0.05em"/>
 <style xml:id="s_outlinecyan" tts:textOutline="#00FFFF 0.05em"/>
 <style xml:id="s_outlineblue" tts:textOutline="#0000FF 0.05em"/>
 <style xml:id="s_outlinemagenta" tts:textOutline="#FF00FF 0.05em"/>
 <style xml:id="s_outlinewhite" tts:textOutline="#FFFFFF 0.05em"/>

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
 
 
 <style xml:id="p_rb_res_outside" tts:rubyReserve="outside"/>

 <style xml:id="p_shear" tts:shear="16.67%"/>
 
 <style xml:id="s_rb_b" tts:ruby="base"/>
 <style xml:id="s_rb_t" tts:ruby="text"/>
 
 <style xml:id="s_rb_algn_center" tts:ruby="container" tts:rubyAlign="center"/>
 <style xml:id="s_rb_algn_around" tts:ruby="container" tts:rubyAlign="spaceAround"/>
 
 <style xml:id="s_rb_posn_outside" tts:ruby="container" tts:rubyPosition="outside"/>
 
 <style xml:id="s_combine" tts:textCombine="all"/>
 
 <style xml:id="s_emf_fco" tts:textEmphasis="filled circle outside"/>
 <style xml:id="s_emf_fdo" tts:textEmphasis="filled dot outside"/>
 <style xml:id="s_emf_fso" tts:textEmphasis="filled sesame outside"/>
 <style xml:id="s_emf_oco" tts:textEmphasis="open circle outside"/>
 <style xml:id="s_emf_odo" tts:textEmphasis="open dot outside"/>
 <style xml:id="s_emf_oso" tts:textEmphasis="open sesame outside"/>
 
 <style xml:id="_d_default" style="d_outline"/>
 <style xml:id="_r_default" tts:fontSize="5.333rh" tts:lineHeight="125%" ebutts:linePadding="0.25c" tts:luminanceGain="1.0" itts:fillLineGap="false" style="s_fg_white"/>
 <style xml:id="_r_vertical" style=""/>

 <style xml:id="_r_quantisationregion" tts:origin="10% 10%" tts:extent="80% 80%" tts:fontSize="5.333rh" tts:lineHeight="125%"/>


```

## styles which may be modified

### _d_default
you may modify the style attribute of _d_default to contain zero or more styles from the d_xxx range.

### _r_default
you may modify tts:fontSize (in `rh` units only), tts:lineHeight (in `%` units).

you may modify ebutts:linePadding (suggest you don't).  It MUST be specified in `c` units.

you may modify the style attribute. It MUST contain a colour from s_fg_xxx, and MAY contain an alignment from p_al_xxxx.  e.g. style:"s_fg_yellow p_al_center"

you may modify tts:luminanceGain (float value)

you may modify itts:fillLineGap ("true" or "false")

### _r_quantisationregion
you may modify tts:origin, tts:extent, tts:fontSize, tts:lineHeight.

See below 'region size and position quantisation' for more explanation

### _r_vertical
you may modify the style attribute. It MUST be empty, or contain an alignment from p_al_xxxx only

### s_fg_xxx
you may modify the tts:color attribute

Foreground colours must be specified in `#xxxxxx` notation using only 6 digits from upper case hex set `0123456789ABCDEF`

### s_outlinexxx
you may modify the tts:textOutline attribute's color value.

Colours in tts:textOutline must be specified in `#xxxxxx` notation using 6 digits from upper case hex set `0123456789ABCDEF`

### s_dropxxx
you may modify the tts:textOutline attribute's color value.

Colours in tts:textOutline must be specified in `#xxxxxx` notation using only 6 digits from upper case hex set `0123456789ABCDEF`

### ps_bg_boxedxxx
you may modify the tts:backgroundColor attribute

as this is a solid box, colours must be specified in `#xxxxxx` notation using only 6 digits from upper case hex set `0123456789ABCDEF`

### ps_bg_ghostboxedxxx
you may modify the tts:backgroundColor attribute

as this is a transparent box, colours must be specified in `#xxxxxxxx` notation using 8 digits from upper case hex set `0123456789ABCDEF`


## general

Any styles not mentioned above are fixed, and may not be modified.

All styles must contain only the attributes as above. (i.e. only the attribute value may be changed)

Unused styles MAY be omitted, except for `_r_quantisationregion` which must never be used, but must always be present.

## region size and position quantisation

`_r_quantisationregion` should be set such that the origin and extent represent the active subtitle area, and fontSize/lineHeight set such that extent(y) / fontSize x lineHeight is close to a round number.

This style is NEVER used.  Actual fontsize is set by combination of fontsize in `rh` from _r_default and fontsize in `%` from p_font1/p_font2

It MUST be present, and MUST contain tts:origin as a pair of `%` values, tts:extent as a pair of `%` values, tts:fontSize in `rh` units, and tts:lineHeight in `%` units.

This resulting number is the ethereal 'number of lines on a screen', and should be used to position region edges when one edge of a region is not against the edge of active subtitle area.

Subsequent calculated `tts:origin` and `tts:extent` values should be rounded to 1 decimal place.

Example for horizontal:

tts:origin="10% 10%" tts:extent="80% 80%" tts:fontSize="5.333rh" tts:lineHeight="125%"

number of ethereal lines = 0.80/(0.0533x1.25) = 12.0008 = ~12

Percent of screen per line = 80/12 = 6.667%

Therefore, raising a region off the bottom of the subtitle active area by 1 line would mean the region would be:

`<region xml:id="R1" tts:origin="10% 10%" tts:extent="80% 73.3%" tts:displayAlign="after" style="r_default">`

Conversely, Placing a subtitle one line down from the top would mean the region would be:

`<region xml:id="R1" tts:origin="10% 16.7%" tts:extent="80% 73.3%" tts:displayAlign="before" style="r_default">`

The purpose of introducing formal quantisation is to minimise the number of regions created.  Theoretically, with the above definitions, there would be a maximum of 12 regions for a file containing horizontal only text.

For vertical, please assume square characters and 16:9 aspect ratio.  

Example for vertical:

number of ethereal columns = 0.80/(0.0533x1.25)x(16/9) = 21.33 = ~21

Percent of screen per column = 80/21 = 3.81%

Therefore, moving a region one column to the left from the subtitle active area would mean the region would be:

`<region xml:id="R1" tts:origin="10% 10%" tts:extent="76.2% 80%" tts:displayAlign="after" style="r_default r_vertical">`

Conversely, Placing a subtitle one column in from the left would mean the region would be:

`<region xml:id="R1" tts:origin="13.8% 10%" tts:extent="76.2% 80%" tts:displayAlign="before" style="r_default r_vertical">`

### fontSize

p_font1 and p_font2 are used to control actual font dimensions.

fontSize must be set as a percentage (of the size specified in _r_default), e.g. "100%".

*note: this will set the actual size of text on the screen, and is not necessarily related to the fontSize used to set the line quantisation in _r_quantisationregion*

Since lineHeight can be a problematic variable, it MUST be set every time fontSize is set.  It is probably best to set it to "125%".

fontFamily should be set to "proportionalSansSerif" unless specific requirements state otherwise.

### colors

styles defining colors may be modified in the event that a specific color is required.

For example, if a specific regional norm is to use a pale yellow foreground (not uncommon in the far east), the s_fg_yellow style may be modified to reflect the different shade of yellow.

i.e. in specific circumstances styles starting with s_fg_, ps_bg_, ds_outline, ds_drop may be modified.

It is NOT intended that this should provide a way to change yellow to blue, for example, only to adjust a shade.

If modifying colouring style attributes, solid colours (s_fg_xxx, s_outlinexxx, s_dropxxx) must be specified in `#xxxxxx` notation using only 6 digits from upper case hex set `0123456789ABCDEF`, and transparent colours (ps_bg_ghostboxedxxx) must be specified in `#xxxxxxxx` notation using 8 digits from upper case hex set `0123456789ABCDEF`.

(note: when converting to formats like PAC, STL, etc, exact colours cannot be carried over, hence why we use fixed names for the 'normal' 8 teletext colours.  These MAY be re-defined by the transmission system on playout.)

The `style` attribute in _r_default must be present, and must only be one of the 8 foreground colour style names (those that start `s_fg_`) - this may be used to change the overall default colour for the subtitles.


## Style use

general:

styles prefixed with r_ may be applied to `<region>`.

styles prefixed with d_ may be applied to `<div>`.

styles prefixed with p_, ps_ may be applied to `<p>`.

styles prefixed with s_, ps_ may be applied to `<span>`.

if the style attribute in _d_default is modified, only styles applicable to div may be referenced.

_r_default and _r_vertical MAY contain style references to p_al_xxx as a way to set the default alignment/justification for the whole file.

_r_quantisationregion must never be used, but must always be present.

Every `div` must reference `d_default`

Every `region` must reference `r_default`


### alignment/justification.

Note that start means the side (including top/bottom for vertical) where the first character will be closest to.

Note that end means the side (including top/bottom for vertical) where the first character will be furthest from.

e.g. in Arabic/Hebrew correctly marked up as p_rtl, start means right, and end means left.

e.g. in vertical Japanese, start means top, end means bottom.

p_al_start, p_al_end - these align a single line or multi-line `<p>` element against the region edge.

p_al_center - this aligns a single line or multi-line `<p>` element to the center.

p_al_start_center, p_al_start_end - these align the the `<p>` element against the 'start' region edge, but justify the content start/center/end

p_al_end_start, p_al_end_center - these align the the `<p>` element against the 'end' region edge, but justify the content start/center/end

p_al_center_start, p_al_center_end  - these align the the `<p>` element to the center of the region, but justify the content start/center/end

the _r_default style attribute MAY contain an alignment style from the set p_al_start, p_al_end, p_al_center, p_al_start_center, p_al_start_end, p_al_end_start, p_al_end_center, p_al_center_start, p_al_center_end.
This would set the default text alignment for all regions.

the _r_vertical style MAY contain a style attribute containing an alignment style from the set p_al_start, p_al_end, p_al_center, p_al_start_center, p_al_start_end, p_al_end_start, p_al_end_center, p_al_center_start, p_al_center_end.
This would set the default text alignment for vertical regions


### outline/dropshadow

Imsc does not support dropshadow, but you may use d_drop in place of d_outline, and s_dropxxx in place of s_outlinexxx to signify that the text is desired dropshadow.  This feature is to enable the dropshadow to be reproduced if the rosetta file is converted back to an extant format by a processor which fully understands the style name usage.

d_outline or d_drop may be specified as a style of _d_default to apply it to the whole file.

It may also be specified individually on `<div>` elements using d_outline or d_drop.

Should a `<span>` need a different 'background' color when outlined, then s_outlinexxx or s_dropxxx may be specified on `<span>`.  

***However, s_outlinexxx or s_dropxxx may not be used on `<span>` unless d_outline or d_drop (respectively) has been specified in _d_default or on `<div>`***.

Note: it is normal for translation subtitles to be outlined.

### boxing

To box only the line areas, please specify ps_bg_boxedxxx or ps_bg_ghostboxedxxx on every base level span in every `<p>`.

If a subtitle contains multiple `<p>`, all base level `<span>` elements in all `<p>` for that subtitle must have the same type (but not necessarily color) of boxing style applied.

To change the background color of a single `<span>`, apply a different ps_bg_ style to it.

Do not mix ps_bg_boxedxxx and ps_bg_ghostboxedxxx in a single subtitle.

Do not box subtitles containing Ruby text (Japanese) unless you have fully checked it all the way through to the player, and understand the result.

### stripe

To box lines so that the boxing reaches the edges of the region, please specify ps_bg_boxedxxx or ps_bg_ghostboxedxxx on *every* `<p>` in the subtitle.

To change the background color of a single `<span>`, apply a different ps_bg_ style to it - but bear in mind that in TTML, for ghost box, this will double the opacity of that span.

Do not mix ps_bg_boxedxxx and ps_bg_ghostboxedxxx in a single subtitle.

Do not stripe subtitles containing Ruby text (Japanese) unless you have fully checked it all the way through to the player, and understand the result.

