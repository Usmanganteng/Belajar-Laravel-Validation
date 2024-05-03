<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

>
---
<b>requirement/persyaratan</b>
---
> #### Php versi 8
>> - Cara menginstal php dalam bahasa indonesia : https://youtu.be/Uw3ZGIMvIdA?si=mBVZ-lBnoCilASzo
>> - Cara menginstal php dalam bahasa inggris : https://youtu.be/MPRLUd8Pmyo?si=FqN54nVr4duH4Keg
-----
> #### Laravel versi 10.0.3
>> - cara menginstal laravel yang versi yang sama 
```
   Composer Create-project laravel\laravel=v10.0.3 nama-folder
```
>> - Cara tahu laravel sekarang versi berapa : https://packagist.org/packages/laravel/laravel
---
<b>materi</b>
---
> #### apa itu validation
> - validasi di Laravel adalah proses memastikan data yang dimasukkan ke dalam aplikasi web Anda aman dan sesuai dengan yang diharapkan.
> #### manfaat
> - Meningkatkan keamanan aplikasi
> - Memastikan data yang konsisten
> - Mempermudah pengembangan aplikasi
> - Menampilkan pesan error yang informatif
---
> #### validator
> - `Validator` dalam Laravel adalah kelas yang digunakan untuk memvalidasi data. Dengan `Validator`, Anda bisa menentukan aturan validasi, seperti memastikan bahwa input adalah string, panjangnya tidak melebihi batas tertentu, atau memenuhi format email.
> - contoh sintaksnya :
> ```
> $validator = Validator::make($data, $rules);
>
> if ($validator->fails()) {
>    // Tangani kesalahan jika validasi gagal
> } else {
>    // Lakukan tindakan jika validasi berhasil
> }
> ```
> -Dalam contoh ini, `$data` adalah data yang ingin divalidasi, dan $rules adalah aturan validasi yang ditentukan. Jika validasi gagal, Anda bisa menangani kesalahan tersebut; jika tidak, 
---
> #### Error Message
> - Error Message dalam Laravel adalah pesan yang memberi tahu pengguna tentang kesalahan dalam input yang mereka berikan. Ini muncul ketika validasi data gagal, membantu pengguna memahami masalahnya. Misalnya, "Email harus berupa alamat email yang valid." pesan kesalahan memberi tahu pengguna bahwa mereka harus memasukkan alamat email yang benar.
---
> #### Validation Exception
> - `ValidationException` dalam Laravel adalah pengecualian yang dilemparkan ketika validasi data gagal. Ketika Anda memvalidasi data dan ada kesalahan, Laravel secara otomatis melemparkan pengecualian ini. Anda dapat menangkapnya dalam kontroler atau bagian lain dari kode Anda untuk menangani kesalahan validasi dan memberikan respons yang sesuai kepada pengguna.
> - contoh sintaksnya:
>```
>use Illuminate\Validation\ValidationException;
>
>try {
>    // Lakukan validasi data di sini
>} catch (ValidationException $e) {
>    // Tangani pengecualian validasi di sini
>    $errors = $e->validator->errors()->all();
>    return response()->json(['errors' => $errors], 422);
>}
>```
> - Dalam blok `catch`, kita menangkap `ValidationException` dan kemudian dapat melakukan apa pun yang diperlukan, seperti mengambil pesan kesalahan validasi dari objek validator dan mengembalikannya kepada
pengguna dalam bentuk yang sesuai. Hal ini memungkinkan aplikasi Anda untuk memberikan umpan balik yang tepat kepada pengguna ketika terjadi kesalahan validasi.
---
> #### Validation Rules
> - Aturan validasi dalam Laravel adalah kumpulan aturan yang digunakan untuk memeriksa data yang dimasukkan oleh pengguna. Ini termasuk memastikan data tidak kosong (`required`), adalah alamat email yang valid (`email`), merupakan bilangan (`numeric`), dll. Anda bisa menggunakan aturan ini untuk memvalidasi input dengan cepat dan tepat.
---
> #### Valid Data
> - Data yang valid adalah data yang sesuai dengan aturan validasi yang telah ditetapkan. Dalam konteks Laravel, ini berarti data yang memenuhi semua aturan validasi yang telah didefinisikan, seperti tidak kosong (required), memiliki format yang benar (misalnya, alamat email yang valid), atau memenuhi batasan tertentu (misalnya, panjang string minimum). Jadi, data yang valid adalah data yang lolos semua pengujian validasi yang telah ditetapkan untuk itu.
---
> #### Validation Message
> - Validation Message adalah pesan yang memberitahu pengguna tentang kesalahan yang terjadi saat validasi data. Ketika data yang dimasukkan pengguna tidak memenuhi aturan validasi yang telah ditetapkan, pesan validasi memberikan informasi tentang kesalahan tersebut. Pesan ini membantu pengguna memahami masalahnya dan dapat membimbing mereka untuk memperbaiki input mereka. Pesan validasi yang baik biasanya jelas dan informatif, memberikan petunjuk yang berguna kepada pengguna tentang apa yang salah dengan data yang mereka masukkan.
---
> #### Additional Validation
> - Validasi tambahan adalah langkah-langkah validasi ekstra yang Anda terapkan untuk memeriksa data lebih lanjut setelah validasi standar. Ini bisa termasuk pengujian spesifik untuk kasus penggunaan tertentu atau memverifikasi data melawan layanan eksternal. Validasi tambahan membantu memastikan bahwa data yang dimasukkan memenuhi persyaratan lebih lanjut sesuai dengan kebutuhan aplikasi Anda.
---
> #### Custom Rule
> - Anda bisa membuat aturan validasi kustom dengan Laravel. Berikut langkahnya:
>> 1. Gunakan perintah artisan untuk membuat aturan baru:
>>```
>>php artisan make:rule CustomRule
>>```
>> 2. Di dalam file yang baru dibuat (CustomRule.php), tentukan logika validasi di dalam metode `passes`.
>>```
>>public function passes($attribute, $value)
>>{
>>    // Logika validasi Anda di sini
>>}
>>```
>> 3. Definisikan pesan kesalahan dalam metode `message`.
>> ```
>> public function message()
>>{
>>    return 'Pesan kesalahan kustom Anda di sini.';
>>}
>> ```
>>  4. Gunakan aturan validasi kustom Anda dalam validasi Anda seperti aturan validasi bawaan lainnya.
>> ```
>> $request->validate([
>>    'field' => ['required', new CustomRule],
>>]);
>>```
---
> #### Rule Classes
> - Rule classes dalam Laravel adalah kelas yang menerapkan aturan validasi khusus. Dengan membuat rule class, Anda bisa memisahkan logika validasi dari kontroler, meningkatkan keterbacaan kode. Langkahnya: buat rule class, tentukan logika validasi dalam metode `passes`, definisikan pesan kesalahan dalam metode `message`, lalu gunakan rule class tersebut dalam validasi seperti aturan bawaan.
---
> #### Nested Array Validation
> - Anda bisa memvalidasi array bersarang dalam Laravel dengan menggunakan sintaks seperti ini:
> ```
> $request->validate([
>    'users.*.name' => 'required|string',
>    'users.*.email' => 'required|email',
>    'users.*.age' => 'required|integer|min:18',
>]);
>```
> - Dalam contoh ini, kita memvalidasi setiap elemen dalam array `users`, memastikan bahwa setiap pengguna memiliki nama, email, dan usia yang sesuai dengan aturan validasi yang ditetapkan.
---
> #### Http Request Validation
> - Validasi permintaan HTTP dalam Laravel memungkinkan Anda untuk memverifikasi data yang dikirim oleh pengguna melalui permintaan HTTP, seperti formulir web atau permintaan API.
>> 1. Buat Aturan Validasi: Tentukan aturan validasi untuk setiap bidang data yang ingin Anda validasi di dalam kelas permintaan.
>> ```
>> public function rules()
>>{
>>    return [
>>        'title' => 'required|string|max:255',
>>        'content' => 'required|string',
>>        'tags' => 'nullable|array',
>>        'tags.*' => 'string|max:50',
>>    ];
>> }
>> ```
>>  2. Gunakan Kelas Permintaan: Gunakan kelas permintaan yang baru Anda buat dalam metode kontroler untuk menangani validasi.
>> ```
>> public function store(StorePostRequest $request)
>>{
>>    // Data sudah divalidasi dan disahkan, lanjutkan dengan pemrosesan
>>}
>>```
>>  3. Tampilkan Pesan Kesalahan: Jika validasi gagal, Laravel akan secara otomatis mengembalikan pengguna ke halaman sebelumnya dengan pesan kesalahan yang sesuai.
---
<B>TERIMA KASIH</b>
