# splusiniloader

Program : INI Loader 1.0
By      : Nicholas Pepper
Version : 1.0

This simple module takes an configuration file (default is \NVRAM\system.conf) and 
parses information out of it.  You can send it digital, analog, or serial values 
directly from an ini style text file when sections are not being used.  Input after 
semi-colons is treated as a comment.

When a section comes up, all strings following the section header are directly
passed out the bus for processing by other modules.

What this means, is that all parameters that you would like to load directly into
this module generically need to be defined before a section is declared.  You
have 1 to 100 signals defined for each type of signal for you to utilize.

For analog values specifically, you can append an 's' to the number and the module
will do the conversion to ticks for you.  This is uesful for time parameters.
**NOTE** that I do not process HH.MM.SSs format, everything must be in generic
seconds with the maximum time of 655.35 seconds.

`[section]`

The above formatting starts a section, and all values, no matter what they are,
are directly passed to the bus out.  The only exception to this is still comments,
which will just be dropped.

Format of the file for generic signals:

`<value_type><value_number>=<data>`

`dv1=0 (or 1) : set digital output ### to either 0 or 1
av1=512 : set analog value 1 to a value of 512
sv1=Conference : set serial value 1 to "Conference"`

Format of the file for other module signals:

`[<section>]

<key>=<value>`

Version History

1.0		Initial version
