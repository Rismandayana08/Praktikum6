# Praktikum 6
## Hasil Input 
```python
data_mahasiswa = {}

def lihat_data():
    if not data_mahasiswa:
        print("Daftar Nilai")
        print("=" * 81)
        print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
        print("=" * 81)
        print(f"{'TIDAK ADA DATA'.center(75)}")
        print("=" * 81)
        return
    print("Daftar Nilai")
    print("=" * 81)
    print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
    print("=" * 81)
    for i, (nim, mhs) in enumerate(data_mahasiswa.items(), start=1):
        print(f"{str(i).center(5)}|{mhs['nama'].ljust(15)}|{nim.center(10)}|{str(mhs['tugas']).center(13)}|{str(mhs['uts']).center(10)}|{str(mhs['uas']).center(10)}|{format(mhs['nilai_akhir'], '.2f').center(10)} |")
    print("=" * 81)

def tambah_data():
    print("Tambah Data")
    nim = input("NIM: ")
    if nim in data_mahasiswa:
        print("Data dengan NIM tersebut sudah ada!")
        return
    nama = input("Nama: ")
    tugas = float(input("Nilai Tugas: "))
    uts = float(input("Nilai UTS: "))
    uas = float(input("Nilai UAS: "))
    nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)

    data_mahasiswa[nim] = {
        "nama": nama,
        "tugas": tugas,
        "uts": uts,
        "uas": uas,
        "nilai_akhir": nilai_akhir
    }
    print("Data berhasil ditambahkan!")

def ubah_data():
    lihat_data()
    if not data_mahasiswa:
        return
    
    nim = input("Masukkan NIM data yang akan diubah: ")
    if nim in data_mahasiswa:
        print("Masukkan Data Baru")
        nama = input("Nama: ")
        tugas = float(input("Nilai Tugas: "))
        uts = float(input("Nilai UTS: "))
        uas = float(input("Nilai UAS: "))
        nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)

        data_mahasiswa[nim] = {
            "nama": nama,
            "tugas": tugas,
            "uts": uts,
            "uas": uas,
            "nilai_akhir": nilai_akhir
        }
        print("Data berhasil diubah!")
    else:
        print("NIM tidak ditemukan!")

def hapus_data():
    lihat_data()
    if not data_mahasiswa:
        return

    nim = input("Masukkan NIM data yang akan dihapus: ")
    if nim in data_mahasiswa:
        del data_mahasiswa[nim]
        print("Data berhasil dihapus!")
    else:
        print("NIM tidak ditemukan!")

def cari_data():
    keyword = input("Masukkan nama atau NIM yang ingin dicari: ")
    hasil_cari = {nim: mhs for nim, mhs in data_mahasiswa.items() if keyword.lower() in mhs['nama'].lower() or keyword in nim}
    
    if hasil_cari:
        print("Hasil Pencarian:")
        print("=" * 81)
        print(f"{'No'.center(5)}|{'Nama'.center(15)}|{'NIM'.center(10)}|{'Nilai Tugas'.center(13)}|{'Nilai UTS'.center(10)}|{'Nilai UAS'.center(10)}|{'Nilai Akhir'.center(10)}|")
        print("=" * 81)
        for i, (nim, mhs) in enumerate(hasil_cari.items(), start=1):
            print(f"{str(i).center(5)}|{mhs['nama'].ljust(15)}|{nim.center(10)}|{str(mhs['tugas']).center(13)}|{str(mhs['uts']).center(10)}|{str(mhs['uas']).center(10)}|{format(mhs['nilai_akhir'], '.2f').center(10)}|")
        print("=" * 81)
    else:
        print("Data tidak ditemukan.")

while True:
    pilihan = input("[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : ").lower()
    if pilihan == 't':
        tambah_data()
    elif pilihan == 'u':
        ubah_data()
    elif pilihan == 'h':
        hapus_data()
    elif pilihan == 'l':
        lihat_data()
    elif pilihan == 'c':
        cari_data()
    elif pilihan == 'k':
        print("Program selesai.")
        break
    else:
        print("Pilihan tidak valid!")
```

# Hasil Output
````markdown
[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : t
Tambah Data
NIM: 312410015
Nama: Aldi Rismandayana
Nilai Tugas: 89
Nilai UTS: 89
Nilai UAS: 90
Data berhasil ditambahkan!
[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : l
Daftar Nilai
=================================================================================
  No |      Nama     |   NIM    | Nilai Tugas |Nilai UTS |Nilai UAS |Nilai Akhir|
=================================================================================
  1  |Aldi Rismandayana|312410015 |     89.0    |   89.0   |   90.0   |  89.35    |
=================================================================================
[(L)ihat (T)ambah (U)bah (H)apus (C)ari (K)eluar] : k
Program selesai.
````
# Flowchart
 ![Flowchart](/flowchart.png)
# Penjelasan Program
Kode Python di atas dirancang untuk mengelola data mahasiswa dalam bentuk kamus (dictionary). Setiap entri dalam kamus mewakili satu mahasiswa dengan NIM sebagai kunci dan informasi lainnya (nama, nilai tugas, UTS, UAS, dan nilai akhir) sebagai nilai.

Pemahaman Fungsi-Fungsi Utama
lihat_data():

Fungsi ini menampilkan daftar seluruh data mahasiswa yang sudah tersimpan.
Jika belum ada data, akan ditampilkan pesan "TIDAK ADA DATA".
Format tampilan data dibuat rapi dengan menggunakan pemisah garis dan penjajaran kolom.
tambah_data():

Fungsi ini menambahkan data mahasiswa baru.
User diminta memasukkan NIM, nama, nilai tugas, UTS, dan UAS.
Nilai akhir dihitung berdasarkan bobot masing-masing komponen nilai.
Data baru kemudian ditambahkan ke dalam kamus data_mahasiswa.
ubah_data():

Fungsi ini mengupdate data mahasiswa yang sudah ada.
User diminta memasukkan NIM mahasiswa yang ingin diubah.
Jika NIM ditemukan, user akan diminta memasukkan data baru untuk mengganti data yang lama.
hapus_data():

Fungsi ini menghapus data mahasiswa berdasarkan NIM.
User diminta memasukkan NIM mahasiswa yang ingin dihapus.
Jika NIM ditemukan, data tersebut akan dihapus dari kamus.
cari_data():

Fungsi ini mencari data mahasiswa berdasarkan nama atau NIM.
User diminta memasukkan kata kunci yang ingin dicari.
Hasil pencarian akan ditampilkan dalam format yang sama seperti fungsi lihat_data().
Struktur Data
data_mahasiswa: Ini adalah kamus utama yang menyimpan seluruh data mahasiswa.
Setiap entri dalam kamus: Mempunyai struktur sebagai berikut:
```Python
{
    "NIM": {
        "nama": "Nama Mahasiswa",
        "tugas": nilai_tugas,
        "uts": nilai_uts,
        "uas": nilai_uas,
        "nilai_akhir": nilai_akhir
    }
}
```
Gunakan kode dengan hati-hati.

# Alur Kerja Program
Program dimulai dengan mendefinisikan fungsi-fungsi yang dibutuhkan.
Kemudian, program masuk ke dalam loop while True untuk terus meminta input dari pengguna.
Pengguna diminta memilih aksi yang ingin dilakukan (lihat, tambah, ubah, hapus, cari, atau keluar).
Berdasarkan pilihan pengguna, fungsi yang sesuai akan dipanggil dan menjalankan tugasnya.
Loop akan terus berulang sampai pengguna memilih opsi "keluar".
## A. Kelebihan Kode
- Terstruktur: Kode terbagi menjadi fungsi-fungsi yang jelas, memudahkan pemahaman dan modifikasi.
- Fleksibel: Dapat digunakan untuk mengelola data mahasiswa dalam jumlah yang banyak.
- User-friendly: Tampilan output yang rapi dan mudah dibaca.
- Komprehensif: Mencakup fitur-fitur dasar untuk manajemen data mahasiswa, seperti tambah, ubah, hapus, dan cari.
## B. Potensi Pengembangan
- Validasi input: Menambahkan validasi input untuk memastikan data yang dimasukkan oleh pengguna sesuai dengan tipe data yang diharapkan (misalnya, NIM harus berupa angka).
- Penyimpanan data: Menyimpan data ke dalam file (misalnya, CSV atau JSON) agar data tidak hilang ketika program dijalankan ulang.
- Fitur tambahan: Menambahkan fitur-fitur lain seperti mengurutkan data berdasarkan nilai akhir, mencari mahasiswa dengan nilai tertentu, atau menghasilkan laporan.
- Antarmuka pengguna: Membuat antarmuka pengguna yang lebih interaktif menggunakan library seperti Tkinter atau PyQt.

