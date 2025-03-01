# REST API Wilayah Indonesia

## Deskripsi

Proyek ini adalah REST API berbasis **Golang** menggunakan **Gin Framework** dan **GORM** untuk mengelola data provinsi Indonesia. API dapat mengambil data dari API eksternal dan menyimpannya ke dalam database MySQL.

## Teknologi yang Digunakan

- Golang
- Gin Framework
- GORM (ORM untuk Golang)
- MySQL

## Struktur Proyek

```
.
├── controllers
│   ├── province_controller.go  # Controller untuk mengambil dan menyimpan data
├── models
│   ├── database.go  # Koneksi database
│   ├── province.go  # Model Province
├── main.go  # Entry point aplikasi
```

## Instalasi & Menjalankan Aplikasi

### **1. Persiapan Database**

Buat database MySQL dengan nama **wilayahs**:

```sql
CREATE DATABASE wilayahs;
```

### **2. Clone Repository & Install Dependency**

```sh
git clone https://github.com/username/repository.git
cd repository
go mod tidy
```

### **3. Konfigurasi Database**

Ubah koneksi database di `models/database.go` sesuai dengan kredensial Anda:

```go
dsn := "root:@tcp(localhost:3306)/wilayahs?charset=utf8mb4&parseTime=True&loc=Local"
```

### **4. Jalankan Aplikasi**

```sh
go run main.go
```

## Endpoints API

### **1. Fetch Data dari API Eksternal dan Simpan ke Database**

```http
GET /api/provinces/fetch
```

- **Deskripsi:** Mengambil data provinsi dari [API Emsifa](https://www.emsifa.com/api-wilayah-indonesia/) dan menyimpannya ke MySQL.
- **Response:**

```json
{
  "status": "success",
  "message": "Data inserted"
}
```

### **2. Ambil Data dari Database**

```http
GET /api/provinces
```

- **Deskripsi:** Mengambil semua data provinsi yang telah disimpan di MySQL.
- **Response:**

```json
{
  "status": "success",
  "message": "Successfully get data",
  "data": [
    {
      "id": 1,
      "code": "11",
      "name": "ACEH"
    }
  ]
}
```

## Lisensi

MIT License



