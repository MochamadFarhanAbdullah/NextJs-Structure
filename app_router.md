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