# MAGIC METHOD

Magic methods adalah metode khusus yang menggantikan perilaku default PHP ketika beberapa aksi dilakukan pada objek. Misalnya, ketika kita membuat objek baru, metode __construct () akan dipanggil secara otomatis. Magic methods menggunakan awalan __ (double underscore) diikuti nama metodenya. Beberapa contoh magic methods adalah:

- __get (): metode ini dipanggil ketika kita mencoba mendapatkan data dari properti yang tidak dapat diakses atau tidak ada pada objek. Biasanya digunakan untuk mendapatkan data tambahan objek yang tidak didefinisikan secara eksplisit sebagai properti.
- __set (): metode ini dipanggil ketika kita mencoba menetapkan data ke properti yang tidak dapat diakses atau tidak ada pada objek. Biasanya digunakan untuk menetapkan data tambahan objek yang tidak didefinisikan secara eksplisit sebagai properti.


- __construct (): metode ini dipanggil ketika objek dibuat. Biasanya digunakan untuk menetapkan nilai awal untuk properti objek.
- __destruct (): metode ini dipanggil ketika objek dihancurkan. Biasanya digunakan untuk melakukan pembersihan atau penyimpanan data objek.
- __call (): metode ini dipanggil ketika kita mencoba memanggil metode yang tidak dapat diakses atau tidak ada pada objek. Biasanya digunakan untuk menangani panggilan metode yang tidak valid atau dinamis.
- __callStatic (): metode ini dipanggil ketika kita mencoba memanggil metode statis yang tidak dapat diakses atau tidak ada pada kelas. Biasanya digunakan untuk menangani panggilan metode statis yang tidak valid atau dinamis.

- __isset (): metode ini dipanggil ketika kita menggunakan fungsi isset () pada properti yang tidak dapat diakses atau tidak ada pada objek. Biasanya digunakan untuk memeriksa apakah data tambahan objek telah ditetapkan atau tidak.
- __unset (): metode ini dipanggil ketika kita menggunakan fungsi unset () pada properti yang tidak dapat diakses atau tidak ada pada objek. Biasanya digunakan untuk menghapus data tambahan objek.
- __sleep (): metode ini dipanggil ketika kita menggunakan fungsi serialize () pada objek. Biasanya digunakan untuk melakukan persiapan sebelum serialisasi, seperti membersihkan objek atau mengembalikan array dengan nama variabel yang harus diserialisasi.
- __wakeup (): metode ini dipanggil ketika kita menggunakan fungsi unserialize () pada objek. Biasanya digunakan untuk melakukan inisialisasi setelah deserialisasi, seperti menghubungkan kembali sumber daya atau melakukan tugas lainnya.
- __toString (): metode ini dipanggil ketika kita mencoba mengubah objek menjadi string, misalnya dengan menggunakan fungsi echo () atau print (). Biasanya digunakan untuk mengembalikan representasi string dari objek.
- __invoke (): metode ini dipanggil ketika kita mencoba memperlakukan objek sebagai fungsi, misalnya dengan menggunakan tanda kurung (). Biasanya digunakan untuk membuat objek dapat dipanggil seperti fungsi.
- __set_state (): metode ini dipanggil ketika kita menggunakan fungsi var_export () pada objek. Biasanya digunakan untuk mengembalikan array dengan nilai-nilai properti yang dapat digunakan untuk membuat kembali objek.
- __clone (): metode ini dipanggil ketika kita menggunakan kata kunci clone pada objek. Biasanya digunakan untuk melakukan duplikasi atau modifikasi pada objek yang dikloning.
- __debugInfo (): metode ini dipanggil ketika kita menggunakan fungsi var_dump () pada objek. Biasanya digunakan untuk mengembalikan array dengan informasi debug tentang objek.

Berikut adalah contoh kode yang menggunakan beberapa magic methods:

```php
<?php
class Mahasiswa {
  private $nama;
  private $nim;
  private $data = [];

  public function __construct($nama, $nim) {
    $this->nama = $nama;
    $this->nim = $nim;
  }

  public function __get($properti) {
    if (array_key_exists($properti, $this->data)) {
      return $this->data[$properti];
    } else {
      return "Properti $properti tidak ada";
    }
  }

  public function __set($properti, $nilai) {
    $this->data[$properti] = $nilai;
  }

  public function __toString() {
    return "Nama: $this->nama, NIM: $this->nim";
  }

  public function __invoke($pesan) {
    echo "Anda memanggil objek dengan pesan: $pesan";
  }
}

$mhs = new Mahasiswa("Budi", "123456");
echo $mhs; // Nama: Budi, NIM: 123456
echo "\n";
$mhs("Halo"); // Anda memanggil objek dengan pesan: Halo
echo "\n";
$mhs->jurusan = "Teknik Informatika"; // menggunakan __set
echo $mhs->jurusan; // Teknik Informatika, menggunakan __get
echo "\n";
echo $mhs->alamat; // Properti alamat tidak ada, menggunakan __get
?>
```
## PHP __set 
metode ini dipanggil ketika kita mencoba menetapkan data ke properti yang tidak dapat diakses atau tidak ada pada objek. Biasanya digunakan untuk menetapkan data tambahan objek yang tidak didefinisikan secara eksplisit sebagai properti.

