# Tanya Jawab
Tujuan dokumen ini untuk menampung FAQ (Frequently Asked Question) tentang vim
atau neovim.

## Apa Perbedaan Vim dan Neovim?
- Lokasi berkas konfigurasi.
  - `~/.vimrc` untuk vim
  - `~/.config/nvim/init.vim` untuk neovim
- Neovim memiliki API yang memungkinkan kita untuk bisa menulis konfigurasi
atau plugin dengan bahasa selain vimscript, seperti JS, Ruby, Python, Lua, dll.

## Bagaimana Cara Memasang Plugin?
Kalian bisa menggunakan [vim-plug](https://github.com/junegunn/vim-plug) untuk
memasang plugin.

#### Memasang Vim-plug

###### Untuk Vim

```sh
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
###### Untuk Neovim

```sh
curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

#### Menggunakan Vim-plug
Buka `~/.vimrc` atau `~/.config/nvim/init.vim` kalian, lalu ketikan daftar
plugin kalian diantara `call plug#begin()` dan `call plug#end()`

##### Contoh

```vim
call plug#begin()

" Baris di bawah berarti akan memasang plugin dari repositori https://github.com/junegunn/vim-easy-align
Plug 'junegunn/vim-easy-align'

call plug#end()
```

Lalu muat ulang `.vimrc` atau `init.vim` dan ketikan `:PlugInstall` untuk
memasang pluginnya.

## Bagaimana Cara Memunculkan Auto Completion?

### Coc.nvim
Coc sangatlah mudah untuk di-_setup_ tetapi cukup memakan resource ram karena
membutuhkan nodejs untuk bisa berjalan. Dari pengalaman saya, jika kalian
memiliki ram >= 4 GB, saya rasa coc bisa berjalan dengan lancar.

#### Memasang Coc.nvim
Pastikan kalian sudah memasang nodejs terlebih dahulu. Lalu pasang plugin coc
dengan plug.

```vim
Plug 'neoclide/coc.nvim', {'branch': 'release'}
```

#### Menggunakan Coc.nvim
Setelah itu kalian pasang coc extension untuk bahasa yang ingin kalian pakai
seperti ini:

```vim
:CocInstall coc-json coc-tsserver
```

## Bagaimana Cara Memunculkan Sidebar seperti di VSCode?
Sidebar yang digunakan untuk menjelajahi berkas dinamakan tree-explorer di vim. Plugin tree-explorer ada banyak macamnya tetapi yang paling banyak digunakan adalah [NERDTree](https://github.com/preservim/nerdtree).

#### Memasang NERDTree
Pasang nerdtree dengan vim-plug

```vim
Plug 'preservim/nerdtree'
```

#### Menggunakan NERDTree
Untuk membuka tree-explorer dengan nerdtree, kalian bisa menggunakan perintah `:NERDTree`.
