# Materi Struktur File di Next.js

Pada Next.js, struktur file sangat penting untuk pengelolaan dan pengembangan aplikasi web. Di bawah ini, kita akan membahas tentang **Top-level**, **Pages Router**, dan **App Router**.

## A. Top-level Struktur File di Next.js

### 1. **Top-level Folder**
Top-level folder di dalam proyek Next.js biasanya berisi folder dan file utama yang digunakan untuk konfigurasi dan penataan aplikasi. Beberapa folder yang umum ditemukan adalah:

- **`pages/`**: Menyimpan file-file halaman aplikasi yang akan diakses oleh pengguna.
- **`public/`**: Menyimpan file statis seperti gambar, CSS, dan JavaScript yang dapat diakses langsung oleh browser.
- **`styles/`**: Folder untuk menyimpan file CSS atau file styling global.
- **`node_modules/`**: Folder yang berisi dependensi proyek.
- **`components/`** (opsional): Menyimpan komponen React yang digunakan di beberapa halaman.
- **`lib/`** (opsional): Menyimpan kode utilitas atau fungsi yang digunakan di berbagai bagian aplikasi.

### 2. **Top-level Files**
Di level atas folder, Anda akan menemukan beberapa file penting:

- **`package.json`**: File konfigurasi untuk manajemen dependensi dan pengaturan aplikasi.
- **`next.config.js`**: File konfigurasi untuk Next.js (misalnya untuk penyesuaian build, pengaturan custom server, dsb).
- **`tsconfig.json`** (jika menggunakan TypeScript): File konfigurasi untuk TypeScript.
- **`.gitignore`**: Menentukan file atau folder mana yang harus diabaikan oleh Git.

---

## B. Pages Router

Next.js menyediakan **Pages Router** untuk routing berbasis file. Setiap file JavaScript atau TypeScript dalam folder `pages/` otomatis menjadi route pada aplikasi.

### 1. **Struktur File Pages Router**
Struktur file di dalam folder `pages/` sangat mudah dipahami karena setiap file mewakili URL di aplikasi.

Contoh struktur:

```text
pages/
├── index.js            // Home page, URL: /
├── about.js            // About page, URL: /about
└── products/
    └── index.js        // Products list, URL: /products
    └── [id].js         // Dynamic route, URL: /products/:id
```

### 2. **Special Files in Pages Router**
Beberapa file khusus di dalam pages/ memiliki peran tertentu:

- **`_app.js / _app.tsx`**: File ini digunakan untuk membungkus seluruh aplikasi. Biasanya digunakan untuk inisialisasi global, seperti pengaturan provider atau layout global.
- **`_document.js`**: Digunakan untuk kustomisasi HTML dan struktur dokumen (biasanya untuk menambahkan metadata atau elemen global seperti font).
- **`404.js`**: Halaman error 404, yang akan ditampilkan ketika route yang diminta tidak ada.
- **`_error.js`**: Halaman untuk menangani kesalahan pada level aplikasi.
