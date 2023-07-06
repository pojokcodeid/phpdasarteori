
# STATIC METHOD DAN PROPERTYES

Static method dan static properties adalah method dan properties yang dapat diakses langsung dari class tanpa perlu membuat objek dari class tersebut. Mereka dideklarasikan dengan kata kunci **static** dan dapat digunakan dalam konteks class daripada objek. Static method dan properties berguna untuk berbagi data dan fungsi yang umum antara fungsi dan objek yang berbeda dalam program.

Contoh static method:

```php
class Foo {
    public static function aStaticMethod() {
        // ...
    }
}

Foo::aStaticMethod(); // memanggil static method tanpa membuat objek
$classname = 'Foo';
$classname::aStaticMethod(); // memanggil static method dengan nama class dalam variabel
```

Contoh static properties:

```php
class Foo {
    public static $my_static = 'foo'; // mendeklarasikan static properties
}

echo Foo::$my_static; // mengakses static properties tanpa membuat objek
$foo = new Foo();
echo $foo::$my_static; // mengakses static properties dengan objek
```

# CLASS CONSTRAINT

Class constants adalah konstanta yang didefinisikan dalam class dan tetap sama dan tidak dapat diubah. Mereka dideklarasikan dengan kata kunci **const** dan memiliki visibility default **public**. Class constants dapat diakses dari luar class dengan menggunakan nama class, operator resolusi scope (::), dan nama konstanta¹².

Contoh class constants:

```php
class MyClass {
    const CONSTANT = 'nilai konstan'; // mendeklarasikan class constant
}

echo MyClass::CONSTANT; // mengakses class constant dari luar class
```
# Late Static Binding

Late Static Binding adalah fitur PHP yang dapat digunakan untuk mereferensikan class yang dipanggil dalam konteks pewarisan statis. Secara lebih tepat, Late Static Binding bekerja dengan menyimpan nama class dalam panggilan \"non-forwarding\" terakhir. Dalam kasus panggilan method statis, ini adalah class yang secara eksplisit dinamakan (biasanya yang di sebelah kiri operator ::); dalam kasus panggilan method non-statis, ini adalah class dari objek. Sebuah panggilan \"forwarding\" adalah panggilan statis yang diperkenalkan oleh self::, parent::, static::, atau, jika naik dalam hierarki class, forward_static_call()¹².

Late Static Binding mencoba menyelesaikan keterbatasan dari self:: yang selalu menyelesaikan ke class di mana fungsi itu berada, seperti di mana ia didefinisikan. Dengan menggunakan static::, kita dapat menyelesaikan ke class yang dipanggil pada saat runtime³⁴.

Contoh Late Static Binding:

```php
class A {
    public static function who() {
        echo __CLASS__;
    }
    public static function test() {
        self::who(); // selalu menyelesaikan ke A
        static::who(); // menyelesaikan ke class yang dipanggil
    }
}

class B extends A {
    public static function who() {
        echo __CLASS__;
    }
}

B::test(); // output: AB
```
