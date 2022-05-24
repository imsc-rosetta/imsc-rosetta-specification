
# Outline

This file is a sample which demonstrates the alignment features of imsc-rosetta.

imsc-rosetta has 7 alignment style names which can be applied to `<p>`:

- p_al_start
- p_al_end
- p_al_start_center
- p_al_start_end
- p_al_end_start
- p_al_end_center
- p_al_center_start
- p_al_center_end

*note: there is no style p_al_center, as this is the fixed default*

*note: there are no styles p_al_start_start, p_al_center_center, p_al_end_end - use p_al_start, and p_al_end*

Vertical placement (in horiozontal subtitling) is determined by region edge placement.

The region edge against which the subtitle rests is placed according to the quantisation calculated from the extent, fontSize and lineHeight specified in _r_region.

For this file, the region edge position is based on 12 row positions, determined by

row height = 5.333/100 x 125/100 = 6.666/100 or 6.666% of screen height

subtitle vertical area = 80/100

postion count = subtitle vertical area/row height = 0.8/0.06666 = ~12

Therefore region edges are quantised to n * 80%/12

# div 1

This div represents a single line centered at the bottom of the screen.  Note the absence of a p_al_ style - here we are using the default positon which is fixed as center in imsc-rosetta.

# div 2

This div represents a single line on the left using p_al_start in left to right text.

# div 3

This div represents a single line on the right using p_al_end in left to right text.

# div 4

This div represents two lines centered at the bottom.  Note the absence of a p_al_ style - here we are using the default positon which is fixed as center in imsc-rosetta.

# div 5

This div represents two lines on the left bottom using p_al_start in left to right text.

# div 6

This div represents two lines on the right bottom using p_al_end in left to right text.

# div 7

This div represents two lines, where the longest line is centered, and the shorter line left aligned to the longer line (commonly know and center left align) using p_al_center_start in left to right text.

# div 8

This div represents two lines, where the longest line is centered, and the shorter line right aligned to the longer line (uncommon) using p_al_center_end in left to right text.

# div 9

This div represents two lines, where the longest line is left aligned, and the shorter line center aligned relative to longer line (uncommon) using p_al_start_center in left to right text.

# div 10

This div represents two lines, where the longest line is left aligned, and the shorter line right aligned relative to longer line (uncommon) using p_al_start_end in left to right text.

# div 11

This div represents two lines, where the longest line is right aligned, and the shorter line left aligned relative to longer line (uncommon) using p_al_end_start in left to right text.

# div 12

This div represents two lines, where the longest line is right aligned, and the shorter line center aligned relative to longer line (uncommon) using p_al_end_center in left to right text.

# div 13

This div represents three lines, where the first is left aligned, the second is centered, and the third is right aligned.  This uses three separate `<p>` elements, marked with p_al_start, p_al_center_ and p_al_end respectively.

# div 14

Subtitles 14-22 demonstrate vertical positioing using regions.


