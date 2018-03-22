# Dokumentasi Web Service Aplikasi Alumni Salman

| Endpoint      | https://api.alumni.salmanitb.com   | 
| ------------- |:----------------------------------:|

Secara umum respon yang akan diberikan adalah sebagai berikut:
```
{
  "success" : false,
  "data" : null,
  "error": {
      "code": 503,
      "message": "User not authenticated"
  }
}
```
Dengan parameter yang harus selalu dikirimkan:

| Parameter        |            | Deskripsi  |
| ------------- |:-------------:| -----:|
| token      | required | string unik yang didapatkan setelah login  |

Penjelasan respon:

| Parameter     | Deskripsi  |
| ------------- |:-------------|
| `success`       | Bernilai `true` jika tidak terjadi kesalahan, sebaliknya akan mengembalikan `false` |
| `data`       | Data utama yang dapat digunakan, berisi `null` jika kososng|
| `error`      | Object error yang berisi kode dan keterangan error. Bernilai `null` jika tidak terjadi error. Object error memiliki atribut `code` dan `message`|

Pada bagian selanjutnya akan dijelaskan web service yang dapat digunakan beserta `data` yang akan diperoleh.

## Autentikasi
-------------------------
### Login
### Registrasi
### Cek Email sudah Terdaftar
### Cek sudah Terverifikasi
### Perbaharui Token

## Salman Menyapa
-------------------------
### List Berita
Mendapatkan daftar berita yang sudah dipublikasikan oleh admin

| HTTP Request
```
    GET     /news
```
| Parameters

| Parameter        |            | Deskripsi  |
| ------------- |:-------------:| :-----|
| `count`         | required | Jumlah berita yang ingin diperoleh |
| `page`          | optional | Posisi berita pada halaman berapa yang ingin deperoleh. Secara default akan bernilai 0 atau halaman pertama |

| Respon Data

Akan dikirimkan array of berita sejumlah `count` dan struktur tiap item berita adalah sebagai berikut:

| Parameter     | Deskripsi  |
| ------------- |:-------------|
| `title`       | Judul berita |
| `time`       | Waktu berita dipublikasikan. Menggunakan nilai UNIX timestamp |
| `image`       | URL gambar utama untuk berita |
| `intro`       | Sebagian awal dari konten berita, terdiri dari 100 karakter awal isi berita |

contoh:
```
[
    {
        "title": "Tarif Tol di RI Lebih Mahal dari Singapura hingga China",
        "time": 121236127612,
        "image": "https://akcdn.detik.net.id/community/media/visual/2017/12/09/3e94447f-2a62-4fc9-a406-659605f8521c_169.jpg?w=700&q=80",
        "intro": "Bagaimana perbandingan tarif tol di Indonesia dengan negara-negara di ASEAN?"
    }
]

```


### Detail Berita

to be defined


## Cari Alumni
-------------------------
### Alumni di Sekitar
### Pencarian dengan Nama
### Detail Profil Alumni


## Profil Pengguna
-------------------------
### Upload Gambar Profil
### Ambil data Profil
### Ubah data Profil

## Kontak Admin
-------------------------
### Info Admin
dapetin no telp, alamat, email, nama, dlsb (bisa diganti dari admin)
