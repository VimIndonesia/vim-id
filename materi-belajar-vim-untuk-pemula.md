Cinta pertama kita para vimmers tergantungan pada vimrc pertama kita. Vim membaca confignya bernama *vimrc* dari beberapa lokasi berurutan, dan akan memlih hanya satu. System config yang terletak di lokasi terinstall Vim `/etc/vim` (lin) dan `C:\Program Files\Vim`(win)  bernama `vimrc` akan mengambil config utama. Untuk PC masing-masing ini tidak buruk, tetapi jika berbagi PC, lebih baik system vimrc tidak ada, dan memilih untuk menggunakan user config. Yaitu di `/home/NAMA/.vimrc` (lin) dan `C:\User\NAMA\_vimrc`. Untuk coba-coba, versi portable/extract tersedia dari [repo Vim](https://github.com/vim).

Lebih susah mempelajari Vim, dan akan disarankan untuk menggunakan easy-mode dan memakai *defaults dan mswin*.vim. Ini adalah langkah bagus untuk berterjun ke dunia Vim yang begitu suram. Settingan dari defaults dan mswin akan merasa lebih nyaman karena defaults memiliki setting modern, dan mswin memiliki kenyamaan settingan GUI seperti `ctrl c` untuk copy seperti banyak aplikasi lainnya.

`runtime defaults.vim mswin.vim`

Pandangan pertama memang tidak menarik di Vim, untuk menggantinya, kita bisa mencari *colorscheme* yang lebih baik dari beberapa sumber, seperti GitHub. Colorscheme yang menurut saya sederhana, mudah di modif, dan berjalan lancar di G/Vim adalah [utb.vim](https://github.com/utubo/vim-utb). Jangan lupa simpannya di folder `colors`.

`colorscheme utb.vim`

Cara Vim menggunakan `clipboard` memang unik, dan akan mengganggu perjalan Anda. Untuk menggunakan system clipboard untuk semua system dan aplikasi, setting ini akan melancarkan integrasi Vim dan aplikasi lainnya.

`set clipboard=unnamedplus`

Untuk langkah pertama, segini bisa dipanggil cukup. Vim memiliki banyak options tambahan yang kita bisa lihat dengan `help options`.

```
runtime defaults.vim mswin.vim
colorscheme utb
set clipboard=unnamedplus
```

Untuk mengganti font pada GVim, kita tinggal memakai ini. Tidak semua monospace font yang bisa dipakai, dan GVim lebih ketat dibanding aplikasi lainnya. Untuk memastikan apakah kita bisa memilih dia, kita cari dulu di `menu - edit - select font`, dan baru aman di simpan di settingan kita. Saya sarankan mencari font kesukaan Anda dari [app.programmingfonts](https://app.programmingfonts.org) dan memakai font yang memiliki nama sederhana, seperti `hack`. Jika tidak dipakai, maka akan memakai default terminal bawaan system kita. Vim juga hanya bisa menggunakan font dari settingan terminal.

`set guifont=hack`

Ada banyak aplikasi yang lebih baik dibanding `vimgrep`, dan Vim sudah banyak berkembang untuk mendukung berbagai aplikasi eksternal. Untuk penjelasan di sini, hanya mesin pencari lokal yang akan dibahas. Untuk melihat aplikasi yang terdukung, sekaligus contoh plugin yang baik, [vim-grepper](https://github.com/mhinz/vim-grepper) memiliki daftar lengkap. Jika ingin mencoba salah satunya, kita tinggal memasang `path` sementara sebelum diinstal.

`set grepprg=ag\ -r\ --vimgrep`

Versi modern untuk semua setting adalah dengan `let &option`. Ini lebih sederhana karena akan ditutup oleh tanda kutip satu `'`.

```
let &guifont='hack'
let &grepprg='ag -r --vimgrep'
```

