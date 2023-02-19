# yuiop

## examples

    $ ./yuiop hllo.yuiop   # The classic.
    $ ./yuiop put.yuiop    # 'cat' clone.
    $ ./yuiop yup.yuiop    # 'yes' clone. Press CTRL-C.
    $ ./yuiop ho.yuiop hi  # 'echo' clone.

## statements

### `loop`

`loop` begins a loop statement. The body of the loop
follows the `loop` keyword and must be enclosed in `{` and
`}`. The loop can be exited with the `noloop` statement.

```c
loop {
    /* ... */
}
```

See `yup.yuiop` for an example of `loop`.

### `noloop`

`noloop` stops the inner-most `loop` statement.

`noloop` must be terminated by a `;`.

`noloop` often appears inside of an `on` statement to
conditionally exit the loop.

```c
loop {
    /* ... */
    on (/* ... */) {
        noloop;
    }
    /* ... */
}
```

See `ho.yuiop` for an example of `noloop`.

### `on`

`on` begins a conditional statement. The condition follows
the `on` keyword and must be enclosed in `(` and `)`. The
body, which is only executed if the condition is true, must
be enclosed in `{` and `}`.

```c
Yoyo in = in_h();
on (in == 'y') {
    p_yoyo("yup.\n");
}
on (in == 'n') {
    p_yoyo("nop.\n");
}
```

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

`Nop p_h(I h)`: Print the character `h`. Note that `h` is
not printed as a decimal number; `h(69)` prints the letter
E.
Mneumonic: **P**rint c**H**aracter

`Nop p_yoyo(Yoyo yoyo)`: Print each character in `yoyo`, excluding the
null terminator. Prints nothing if `yoyo` is `no_yoyo`.
Mneumonic: **P**rint **YOYO**

## input

### `in_h`

`I in_h()`: Read one character from standard input. If there
is no character to read, returns `no_h` instead.
Mneumonic: **IN**put c**H**aracter

### `ui`

`Yoyo ui(I i)`: Return one entry from the command line given
its index *i*. Index `0` is the command name. Index `1` is
the first argument. Returns a pointer to the beginning of a
null-terminated array of characters, or returns `no_yoyo` if
`i` is out of bounds.
Mneumonic: **U**ser **I**nput

## file I/O

### `lo_yoyo`

`Yoyo lo_yoyo(Yoyo nom)`: Load a file named *nom*. Returns a
new `Yoyo` containing the text file's content.
Mneumonic: **LO**ad **YOYO**

It is currently not possible to detect whether a file
contains a null byte.

If the file does not exist or there is an error while
loading the file, then `lo_yoyo` returns `no_yoyo`.

## control flow

### `no_mo`

`Nop no_mo(I ok)`: Exit the program with status code `ok`.
If `ok` is zero, then the program indicates that it was
successful. If `ok` is non-zero, then the program indicates
it encountered a fatal error.
