# advprog-modul11

1. Sebelum aplikasi di-expose sebagai Service, log aplikasi hanya berisi 2 baris, yaitu Started HTTP server dan Started UDP server. Setelah diexpose ke service dan servicenya dipanggil (muncul tab browser baru), log aplikasi bertambah. Terdapat dua baris baru, dua-duanya GET. Jika saya memanggil IP addressnya lagi, maka muncul dua baris lagi. Jadi, berdasarkan pengamatan saya, baris pada logs bertambah dua setiap kali melakukan pembanggila IP address. Service

2. Option -n digunakan untuk menentukan namespace di mana pods dan service pada namespace tersebut akan ditampilkan. Tanpa menggunakan -n, namespace yang digunakan adalah default namespace. Sementara jika menggunakan -n kube-system, akan ditampilkan semua pods dan services di namespace kube-system, yaitu service dari sistem Kubernetes itu sendiri. Oleh karena itu, service yang kita buat sendiri tidak akan ditampilkan, karena bukan bagian dari namepsace kube-system.

3. 
