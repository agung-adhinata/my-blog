+++
author = "Hugo Authors"
title = "Markdown Syntax Guide"
date = "2021-03-06"
description = "artikel sampel untuk pengujian styling Markdown pada hugo static server atau sejenisnya yang menggunakan markdown sebagai media penulisan kontennya"
tags = [
    "markdown",
    "css",
    "html",
]
categories = [
    "themes",
    "syntax",
]
series = ["Themes Guide"]
aliases = ["migrate-from-jekyl"]
draft=false
+++

Postingan ini menunjukkan bentuk styling markdown setelah melalui proses build menuju konten html.

## Headings

Tag HTML seperti `<h1>`—`<h6>` mempresentasikan enam tingkatan _Heading_, `<h1>` adalah tingkatan tertinggi pada _Heading_ sedangkan `<h6>` adalah tingkatan yang terendah. contohnya ada di berikut ini:

# H1

## H2

### H3

#### H4

##### H5

###### H6

## Paragraf

Xerum, quo qui aut unt expliquam qui dolut labo. Aque venitatiusda cum, voluptionse latur sitiae dolessi aut parist aut dollo enim qui voluptate ma dolestendit peritin re plis aut quas inctum laceat est volestemque commosa as cus endigna tectur, offic to cor sequas etum rerum idem sintibus eiur? Quianimin porecus evelectur, cum que nis nust voloribus ratem aut omnimi, sitatur? Quiatem. Nam, omnis sum am facea corem alique molestrunt et eos evelece arcillit ut aut eos eos nus, sin conecerem erum fuga. Ri oditatquam, ad quibus unda veliamenimin cusam et facea ipsamus es exerum sitate dolores editium rerore eost, temped molorro ratiae volorro te reribus dolorer sperchicium faceata tiustia prat.

Itatur? Quiatae cullecum rem ent aut odis in re eossequodi nonsequ idebis ne sapicia is sinveli squiatum, core et que aut hariosam ex eat.

## Blockquotes

elemen _blockquote_ menunjukkan konten dalam bentuk kutipan atau quotes, dapat ditambahkan dengan elemen tag `cite` atau `footer`, maupun tag `abbr` sebagai atribut.

#### Blockquote tanpa atribut

> Ini adalah kutipan/ quotes, bla bla bla :v 

> **Catatan:** anda dapat menggunakan sintax _Markdown_ di dalam quotes

#### Blockquote dengan atribut

> Pemujaan yang berlebihan tidak sehat.
> — <cite>Patrick[^1]</cite>

[^1]: Kutipan di atas pernah dikatakan oleh patrick di film [Spongebob](https://id.wikipedia.org/wiki/SpongeBob_SquarePants) pada episode tentang Kevin si timun sombong.

## Tabel

Tabel sebenarnya bukan bagian dari markdown, namun secara _out-of-the-box_ Hugo mendukung format tabel ini.

| Name  | Age |
| ----- | --- |
| Bob   | 27  |
| Alice | 23  |

#### Inline Markdown dengan tabel

| Italics   | Bold     | Code   |
| --------- | -------- | ------ |
| _italics_ | **bold** | `code` |

## Code Block

Sesuai judul, digunakan untuk memblok kode supaya terlihat lebih rapi. yah itu aja sih.

#### Code block dengan koma terbalik (_backticks_)

```
html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

#### Code block dengan dua tab indentasi

    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>

#### Code block dengan shortcode bawaan Hugo

{{<highlight js >}}
function hello(props) {
console.log('hello bro');
}
{{</highlight >}}

## Tipe List

#### Ordered List

1. Ikan Tuna
2. Ayam Bangkok
3. Burung Kutilang

#### Unordered List

- Soda Kue
- Pewarna
- Tepung Terigu

#### Nested list

- Buah
  - Melon
  - Jeruk
  - Semangka
- Catatan
  - Membersihkan Kandang Burung
  - Cek Pelanggan

## Elemen tag lainnya — abbr, sub, sup, kbd, mark

<abbr title="Graphics Interchange Format">GIF</abbr> adalah format bitmap.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

_Press_ <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> _to end the session._

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.
