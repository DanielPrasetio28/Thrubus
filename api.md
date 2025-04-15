Berikut adalah dokumentasi API untuk dua endpoint pada layanan **Cek Harga** dari **Thrubus API**.

---

## 📘 Dokumentasi API: Cek Harga Thrubus

### 🔗 1. **Cek Harga Layanan Banyak Tujuan**

- **Endpoint:**  
  `POST https://api-order.thrubus.co.id/pool-layanan`

- **Deskripsi:**  
  Menghitung estimasi harga untuk layanan sewa mobil dengan beberapa tujuan (multi-destinasi).



- **Request Body (JSON):**
  ```json
  {
    "kategori": "sewa_mobil", // Jenis layanan (misal: sewa_mobil)
    "tgl_mulai": "2025-03-17 08:07:00", // Tanggal & waktu mulai
    "tgl_selesai": "2025-03-20 22:11:00", // Tanggal & waktu selesai
    "penjemputan": "Juanda Airport (SUB), ...", // Lokasi penjemputan
    "lokasi_turun": "Juanda Airport (SUB), ...", // Lokasi akhir setelah rute selesai
    "tujuan": [ // Daftar destinasi yang akan dikunjungi
      "Malang, Kota Malang, Jawa Timur, Indonesia",
      "Kepanjen, Malang, Jawa Timur, Indonesia",
      "Kediri, Jawa Timur, Indonesia",
      "Mojokerto, Kota Mojokerto, Jawa Timur, Indonesia"
    ]
  }
  ```

- **Response :**
  ```json
  {
    "status": true,
    "code": 200,
    "message": "OK",
    "data": {
        "id": "64629851-9dc0-44f9-9629-5cb314b1d4e9",
        "create_at": "2025-04-14 20:43:15",
        "route": {
            "tgl_mulai": "2025-11-25 08:07:00",
            "tgl_selesai": "2025-11-28 22:11:00",
            "penjemputan": "Juanda Airport (SUB), Jl. Ir. H. Juanda, Betro, Kabupaten Sidoarjo, Jawa Timur, Indonesia",
            "tujuan": [
                "Malang, Kota Malang, Jawa Timur, Indonesia",
                "Kepanjen, Malang, Jawa Timur, Indonesia",
                "Kediri, Jawa Timur, Indonesia",
                "Mojokerto, Mergelo, Kota Mojokerto, Jawa Timur, Indonesia"
            ],
            "lokasi_turun": "Juanda Airport (SUB), Jl. Ir. H. Juanda, Betro, Kabupaten Sidoarjo, Jawa Timur, Indonesia",
            "durasi": 86
        },
        "paket": [
            {
                "idpaket_biaya": "1",
                "iditem_paket": "2",
                "jumlah": "5",
                "nama_paket": "5 Jam",
                "range_jumlah_min": "3",
                "range_jumlah_max": "8.4"
            },
            {
                "idpaket_biaya": "3",
                "iditem_paket": "2",
                "jumlah": "19",
                "nama_paket": "19 Jam",
                "range_jumlah_min": "15.5",
                "range_jumlah_max": "19.5"
            },
            {
                "idpaket_biaya": "5",
                "iditem_paket": "1",
                "jumlah": "0",
                "nama_paket": "Dropoff",
                "range_jumlah_min": null,
                "range_jumlah_max": null
            },
            {
                "idpaket_biaya": "6",
                "iditem_paket": "2",
                "jumlah": "1",
                "nama_paket": "1 Jam",
                "range_jumlah_min": "0.5",
                "range_jumlah_max": "2.9"
            },
            {
                "idpaket_biaya": "9",
                "iditem_paket": "2",
                "jumlah": "12",
                "nama_paket": "12 Jam",
                "range_jumlah_min": "8.5",
                "range_jumlah_max": "15.4"
            }
        ]
    }
}

  ```

```
### 🔗 2. **Cek Harga Drop-Off (Satu Arah)**

- **Endpoint:**  
  `POST https://api-order.thrubus.co.id/cek-harga/pool-dropoff`

- **Deskripsi:**  
  Menghitung estimasi harga layanan drop-off (antar satu kali jalan) dari satu lokasi ke lokasi lain.



- **Request Body (JSON):**
  ```json
  {
    "tgl_mulai": "2024-07-11 15:33:00", // Tanggal & waktu mulai
    "penjemputan": "Jakarta Selatan, Kota Jakarta Selatan, ...", // Lokasi awal penjemputan
    "tujuan": "Malang, Kota Malang, Jawa Timur, Indonesia" // Tujuan akhir
  }
  ```

- **Contoh Response:**
  ```json
  {
    "status": true,
    "code": 200,
    "message": "OK",
    "data": {
        "id": "47f5c3a8-24b0-4b58-ad30-ffa2939d4d06",
        "create_at": "2025-04-14 20:41:28",
        "route": {
            "tgl_mulai": "2025-07-11 15:33:00",
            "penjemputan": "Juanda Airport (SUB), Jl. Ir. H. Juanda, Betro, Kabupaten Sidoarjo, Jawa Timur, Indonesia",
            "tujuan": "Malang, Kota Malang, Jawa Timur, Indonesia"
        },
        "paket": {
            "idpaket_biaya": 5,
            "iditem_layanan": 1,
            "iditem_paket": 1,
            "nama": "DROPOFF"
        },
        "pool": {
            "idpool": 1,
            "lokasi": "Jl. Gerbang Pakir Terminal I, Segoro Tambak, Kec. Sedati, Kabupaten Sidoarjo, Jawa Timur 61253, Indonesia",
            "start_pool": "2025-07-11 14:33:00",
            "end_pool": "2025-07-12 01:33:00",
            "durasi": 11,
            "paket": {
                "droppenjemputan": {
                    "start_time": "2025-07-11 15:33:00",
                    "end_time": "2025-07-11 16:33:00",
                    "jarak": 1,
                    "idradius": 1,
                    "km_radius": 10,
                    "durasi": 1,
                    "address": "Juanda Airport (SUB), Jl. Ir. H. Juanda, Betro, Kabupaten Sidoarjo, Jawa Timur, Indonesia",
                    "formatted_address": "Juanda International Airport (SUB), Jl. Ir. Haji Juanda, Betro, Kec. Sedati, Kabupaten Sidoarjo, Jawa Timur 61253, Indonesia",
                    "lat": -7.3788716,
                    "lng": 112.787289,
                    "koordinat": "-7.3788716,112.787289"
                },
                "layanan": {
                    "start_time": "2025-07-11 20:33:00",
                    "end_time": "2025-07-11 21:33:00",
                    "jarak": 67,
                    "idradius": 7,
                    "km_radius": 80,
                    "durasi": 4,
                    "address": "Malang, Kota Malang, Jawa Timur, Indonesia",
                    "formatted_address": "Malang, Malang City, East Java, Indonesia",
                    "lat": -7.9666204,
                    "lng": 112.6326321,
                    "koordinat": "-7.9666204,112.6326321"
                },
                "droppool": {
                    "start_time": "2025-07-12 01:33:00",
                    "end_time": "2025-07-12 01:33:00",
                    "jarak": 68,
                    "idradius": 7,
                    "km_radius": 80,
                    "durasi": 4,
                    "address": "Jl. Gerbang Pakir Terminal I, Segoro Tambak, Kec. Sedati, Kabupaten Sidoarjo, Jawa Timur 61253, Indonesia",
                    "formatted_address": "Jl. Gerbang Pakir Terminal I, Segoro Tambak, Kec. Sedati, Kabupaten Sidoarjo, Jawa Timur 61253, Indonesia",
                    "lat": -7.3726835,
                    "lng": 112.7947549,
                    "koordinat": "-7.3726835,112.7947549"
                }
            }
        },
        "durasi": {
            "longdistance": 67
        },
        "paket_mobil": [
            {
                "idpaket_mobil": 19,
                "idradius": 7,
                "idpaket_biaya": 5,
                "iditem_layanan": 1,
                "idtipe_mobil_kisaran_harga": 1,
                "harga": 438000
            },
            {
                "idpaket_mobil": 85,
                "idradius": 7,
                "idpaket_biaya": 5,
                "iditem_layanan": 1,
                "idtipe_mobil_kisaran_harga": 2,
                "harga": 471600
            },
            {
                "idpaket_mobil": 151,
                "idradius": 7,
                "idpaket_biaya": 5,
                "iditem_layanan": 1,
                "idtipe_mobil_kisaran_harga": 3,
                "harga": 624000
            },
            {
                "idpaket_mobil": 217,
                "idradius": 7,
                "idpaket_biaya": 5,
                "iditem_layanan": 1,
                "idtipe_mobil_kisaran_harga": 4,
                "harga": 1200000
            },
            {
                "idpaket_mobil": 277,
                "idradius": 7,
                "idpaket_biaya": 5,
                "iditem_layanan": 1,
                "idtipe_mobil_kisaran_harga": 5,
                "harga": 1800000
            },
            {
                "idpaket_mobil": 332,
                "idradius": 7,
                "idpaket_biaya": 5,
                "iditem_layanan": 1,
                "idtipe_mobil_kisaran_harga": 6,
                "harga": 1841400
            },
            {
                "idpaket_mobil": 460,
                "idradius": 7,
                "idpaket_biaya": 5,
                "iditem_layanan": 1,
                "idtipe_mobil_kisaran_harga": 7,
                "harga": 2455200
            }
        ]
    }

  ```
