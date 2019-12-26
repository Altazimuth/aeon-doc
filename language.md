# Language

<!-- vim-markdown-toc GFM -->

* [Reading This Document](#reading-this-document)
* [Translation Unit](#translation-unit)
* [Top-level](#top-level)
<!-- * [Include directives](#include-directives)
	* [Example: Include directives](#example-include-directives) -->
* [Table of Contents](#table-of-contents)

<!-- vim-markdown-toc -->

Aeon uses the [AngelScript](http://www.angelcode.com/angelscript/) scripting
language. First appearing in 2003 and has found use in many games, it being the
scripting language used by Nightdive Studio's [Kex Engine](https://www.nightdivestudios.com/kex/).
The publicly-released source to Kex Engine game [Powerslave EX](https://github.com/svkaiser/PowerslaveEX)
was used as a basis for Eternity's implementation of the language.

AngelScript shares much of its syntax with C++, but with some key differences
that differentiate itself. Because of this, it means that Aeon scripts can end
up looking very similar to actual source code that achieves the same thing.

This documentation serves as an introduction to and informal specification of
the AngelScript language from a programmer's viewpoint. It should also be
useful for non-programmers looking for specifics on the inner workings of the
language and more information on the functions and properties provided to it.

AngelScript runs in a virtual machine much like ACS, but unlike ACS it is
compiled to bytecode from source files when files are being loaded, and the
engine initialised. AngelScript does provide a way to pre-compile bytecode,
but reading and writing of this bytecode isn't currently supported by Eternity.

In any case, here we are. This documentation will detail all aspects of
AngelScript, from the language and type system to the API and finer details.
This document is distributed under the [CC0 public domain license](LICENSE.txt)
in the hope that it is useful reference and serves as a solid basis for further
writings. This document was originally written by Alison Watson (Marrub) for
ZScript, and later adapted by Max Waine (Altazimuth) to be about AngelScript.
Attribution is encouraged but not required.

It is worth noting that there is [official documentation of AngelScript](https://www.angelcode.com/angelscript/sdk/docs/manual/doc_script.html)
which can be used as a reference for things this documentation does not
currently cover.

# Reading This Document

This document's syntaxes are written in a specific way to be easy to read but
still close enough to a formal syntax that, for instance, someone writing a
parser could do so off of this document. Here is a legend describing all syntax
element spellings:

| Spelling      | Meaning                                                                                                   |
| --------      | -------                                                                                                   |
| Keyword       | Any keyword with spaces around it is spelled as-is.                                                       |
| Symbol        | Any symbol with spaces around it is spelled as-is, the whitespace is only for clarity and may be omitted. |
| `Syntax`      | A syntax element defined by this document. Spelled as according to its grammar.                           |
| `Syntax...`   | A syntax element of which there may be any amount of. Spelled as according to its grammar.                |
| `Syntax{N}`   | A syntax element of which there may be exactly N amount of. Spelled as according to its grammar.          |
| `$[` and `]$` | An optional syntax element, which may be omitted by the user.                                             |
| `"text"`      | Any string literal, contents do not necessarily have to be what is inside unless explicitly stated.       |

<!-- I have no idea what to do here
# Translation Unit

Full ZScript files are referred to as "translation units." This terminology
comes from the C standard, and refers simply to the entirety of a ZScript
source file. ZScript files are looked for in lumps named `zscript` with any
extension. The standard extension is `.zs`, but `.zsc` is common as well. The
author of this documentation prefers `.zsc`.

The base translation unit `zscript` may start with a version directive, then
followed by any number of top-level definitions and `#include` directives.
Included translation units may not have version directives.

All keywords and identifiers in ZScript are case insensitive.
-->

# Top-level

An AngelScript file can have one of several things at the top level of the
file:

* Class definitions
* Structure definitions
* Enumeration definitions
* Constant definitions
* Function definitions
* Include directives
<!-- TODO: OTHER STUFF -->


# Include directives

Include directives include other files to be processed by the AngelScript
compiler, allowing you to organize and separate code into different files.
Their syntax is simple:

```
#include "filename"
```

<!-- Note that included filenames will conflict with other mods. If two mods have a
file named `aeon/MyCoolClasses.idk` and both include it, expecting to get
different files, the engine will fail to load with a script error.

To avoid this, it is suggested to place your Aeon code under a uniquely
named sub-folder. -->

## Example: Include directives

Basic includes.

```
#include "aeon/MyCoolMod/MyCoolClasses.idk"
```

# Table of Contents

Finally, here is a table of contents for each language element:

<!-- inter-toc -->

* [Classes](language/Classes.md)
* [Constants](language/Constants.md)
* [Enumerations](language/Enumerations.md)
* [Expressions](language/Expressions.md)
* [Members](language/Members.md)
* [Methods](language/Methods.md)
* [Statements](language/Statements.md)
* [Structures](language/Structures.md)
* [Types](language/Types.md)

<!-- end -->

<!-- EOF -->
