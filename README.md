# LOD_Indonesia
pemetaan dataset-dataset open data di Indonesia ke dalam format RDF


untuk mencoba hasilnya silakan gunakan aplikasi di http://pebbie.org/mashup/rml

+ klik pada tombol "Load RML" di kiri atas halaman hingga muncul dialog

+ masukkan raw github url dari file .rml.ttl yang ingin dicoba (contoh: https://github.com/pebbie/LOD_Indonesia/raw/master/data.go.id/data-bongkar-dan-muat-barang-melalui-jalur-transportasi-laut.rml.ttl)

+ setelah berhasil dimuat, klik pada tab "Output", lalu klik tombol "Run RML"
+ Simpan data RDF dengan klik pada tombol "Save RDF"

catatan:
beberapa bagian dari spesifikasi RML belum didukung oleh editor visual tersebut sehingga akan ada bagian yang hilang (rr:termType pada node rr:objectMap). Untuk mengantisipasi hal ini, langsung saja salin isi file .rml.ttl ke tab "Output" bagian "RML Output".

## Integrasi mashup pada platform LinkedWidget (eksperimental)

+ setelah file rml berhasil dimuat, klik pada tombol "Export as Linked Widget" di kiri atas halaman. Selanjutnya jendela peramban baru akan terbuka. 
+ Salin alamat halaman yang baru ke Clipboard.
+ buka situs http://linkedwidgets.org
+ isikan alamat yang telah disalin pada Dialog "Quick Mashup" di pojok kanan bawah halaman (di kotak isian Url). jangan lupa isi kotak isian "Name". lalu klik tombol bergambar "+"
+ pilih widget lain dari koleksi (misal "JSON Viewer") yang dibutuhkan lalu klik pada tautan "Quick Mashup"
+ drag-and-drop widget baru dari sisi kiri halaman, lalu hubungkan port dengan menarik (drag-drop) "kabel"
+ klik "Run" pada widget "JSON Viewer", lalu tunggu sejenak.