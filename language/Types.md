<!-- vim-markdown-toc GFM -->

* [Types](#types)
* [Integer Types](#integer-types)
* [Fixed-point Type](#fixed-point-type)
* [Floating-point Types](#floating-point-types)
* [Strings](#strings)
* [Vectors](#vectors)
* [Arrays](#arrays)
* [Dictionary](#dictionary)
* [User Types](#user-types)
* [Read-only Types](#read-only-types)
* [Other Types](#other-types)

<!-- vim-markdown-toc -->

# Types

Aeon has several categories of types: Integer types, floating-point
(decimal) types, strings, vectors, names, classes, et al. There are a wide
variety of ways to use these types, as well as a wide variety of places they
are used.

Types determine what kind of value an object stores, how it acts within an
expression, etc. All objects, constants and enumerations have a type. Argument
lists use types to ensure a function is used properly.

Most basic types have methods attached to them, and both integer and
floating-point type names have symbols accessible from them. See the API
section for more information.

# Integer Types

Integer types are basic integral numbers. They include:

| Name        | Bits | Lowest value               | Highest value              |
| ----        | :--: | -----------:               | :------------              |
| `int8_t`    | 8    | -128                       | 127                        |
| `int16_t`   | 16   | -32,768                    | 32,767                     |
| `int32_t`   | 32   | -2,147,483,648             | 2,147,483,647              |
| `int64_t`   | 64   | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807  |
| `uint8_t`   | 8    | 0                          | 255                        |
| `uint16_t`  | 16   | 0                          | 65,535                     |
| `uint32_t`  | 32   | 0                          | 4,294,967,295              |
| `uint64_t`  | 64   | 0                          | 18,446,744,073,709,551,615 |

As the scripting engine has been optimized for 32 bit datatypes, using the
smaller variants is only recommended for accessing application specified
variables. For local variables it is better to use the 32 bit variant.

Some types have aliases as well:

| Name       | Aliases    |
| ----       | -------    |
| `int`      | `int32_t`  |
| `uint`     | `uint32_t` |
| `char`     | `int8_t`   |
| `uchar`    | `uint8_t`  |

In addition to the types in this table, there are aliases for every type in
the first integer types table, but without the `_t` suffix.

# Fixed-point Type

The fixed-point type, `fixed_t`, is 32-bit signed number, with 16 bits each for
the integer and fractional parts of the number. While there are no `fixed_t`
literals it is perfectly valid to assign them a value like `2.0`.

`fixed_t` is an extremely common type in Eternity, and by extension Aeon, being
used for nearly all non-integer numbers.

# Floating-point Types

Floating-point types hold exponents, generally represented as regular decimal
numbers. There are two floating-point types available to Aeon:

| Name     | Bits | Maximum digits |
| ---      | :--: | -------------- |
| `float`  | 32   | 6              |
| `double` | 64   | 16             |

Rounding errors may occur if more digits than the maximum number of digits are
used.

It is highly suggested to **avoid declaring floats,** and instead use `fixed_t`
where feasible. If you must use floats then try `double`s, as they are
precise enough to properly represent all values that a `fixed_t` can.

# Strings

| Name         |
| ----         |
| `String`     |

The `String` type is a mutable, garbage-collected string reference type.
Strings are an object, instances of a class. Their methods are detailed in the
API section.

# Vectors

| Name      |
| ----      |
| `vector2` |
| `vector3` |

There are two vector types in Aeon, `vector2` and `vector3`, which hold two
and three members, respectively. Their members can be accessed through `x`, `y`
and (for `vector3`,) `z`. `vector3` can additionally get the X and Y components
as a `vector2` with `xy`.

Vectors can use many operators and even have special ones to themselves. See
the Expressions and Operators section for more information.

# Arrays

| Name             |
| ----             |
| `array < Type >` |

Arrays take the form `array<Type>`, and hold a dynamic and arbitrary
number of `Type` elements, which can be accessed with the array access
operator.

It's worth noting that, unlike ZScript, AngelScript's arrays _can_ store other
arrays. This enables the ability to have multi-dimensional arrays.

<!-- TODO: Move to other document
```cpp
// Declare an int array of size 5 with all elements initialised to value 4.
array<int> int_arr(5, 4);

// Declare a string array which is implicitly of size three and has
// three explicitly-specified elements.
array<String> str_arr = {"Index Zero", "Index Eins", "Index Dos"};

// Declare a two-dimensional fixed_t array.
```
-->

# Dictionaries

| Name                         |
| ----                         |
| `dictionary < Type , Type >` |

Dictionary types take the form `dictionary<Type, Type>`.
They are not yet implemented.

# User Types

| Name                         |
| ----                         |
| Any class object             |

Any other identifier used as a type will resolve to a user class, structure or
enumeration type.

<!--
Types prefixed with `@` are native pointers to objects (as opposed to objects
placed directly in the structure's data.) This is not usable in user code.

A type name that is within a specific scope can be accessed by prefixing it
with a `.`. The type `.MyClass.MySubStructure` will resolve to the type
`MySubStructure` contained within `MyClass`.
-->

# Read-only Types

<!-- Would this be useful for EE?
| Name                | Usable as argument |
| ----                | :----------------: |
| `readonly < Type >` | Yes                |

A read-only type, as its name implies, may only be read from, and is
effectively immutable. They take the form `readonly<Type>`. Do note that this
is separate from the member declaration flag.
-->

# Other Types

| Name         | Description                                                     |
| ----         | -----------                                                     |
| `bool`       | Holds one of two values: `true` or `false`.                     |
| `void`       | Less type and more lack thereof. Only use is defining a function that returns no data. |
| `EE::Sound`  | Holds a sound reference.                                        |

<!--
Strings will implicitly convert to `EE::Sound`.
-->

<!-- EOF -->
