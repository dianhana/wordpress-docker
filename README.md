# WordPress CMS dengan Docker Compose (MySQL + Redis)

Project ini merupakan implementasi WordPress CMS menggunakan Docker Compose dengan beberapa layanan utama:

* **MySQL** sebagai database
* **Redis** sebagai object cache

Tujuan dari project ini adalah untuk memahami konsep **multi-container orchestration**, komunikasi antar container, serta penggunaan **volume** untuk penyimpanan data.

---

## Teknologi yang Digunakan

* Docker & Docker Compose
* WordPress
* MySQL 5.7
* Redis

---

## Cara Menjalankan Project

1. Clone repository:

```
git clone https://github.com/dianhana/wordpress-docker.git
cd wordpress-docker
```

2. Jalankan container:

```
docker-compose up -d
```

3. Cek container:

```
docker ps
```

4. Akses WordPress:

```
http://localhost:8000
```

---

## Konfigurasi Docker Compose

Project ini menggunakan 3 service utama:

* **wordpress**
* **mysql**
* **redis**

---

## Volume

* **wordpress_data** → menyimpan file WordPress
* **mysql_data** → menyimpan database

---

## Network

Semua container berada dalam satu network sehingga dapat saling berkomunikasi.

---

## Hasil Testing

✅ **WordPress Running**
WordPress berhasil diakses melalui browser.

✅ **MySQL Connection**
Berhasil membuat dan menyimpan postingan sebagai bukti koneksi database berjalan.

✅ **Redis Cache**
Redis berhasil dikonfigurasi dan terhubung dengan WordPress.

✅ **Data Persistence**
Data tetap tersimpan setelah container di-restart.

---

## Pertanyaan & Jawaban

### 1. Kenapa perlu volume untuk MySQL?

Volume digunakan agar data database tidak hilang meskipun container dihentikan atau dihapus.

### 2. Apa fungsi depends_on?

Untuk mengatur urutan startup container, sehingga WordPress menunggu MySQL siap terlebih dahulu.

### 3. Bagaimana cara WordPress connect ke MySQL?

WordPress menggunakan environment variable:

```
WORDPRESS_DB_HOST=mysql:3306
```

Docker menyediakan DNS internal berdasarkan nama service (**mysql**).

### 4. Apa keuntungan pakai Redis untuk WordPress?

Redis digunakan sebagai cache untuk mempercepat akses website dengan menyimpan query database yang sering digunakan.

---

## Kesimpulan

Dengan menggunakan Docker Compose, kita dapat menjalankan beberapa service sekaligus dalam satu environment yang terisolasi. Integrasi WordPress, MySQL, dan Redis membuat aplikasi lebih cepat, modular, dan mudah dikelola.
