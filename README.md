# UTF-8 Module for Lua 5.1

This library provides a pure-Lua implementation of the `utf8` module introduced in Lua 5.3, offering the functions listed in the [latest docs](https://www.lua.org/manual/5.4/manual.html#6.5). It should be compatible with Lua 5.1, Lua 5.2 and LuaJIT.

On top of that, this version of the library has been extended with some additional functions:

- `utf8.force(str)` for making a copy of a string where all of its bytes represent valid UTF-8 codepoints. Any invalid byte sequences are replaced with the Unicode "Replacement Character" (U+FFFD).
 - `utf8.sub(str, i, j)` for extracting UTF-8 substrings by using codepoint indexes instead of byte indexes.
 - `utf8.chars()` for iterating over a UTF-8 string. It works in a similar fashion to `utf8.codes()`, except it returns substrings on each key/value pair instead of a numeric codepoint.
 - `utf8.upper(str)` for converting all characters in a UTF-8 string to uppercase, even if some of them are encoded in multiple bytes.
 - `utf8.lower(str)` for converting all characters in a UTF-8 string to lowercase, even if some of them are encoded in multiple bytes.
 - `utf8.title(str)` for converting all words in a UTF-8 string to titlecase, accounting for multi-letter characters with a special titlecase form.


In order to use this library, require it into the `utf8` global, or use the variable of your preference:

```lua
utf8 = require('utf8');
```

**Note:** This library depends on a global `bit` library being present, like the one included with LuaJIT 2.0.3. If you are not using LuaJIT, please make sure to load a compatible `bit` library before loading this one.
