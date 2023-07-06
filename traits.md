
# TRAITS

Trait di PHP adalah mekanisme untuk menggunakan kembali kode dalam bahasa yang hanya mendukung pewarisan tunggal, seperti PHP. Trait dimaksudkan untuk mengurangi beberapa keterbatasan pewarisan tunggal dengan memungkinkan pengembang untuk menggunakan kembali sekumpulan metode secara bebas di beberapa kelas yang independen dan hidup di hierarki kelas yang berbeda.

Trait mirip dengan kelas, tetapi hanya dimaksudkan untuk mengelompokkan fungsionalitas secara halus dan konsisten. Tidak mungkin untuk membuat instance dari Trait sendiri. Trait adalah tambahan untuk pewarisan tradisional dan memungkinkan komposisi horizontal perilaku; yaitu, penerapan anggota kelas tanpa memerlukan pewarisan¹.

Untuk menggunakan Trait dalam kelas, gunakan kata kunci `use`. Contoh:

```php
<?php
trait message1 {
  public function msg1 () {
    echo "OOP is fun! ";
  }
}

class Welcome {
  use message1;
}

$obj = new Welcome ();
$obj->msg1 ();
?>
```

Output:

```
OOP is fun!
```

Dalam contoh ini, kita mendeklarasikan satu trait: `message1`. Kemudian, kita membuat satu kelas: `Welcome`. Kelas ini menggunakan trait, dan semua metode dalam trait akan tersedia dalam kelas.

Kita juga bisa menggunakan beberapa trait dalam satu kelas dengan memisahkannya dengan koma. Contoh:

```php
<?php
trait message1 {
  public function msg1 () {
    echo "OOP is fun! ";
  }
}

trait message2 {
  public function msg2 () {
    echo "OOP reduces code duplication!";
  }
}

class Welcome {
  use message1, message2;
}

$obj = new Welcome ();
$obj->msg1 ();
$obj->msg2 ();
?>
```

Output:

```
OOP is fun! OOP reduces code duplication!
```

Dalam contoh ini, kita mendeklarasikan dua trait: `message1` dan `message2`. Kemudian, kita membuat satu kelas: `Welcome`. Kelas ini menggunakan kedua trait, dan semua metode dalam kedua trait akan tersedia dalam kelas.

Trait bisa berguna untuk mengimplementasikan fungsionalitas umum yang bisa dibagi antara beberapa kelas, seperti logging, keamanan, caching, dll. Trait juga bisa membantu menghindari duplikasi kode, karena tidak perlu mendeklarasikan ulang metode yang sama berulang kali.
