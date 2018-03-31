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
Mendapatkan daftar alumni salman berdasarkan kota

| HTTP Request
```
    GET     /alumni_by_city
```
| Parameters

| Parameter       |         | Deskripsi  |
| ----------------|:-------:| :-----|
| `city`         | required | Kota asal alumni yang akan dicari|

| Respon Data

Akan dikirimkan array of data alumni sejumlah `count` dan struktur tiap item alumni adalah sebagai berikut:

| Parameter     | Deskripsi  |
| ------------- |:-------------|
| `uid`       | User id |
| `name`       | Nama alumni sesuai dengan `uid` |
| `image`       | URL gambar utama untuk profil alumni |
| `city`       | Kota/Domisili alumni |
| `email`       | Alamat email alumni |

contoh:
```
[
    {
        "uid": "XXXXXX",
        "name": "Muhammad Hilmi Asyrofi",
        "image": "https://akcdn.detik.net.id/community/media/visual/2017/12/09/3e94447f-2a62-4fc9-a406-659605f8521c_169.jpg?w=700&q=80",
        "city": "Bandung"
        "email": "mhilmiasyrofi@gamil.com"
    }
]

```

### Pencarian dengan Nama
Mendapatkan daftar alumni salman berdasarkan nama

| HTTP Request
```
    GET     /alumni_by_name
```
| Parameters

| Parameter       |         | Deskripsi  |
| ----------------|:-------:| :-----|
| `name`         | required | Nama alumni yang akan dicari|
| `count`          | optional | Jumlah alumni yang ingin diperoleh |

| Respon Data

Akan dikirimkan array of data alumni sejumlah `count` dan struktur tiap item alumni adalah sebagai berikut:

| Parameter     | Deskripsi  |
| ------------- |:-------------|
| `uid`       | User id |
| `name`       | Nama alumni sesuai dengan `uid` |
| `image`       | URL gambar utama untuk profil alumni |
| `city`       | Kota/Domisili alumni |
| `email`       | Alamat email alumni |

contoh:
```
[
    {
        "uid": "XXXXXX",
        "name": "Muhammad Hilmi Asyrofi",
        "image": "https://akcdn.detik.net.id/community/media/visual/2017/12/09/3e94447f-2a62-4fc9-a406-659605f8521c_169.jpg?w=700&q=80",
        "city": "Bandung"
        "email": "mhilmiasyrofi@gamil.com"
    }
]

```
### Detail Profil Alumni

## Profil Pengguna
-------------------------
### Upload Gambar Profil


### Ambil data Profil
Mendapatkan detail profil alumni salman

| HTTP Request
```
    GET     /alumni_by_uid
```
| Parameters

| Parameter       |         | Deskripsi  |
| ----------------|:-------:| :-----|
| `uid`         | required | user id alumni |


| Respon Data

Akan dikirimkan item alumni sebagai berikut:

| Parameter     | Deskripsi  |
| ------------- |:-------------|
| `uid`       | User id |
| `name`       | Nama alumni sesuai dengan `uid` |
| `email`       | Alamat email alumni |
| `image`       | URL gambar utama untuk profil alumni |
| `sex`       | Jenis kelamin alumni |
| `job`       | Pekerjaan alumni |
| `company`       | Pekerjaan alumni |
| `address`       | Alamat alumni |
| `city`       | Kota/Domisili alumni |
| `country`       | Negara asal alumni |
| `phonenumber`       | Nomor telepon alumni |
| `university`       | Universitas ketika menjadi aktivis alumni |
| `year_university`       | Tahun menjalani niversitas alumni |
| `major`       | Jurusan universitas alumni |
| `lmd`       | Tahun LMD alumni |
| `activities`    | Aktivitas di salman |
| `year_activities`    | Tahun menjalani aktivitas |
| `latitude`    | Latitude |
| `longitude`    | Longitude |

contoh:
```
[
    {
        "uid": "XXXXXX",
        "name": "Muhammad Hilmi Asyrofi",
        "email": "mhilmiasyrofi@gamil.com"
        "image": "https://akcdn.detik.net.id/community/media/visual/2017/12/09/3e94447f-2a62-4fc9-a406-659605f8521c_169.jpg?w=700&q=80",
        "sex": "Laki-laki",
        "job": "Ai Engineer",
        "company": "Google",
        "address": "Jalan Impian",
        "city": "Silicon Valley",
        "country": "US",
        "phonenumber": "081214841782",
        "university": "MIT",
        "year_university": "2015",
        "major": "T Informatika",
        "lmd": "2017",
        "activities": "Imam Muda Salman",
        "year_activities": "2017",
        "latitude": 0.5234523,
        "longitude": 0.2412421
    }
]

```
### Ubah data Profil
Mengubah data profil alumni salman

Secara umum respon yang akan diberikan adalah sebagai berikut:
```
{
  "success" : false,
  "data" : null,
  "error": {
      "code": 503,
      "message": "Edit profil failed"
  }
}
```

| HTTP Request
```
    POST     /edit_profil_alumni
```
| Parameters

| Parameter       |         | Deskripsi  |
| ----------------|:-------:| :-----|
| `uid`         | required | user id alumni |
| `name`       | Nama alumni sesuai dengan `uid` |
| `email`       | Alamat email alumni |
| `image`       | URL gambar utama untuk profil alumni |
| `sex`       | Jenis kelamin alumni |
| `job`       | Pekerjaan alumni |
| `company`       | Pekerjaan alumni |
| `address`       | Alamat alumni |
| `city`       | Kota/Domisili alumni |
| `country`       | Negara asal alumni |
| `phonenumber`       | Nomor telepon alumni |
| `university`       | Universitas ketika menjadi aktivis alumni |
| `year_university`       | Tahun menjalani niversitas alumni |
| `major`       | Jurusan universitas alumni |
| `lmd`       | Tahun LMD alumni |
| `activities`    | Aktivitas di salman |
| `year_activities`    | Tahun menjalani aktivitas |
| `latitude`    | Latitude |
| `longitude`    | Longitude |


| Respon Data

Akan dikirimkan item alumni sebagai berikut:

| Parameter     | Deskripsi  |
| ------------- |:-------------|
| `success`       | Bernilai `true` jika tidak terjadi kesalahan, sebaliknya akan mengembalikan `false` |
| `data`       | Data utama yang dapat digunakan, berisi `null` jika kososng|
| `error`      | Object error yang berisi kode dan keterangan error. Bernilai `null` jika tidak terjadi error. Object error memiliki atribut `code` dan `message`|

## Kontak Admin
-------------------------
### Info Admin
dapetin no telp, alamat, email, nama, dlsb (bisa diganti dari admin)
