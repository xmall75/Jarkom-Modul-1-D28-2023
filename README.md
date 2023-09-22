# Jarkom-Modul-1-D28-2023


## No. 6
Soal : 

`Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.`

Dari soal di atas kita pertama-tama dapat menganalisa soal terlebih dahulu. Berdasarkan pengamatan, huruf kapital pada paragraf tidaklah mengikuti standar KBBI. Sehingga jika kita mengambil seluruh huruf kapitalnya akan termuncul sebuah kata `SUBSTITUSI`. Setelah itu terdapat hint `server SOURCE ADDRESS 7812 is invalid` dan `a1 e5 u21`. Mari kita selesaikan satu per satu.

Untuk `server SOURCE ADDRESS 7812 is invalid` dapat kita gunakan wireshark untuk mencari packet ke 7812 dari file PCAP yang diberikan. Setelah itu kita dapat mengambil source address packet tersebut yakni, `104.18.14.101`.

![[src/No. 6/Go to.jpg]]

Kemudian ada hint tadi `SUBSTITUSI` dan `a1 e5 u21`. Ini berarti kita diminta untuk mensubstitusikan source address yang sudah kita dapat dengan metode cipher a1z26. Kita dapat menggunakan website online untuk cipher tersebut, salah satunya seperti website https://planetcalc.com/4884/ yang saya gunakan untuk melakukan substitusi tersebut. 

Jika kita langsung melakukan cipher tanpa mengubah apa-apa akan didapatkan hasil sebagai berikut.

Tetapi karena dari hint diberitahukan bahwa yang di cipher adalah angka 1-18. Kita dapat mencoba untuk memisah source address hingga memenuhi parameter tersebut. Hasilnya adalah sebagai berikut. 


Sekarang dapat kita coba masukkan jawaban di terminal. 

Seperti yang dilihat, jawaban benar dan kita berhasil mendapatkan flag.
