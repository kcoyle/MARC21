# MARC21 is not Z39.2 (or ISO2709)

The MARC21 record is a single implementation of the actual MARC (general) standard. That latter is defined as Z39.2 in NISO and ISO2709 in ISO. The standard that is behind the MARC21 record format has capabilities that were not implemented in the Library of Congress or other library versions of MARC, once called "US MARC" and now called "MARC21". 

| datum | ISO2709 (Z39.2) | MARC21 |
| ----- | --------------- | ------ |
| record length field | 0-99999 | 0-99999 |
| indicator count | 0-9 | 2 |
| length subfield code | 1-9 | 2 |
| field length # chars | 0-9 | 4 |
| actual field length limits | 0-999999999 | 0-9999 |
| starting position len | 0-9 | 5 |
| implementation defined portion | 0-9 | n/a |
| tag | 3 chars, 0-9+a-z | 0-9 |
| sub-record tag | 002 | n/a |

The ISO2709 record format uses bytes in the Leader to set the length of fields, subfield codes, and indicators. MARC21 is a single selection of these options: maximum field length of 9999, 2 indicators in each field. In addition, although ISO2709 allows for an alphanumeric tag, MARC21 limits tags to numerics only.

These limitations matter because in the course of extending the MARC21 format to accommodate new data, the limit of a-z as codes for subfields in some fields has been reached, and no further expansion has been possible. (Note that characters 0-9 are reserved for specific functions as subfield codes.) This has caused some "shoe-horning" of data into tagged fields, sometimes combining separate data points into a single subfield, other times creating separate fields where a subfield in an existing field might suffice.

## Examples

### 773 Host Item Entry

The 773 is where one can encode the citation information for a journal article. The citation was originally given in display form ("Vol. 23, issue 36"). With the need to link journal articles to discovery systems and OpenURLs. it was desired to have a place to carry citation information in an actionable format. This information often came to the catalog from databases that stored volume and issue numbers as separate data elements. However, the 773 field was already using most of the a-z subfield codes, and some of the available codes were normally reserved for certain mnemonic purposes. Therefore, the actionable volume and issue information was placed in a single subfield using a format defined by a citation display standard.

773 $tMetro. $gVol. 96, no. 4 (May 2000), p. 23-24, 27$q96:4<23
