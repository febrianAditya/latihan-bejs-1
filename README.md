# Latihan Membuat CRUD dengan Express.js dan Filesystem

## Deskripsi
Latihan ini bertujuan untuk membuat server HTTP sederhana dengan menggunakan Express.js yang mampu melakukan operasi CRUD (Create, Read, Update, Delete) pada data yang disimpan dalam file JSON. File JSON ini akan digunakan sebagai database sementara, dan Anda akan memanfaatkan modul `fs` dari Node.js untuk membaca dan menulis data ke dalam file tersebut.

## Struktur Data JSON
Data akan disimpan dalam file `data.json` dalam format array objek, di mana setiap objek merepresentasikan data dari item yang disimpan.

Contoh isi file `data.json`:
```json
[
  {
    "id": 1,
    "name": "Item 1",
    "description": "Description of Item 1"
  },
  {
    "id": 2,
    "name": "Item 2",
    "description": "Description of Item 2"
  }
]


Instruksi
1. Inisialisasi Server
Buat server HTTP dengan menggunakan Express.js.
Atur server untuk berjalan di port 3000.
2. Operasi CRUD
Buat route berikut ini untuk menangani operasi CRUD pada file data.json:
* Create Item (POST /items)
Endpoint ini akan menerima data item baru dalam format JSON dan menambahkannya ke dalam data.json. Data item yang diterima harus memiliki id, name, dan description. id harus unik. Jika ada data sebelumnya di data.json, buat ID baru sebagai angka terakhir + 1. Kembalikan respons berupa data item yang baru ditambahkan beserta status berhasil.

* Read All Items (GET /items)
Endpoint ini membaca semua item dari data.json dan mengirimkannya sebagai respons dalam format JSON. Jika tidak ada item, kirim respons berupa array kosong [].

* Read Item By Id (GET /items/:id)
Endpoint ini membaca item berdasarkan id yang diberikan di parameter URL. Jika item ditemukan, kirim data item tersebut sebagai respons. Jika tidak ada item dengan id yang diminta, kirimkan status 404 beserta pesan "Item not found".

* Update Item (PUT /items/:id)
Endpoint ini memperbarui data item yang sudah ada berdasarkan id. Menerima data name dan description untuk diperbarui. Jika item dengan id yang diminta ditemukan, perbarui data tersebut dan kirim respons berupa data item yang telah diubah. Jika tidak ditemukan, kirimkan status 404 beserta pesan "Item not found".

* Delete Item (DELETE /items/:id)
Endpoint ini menghapus item berdasarkan id.Jika item ditemukan, hapus dari data.json dan kirim respons sukses. Jika tidak ditemukan, kirimkan status 404 beserta pesan "Item not found".

3. Validasi Data
Pastikan semua data yang diterima memiliki format yang benar. Jika data yang diterima tidak sesuai (misalnya, name atau description kosong), kirimkan respons status 400 beserta pesan error yang relevan.

4. Error Handling
Gunakan blok try-catch untuk menangani semua error yang mungkin terjadi saat membaca atau menulis file JSON.
Kirim pesan error yang informatif kepada client jika terjadi kegagalan dalam operasi file.