# Kegunaan Register

Si A membuka file menggunakan vim lalu  melakukan copy teks. sebelum melakukan paste dia menghapus beberapa teks, dengan register si A bisa melakukan paste yang sebelumnya sudah dicopy

## Logic Register

> "[character-name-register][operator]

## Contoh

Copy satu baris ke register p
> "pyy

Paste teks yang tersimpan di register p
> "pp

## Permasalahan

Register tidak menimpa teks yang ada di register itu sendiri, jika anda melakukan copy teks dua kali pada (misalnya) register p, maka teks akan menumpuk

## Tips

Bersihkan teks yang tersimpan didalam register untuk menyimpan teks baru

```vim
Tambahkan kode dibawah ini kedalam .vimrc

command! DelReg for i in range(34,122) | silent! call setreg(nr2char(i), []) | endfor
```

maka untuk membersihkan semua register gunakan command :DelReg
