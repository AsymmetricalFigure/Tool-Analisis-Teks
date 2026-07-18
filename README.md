# Tool-Analisis-Teks
Kelompok 5, consisting Muhammad Husain and Irsyad Mulyahida Yanto
---

Proposal:

Coding:

```python
"""
============================================================
                    TOOL ANALISIS TEKS
============================================================

Deskripsi:
Program sederhana untuk menganalisis sebuah teks.

Fitur:
1. Menghitung jumlah karakter.
2. Menghitung jumlah kata.
3. Menghitung jumlah kalimat.
4. Menghitung frekuensi kata.
5. Menampilkan kata paling sering digunakan.
6. Melakukan analisis sentimen sederhana.
7. Menampilkan kata positif dan negatif yang ditemukan.

Program ini hanya menggunakan library bawaan Python.
============================================================
"""

import re
import string
from collections import Counter


# ==========================================================
# KONFIGURASI PROGRAM
# ==========================================================

NAMA_PROGRAM = "Tool Analisis Teks"
VERSI_PROGRAM = "1.0"


# Daftar kata yang dianggap memiliki sentimen positif.
KATA_POSITIF = {
    "baik",
    "bagus",
    "hebat",
    "senang",
    "bahagia",
    "suka",
    "cinta",
    "indah",
    "ramah",
    "sukses",
    "berhasil",
    "menarik",
    "nyaman",
    "aman",
    "cepat",
    "mudah",
    "keren",
    "mantap",
    "puas",
    "positif",
    "bermanfaat",
    "membantu",
    "terbaik",
    "unggul",
    "cerdas",
    "menyenangkan",
    "gembira",
    "optimis",
    "bersih",
    "rapi",
    "murah",
    "lezat",
    "enak",
    "favorit",
    "jujur",
    "setia",
    "semangat",
    "berkualitas",
    "rekomendasi",
    "luar biasa",
    "terima kasih",
    "good",
    "great",
    "excellent",
    "amazing",
    "happy",
    "wonderful",
    "perfect",
    "awesome",
    "love",
}


# Daftar kata yang dianggap memiliki sentimen negatif.
KATA_NEGATIF = {
    "buruk",
    "jelek",
    "sedih",
    "marah",
    "benci",
    "kecewa",
    "gagal",
    "sulit",
    "lambat",
    "mahal",
    "rusak",
    "masalah",
    "berbahaya",
    "takut",
    "menakutkan",
    "menyebalkan",
    "bodoh",
    "lemah",
    "parah",
    "kacau",
    "negatif",
    "menyesal",
    "menyedihkan",
    "membosankan",
    "bosan",
    "kasar",
    "kotor",
    "ribet",
    "sakit",
    "hancur",
    "payah",
    "sampah",
    "tipu",
    "bohong",
    "terburuk",
    "menjijikkan",
    "aneh",
    "error",
    "bug",
    "tidak nyaman",
    "tidak aman",
    "bad",
    "terrible",
    "awful",
    "sad",
    "angry",
    "hate",
    "disappointed",
    "worst",
    "horrible",
}


# Stopword adalah kata umum yang tidak terlalu penting
# dalam perhitungan frekuensi kata.
STOPWORDS = {
    "yang",
    "dan",
    "di",
    "ke",
    "dari",
    "ini",
    "itu",
    "untuk",
    "dengan",
    "pada",
    "adalah",
    "sebagai",
    "atau",
    "karena",
    "juga",
    "saya",
    "aku",
    "kamu",
    "dia",
    "mereka",
    "kami",
    "kita",
    "ada",
    "akan",
    "sudah",
    "belum",
    "bisa",
    "dapat",
    "dalam",
    "oleh",
    "sebuah",
    "suatu",
    "sangat",
    "lebih",
    "kurang",
    "namun",
    "tetapi",
    "jadi",
    "jika",
    "kalau",
    "saat",
    "ketika",
    "apa",
    "siapa",
    "bagaimana",
    "mengapa",
    "dimana",
    "mana",
    "pun",
    "lah",
    "nya",
    "the",
    "a",
    "an",
    "and",
    "or",
    "is",
    "are",
    "was",
    "were",
    "to",
    "of",
    "in",
    "on",
    "for",
    "with",
    "this",
    "that",
}


# ==========================================================
# FUNGSI TAMPILAN
# ==========================================================

def tampilkan_garis(panjang=60):
    """
    Menampilkan garis pembatas.
    """
    print("=" * panjang)


def tampilkan_judul():
    """
    Menampilkan judul program.
    """
    tampilkan_garis()
    print(NAMA_PROGRAM.center(60))
    print(f"Versi {VERSI_PROGRAM}".center(60))
    tampilkan_garis()


def tampilkan_menu():
    """
    Menampilkan menu utama.
    """
    print()
    print("MENU UTAMA")
    print("-" * 60)
    print("1. Analisis teks")
    print("2. Lihat daftar kata sentimen")
    print("3. Keluar")
    print("-" * 60)


# ==========================================================
# FUNGSI PEMROSESAN TEKS
# ==========================================================

def bersihkan_spasi(teks):
    """
    Menghapus spasi berlebihan dari teks.
    """
    teks_bersih = re.sub(r"\s+", " ", teks)

    return teks_bersih.strip()


def ubah_ke_huruf_kecil(teks):
    """
    Mengubah teks menjadi huruf kecil.
    """
    return teks.lower()


def hapus_tanda_baca(teks):
    """
    Menghapus tanda baca dari teks.
    """
    tabel_tanda_baca = str.maketrans(
        "",
        "",
        string.punctuation
    )

    return teks.translate(tabel_tanda_baca)


def ambil_daftar_kata(teks):
    """
    Memisahkan teks menjadi daftar kata.
    """
    teks = ubah_ke_huruf_kecil(teks)

    daftar_kata = re.findall(
        r"\b[a-zA-ZÀ-ÿ0-9]+\b",
        teks
    )

    return daftar_kata


def ambil_kata_penting(teks):
    """
    Mengambil kata yang bukan stopword.
    """
    semua_kata = ambil_daftar_kata(teks)

    kata_penting = []

    for kata in semua_kata:
        if kata not in STOPWORDS and len(kata) > 1:
            kata_penting.append(kata)

    return kata_penting


def ambil_daftar_kalimat(teks):
    """
    Memisahkan teks menjadi beberapa kalimat.

    Pemisahan dilakukan berdasarkan tanda:
    - Titik
    - Tanda tanya
    - Tanda seru
    """
    hasil_pemisahan = re.split(r"[.!?]+", teks)

    daftar_kalimat = []

    for kalimat in hasil_pemisahan:
        kalimat = kalimat.strip()

        if kalimat:
            daftar_kalimat.append(kalimat)

    return daftar_kalimat


# ==========================================================
# FITUR 1: MENGHITUNG JUMLAH KARAKTER
# ==========================================================

def hitung_jumlah_karakter(teks):
    """
    Menghitung jumlah seluruh karakter.

    Spasi dan tanda baca ikut dihitung.
    """
    return len(teks)


def hitung_karakter_tanpa_spasi(teks):
    """
    Menghitung jumlah karakter tanpa spasi.
    """
    teks_tanpa_spasi = teks.replace(" ", "")
    teks_tanpa_spasi = teks_tanpa_spasi.replace("\n", "")
    teks_tanpa_spasi = teks_tanpa_spasi.replace("\t", "")

    return len(teks_tanpa_spasi)


# ==========================================================
# FITUR 2: MENGHITUNG JUMLAH KATA
# ==========================================================

def hitung_jumlah_kata(teks):
    """
    Menghitung jumlah kata dalam teks.
    """
    daftar_kata = ambil_daftar_kata(teks)

    return len(daftar_kata)


def hitung_jumlah_kata_unik(teks):
    """
    Menghitung jumlah kata yang berbeda.

    Fungsi ini hanya menjadi informasi tambahan
    dalam bagian jumlah kata.
    """
    daftar_kata = ambil_daftar_kata(teks)

    kata_unik = set(daftar_kata)

    return len(kata_unik)


# ==========================================================
# FITUR 3: MENGHITUNG JUMLAH KALIMAT
# ==========================================================

def hitung_jumlah_kalimat(teks):
    """
    Menghitung jumlah kalimat dalam teks.
    """
    daftar_kalimat = ambil_daftar_kalimat(teks)

    return len(daftar_kalimat)


# ==========================================================
# FITUR 4: MENGHITUNG FREKUENSI KATA
# ==========================================================

def hitung_frekuensi_kata(teks, hapus_stopword=True):
    """
    Menghitung frekuensi setiap kata.

    Parameter hapus_stopword:
    True:
        Kata umum seperti 'dan', 'yang', dan 'di'
        tidak ikut dihitung.

    False:
        Seluruh kata ikut dihitung.
    """
    if hapus_stopword:
        daftar_kata = ambil_kata_penting(teks)
    else:
        daftar_kata = ambil_daftar_kata(teks)

    frekuensi = Counter(daftar_kata)

    return frekuensi


def tampilkan_semua_frekuensi(teks):
    """
    Menampilkan seluruh frekuensi kata penting.
    """
    frekuensi = hitung_frekuensi_kata(
        teks,
        hapus_stopword=True
    )

    print()
    print("D. FREKUENSI SELURUH KATA")
    print("-" * 60)

    if not frekuensi:
        print("Tidak ada kata yang dapat dihitung.")
        return

    frekuensi_terurut = sorted(
        frekuensi.items(),
        key=lambda data: (-data[1], data[0])
    )

    for nomor, data in enumerate(frekuensi_terurut, start=1):
        kata, jumlah = data

        print(
            f"{nomor:>3}. "
            f"{kata:<20} "
            f"{jumlah:>3} kali"
        )


# ==========================================================
# FITUR 5: MENAMPILKAN KATA PALING SERING
# ==========================================================

def ambil_kata_tersering(teks, jumlah=10):
    """
    Mengambil beberapa kata yang paling sering muncul.
    """
    frekuensi = hitung_frekuensi_kata(
        teks,
        hapus_stopword=True
    )

    return frekuensi.most_common(jumlah)


def buat_batang_frekuensi(jumlah, panjang_maksimal=30):
    """
    Membuat batang frekuensi sederhana menggunakan simbol #.
    """
    panjang_batang = min(jumlah, panjang_maksimal)

    return "#" * panjang_batang


def tampilkan_kata_tersering(teks, jumlah=10):
    """
    Menampilkan kata yang paling sering digunakan.
    """
    kata_tersering = ambil_kata_tersering(
        teks,
        jumlah
    )

    print()
    print("E. KATA PALING SERING DIGUNAKAN")
    print("-" * 60)

    if not kata_tersering:
        print("Tidak ada kata yang dapat ditampilkan.")
        return

    for nomor, data in enumerate(kata_tersering, start=1):
        kata, frekuensi = data

        batang = buat_batang_frekuensi(frekuensi)

        print(
            f"{nomor:>2}. "
            f"{kata:<20} "
            f"{frekuensi:>3} kali | "
            f"{batang}"
        )


# ==========================================================
# FITUR 6: ANALISIS SENTIMEN SEDERHANA
# ==========================================================

def cari_frasa_sentimen(teks, daftar_sentimen):
    """
    Mencari kata sentimen yang terdiri dari lebih dari satu kata.

    Contoh:
    - luar biasa
    - terima kasih
    - tidak nyaman
    - tidak aman
    """
    teks_kecil = ubah_ke_huruf_kecil(teks)

    frasa_ditemukan = []

    for kata in daftar_sentimen:
        if " " in kata:
            pola = r"\b" + re.escape(kata) + r"\b"

            jumlah = len(
                re.findall(pola, teks_kecil)
            )

            for _ in range(jumlah):
                frasa_ditemukan.append(kata)

    return frasa_ditemukan


def analisis_sentimen(teks):
    """
    Menganalisis sentimen teks berdasarkan kata positif
    dan kata negatif.

    Skor:
    - Kata positif bernilai +1.
    - Kata negatif bernilai -1.
    """
    daftar_kata = ambil_daftar_kata(teks)

    kata_positif_ditemukan = []
    kata_negatif_ditemukan = []

    for kata in daftar_kata:
        if kata in KATA_POSITIF:
            kata_positif_ditemukan.append(kata)

        if kata in KATA_NEGATIF:
            kata_negatif_ditemukan.append(kata)

    frasa_positif = cari_frasa_sentimen(
        teks,
        KATA_POSITIF
    )

    frasa_negatif = cari_frasa_sentimen(
        teks,
        KATA_NEGATIF
    )

    kata_positif_ditemukan.extend(frasa_positif)
    kata_negatif_ditemukan.extend(frasa_negatif)

    jumlah_positif = len(kata_positif_ditemukan)
    jumlah_negatif = len(kata_negatif_ditemukan)

    skor_sentimen = jumlah_positif - jumlah_negatif

    if skor_sentimen > 0:
        kategori = "POSITIF"

    elif skor_sentimen < 0:
        kategori = "NEGATIF"

    else:
        kategori = "NETRAL"

    total_kata_sentimen = jumlah_positif + jumlah_negatif

    if total_kata_sentimen == 0:
        persentase_positif = 0
        persentase_negatif = 0

    else:
        persentase_positif = (
            jumlah_positif
            / total_kata_sentimen
            * 100
        )

        persentase_negatif = (
            jumlah_negatif
            / total_kata_sentimen
            * 100
        )

    hasil = {
        "kategori": kategori,
        "skor": skor_sentimen,
        "jumlah_positif": jumlah_positif,
        "jumlah_negatif": jumlah_negatif,
        "persentase_positif": persentase_positif,
        "persentase_negatif": persentase_negatif,
        "kata_positif": kata_positif_ditemukan,
        "kata_negatif": kata_negatif_ditemukan,
    }

    return hasil


# ==========================================================
# FITUR 7: MENAMPILKAN KATA POSITIF DAN NEGATIF
# ==========================================================

def tampilkan_kata_sentimen_ditemukan(hasil_sentimen):
    """
    Menampilkan kata positif dan negatif yang ditemukan.
    """
    print()
    print("G. KATA SENTIMEN YANG DITEMUKAN")
    print("-" * 60)

    kata_positif = hasil_sentimen["kata_positif"]
    kata_negatif = hasil_sentimen["kata_negatif"]

    print("Kata positif:")

    if kata_positif:
        frekuensi_positif = Counter(kata_positif)

        for kata, jumlah in frekuensi_positif.most_common():
            print(f"- {kata}: {jumlah} kali")

    else:
        print("- Tidak ada kata positif yang ditemukan.")

    print()
    print("Kata negatif:")

    if kata_negatif:
        frekuensi_negatif = Counter(kata_negatif)

        for kata, jumlah in frekuensi_negatif.most_common():
            print(f"- {kata}: {jumlah} kali")

    else:
        print("- Tidak ada kata negatif yang ditemukan.")


# ==========================================================
# FUNGSI INPUT
# ==========================================================

def input_teks_multibaris():
    """
    Menerima input teks lebih dari satu baris.

    Untuk mengakhiri input, pengguna harus mengetik:
    SELESAI
    """
    print()
    print("Masukkan teks yang ingin dianalisis.")
    print("Ketik SELESAI pada baris baru untuk menyelesaikan input.")
    print("-" * 60)

    kumpulan_baris = []

    while True:
        baris = input()

        if baris.strip().upper() == "SELESAI":
            break

        kumpulan_baris.append(baris)

    teks = "\n".join(kumpulan_baris)

    return teks.strip()


# ==========================================================
# FUNGSI LAPORAN ANALISIS
# ==========================================================

def tampilkan_statistik_dasar(teks):
    """
    Menampilkan statistik dasar teks.
    """
    jumlah_karakter = hitung_jumlah_karakter(teks)
    karakter_tanpa_spasi = hitung_karakter_tanpa_spasi(teks)
    jumlah_kata = hitung_jumlah_kata(teks)
    jumlah_kata_unik = hitung_jumlah_kata_unik(teks)
    jumlah_kalimat = hitung_jumlah_kalimat(teks)

    print()
    tampilkan_garis()
    print("HASIL ANALISIS TEKS".center(60))
    tampilkan_garis()

    print()
    print("A. JUMLAH KARAKTER")
    print("-" * 60)
    print(f"Jumlah karakter            : {jumlah_karakter}")
    print(f"Karakter tanpa spasi       : {karakter_tanpa_spasi}")

    print()
    print("B. JUMLAH KATA")
    print("-" * 60)
    print(f"Jumlah seluruh kata        : {jumlah_kata}")
    print(f"Jumlah kata unik           : {jumlah_kata_unik}")

    print()
    print("C. JUMLAH KALIMAT")
    print("-" * 60)
    print(f"Jumlah kalimat             : {jumlah_kalimat}")


def tampilkan_hasil_sentimen(hasil_sentimen):
    """
    Menampilkan hasil utama analisis sentimen.
    """
    print()
    print("F. HASIL ANALISIS SENTIMEN")
    print("-" * 60)

    print(
        f"Kategori sentimen          : "
        f"{hasil_sentimen['kategori']}"
    )

    print(
        f"Skor sentimen              : "
        f"{hasil_sentimen['skor']}"
    )

    print(
        f"Jumlah kata positif        : "
        f"{hasil_sentimen['jumlah_positif']}"
    )

    print(
        f"Jumlah kata negatif        : "
        f"{hasil_sentimen['jumlah_negatif']}"
    )

    print(
        f"Persentase positif         : "
        f"{hasil_sentimen['persentase_positif']:.2f}%"
    )

    print(
        f"Persentase negatif         : "
        f"{hasil_sentimen['persentase_negatif']:.2f}%"
    )


def tampilkan_kesimpulan(hasil_sentimen):
    """
    Menampilkan kesimpulan berdasarkan kategori sentimen.
    """
    kategori = hasil_sentimen["kategori"]

    print()
    print("KESIMPULAN")
    print("-" * 60)

    if kategori == "POSITIF":
        print(
            "Teks cenderung memiliki sentimen positif karena "
            "kata positif lebih banyak daripada kata negatif."
        )

    elif kategori == "NEGATIF":
        print(
            "Teks cenderung memiliki sentimen negatif karena "
            "kata negatif lebih banyak daripada kata positif."
        )

    else:
        print(
            "Teks memiliki sentimen netral karena jumlah kata "
            "positif dan negatif sama atau tidak ditemukan."
        )

    print()
    print(
        "Catatan: Analisis ini menggunakan pencocokan kata sederhana."
    )

    print(
        "Program belum memahami konteks, sindiran, dan sarkasme."
    )

    tampilkan_garis()


# ==========================================================
# FUNGSI PROSES ANALISIS
# ==========================================================

def proses_analisis(teks):
    """
    Menjalankan seluruh proses analisis teks.
    """
    teks = bersihkan_spasi(teks)

    if not teks:
        print()
        print("Teks kosong. Tidak ada teks yang dapat dianalisis.")
        return

    hasil_sentimen = analisis_sentimen(teks)

    tampilkan_statistik_dasar(teks)

    tampilkan_semua_frekuensi(teks)

    tampilkan_kata_tersering(
        teks,
        jumlah=10
    )

    tampilkan_hasil_sentimen(
        hasil_sentimen
    )

    tampilkan_kata_sentimen_ditemukan(
        hasil_sentimen
    )

    tampilkan_kesimpulan(
        hasil_sentimen
    )


# ==========================================================
# FUNGSI DAFTAR KATA SENTIMEN
# ==========================================================

def tampilkan_daftar_kata_sentimen():
    """
    Menampilkan seluruh kata positif dan kata negatif.
    """
    print()
    tampilkan_garis()
    print("DAFTAR KATA SENTIMEN".center(60))
    tampilkan_garis()

    print()
    print("KATA POSITIF")
    print("-" * 60)

    daftar_positif = sorted(KATA_POSITIF)

    for nomor, kata in enumerate(daftar_positif, start=1):
        print(f"{nomor:>3}. {kata}")

    print()
    print("KATA NEGATIF")
    print("-" * 60)

    daftar_negatif = sorted(KATA_NEGATIF)

    for nomor, kata in enumerate(daftar_negatif, start=1):
        print(f"{nomor:>3}. {kata}")

    tampilkan_garis()


# ==========================================================
# FUNGSI UTAMA
# ==========================================================

def main():
    """
    Fungsi utama program.
    """
    tampilkan_judul()

    while True:
        tampilkan_menu()

        pilihan = input("Pilih menu 1-3: ").strip()

        if pilihan == "1":
            teks = input_teks_multibaris()

            proses_analisis(teks)

        elif pilihan == "2":
            tampilkan_daftar_kata_sentimen()

        elif pilihan == "3":
            print()
            tampilkan_garis()
            print("Program selesai.")
            print("Terima kasih telah menggunakan Tool Analisis Teks.")
            tampilkan_garis()

            break

        else:
            print()
            print(
                "Pilihan tidak valid. "
                "Silakan masukkan angka 1 sampai 3."
            )


# ==========================================================
# MENJALANKAN PROGRAM
# ==========================================================

if __name__ == "__main__":
    main()
```

## AI Usage

Dalam proses pengembangan **Tool Analisis Teks**, AI digunakan untuk membantu penyusunan data, dokumentasi fungsi, dan perapian struktur kode.

| No. | Penggunaan AI                              | Prompt yang Digunakan                                                                                                                                                                                                                                                        | Hasil Penggunaan                                                                                                                                          |
| :-: | ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | Membuat daftar kata sentimen dan stopwords | `Buatkan daftar kata positif, kata negatif, dan stopwords Bahasa Indonesia yang dapat digunakan dalam program Python analisis teks sederhana. Daftar tersebut akan digunakan untuk menghitung sentimen dan frekuensi kata.`                                                  | AI membantu membuat kumpulan `KATA_POSITIF`, `KATA_NEGATIF`, dan `STOPWORDS` yang digunakan dalam proses analisis teks.                                   |
|  2  | Menjelaskan seluruh fungsi dalam program   | `Jelaskan fungsi dari setiap function yang terdapat dalam kode Python Tool Analisis Teks. Jelaskan parameter, proses, dan nilai yang dikembalikan dengan bahasa yang sederhana dan mudah dipahami.`                                                                          | AI membantu memberikan komentar dan dokumentasi untuk menjelaskan tujuan serta cara kerja setiap fungsi dalam program.                                    |
|  3  | Memperbaiki format dan struktur kode       | `Perbagus format codingan Python berikut agar lebih rapi, konsisten, dan mudah dibaca tanpa mengubah fungsi utama program. Kelompokkan kode berdasarkan kegunaannya, gunakan penamaan yang jelas, tambahkan komentar seperlunya, dan ikuti gaya penulisan Python yang baik.` | AI membantu merapikan indentasi, penamaan variabel, komentar, pembagian bagian kode, dan struktur program agar lebih mudah dipelajari serta dikembangkan. |

### Catatan Penggunaan AI

AI digunakan sebagai alat bantu dalam proses pengembangan. Hasil yang diberikan oleh AI diperiksa, disesuaikan, dan diuji kembali sebelum dimasukkan ke dalam program akhir.

