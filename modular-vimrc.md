## so[urce] atau ru[ntime]  

Untuk membuat sebuah vimrc modular, kita tinggal menggunakan *so[urce]* atau *ru[ntime]* pada vimrc kita, *ru* adalah *so* yang modern. Akan lebih menguntungkan jika kita juga menambah *!* pada settingan, karena ini akan menambah semua file dari semua lokasi yang tercantum pada *RunTimePath*. Contoh yang payah dan sederhana tersedia di [fonzacus/miv](https://github.com/FONZACUS/miv).

```
Untuk melihat dari mana dan mana saja yang di source dari G/Vim yang sedang aktif.
echo &runtimepath
scr[iptnames]
```

Membuat settingan yang modular, kita harus pintar memilih jalur kabur. Untuk lebih aman, lebih baik setting menggunakan append `+`. Ini akan menambahkan modular kita di ujung `rtp`, dan akan menggunakannya jika Vim benar-benar harus menggunakannya. Dan jika kita ingin menambah plugin dari lokasi baru, kita harus pakai settingan `PackPath` juga.

```
LB lokasi baru
set runtimepath+=LB
set packpath+=LB
```

Pada akhirnya, *rtp* dan *pp* akan terlihat sangat mirip. Jika kita yakin seharusnya akan sama, setting `let &rtp=&pp` tersedia.

## :filetype plugin on  

With this command, you can enable loading the plugin files for specific file types in ~/.vim/ftplugin/ . A file must then be created at ~/.vim/ftplugin/<language>.vim which will be loaded automatically for any buffers using that language.  

### Example:  

Suppose that for C files you want to set the 'softtabstop' option to 4 and define a mapping to insert a three-line comment.  You do this with only two steps:  

1. Create your own runtime directory.  On Unix this usually is "~/.vim".  In this directory create the "ftplugin" directory:  
   
   ```
	 $ mkdir ~/.vim
	 $ mkdir ~/.vim/ftplugin
   ```
   
   When you are not on Unix, check the value of the 'runtimepath' option to see where Vim will look for the "ftplugin" directory:  

   ```
	 set runtimepath
   ```
   
   You would normally use the first directory name (before the first comma). You might want to prepend a directory name to the 'runtimepath' option in your |vimrc| file if you don't like the default value.  
   
 2. Create the file "~/.vim/ftplugin/c.vim", with the contents:  

    ```
	  setlocal softtabstop=4
	  noremap <buffer> <LocalLeader>c o/**************<CR><CR>/<Esc>
    ```

  Try editing a C file.  You should notice that the 'softtabstop' option is set to 4.  But when you edit another file it's reset to the default zero.  That is because the ":setlocal" command was used.  This sets the 'softtabstop' option only locally to the buffer.  As soon as you edit another buffer, it will be set to the value set for that buffer.  For a new buffer it will get the
default value or the value from the last ":set" command. Local options have priority over global ones your .vimrc settings might be ignored.

  Likewise, the mapping for "\c" will disappear when editing another buffer. The ":map <buffer>" command creates a mapping that is local to the current buffer.  This works with any mapping command: ":map!", ":vmap", etc.  The |<LocalLeader>| in the mapping is replaced with the value of the "maplocalleader" variable.  

### autocmd FileType + Source  

On rare occasions you might have enough settings to warrant a separate file, but would like to load them for multiple languages. Using filetype plugins, you'll end up with duplicate files or symlinks.  

A simple alternative is to fall back to autocmd, but instead of writing the settings in one big line, you can instead source a file. For example:  

```
autocmd FileType markdown,tex,textile source ~/.vim/lang_settings/text.vim
```

**Referensi:**  
* https://stackoverflow.com/questions/18932012/how-to-load-different-vimrc-file-for-different-working-directory/18932324#18932324    
* http://vimdoc.sourceforge.net/htmldoc/filetype.html  
* http://vimdoc.sourceforge.net/htmldoc/usr_43.html#filetype-plugin  
* https://vi.stackexchange.com/questions/11696/what-does-filetype-plugin-on-really-do/11705#11705  
