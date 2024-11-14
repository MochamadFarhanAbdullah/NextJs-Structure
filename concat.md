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

# Struktur File di Next.js

Tabel berikut memberikan ringkasan mengenai **Top-level Struktur File**, **Pages Router**, dan **App Router** di Next.js.

| **Kategori**                  | **Deskripsi**                                                                                                                                                                                                                                                                                                                                                                    |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Top-level Struktur File**   | Top-level struktur pada proyek Next.js memiliki folder utama seperti:                                                                                                                                                                                                                                                                                                             |
| **Folder Utama**              | - `app/` (untuk App Router) atau `pages/` (untuk Pages Router): Menyimpan file halaman aplikasi.<br> - `public/`: Menyimpan file statis seperti gambar atau CSS.<br> - `styles/`: Menyimpan file styling global.<br> - `node_modules/`: Menyimpan dependensi proyek.<br> - `components/` (opsional): Menyimpan komponen React yang digunakan.<br> - `lib/` (opsional): Menyimpan fungsi utilitas yang umum digunakan. |
| **File Utama**                | - `package.json`: Mengelola dependensi dan pengaturan aplikasi.<br> - `next.config.js`: Mengonfigurasi Next.js.<br> - `tsconfig.json` (jika menggunakan TypeScript): File konfigurasi TypeScript.<br> - `.gitignore`: Daftar file/folder yang diabaikan oleh Git.                                                                                                           |
| **Pages Router**              | Sistem routing berdasarkan file dalam folder `pages/`. Setiap file dalam folder ini menjadi URL pada aplikasi.                                                                                                                                                                                                                                                                     |
| **Struktur Folder**           | - `pages/`: Menyimpan halaman-halaman aplikasi berbasis URL.<br> - `styles/`: Folder styling aplikasi.                                                                                                                                                                                                                                                                            |
| **Contoh Struktur**           | - `pages/index.js`: Halaman utama, URL: `/`<br> - `pages/about.js`: Halaman about, URL: `/about`<br> - `pages/products/index.js`: Halaman daftar produk, URL: `/products`<br> - `pages/products/[id].js`: Halaman produk dinamis, URL: `/products/:id`                                                                                                                         |
| **File Khusus Pages Router**  | - `_app.js` atau `_app.tsx`: Untuk inisialisasi global atau layout aplikasi.<br> - `_document.js` atau `_document.tsx`: Untuk kustomisasi struktur HTML.<br> - `index.js` atau `index.tsx`: Entry point untuk halaman utama `/`.                                                                                                                                              |
| **App Router**                | Sistem routing baru dari Next.js (versi 13) menggunakan folder `app/` sebagai top-level folder.                                                                                                                                                                                                                                                                                    |
| **Struktur Folder App Router**| - `app/page.js`: Halaman utama, URL: `/`<br> - `app/products/page.js`: Halaman daftar produk, URL: `/products`<br> - `app/chat/[slug]/page.js`: Halaman dinamis untuk URL `/chat/:slug`.                                                                                                                                                                                          |
| **File Khusus App Router**    | - `layout.js` atau `layout.tsx`: Untuk layout aplikasi.<br> - `page.js` atau `page.tsx`: File utama yang pertama diakses.<br> - `loading.js` atau `loading.tsx`: Untuk halaman loading.<br> - `error.js` atau `error.tsx`: Untuk menangani halaman error.<br> - `not-found.js`: Untuk menangani halaman not found.                                                                |

Tabel ini memberikan panduan singkat tentang struktur file di Next.js untuk Pages Router dan App Router, termasuk folder utama, file penting, dan peran masing-masing dalam aplikasi.
