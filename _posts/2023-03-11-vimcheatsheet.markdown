---
layout: post
title: "Vim shortcuts"
date: 2023-03-11 09:00:00 +0100
categories: kubernetes
---

Vim is the editor you are most likely to find on a bare Linux box or inside a container, and it is the default editor behind `kubectl edit`. These are the shortcuts I actually use day to day.

#### Modes
* `esc` - return to **normal** mode from any other mode. When in doubt, press it.
* `i` / `a` - enter **insert** mode before / after the cursor.
* `I` / `A` - insert at the start / end of the line.
* `o` / `O` - open a new line below / above and enter insert mode.
* `v` - **visual** mode (select characters).
* `V` - visual line mode (select whole lines).
* `ctrl+v` - visual block mode (select a column/rectangle).
* `:` - **command-line** mode.

#### Saving and quitting
* `:w` - save.
* `:q` - quit (fails if there are unsaved changes).
* `:wq` or `:x` or `ZZ` - save and quit.
* `:q!` or `ZQ` - quit and discard changes.
* `:w filename` - save as a new file.
* `:e!` - reload the file, throwing away unsaved changes.

#### Moving around
* `h` `j` `k` `l` - left, down, up, right.
* `w` / `b` - next word / previous word.
* `e` - end of the word.
* `0` / `^` / `$` - start of line / first non-blank character / end of line.
* `gg` / `G` - top / bottom of the file.
* `42G` or `:42` - go to line 42.
* `ctrl+d` / `ctrl+u` - scroll half a page down / up.
* `%` - jump to the matching bracket.
* `f<char>` / `F<char>` - jump forward / back to the next occurrence of a character on the line. `;` repeats it.

#### Editing
* `x` - delete the character under the cursor.
* `dd` - delete (cut) the line.
* `dw` - delete to the end of the word.
* `D` - delete to the end of the line.
* `cw` - change word (delete it and enter insert mode).
* `cc` - change the whole line.
* `r<char>` - replace a single character.
* `J` - join the line below onto the current one.
* `u` - undo.
* `ctrl+r` - redo.
* `.` - repeat the last change. One of the most useful keys in Vim.

Most commands take a count, e.g. `3dd` deletes three lines and `5j` moves down five lines.

#### Copy and paste
* `yy` - yank (copy) the line.
* `yw` - yank a word.
* `y` - yank the visual selection.
* `p` / `P` - paste after / before the cursor.
* `"+y` / `"+p` - copy to / paste from the system clipboard (if Vim was built with clipboard support).

#### Search and replace
* `/text` - search forward. `?text` searches backwards.
* `n` / `N` - next / previous match.
* `*` - search for the word under the cursor.
* `:noh` - clear search highlighting.
* `:s/old/new/` - replace the first match on the current line.
* `:%s/old/new/g` - replace every match in the file.
* `:%s/old/new/gc` - same, but confirm each replacement.

#### Indenting (handy for YAML)
* `>>` / `<<` - indent / unindent the line.
* `>` / `<` - indent / unindent the visual selection. Press `.` to repeat.
* `=` - auto-indent the selection.
* `:set paste` - paste text without Vim re-indenting it. Turn it off with `:set nopaste`.

#### Multiple files and windows
* `:e filename` - open another file.
* `:sp` / `:vsp` - split the window horizontally / vertically.
* `ctrl+w` then `w` - cycle between windows.
* `:bn` / `:bp` - next / previous buffer.

#### Useful settings
* `:set number` - show line numbers (`:set nu` for short).
* `:set list` - show tabs and line endings, useful for finding a stray tab in a YAML file.

For Kubernetes work I put the following in `~/.vimrc` so YAML is indented with two spaces:

```vim
set expandtab
set tabstop=2
set shiftwidth=2
set number
```
