## Modul 1

### Reflection 1

Prinsip **Clean Code** yang sudah saya terapkan pada modul 1 adalah, pertama, **Meaningful Names**, saya menamai variabel-variabel seperti `productData`, `productRepository`, dan `allProducts` yang secara jelas mendeskripsikan guna dan isinya. Kedua, **Single Responsibility Principle** atau **SRP**, yang dimana setiap *class* memiliki *role* yang jelas, `Product` meng-*handle* data, `ProductRepository` mengatur logika, dan `ProductController` meng-*handle* *web requests*. Ketiga, **Seperation of Concerns**, saya buat proyek ini dengan memisahkan antara logika bisnisnya, akses data, dan *UI* agar terstruktur dengan rapi.

Keempat, **Don't Repeat Youself** atau **DRY**, dengan menggunakan `@Getter` dan `@Setter` di *model*, kita tidak perlu membuatnya secara manual lagi. Terakhir, kode distruktur agar mudah untuk dilakukan **unit testing** dan **functional testing**.

Praktik **Secure Coding** yang telah diterapkan pada modul 1 ini, pertama, ada **Encapsulation**, dimana *field-field* pada `Product` dan `ProductRepository` dibuat *private* agar tidak dapat diakses dari luar. Kedua, penggunaan `List<Product>` memastikan hanya `Product` yang valid yang di-*handle*, sehingga mengurangi *RTE*. Terakhir, penggunaan `@Autowired` untuk **dependency injections** membuat *inject mock objects* lebih mudah untuk **security testing**.

Area yang dimana bisa di-**improve** adalah saya temui *method* `create` tidak menjamin `productId` yang dibuat unik, sehingga dengan menggunakan `UUID.randomUUID().toString()` dapat menjamin setiap produk memiliki *ID* yang unik.

### Reflection 2

Menulis **unit tests** terasa *time-consuming* tetapi dapat berguna sebagai ***safety net*** yang mendukung kita saat me-*refactor* kode. Walaupun menurut saya tidak ada batasan yang *fix* berapa jumlah tes per *class*, tetapi jumlahnya dapat disesuaikan dengan kompleksitas dan alur *logic*-nya. Setiap *public method* perlu setidaknya satu *test case* dan *test case* tambahan untuk tiap *branch*, *loop*, dan *edge cases*.

Untuk menjamin tes-tesnya cukup, kita perlu memverifikasi **positive scenarios** (input yang valid) dan **negative scenarios** (input yang tidak valid, *list* kosong/ *null*). Jika **code coverage** mencapai 100%, belum tentu berarti kodenya tidak ada *error* sama sekali. *Coverage* hanya mengukur *line-line* mana saja yang tereksekusi dan tidak menilai apakah *logic*-nya benar atau semua kemungkinan input sudah dites.

Jika kita membuat **functional test** baru dengan menduplikasi `CreateProductFunctionalTest`, maka akan timbul beberapa isu. Implementasi ulang semua *setup* dan variabel *instance* di setiap *class* baru akan terlihat redundan dan sulit untuk di-*maintain*. Jika *logic*-nya perlu diubah, maka perlu di-*update* satu-satu. *Test classes*-nya akan terlihat numpuk dengan *setup* daripada fokus tentang tes-tes yang unik. Demi mengatasi masalah ini, ada baiknya dibuat **abstract base class** yang mengandung semua prosedur *setup* yang sama, lalu **functional test classes** yang lain bisa *extend* dari *base class* ini.

---