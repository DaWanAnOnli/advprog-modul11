# advprog-modul11

## Reflection 1

1. Sebelum aplikasi di-expose sebagai Service, log aplikasi hanya berisi 2 baris, yaitu Started HTTP server dan Started UDP server. Setelah diexpose ke service dan servicenya dipanggil (muncul tab browser baru), log aplikasi bertambah. Terdapat dua baris baru, dua-duanya GET. Jika saya memanggil IP addressnya lagi, maka muncul dua baris lagi. Jadi, berdasarkan pengamatan saya, baris pada logs bertambah dua setiap kali melakukan pembanggilan IP address. Saya memanggil IP address sebanyak 4 kali, maka muncul 8 baris baru pada logs.

2. Option -n digunakan untuk menentukan namespace di mana pods dan service pada namespace tersebut akan ditampilkan. Tanpa menggunakan -n, namespace yang digunakan adalah default namespace. Biasanya defaul namespace adalah 'default'. Sementara jika menggunakan -n kube-system, akan ditampilkan semua pods dan services di namespace kube-system. Namespace kube-system berisi service dari sistem Kubernetes itu sendiri. Oleh karena itu, service yang kita buat sendiri tidak akan ditampilkan, karena bukan bagian dari namepsace kube-system.


## Reflection 2

1. Rolling Update: Metode mengupdate Deployment yamg memiliki beberapa pod. Metode ini memastikan tetap ada satu node yang berjalan sehingga aplikasi tidak pernah down. Sementara itu, update dilakukan secara satu per satu untuk semua pod yang ada. Recreate adalah metode updatae di mana semua pods diupdate pada waktu yang sama. Hal ini berarti akan ada momen di mana aplikasi down, sambil menunggu update deployment yang baru. Rolling Update cocok untuk aplikasi yang harus tetap running saat di-update. Recreate cocok untuk aplikasi yang perlu update secara cepat dan sederhana dan dapat mentolernasi downtime.
2. Pertama, saya membuat file manifest baru dengan menjalankan:
   
   ```
   kubectl get deployment spring-petclinic-rest -o yaml > deployment-recreate.yaml
   ```
   
   Lalu, saya mengubah isi file deployment-recreate.yaml pada bagian strategy menjadi:
![image](https://github.com/DaWanAnOnli/advprog-modul11/assets/124868777/a0368bd8-0cbf-4104-8569-f13ea6ec54c6)

Setelah itu saya apply dengan menggunakan command:

'''
kubectl apply -f deployment-recreate.yaml
'''

Lalu saya menjalankan ```kubectl get pods --watch``` untuk memantau pods secara realtime. Didapat hasil sebagai berikut:
![image](https://github.com/DaWanAnOnli/advprog-modul11/assets/124868777/188b396c-6eba-47a2-9a81-37727b014b00)

Dapat dilihat ada satu periode di mana semua semua di-terminate, pods mati (downtime), lalu pods yang baru dicreate, lalu running lagi.

3. Langkahnya mirip dengan langkah 2, saya menjalankan command:
```
   kubectl get deployment spring-petclinic-rest -o yaml > deployment-recreate.yaml
```
Lalu akan muncul file deployment-recreate.yaml yang terbaru.


4. Menurut saya deploy menggunakan manifest files jauh lebih mudah. Jika harus dilakukan secara manual (menggunakan command-command kubectl), tentunya akan lebih kompleks. Hal ini karena kita sulit keep track sudah ada di proses atau status mana, harus menghafal step-stepnya, dan sangat prone terhadap kesalahan input. Dengan manifest files, semua settings kita ada di satu tempat dan mudah di edit. Jika perlu perubahan kecil pada deployment secara manual, semua command harus di run dari awal lagi. Namun menggunakan manifest files, yang perlu diubah hanya baris-baris yang diperlukan saja.
