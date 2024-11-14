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