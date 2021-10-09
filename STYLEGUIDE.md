# Style guide

## Writing

### Spelling

- [**American English**](https://en.wikipedia.org/wiki/American_English) (en_US) throughout.

### Punctuation

Use the [Oxford comma](https://en.wikipedia.org/wiki/Serial_comma):

> Pharoers are friendly, helpful, and kind.

not

> Pharoers are friendly, helpful and kind.

### Markup

Snippets of Pharo (or other) code inline should be marked up as fixed width, `==`:

> create a new instance with ==MyObject new==

References to files should also be marked up as fixed width, `==`:

> simply import your ==.image== and its associated ==.changes== files using the launcher.

References to GUI buttons inline should be marked up in bold, `""`:

> Here we clicked on the top left ""New"" icon to download a new image.

#### Key strokes (and key combinations)

Keys typed should be capitalized.

> `Shift-D`

not

> `Shift-d`

A single chord should be written with hyphens:

> `Ctrl-Alt-Del`

Sequences should be written with a space between the parts:

> `Cmd-O Cmd-W`

would open a Playground

https://en.wikipedia.org/wiki/Modifier_key

##### macOS

The modifier keys should always be written in the order `Control Option Shift Command`

The modifier keys should be written in abreviated form of `Ctrl Option Shift Cmd`

https://developer.apple.com/design/human-interface-guidelines/macos/user-interaction/keyboard/

##### Windows / Linux

The modifier keys should be written in the order `Control Alternate Meta Shift`

The modifier keys should be written in the abreviated form of `Ctrl Alt Meta Shift`


### Titles / Subtitles

Titles written in sentence casing, without a terminating period:

> A quick tour of Pharo

not

> A Quick Tour of Pharo.
