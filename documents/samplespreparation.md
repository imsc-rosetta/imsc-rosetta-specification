# How to prepare a sample document for inclusion in the repository

The [/samples](../samples) folder contains descriptive documents about the samples presented as part of the IMSC-Rosetta specification repository.

To create a descriptive file from an `(name).imsrc` file, do the following:

## Create a `(name).descr.md` file:

e.g. if preparing `myimscrosettasample.imscr` create file called `myimscrosettasample.descr.md`

The descr.md file is parsed automatically by a very simple parser, so take care to keep to the below.  The simple parser spoilt the file on `\n# `, and then expects each part to begin with either `Outline` or `div`.  You MUST use one space after the `#` character, else it will not be considered the start of a description.

The first line should be 

`# Outline`

followed by a descriptive describing the whole file.

e.g.

```
# Outline

#This is my first sample file.

## Purpose:
To test the creation of sample descriptive files

## Subtitles:
very few
```

Note how you may use `#something` (no space) and `## something` (no space directly after hash), and these will be part of the description.

you may now add subsequent sections for each div or for important divs.  Each div section must start `# div (xml:id from div)\n`

e.g.
```
# div 1
A very expressive presentation.

# div 2
With some italics

# div 49
this is the fourth div - sorry I did not describe the third, and sorry the div `xml:id` jumped from 3 to 49
``` 

## create images

Open [imsc-rosetta-qualify](https://imsc-rosetta.github.io/imsc-rosetta-qualify/) and drop both `(name).imsrc` and `(name).descr.md` into it.  (You can drop them both at the same time).

Check you don't have any unexpected parse errors on the imscr file.

Visit the `Patched Render File` tab, and check the renders look as you expect.

Click `Generate images`, and after a short while, the browser will offer you a download of a zip file.  Note that all processing is done locally in your browser.

Download the zip, and unzip it.

The created zip will contain what would be required to add to the [samples](https://github.com/imsc-rosetta/imsc-rosetta-specification/tree/testhtml/samples) folder of the repository.

i.e.

`(name).imsrc.md` descriptive file, referencing the images.

`imscr/(name).imsrc` - your original file.

`imscr/(name).descr.md` - your original file descriptive file.

`images/(name).imscr/*.png` - images generated.

`html/(name).imscr.html` - an html rendition of the descriptive file (markdown specifics are NOT converted to html, except for `\n` being replaced with `<br \>`).  This is useful for local viewing, and references the images via `../images/(name).imscr/`.

Images are named by the `begin` value of their `div` converted to fractional seconds.
