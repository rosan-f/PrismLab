# SentraGuard AI

**SentraGuard AI** adalah aplikasi berbasis **Laravel 12** yang berfungsi untuk melakukan *pemindaian keamanan website* secara otomatis.
Aplikasi ini membantu pengguna mendeteksi kelemahan dasar dari konfigurasi web, seperti header keamanan, HTTPS, dan potensi redirect mencurigakan, kemudian memberikan **analisis dan rekomendasi perbaikan menggunakan kecerdasan buatan (AI).**

---

## Fitur Utama

* **Pemindaian Website Otomatis**

  * Cukup masukkan URL, sistem akan menganalisis status HTTPS, header keamanan (`CSP`, `X-Frame-Options`, `HSTS`, dll), dan pola redirect.

* **Analisis AI & Rekomendasi Perbaikan**

  * Menggunakan API AI (gemini atau model serupa) untuk memberikan saran spesifik:

    * Apa risiko dari konfigurasi saat ini
    * Langkah teknis untuk memperbaikinya
    * Contoh konfigurasi aman (misal contoh CSP header)

* 📊 **Skor Keamanan (0–100)**

  * Sistem menilai tingkat keamanan website berdasarkan hasil pemindaian dan header yang ditemukan.

* 📈 **Dashboard Visualisasi**

  * Tampilan hasil pemindaian dalam bentuk grafik (Chart.js)
  * Riwayat hasil scan tersimpan dan dapat dilihat ulang

* **Autentikasi & Manajemen Pengguna**

  * Setiap pengguna memiliki akun untuk menyimpan hasil pemindaian mereka.

---

## Teknologi yang Digunakan

| Komponen          | Teknologi                      |
| ----------------- | ------------------------------ |
| Framework Backend | Laravel 12                     |
| Frontend          | Blade / TailwindCSS / Chart.js |
| HTTP Client       | Guzzle (Laravel HTTP Facade)   |
| AI Integration    | Gemini API                     |
| Database          | PostgreSQL                     |
| Authentication    | Laravel Breeze                 |
| Version Control   | Git & GitHub                   |

---

## Arsitektur Sederhana

```text
┌───────────────────────────┐
│        User Input         │
│        (URL target)       │
└────────────┬──────────────┘
             │
             ▼
┌───────────────────────────┐
│   ScanController          │
│ - Validasi URL            │
│ - HTTP Request (Guzzle)   │
│ - Analisis Header & HTTPS │
│ - Skor Keamanan           │
└────────────┬──────────────┘
             │
             ▼
┌───────────────────────────┐
│     AI Analyzer (API)     │
│ - Kirim hasil scan ke AI  │
│ - Terima saran perbaikan  │
└────────────┬──────────────┘
             │
             ▼
┌───────────────────────────┐
│  Dashboard & History UI   │
│ - Chart & Detail Temuan   │
│ - AI Recommendation View  │
└───────────────────────────┘
```

---

## Skor Keamanan

| Komponen                      | Bobot | Keterangan                          |
| ----------------------------- | ----- | ----------------------------------- |
| HTTPS & Sertifikat Valid      | 30    | Keamanan koneksi                    |
| Header HSTS                   | 15    | Menegakkan HTTPS                    |
| CSP (Content Security Policy) | 20    | Cegah XSS                           |
| X-Frame-Options               | 10    | Cegah Clickjacking                  |
| X-Content-Type-Options        | 5     | Validasi MIME                       |
| Redirect Aman                 | 10    | Hindari open redirect               |
| Header Tambahan               | 10    | Referrer-Policy, Permissions-Policy |

---

## Contoh Output AI

```json
{
  "summary": "Website menggunakan HTTPS namun belum memiliki Content-Security-Policy dan HSTS.",
  "findings": [
    {
      "title": "Missing Content-Security-Policy",
      "severity": "high",
      "recommend": "Tambahkan CSP untuk membatasi sumber script.",
      "example_config": "Content-Security-Policy: default-src 'self'; script-src 'self';"
    },
    {
      "title": "HSTS Header Not Found",
      "severity": "medium",
      "recommend": "Tambahkan Strict-Transport-Security untuk memaksa HTTPS.",
      "example_config": "Strict-Transport-Security: max-age=31536000; includeSubDomains"
    }
  ],
  "score": 65
}
```

---



## Disclaimer

Aplikasi ini **tidak melakukan serangan atau eksploitasi aktif**.
Semua pemeriksaan bersifat **pasif**, hanya membaca header dan konfigurasi publik.
Gunakan **SentraGuard AI** untuk edukasi dan keamanan website **yang Anda miliki atau telah mendapat izin eksplisit.**

---

## Tujuan Proyek

> Memberikan sarana pembelajaran interaktif untuk mahasiswa dan profesional di bidang keamanan web agar dapat memahami:
>
> * pentingnya konfigurasi header,
> * deteksi kesalahan umum pada server,
> * dan bagaimana kecerdasan buatan dapat membantu proses audit keamanan dasar.

---
