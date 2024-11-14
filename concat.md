# Materi Struktur File di Next.js

Pada Next.js, struktur file sangat penting untuk pengelolaan dan pengembangan aplikasi web. Di bawah ini, kita akan membahas tentang **Top-level**, **Pages Router**, dan **App Router**.

## A. Top-level Struktur File di Next.js

### 1. Top-level Folder
Top-level folder di dalam proyek Next.js biasanya berisi folder dan file utama yang digunakan untuk konfigurasi dan penataan aplikasi. Beberapa folder yang umum ditemukan adalah:

- **app/ (Jika menggunakan App Router)**: Menyimpan file-file halaman aplikasi yang akan diakses oleh pengguna.
- **pages/ (Jika menggunakan Pages Router)**: Menyimpan file-file halaman aplikasi yang akan diakses oleh pengguna.
- **public/**: Menyimpan file statis seperti gambar, CSS, dan JavaScript yang dapat diakses langsung oleh browser.
- **styles/**: Folder untuk menyimpan file CSS atau file styling global.
- **node_modules/**: Folder yang berisi dependensi proyek.
- **components/** (opsional): Menyimpan komponen React yang digunakan di beberapa halaman.
- **lib/** (opsional): Menyimpan kode utilitas atau fungsi yang digunakan di berbagai bagian aplikasi.

### 2. Top-level Files
Di level atas folder, Anda akan menemukan beberapa file penting:

- **package.json**: File konfigurasi untuk manajemen dependensi dan pengaturan aplikasi.
- **next.config.js**: File konfigurasi untuk Next.js (misalnya untuk penyesuaian build, pengaturan custom server, dsb).
- **tsconfig.json** (jika menggunakan TypeScript): File konfigurasi untuk TypeScript.
- **.gitignore**: Menentukan file atau folder mana yang harus diabaikan oleh Git.

---

## B. Pages Router

Next.js menyediakan Pages Router untuk routing berbasis file. Setiap file JavaScript atau TypeScript dalam folder pages/ otomatis menjadi route pada aplikasi.

### 1. Struktur File Pages Router
Secara default bila anda memilih menggunakan rages router maka akan tercipta 2 folder khusus untuk page routing
```text
my-app/
├── pages             // Folder untuk routing
└── styles            // Folder untuk file styling
```

Struktur file di dalam folder pages/ sangat mudah dipahami karena setiap file mewakili URL di aplikasi.

Contoh struktur:

```text
pages/
├── index.js            // Home page, URL: /
├── about.js            // About page, URL: /about
└── products/
    └── index.js        // Products list, URL: /products
    └── [id].js         // Dynamic route, URL: /products/:id
```

### 2. Special Files in Pages Router
Perlu diingat format .js, .jsx, .tsx dapat digunakan pada pages router.
Beberapa file khusus di dalam pages/ memiliki peran tertentu:

- **_app.js / _app.tsx**: File ini digunakan untuk membungkus seluruh aplikasi. Biasanya digunakan untuk inisialisasi global, seperti pengaturan provider atau layout global.
- **_document.js / _document.tsx**: Digunakan untuk kustomisasi HTML dan struktur dokumen (biasanya untuk menambahkan metadata atau elemen global seperti font).
- **index.js / index.tsx**: Berfungsi sebagai entry point atau halaman utama untuk rute / dari aplikasi.

---

## C. App Router

**App Router** adalah jenis routing terbaru yang disediakan oleh Next.js dirilis pada versi 13. Router jenis ini menggunakan top-level folder `app/`. Jadi, semua halaman dalam aplikasi disimpan di dalam folder tersebut.

### 1. **Struktur File App Router**
Struktur file di dalam folder ini kurang lebih hampir sama dengan _Pages Router_. Perbedaan utama terletak pada cara kerja halaman index. Jika di _Pages Router_ halaman utamanya menggunakan nama file `index.tsx`, pada router ini menggunakan nama file `page.tsx ` atau `page.js`.

Contoh struktur:

```text
app/
├── page.js                 // Home page, URL: "/"
├── about.js                // Tidak routable
├── products/
    └── page.js             // Products list, URL: "/products"
    └── ProductsLayout.js   // Tidak routable
└── chat/
    └──[slug]
        └── page.js         // URL: "/chat/:slug" dengan slug adalah dinamis
```

### 2. **Routing Files**
Sama seperti _Pages Router_, _App Router_ juga memiliki file-file khusus atau spesial di dalam top-level folder `app/`. Berikut adalah file-file penting yang harus kita ketahui:

- **`layout.js / layout.tsx`**, yaitu file layout
- **`page.js / page.tsx`**, yaitu file utama yang pertama kali diakses
- **`loading.js / loading.tsx`**, yaitu file untuk menghandle halaman loading
- **`error.js / error.tsx`**, yaitu file untuk menghandle halaman ketika terjadi error

Adapun file-file seperti `not-found.js`, `global-error.js`, dan lain-lain.

# Perbandingan Struktur File di Next.js

Berikut adalah perbandingan struktur file antara **Top-level Struktur File**, **Pages Router**, dan **App Router** di Next.js.

| **Aspek**               | **Top-level Struktur File**                                          | **Pages Router**                                                                                                                                                            | **App Router**                                                                                                                                                          |
|-------------------------|----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Penggunaan**          | Struktur dasar untuk semua proyek Next.js                            | Routing berbasis file, cocok untuk proyek dengan URL langsung.                                                                                                               | Sistem routing terbaru di Next.js (versi 13), menawarkan fitur modular seperti nested routing dan layout hierarki.                                                    |
| **Folder Utama**        | - `app/` (App Router) atau `pages/` (Pages Router) <br> - `public/` (file statis) <br> - `styles/` (file styling) <br> - `components/` (opsional) | - `pages/`: Menyimpan file halaman URL-based <br> - `styles/`: File styling                                                          | - `app/`: Menyimpan semua halaman aplikasi menggunakan App Router <br> - `styles/`: File styling                                                                        |
| **Struktur File Halaman** | Tidak ada aturan khusus; hanya file konfigurasi utama             | - `pages/index.js`: URL: `/` <br> - `pages/about.js`: URL: `/about` <br> - `pages/products/[id].js`: URL: `/products/:id`                                                | - `app/page.js`: URL: `/` <br> - `app/products/page.js`: URL: `/products` <br> - `app/chat/[slug]/page.js`: URL: `/chat/:slug`                                         |
| **Routing**             | Tidak berlaku                                                       | Routing otomatis berdasarkan nama file di `pages/`. Setiap file menjadi endpoint URL sesuai strukturnya.                                                                   | Routing otomatis berdasarkan nama file di `app/`, mendukung nested route dan penggunaan folder layout.                                                                  |
| **File Utama**          | - `package.json`: Dependensi <br> - `next.config.js`: Konfigurasi <br> - `.gitignore`: File/folder yang diabaikan | - `_app.js` atau `_app.tsx`: Layout global dan inisialisasi aplikasi <br> - `_document.js`: Struktur HTML <br> - `index.js`: Halaman utama `/`                         | - `layout.js`: Layout aplikasi <br> - `page.js`: Halaman utama <br> - `loading.js`: Halaman loading <br> - `error.js`: Halaman error                                   |
| **Dynamic Routing**     | Tidak berlaku                                                       | Menggunakan tanda kurung kotak pada nama file (misal, `[id].js` untuk `/products/:id`)                                                                                    | Menggunakan tanda kurung kotak pada nama folder atau file (misal, `[slug]/page.js` untuk `/chat/:slug`)                                                                 |
| **Kustomisasi HTML**    | Tidak berlaku                                                       | `_document.js`: Menambahkan elemen global atau metadata pada struktur HTML                                                                                                 | Mendukung `layout.js` untuk struktur HTML yang lebih fleksibel dan layout hierarki.                                                                                    |
| **Komponen Layout**     | Tidak berlaku                                                       | Tidak ada layout hierarki; layout diterapkan secara manual di `_app.js`.                                                                                                   | Layout bisa diatur dalam `app/` dengan file `layout.js` untuk nested layout yang lebih fleksibel.                                                                      |
| **Kelebihan**           | Struktur sederhana untuk file dan folder utama proyek               | - Setiap file langsung menjadi route <br> - Cocok untuk proyek sederhana                                                                                                  | - Mendukung nested routing dan layout hierarki <br> - Modular dan fleksibel, mendukung loading dan error handling khusus.                                              |
| **Kekurangan**          | Tidak ada routing atau struktur halaman yang terintegrasi           | - Tidak mendukung layout hierarki secara native <br> - Terbatas untuk kasus sederhana                                                                                     | - Struktur lebih kompleks, cocok untuk proyek yang lebih besar <br> - Membutuhkan pemahaman lebih dalam tentang layout dan nested routing.                             |


---
