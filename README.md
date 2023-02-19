# yuiop

## standard types

### `I`

A 32-bit integer.

### `Yoyo`

A pointer to a null-terminated array of characters (C
string), or `no_yoyo`.

### `Nop`

Unit type. Only allowed as the return type of a function.

## standard functions

### output

`Nop p_i(I h)`: Print the character `h`. Note that `h` is
not printed as a decimal number; `h(69)` prints the letter
E.
Mneumonic: **P**rint **I**nteger

`Nop p_yoyo(Yoyo yoyo)`: Print each character in `yoyo`, excluding the
null terminator. Prints nothing if `yoyo` is `no_yoyo`.
Mneumonic: **P**rint **YOYO**

## input

### `ui`

`Yoyo ui(I i)`: Return one entry from the command line given
its index *i*. Index `0` is the command name. Index `1` is
the first argument. Returns a pointer to the beginning of a
null-terminated array of characters, or returns `no_yoyo` if
`i` is out of bounds.
Mneumonic: **U**ser **I**nput
