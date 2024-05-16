# advprog-modul11

1. Sebelum aplikasi di-expose sebagai Service, log aplikasi hanya berisi 2 baris, yaitu Started HTTP server dan Started UDP server. Setelah diexpose ke service dan servicenya dipanggil (muncul tab browser baru), log aplikasi bertambah. Terdapat dua baris baru, dua-duanya GET. Jika saya memanggil IP addressnya lagi, maka muncul dua baris lagi. Jadi, berdasarkan pengamatan saya, baris pada logs bertambah dua setiap kali melakukan pembanggilan IP address. Saya memanggil IP address sebanyak 4 kali, maka muncul 8 baris baru pada logs.

2. Option -n digunakan untuk menentukan namespace di mana pods dan service pada namespace tersebut akan ditampilkan. Tanpa menggunakan -n, namespace yang digunakan adalah default namespace. Biasanya defaul namespace adalah 'default'. Sementara jika menggunakan -n kube-system, akan ditampilkan semua pods dan services di namespace kube-system. Namespace kube-system berisi service dari sistem Kubernetes itu sendiri. Oleh karena itu, service yang kita buat sendiri tidak akan ditampilkan, karena bukan bagian dari namepsace kube-system.




1. Rolling Update: Metode mengupdate Deployment yamg memiliki beberapa pod. Metode ini memastikan tetap ada satu node yang berjalan sehingga aplikasi tidak pernah down. Sementara itu, update dilakukan secara satu per satu untuk semua pod yang ada. Recreate adalah metode updatae di mana semua pods diupdate pada waktu yang sama. Hal ini berarti akan ada momen di mana aplikasi down, sambil menunggu update deployment yang baru. Rolling Update cocok untuk aplikasi yang harus tetap running saat di-update. Recreate cocok untuk aplikasi yang perlu update secara cepat dan sederhana dan dapat mentolernasi downtime.
2. 


