<h1>Tugas Individu Flutter</h1>

<hr>
Nama    : Alwan Takahashi Aditama <br>
NPM     : 2206828853 <br>
Kelas   : PBP E <br>

### Hyperlink:
- [Tugas 7](https://github.com/Ajiens/MyStore#Tugas7)
- [Tugas 8](https://github.com/Ajiens/MyStore#Tugas8)

<hr>

### Tugas8
1. **Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!** <br>
    - **Navigator.push()**, adalah method yang menambahkan route kedalam stack yang dikelola oleh Navigator.
        Jadi ketika kita ingin menampilkan suatu halaman tertentu, kita dapat menggunakan method ini dengan cara
        menumpuk/menimpa halaman baru diatas halaman sebelumnya. Sehingga ketika kita menekan tombol back pada device kita
        halaman yang sebelumnya ditimpa dengan halaman baru akan muncul. Contoh pengaplikasian yang tepat ketika menggunakan
        method ini adalah ketika user perlu melakukan serangkaian proses yang diwajibkan secara berurut namun memerlukan halaman 
        halaman yang berbeda. Jadi user dapat kembali kehalaman sebelumnya tanpa harus takut kehilangan proses yang dilaluinya 
        ketika melanjutkan ke halaman selanjutnya.
    - **Navigator.pushReplacement** adalah method yang menggantikan route saat ini ketika ingin mengakses route baru yang ingin dituju.
        Jadi ketika ingin beralih dari halaman A ke halaman B, halaman A akan dihapus dan digantikan oleh halaman B. Contoh pengaplikasian
        yang tepat ketika menggunakan method ini adalah ketika user menekan tombol navigasi ke halaman utama yang sebelumnya berada di halaman lain.
        Jadi ketika user menekan tombol _back_ pada halaman utama padahal sebelumnya mengakses halaman lain, pengguna akan langsung keluar dari 
        aplikasi tanpa harus melewati halaman lain yang sebelumnya pernah diakses.
   
2. **Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!**
    - **Container** adalah widget serbaguna yang dapat menampung widget-widget lain didalam _layout_ ini.
    - **Row dan Column** adalah widget layout yang berfungsi untuk meletakan widget lain secara horizontal (row) atau vertikal (column).
    - **Expanded and Flexible** adalah widget layout yang digunakan untuk mengkombinasikan antara row dan column
    - **GridView** adalah widget layout yang berfungsi untuk menempatkan widget dengan susunan layaknya pada tabel/grid.

3. **Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!**
    Saat ini saya menggunakan widget TextFormField untuk menampung input dari user. Input-input user yang saya minta antara lain: nama untuk nama suatu produk,
    _price_ untuk harga dari suatu produk, dan _description_ untuk deskripsi dari produk tersebut. Mungkin saja kedepannya saya akan memakai widget lain
    untuk melengkapi formulir yang saya butuhkan dari user. Widget lain yang mungkin akan ditambahkan ada widget ```DropdownButton```, ```Checkbox```, atau ```Radio```.
4. **Bagaimana penerapan clean architecture pada aplikasi Flutter?**
    Clean Architecture pada flutter ditunjunkan untuk memisahkan kode-kode berdasarkan tiap lapisan/halaman yang mempunyai fungsi yang berbeda.
    Flutter mempunyai lapisan utama didalamnya, sehingga kita dapat membagi lapisan tersebut berdasarkan fungsinya masing-masing:
    - **Feature Layer**, lapisan yang berisikan tentang tampilan UI beserta _event handler_nya. Sehingga pada lapisan ini hanya berisikan _interface_ yang ingin 
        ditampilkan kepada user dan tidak boleh berisikan proses logika.
    - **Domain Layer**, lapisan yang berisikan inti dari proses aplikasi tersebut, dimana terdapat logika, objek, dan kontrak repositori tanpa
        tanpa ada campuran _user interface_.
    - **Data Layer**, lapisan yang berisikan implementasi repositori, pemanggilan API jika diperlukan, dan proses pengaksesan data pada database. 
   model di feature dan data layer menunjukkan representasi yang spesifik untuk keperluan antarmuka pengguna atau manipulasi data.

5. **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)**/
<dl>
    <dt><b>Membuat satu halaman formulir yang berfungsi untuk menambahkan item baru dengan beberapa ketentuan</b>
    </dt>
        <dd>
            <p>Pertama yang dilakukan adalah membuat file baru sebagai bentuk halaman baru pada aplikasi. Pada file tersebut dibuat constractor untuk membuat halaman form dengan melakukan override widget build. Didalam widget build tersebut dibuat ```Scaffold()``` sebagai wadah dari halaman tersebut. Scaffold ini dapat berisikan title, body, action-listener, drawer dll. </p>
            <p>Pada bagian body diisikan variabel sebagai tempat menampung input form. Pada bagian ini juga berisikan child yang menampung widget lain yang diatur dengan menggunakan layout ```Column()```. Dalam layout tersebut juga diisikan TextFormField sebagai widget yang berfungsi tempat input user. Masing-masing widget TextFormField akan divalidasi input nya, seperti isian tidak boleh kosong atau harus berupa integer. Berikut salah satu contoh untuk memvalidasi input dari user:</p>
            <span>
            ```
            validator: (String? value) {
            if (value == null || value.isEmpty) {
                return "Harga tidak boleh kosong!";
            }
            if (int.tryParse(value) == null) {
                return "Harga harus berupa angka!";
            }
            }
            ```
            </span>
            <p>Setelah itu, membuat button yang berfungsi untuk menyimpan input dari user. Pada button ini akan memvalidasi _formkey yang sebelumnya didefinisikan. </p>
        </dd>
    <dt><b>Mengarahkan pengguna ke halaman form tambah item baru ketika menekan tombol Tambah Item pada halaman utama.</b></dt>
    <dd>
        <p>Untuk mengarahkan pengguna ke halama form ketika menekan tombol Tambah Item saya menggunakan Navigator.push, pengimplmentasiannya: ```Navigator.push(context, MaterialPageRoute(builder: (context) => const ShopFormPage()));```. Dengan menggunakan navigator ini, halaman yang ingin user akses akan tampil dan ketika tombol back di eksekusi pada device pengguna, pengguna akan kembali ke halaman tempat dimana ia memencet tombol Tambah Item.</p>
    </dd>
    <dt><b>Memunculkan data sesuai isi dari formulir yang diisi dalam sebuah pop-up setelah menekan tombol Save pada halaman formulir tambah item baru. </b></dt>
    <dd> 
        <p>Untuk menambahkan pop-up card ketika tombol save dan input field tervalidasi, kita dapat menambahkan ```showDialog()``` pada bagian ```onPressed()```, sehingga ketika button tersebut dipencet dan input form tervalidasi, maka pop-up card dapat muncul dan memunculkan data-data dari input form yang dimasukan dengan cara memanggil variabel penampung yang didefinisikan sebelumnya.</p>
    </dd>
    <dt><b>Membuat sebuah drawer pada aplikasi dengan ketentuan</b></dt>
    <dd><p>Untuk membuat sebuah drawe pada aplikasi kita, kita dapat membuat berkas file baru dan membuat class yang bernama LeftDrawer yang mengextends StatelessWidget. StatelessWidget digunakan karena ketika load halaman ini, kita tidak memerlukan data dan widget bersifat statis.</p>
    <p>Setelah itu, widget build di lakukan override untuk membentuk widget yang kita inginkan. Kita menggunakan Layout ListView untuk menyusun tiap-tiap widget didalamnya. Setelah itu kita dapat menambahkan widget yang dibutukan. Lalu tiap widget-widget tersebut ditambahkan actionlistener yang melakukan routing ke halaman lain yang bersesuaian</p>
    </dd>

</dl>



<hr>

### Tugas7
* **Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?** <br>
   Perbedaan utama antara statless dan stateful terletak bagaiamana sebuah/sebagian widget ditampilkan di layar
layar pengguna. Untuk me-_load__ widget yang bersifat **Stateful** membutuhkan data untuk menentukan _widget_ yang
seperti apa ingin ditampilkan. _Widget stateful_ juga dapat dirubah tergantung bagaimana data/kondisi yang ditampilkan.
Sedangkan _widget **stateless**_ adalah widget yang ditampilkan tanpa bergantung dengan bagaimana data/kondisi saat ini.
Sehingga konsekuensinya _widget stateless_ tidak dapat diubah secara langsung.
* **Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing!** <br>
   - _Icons_ adalah sebuah _widget_ yang berfungsi untuk menampilkan icon, seperti _shopping_cart, shopping bag_, dll.
   - _Text_ adalah sebuah _widget_ yang berfungsi untuk menampilkan teks atau label.
   - _Color_ adalah sebuah _widget_ yang berfungsi untuk memberi warna.
   - _Card_ adalah sebuah _widget_ yang fungsinya untuk membungkus/_wrapping_ elemen-elemen tertentu.
   - _Padding_ berfungsi untuk memberikan jarak/_gap_ antara elemen dan kontainernya
* **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)** <br>
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
