# Changes based on feedback.

## 2023-05-12 - default foreground colour

Added s_fg_white as defaulting to full-white (#FFFFFF) and use in _r_default

For off-white, s_fg_white may be changed, e.g. to #EEEEEE.

Moved `tts:wrapOption="noWrap"` from _r_default to the non-modifiable r_default

Remove tts:color="white" from r_default, replace with a requirmeent to have a color style mentioned in _r_default

Note: to set a different overall default foreground colour, set (for example) style="s_fg_yellow" in _r_default

Small corrections and added explanation.

Remove _p_default anfd _s_default from the FAQ.
