# Gemini Function Calling – Restaurant Assistant

Project sederhana yang menggunakan **Google Gemini Function Calling** untuk membuat asisten restoran. Asisten menerima pesanan pelanggan, mengambil daftar menu dan harga melalui fungsi Python, lalu menghitung total pembayaran dan menampilkan rincian pesanan dalam Rupiah.

## Fitur

* Melayani pelanggan menggunakan bahasa Indonesia yang natural.
* Mengenali pesanan makanan dan minuman dari teks pelanggan.
* Memanggil fungsi `get\_menu()` untuk mengambil menu beserta harga.
* Menggunakan harga dari fungsi, bukan membuat perkiraan sendiri.
* Menampilkan rincian pesanan dan total pembayaran.
* Memberi tahu pelanggan dengan sopan jika jenis menu tidak ditemukan.

## Teknologi

* Python
* Google Gen AI SDK (`google-genai`)
* Gemini model `gemini-3.8-flash`
* Google Colab / Python Notebook

## Cara Kerja

1. Menginstal dan mengimpor Google Gen AI SDK.
2. Meminta API Key secara tersembunyi menggunakan `getpass`.
3. Membuat fungsi `get\_menu(menu\_type)` yang mengembalikan daftar menu dan harga.
4. Menentukan `system\_instruction` agar Gemini bertindak sebagai pelayan restoran yang ramah dan profesional.
5. Mendaftarkan fungsi `get\_menu` sebagai tool melalui `GenerateContentConfig`.
6. Mengirim permintaan pelanggan ke model Gemini. Model dapat menggunakan fungsi tersebut untuk memperoleh harga sebelum menyusun jawaban.

## Daftar Menu

Menu yang tersedia ditentukan langsung di dalam fungsi `get\_menu()`.

### Makanan

|Menu|Harga|
|-|-:|
|Nasi goreng|Rp15.000|
|Mie goreng|Rp12.000|
|Sate ayam|Rp20.000|

### Minuman

|Menu|Harga|
|-|-:|
|Es teh|Rp5.000|
|Es jeruk|Rp7.000|
|Kopi|Rp10.000|

Fungsi menerima `food` atau `drink` sebagai jenis menu. Jika jenis menu tidak dikenali, fungsi mengembalikan pesan error `Menu type not found`.

## Contoh Penggunaan

**Input pelanggan:**

> Saya pesan Sate ayam, Nasi goreng, dan es teh. Berapa totalnya?

**Hasil dari notebook:**

|Pesanan|Harga|
|-|-:|
|Sate ayam|Rp20.000|
|Nasi goreng|Rp15.000|
|Es teh|Rp5.000|
|**Total**|**Rp40.000**|

Gemini menampilkan rincian pesanan dan menanyakan apakah pesanan sudah sesuai atau ingin ditambahkan.

## Menjalankan Notebook

1. Buka file notebook di Google Colab atau Jupyter Notebook.
2. Jalankan instalasi dependensi:

```bash
   pip install -q -U google-genai
   ```

3. Jalankan cell import library.
4. Masukkan Google Gemini API Key ketika diminta. Notebook menggunakan `getpass`, sehingga input API Key tidak ditampilkan sebagai teks biasa.
5. Jalankan cell secara berurutan sampai contoh permintaan pelanggan diproses.

## Catatan

* API Key Gemini diperlukan untuk menjalankan model.
* Menu dan harga masih berupa data statis yang ditulis di dalam fungsi Python, belum terhubung ke database atau sistem restoran sungguhan.
* Contoh pada notebook menguji satu permintaan pesanan. Belum terlihat implementasi keranjang pesanan yang persisten, pembayaran, penyimpanan transaksi, atau integrasi layanan pemesanan.
* Hasil contoh menunjukkan total Rp40.000 untuk tiga item yang dipesan.

## Struktur Proyek

```text
gemini-function-calling-restaurant-assistant/
└── gemini-function-calling-restaurant-assistant.ipynb


