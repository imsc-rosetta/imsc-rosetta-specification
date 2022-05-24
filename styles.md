# Style names 

Style names are fixed in imsc-rosetta for simplicity of use and understanding.

Some styles are fixed in terms of content,. and others are adjustable, either to represent file defaults, or to represent specific requirements.

## All styles

It is expected that only the used set of styles be present in a file, but it is not incorrect to include more than are used.

The following is the maximal style name set, and thier default values:

```
 <style xml:id="r_region" tts:backgroundColor="transparent" tts:showBackground="whenActive" tts:fontStyle="normal" tts:fontWeight="normal" tts:color="white" tts:fontFamily="proportionalSansSerif" tts:textAlign="center" itts:fillLineGap="false" style="_r_default"/>
 <style xml:id="r_vertical" tts:writingMode="tbrl"/>

 
 <style xml:id="d_fillgap" itts:fillLineGap="true" />
 <style xml:id="d_forced" itts:forcedDisplay="true"/>
 <style xml:id="d_outline" tts:textOutline="#000000 0.05em"/>
 <style xml:id="d_drop" tts:textOutline="#000000 0.05em"/>

 
 <style xml:id="p_rtl" tts:direction="rtl"/>
 <style xml:id="p_ltr" tts:direction="ltr"/>
 
 <style xml:id="p_al_start" tts:textAlign="start"/>
 <style xml:id="p_al_end" tts:textAlign="end"/>
 <style xml:id="p_al_center" tts:textAlign="center"/>
 <style xml:id="p_al_start_start" ebutts:multiRowAlign="start" tts:textAlign="start"/>
 <style xml:id="p_al_start_center" ebutts:multiRowAlign="center" tts:textAlign="start"/>
 <style xml:id="p_al_start_end" ebutts:multiRowAlign="end" tts:textAlign="start"/>
 <style xml:id="p_al_end_start" ebutts:multiRowAlign="start" tts:textAlign="end"/>
 <style xml:id="p_al_end_center" ebutts:multiRowAlign="center" tts:textAlign="end"/>
 <style xml:id="p_al_end_end" ebutts:multiRowAlign="end" tts:textAlign="end"/>
 <style xml:id="p_al_center_start" ebutts:multiRowAlign="start" tts:textAlign="center"/>
 <style xml:id="p_al_center_center" ebutts:multiRowAlign="end" tts:textAlign="center"/>
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
 
 
 <style xml:id="p_rb_res_before" tts:rubyReserve="before"/>
 <style xml:id="p_rb_res_after" tts:rubyReserve="after"/>
 <style xml:id="p_rb_res_both" tts:rubyReserve="both"/>
 <style xml:id="p_rb_res_outside" tts:rubyReserve="outside"/>

 <style xml:id="ps_shear" tts:shear="16.67%"/>
 
 <style xml:id="s_rb_b" tts:ruby="base"/>
 <style xml:id="s_rb_t" tts:ruby="text"/>
 
 <style xml:id="s_rb_algn_center" tts:ruby="container" tts:rubyAlign="center"/>
 <style xml:id="s_rb_algn_around" tts:ruby="container" tts:rubyAlign="spaceAround"/>
 
 <style xml:id="s_rb_posn_before" tts:ruby="container" tts:rubyPosition="before"/>
 <style xml:id="s_rb_posn_after" tts:ruby="container" tts:rubyPosition="after"/>
 <style xml:id="s_rb_posn_outside" tts:ruby="container" tts:rubyPosition="outside"/>
 
 <style xml:id="s_combine" tts:textCombine="all"/>
 
 <style xml:id="s_emf_fcb" tts:textEmphasis="filled circle before"/>
 <style xml:id="s_emf_fdb" tts:textEmphasis="filled dot before"/>
 <style xml:id="s_emf_fsb" tts:textEmphasis="filled sesame before"/>
 <style xml:id="s_emf_ocb" tts:textEmphasis="open circle before"/>
 <style xml:id="s_emf_odb" tts:textEmphasis="open dot before"/>
 <style xml:id="s_emf_osb" tts:textEmphasis="open sesame before"/>
 <style xml:id="s_emf_fca" tts:textEmphasis="filled circle after"/>
 <style xml:id="s_emf_fda" tts:textEmphasis="filled dot after"/>
 <style xml:id="s_emf_fsa" tts:textEmphasis="filled sesame after"/>
 <style xml:id="s_emf_oca" tts:textEmphasis="open circle after"/>
 <style xml:id="s_emf_oda" tts:textEmphasis="open dot after"/>
 <style xml:id="s_emf_osa" tts:textEmphasis="open sesame after"/>
 <style xml:id="s_emf_fco" tts:textEmphasis="filled circle outside"/>
 <style xml:id="s_emf_fdo" tts:textEmphasis="filled dot outside"/>
 <style xml:id="s_emf_fso" tts:textEmphasis="filled sesame outside"/>
 <style xml:id="s_emf_oco" tts:textEmphasis="open circle outside"/>
 <style xml:id="s_emf_odo" tts:textEmphasis="open dot outside"/>
 <style xml:id="s_emf_oso" tts:textEmphasis="open sesame outside"/>
 
 <style xml:id="_d_default" style="d_outline"/>
 <style xml:id="_r_default" tts:origin="10% 10%" tts:extent="80% 80%" tts:displayAlign="after" tts:wrapOption="noWrap" tts:fontSize="5.333rh" tts:lineHeight="125%" ebutts:linePadding="0.25c"/>
```

## styles which may be modified

Any styles not mentioned below are fixed, and may not be modified.

All styles must contain only the attributes as above. (i.e. only the attribute value may be changed)

### region size and position quantisation

_r_default should be set such that the origin and extent represent the active subtitle area, and fontSize set such that extent(y) / fontSize x lineHeight is close to a round number.

This resulting number is the ethereal 'number of lines on a screen', and should be used to position region edges.

### fontSize

p_font1 and p_font2 are used to control actual font dimensions.

fontSize must be set as a percentage (of the size specified in _r_default), e.g. "100%".

*note: this will set the actual size of text on the screen, and is not necessarily related to the fontSize used to set the line quantisation in _r_region*

Since lineHeight can be a problematic variable, it MUST be set every time fontSize is set.  It is probably best to set it to "125%".

fontFamily should be set to "proportionalSansSerif" unless specific requirments state otherwise.

### colors

styles defining colors may be modified in the even that a specific color is required.

For example, if a specific regional norm is to use a pale yellow foreground (not uncommon in the far east), the ds_fg_yellow style may be modified to reflect the different shade of yellow.

i.e. in specific circumstances styles starting with ds_fg_, ps_bg_, ds_outline, ds_drop may be modified.

It is NOT intended that this should provide a way to change yellow to blue, for example, only to adjust a shade.

## Style use

general:

styles prefixed with r_, _r may be applied to `<region>`.

styles prefixed with d_, _d may be applied to `<div>`.

styles prefixed with p_, ps_, _p may be applied to `<p>`.

styles prefixed with s_, ps_, _s may be applied to `<span>`.

if the style attribute in _d_default is modified, only styles applicable to div may be referenced.

### alignment/justification.

Note that start means side (including top/bottom) where the first character will be closest to.

Note that end means side (including top/bottom) where the first character will be furthest from.

e.g. in Arabic/Hebrew correctly marked up as p_rtl, start means right, and end means left.

e.g. in vertical Japanese, start means top, end means bottom.

p_al_start, p_al_end - these align a single line or multi-line `<p>` element against the region edge.

p_al_center - this aligns the `<p>` element centrally in the region.

p_al_start_start, p_al_start_center, p_al_start_end - these align the the `<p>` element against the 'start' region edge, but justify the content start/center/end

p_al_end_start, p_al_end_center, p_al_end_end - these align the the `<p>` element against the 'end' region edge, but justify the content start/center/end

p_al_center_start, p_al_center_center, p_al_center_end  - these align the the `<p>` element to the center of the region, but justify the content start/center/end

Note that p_al_center and p_al_center_center are equivlent, as are p_al_start, p_al_start_start and p_al_end, p_al_end_end.

### outline/dropshadow

Imsc does not support dropshadow, but you may use d_drop in place of d_outline, and s_dropxxx in place of s_outlinexxx to signify that the text is desired outlined.  This feature is to enable the dropshadow to be reproduced if the rosetta file is converted back to an extant format by a processor which fully understands the style name usage.

d_outline or d_drop may be specified as a style of _d_default to apply it to the whole file.

It may also be specified individually on `<div>` elements using d_outline or d_drop.

Should a `<span>` need a different 'background' color when outlined, then s_outlinexxx or s_dropxxx may be specified on `<span>`.  

***However, s_outlinexxx or s_dropxxx may not be used on `<span>` unless d_outline or d_drop (respectively) has been speified in _d_default or on `<div>`***.

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

