![image](https://github.com/xmall75/Jarkom-Modul-1-D28-2023/assets/115076652/938c7bb8-ec17-4e4b-b499-32dd44586d16)# Jarkom-Modul-1-D28-2023


## No. 6
Soal : 

`Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.`

Dari soal di atas kita pertama-tama dapat menganalisa soal terlebih dahulu. Berdasarkan pengamatan, huruf kapital pada paragraf tidaklah mengikuti standar KBBI. Sehingga jika kita mengambil seluruh huruf kapitalnya akan termuncul sebuah kata `SUBSTITUSI`. Setelah itu terdapat hint `server SOURCE ADDRESS 7812 is invalid` dan `a1 e5 u21`. Mari kita selesaikan satu per satu.

Untuk `server SOURCE ADDRESS 7812 is invalid` dapat kita gunakan wireshark untuk mencari packet ke 7812 dari file PCAP yang diberikan. `.

![goto](src/no6/goto.jpg)

![7812](src/no6/7812.jpg)

Setelah itu kita dapat mengambil source address packet tersebut yakni, `104.18.14.101

![sa](src/no6/sa.jpg)

Kemudian ada hint tadi `SUBSTITUSI` dan `a1 e5 u21`. Ini berarti kita diminta untuk mensubstitusikan source address yang sudah kita dapat dengan metode cipher a1z26. Kita dapat menggunakan website online untuk cipher tersebut, salah satunya seperti website https://planetcalc.com/4884/ yang saya gunakan untuk melakukan substitusi tersebut. Jika kita langsung melakukan cipher tanpa mengubah apa-apa akan didapatkan hasil sebagai berikut.

![cipherawal](src/no6/cipherawal.jpg)

Tetapi karena dari hint diberitahukan bahwa yang di cipher adalah angka 1-18. Kita dapat mencoba untuk memisah source address hingga memenuhi parameter tersebut. Hasilnya adalah sebagai berikut. 

![cipherberhasil](src/no6/cipherberhasil.jpg)

Sekarang dapat kita coba masukkan jawaban di terminal. 

![hasil](/src/no6/hasil.jpg)

Seperti yang dilihat, jawaban benar dan kita berhasil mendapatkan flag.


## No. 7
Soal : 

`Berapa jumlah packet yang menuju IP 184.87.193.88?`

Untuk menjawab soal ini kita perlu menggunakan filter pada file PCAP yang diberikan. Filter yang kita gunakan yakni `ip.dst == 184.87.193.88`.

![filter](src/no7/filter.jpg)

Dari filter tersebut dapat kita lihat pada bagian kanan bawah yang menunjukkan jumlah paket yang menuju IP 184.87.193.88, yaitu berjumlah 6.

![packet](src/no7/packet.jpg)

Setelah itu dapat kita coba submit jawaban ke terminal.

![hasil](src/no7/hasil.jpg)

Seperti yang dilihat, kita mendapatkan jawaban benar dan mendapatkan flag.


## No. 8
Soal : 

`Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)`

Untuk soal ini kita cukup membaca referensi pada modul https://github.com/arsitektur-jaringan-komputer/Modul-Jarkom/tree/master/Modul-1. Dikarenakan diminta kueri filter menuju port 80, terdapat dua port yang perlu kita tulis yaitu tcp dan udp. Sehingga didapatkan queri berupa `tcp.dstport == 80 || udp.dstport == 80`.

Hasil setelah mengsubmit jawaban ke terminal adalah sebagai berikut.

![hasil](src/no8/hasil.jpg)



## No. 9
Soal : 

`Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!`

Sama seperti no 8, kita bisa membaca modul untuk mencari tahu cara untuk melakukan filter sesuai permintaan soal, yakni `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`. Pada soal ini kita berfokus untuk memanipulasi relational operator untuk mendapatkan jawaban yang diinginkan.

Hasil submit jawaban ke terminal adalah sebagai berikut. 

![hasil](src/no9/hasil.jpg)



## No. 10
Soal : 

`Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet`

Untuk soal ini saya menggunakan referensi youtube `https://youtu.be/GY_0TeV8Juw?si=pheIKm1YrbCypZ4L` sebagai panduan dalam mengerjakan soal ini. Dikarenakan kita ingin mencari kredensial user yang mencoba login menggunakan telnet. Kita dapat mencoba melakukan filter dengan kueri `tcp contains "Password". 

![filter](src/no10/filter.jpg)

Setelah itu kita dapat melakukan follow stream seperti berikut.

![follow](src/no10/follow.jpg)

Setelah melakukan follow, kita akan mendapatkan hasil seperti ini.

![kredensial](src/no10/kredensial.jpg)

Dari hasil tersebut kita mendapatkan username berupa `dhafin` (username tidak berupa ddhhaaffiin karena berdasarkan youtube tersebut ketika melakukan login, nama username akan agak menjadi double seperti itu). Kita juga berhasil mendapatkan password berupa `kesayangannyak0k0`. Kita dapat mencoba mengsubmit jawaban ke terminal setelah menemukan username dan password tersebut.

![hasil](src/no10/hasil.jpg)

Bisa dilihat kita berhasil mendapatkan flag setelah mengsubmit jawaban tersebut.









