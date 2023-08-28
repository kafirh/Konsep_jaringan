# Three-way_Handshaking

### Langkah 1 - Permintaan Koneksi (SYN):

Pihak yang memulai koneksi (biasanya klien) mengirimkan pesan SYN (synchronize) ke pihak tujuan (server). Pesan ini berisi nomor urutan awal yang akan digunakan untuk mengidentifikasi data yang dikirim. Langkah ini menunjukkan bahwa klien ingin menginisiasi koneksi.

### Langkah 2 - Persetujuan Koneksi (SYN-ACK)

Pihak tujuan menerima pesan SYN, kemudian mengirimkan balasan SYN-ACK (synchronize-acknowledge) kembali ke pihak yang memulai koneksi. Pesan SYN-ACK mengandung nomor urutan acak yang dihasilkan oleh server dan nomor urutan awal yang diterima dari klien. Dengan demikian, server menunjukkan persetujuannya untuk memulai koneksi dan menyetujui nomor urutan yang telah diberikan oleh klien

### Langkah 3 - Konfirmasi Koneksi (ACK):

Pihak yang memulai koneksi (klien) menerima pesan SYN-ACK, kemudian mengirimkan balasan ACK (acknowledge) kembali ke pihak tujuan (server). Pesan ACK mengandung nomor urutan yang diinkremen untuk mengonfirmasi bahwa pihak klien telah menerima pesan SYN-ACK. Dengan ini, koneksi dianggap sudah terbentuk dan siap digunakan.

## Fungsi Three-way_handshaking
Setelah tiga langkah ini selesai, kedua perangkat telah menyelesaikan proses three-way handshake dan koneksi TCP-nya sudah aktif. Kedua perangkat dapat mulai bertukar data melalui koneksi tersebut. Three-way handshake memastikan bahwa koneksi dimulai dengan cara yang terkoordinasi dan terjamin, serta memungkinkan kedua pihak untuk menetapkan parameter awal seperti nomor urutan dan jendela ukuran penerimaan (receive window size) yang akan digunakan selama koneksi berlangsung.
