# pbo2-2410010589

=================================================================================================================
Jawaban Praktikum 6 Pertemuan 2

Eksperimen 1: Error Koleksi is abstract; cannot be instantiated karena kelas abstract tidak bisa dibuat objeknya dengan new.

Eksperimen 2: Jika ada @Override terjadi error kompilasi karena nama method tidak cocok. Jika @Override dihapus, program berjalan tapi polymorphism denda tidak berfungsi.

Eksperimen 3: Error java.lang.IllegalArgumentException: Judul tidak boleh kosong karena gagal validasi di konstruktor Koleksi.

Eksperimen 4: Melanggar Enkapsulasi karena mengubah status langsung dari luar tanpa lewat method pinjam()/kembalikan().

=================================================================================================================
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
