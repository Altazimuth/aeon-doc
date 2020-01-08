# String

Strings have many methods attached to them for manipulating text.

```cpp
class String
{
   uint32_t npos() const;
   uint32_t length() const;
   bool empty() const;
   String &clear();
   char charAt(uint32_t index) const;
   uchar ucharAt(uint32_t index) const;
   String &push(char ch);
   String &pop();
   String &concat(const String &in);
   bool compare(const String &in) const;
   uint32_t hashCode() const;
   uint32_t hashCodeCase() const;
   int strCmp(const String &in) const;
   String &copy(const String &in);
   String &copyInto(String &inout) const;
   void swapWith(String &inout);
   String &toUpper();
   String &toLower();
   int toInt() const;
   uint findFirstOf(int) const;
   uint findFirstNotOf(int) const;
   uint findLastOf(int) const;

   String &opAssign(const String &in); // String = String
   String &opAddAssign(const String &in); // String += String
   bool opEquals(const String &in) const; // String == String
   bool opCmp(const String &in) const; // String [comparison operator] String
   int opShl(const String &in) const; // String << String
   String &opShl(int); // String << int32_t
   String &opShl(double); // String << double
   int get_opIndex(int) const; // String[int]
   void set_opIndex(int, int); // String[int] = int
}
```

### `npos`

TODO: Make "static" class property.

### `length`

Returns the number of characters in this string.

### `empty`

Returns whether or not the string is empty.

### `clear`

Clears the contents of a string.

### `charAt`

Returns `char` at a given index with a slower but safer method compared to `[]`.

### `ucharAt`

Same as `charAt` but returns a `uchar` instead of a `char`.

### `push`

Adds a character to the end of a string.

### `pop`

Deletes a character from the end of a string.

### `concat`

Adds another string to the end of a string.

### `compare`

Returns true if another string is equal to this one, otherwise returning false.

### `hashCode`

Returns the hash code of a string.

### `hashCodeCase`

Same as above but case-insensitive.

### `strCmp`

Compares characters in a string until a different one is found, and returns the
difference of those characters. Returns 0 if strings are the same, more than 0
if the first matching character has a greater value in the calling object than
the parameter, and less than 0 if said character has a lesser value in the
calling object.

### `copy`

Copies another string into this string, clearing this string first.

### `copyInto`

Copies this string into another string, clearing it first.

### `swapWith`

Swaps the contents of this string with another string.

### `toUpper`

Converts all characters in the string to uppercase.

### `toLower`

Converts all characters in the string to lowercase.

### `toInt`

Returns the string to an int32_t.
TODO: Don't use atoi good lord.

### `findFirstOf`

Returns the first index equal to a character. If the character is not found it
returns `String::npos()`.

### `findFirstNotOf`

Returns the first index not equal to a character. If such a character is not
found it returns `String::npos()`.

### `findLastOf`

Returns the last index equal to a character. If the character is not found it
returns `String::npos()`.

### `String = String`

Set the contents of this string to another string.

### `String += String`

Concatenate another string to the end of this string.

### `String == `String`

Returns true if another string is equal to this one, otherwise returning false.
Note that `!=` is the same but negated.

### `String [comparison operator] String`

Returns true if a given comparison is true based on ASCII ordinal.

e.g.
```cpp
"A" < "B"; // true
"a" < "B"; // false
"Charlie" < "Delta" ; // true
"Cookie" >= "Corsair"; // false
"Shark" <= "Shark"; // true
```

### `String << String`

Concatenate another string to the end of this string.

### `String << int32_t`

Concatenate the string representation of an integer to the end of this string.

### `String << int32_t`

Concatenate the string representation of a double-precision float to the end of
this string.

### `String[int]`

Get the character at a given index of the string.

### `String[int] = int`

Set the character at a given index of the string.

<!-- EOF -->
