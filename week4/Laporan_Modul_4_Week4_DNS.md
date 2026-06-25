# LAPORAN PRAKTIKUM JARINGAN KOMPUTER
## Modul 4 — DNS
### Minggu ke-4

| | |
|---|---|
| **Nama** | ............................................ |
| **NIM** | ............................................ |
| **Kelas** | ............................................ |
| **Tanggal Praktikum** | ............................................ |
| **Asisten Praktikum** | ............................................ |

---

## 1. Tujuan Praktikum
Mahasiswa dapat menginvestigasi cara kerja DNS menggunakan Wireshark.

## 2. Dasar Teori

**Domain Name System (DNS)** menerjemahkan nama host (domain) menjadi alamat IP.
- **nslookup** — utilitas untuk mengirim query DNS secara manual ke server DNS tertentu.
  Sintaks umum: `nslookup -option1 -option2 host-to-find dns-server`.
  - Tipe query default adalah record **A** (alamat IP).
  - Opsi `-type=NS` digunakan untuk meminta nama server DNS otoritatif suatu domain.
- **ipconfig /all** — menampilkan konfigurasi TCP/IP, termasuk alamat server DNS lokal.
  `ipconfig /displaydns` menampilkan cache DNS lokal, `ipconfig /flushdns` mengosongkannya.
- DNS umumnya menggunakan **UDP port 53**.

## 3. Alat dan Bahan
- Wireshark
- Command Prompt/Terminal
- Browser web

## 4. Langkah Percobaan

### 4.1 Eksplorasi nslookup
Jalankan dan amati tiga perintah nslookup berikut, sebagai latihan mandiri:
1. `nslookup <web_server_Asia>` — mencari alamat IP server web di Asia.
2. `nslookup -type=NS <universitas_Eropa>` — mencari DNS otoritatif universitas di Eropa.
3. `nslookup <mail_server_Yahoo> <salah_satu_server_dari_no.2>` — mencari info mail server
   Yahoo melalui server hasil dari langkah 2.

### 4.2 Tracing DNS dengan Wireshark (Browsing)
1. Kosongkan cache DNS: `ipconfig /flushdns`
2. Bersihkan cache browser.
3. Buka Wireshark, terapkan filter `ip.addr == <alamat_IP_Anda>`.
4. Mulai capture, akses `http://www.ietf.org`, lalu hentikan capture.

### 4.3 nslookup + Wireshark
1. Mulai capture Wireshark.
2. Jalankan: `nslookup www.mit.edu`
3. Hentikan capture.
4. Ulangi dengan: `nslookup -type=NS mit.edu`
5. Ulangi dengan: `nslookup www.aiit.or.kr bitsy.mit.edu`

## 5. Hasil Pengamatan dan Analisis

### 5.1 Eksplorasi nslookup Mandiri
```
[Sisipkan screenshot hasil ketiga perintah nslookup di sini]
```
1. Alamat IP server web di Asia yang Anda temukan: .....................................
2. Nama server DNS otoritatif universitas di Eropa: .....................................
3. Alamat IP mail server Yahoo! Mail hasil query: .....................................

### 5.2 Tracing DNS — Browsing ke www.ietf.org
```
[Sisipkan screenshot capture Wireshark di sini]
```
1. Pesan permintaan dan balasan DNS dikirimkan melalui UDP atau TCP? .....................................
2. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasannya?
   .....................................
3. Pada pesan permintaan DNS, apa alamat IP tujuannya? Apakah sama dengan alamat IP
   server DNS lokal Anda (`ipconfig /all`)? .....................................
4. Apa "jenis"/"type" dari pesan permintaan DNS tersebut? Apakah pesan tersebut
   mengandung "jawaban"/"answers"? .....................................
5. Pada pesan balasan DNS, berapa banyak "jawaban" yang terdapat? Apa isi setiap jawaban
   tersebut? .....................................
6. Apakah alamat IP tujuan pada paket TCP SYN berikutnya sesuai dengan alamat IP pada
   pesan balasan DNS? .....................................
7. Halaman `www.ietf.org` memuat beberapa gambar. Apakah host Anda mengirim pesan DNS
   baru setiap kali mengambil gambar tersebut? Jelaskan. .....................................

### 5.3 nslookup www.mit.edu (dengan Wireshark)
```
[Sisipkan screenshot capture di sini]
```
1. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasan DNS?
   .....................................
2. Ke alamat IP mana pesan permintaan DNS dikirimkan? Apakah itu default DNS lokal Anda?
   .....................................
3. Apa "jenis"/"type" dari pesan tersebut? Apakah mengandung jawaban? .....................................
4. Berapa banyak jawaban pada pesan balasan? Apa isi setiap jawaban? .....................................

### 5.4 nslookup -type=NS mit.edu (dengan Wireshark)
```
[Sisipkan screenshot capture di sini]
```
1. Ke alamat IP mana pesan permintaan DNS dikirimkan? Apakah default DNS lokal Anda?
   .....................................
2. Apa "jenis"/"type" dari pesan tersebut? Apakah mengandung jawaban? .....................................
3. Apa nama server MIT yang diberikan pada pesan balasan? Apakah disertai alamat IP-nya
   juga? .....................................

### 5.5 nslookup www.aiit.or.kr bitsy.mit.edu (dengan Wireshark)
```
[Sisipkan screenshot capture di sini]
```
1. Ke alamat IP mana pesan permintaan DNS dikirimkan? Apakah default DNS lokal Anda?
   .....................................
2. Apa "jenis"/"type" dari pesan tersebut? Apakah mengandung jawaban? .....................................
3. Berapa banyak jawaban pada pesan balasan? Apa isi setiap jawaban tersebut? .....................................

## 6. Kesimpulan
......................................................................
......................................................................
......................................................................

## Daftar Pustaka
1. Kurose, J.F., Ross, K.W. *Computer Networking: A Top-Down Approach*, 8th ed., Pearson, 2021.
2. Modul Praktikum Jaringan Komputer, S1 Informatika, Telkom University, Semester Genap 2025/2026.
