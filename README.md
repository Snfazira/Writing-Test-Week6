# __Writing Test Week 6__
## __Database__

- Database adalah kumpulan informasi yang disimpan didalam komputer secara sistematik dan saling berelasi dan sekumpulan tabel yang berisikan informasi untuk diolah yang kemudian data tersebut bisa digunakan di dalam sebuah sistem Untuk membuat Database diperlukan sebuah software yang dinamakan dengan DBMS(Database Management System)

- Database Management System : software yang dapat digunakan oleh user untuk berkomunikasi dengan data yang ada dalam media penyimpanan.

- Tipe utama pada Database management System antara lain : 
    - Hierarchical
    - Network
    - Relational
    - Non Relational
    - Object Oriented


- Adapun istilah pada database, yaitu : 
    - Table : kumpulan value yang dibangun oleh baris dan kolom, yang didalamnya berisikan atribut dari sebuah data.

    - Field : kolom dari sebuah tabel dimana masing-masing field memiliki tipe data masing-masing.

    - Record :  kumpulan nilai yang saling terkait. Record merupakan isi dari sebuah tabel.

- SQL (Structured Query Language)merupakan bahasa yang digunakan untuk mengakses database.

- SQL adalah Bahasa Query yang digunakan untuk melakukan interaksi di RDMS (Relational Database Management System) 
    - Membuat, Menampilkan dan menghapus data didalam database.
    - Mengatur “Permission” (siapa saja yang bisa mengakses data).
    - Membuat dan menghapus Database.

- DDL (Data Definition Language) : merupakan kumpulan perintah SQL yang digunakan untuk membuat, mengubah dan menghapus struktur dan definisi metadata dari objek-objek Database.

- Membuat table pada database
```
CREATE TABLE perpustakaan (
    no_buku varchar(10)
    judul varchar(50)
    pengarang varchar(50)
    tahun_terbit varchar(10)
    jenis_buku varchar(50)
    PRIMARY KEY (KdBuku)
)
```

- Alter : digunakan untuk mengubah struktur dari tabel yang ada, seperti untuk menambahkan atau menghapus kolom/field.

- Menambah primary key
```
ALTER TABLE nama_tabel ADD Primary key (nama_field)
ALTER TABLE buku ADD PRIMARY KEY (KdBuku)
```

- Menambah kolom
```
ALTER TABLE nama_tabel ADD nama_field tipe_data(ukuran)
ALTER TABLE buku ADD pengarang varchar (50)
```

- Mengubah struktur untuk field pengarang dari Leght (50) menjadi (30)
```
ALTER TABLE buku ALTER COLUMN pengarang varchar(30)
```

- Drop : digunakan untuk menghapus Database, Table, dan View atau Index.

- Menghapus database 
```
DROP DATABASE Nama_Database
DROP DATABASE buku
```

- DML (Data Manipulation Language) 

    - Select : digunakan untuk menyeleksi data berdasarkan syarat yang diberikan dan Dengan menggunakan perintah SELECT ini record didalam tabel tertentu yang berjumlah ribuan bahkan jutaan dapat ditampilkan.
    ```
    SELECT * FROM NAMA_TABEL
    SELECT NAMA_KOLOM FROM NAMA_TABEL
    SELECT DISTINCT NAMA_KOLOM FROM NAMA_TABEL
    Distinct digunakan apabila ingin menghilangkan duplikasi dari hasil query (hasil quet yang di tampilkan sekali)
    ```

    - Insert : digunakan untuk memasukkan data ke kolom-kolom yang terdapat pada tabel/view.
    ```
    INSERT INTO NAMA_TABEL VALUES (value1, values2, ..., valueN)
    INSERT INTO NAMA_TABEL (nama_field1, nama_field2,... nama_fieldN) VALUES (value1, value2,..., valueN)
    ```
    - Where, And, Or, Not, Like
    ```
    SELECT column1, column2
    FROM nama_tabel
    WHERE conditionl AND condition2 OR condition3 NOT condition4;
    ```
    Syntax penulisannya seperti gambar diatas, tinggal disesuaikan dengan nama column, tabel, dan kondisi yang diinginkan untuk mendapatkan data.
    ```
    SELECT * FROM customers WHERE age > 20;
    SELECT * FROM customers WHERE firstname = "Zira";
    SELECT * FROM customers WHERE city = "Medan" age > 20;
    ```

    ```
    SELECT * FROM customers WHERE city LIKE "%on";
    SELECT * FROM customers WHERE city LIKE "n%"
    SELECT * FROM customers WHERE city NOT LIKE "%n%";
    ```

    - Update : digunakan untuk melakukan editing pada isi dari kolom (field) yang dipilih. Hal ini dilakukan untuk memperbaiki data lama / terjadi kesalahan.
    ```
    UPDATE nama_tabel SET nama_kolom = "new data" WHERE key_column = 1;
    ```
    - Delete 
    : digunakan untuk menghapus data dalam tabel yang menjadi target.
    ```
    DELETE FROM nama_tabel WHERE condition;
    ```

- DCL (Data Control Language) : 
    
    - GRANT : digunakan untuk memberikan hak akses pada user.

    - REVOKE : digunakan untuk mencabut hak akses yang telah diberikan pada user
    ```
    GRANT INSERT, UPDATE, DELETE ON MAHASISWA TO PUBLIC
    REVOKE SELECT ON MAHASISWA TO PUBLIC
    ```

    - Database Relationships : elasi atau hubungan antara beberapa tabel dalam bahasa yang kita miliki.
    
    - Relasi antar tabel dihubungkan oleh Primary key dan foreign key.

    - Primary key adalah atribut yang tidak hanya mengidentifikasi secara unik suatu kejadian, tapi juga mewakili setiap kejadian suatu entitas.
    ```
    CREATE TABLE buku(
        kd_buku AUTO_INCREMENT PRIMARY KEY,
        pengarang VARCHAR(50)
    );
    ```

- Foreign key : atribut yang melengkapi relationship dan menunjukan hubungan antara tabel induk dengan tabel anak.

- Membuat Foreign key tanpa explicit declaration, customer_id dengan menggunakan INDEX.
```
CREATE TABLE orders(
    order_id INT AUTO_INCREMENT PRIMARY KEY, 
    customers_id INT,
    amount DOUBLE,
    INDEX (costumer_id)
);
```


- Beberapa tipe database relationships:

    - One To One Relationships
    - One to Many and Many to One      Relationships
    - Many to Many Relationships
    - Self Referencing Relationships

- SQL Table Join

- Join : penggabungan tabel yang dilakukan melalui kolom/key tertentu yang memiliki nilai terkait untuk mendapatkan satu set data dengan informasi lengkap.

- Inner Join : menampilkan data hanya yang sesuai di kedua tabel.

```
SELECT * FROM karyawan INNER JOIN gaji
ON karyawan.karyawan.id = gaji.karyawan_id;
```

- Left Join : menampilkan semua data sebelah kiri dari tabel yang di joinkan dan menampilkan data sebelah kanan yang cocok dengan kondisi join. Jika tidak ditemukan kecocokan, maka akan di set NULL secara otomatis.
```
SELECT * FROM karyawan LEFT JOIN gaji
ON karyawan.karyawan_id = gaji.karywan_id;
```
- Right Join : menampilkan semua data sebelah kanan dari tabel yang di joinkan dan menampilkan data sebelah kiri yang cocok dengan kondisi join. Jika tidak ditemukan kecocokan, maka akan di set NULL secara otomatis.
```
SELECT * FROM gaji RIGHT JOIN gaji
ON karyawan.karyawan_id = gaji.karywan_id;
```

- NoSQL : database yang tidak memiliki perintah SQL dan memiliki tujuan untuk model data spesifik dan memiliki skema fleksibel dalam mengembangkan aplikasi modern, contoh: aplikasi yang bersifat real time.

- Kelebihan NoSQL di banding Relasional Database.
    - NoSQL bisa menampung data yang terstruktur, semi terstruktur dan tidak terstruktur.
    - Menggunakan OOP dalam pengaksesan/manipulasi data.
    - NoSQL tidak mengenal schema tabel yang kaku.

- Document Database : penyimpan data dan proses manipulasinya dalam bentuk Objek dokumen.

<hr>

## __MySQL__

- Relations di SQL:
- One to Many
    - Paling Sering Digunakan
    - Satu baris dalam tabel dapat memiliki beberapa baris di table relasinya

- Many to Many
    - Digunakan ketika kedua tabel yang berelasi dapat memiliki beberapa baris di tabel relasinya.

- One to One
    - Sangat jarang digunakan
    - Diimplementasikan dengan cara yang sama seperti One to Many tetapi dengan kondisi tambahan (foreign key merupakan primary key)

- Efek Jika Tidak Melakukan Database Normalization

    - INSERT Anomali : Situasi dimana tidak memungkinkan memasukkan beberapa jenis data secara langsung di database.

    - DELETE Anomali : Penghapusan data yang tidak sesuai dengan yang diharapkan, artinya data yang harusnya tidak terhapus mungkin ikut terhapus.

    - UPDATE Anomali : Situasi dimana nilai yang diubah menyebabkan inkonsistensi database, dalam artian data yang diubah tidak sesuai dengan yang diperintahkan atau yang diinginkan.

- Bentuk Database Normalization : 
- First Normal Form (1NF)
    - Menghilangkan multiple value pada sebuah kolom table database
    - Sebuah table memenuhi kaidah 1NF jika :
    1. Setiap kolom bernilai tunggal (single value)
    2. Setiap kolom memiliki nama yang unik
    3. Urutan penyimpanan data tidak menjadi masalah

- Second Normal Form (2NF)
    - Harus sudah dalam bentuk 1NF untuk mendapatkan 2NF
    - Menghapus beberapa subset data yang ada pada tabel dan menempatkan mereka pada tabel terpisah.

- Third Normal Form (3NF)
    - Menghilangkan seluruh atribut atau field yang tidak berhubungan dengan primary key. Dengan demikian tidak ada ketergantungan transitif pada setiap kandidat key.


- Masih ada banyak bentuk database normalisasi, diantaranya : EKNF,BCNF,4NF,5NF,DKNF,6NF

- Keys di SQL :
- Super Key : Kumpulan dari satu atau lebih dari satu key yang dapat digunakan untuk mengidentifikasi record secara unik dalam sebuah tabel dan  superset dari Candidate Key.

- Candidate Key : kumpulan satu atau lebih fields/columns yang dapat mengidentifikasi record secara unik dalam tabel.
Bisa jadi ada beberapa Candidate Keys di dalam satu tabel
Setiap Candidate Key bisa digunakan sebagai Primary Key dan sebagai key yang tidak mempunyai value yang berulang.

- Primary Key : kumpulan satu atau lebih fields/columns dari sebuah tabel yang secara unik mengidentifikasi sebuah record dalam tabel database.
Valuenya tidak boleh berupa null ataupun duplicate value dan hanya boleh salah satu Candidate Key yang bisa menjadi Primary Key.

- Alternate Key : bisa digunakan menjadi primary key dan merupakan candidate key yang tidak dijadikan  primary key.

- Unique Key : Kumpulan dari satu atau lebih fields/columns di sebuah table database yang secara unik mengidentifikasi sebuah record dalam table database tersebut.
value dari Unique Key bisa berupa satu buah null value di dalam sebuah table database, dan Unique Key tidak bisa memiliki duplicate values

- Foreign Key : Field di sebuah table database yang menjadi Primary Key di table database lain dan value dari Foreign key bisa menerima multiple null dan duplicate values.

- Join Multiple Tables : Mengambil records dari dua atau lebih table database yang memiliki relationship dan akan di sajikan dalam single result set.

- Aggregate Functions : Mengambil satu nilai setelah melakukan perhitungan pada sekumpulan nilai
    
    - MAX : fungsi mengembalikan nilai terbesar dari kolom yang dipilih.
    
    - MIN : fungsi mengembalikan nilai terkecil dari kolom yang dipilih.

    - SUM : fungsi mengembalikan jumlah total kolom numerik.

    - COUNT : fungsi mengembalikan jumlah baris yang cocok dengan kriteria yang ditentukan.

    - AVG : fungsi mengembalikan nilai rata-rata kolom numerik
    
    - UNION : Digunakan untuk menggabungkan kumpulan hasil dari dua atau lebih pernyataan SELECT.

    - GROUP BY : Mengelompokkan baris yang memiliki nilai yang sama ke dalam baris ringkasan dan sering digunakan dengan fungsi agregat untuk mengelompokkan kumpulan hasil dengan satu atau lebih kolom.

    - HAVING : ditambahkan ke SQL karena kata kunci WHERE tidak dapat digunakan dengan aggregate functions.

    - LIKE & Wildcards : Operator LIKE digunakan dalam klausa WHERE untuk mencari pola tertentu dalam kolom sedangkan wildcard digunakan untuk menggantikan satu atau lebih karakter dalam sebuah string.

<hr>

## __Authentication & Authorization in Express__

- Authentication adalah verifikasi siapa anda dan bergantung pada satu atau lebih faktor untuk memverifikasi identitas, dan faktor-faktor ini datang dalam tiga jenis utama:

    - Pengetahuan contohnya username and password.

    - Kepemilikan seperti kartu keamanan atau perangkat seluler

    - Inherence contohnya data biometrik seperti sidik jari.

- Authentication bergantung pada satu faktor, seperti kombinasi nama pengguna/sandi sederhana, disebut Otentikasi Satu Faktor, dan menjadi semakin tidak aman.

- Authorization : verifikasi atas apa yang boleh Anda lakukan.

- Authorization sangat penting untuk keamanan web, dan bertanggung jawab atas segala hal mulai dari mencegah pengguna memodifikasi akun satu sama lain, melindungi aset back-end dari penyerang, hingga memberikan akses terbatas ke layanan eksternal.

- Encryption : proses mengubah data menjadi format yang tidak dapat dibaca kecuali Anda memiliki kunci yang benar untuk mendekripsinya. Enkripsi datang dalam dua jenis utama:

    - Enkripsi simetris
    - Enkripsi asimetris

- web session : mengacu pada serangkaian interaksi pengguna selama jangka waktu tertentu. Data sesi disimpan di sisi server dan dikaitkan dengan ID sesi.

- Cookies adalah potongan kecil data file teks berukuran maksimal 4kb browser menyimpan yang secara otomatis dikirim dengan permintaan HTTP ke aplikasi web.

- JSON Web Tokens : bjek JSON mandiri yang secara kompak dan aman mengirimkan informasi antara dua pihak. Mereka aman karena ditandatangani secara digital menggunakan pasangan kunci rahasia atau publik/pribadi.

- Komponen JWT
JWT terdiri dari tiga komponen:

    - Header
    - Payload
    - Signature

- JWT header : berisi jenis token yang kami buat dan algoritma penandatanganan yang akan digunakan.

- JWT payload : berisi klaim tentang suatu entitas. Klaim adalah pernyataan atau informasi dan entitas sering kali adalah pengguna.

- JWT signature  : digunakan untuk memverifikasi bahwa JWT tidak dirusak atau diubah. Itu dapat dibuat dengan mengambil tajuk yang disandikan, muatan yang disandikan, rahasia, dan menggunakan algoritma hashing untuk membuat hash dari elemen-elemen itu.

<hr>

## __Sequelize__

- Sequelize : ORM (Object Relational Mapping) Node JS yang berbasis promise. Sequelize mendukung sebagian besar relational Database seperti MySQL, PostgresQL, MariaDB, SQLite dan Miscrosoft SQL Server.

- ORM : suatu metode/teknik pemrograman yang digunakan untuk mengkonversi data dari lingkungan bahasa pemrograman berorientasi objek (OOP) dengan lingkungan database relational.  

- Install Sequelize-cli
```
npm install -g sequelize-cli
```

- menginstall driver sql yang kita butuhkan
```
Installing by NPM
npm install --save sequelize
install Driver Database
npm install --save mysql
```

- Generate Sequelize

    - Sequelize init
    ```
    npx sequelize-cli init
    ```

    - Setting database

- Generate Model

    - kita dapat menggunakan generate dan kita bisa mengecek ke database sehingga dapat kita gunakan untuk penimpanan DB
    ```
    npx sequelize-cli db:migrate
    ```

    - kita bisa mengembalikan (undo) menggunakan :
    ```
    npx sequelize-cli db:migrate:undo
    ```
- Generate Seed : data awal yang bisa kita gunakan untuk mengisi data di database untuk keperluan awal project menggunakan sequelize
```
npx sequelize-cli seed:generate --name demo-todo
```

- menjalankan generate seed menggunakan sequelize 
```
npx sequelize-cli db:seed:all
```

- mengembalikan (undo) menggunakan
```
npx sequelize-cli db:seed:undo
```

- Membuat CRUD Dengan Express dan Sequelize

    Setelah Model tersedia, maka model tersebut bisa kita gunakan untuk membuat CRUD.

    Beberapa endpoint RESTFul :
    
    - Get All Todos
    - Get Todo Detail By Id
    - Create New Todo
    - Update Todo By Id
    - Delete Todo

<hr>




















































 