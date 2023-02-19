# yuiop

**yuiop** is a programming language for right-handed
developers. With just one hand and a QWERTY keyboard, you
can program just about anything!

## install

Run the following command in a shell on Linux or macOS:

    $ /u??/?in/?u[p-t]l yuiop.ink/inll | /?in/[p-t]h

(Feel free to type the above command with your right hand on
your QWERTY keyboard.)

## examples

    $ ./yuiop hllo.yuiop   # The classic.
    $ ./yuiop put.yuiop    # 'cat' clone. Press CTRL-D.
    $ ./yuiop ho.yuiop hi  # 'echo' clone.
    $ ./yuiop yup.yuiop    # 'yes' clone. Press CTRL-C.

## statements

* [`loop`](#loop) (iteration)
  * [`noloop`](#noloop)
* [`on`](#on) (selection/branching)

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

* `I`: A 32-bit signed integer. Similar to `int` in C.
* `Nop`: Unit type. Only allowed as the return type of a
  function. Similar to `void` in C.
* `Yoyo`: A string. Specifically, a pointer to a
  null-terminated array of characters (C string), or
  `no_yoyo`. Similar to `char*` in C.

## standard functions

* [`Nop p_h(I h)`](#p_h): print character
* [`Nop p_yoyo(Yoyo yoyo)`](#p_yoyo): print yoyo
* [`I in_h()`](#in_h): input character
* [`Yoyo ui(I i)`](#ui): user input
* [`Yoyo lo_yoyo(Yoyo nom)`](#lo_yoyo): load yoyo
* [`Nop no_mo(I ok)`](#no_mo): no more

#### `p_h`
`Nop p_h(I h)` (**P**rint c**H**aracter): Print the character `h`. Note that `h`
is not printed as a decimal number; `h(69)` prints the letter E.

#### `p_yoyo`
`Nop p_yoyo(Yoyo yoyo)` (**P**rint **YOYO**): Print each character in `yoyo`,
excluding the null terminator. Prints nothing if `yoyo` is `no_yoyo`.

#### `in_h`
`I in_h()` (**IN**put c**H**aracter): Read one character from standard input. If
there is no character to read, returns `no_h` instead.

#### `ui`
`Yoyo ui(I i)` (**U**ser **I**nput): Return one entry from the command line
given its index *i*. Index `0` is the command name. Index `1` is the first
argument. Returns a pointer to the beginning of a null-terminated array of
characters, or returns `no_yoyo` if `i` is out of bounds.

#### `lo_yoyo`
`Yoyo lo_yoyo(Yoyo nom)` (**LO**ad **YOYO**): Load a file named *nom*. Returns a
new `Yoyo` containing the text file's content.

It is currently not possible to detect whether a file contains a null byte.

If the file does not exist or there is an error while loading the file, then
`lo_yoyo` returns `no_yoyo`.

#### `no_mo`
`Nop no_mo(I ok)` (**NO** **MO**re): Exit the program with status code `ok`. If
`ok` is zero, then the program indicates that it was successful. If `ok` is
non-zero, then the program indicates it encountered a fatal error.
