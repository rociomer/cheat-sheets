### Using [Vim](https://www.vim.org/)

Vim is a text editor that makes it very convenient to edit files without having to exit the terminal. 

You can customize many things in the editor by editing the .vimrc file. See [this post](https://dougblack.io/words/a-good-vimrc.html) for some tips.

For a nice cheat sheet of Vim commands, see [this post](https://devhints.io/vim).

---

#### Quick list of commands

* To open a file from the terminal using Vim, type 

```
vim my-example-file
```

* You can move around the file using the arrows, as well as

    * `gg` to go to the top of the file
    * `G` to go to the end of the file
    * `:{line_number}` to go to a specific line number

* To insert text into the file, you can enter "insert mode" by using
    * `i` to start inserting at the current cursor position
    * `a` to start inserting at +1 the current cursor position
    
* To get out of insert mode, use `Esc`

* To at any point save the file, use `:w`

* To select multiple characters or lines of text, you must enter "visual mode." To do this
    * press `v` to start highlighting at the current cursor position
    * move your cursor to the final character you would like to highlight

* You can select entire lines by instead
    * pressing `V` at the first line you want to highlight
    * moving the cursor to the last line you want to highlight

* You can exit visual mode at any time by pressing `Esc`, and the text will become un-highlighted

* To copy highlighted characters/lines, use `y` ("yank"); the text should then become un-highlighted

* You can paste previously "yanked" characters/lines using `p`

* To remove text from the file, you can either delete things from within insert mode, or use
    * `x` to delete the character at you current cursor position
    * select text as shown above, and then press `x`

* To undo changes, use `u`; to redo them, use `ctrl + r`

* To search for things withing the file, enter `/` and then type the string you would like to search for
    * If you press `Enter`, you can then navitage to all occurences of that string by typing `n` ("next")

* To close the editor *without saving*, type `:q`
    * Note: if you have made changes to the file, and you would like to discard them, type instead `:q!`
    
* To close the editor and save your changes, instead type `:wq`

---

There are a TON more things you can do in Vim than what I have shown above, which make it a very powerful text editor. For example, check out [search and replace](https://vim.fandom.com/wiki/Search_and_replace), [recording macros](https://vim.fandom.com/wiki/Macros), and [Visual Blocks](https://www.youtube.com/watch?v=Ydzw70SvF-g), to name just a few features.
