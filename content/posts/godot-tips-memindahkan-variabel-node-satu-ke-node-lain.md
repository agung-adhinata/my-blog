---
title: "Godot Tips: Memindahkan Variabel Node Satu Ke Node Lain menggunakan Signal"
date: 2021-08-24T10:28:58+08:00
draft: false
tags: 
  - godot
---

Pada artikel ini saya anggap para pembaca sudah mengerti tentang konsep dasa godot dan cara kerja *signal* dan penggunaannya pada Godot.

Bagi yang belum tahu, kalian bisa mempelajarinya di channel youtube luar yang berjudul GDQuest.

Oke lanjut!

Caranya cukup sederhana.
pada project yang saya buat, bentuk hierarki object yang akan di klik seperti ini : 

```go
- IniKotak(type: KinematicObject2D)
	- Polygon2D(type: Polygon2D)
	- CollisionShape2D(type: CollisionShape2D)
```

![Tampilan Struktur Main](https://i.imgur.com/X9N5U3O.png)

kira - kira seperti ini

para pembaca dapat menyesuaikannya sesuai project yang kalian punya, dengan syarat *Parent* yang digunakan adalah ***KinematicBody2D***, atau Node sejenisnya yang memiliki properti signal *Input_Event*.

kemudian, pada ***IniKotak***, kita tambahkan kode berikut ini, penjelasan tertera pada kode:

```go
extends KinematicBody2D

//membuat signal yang akan digunakan untuk bypass variabel objek ini ke objek lain
signal clicked(node: Object)

//kita siapkan variabelnya yang akan kita pindahkan
var ini_variabel : Int = 123

//membuat fungsi bawaan yang mendeteksi input mouse yaitu klikan
func _input_event(viewport: Object, event: InputEvent, shape_idx: int) -> void:
	if event is InputEventMouseButton:
		if event.button_index == BUTTON_LEFT:
			if event.pressed:
				//optional: print pada code ini hanya untuk testing saja, boleh dihapus
				print("clicking")

				//menghubungkan fungsi ini dengan signal clicked yang telah kita buat.
				emit_signal("clicked",self) 
				//PENTING!: parameter self pada fungsi di atas diperlukan  
				//bila ingin membawa data variabel ke Object lain
```

kemudian simpan dengan nama sesuai dengan yang kalian inginkan. Namun, disarankan nama yang di buat harus sama dengan nama Object nya agar tidak membingungkan diri sendiri di kemudian hari.

![Contoh penempatan objek IniKotak pada folder](https://i.imgur.com/wmpORQW.png)

Object IniKotak dengan nama file IniKotak. pada project yang saya buat, saya simpan objeknya di object/environment. 

setelah itu, kita akan membuat Main Scene, hierarkinya seperti ini:

```go
- Main(type: Node2D)
```

yap, hanya ini aja. Karena objek ***IniKotak*** yang kita buat akan kita munculkan melalui kode melalui proses *Instantiate*.

kemudian, pada node ***Main*** tulis kode di bawah ini, penjelasan ada di dalam kode:

```go
extends Node2D

//melakukan preload object
const TheBox := preload("res://object/environment/IniKotak.tscn")

func box_clicked(node) -> void:
	//membuat print, fungsi ini akan muncul pada terminal console godot
	print("im click!", node.ini_variabel) //Output: im click!123

//membuat fungsi inisialisasi, fungsi ini akan jalan pertama kali ketika memulai 
//permainan
func _ready() -> void:

	//melakukan instancing
	var box1 = TheBox.instance()

	//menghubungkan signal yang telah kita buat pada IniKotak dengan fungsi
	// box_clicked() yang telah kita buat sebelumnya
	box1.connect("clicked",self,"box_clicked")
	//memasukkan TheBox ke dalam Scene
	add_child(box1)
	// Mengubah posisi instance pada layar
	box1.translate(Vector2(70, 120))
	
```

![Hasil kodingnya](https://i.imgur.com/gMYYfd9.png)

hasil output pada layar

oke itu aja, sisanya kalian dapat mengkreasikannya sendiri sesuai selera, misalnya untuk membuat fungsi *drag & drop*.