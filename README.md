<h1>Tugas Individu Flutter</h1>

### Hyperlink:
- [Tugas7](https://github.com/Ajiens/MyStore#Tugas7)

<hr>

### Tugas7
* **Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?** <br>
   Perbedaan utama antara statless dan stateful terletak bagaiamana sebuah/sebagian widget ditampilkan di layar
layar pengguna. Untuk me-_load__ widget yang bersifat **Stateful** membutuhkan data untuk menentukan _widget_ yang
seperti apa ingin ditampilkan. _Widget stateful_ juga dapat dirubah tergantung bagaimana data/kondisi yang ditampilkan.
Sedangkan _widget **stateless**_ adalah widget yang ditampilkan tanpa bergantung dengan bagaimana data/kondisi saat ini.
Sehingga konsekuensinya _widget stateless_ tidak dapat diubah secara langsung. 
<br>
* **Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing!**
   - _Icons_ adalah sebuah _widget_ yang berfungsi untuk menampilkan icon, seperti _shopping_cart, shopping bag_, dll.
   - _Text_ adalah sebuah _widget_ yang berfungsi untuk menampilkan teks atau label.
   - _Color_ adalah sebuah _widget_ yang berfungsi untuk memberi warna.
   - _Card_ adalah sebuah _widget_ yang fungsinya untuk membungkus/_wrapping_ elemen-elemen tertentu.
   - _Padding_ berfungsi untuk memberikan jarak/_gap_ antara elemen dan kontainernya
<br>
* **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)**
   - Membuat sebuah program Flutter baru dengan tema inventory seperti tugas-tugas sebelumnya. <br>
      Untuk membuat program Flutter baru, dapat dilakukan dengan ```flutter create my_store```. Dari perintah tersebut maka secara otomatis
      membuat _project_ Flutter baru dengan nama my_store.
   - Membuat tiga tombol sederhana dengan ikon dan teks. <br>
      Perama yang dapat dilakukana adalah dengan mendfinisikan objek yang ingin kita buat. Untuk membuat sebuah objek baru yang diinginkan
      kita dapat membuat sebuah class baru. Saya membuat class baru tersebut dengan nama ShopItem dengan atribut ikon, teks, dan warna. Setelah itu mendefinisikan _constructor_
      pada class tersebut untuk dapat membuat objek baru dari kelas ShopItem. Setelah 4 objek baru yang sudah saya bentuk, keempat objek tersebut
      diiterasi untuk ditampilkan. Sebelum ditampilkan sebagai _user interface_, objek tersebut terlebih dahulu dibungkus dengan class baru yang
      bernama ShopCard. ShopCard ini menggunakan _Card widget_ untuk membungkusnya. Selain itu, didalam class ShopCard diberi perintah dengan
      menggunakan ```onTap()```. Hal tersebut ditunjukan agar card yang didefinisikan dapat berperan selayaknya sebuah _button_.
   - Memunculkan Snackbar dengan teks sesuai tombolnya.
      Untuk dapat memunculkan teks ketika tombol dipencet, kita dapat menggunakan ```onTap()``` yang akan berperan sebagai _action listener_ ketika tombol dipencet.
      Agar _snackbar_ dapat muncul ketika tombol dipencet, kita dapat mendefinisikan snackbar didalam onTap(), yaitu dapat digunakan dengan cara:
      ```SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))```.
   