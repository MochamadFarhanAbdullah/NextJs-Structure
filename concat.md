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

---
