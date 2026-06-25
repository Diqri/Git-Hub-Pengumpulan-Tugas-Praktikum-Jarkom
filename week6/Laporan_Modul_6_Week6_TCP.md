# LAPORAN PRAKTIKUM JARINGAN KOMPUTER
## Modul 6 — TCP
### Minggu ke-6

| | |
|---|---|
| **Nama** | ............................................ |
| **NIM** | ............................................ |
| **Kelas** | ............................................ |
| **Tanggal Praktikum** | ............................................ |
| **Asisten Praktikum** | ............................................ |

---

## 1. Tujuan Praktikum
Mahasiswa dapat menginvestigasi cara kerja protokol TCP menggunakan Wireshark.

## 2. Dasar Teori

**Transmission Control Protocol (TCP)** adalah protokol transport-layer yang
*connection-oriented* dan andal (*reliable*). Beberapa konsep kunci yang dipelajari pada
modul ini:
- **Three-way handshake** — `SYN` → `SYN/ACK` → `ACK`, digunakan untuk membangun koneksi.
- **Sequence Number & Acknowledgement Number** — digunakan untuk memastikan data sampai
  secara utuh dan berurutan.
- **Round Trip Time (RTT)** — selisih waktu antara saat segmen dikirim dan ACK-nya diterima.
- **Flow Control** — bidang *Window Size* yang disarankan penerima agar pengirim tidak
  membanjiri buffer penerima.
- **Congestion Control** — algoritma *slow start* dan *congestion avoidance* yang mengatur
  laju pengiriman data berdasarkan kondisi jaringan, dapat diamati melalui grafik
  *Time-Sequence-Graph (Stevens)* pada Wireshark.

## 3. Alat dan Bahan
- Wireshark
- Browser web
- File `alice.txt` (naskah *Alice's Adventures in Wonderland*)
- File trace (jika diperlukan): `tcp-ethereal-trace-1`

## 4. Langkah Percobaan
1. Unduh `http://gaia.cs.umass.edu/wireshark-labs/alice.txt` dan simpan di komputer.
2. Buka `http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html`.
3. Pilih file `alice.txt` melalui tombol **Browse**, lalu mulai capture Wireshark.
4. Klik **Upload alice.txt file**, tunggu sampai selesai, lalu hentikan capture.
5. Terapkan filter `tcp`.
6. (Opsional) Nonaktifkan protokol HTTP (Analyze → Enabled Protocols → uncheck HTTP) agar
   hanya terlihat segmen TCP murni.
7. Gunakan **Statistics → TCP Stream Graph → Time-Sequence-Graph (Stevens)** untuk melihat
   grafik nomor urut vs waktu.
8. Gunakan **Statistics → TCP Stream Graph → Round Trip Time Graph** untuk melihat grafik RTT.

## 5. Hasil Pengamatan

### 5.1 Capture Upload alice.txt
```
[Sisipkan screenshot capture Wireshark (filter "tcp") di sini]
```

### 5.2 Time-Sequence-Graph (Stevens)
```
[Sisipkan screenshot grafik Time-Sequence di sini]
```

## 6. Analisis

### 6.1 Tampilan Awal pada Captured Trace
1. Berapa alamat IP dan nomor port TCP komputer klien (sumber) untuk transfer file ke
   `gaia.cs.umass.edu`? .....................................
2. Berapa alamat IP `gaia.cs.umass.edu`? Pada nomor port berapa ia mengirim/menerima
   segmen TCP untuk koneksi ini? .....................................
3. (Jika menggunakan trace sendiri) Berapa alamat IP dan nomor port TCP komputer Anda?
   .....................................

### 6.2 Dasar TCP
1. Berapa nomor urut segmen TCP **SYN** untuk memulai koneksi? Apa ciri yang
   mengidentifikasinya sebagai segmen SYN? .....................................
2. Berapa nomor urut segmen **SYN/ACK** dari server? Berapa nilai *Acknowledgement*-nya,
   dan bagaimana server menentukan nilai tersebut? .....................................
3. Berapa nomor urut segmen TCP yang berisi perintah **HTTP POST**? .....................................
4. Catat nomor urut, waktu kirim, dan waktu ACK diterima untuk **6 segmen pertama** TCP
   (termasuk segmen HTTP POST). Hitung nilai RTT dan *EstimatedRTT* setelah setiap ACK
   diterima.

   | Segmen | Seq No. | Waktu Kirim | Waktu ACK Diterima | RTT | EstimatedRTT |
   |---|---|---|---|---|---|
   | 1 | | | | | |
   | 2 | | | | | |
   | 3 | | | | | |
   | 4 | | | | | |
   | 5 | | | | | |
   | 6 | | | | | |

5. Berapa panjang (byte) masing-masing dari 6 segmen TCP pertama tersebut? .....................................
6. Berapa jumlah minimum *receive window* (buffer) yang disarankan untuk seluruh trace?
   Apakah keterbatasan buffer penerima pernah menghambat pengiriman? .....................................
7. Apakah ada segmen yang ditransmisikan ulang (*retransmission*) pada trace? Apa yang
   Anda periksa untuk menjawab ini? .....................................
8. Berapa banyak data yang biasanya diakui (*ACK*) oleh penerima sekaligus? Apakah ada
   kasus penerima mengirim ACK untuk setiap segmen yang diterima? .....................................
9. Berapa throughput (byte/satuan waktu) koneksi TCP ini? Jelaskan cara menghitungnya.
   .....................................

### 6.3 Congestion Control pada TCP
1. Berdasarkan grafik Time-Sequence (Stevens), identifikasi di mana fase **slow start**
   dimulai dan berakhir, dan di mana **congestion avoidance** mengambil alih. Berikan
   komentar tentang perbedaan data yang diukur dengan perilaku ideal TCP yang dipelajari
   di teori. .....................................
2. (Jika menggunakan trace sendiri) Jawab kembali pertanyaan di atas menggunakan trace
   hasil upload Anda sendiri. .....................................

## 7. Kesimpulan
......................................................................
......................................................................
......................................................................

## Daftar Pustaka
1. Kurose, J.F., Ross, K.W. *Computer Networking: A Top-Down Approach*, 8th ed., Pearson, 2021.
2. Modul Praktikum Jaringan Komputer, S1 Informatika, Telkom University, Semester Genap 2025/2026.
