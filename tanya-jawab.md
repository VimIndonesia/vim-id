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

### Ale dan Deoplete
[ALE](https://github.com/dense-analysis/ale) bertindak sebagai LSP
(Language Server Protocol) client. Sederhananya, ALE menyediakan support untuk
menulis kode pada bahasa pemrograman kalian, seperti menunjukkan syntax yang
salah, *menyediakan completion*, dll.

Defaultnya, untuk memunculkan completion yang telah disediakan oleh ALE, kalian
harus menekan Ctrl-x lalu Ctrl-n. Agar kalian bisa memunculkan completion-nya
secara otomatis, seperti di VSCode, kalian memerlukan
[deoplete](https://github.com/Shougo/deoplete.nvim).

#### Memasang ALE dan Deoplete
Karena deoplete ditulis dengan bahasa python, maka kita perlu memasang `pynvim`
agar neovim bisa membaca codenya. Deoplete juga membutuhkan
[`msgpack`](https://github.com/msgpack/msgpack-python) agar bisa berfungsi.

```
pip3 install --user pynvim msgpack
```

Setelah itu kita tinggal memasang ALE dan deoplete

```vim
Plug 'dense-analysis/ale'
Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
```

#### Menggunakan ALE dan Deoplete

Perlu diingat bahwa ALE hanyalah LSP client. Kalian juga perlu memasang
language server sesuai bahasa pemrograman yang kalian pakai. Kalian bisa
melihat daftar language server tersebut di [sini](https://langserver.org/#implementations-server).

Setelah itu letakkan konfigurasi ini setelah konfigurasi vim-plug.

```vim
" Mengaktifkan deoplete
let g:deoplete#enable_at_startup = 1

" Menjadikan ALE sebagai sumber completion
call deoplete#custom#option('sources', {
\ '_': ['ale'],
\})
```

### Neovim built-in LSP client dan Nvim-compe
Jika kalian menggunakan Neovim 0.5+, kalian bisa menggunakan
[nvim-compe](https://github.com/hrsh7th/nvim-compe) dan built-in LSP client
yang telah disediakan neovim sebagai pengganti ALE dan deoplete.

#### Memasang Nvim-lspconfig dan Nvim-compe
[Nvim-lspconfig](https://github.com/neovim/nvim-lspconfig) adalah plugin untuk
memudahkan kita mengonfigurasi pengaturan LSP client yang disediakan Neovim.

Kita bisa memasang nvim-lspconfig dan nvim-compe dengan vim-plug maupun
[packer.nvim](https://github.com/wbthomason/packer.nvim)

###### Vim-plug

```vim
Plug 'neovim/nvim-lspconfig'
Plug 'hrsh7th/nvim-compe'
```

###### Packer.nvim

```lua
use 'neovim/nvim-lspconfig'
use 'hrsh7th/nvim-compe'
```

#### Menggunakan Nvim-lspconfig dan Nvim-compe
Seperti yang telah dijelaskan di [sini](#menggunakan-ale-dan-deoplete), jangan
lupa untuk memasang language server sesuai bahasa pemrograman yang kalian pakai.

Setelah itu kalian bisa menaruh konfigurasi nvim-compe di `init.lua` 

```lua
require'compe'.setup {
  enabled = true;
  autocomplete = true;
  documentation = true;

  source = {
    nvim_lsp = true;
  };
}
```

## Bagaimana Cara Memunculkan Sidebar seperti di VSCode?
Sidebar yang digunakan untuk menjelajahi berkas dinamakan tree-explorer di vim.
Plugin tree-explorer ada banyak macamnya tetapi yang paling banyak digunakan
adalah [NERDTree](https://github.com/preservim/nerdtree).

#### Memasang NERDTree
Pasang nerdtree dengan vim-plug

```vim
Plug 'preservim/nerdtree'
```

#### Menggunakan NERDTree
Untuk membuka tree-explorer dengan nerdtree, kalian bisa menggunakan perintah
`:NERDTree`.
