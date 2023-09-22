![image](https://github.com/xmall75/Jarkom-Modul-1-D28-2023/assets/115076652/dcaee7fb-6067-4461-822c-32b5170f2302)# Jarkom-Modul-1-D28-2023


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
