# Vim Cheat Sheet

## Basic Commands

- `yy` _copy a line_
- `p` _paste a line_
- `u` _undo changes_
- `CTRL+r` _redo changes_
- `V` _enter v-line mode_
- `CTRL+v` _enter v-block mode_ 

## Insert Commands

- `o` or `O` _Insert a new line under your cursor (o) or insert a new line above your cursor (O)_
- `cc` _Enter insert mode respecting the indentation_
- `A` _Enter insert mode at the end of the line_

## Delete Commands

- `dd` or `{n}dd` _delete a line or **n** number of lines._
- `dw` or `db` _delete one word ahead or one word backwards_
- `cw` or `ce` _delete a word and enter insert mode_
- `D` _delete everything ahead of your cursor_
- `C` _delete everything ahead of your cursor and enter insert mode_
- `S` _delete the current line and enter insert mode_
- `x` or `s` _delete a character or delete a character and enter insert mode_

## Navigation Commands

- `:{n}` _go to specific line number in the buffer_
- `gg` _go to the start of the buffer_
- `G` _go to the end of the buffer_
- `w` or `e` _go a word forward_
- `b` _go a word backwards_
- `$` _go to the end of the line_
- `^` _go to the start of the line_
- `%` _go to matching pair_
- `CTRL+u` _"scroll up" in the current buffer_
- `CTRL+d` _"scroll down" in the current buffer_
- `f{c}` or `F{c}` _jump to a character **c** (when shift is pressed you go backwards)_
- `t{c}` or `T{c}` _jump behind a character **c** (when shift is pressed you go backwards)_
> _You can jump one result forward in character results with `;` or jump one result backwards with `,`_


## Search Commands

- `%s/{text-to-replace}/{new-text}/` _replace text_
- `s/\(.*\)/repeat \1`
- `/{word}` _search for a text press **n** to look forward and **shift+n** to look backwards_

## Misc
- `g<Ctrl>a` _Increment numbers_

## Useful Combos

### First set of combos

- `df*` or `dt*`
- `vf*` or `vt*`
- `yf*` or `yt*`
- `ct*` or `ct*`

### Second set of combos

[Tutorial](https://youtu.be/qZO9A5F6BZs)

- `viw`
- `vi*` or `va*` _Select everything inside the character ([], (), "", {})_
- `yi*` or  `ya*`
- `ci*` or `ca*`
- `di*` or `da*`
