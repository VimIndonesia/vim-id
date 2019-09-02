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
