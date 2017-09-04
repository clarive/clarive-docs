---
title: Search Syntax
index: 5000
icon: search-small
---

Most of Clarive's Lists and Reports have search boxes. Terms introduced in the search boxes are case insensitive and
represent an OR search.

For example, a search for the following terms:

    gui security

will match all documents that have EITHER *gui* or *security* in one of the documents' fields, be it
a [Resource](/concepts/resource) or a [Topic](/concepts/topic).

On the other hand, the following query:

    +gui +security

will only match documents that have BOTH *gui* and *security* in any of the documents' fields. One field, i.e. "title"
may contain the word "gui", and the other, i.e. "department" may contain the word "security".

### Case Sensitivity

All searches are case insensitive. To make them case sensitive, put double quotes around the word:

    "GUI"

This will only search for documents with the word "GUI" in full uppercase.

In summary, here's a sample of supported search syntax:

    term "term"  - case insensitive
    Term  - case insensitive
    T?rm  - matches 1 character in ?
    T*rm  - matches 0 or more characters in *
    +term1 +term2  - must have both term1 and term2
    +term  -term2  - must have term1 but not term2
    /term regex.*/  - regular expression

### Field searching

Clarive supports also a limited set of field searches. Field searches search only specified fields.

    status:"QA Done"

Searches only the "QA Done" status.


The tool also allows the use of hash for direct access to a specific Topic.

    #123456

This goes directly to the specific Topic.
