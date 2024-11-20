# Imsc-Rosetta Metadata - overall file metadata

Not to be confused with comments, which are metadata in `<div>` (see document structure).

## Language
The language for a file is defines in the xml:lang attribute of the tt element.

Exact Language coding to be defined by customer.  e.g. bcp47/MESA/CDSA.

*Note that the attribute `xml:lang` is used.  Be aware that this may be constrained in terms of content, and if checked by an 'official' XML checker, unknown language codes may be flagged as errors.*

## Information about subtitle type/categorisation
Optional.  The purpose of this classification is as confirmation of external classification. 

`<rosetta:role>SDH|translationonly|translationwithforced|forcedonly</rosetta:role>`

## Information about time in the media
startOfProgramme: Optional. If present, should correspond to the time in HH:MM:SS.TTT since midnight which represents the first frame of video which is intended for transmission. (i.e. if the media contains a 'slate', this is the time of the first frame AFTER the slate).

`<rosetta:startOfProgramme>10:00:00.000</rosetta:startOfProgramme>`

startOfMedia: Optional. If present, should correspond to the time in HH:MM:SS.TTT since midnight which represents the first frame of video of the media used to prepare the subtitles. (i.e. if the media contains a 'slate', this is the time of the first frame of the slate).

`<rosetta:startOfMedia>09:59:30.000</rosetta:startOfMedia>`


Note: for 23.976 media, a Timecode of 10:00:00:00 is represented as a Time of 10:00:36.000 - and TC of 01:00:00:00 is 01:00:03.600

This is because in 23.976, there is no drop frame timecode, and each frame of video is (1001/1000 x 1/24) seconds long


## dates and times
In the below, 'ISO Date' refers to the full UTC date and time YYYY-MM-DDTHH:MM:SS.SSSZ, e.g. 2019-11-14T00:55:31.820Z

For simplicity, use the 'Z' timezone (UTC).

### created date: Optional.  

This is intended to preserve the original time of creation of the subtitle data (e.g. the date of the translation).  In a conversion scenario, this could be the creation date of the original file.

`<rosetta:created>ISO date</rosetta:created>`

### modified date: Optional.  

This is intended to preserve the last modification time the subtitle data (e.g. the date of the last edit or conversion).  In a conversion scenario, this could be the date of the conversion.

`<rosetta:modified>ISO date</rosetta:modified>`

Example:

`<rosetta:created>2019-11-14T00:55:31.820Z</rosetta:created>`

`<rosetta:modified>2021-02-15T13:42:03.000Z</rosetta:modified>`

## Constraints.  How to define?



## Originator
Optional.  Indicates the organisation which originated the subtitles.

`<rosetta:originator>{origination company}</rosetta:originator>`

## Information about the original subtitle format
Optional. Indicates the original format the subtitles were converted from.

`<rosetta:originalFormat>EBUSTL|OpenSTL|SRT|FPC|PAC|890|CAP|SMPTE2052|EBUTT|IMSC1.0</rosetta:originalFormat>`

## Information about the transformation product
Optional.  Indicates the product and version used to convert the subtitles.

`<rosetta:transformationProduct>{Transformation Product}</rosetta:transformationProduct>`

`<rosetta:transformationProductVersion>{Transformation Engine Version}</rosetta:transformationProductVersion>`

## Custom Document Metadata

At times, there will be a need to carry customer specific metadata in IMSCR.  This could to be used to drive business logic in processes specific to a particular customer.

Within the `<metadata>` element within `<tt>` `<head>`, other elements may be included.

Bear in mind that some processors will ignore/remove this metadata.  

Bear in mind that some simpler XML parsers may not preserve element order, and so element order should not be a requirement of metadata used.

Because we have fixed namespace declarations in the `<tt>` element for simplicity, please use local namespacing (see example of use of ebu-tt metadata below).

### Examples of using foreign metadata.  These are not suggestions of metadata that should be included.

With explicit namespace alias:
```
<metadata>
	<ebuttm:documentMetadata xmlns:ebuttm="urn:ebu:tt:metadata">
		<ebuttm:documentOriginalProgrammeTitle>Snow White</ebuttm:documentOriginalProgrammeTitle>
		<ebuttm:documentOriginalEpisodeTitle>Series 1, Episode 1</ebuttm:documentOriginalEpisodeTitle>
	</ebuttm:documentMetadata>
</metadata>
```

Redefining the default namespace for this element and it's children.  This is equivalent to above:
```
<metadata>
	<documentMetadata xmlns="urn:ebu:tt:metadata">
		<documentOriginalProgrammeTitle>Snow White</documentOriginalProgrammeTitle>
		<documentOriginalEpisodeTitle>Series 1, Episode 1</documentOriginalEpisodeTitle>
	</documentMetadata>
</metadata>
```

example of preserving metadata from an original format:
```
<metadata>
	<_890 xmlns="https://nebula.yella.tv/yella/imscr/filemeta/_890">
		<headers>
			<tapenumber>12345657</tapenumber>
			<originaltitle>Snow White</originaltitle>
			<SOM>10:00:00:00</SOM>
			<languageid1>0x90</languageid1>
			<languageid2>0x90</languageid2>
			<primaryfont>CCKM44.V</primaryfont>
			<secondaryfont>CCKM44.V</secondaryfont>
			<softwareversion>TBX352</softwareversion>
		</headers>
	</_890>
</metadata>
```


