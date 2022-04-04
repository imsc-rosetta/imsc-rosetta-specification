# Rosetta-imsc
This repo represents the base specification and description of rosetta-imsc - a practical cut down IMSC compatible subtitle format

At version 0.0.1, rosetta-imsc will be suitable for horizontal translation subtitles in all languages, with the exception of advanced Japanese (i.e. no rubies yet).

The general intent is to have a subtitle format which is fully IMSC complient (and so TTML 2 complient), whilst being specifically easy to parse, and easy to create, without detailed knowledge of XML and the specs that IMSC/TTML are based on.

To this end, the use of TTML constructs is highly restricted so that the exact form of the file may be specified in full without ambiguity.

