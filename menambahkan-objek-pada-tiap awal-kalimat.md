# 3 Cara Menambahkan Objek Pada Awal Kalimat

Pada kesempatan kali ini kita akan membahas 3 cara yang bisa digunakan untuk menambahkan objek pada awal kalimat.

## Tantangan

Katakanlah kita memiliki file `html` sebagai berikut:

```html
Saya suka roti saya dilapisi dengan selai:

<ul>
  Coklat
  Kacang
  Pisang
</ul>
```

Karena beberapa hal, kita lupa menambahkan tag `<li>` di tiap jenis selai yang kita suka. Menambahkan tab `<li>` di 3 baris adalah hal yang mudah, cukup tulis aja. Tapi gimana kalau ada 100 baris yang harus kita tambahkan? Bisa kriting tangan kita!

## Vim Way

Beruntungnya, vim menyediakan beberapa cara yang sangat powerful dalam melakukan ini. Disini saya hanya akan membahas 3 cara dasar saja, tapi sebenarnya ada 1001 cara yang bisa kita gunakan.

### Visual Insert Mode

Cara pertama adalah melalui *visual insert mode*. Apa itu? Seperti namanya, *visual insert mode* adalah cara yang digunakan dengan menggunakan dua mode secara bersamaan: *visual mode* dan *insert mode*.

![](https://i.imgur.com/As6rqNT.gif)

### Macro

Cara kedua adalah menggunakan *macro*. Vim dapat menyimpat keystroke yang kita ketikkan menjadi suatu register yang kemudian dapat digunakan kembali.

![](https://i.imgur.com/yFgAVwk.gif)

### Range Operation

Cara terakhir adalah menggunakan operation dalam range. Salah satu fitur powerful vim adalah range. Menggunakan range kita dapat melakukan operation yang biasa kita lakukan dalam normal mode.

![](https://i.imgur.com/cPGKV7a.gif)

