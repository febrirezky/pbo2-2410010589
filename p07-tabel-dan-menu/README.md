# P07 – Tabel, Menu, dan Mini Proyek GUI

Nama / NPM : Febriawan Rezky

## Bagian E. Tugas yang Dikumpulkan

### 1. Tautan repository GitHub
`https://github.com/febrirezky5/pbo2-2410010589`

### 2. Jawaban eksperimen Praktikum 5
| 1 | `fireTableRowsInserted(baris, baris);` dijadikan komentar, lalu tambah kontak baru. Apakah tabel langsung berubah? | **Tidak berubah.** Kontak sudah masuk ke `List` di model, tetapi JTable dan `TableRowSorter` tidak diberi tahu sehingga masih memakai jumlah baris lama. Label status ikut tidak sinkron, misalnya "Menampilkan 5 dari 6 kontak". Baris baru baru tampil setelah ada aksi yang memaksa sorter membaca ulang model, misalnya mengetik di kolom cari. |
| 2 | `barisTerpilih()` diganti `return kontakTable.getSelectedRow();`. Cari "ah", pilih Ahmad Fauzi, klik Hapus, pilih No. Nama siapa yang muncul? | Dialog menampilkan **"Hapus kontak Budi Santoso?"**. Setelah dicari, Ahmad Fauzi ada di baris tampilan 1, sedangkan baris 1 di model adalah Budi Santoso. Nomor baris tampilan dipakai langsung tanpa `convertRowIndexToModel`, sehingga kontak yang salah terambil (jika Yes ditekan, Budi yang terhapus). |
| 3 | `super(pemilik, judul, true)` diubah menjadi `false`. Klik jendela utama saat dialog terbuka. Apa yang terjadi pada kontak yang ditambahkan? | Dialog tidak lagi modal, jadi jendela utama masih bisa diklik. `setVisible(true)` tidak menunggu dialog ditutup, sehingga `tampilkan()` langsung mengembalikan `null`. Akibatnya kontak yang diisi **tidak pernah masuk ke tabel**. |
| 4 | Tekan Ctrl+N, Ctrl+E, Ctrl+D. Mengapa Ctrl+E dan Ctrl+D tidak bekerja saat tidak ada baris dipilih? | Ctrl+N selalu bekerja. `perbaruiTombol()` memanggil `ubahItem.setEnabled(false)` dan `hapusItem.setEnabled(false)` saat tidak ada baris terpilih, dan menu item yang nonaktif tidak menjalankan accelerator-nya. |
| 5 | Ubah accelerator `hapusItem` menjadi Delete tanpa Ctrl. Baris apa yang berubah di `initComponents()`? | Satu baris berubah: `hapusItem.setAccelerator(javax.swing.KeyStroke.getKeyStroke(java.awt.event.KeyEvent.VK_D, java.awt.event.InputEvent.CTRL_DOWN_MASK));` menjadi `hapusItem.setAccelerator(javax.swing.KeyStroke.getKeyStroke(java.awt.event.KeyEvent.VK_DELETE, 0));` (`VK_D` menjadi `VK_DELETE`, `CTRL_DOWN_MASK` menjadi `0`). |
| 6 | Atribut `private KontakTableModel model;` lalu `model = new KontakTableModel();` setelah `initComponents()`. Pesan error apa yang muncul dan mengapa? | Aplikasi gagal dibuka dengan `java.lang.IllegalArgumentException: Cannot set a null TableModel`. `initComponents()` dipanggil di awal konstruktor dan menjalankan `kontakTable.setModel(model);`, padahal `model` masih `null` karena baru dibuat setelahnya. |

### 3. Video demo
Tautan video demo mini proyek (maks. 3 menit): [<video controls src="Video Demo Mini Proyek.mp4" title="Demo mini proyek"></video>](https://github.com/user-attachments/assets/1135f08e-3d02-4dc2-9fba-c9008ff84e9c)
