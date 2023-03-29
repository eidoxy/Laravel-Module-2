###### Nama     : Adrian
###### Kelas    : RPL-1
###### No Absen : 08

# Modul 3
## Routing

**Pada Modul 3 ini, kita akan belajar mengenal konsep routing, mengetahui jenis jenis route, dan cara membuat route.**

>Routing pada Laravel merupakan cara mengakses suatu halaman pada aplikasi melalui URL.
Misalnya untuk membuka halaman awal aplikasi dapat dilakukan dengan mengetik URL
localhost:8000. Berarti dalam menentukan route, kita menentukan bagaimana struktur URL untuk
mengakses halaman tertentu. File yang digunakan untuk melakukan penyetingan route terdapat pada
folder routes. Pada folder ini terdapat empat file php untuk pembuatan aplikasi, file yang digunakan
untuk pembuatan route adalah web.php.

>Ada berbagai method dalam route yang dapat digunakan sesuai dengan HTTP request. Pada
contoh berikut ada beberapa contoh route yang menggunakan route method:
>1. Untuk menampilkan atau mengambil data dapat menggunakan method GET. Route dengan
method ini dapat langsung kita akses melalui link pada browser. Contohnya dapat dilihat pada
latihan dibawah:

```
Route::get('/index', function(){
        echo "Uji coba route dengan method GET"
    })
```

>2. Untuk mengirim data dari form dengan dapat menggunakan method POST, biasasnya
digunakan untuk menambah data. Adapun penulisan dari route ini adalah sebagai berikut:

```
Route::post(‘/store’, fucntion() {
        // sintak untuk menyimpan data
    })
```

>3. Untuk mengirim data dari form dengan tujuan untuk memperbaharui data dapat menggunakan
method PUT, contoh penulisan route dengan method PUT adalah sebagai berikut:

```
Route::put(‘/update’, fucntion() {
        // sintak untuk update data
      })
```

>4. Untuk mengirim data dari form dengen tujuan untuk menghapus data dapat menggunakan
method DELETE. Contoh dari penulisan route dengen method delete adalah sebagai berikut:

```
Route::delete(‘/delete’, fucntion() {
        // sintak untuk menghapus data
    })
```

>5. Untuk route yang dapat merespons beberapa HTTP request, kita dapat menggunakan method
match().

```
Route::match([‘get’, ‘post’], ‘/welcome’ fucntion() {
        //
    })
```

>6. Sedangkan untuk route yang dapat merespons semua HTTP request, dapat menggunakan
method any(). Contohnya pada script berikut:

```
Route::any(‘/welcome’, fucntion() {
      //
    })
```

Setelah kalian mengenal apa itu router dan jenis jenis router, selanjutnya kita akan membuat router sederhana. Untuk membuat router pada server kalian harus mengaktifkan server laravel serta web server kalian, disini saya menggunakan web server XAMPP.

![image](https://user-images.githubusercontent.com/79520394/182096364-90f02f48-1d82-4fcc-8bf6-beda8c023342.png)

Dan untuk mengaktifkan server laravel kalian ketik code berikut ke terminal/cmd, tapi sebelumnya kalian harus pergi ke folder project penjualan (nama project laravelnya) :

```
php artisan serve
```

Maka terminal akan menampilkan tampilan berikut.

![image](https://user-images.githubusercontent.com/79520394/182097526-f65fefb0-b60a-4a84-be0b-852ea85c33ba.png)

Dan setelah kalian mengaktifkan web server dan server artisan Laravelnya, selanjutnya kalian pergi ke folder penjualan - routes - web.php.

![image](https://user-images.githubusercontent.com/79520394/182098029-646cbbe4-7974-4ef4-9168-207ecc81ad29.png)

Di file web.php kalian ketikan code berikut :

```
<?php

use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    echo "Hello World";
});
```

Untuk melihat web.php nya kalian bisa ketikan ID berikut pada browser : 127.0.0.1:8000 , kalian bisa melihat link urlnya pada foto saat kalian mengetikkan PHP artisan serve.

![image](https://user-images.githubusercontent.com/79520394/182096364-90f02f48-1d82-4fcc-8bf6-beda8c023342.png)

Berikut tampilan web.php :

![image](https://user-images.githubusercontent.com/79520394/182103450-5de40a67-1759-4abb-ab51-b8f79cd22a97.png)


# Tugas
Pada tugas modul 3 kali ini saya akan membuat route yang menuju ke kategori dan akan menuju lagi ke halaman tambah data kategori menggunakan route controller.

Pertama kalian buat buat controllernya dengan mengetikkan :

```
php artisan make:controller KategoriController
```

Setelah kalian membuat controller baru, maka file yang akan kalian buat akan berada di app - Http - Controllers. Pada file KategoriController.php kalian ketik code berikut :

```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class KategoriController extends Controller
{
    Public function homeClass(){
        return "<a href='/kategori'> Menuju kategori </a>";
    }

    Public function kategoriClass(){
        return 'Ini adalah halaman Kategori <p><a href="/kategori/add"> Tambah kategori</a></p>';
    }

    Public function kategoriAddClass(){
        return 'Halaman add kategori <p><a href="/home"> Balik ke halaman utama</a>';
    }
}
```

Fungsi membuat controller tersebut adalah untuk membuat fungsi atau isi dari web php yang akan dibuat, setelah kalian mengetikkan code berikut kalian pergi ke web.php dan ketik code berikut :

```
<?php

use Illuminate\Support\Facades\Route;
use App\Http\Controllers\KategoriController;


Route::get('/home', [KategoriController::class, 'homeClass']);
Route::get('/kategori', [KategoriController::class, 'kategoriClass']);
Route::get('/kategori/add', [KategoriController::class, 'kategoriAddClass']);
```

Fungsi route::get adalah untuk membuat lokasi url yaitu "/" atau _slash_ pada router url, pada koma (,) selanjutnya terdapat array yang diapit dengan tanda "[]" yang berisi nama controller yang telah dibuat dan nama funtion di dalamnya. Untuk mengakses web diatas kalian ketikkan *localhost:8000/{id}* id yang dimaksud itu adalah nama yang berada di "/" atau _slash_, maka kita ketikkan url berikut localhost:8000/home.

Unuk hasil dari code diatas adalah seperti berikut :

![image](https://user-images.githubusercontent.com/79520394/182106223-f06571f1-f84c-4c72-b08c-9175e8dad106.png)

Kalian bisa pencet link pada text dan akan menuju *kategori* dan *kategori/add*.

![image](https://user-images.githubusercontent.com/79520394/182106223-f06571f1-f84c-4c72-b08c-9175e8dad106.png)
_Tampilan web /kategori_

![image](https://user-images.githubusercontent.com/79520394/182106604-b45b08e3-6fb6-4c9d-960d-e1069c513a0c.png)
_Tampilan web /kategori/add_
