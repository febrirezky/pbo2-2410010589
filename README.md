# pbo2-2410010589

=====================================================================================
Jawaban Praktikum 6 Pertemuan 2

Eksperimen 1: Error Koleksi is abstract; cannot be instantiated karena kelas abstract tidak bisa dibuat objeknya dengan new.

Eksperimen 2: Jika ada @Override terjadi error kompilasi karena nama method tidak cocok. Jika @Override dihapus, program berjalan tapi polymorphism denda tidak berfungsi.

Eksperimen 3: Error java.lang.IllegalArgumentException: Judul tidak boleh kosong karena gagal validasi di konstruktor Koleksi.

Eksperimen 4: Melanggar Enkapsulasi karena mengubah status langsung dari luar tanpa lewat method pinjam()/kembalikan().

=====================================================================================
Jawaban G. Pertanyaan Refleksi Pertemuan 3

1. Perbedaan Container & Component: Top-level container: Jendela utama aplikasi yang memiliki bingkai dan judul (Contoh: JFrame).
                                    Intermediate container: Wadah untuk mengelompokkan komponen di dalam jendela (Contoh: JPanel).
                                    Atomic component: Komponen tunggal untuk interaksi pengguna (Contoh: JButton).

2. Alasan buttonGroup sama pada JRadioButton:   Agar pilihan bersifat mutually exclusive (pilihan tunggal), sehingga hanya satu radio button
                                                yang bisa dipilih dalam satu waktu.

3. Memilih JComboBox vs JRadioButton:   JComboBox: Dipilih jika pilihan banyak untuk menghemat ruang layar.
                                        JRadioButton: Dipilih jika pilihan sedikit (2–3 opsi) agar semua pilihan langsung terlihat.
                                
4. Alasan initComponents() tidak boleh diedit manual & lokasi kode tambahan:    initComponents() di-generate otomatis oleh NetBeans dan akan
                                                                                tertimpa ulang saat tab Design diubah.

5. Alasan FlatLightLaf.setup() dipanggil di awal:   Agar tema FlatLaf mendaftar ke sistem Swing sebelum komponen dibuat,
                                                    sehingga tampilan seluruh komponen langsung menggunakan gaya FlatLaf.

====================================================================================
1. Mengapa Null Layout dan Absolute Layout sebaiknya dihindari?
Keduanya memakai posisi dan ukuran piksel yang tetap, misalnya `setBounds(110, 20, 200, 25)`. Akibatnya:
- Isian tidak menyesuaikan saat jendela dilebarkan dan tetap 200 piksel.
- Teks bisa terpotong karena ukuran huruf dan skala layar berbeda di setiap laptop.
- Absolute Layout membutuhkan library tambahan NetBeans, sehingga aplikasi sulit dijalankan di komputer lain.

Layout manager menghitung posisi dan ukuran komponen secara otomatis mengikuti ukuran jendela.

2. Perbedaan perilaku FlowLayout dan GridLayout saat jendela dilebarkan
- FlowLayout menyusun komponen berderet dari kiri ke kanan dengan ukuran aslinya. Komponen tidak ditarik melebar, dan yang tidak muat pindah ke baris berikutnya. Saat jendela dilebarkan, tombol tetap berukuran sama dan hanya muncul ruang kosong. Saat dikecilkan, tombol pindah baris.
- GridLayout membagi ukuran panel rata ke semua sel. Saat jendela dilebarkan, semua sel dan komponen di dalamnya ikut melebar dengan ukuran sama, dan jumlah baris dan kolom tetap.

Karena GridLayout membagi kolom sama besar, kolom label ikut melebar dan isian terdorong jauh ke kanan. Itu sebabnya GridLayout tidak cocok untuk form berisi label dan isian.

3. Fungsi Weight X dan Fill pada constraint GridBagLayout
- Weight X menentukan kolom mana yang mendapat sisa lebar saat jendela dilebarkan. Di form ini, label memakai 0.0 sehingga lebarnya tetap, dan isian memakai 1.0 sehingga kolom isian mengambil semua sisa lebar.
- Fill menentukan apakah komponen memenuhi sel yang ditempatinya. Fill Horizontal membuat isian memenuhi lebar kolomnya.

Kuncinya adalah memakai keduanya bersama pada kolom isian. Weight X 1.0 membuat kolomnya melebar, dan Fill Horizontal membuat isiannya ikut melebar. Hasilnya label tetap dan isian melebar.

4. Mengapa `formPanel` dibungkus `isiPanel` dan diletakkan di North?
Jika `formPanel` langsung diletakkan di Center, ia ditarik mengisi seluruh tinggi saat jendela ditinggikan. Karena semua baris form tidak punya Weight Y, baris-barisnya berkumpul di tengah dan muncul ruang kosong di atas dan bawah.

Dengan `isiPanel` (BorderLayout) sebagai pembungkus dan `formPanel` di North, `formPanel` hanya setinggi isinya. Baris form tetap di atas, dan ruang tambahan menjadi ruang kosong di bawah.

5. Dua prinsip desain di Form Anggota Perpustakaan dan buktinya
- Keselarasan. Semua label berada di kolom 0 dengan Anchor West, dan semua isian di kolom 1, sehingga membentuk garis lurus dari atas ke bawah. Bukti: tangkapan layar ukuran awal dan saat dilebarkan, label tetap sejajar di kiri dan isian sejajar dengan tepi yang sama.
- Kedekatan. Isian yang berkaitan dikelompokkan dengan judul bagian, yaitu Data Anggota (NPM, Nama lengkap, Program studi, Jenis anggota) dan Kontak (Email, Nomor HP, Alamat). Ada jarak atas 16 piksel sebelum judul Kontak. Bukti: tangkapan layar form yang menampilkan dua kelompok terpisah.

Prinsip konsistensi dan urutan yang wajar juga terpenuhi, kalau Anda ingin menjadikannya cadangan jawaban:
- Konsistensi: Insets label selalu 6, 0, 6, 12 dan isian selalu 4, 0, 4, 0.
- Urutan yang wajar: tombol Daftar ada di kanan bawah.

Foto sketsa form dan tabel rancangan Pertemuan 4
1. Sketsa FormAnggotaPerpustakaan
+-----------------------------------------------+
| JFrame : BorderLayout                         |
| +-------------------------------------------+ |
| | NORTH  headerPanel : BoxLayout, Y Axis    | |
| |   judulLabel / keteranganLabel            | |
| +-------------------------------------------+ |
| | CENTER isiPanel : BorderLayout            | |
| |  +-------------------------------------+  | |
| |  | NORTH formPanel : GridBagLayout     |  | |
| |  |  Data Anggota                       |  | |
| |  |  NPM | [____________]               |  | |
| |  |  Nama lengkap | [____________]      |  | |
| |  |  Program studi | [Combo Box v]      |  | |
| |  |  Jenis anggota | (o)Mhs ( )Dosen ( )Umum |
| |  |  Kontak                             |  | |
| |  |  Email | [____]   Nomor HP | [____] |  | |
| |  |  Alamat | [Text Area]               |  | |
| |  |  [ ] Setuju dengan tata tertib      |  | |
| |  +-------------------------------------+  | |
| +-------------------------------------------+ |
| | SOUTH  tombolPanel : FlowLayout, Right    | |
| |                        [Batal] [Daftar]   | |
| +-------------------------------------------+ |
+-----------------------------------------------+
   
5. Saran dari teman (Tahap 4)
Jawaban eksperimen Praktikum 2 dan Praktikum 4, serta saran dari teman pada Tahap 4
Diisi oleh teman yang menilai:

| No | Pemeriksaan | Ya / Belum |
| 1 | Label singkat, jelas, dan sejajar | Ya |
| 2 | Isian dikelompokkan dengan judul bagian | Ya |
| 3 | Placeholder dipakai untuk isian yang punya format | Ya |
| 4 | Komponen sesuai jenis data | Ya |
| 5 | Tombol utama menonjol dan di kanan bawah | Ya |
| 6 | Jarak antar komponen konsisten | Ya |
| 7 | Rapi saat dilebarkan dan ditinggikan | Ya |
| 8 | JFrame Form dan layout manager, bukan Null/Absolute Layout | Ya |

6. Deklarasi penggunaan AI
Saya menggunakan Claude (Anthropic) untuk: (1) menyusun draf tabel rancangan dan sketsa acuan. Hasilnya saya buka di NetBeans, jalankan, dan periksa sendiri; pengamatan pada eksperimen yang berasal dari percobaan saya.
