# LAPORAN PRAKTIKUM JARINGAN KOMPUTER
## Modul 5 — UDP
### Minggu ke-5

| | |
|---|---|
| **Nama** | ............................................ |
| **NIM** | ............................................ |
| **Kelas** | ............................................ |
| **Tanggal Praktikum** | ............................................ |
| **Asisten Praktikum** | ............................................ |

---

## 1. Tujuan Praktikum
Mahasiswa dapat menginvestigasi cara kerja protokol UDP menggunakan Wireshark.

## 2. Dasar Teori

**User Datagram Protocol (UDP)** adalah protokol transport-layer yang sederhana dan
*connectionless* (tanpa koneksi). Header UDP terdiri dari 4 bidang utama, masing-masing
**2 byte**, sehingga total header berukuran **8 byte**:

| Bidang | Ukuran | Keterangan |
|---|---|---|
| Source Port | 2 byte | Nomor port pengirim |
| Destination Port | 2 byte | Nomor port tujuan |
| Length | 2 byte | Panjang total (header + data) UDP dalam byte |
| Checksum | 2 byte | Untuk deteksi error sederhana |

Karena bidang *Length* berukuran 2 byte (16 bit), nilai maksimumnya adalah 2¹⁶ − 1 = 65535
byte (termasuk header 8 byte), sehingga payload maksimum = 65535 − 8 = **65527 byte**.
Nomor port pada UDP/TCP juga 16 bit, sehingga nomor port terbesar yang mungkin adalah
**65535**. Nomor protokol UDP pada bidang *Protocol* datagram IP adalah **17 (desimal)**
atau **0x11 (heksadesimal)**.

## 3. Alat dan Bahan
- Wireshark

## 4. Langkah Percobaan
1. Mulai capture paket di Wireshark.
2. Lakukan aktivitas yang menghasilkan trafik UDP (browsing, atau biarkan trafik SNMP/DNS
   tertangkap secara alami).
3. Hentikan capture, terapkan filter `udp`.
4. Pilih salah satu paket UDP, lalu perluas detail header-nya.

## 5. Hasil Pengamatan
```
[Sisipkan screenshot capture Wireshark dengan filter "udp", beserta detail header
salah satu paket UDP yang dipilih, di sini]
```

| No. Paket | Source Port | Destination Port | Length | Checksum |
|---|---|---|---|---|
| | | | | |

## 6. Analisis

1. Pilih satu paket UDP pada trace Anda. Berapa banyak *field* yang terdapat pada
   header UDP? Sebutkan nama-nama field tersebut. .....................................

2. Berapa panjang (byte) masing-masing field pada header UDP yang Anda temukan?
   .....................................

3. Nilai pada bidang *Length* menyatakan apa? Verifikasi jawaban Anda dengan menghitung
   ulang berdasarkan ukuran payload pada paket tersebut. .....................................

4. Berapa jumlah maksimum byte yang dapat disertakan dalam payload UDP? (berdasarkan
   ukuran maksimum bidang *Length* dikurangi ukuran header) .....................................

5. Berapa nomor port terbesar yang dapat menjadi port sumber? .....................................

6. Berapa nomor protokol untuk UDP (dalam notasi heksadesimal dan desimal)? Tunjukkan
   pada bidang *Protocol* di datagram IP yang Anda amati. .....................................

7. Periksa sepasang paket UDP di mana host Anda mengirim paket pertama dan menerima
   paket kedua sebagai balasannya. Jelaskan hubungan antara nomor port sumber/tujuan
   pada kedua paket tersebut (mengapa port sumber paket pertama menjadi port tujuan
   paket kedua, dan sebaliknya). .....................................

## 7. Kesimpulan
......................................................................
......................................................................
......................................................................

## Daftar Pustaka
1. Kurose, J.F., Ross, K.W. *Computer Networking: A Top-Down Approach*, 8th ed., Pearson, 2021.
2. Modul Praktikum Jaringan Komputer, S1 Informatika, Telkom University, Semester Genap 2025/2026.
