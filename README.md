
##  **PrismLab — API Testing & Local Web Security Testing Toolkit**

**PrismLab** adalah aplikasi web yang membantu developer melakukan **pengujian API** dan **pemeriksaan keamanan web dasar**, serta menyediakan lingkungan aman untuk menguji serangan web **khusus pada server lokal**.

Aplikasi ini menggabungkan kemampuan utama seperti alat uji API dan fitur pengecekan keamanan ringan untuk membantu proses development, debugging, dan pembelajaran cybersecurity secara aman dan legal.

---

# **Fitur Utama**

## **1. API Tester (Postman Lite)**

Fitur untuk menguji endpoint API secara cepat dan efisien.

### Fitur API Tester:

* Pilihan metode: GET, POST, PUT, DELETE
* Input URL
* Custom headers
* Input body JSON
* Melihat hasil response:

  * Status Code
  * Response Time
  * Response Headers
  * Response Body (formatted & raw)
* Seluruh request disimpan ke database sebagai riwayat

---

## **2. Web Security Testing (Local Only)**

PrismLab menyediakan fitur pemeriksaan keamanan dasar pada website, tetapi **dibatasi hanya untuk server lokal** (localhost atau jaringan private). Pembatasan ini dibuat untuk memastikan penggunaan tetap aman dan sesuai hukum.

### Fitur Security Testing:

#### **SSL Check**

* Deteksi apakah HTTPS digunakan
* Validitas sertifikat SSL
* Informasi tanggal kedaluwarsa SSL

#### **Security Headers Check**

Pemeriksaan terhadap header keamanan penting:

* Content-Security-Policy
* Strict-Transport-Security
* X-Frame-Options
* X-Content-Type-Options
* Referrer-Policy

####  **Sensitive File Exposure Check**

Mendeteksi keberadaan file sensitif (khusus target lokal):

* `/.env`
* `/phpinfo.php`
* `/backup.zip`

> Fitur ini **tidak dapat digunakan pada website publik**.
> PrismLab otomatis menolak URL non-local.

---

## **3. Local Attack Playground**

PrismLab menyediakan lingkungan khusus untuk menguji serangan dasar, tetapi **hanya pada server lokal** yang dibuat dan dikontrol pengguna.

Fitur serangan yang tersedia di local mode:

* SQL Injection Testing (error-based)
* XSS Testing (reflected)
* Directory brute-force (wordlist dasar)
* Brute-force login simulasi
* Parameter fuzzing
* Command injection testing (simulasi)

PrismLab membatasi target:

* Hanya `localhost`, `127.0.0.1`, dan jaringan private
* URL di luar ini akan ditolak

Dengan demikian, fitur serangan tidak dapat disalahgunakan.

---

## **4. Dashboard**

Dashboard menampilkan informasi ringkas:

* Jumlah total API request
* Jumlah total security scan
* Riwayat penggunaan terbaru
* Ringkasan aktivitas pengguna

---

## **5. Database Integration**

PrismLab menyimpan:

* Riwayat pengujian API
* Riwayat pemeriksaan keamanan
* Catatan aktivitas attack tool (local mode)
* Data pengguna

Tabel yang digunakan:

* `users`
* `api_requests`
* `security_scans`
* `attack_logs`

---

