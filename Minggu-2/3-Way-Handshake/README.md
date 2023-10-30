# 3 Way Handshake

    Nama		: Moch. Irham Kafi Billah
    NRP		: 3122600009
    Kelas		: 2 D4 Teknik Informatika
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

#

<div align="center">
    <img src="assets/3way.png" alt="3 Way Handshake" width="70%">
    <p><strong>Gambar:</strong> 3 Way Handshake</p>
</div>

3 Way handshake adalah bagian dari proses pembangunan koneksi (connection establishment) dalam protokol TCP. Tahapan ini melibatkan tiga langkah utama untuk memulai koneksi antara dua perangkat: SYN (permintaan sinkronisasi), SYN-ACK (persetujuan sinkronisasi dan permintaan sinkronisasi), dan ACK (persetujuan sinkronisasi). Berikut adalah penjelasan dari langkah-langkah dalam 3-way handshake:

### Langkah 1: Permintaan Sinkronisasi (SYN):

- Pada langkah pertama, klien (misalnya, browser pada komputer klien) ingin memulai koneksi dengan server.
- Klien mengirimkan paket khusus yang disebut "SYN packet" ke server.
- Paket ini berisi nomor urut sekuen (sequence number) awal yang digunakan untuk mengidentifikasi data dalam koneksi, serta nomor acak yang disebut "initial sequence number" (ISN).

### Langkah 2: Persetujuan Sinkronisasi dan Permintaan Sinkronisasi (SYN-ACK):

- Setelah server menerima paket SYN dari klien, server akan mengirimkan balasan SYN-ACK (Synchronize-Acknowledgment) ke klien.
- Balasan ini berisi nomor urut sekuen yang dihasilkan oleh server (biasanya dengan tambahan 1), nomor ACK (acknowledgment number) yang merupakan nomor urut sekuen yang diharapkan dari klien selanjutnya, dan juga nomor acak ISN yang dihasilkan oleh server.
- Server juga mengonfirmasi SYN yang telah diterima dari klien dengan mengatur flag SYN dan ACK pada paket.

### Langkah 3: Persetujuan Sinkronisasi (ACK):

- Klien menerima paket SYN-ACK dari server.
- Klien mengirimkan kembali paket ACK (Acknowledgment) ke server sebagai tanda bahwa paket SYN-ACK telah diterima.
- Klien juga menambahkan nomor ACK yang sesuai dengan nomor urut sekuen dari server yang telah diterima.
- Server pun menerima paket ACK tersebut, dan koneksi TCP dianggap sudah berhasil terbentuk.

Setelah 3-way handshake berhasil, koneksi TCP dapat memulai **transfer data (data transfer)** antara klien dan server.

Pada akhirnya, **connection termination** (penutupan koneksi) juga melibatkan beberapa langkah untuk mengakhiri koneksi dengan benar. Biasanya ini melibatkan 4 langkah dan disebut **4-way handshake**.
