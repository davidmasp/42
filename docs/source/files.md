# Virtual files

What do people think of people who do keep a messy and unorganized
desk at the office? Should we feel shame in keeping a untidy virtual
desktop?

The answer is yes!

Not just because of what your colleague will think about your mental
disorder after but because maintaining order in the digital era saves time!

## Naming

<!---
Current structure is:
    1. why is this important
    2. aims of a good system
    3. rules
    4. exceptions
    5. examples
-->

Naming a file is high-cost decision. Not only takes time to choose a file
but if done incorrectly it will also cost time to search for that file,
either visually (through a file browser) or programmatically
(through a script). The idea of a good naming system has to do with
integrating both worlds. File metadata (aka a database)
is also a useful resource for finding files but it requires more effort and
will be avoided.

A good file naming system should:

* Be easy to use with a computer based system (script)
* Contain meaningful information
* Define the contents in any context
* Be short
* Not too short

### Naming files - elements

The name of the file should be informative enough so if seen in any
context, the contents of it can be understood by multiple people.

It has to contain the following elements (exceptions in brackets):

* Date (if required but always first)
* Main describing element
* Possible modifiers
* Parameters that describe the file itself (optional)
* Source of the file (if not self-produced or not clear)
* File format (if the file extension is not enough to determine that)

The order should be maintained if possible but not enforced. If multiple
similar files are in the same folder the same set of elements should
be used for all similar files although some parameters or modifiers
are not relevant for some files.

### Naming files - style

The file name should contain a mixed style, with each element (see below)
written in `camelCase` and each of these elements separated by an underscore
`_`. The only exceptions for dates (see below).

<!---
This aims to maximize computer interpretability and parsing. It also
represents a 2 space-types system like our common writing with spaces
and return carriages. In an horizontal (1-dimension) world like filenames
the camel case substitutes the space and the underscore the return
-->

The extension should always be present in the last part of the file name after
a period. There are some exceptions:

* hidden files
* scripts (CLI)
* Other protected files (i.e. `Makefile`)

### Naming files - date

The date of the files should be used when relevant. It should always be based
in the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. Common variant
like for example the truncated version are acceptable and sometimes
recommended to avoid clashes with other styling rules (above).

If archiving, the date of the filename should always be the first element.

If versioning date might be included as any other element separated by
underscores. Elements like "finalVersion" or "thisIsTheOne" should be if
possible avoided.

### Naming files - examples

This would be an idea of how to name videos of the last years of high-school
of a girl names Maria.

```txt
~ [date]_[main]_[modifier]_[param].mp4
~ 20100406_promVideo_mariaAndJames_1.mp4
~ 20100406_promVideo_mariaAndJames_2.mp4
~ 20100406_promVideo_mariaAndJames_3.mp4
~ 20100416_graduation_mariaDiploma_1.mp4
~ 20100416_graduation_mariaSpeech_1.mp4
```

Note that although the index parameter is not useful for the graduation videos
we should maintain it for consistency if parsing.

### Naming files - major exceptions

* If files are not meant to be under visual inspection as files. One example
are photo albums which are meant to be visualized as pictures. They
should at least contain minimal metadata as filenames. An example is
`IMG_213`
* When it is not achievable due to the amount of files
* If they are computer generated and not meant for human visual inspection
* If they are linked to a rich metadata or documentation
