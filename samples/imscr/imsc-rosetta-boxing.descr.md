
# Outline

This file is a sample which demonstrates the boxing features of imsc-rosetta.

In imsc-rosetta, subtitles can be boxed in a variety of ways:

- unboxed
- solid boxing
- ghost boxing (semi-transparent)
- solid stripe (box which extends to the maximum subtitle area in the writing direction)
- ghost stripe (semi-transparent)

The background color of text can be changed if boxed

*note that file contains ALL imsc-rosetta defined styles as an example - this is not necessary, only the used styles are required*

# div e_1

Unboxed.  Note that this file has black outline (d_outline) in _d_default.

# div e_2

Solid black box.  Note if you look closely, parts of 'y' and 'Á' go outside of the box, and are outlined.

Sometimes used as a channel style.  Other times used to make text readable when on top of a bright or contrasty background.

# div e_3

Ghost box

Sometimes used as a channel style.  Other times used to make text readable when on top of a bright or contrasty background.

# div e_4

Solid Stripe

Generally used to cover existing text more fully that a box around the text only would.

# div e_5

Ghost Stripe

Generally used to cover existing text more fully that a box around the text only would.

# div e_6

Unboxed but demonstrating 'background' color change on outlined text.

Retention of background colour may be important if the file is to be exported to teletext.

# div e_7

Solid box demonstrating change of background color.

Note that black outline is retained.  Comments?

# div e_8

Ghost box demonstrating change of background color.

Note that black outline is retained.  Comments?

# div e_9

Solid Stripe demonstrating change of background color.

Note that black outline is retained.  Comments?

# div e_10

Ghost Stripe demonstrating change of background color.

Note how the changed background color spans have double the opacity of the black.

This is unavoidable because of the way boxing on `<p>` and `<span>` work in TTML.

Note that black outline is retained.  Comments?

# div e_11

Solid black box with d_fillgap specified on `<div>`.

# div e_12

Ghost box with d_fillgap specified on `<div>`, but with a blank line in between the lines.

***The result is probably not desirable.***

