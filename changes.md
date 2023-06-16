# Changes based on feedback.

## 2023-06-16

To allow the default outline/dropshadow to reflect the change fo the colour black, change: 
```
   <style xml:id="d_outline" tts:textOutline="#000000 0.05em"/>
   <style xml:id="d_drop" tts:textOutline="#000000 0.05em"/>
```
to
```
   <style xml:id="d_outline" style="s_outlineblack"/>
   <style xml:id="d_drop" style="s_dropblack"/>
```

Updated README.md and japanese.md to be more explicit about overlapping cues and regions.

## 2023-05-25

change all references to r_region to r_default to ensure clarity and consistency with d_default

change any ref to `transparent` as a color to `#00000000` to be explicit and consistent

change p_al_start/center/end to include ebutts:multiRowAlign.

move itts:fillLineGap from r_default to _r_default, and make it manditory.


## 2023-05-23

Somewhere in the introduction of default colours, we lost one premise of IMSC, and got confused over defaults.

To address this, we've modified the use of some default styles.

Therefore ALL regions must have r_default, ALL divs must have d_default, and these in turn reference _r_default and _d_default.  And _r_default and _d_default must not be referenced by regions or styles.

Also, _r_quantisationregion is introduced, as we need some way to store the quantisation intent more explicitly, and outside of things we may consider to be for a different reason.  _r_quantisationregion must never be referenced, but always be present.  tts:extent and tts:origin have been removed from r_default as they must always be present on each region.

These changes will require code changes to existing implementations, but we're getting close now with good feedback from implementors.

Please use [the updated imsc-rosetta-qualify](https://imsc-rosetta.github.io/imsc-rosetta-qualify/) to help you get the files correct, and visit styles.md

Added tts:luminanceGain in _r_default

Added more explanation of line quantisation in styles.md

Added `tts:overflow="visible"` to `r_region`.  Note that subtitles should not generally exceed region sizes, but it is noted that when using p_shear, it may cause a p to extend beyond the region bounds.  Players/renderers may not honour drawing outside fo the region bounds.

Update samples and rebuilt sample descriptive files, including image re-render.


## 2023-05-17 - ps_shear

`ps_shear` renamed to `p_shear`, as tts:shear cannot be applied to `span`

Updated samples and documentation to reflect the change.

re-introduce p_al_center, and allow p_al_xxx to be set in style on _r_default and _r_vertical to set default alignment/justification on horizontal and vertical regions.

Be more explicit about what you may modify.

## 2023-05-12 - default foreground colour

Added s_fg_white as defaulting to full-white (#FFFFFF) and use in _r_default

For off-white, s_fg_white may be changed, e.g. to #EEEEEE.

Moved `tts:wrapOption="noWrap"` from _r_default to the non-modifiable r_default

Remove tts:color="white" from r_default, replace with a requirmeent to have a color style mentioned in _r_default

Note: to set a different overall default foreground colour, set (for example) style="s_fg_yellow" in _r_default

Small corrections and added explanation.

Remove _p_default and _s_default from the FAQ.

Modified sample files to reflect the changes.

Add p_al_center back in to the style names set.

Allow style in _r_region to contain an alignment p_al_xxxx as a default alignment.

Add _r_vertical as a holder for (changeable) default vertical styles.  The style attribute may contain an alignment p_al_xxxx as a default alignment for vertical text.
