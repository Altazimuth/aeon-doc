<!-- vim-markdown-toc GFM -->

* [Enumeration Definitions](#enumeration-definitions)
	* [Example: Enumeration definitions](#example-enumeration-definitions)

<!-- vim-markdown-toc -->

# Enumeration Definitions

An enumeration is a list of named numbers, which by default will be incremental
from 0. They decay to the type `int`, and unlike ZScript or C++ the type that
an enum is represented by cannot be changed to any other integer type.

An enumeration definition takes the form:

```cpp
enum Identifier
{
	$[Enumerator $[ , Enumerator]$... $[ , ]$]$
}
```

Optionally followed by a semicolon.
Enumerators can either be incremental (from the last enumerator or 0 if there
is none) or explicitly set with the syntax `Identifier = Expression`.
Enumerators must be followed by a comma unless it is the end of the list.

Enumerator syntax is:

```
Identifier $[ = Expression]$
```

## Example: Enumeration definitions

```cpp
// Basic enumeration.
enum MyCoolEnum
{
	A_THING, // Has value int(0) ...
	BEES, // ... 1 ...
	CALCIUM, // ... 2 ...
	DEXTROSE, // ... and 3.
}

// Less trivial example.
enum MyCoolerEnum
{
	A = 500, // Has value 500,
	B, // 501,
	C = 200,
	D, // 201,
	E, // and 202.
}
```
<!-- EOF -->
