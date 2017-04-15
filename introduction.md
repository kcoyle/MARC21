# Introduction

There is no consensus within the profession on the need to replace the long-standing MARC record format with something different. A common reply to the suggestion that library data creation needs a new data schema is the phrase: "If it ain't broke, don't fix it." This is often uttered by catalogers who are comfortable working with the current record format. In fact, there is much that is broken about MARC from a systems and from a technology point of view. Fixing MARC and replacing it are different things. It does little good to replace MARC if the problems it has are not fixed, and it does little good to replace MARC if its benefits are not also carried over. 

Some of the problems with MARC are addressed in the goals of projects such as BIBFRAME. BIBFRAME's stated goals were 

1. Differentiate clearly between conceptual content and its physical manifestation(s) (e.g., works and instances)
2. Focus on unambiguously identifying information entities (e.g., authorities)
3. Leverage and expose relationships between and among entities

It also had a stated goal of bringing library cataloging into the "web-scale world" by making use of linked data. These goals are fine, but say little about the details, and library cataloging has a lot of details. 

# What is MARC?

The MARC21 record has at least four distinct components. The first is the data processing format of the record itself, originally described in the ANSI/NISO Z39.2 standard and now also recorded as ISO 2907. This record format is quite flexible, allowing the creation of records that look little like the MARC21 record we know. The MARC21 record is a particular application of Z39.2, using two indicator positions in each field, and a one-character subfield code (a-z, 0-9). Other options provided by Z39.2 would have allowed up to nine characters for both the indicators and for the subfield code. Thus, a record could have been formed that used two characters for the subfield code, and therefore would have provided for over one thousand subfields in each field rather than the 36 (lowercase a-z plus 0-9) in MARC21. Or the decision could have been, for example, to allow 6 characters for the subfield code and subfields could have been mnemonic terms, such as "$lastnm," "$forenm," "$title_". The MARC "instance" of Z39.2, however, chose to make use of two indicator positions and a single character subfield code. That instance, the second component of the MARC21 record, is what many people assume is the only possible use of the Z39.2 record because it has become so very familiar to us. 

The third component of the MARC21 record is the assignment of semantics to particular tags and subfields. What began as a fairly simple record in 1970 has grown greatly in complexity as more tags and subfields are defined for new data elements. Based on the data element list in Appendix E of Tom Delsey's Functional Analysis of the MARC 21 Bibliographic and Holdings Formats,  there are almost 2300 data elements in the bibliographic format and 2600 in the Bibliographic and Holdings Formats combined. 

The fourth component consists of actual values that are included in the MARC21 standard. The majority of fields in the MARC21 record are textual in nature and do not have a fixed set of values. However, sets of values for some data elements, such as codes for languages or place of publication, are based on a finite set of accepted values. These values tend to be in the "fixed fields," that is, fields of fixed length that consist of fixed length coded data elements. As an example, the data element used to describe the color for visual materials has the following values:

```
MARC21 Code	Description
b 	 Black and white
c 	 Multicolored
h 	 Hand colored
m 	 Mixed
u 	 Unknown
z 	 Other (Includes stained, tinted, or toned items.)
| 	 No attempt to code
```

Most of these code lists are short, but some lists, like those for place of publication and language, are very long. These lists are maintained outside of the MARC21 standard itself.

In addition to these four components, MARC21 consists of five separate standards: Bibliographic, Holdings, Authority, Classification, and Community Information. The latter two, Classification and Community Information, although they use the same record format as the MARC21 record, have little or no interaction with the other record formats in systems today. The former three, Bibliographic, Holdings, and Authority formats, are related either hierarchically or semantically to each other (with the Bibliographic record as the base that the other two enhance) and are used heavily by library systems. Any structural change to Bibliographic format must be reflected also in the Holdings and the Authority formats. This paper will address the MARC21 Bibliographic format, with the assumption that if changes to that format are approved by the appropriate community, those changes will also be made in the other two related formats. 
