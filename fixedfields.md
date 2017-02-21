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

The date information in positions 06-14 is nearly always redundant with textual information in the variable fields, although there may be some differences, such as when the data is unknown or not clear. The 008 can have a date like "196u" while the descriptive field may read "1962?". 

Also, since the date is primarily used to order displays by date of publication, the use of non-numerics in dates forces those dates to sort before the complete dates, thus often giving users the least useful dates first.

# 006

The 008 carries data that is format specific, and some number of resources include more than one format (e.g. a sound recording with an included libretto). The 008 cannot be repeated because there is no place within the field to indicate what the format is - the format is interpreted from the Leader, which only contains one format code. For this reason, the 006 field was developed. The 006 field is repeatable and carries a format code plus the format-specific data elements that are in positions 18-34 of the 008 field. The 006 is 100% redundant with the 008, but was needed because the original design did not anticipate carrying coded information for multiple formats in a single MARC record.

# 007

The 007 field carries information about the physical formats of the resources being described. The first two characters of the 007 describe the format; subsequent character positions are defined differently for different formats. The 007 is repeatable. In some cases there are variable fields in the record that provide descriptive cataloging information of the display format. Although at times the coded data in the 007 and the descriptive information in the variable fields give the same information, there is no direct link between the coded data and the variable fields.

# Code Lists

There are over 200 individual code lists that are used in the fixed fields, some of which are used only with specific formats. For example:

```
color (maps)
  * One color
  * Multicolored
color (microforms)
  * Black-and-while
  * Multicolored
  * Mixed
  ```

# Summary of problems

* Each format requires a different overlay to interpret the coded positions
* There is no stated functionality for the codes - what is their intended use?
* In a number of cases, a blank in a fixed field position is meaningful, so there is no way to know whether the blank means that the cataloger did not fill in the code for that position, or if the blank carries its intended meaning.
* There are few library systems that make use of most of the coded data. (It would be great to find some data on this.) Yet the fact that the data is coded implies that the codes are for machine use. It is a waste of time for catalogers to fill in these codes if they are not in fact used in systems.
* Because systems do not use the codes, some catalogers do not fill in these fields in records. If you have a file where some records have the codes and others do not, even if you want to make use of the codes for searching you cannot because searches will never retrieve records where the codes were not filled in.

# Some systems usage

* BC Libraries. Shows how fixed field information shows in displays, but only appears to make use of physical format code. http://docs.sitka.bclibraries.ca/Sitka/current/html/cat-MARC-leader.html
