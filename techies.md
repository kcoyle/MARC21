# What Developers and Library Technologists Like About MARC

## Records and Files Are Compact

It is not uncommon to exchange or process files with millions of records. These files can be transferred over the network fairly quickly and can be stored on a desktop computer. This is important because libraries receive files of records from other libraries or from vendors, and it must be possible to process them in house.

## Tools Exist

There are tools that process the MARC record that can be used without having to do programmiing. The primary one is Terry Reese's MARCedit. These tools are used for various functions, including:

* statistical analysis of a file of records; this can be a general overview of the file or a specific inquiry about quality such as which records are missing a particular field
* batch updates; batch updates can be used to include particular information, such as the library name and ownership information, or to correct known problems, like records that have retained an obsoleted value.

## The Mnemonics 

The mnemonics in MARC tagging make it easy to select logical groups of fields. A search on tags with the first character "6" selects all of the subject headings. Also, some fields with similar tags contain the same subfields, like all fields with the second and third characters "11" (meaning the name of a corporate body). 

## Coded Data

There are data elements that are represented in certain positions of fields 006-008 that are alphanumeric codes. Most of these are a single character, although some occupy more than one position. For example,there is a one-character code to indicate the publication frequency of a periodical: a=Annual, b=Bimonthly, etc. For books there are four positions in which to code the nature of the contents, such as a=illustrations, b=maps. That there are four positions means that up to four characteristics may be coded. 

## Library Systems Know MARC

MARC is the common input and output format for nearly all major library systems in use. Because libraries will not have the capacity (nor would it be efficient) to create their systems in-house, vendor support is essential. 

# What Developers and Library Technologists Dislike About MARC

## Data Quality

One of the biggest concerns is that there are huge data quality issues. This is not just a "imperfect humans" problem, because MARC is not easily subject to validation other than a few required and a few non-repeatable fields, so creating better data through interface design may not be a plausible solution. 

## Ambiguous Fields

There are fields that are defined as either X or Y. There are other fields that have been re-defined over the years, and there is no way to know under which set of rules data was created. 

## Fixed Fields

Fixed field data, which is the main data that can be addressed algorithmically, is either not filled in, is incorrect, or contradicts the same information in the display area (variable fields) of the record. 

## Limited to MARC Only

The MARC record cannot be intermingled with data from any other sources. 

## The Standard

The MARC standard is developed only through a Library of Congress process which is notriously slow. Once decided, adding new data elements has to be scheduled months or years in advance so that all major players (LoC, OCLC, and library systems vendors) can implement simultaneously.

## Cataloging Concepts not Easily Knowable

The MARC record can contain subtleties that make sense to (some) catalogers but that aren't obvious to technical staff trying to run applications. Most of these subtleties would provide context for the content but aren't visible in the MARC code itself.
