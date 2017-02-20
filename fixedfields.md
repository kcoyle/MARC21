# MARC21 fixed fields (006, 007, 008)

The fixed fields are the proof that the developers and maintainers of the MARC format recognized that there is a need for DATA that the textual fields and subfields do not fulfill. Unfortunately, this data portion of the record seems to be considered of secondary importance in comparison to the textual fields. These data elements had no use for the card display, but some elements were used to create reports such as lists of new library acquisitions. 

In library systems there is a strong "chicken and egg" dilemma relating to the fixed fields: they are not seen as being important because there isn't a visible system use of them, but because record creators often neglect to input the values in these fields they cannot be used reliably for automated functions. The fact that with a few exceptions the fixed fields are valid for only certain resource formats (text, maps, music, etc.) also makes it difficult to find uses for them in catalogs of mixed content. It may not be obvious to a user that an element like Target Audience will retrieve books, music, computer files and visual materials, but not maps, serials or sound recordings.

Some current library systems make use of fixed field data in their "faceted" display. This typically uses the coded date of publication and the language of text. The facets relating to resource format (book, sound recording, etc.) most likely comes from the coded format in the Leader. 

# 008

The primary fixed field is the 008, and it is nearly always considered required. The 008 is coordinated with the resource format in the Leader - that is, there is an 008 for books, one for maps, one for sound recordings, etc. The positions in the 008 are interpreted based on the format coded in Leader positions 06 and 07. For each different format type there can be different meanings to the positions in the 008. Most data elements are expressed as codes, and the codes can be 1, 2 or 3 characters in length. The date is also entered in the 008 as a four-character date with two date types possible.

The 008 field is always 40 characters in length and the coded data elements are positional. This means that even if elements are not encoded, blanks must fill in those positions. 

```
008	050817s2005    nyua     b    001 0 eng
```

Positions 00-17 and 35-39 are the same for all resource formats. The remaining positions are defined differently for different formats.

# 006

The 008 carries data that is format specific, and some number of resources include more than one format (e.g. a sound recording with an included libretto). The 008 cannot be repeated because there is no place within the field to indicate what the format is - the format is interpreted from the Leader, which only contains one format code. For this reason, the 006 field was developed. The 006 field is repeatable and carries a format code plus the format-specific data elements that are in positions 18-34 of the 008 field. The 006 is 100% redundant with the 008, but was needed because the original design did not anticipate carrying coded information for multiple formats in a single MARC record.

#007
