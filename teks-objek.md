# Intro

menurut [kana the wizard](https://github.com/kana) di artikel [ini](https://whileimautomaton.net/2008/11/vimm3/operator) pengguna vim dibagi dalam 7 level

dan pengguna vim level 5 adalah "who knows text objects"

## Tantangan 1

bagaimana cara menghapus/merubah teks dibawah ini? ( '|' letak cursor )
> he|llo

biasanya kita menekan tombol 'b' lalu 'de' atau 'ce'. dengan text object kita cukup mengetikkan 'daw' atau 'ciw'

lalu apa bedanya? oke, bagaimana kalau seperti ini
```html
<a href="https://github.com/vim-i|d/vim-id"></a>
```
coba hapus teks yang dimulai dari https...dengan text object tidak perlu berpindah cursor, cukup mengetikkan ' di" '

## Logic text object
> [operator][object-selection][motion]
* operator : d,y,c...
* selection : ada dua object-selection didalam text object yaitu 'i' inner dan 'a' around
* motion : w,t,"...

> contoh " daw " yang artinya 'delete word under cursor and spaces after word'. atau " cit " yang artinya ' change inner tag '

delete around word
```
before : 
he|llo world!
after : 
|world!
```
change inner tag
```html
before :
<a href="#"><|h1>hello world</h1></a>
after :
<a href="#"><h1>|</h1></a>
```
> Note : biasanya untuk menghapus gunakan selection 'around' sedangkan untuk change gunakan selection 'inner'

## Tantangan 2

('|' letak cursor)

Bagaimana cara mengcopy teks " hell|o-world " tanpa menggunakan visual mode?

Logic dalam teks objek bisa juga diaplikasian dengan number menjadi 
> [operator][number][object-selection][motion]

dengan begitu kita bisa menjawab tantangan diatas dengan mengcopy tanpa visual mode menggunakan teks object 'y3iw' yang artinya 'yank inner 3 word'. disini terdapat 3 word yaitu " hello ", " - ", " world "

> Note : gunakan perintah " :h iskeyword " untuk informasi mengenai keyword di vim 

untuk lebih jelas tentang operator, object-selection, dan motion silahkan kunjungi link [ini](http://vimdoc.sourceforge.net/htmldoc/motion.html)

Selamat bereksperimen..
