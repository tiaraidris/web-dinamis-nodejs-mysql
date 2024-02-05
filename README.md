# web-dinamis-nodejs-mysql
1. Pastikan Node.js telah terinstal di komputer Anda.

2. Buat folder proyek baru dan masuk ke dalamnya di terminal Anda.

3. Jalankan npm init untuk membuat file package.json yang menyimpan informasi tentang proyek Anda.

4. Instal modul-modul yang diperlukan seperti express, mysql, dan body-parser dengan perintah npm install express mysql body-parser.

Langkah 2: Setup Server dengan Express

javascript
Copy code
// app.js

const express = require('express');
const bodyParser = require('body-parser');
const mysql = require('mysql');

const app = express();
const port = 3000;

// Menggunakan body-parser untuk membaca data dari body request
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));

// Setup koneksi MySQL
const connection = mysql.createConnection({
    host: 'localhost',
    user: 'username', // ganti dengan username MySQL Anda
    password: 'password', // ganti dengan password MySQL Anda
    database: 'database_name' // ganti dengan nama database Anda
});

connection.connect();

// Route untuk menampilkan semua biodata siswa
app.get('/siswa', (req, res) => {
    connection.query('SELECT * FROM siswa', (error, results, fields) => {
        if (error) throw error;
        res.json(results);
    });
});

// Route untuk menambahkan biodata siswa baru
app.post('/siswa', (req, res) => {
    const { nama, umur, alamat } = req.body;
    const query = `INSERT INTO siswa (nama, umur, alamat) VALUES ('${nama}', '${umur}', '${alamat}')`;
    connection.query(query, (error, results, fields) => {
        if (error) throw error;
        res.send('Data siswa berhasil ditambahkan');
    });
});

// Mulai server
app.listen(port, () => {
    console.log(`Server berjalan di http://localhost:${port}`);
});
Langkah 3: Buat Database

5. Buka MySQL dan buat database dengan nama biodata_siswa.

6. Buat tabel siswa dengan kolom id, nama, umur, dan alamat.

7. Langkah 4: Buat Frontend (HTML/CSS/JavaScript)

8. Buatlah file HTML, CSS, dan JavaScript untuk membuat antarmuka pengguna yang interaktif untuk menambah dan menampilkan biodata siswa.

Ini adalah dasar yang dapat Anda mulai. Anda dapat memperluas dan menyesuaikan sesuai kebutuhan proyek Anda. Jangan lupa untuk menambahkan keamanan dan validasi data agar aplikasi Anda lebih aman dan andal.





