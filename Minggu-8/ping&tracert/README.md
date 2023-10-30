# Minggu-8 | Ping & Traceroute di Command Prompt

    Nama		: Moch. Irham Kafi Billah
    NRP		: 3122600009
    Kelas		: 2 D4 Teknik Informatika
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

#

## 1. Ping

Perintah ping bekerja dengan cara mengirim paket ke alamat yang ditentukan, pengirim paket menunggu balasan dari alamat tersebut. Perjalanan paket dari mulai dikirim dan balik lagi ke pengirim memerlukan waktu. Makin cepat paket kembali ke pengirim, maka makin bagus koneksi antara pengirim dan tujuan. Bila melakukan ping ke 2 alamat tujuan yang berbeda dengan memakai jaringan yang sama, bisa disimpulkan letak server dari 2 alamat tujuan tersebut.

Berikut adalah elemen-elemen utama yang Anda lihat saat menjalankan tes ping di cmd:

1. Paket Data: Setiap kali Anda menjalankan tes ping, cmd mengirimkan serangkaian paket data ke alamat tujuan yang Anda tentukan. Paket data ini berisi informasi yang diperlukan untuk mengukur respons dari alamat tersebut.

2. Waktu (Time): Salah satu elemen yang paling penting dalam hasil ping adalah waktu (time) yang diperlukan untuk setiap paket data untuk pergi ke alamat tujuan dan kembali lagi ke komputer Anda. Ini diukur dalam milisecond (ms) dan menunjukkan berapa lama perjalanan pulang-pergi paket data tersebut.

3. TTL (Time To Live): TTL adalah nilai yang ditambahkan ke setiap paket data yang dikirim. Nilai ini menurun setiap kali paket data melewati perangkat jaringan seperti router. Jika TTL mencapai nol, paket data akan dibuang. Informasi TTL dapat memberikan gambaran tentang jumlah "langkah" atau router yang diperlukan untuk mencapai alamat tujuan.

4. Ukuran Paket: Ukuran paket data yang dikirimkan dalam tes ping dapat bervariasi. Biasanya, ukuran paket ping adalah 32 byte, tetapi ini dapat diubah sesuai preferensi atau kebutuhan pengguna.

5. Rute (Route): Hasil ping biasanya menampilkan rute yang diambil oleh paket data untuk mencapai tujuan. Ini adalah daftar alamat IP dari setiap perangkat jaringan yang dilalui paket data selama perjalanan.

6. Statistik: Setelah semua paket data telah dikirim dan diterima, cmd akan menampilkan statistik mengenai kecepatan, waktu minimum, waktu maksimum, dan rata-rata respons dari alamat tujuan.

7. Keterangan Kesalahan: Jika ada masalah dengan koneksi, Anda mungkin akan melihat keterangan kesalahan seperti "Request Timed Out" (Permintaan Waktu Habis), yang menunjukkan bahwa paket data tidak berhasil sampai ke tujuan dalam batas waktu yang ditentukan.

#### Percobaan ping www.detik.com

<div align="center">
    <img src="assets/ping1.png" alt="Tes ping" width="70%">
    <p><strong>Gambar:</strong> Ping ke www.detik.com</p>
</div>

Analisa :

- Pinging detik.com [103.49.221.211] with 32 bytes of data: Ini adalah baris yang memberikan informasi tentang apa yang akan di-ping. Perintah akan mengirim paket data ke alamat IP 103.49.221.211, yang sesuai dengan nama domain "detik.com." Setiap paket data memiliki ukuran 32 byte.

- Reply from 103.49.221.211: bytes=32 time=102ms TTL=58: Ini adalah hasil dari ping yang pertama. Ini menunjukkan bahwa paket data telah dikirimkan dengan sukses ke alamat IP 103.49.221.211, dan Anda menerima balasan. Elemen-elemen berikut ini menjelaskan detailnya:

- "Reply from 103.49.221.211": Ini menunjukkan bahwa Anda menerima respons dari alamat IP tujuan. "bytes=32": Ini adalah ukuran paket data yang dikirimkan, yaitu 32 byte. "time=102ms": Ini adalah waktu yang diperlukan untuk paket data pergi ke tujuan dan kembali, diukur dalam milidetik (ms). TTL=58": Ini adalah Time-to-Live (TTL) atau batasan maksimum perjalanan paket data dalam jaringan. TTL ini berkurang setiap kali paket data melewati hop dalam jaringan.

- Ping statistics for 103.49.221.211: Ini adalah ringkasan statistik dari ping yang telah dilakukan.

- "Packets: Sent = 4": Ini menunjukkan bahwa Anda telah mengirimkan 4 paket data. "Received = 4": Ini menunjukkan bahwa Anda telah menerima respons dari semua 4 paket data yang dikirimkan. "Lost = 0 (0% loss)": Tidak ada paket data yang hilang, yang berarti tidak ada paket data yang hilang dalam perjalanan.

- Approximate round trip times in milli-seconds:
  "Minimum = 102ms": Ini adalah waktu tercepat (minimum) yang diperlukan untuk pergi dan kembali dari tujuan, diukur dalam milidetik.
  "Maximum = 152ms": Ini adalah waktu terlama (maksimum) yang diperlukan untuk pergi dan kembali dari tujuan, diukur dalam milidetik. "Average = 124ms": Ini adalah rata-rata waktu yang diperlukan untuk pergi dan kembali dari tujuan, diukur dalam milidetik.

## 2. Traceroute

Traceroute (Tracert) adalah perintah untuk menunjukkan rute yang dilewati paket untuk mencapai tujuan. Ini dilakukan dengan mengirim pesan Internet Control Message Protocol (ICMP) Echo Request Ke tujuan dengan nilai Time to Live yang semakin meningkat. Rute yang ditampilkan adalah daftar interface router (yang paling dekat dengan host) yang terdapat pada jalur antara host dan tujuan.

Berikut adalah elemen-elemen utama yang Anda lihat saat menjalankan tes tracert di cmd:

1. Hop: Setiap langkah dalam perjalanan paket data dari komputer Anda ke alamat tujuan disebut sebagai "hop." Setiap hop mewakili perangkat jaringan seperti router yang ditemui oleh paket data dalam perjalanan menuju tujuan.

2. Waktu (Time): Seperti pada perintah "ping," waktu (time) di sini menunjukkan berapa lama dibutuhkan oleh setiap paket data untuk mencapai hop berikutnya. Ini diukur dalam milisecond (ms) dan menunjukkan latensi pada setiap hop.

3. Nama Host atau Alamat IP: Untuk setiap hop, Anda akan melihat nama host (jika tersedia) atau alamat IP perangkat jaringan yang ada di hop tersebut. Ini membantu Anda memahami jalur perjalanan data dan mengidentifikasi perangkat jaringan tertentu.

4. Hilang (Loss): Terkadang, paket data dapat hilang di salah satu hop, biasanya disebabkan oleh kelebihan lalu lintas, masalah jaringan, atau firewall yang memblokir respons. Anda akan melihat asterisk (\*) atau waktu yang lebih lama untuk mengindikasikan paket data yang hilang.

5. Jarak (TTL - Time To Live): Seperti pada perintah "ping," nilai TTL menunjukkan berapa banyak hop yang ditemui oleh paket data sebelum mencapai tujuan akhir atau sebelum TTL mencapai nol. Hal ini membantu Anda melihat seberapa banyak perangkat jaringan yang ditemui dalam perjalanan.

6. Statistik: Setelah semua hop telah dilacak, cmd akan menampilkan statistik mengenai waktu minimum, maksimum, dan rata-rata respons pada setiap hop.

7. Keterangan Kesalahan: Jika ada hop yang tidak merespons atau mengalami masalah, Anda mungkin akan melihat keterangan kesalahan seperti "Request Timed Out" (Permintaan Waktu Habis).

#### Percobaan tracert www.detik.com

<div align="center">
    <img src="assets/tracert1.png" alt="Traceroute" width="70%">
    <p><strong>Gambar:</strong> Traceroute ke www.detik.com</p>
</div>

Analisa :

- "tracert www.detik.com": Ini adalah perintah yang Anda jalankan untuk melacak rute jaringan ke situs web "www.detik.com" yang resolusi IP-nya adalah 103.49.221.211. Perintah ini akan mengungkapkan semua hop jaringan antara komputer Anda dan server tujuan.

- "Tracing route to detik.com [103.49.221.211]": Output ini menunjukkan bahwa perintah "tracert" sedang melakukan pelacakan rute ke alamat IP 103.49.221.211, yang merupakan alamat IP untuk "www.detik.com."

- "over a maximum of 30 hops": Ini menunjukkan bahwa perintah akan melacak hingga 30 hop (atau langkah) dalam rute jaringan, maksimum.

- Kemudian, daftar hasil "tracert" dimulai:

> Hop 1: Ini adalah langkah pertama dalam rute, yang merupakan router di dalam jaringan lokal Anda dengan alamat IP 192.168.100.1.

> Hop 2: Ini adalah hop kedua, dan tampaknya ada beberapa latency (keterlambatan) dalam komunikasi dengan alamat IP 10.9.0.1. Kemungkinan ini adalah router berikutnya dalam rute.

> Hop 3: Ini adalah hop ketiga, dengan alamat IP 103.94.168.14, yang mungkin merupakan bagian dari jaringan penyedia layanan internet Anda.

> Hop 4: Ini adalah hop keempat, dengan alamat IP 103.94.168.233, yang juga merupakan bagian dari jaringan penyedia layanan internet Anda.

> Hop 5: Hop kelima menunjukkan "Request timed out," yang berarti tidak ada respons dari hop ini. Ini bisa terjadi karena hop ini diatur untuk tidak merespons permintaan ICMP, atau ada masalah konektivitas di sana.

> Hop 6: Hop keenam memiliki alamat IP 218.100.36.9, yang kemungkinan adalah salah satu hop dalam jaringan penyedia layanan internet atau server tujuan.

> Hop 7: Hop ketujuh menunjukkan alamat IP 103.49.221.211, yang sesuai dengan tujuan akhir, yaitu "s211-cast-211-221-49-103.detik.com."

Berikut penjelasan untuk setiap kolom dalam perintah tracert:

1. Hop Number: Ini adalah urutan dari langkah-langkah dalam tracert. Hop pertama adalah router atau perangkat pertama yang data Anda lewati dalam perjalanan menuju tujuan, hop kedua adalah yang kedua, dan seterusnya.

2. Round-Trip Time (RTT) 1: Ini adalah waktu yang diperlukan untuk paket data pergi dari komputer Anda ke hop ini dan kembali ke komputer Anda. RTT diukur dalam milidetik (ms).

3. Round-Trip Time (RTT) 2: Ini adalah pengukuran kedua dari RTT, yang menunjukkan waktu yang diperlukan untuk dua perjalanan (pergi dan kembali) dari komputer Anda ke hop ini dan kembali.

4. Round-Trip Time (RTT) 3: Ini adalah pengukuran ketiga dari RTT, seperti yang dijelaskan di atas.
