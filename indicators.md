
# MARC Indicators

The indicators in MARC pose a number of problems because of the great variety of meanings and ways that they have been used. Some indicators control card printing; some give provenance information; some drastically change the meaning of the field. In addition, it often isn't cleaar whether indicators address the entire field, or only certain subfields.

 
## Undefined and blank indicators

Each variable field begins with two positions before the first subfield. These are known as the first and second indicators. The indicators are not always defined; in fact, in about 60% of the tags one or both indicators is not defined and is therefore always left blank in instance data. Unfortunately, in some indicators the blank is a meaningful value. This practice was recognized as problematic after a while, but some instances of this remain.

Indicators are displayed in various ways in MARC displays.  MARCEdit uses backslashes for blanks in the indicator positions:
 
```
  =082  0\$a813/.54$21
  =100  1\$aWallace, Carol,$d1955-
  =245  10$aWelcome to Mount Merry College 
```
 
The LC Catalog uses an underscore:
```
  043 __ |a n-us---
  050 00 |a ZA3250.U6 |b C68 1997
  082 00 |a 025.04 |2 21
  100 1_ |a Coyle, Karen.
```

Instance data cannot distinguish between blank indicators and undefined indicators. This means that programs that process MARC21 records have to "know" which fields have indicators and which indicators are valid.
 
## Indicators not affecting the meaning of the field

Some indicators have no effect on the semantics of the field. Instead, these indicators control how the field is displayed or whether the field should yield a "traced" heading. Traced headings are those that were once used as headings on cards, such that every traced heading resulted in a card in the card catalog. Some systems today interpret the traced headings as ones that should be indexed for user searching. Other catalogs ignore the indicator for traced headings and instead index all fields.
 
**Display indicators**

There are some indicators that are used to assign display constants to fields. These are:

    Display constant controller
    Note controller

Some of the display indicators add semantics to the field, and will be covered in the next section. This section covers those that only indicator whether or not a MARC-defined display label will be used.
 
Caption or label
>	tags in form: tag + subfield position (either 01 or 02)

Display constant controller
>	30701, 51601, 52201, 52401, 52601, 55601, 56501, 56701, 58101, 58601, 51601, 76002, 76202, 76502, 76702, 77002, 77202, 77302, 77402, 77502, 77602, 77702, 78602

Note controller
>	24702, 76001, 76201, 76501, 76701, 77001, 77201, 77301, 77401, 77501, 77601, 77701, 78001, 78501, 78601, 78701, 02802
 
Note/added entry controller 	02802, 24601

Unform title printed or displayed 	24301, 24001

**Example:**
```
775 Other Edition Entry, Second Indicator
Display constant controller
# - Other edition available
8 - No display constant generated
```
 

In a few cases it isn't clear to me what the indicators mean, for example the "File size" indicator below. I don't understand when 'file size' is used as opposed to 'case file characteristics'. It appears that 'file size' can only be used when the field has a $a subfield. If anyone knows more about the 565 and its usage, I'd like to hear about it:

 

565 Case File Characteristics Note, First Indicator
Display constant controller
# - File size
0 - Case file characteristics
8 - No display constant generated

 

Display constants were used when cards were produced by vendors and represented printing options for the cards and card sets. These types of options are now included in online systems and I would be surprised if libraries coded them on a record-by-record basis. Display constants are used in ILSs based on tables, generally, and include fields that have no MARC subfield or indicator for display. (Note, some MARC fields have a $i subfield that contains a display text that precedes the contents of the field. This is another example where similar or same functionality is achieved in more than one way in MARC. I'll try to bring all of the "display" issues together later in my analysis.)

 

It also seems that display constants are not inherently 'sharable'. They appear to be decisions made on a library-by-library basis rather than on the nature of the field. In CRS it says:

 

     "The use of display constants is determined by each organization or automation system."

 

Note controller is binary ("display note" "do not display note"). Display constant controller often has two choices: a display constant or no display constant.

 

My feeling is that we can ignore these in the current environment, but I will try to find out if any systems still use them. I can find evidence that they appear in LC records:

 

LCCN Permalink: http://lccn.loc.gov/2004062872

526 0_ |a Accelerated Reader/Renaissance Learning |b LG |c 3.1 |d 0.5

 
Trace/do not trace

 

This is another function that seems deeply linked to the card catalog. "Tracing" meant that a card would be generated with that field's data at the top above the main body of the card. Each traced card became an entry in the catalog. It is analogous to the question of whether or not certain fields should be indexed, but is not precisely equivalent since it is in some cases only pertinent to the card situation.

 

Whether or not a field is traced does not change the meaning of the field. For that reason, I am considering these indicators not relevant for this analysis.

 
Non-filing 

 

We've all gotten frustrated at systems that file titles or other strings under "The " so it seems like a good idea not to lose this information.The MARC record has handled this using an indicator that has a number representing the number of characters (not bytes, characters) to ignore from the left-hand side of the string when "filing" -- or what we would call "sorting" today.

 

My feeling is that we should create two elements: display form and sort form. The trick in implementation will be to keep links between the two forms so it is known that they represent the same string.

There are 11 fields that have non-filing indicators:

 

130, 222, 240, 242, 243, 245, 440, 630, 730, 740, 830
 

The non-filing indicator is a single digit, 0-9, that says how many characters to ignore when filing/sorting the string. Thus:

 

245 = The wizard of Oz

non-filing = 4

result = wizard of Oz

 

Many systems internally create a filing form that uses the non-filing indicator and also normalizes the string removing punctuation, changing case to all lower (or upper), etc.

 

I see two options: 1) create two elements: display form and sort form. The trick in implementation will be to keep links between the two forms so it is known that they represent the same string. 2) Have the non-filing coding be part of the string. There is an option to do this in MARC (never implemented in the U.S.). The disadvantage is that it needs to be understood by everyone who will receive the string with this special coding.

 

<x88>The <x89>wizard of Oz

 
"Existence in x collection"

There are four call number fields (050, 055, 060, 070) that include a binary element for whether the item is in the related collection, e.g. "Existence in NAL collection" on the NAL call number tag (070). This happens to be an indicator, but it really is a binary data element relating to holdings. In the section on the 0XX fields, I treat these as free-standing data elements. My thinking is that their placement on the fields for the call numbers is convenient but the information is about the primary resource of the record.

 
II. Indicators that change or enhance the meaning of the field

 
Identifying sources

A large number of the indicators are used to identify the authoritative source of some of the data in the field. I say "some" of the data because MARC fields are designed around display, not semantics, and therefore can contain subfields that cover more than one logical data entity. The indicators that identify sources give the information that would normally be included in a URI; that is, they provide uniqueness for the data in the subfields, and they indicate the authoritative source of the data.

 

The indicators have a variety of names:

code source 9052, 072)

national bibliographic agency (016)

number source (086)

source of call number (050, 060)

source of classification number (082)

source of code (041, 047)

source of term (656. 657)

subject heading system/thesaurus (600, 610, 611, 630, 648, 650, 655)

 

In most cases, the indicator has values ranging from 0 to 5 or 6. Any source not included in that value list is given in the subfield $2. Indicator value 7 means "Source specified in $2," and therefore serves as a re-direct to the $2 subfield. There are two significant aspects to this: the first is that the subfield $2 has the same role as an indicator even though it is a subfield; the second is that the $2 represents a much expanded list of possible sources. Fortunately, the $2 is not free text but takes its values from the MARC source codes for vocabularies, rules and schemas.

 

It is my assumption that the information about the source does not apply to the control subfields ($3, $5, $6, $8). These subfields have a different role, generally to create linkages between fields in the same record.

 
Identifying Element Types

These indicators definitely change the meaning of the field. They are generally a way to get more than one meaning out of a single MARC tag. For example:

 

545 - Biographical or Historical Data

First indicator:

0 - Biographical sketch

1 - Administrative history

 

Some of these overlap with the display indicators. In the case below, there is a clear type ("Mailing") and an uncontrolled display field ($i) that covers every other kind of type. (If the vocabulary of that $i were controlled, then you would have multiple types. Since it isn't controlled, you have "Mailing" and "other".)

 

270 - Address

Second indicator:

0 - Mailing

7 - Type specified in subfield $i

 

Then again, the 246 second indicator provides a clear list of types:

 

246 - Varying Form of Title

0 - Portion of title

1 - Parallel title

2 - Distinctive title

3 - Other title

4 - Cover title

5 - Added title page title

6 - Caption title

7 - Running title

8 - Spine title

 

It's not always clear to me why some of the distinctions are needed, or if any systems pay attention to them. Some examples of these:

 

655 - Index Term-Genre/Form

First indicator:

# - Basic

0 - Faceted

 

100 - Main Entry-Personal Name

First indicator:

0 - Forenamne

1 - Surname

3 - Family name

 

 

 
Pseudo-display controllers

I was surprised to discover that some of the "display constant controllers" actually refine the meaning of the tag. These will need to be treated as semantically separate elements in the analysis.

 
Tag + indicator label
	Indicator values
505 Contents note, indicator 1, Display constant controller
	0 - Contents
1 - Incomplete contents
2 - Partial contents
8 - No display constant generated
511 Participant or performer note, indicator 1, Display constant controller 	

0 - No display constant generated
1 - Cast

(used when note contains cast list, but note does not always have that)
520 Summary, etc., indicator 1, Display constant controller 	

# - Summary
0 - Subject
1 - Review
2 - Scope and content
3 - Abstract
4 - Content advice
8 - No display constant generated

(adds meaning to 'etc.')
521 Target Audience Note, indicator 1, Display constant controller 	

# - Audience
0 - Reading grade level
1 - Interest age level
2 - Interest grade level
3 - Special audience characteristics
4 - Motivation/interest level
8 - No display constant generated

(defines the aspect of the target audience that is included)
555 Cumulative index/Finding Aids Note, indicator 1, Display constant controller 	

# - Indexes
0 - Finding aids
8 - No display constant generated

(two things carried in otherwise undistinguished field)

 

 
 
III. Other indicator functions
 
IV. Indicators, Fields and Subfields

Because the MARC indicators are at the field level, it might be logical to assume that they modify the entire field. The source and type indicators, and the display indicators that actually modify the meaning of the field, generally modify the combined set of subfields except the control subfields ($2-$8). (I am still checking to see if I can find any cases of indicators that modify the meaning of a control subfield.)

 

Many indicators appear to modify only the $a subfield, such as the non-filing indicator in 245, or the "Type of personal name entry element" in the x00 name fields. These fields can have many other subfields that are not affected by the indicator value.

 

The indicators that provide only display constants that do not affect the meaning of the field (described in section I) are at the field level, but only indicate a display constant that would precede the field; they do not modify or amplify the field at all.
