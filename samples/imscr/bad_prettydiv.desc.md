# Outline

This file is prettified by a 'standard' XML output. Although on the face of it, it looks like a valid XML file, it is not a valid IMSC-Rosetta file.

IMSC-Rosetta uses xml:space="preserve" to ensure that dcertain asepects of the subtitles are rendered correctly (e.g. multiple spaces are represented as multiple spaces, and very specifically, change of background colour between spans always works.)

Because we need xml:space="preserve", the indentation spaces and carriage returns inside `<p>` are rendered by the player, and severely disturb the rendering, leading to imncorrect images.  See below.

Please do NOT prettify within a `<p>` element.  TTML does not care it your prettify anything else in the file - but `<p>` must effectively be on one line.

If you run the file through [imsc-rosetta-qualify](https://imsc-rosetta.github.io/imsc-rosetta-qualify/), it will report errors, but also you will find a corrected version in `XML round trip from Simple Parse JSON`, which if run through again is error free.

# div 1
This subtitle should be all on one line at the bottom, but has been split into multiple lines and raised by the player rendering the carriage returns.

# div 4
The two `<p>` of this subtitle are intended to be adjacent, and not raised.

# div 26
This subtitle illustrates the rendering if carriage returns by the player, and how the subtitle is raised by the trailing CR after the last span.