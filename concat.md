# Materi Struktur File di Next.js

Di Next.js, struktur file berperan besar dalam mengatur dan mengembangkan aplikasi web. Mari kita bahas tiga topik penting: **Top-level**, **Pages Router**, dan **App Router**.

## A. Top-level Struktur File di Next.js

### 1. Top-level Folder
Di Next.js, folder utama dalam proyek biasanya berisi beberapa folder penting untuk mengatur halaman dan pengaturan aplikasi. Beberapa folder yang sering dijumpai meliputi:

- **app/ (Jika menggunakan App Router)**: Folder ini ada jika kamu menggunakan App Router. Di sini, semua file halaman untuk App Router disimpan.
- **pages/ (Jika menggunakan Pages Router)**:Folder ini digunakan kalau kamu pakai Pages Router. Di sini, file-file halaman disimpan dan otomatis bisa diakses pengguna.
- **public/**: Folder ini menyimpan file statis, seperti gambar, CSS, atau JavaScript, yang langsung bisa diakses oleh browser.
- **styles/**: Folder untuk menyimpan file CSS atau file styling global.
- **node_modules/**: Folder yang berisi dependensi proyek.
- **components/** (opsional): Menyimpan komponen React yang bisa digunakan di beberapa halaman.
- **lib/** (opsional): Tempat menyimpan fungsi utilitas atau kode umum lainnya.

### 2. Top-level Files
Di folder Top-level , da beberapa file penting yang perlu kamu ketahui:

- **package.json**: File konfigurasi untuk manajemen dependensi dan pengaturan aplikasi.
- **next.config.js**: File untuk mengatur konfigurasi Next.js, seperti pengaturan server atau build.
- **tsconfig.json** (jika menggunakan TypeScript): File untuk mengatur TypeScript di proyek.
- **.gitignore**: Menentukan file atau folder yang diabaikan oleh Git.

---

## B. Pages Router

Pages Router adalah cara tradisional Next.js dalam mengatur rute (route) dengan file. Jadi, setiap file di folder pages/ akan otomatis menjadi route di aplikasi.

### 1. Struktur File Pages Router
Misalnya, jika kamu memilih menggunakan Pages Router, maka proyekmu akan memiliki folder :
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
Ada beberapa file khusus di Pages Router yang memiliki fungsi spesial:

- **_app.js / _app.tsx**: Ini adalah tempat untuk inisialisasi global, seperti layout atau provider
- **_document.js / _document.tsx**: Digunakan untuk kustomisasi HTML di aplikasi, misalnya menambahkan font.
- **index.js / index.tsx**: Berfungsi sebagai entry point atau halaman utama untuk rute / dari aplikasi.

---

## C. App Router

**App Router** adalah jenis routing terbaru yang disediakan oleh Next.js versi 13. Router jenis ini menggunakan top-level folder `app/`. Jadi, semua halaman dalam aplikasi disimpan di dalam folder tersebut.

### 1. **Struktur File App Router**
Struktur file di **App Router** hampir mirip dengan Pages Router, tetapi menggunakan penamaan berbeda untuk halaman utamanya.

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
Sama seperti _Pages Router_, _App Router_ juga memiliki file-file khusus atau spesial di dalam top-level folder `app/`. Berikut adalah file-file penting yang harus diketahui:

- **`layout.js / layout.tsx`**, yaitu file layout
- **`page.js / page.tsx`**, yaitu file utama yang pertama kali diakses
- **`loading.js / loading.tsx`**, yaitu file untuk menghandle halaman loading
- **`error.js / error.tsx`**, yaitu file untuk menghandle halaman ketika terjadi error

Adapun file-file seperti `not-found.js`, `global-error.js`, dan lain-lain.


# Kesimpulan

Tabel berikut merangkum **Struktur Top-level**, **Pages Router**, dan **App Router** di Next.js.

| **Kategori**                 | **Deskripsi**                                                                                                                                                                                                                                                                                                                                                                       |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Top-level Struktur File**  | Struktur utama proyek Next.js memiliki beberapa folder utama, antara lain:                                                                                                                                                                                                                                                                                                           |
| **Folder Utama**             | - `app/` (untuk App Router) atau `pages/` (untuk Pages Router): Menyimpan file halaman aplikasi.<br> - `public/`: Menyimpan file statis, seperti gambar atau CSS.<br> - `styles/`: Menyimpan file untuk styling global.<br> - `node_modules/`: Folder untuk dependensi proyek.<br> - `components/` (opsional): Menyimpan komponen React.<br> - `lib/` (opsional): Folder untuk fungsi atau utilitas umum. |
| **File Utama**               | - `package.json`: Mengelola dependensi dan pengaturan aplikasi.<br> - `next.config.js`: Mengonfigurasi Next.js.<br> - `tsconfig.json` (jika menggunakan TypeScript): File konfigurasi untuk TypeScript.<br> - `.gitignore`: Menentukan file/folder yang diabaikan oleh Git.                                                                                                          |
| **Pages Router**             | Sistem routing berbasis file di folder `pages/`. Setiap file dalam folder ini menjadi URL di aplikasi.                                                                                                                                                                                                                                                                               |
| **Struktur Folder Pages**    | - `pages/`: Folder untuk halaman yang diakses pengguna.<br> - `styles/`: Folder untuk styling aplikasi.                                                                                                                                                                                                                                                                              |
| **Contoh Struktur Pages**    | - `pages/index.js`: Halaman utama, URL: `/`<br> - `pages/about.js`: Halaman about, URL: `/about`<br> - `pages/products/index.js`: Halaman daftar produk, URL: `/products`<br> - `pages/products/[id].js`: Halaman produk dinamis, URL: `/products/:id`                                                                                                                            |
| **File Khusus Pages Router** | - `_app.js` atau `_app.tsx`: Inisialisasi global atau layout aplikasi.<br> - `_document.js` atau `_document.tsx`: Kustomisasi struktur HTML.<br> - `index.js` atau `index.tsx`: Entry point untuk halaman utama `/`.                                                                                                                          |
| **App Router**               | Sistem routing baru di Next.js (v13), menggunakan folder `app/` sebagai top-level.                                                                                                                                                                                                                                                                                                   |
| **Struktur Folder App**      | - `app/page.js`: Halaman utama, URL: `/`<br> - `app/products/page.js`: Halaman daftar produk, URL: `/products`<br> - `app/chat/[slug]/page.js`: Halaman dinamis untuk URL `/chat/:slug`.                                                                                                                                                                                            |
| **File Khusus App Router**   | - `layout.js` atau `layout.tsx`: Untuk layout global.<br> - `page.js` atau `page.tsx`: File halaman utama.<br> - `loading.js` atau `loading.tsx`: Untuk halaman loading.<br> - `error.js` atau `error.tsx`: Untuk menangani error.<br> - `not-found.js`: Untuk halaman 404 atau "not found".                                                   |
