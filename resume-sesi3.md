# Resume Materi Sesi 3

## Konstruktor dan Enkapsulasi pada Dart

Nama     : Aneka Lisda
NIM      : 25141013P
Class    : SI2KR

---

# 1. Pengertian Konstruktor

Konstruktor adalah fungsi khusus dalam sebuah class yang digunakan untuk membuat objek dan memberikan nilai awal pada atribut class.
Konstruktor akan dipanggil secara otomatis ketika objek dibuat.

## Jenis Konstruktor di Dart

### Default Constructor

Default constructor digunakan untuk membuat objek dengan memberikan nilai langsung pada atribut.

Contoh:

```dart
class Mahasiswa {
  String nama;
  int nim;

  Mahasiswa(this.nama, this.nim);
}
```

---

### Named Constructor

Named constructor adalah constructor yang memiliki nama tambahan sehingga satu class dapat memiliki lebih dari satu constructor.

Contoh:

```dart
Mahasiswa.dariMap(Map data)
    : nama = data['nama'],
      nim = data['nim'];
```

---

### Constructor dengan Nilai Default

Constructor ini digunakan untuk memberikan nilai awal jika data belum tersedia.

```dart
Mahasiswa.tanpaNama()
    : nama = "Tidak ada",
      nim = 0;
```

---

# 2. Pengertian Enkapsulasi

Enkapsulasi adalah konsep dalam Object Oriented Programming (OOP) yang digunakan untuk melindungi data dalam class agar tidak dapat diakses secara langsung dari luar class.

Dalam Dart, variabel private ditandai dengan tanda underscore `_`.

Contoh:

```dart
String _username;
```

---

# 3. Getter

Getter digunakan untuk mengambil atau membaca nilai dari variabel private.

Contoh:

```dart
String get username => _username;
```

---

# 4. Setter

Setter digunakan untuk mengubah nilai variabel private dengan aturan atau validasi tertentu.

Contoh validasi:

* Username minimal 5 karakter
* Password minimal 8 karakter
* Email harus mengandung simbol `@`

Contoh setter:

```dart
set username(String value) {
  if (value.length >= 5) {
    _username = value;
  }
}
```

---

# Jawaban Soal 1

## Membuat Multiple Constructor

```dart
class Mahasiswa {
  String nama;
  int nim;

  // Default constructor
  Mahasiswa(this.nama, this.nim);

  // Named constructor dariMap
  Mahasiswa.dariMap(Map data)
      : nama = data['nama'],
        nim = data['nim'];

  // Named constructor tanpaNama
  Mahasiswa.tanpaNama()
      : nama = "Tidak ada",
        nim = 0;
}

void main() {
  var m1 = Mahasiswa("Aneka Lisda", 25141013);
  var m2 = Mahasiswa.dariMap({"nama": "Adillia Fransiska", "nim": 25141014});
  var m3 = Mahasiswa.tanpaNama();

  print("Mahasiswa 1");
  print("-------------------");
  print("Nama: ${m1.nama}");
  print("NIM: ${m1.nim}");

  print("\nMahasiswa 2");
  print("-------------------");
  print("Nama: ${m2.nama}");
  print("NIM: ${m2.nim}");

  print("\nMahasiswa 3");
  print("-------------------");
  print("Nama: ${m3.nama}");
  print("NIM: ${m3.nim}");

}
```

---

# Jawaban Soal 2

## Membuat Class dengan Enkapsulasi

```dart
class User {
  String _username = "";
  String _password = "";
  String _email = "";

  // Getter
  String get username => _username;
  String get password => _password;
  String get email => _email;

  // Setter dengan validasi
  set username(String value) {
    if (value.length >= 5) {
      _username = value;
    } else {
      print("Username minimal 5 karakter");
    }
  }

  set password(String value) {
    if (value.length >= 8) {
      _password = value;
    } else {
      print("Password minimal 8 karakter");
    }
  }

  set email(String value) {
    if (value.contains("@")) {
      _email = value;
    } else {
      print("Email harus mengandung @");
    }
  }
}

void main() {
  User user = User();

  user.username = "anekalisda";
  user.password = "biarobaru321!";
  user.email = "anekalsd96@gmail.com";

  print("Username: ${user.username}");
  print("Password: ${user.password}");
  print("Email: ${user.email}");
}
```
# Sistem login sederhana
```dart
class User {
  String _username = "";
  String _password = "";

  // Getter
  String get username => _username;
  String get password => _password;

  // Setter
  set username(String value) {
    _username = value;
  }

  set password(String value) {
    _password = value;
  }

  // Method untuk login
  bool login(String inputUsername, String inputPassword) {
    if (inputUsername == _username && inputPassword == _password) {
      return true;
    } else {
      return false;
    }
  }
}

void main() {
  var user = User();

  // Mengisi data user
  user.username = "anekalisda";
  user.password = "biarobaru321!";

  // Simulasi login
  String inputUsername = "anekalisda";
  String inputPassword = "biarobaru321!";

  if (user.login(inputUsername, inputPassword)) {
    print("Login berhasil");
  } else {
    print("Login gagal");
  }
}
```
Program ini mensimulasikan sistem login sederhana yang membandingkan username dan password yang dimasukkan dengan data yang tersimpan.
Program ini membuat class User dengan field private:

_username

_password

Data tidak dapat diakses langsung karena bersifat private, sehingga digunakan:

Getter → untuk membaca data

Setter → untuk mengubah data

Kemudian dibuat method login() untuk mengecek apakah username dan password yang dimasukkan sesuai dengan data user.

Jika cocok maka program menampilkan:

Login berhasil

Jika tidak cocok maka:

Login gagal


# Kesimpulan

Dapat disimpulkan bahwa constructor merupakan bagian penting dalam pembuatan objek pada bahasa pemrograman Dart.
Constructor digunakan untuk memberikan nilai awal pada atribut yang dimiliki oleh sebuah class.
Selain itu, konsep enkapsulasi memungkinkan data dalam sebuah class dilindungi dengan cara menjadikannya private.
Akses terhadap data tersebut dapat dilakukan melalui getter dan setter sehingga keamanan data dapat terjaga.
Dengan menerapkan constructor dan enkapsulasi, program dapat menjadi lebih terstruktur, aman, dan mudah untuk dikembangkan di masa yang akan datang.

---

## Menjalankan Program

Kode dapat dijalankan langsung melalui DartPad menggunakan link berikut:

- [Soal 1 – Multiple Constructor](https://gist.github.com/anekalsd96-source/21dfcb61bde4b5bc018f531c4f0b51fa)

- [Soal 2 – Enkapsulasi](https://dartpad.dev/?id=https://gist.github.com/anekalsd96-source/ce546772572cb03137c99feedd1d5136)

- [Sistem Login Sederhana](https://gist.github.com/anekalsd96-source/11c4be90ab6f0f045247ee8170425189)

---
