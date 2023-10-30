# Network Configuration

     Nama		: Moch. Irham Kafi Billah
    NRP		: 3122600009
    Kelas		: 2 D4 Teknik Informatika
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

## 1 Router - 2 Switch - 4 PC

Pada praktikum kali ini, kita menggunakan Cisco Packet Tracer untuk memvisualisasi-kan pc yang saling terhubung dalam satu route.
Dalam konteks ini, kita akan menjelajahi implementasi konkret dari topologi yang melibatkan satu router, dua switch, dan empat komputer (PC).

<div align="center">
    <img src="assets/nc1.png" width="70%">
    <p><strong>Gambar:</strong> Configuration</p>
</div>

## Keterangan tiap komponen

**Router:**

- Antarmuka 0/0:
  - IP Address: 192.168.1.1
  - Subnet Mask: 255.255.255.0
- Antarmuka 0/1:
  - IP Address: 192.168.6.1
  - Subnet Mask: 255.255.255.0

**Switch:** Setiap switch menghubungkan dua PC dalam jaringan yang sama. Penjelasan:

Switch 1:

- PC1:
  - IP Address: 192.168.1.2
  - Subnet Mask: 255.255.255.0
- PC2:
  - IP Address: 192.168.1.3
  - Subnet Mask: 255.255.255.0

Switch 2:

- PC3:
  - IP Address: 192.168.6.2
  - Subnet Mask: 255.255.255.0
- PC4:
  - IP Address: 192.168.6.3
  - Subnet Mask: 255.255.255.0

## Percobaan

### 1. Ping 192.168.1.2 ke 192.168.1.3

<div align="center">
<img src="./assets/ping1.gif">
</div>

mekanisme broadcast digunakan hanya dalam proses ARP untuk menentukan alamat MAC tujuan saat komunikasi pertama kali terjadi antara dua PC yang belum saling kenal. Setelah itu, komunikasi berlangsung menggunakan alamat MAC yang telah diketahui.

1. PC 0 (192.168.1.2) ingin melakukan ping ke PC 1 (192.168.1.3). Ketika PC 0 mencoba mengirim paket, ia menyadari bahwa PC 1 berada dalam jaringan yang sama (subnet yang sama), yaitu 192.168.1.0.

2. PC 0 menentukan bahwa alamat IP PC 1 (192.168.1.3) berada dalam jaringan yang sama, sehingga ia tidak perlu mengirim paket ke router untuk mencapai tujuan. PC 0 tahu bahwa PC 1 ada di jaringan lokal (LAN) yang sama karena keduanya terhubung ke Switch 0, dan Switch 0 adalah perangkat jaringan yang beroperasi di tingkat Layer 2 (Data Link Layer).

3. PC 0 menciptakan paket ICMP (ping) yang ditujukan ke alamat IP 192.168.1.3 (PC 1). Paket ini akan memiliki alamat MAC tujuan yang sesuai dengan alamat MAC PC 1 di jaringan lokal.

4. Namun, karena PC 0 belum tahu alamat MAC PC 1 (karena PC 0 belum pernah berkomunikasi dengan PC 1 sebelumnya), PC 0 harus melakukan proses ARP (Address Resolution Protocol) untuk mengidentifikasi alamat MAC PC 1.

5. PC 0 mengirim pesan ARP broadcast ke alamat MAC broadcast (FF:FF:FF:FF:FF:FF) ke dalam jaringan lokal (subnet) yang bertanya, "Siapa yang memiliki alamat IP 192.168.1.3?" Ini adalah mekanisme broadcast yang digunakan untuk menemukan alamat MAC pemilik alamat IP yang dituju.

6. Switch 0 menerima pesan ARP broadcast dan mengirimkannya ke semua perangkat di jaringan lokal kecuali perangkat pengirimnya (PC 0) karena ini adalah tindakan broadcast. Ini berarti bahwa semua perangkat di jaringan lokal, termasuk PC 1, akan menerima pesan ARP.

### 2. Ping 192.168.1.2 ke 192.168.1.3

<div align="center">
<img src="./assets/ping2.gif">
</div>

Dalam situasi ini, karena PC 0 dan PC 1 sudah saling mengenal dan memiliki informasi alamat MAC satu sama lain, tidak diperlukan mekanisme broadcast atau permintaan ARP. Paket ICMP (ping) dikirimkan langsung ke alamat MAC PC 1 melalui Switch 0 dan diterima oleh PC 1 tanpa perlu mencari tahu alamat MAC terlebih dahulu.

1. PC 0 (192.168.1.2) ingin melakukan ping ke PC 1 (192.168.1.3). Karena keduanya sudah saling mengenal, PC 0 tahu alamat MAC dari PC 1.

2. PC 0 membuat paket ICMP (ping) yang ditujukan ke alamat IP 192.168.1.3 (PC 1) dan menentukan alamat MAC tujuan yang sesuai dengan alamat MAC PC 1.

3. PC 0 mengirimkan paket ICMP ke Switch 0. Switch 0 tahu bahwa PC 1 terhubung ke port-nya dan akan meneruskan paket tersebut ke PC 1 berdasarkan alamat MAC tujuan yang telah ditentukan oleh PC 0.

4. PC 1 menerima paket ICMP dari PC 0 dan meresponsnya jika konfigurasi jaringan dan firewall memungkinkan.

### 3. Ping 192.168.1.2 -> 192.168.6.2 (BRODCAST)

<div align="center">
<img src="./assets/ping3.gif">
</div>

Ketika PC 0 (192.168.1.2) ingin melakukan ping ke PC 2 (192.168.6.2) dan keduanya berada di subnet yang berbeda, maka prosesnya akan melibatkan router sebagai perangkat yang menghubungkan dua subnet yang berbeda. Dalam proses ini, mekanisme broadcast terjadi ketika PC 0 mencoba menentukan alamat MAC dari router, karena router adalah gateway ke subnet yang berbeda.

1. PC 0 (192.168.1.2) ingin melakukan ping ke PC 2 (192.168.6.2). Karena keduanya berada di subnet yang berbeda, PC 0 tahu bahwa untuk mencapai subnet 192.168.6.0, ia harus menggunakan router.

2. PC 0 menciptakan paket ICMP (ping) dengan alamat IP tujuan 192.168.6.2. Namun, PC 0 tidak tahu alamat MAC dari router.

3. PC 0 perlu mengetahui alamat MAC router untuk mengirimkan paket ICMP ke router. Oleh karena itu, PC 0 melakukan permintaan ARP broadcast ke alamat MAC broadcast (FF:FF:FF:FF:FF:FF) dalam jaringan lokal (subnet 192.168.1.0) dengan pertanyaan, "Siapa yang memiliki alamat IP 192.168.1.1?" Alamat IP 192.168.1.1 adalah alamat IP router yang terhubung ke subnet 192.168.1.0.

4. Switch 0 menerima pesan ARP broadcast dari PC 0 dan mengirimkannya ke semua perangkat di jaringan lokal, termasuk router.

5. Router menerima pesan ARP broadcast yang menyatakan bahwa ada permintaan untuk alamat IP 192.168.1.1. Router kemudian merespons pesan ARP ini dengan mengirimkan alamat MAC-nya ke PC 0.

6. PC 0 menerima respons ARP dari router, sehingga sekarang ia tahu alamat MAC dari router.

7. Switch 1 menerima paket dan memutuskan untuk mengirimkannya ke PC 2 berdasarkan alamat MAC tujuan yang telah ditentukan dalam paket ICMP.

8. PC 2 (192.168.6.2) menerima paket ICMP dari PC 0 dan merespons jika konfigurasi jaringan dan firewall memungkinkan.

### 4. Ping 192.168.1.2 ke 192.168.6.2

<div align="center">
<img src="./assets/ping4.gif">
</div>

Dalam situasi ini, karena PC 0 dan PC 2 sudah saling mengenal dan memiliki informasi alamat MAC satu sama lain, tidak diperlukan mekanisme broadcast atau permintaan ARP. Paket ICMP (ping) dikirimkan langsung ke alamat MAC PC 2 melalui Switch 0 dan diterima oleh PC 2 tanpa perlu mencari tahu alamat MAC terlebih dahulu.

1. PC 0 (192.168.1.2) ingin melakukan ping ke PC 2 (192.168.6.2). Karena keduanya sudah saling mengenal, PC 0 tahu alamat MAC dari PC 2 dan tahu bahwa untuk mencapai PC 2 di subnet 192.168.6.0, ia harus menggunakan router.

2. PC 0 menciptakan paket ICMP (ping) dengan alamat IP tujuan 192.168.6.2 dan menentukan alamat MAC PC 2 sebagai alamat tujuan dalam paket.

3. PC 0 mengirimkan paket ICMP ke Switch 0. Switch 0 tahu bahwa PC 2 terhubung ke port-nya dan akan meneruskan paket tersebut ke PC 2 berdasarkan alamat MAC tujuan yang telah ditentukan oleh PC 0.

4. PC 2 (192.168.6.2) menerima paket ICMP dari PC 0 dan meresponsnya jika konfigurasi jaringan dan firewall memungkinkan.

## 1 Router - 2 Hub - 4 PC (Menggantu switch dengan hub)

### 1. Ping 192.168.1.2 -> 192.168.1.3

<div align="center">
<img src="./assets/hub1.gif">
</div>

Dalam situasi ini, karena penggunaan hub, setiap paket yang dikirim dari PC 0 ke hub 0 akan didistribusikan ke semua perangkat yang terhubung ke hub tersebut. Inilah yang disebut dengan mekanisme broadcast karena semua perangkat dalam jaringan mendengar dan menerima paket yang dikirim, bahkan jika paket tersebut sebenarnya ditujukan hanya untuk PC 1.

### 2. Ping 192.168.1.2 -> 192.168.6.2

<div align="center">
<img src="./assets/hub1.gif">
</div>

Dalam situasi ini, karena penggunaan hub, setiap paket yang dikirim dari PC 0 ke hub 0 akan disiarkan ke semua perangkat yang terhubung ke hub tersebut, termasuk PC 2 yang berada di subnet yang berbeda. Hal ini menciptakan mekanisme broadcast yang ineffisien dan dapat menyebabkan overhead lalu lintas jaringan yang signifikan. Switch yang lebih cerdas akan dapat membatasi lalu lintas hanya ke perangkat yang relevan dan meminimalkan mekanisme broadcast, yang mana akan lebih efisien dalam jaringan yang lebih besar atau lebih kompleks.
