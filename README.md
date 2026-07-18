# 📄 Laporan Proyek Akhir - Tool-Analisis-Teks
## Tool Analisis Teks

| Informasi | Keterangan |
|-----------|------------|
| **Nama** | Irshad Mulyahida - 0112525004|
| **Nama** | Muhammad Husain - 0112525010|
| **Program Studi** | Informatika |
| **Universitas** | Universitas Al Azhar Indonesia |

Akses codingan colabnya di [Colab Proyek Akhir](https://colab.research.google.com/drive/1WuAOmtlD-FX-FDoaj2cioGKy-R1vj7qF?usp=sharing)
---

# BAB I - Pendahuluan

## 1.1 Latar Belakang

Dalam era digital saat ini, data tekstual dihasilkan dalam jumlah yang sangat besar setiap harinya. Analisis data teks menjadi penting untuk mengekstrak informasi yang bernilai dari kumpulan data tersebut.

Proyek ini bertujuan untuk mengembangkan sebuah **Tool Analisis Teks** yang mampu memproses serta menganalisis korpus teks secara efisien sehingga menghasilkan informasi statistik yang berguna.

---

## 1.2 Rumusan Masalah

1. Bagaimana merancang sistem yang dapat melakukan **preprocessing** pada data teks mentah?
2. Bagaimana mengimplementasikan ekstraksi fitur serta statistik dasar seperti **Term Frequency** dari suatu teks?

---

## 1.3 Tujuan

- Membangun aplikasi atau skrip yang mampu membersihkan serta menganalisis data teks.
- Menghasilkan visualisasi maupun laporan statistik dasar sebagai bahan analisis data.

---

# BAB II - Landasan Teori

## 2.1 Pemrosesan Bahasa Alami (Natural Language Processing)

**Natural Language Processing (NLP)** merupakan cabang ilmu komputer yang mempelajari interaksi antara komputer dan bahasa manusia.

Tahapan dasar NLP meliputi:

- Tokenisasi
- Penghapusan *stop words*
- Stemming atau Lemmatization

---

## 2.2 Analisis Data dan Statistik

Analisis teks umumnya menggunakan pendekatan statistik untuk memahami distribusi kata serta makna yang tersembunyi di dalam dokumen.

Beberapa konsep penting antara lain:

- Distribusi Frekuensi
- Probabilitas Dasar
- Term Frequency (TF)
- Pembobotan Kata

---

# BAB III - Perancangan Sistem

## 3.1 Alur Kerja (Workflow)

```text
                    START
                      │
                      ▼
        Pengguna Memilih Menu Analisis
                      │
                      ▼
             Input Teks dari Pengguna
                      │
                      ▼
          Pembersihan Teks (Preprocessing)
        ┌───────────────────────────────────┐
        │ • Menghapus spasi berlebih        │
        │ • Case Folding                    │
        │ • Menghapus tanda baca            │
        └───────────────────────────────────┘
                      │
                      ▼
               Tokenisasi Kata
                      │
                      ▼
        ┌───────────────────────────────────┐
        │ Statistik Dasar                   │
        │ • Jumlah karakter                 │
        │ • Jumlah kata                     │
        │ • Jumlah kata unik                │
        │ • Jumlah kalimat                  │
        └───────────────────────────────────┘
                      │
                      ▼
        ┌───────────────────────────────────┐
        │ Analisis Frekuensi Kata           │
        │ • Menghapus Stopword              │
        │ • Menghitung Term Frequency       │
        │ • Menampilkan Kata Terbanyak      │
        └───────────────────────────────────┘
                      │
                      ▼
        ┌───────────────────────────────────┐
        │ Analisis Sentimen                 │
        │ • Kata Positif                    │
        │ • Kata Negatif                    │
        │ • Menghitung Skor Sentimen        │
        │ • Menentukan Kategori             │
        └───────────────────────────────────┘
                      │
                      ▼
           Menampilkan Hasil Analisis
                      │
                      ▼
                     END
```

### Tahapan Sistem

| Tahap | Deskripsi |
|-------|-----------|
| **Input** | Pengguna memasukkan teks atau mengunggah dokumen |
| **Preprocessing** | Case folding dan penghapusan tanda baca |
| **Processing** | Tokenisasi serta perhitungan frekuensi kata |
| **Output** | Menampilkan hasil analisis berupa tabel frekuensi kata |

---

## 3.2 Arsitektur Lingkungan

Tahapan pengembangan dilakukan menggunakan lingkungan interaktif seperti **Google Colab** agar proses eksplorasi data dan pengujian lebih mudah.

Setelah proses pengujian selesai, implementasi dapat dipindahkan ke aplikasi menggunakan bahasa seperti:

- Python
- C++
- Bahasa lain sesuai kebutuhan

---

# BAB IV - Implementasi dan Hasil

## 4.1 Contoh Implementasi

```python
import string
from collections import Counter

def preprocess_and_analyze(text):
    # Case folding
    text = text.lower()

    # Menghapus tanda baca
    text = text.translate(
        str.maketrans('', '', string.punctuation)
    )

    # Tokenisasi
    tokens = text.split()

    # Menghitung frekuensi kata
    word_counts = Counter(tokens)

    return word_counts.most_common(5)
```

---

## 4.2 Simulasi Pengujian

Pengujian dilakukan menggunakan sebuah paragraf sebagai data masukan.

### Hasil Analisis

| Peringkat | Kata (Token) | Frekuensi (Term Frequency) |
|----------:|--------------|---------------------------:|
| 1 | data | 15 |
| 2 | sistem | 12 |
| 3 | analisis | 10 |
| 4 | teks | 8 |
| 5 | informasi | 7 |

---

# BAB V - Kesimpulan dan Saran

## 5.1 Kesimpulan

Tool Analisis Teks berhasil dirancang dengan kemampuan dasar sebagai berikut:

- Membersihkan data teks (*text preprocessing*)
- Melakukan tokenisasi
- Menghitung frekuensi kemunculan kata
- Menampilkan statistik sederhana hasil analisis

Implementasi tersebut menjadi dasar yang baik untuk pengembangan sistem analisis teks yang lebih kompleks.

---

## 5.2 Saran

Pengembangan selanjutnya dapat dilakukan dengan menambahkan fitur seperti:

- TF-IDF
- Word Cloud
- Analisis Sentimen
- Naive Bayes untuk klasifikasi teks
- Visualisasi statistik menggunakan Matplotlib
- Optimasi performa menggunakan C++ pada modul yang membutuhkan efisiensi tinggi

---

# Referensi

1. Jurafsky, D., & Martin, J. H. (2024). *Speech and Language Processing*.
2. Bird, S., Klein, E., & Loper, E. *Natural Language Processing with Python*.
3. Manning, C. D., Raghavan, P., & Schütze, H. *Introduction to Information Retrieval*.

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

# Tool Analisis Teks Python

Program ini memiliki fitur:

1. Menghitung jumlah karakter.
2. Menghitung jumlah kata.
3. Menghitung jumlah kalimat.
4. Menghitung frekuensi kata.
5. Menampilkan kata paling sering.
6. Melakukan analisis sentimen sederhana.
7. Menampilkan kata positif dan negatif.

---

### Bagian 1 — Mengimpor Library

```python
import re
from collections import Counter
```

**Penjelasan:**

| Library   | Fungsi                                                 |
| --------- | ------------------------------------------------------ |
| `re`      | Mengolah teks menggunakan pola atau regular expression |
| `Counter` | Menghitung jumlah kemunculan setiap kata               |

Library `re` digunakan untuk mengambil kata, memisahkan kalimat, dan membersihkan spasi.

Library `Counter` digunakan untuk menghitung frekuensi kata.

---

### Bagian 2 — Membuat Informasi Program

```python
NAMA_PROGRAM = "Tool Analisis Teks"
VERSI_PROGRAM = "1.0"
```

**Penjelasan:**

* `NAMA_PROGRAM` menyimpan nama aplikasi.
* `VERSI_PROGRAM` menyimpan versi aplikasi.
* Kedua variabel tersebut bertipe `string`.

Nilainya akan ditampilkan saat program pertama kali dijalankan.

---

### Bagian 3 — Membuat Daftar Kata Positif

```python
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
}
```

**Penjelasan:**

`KATA_POSITIF` menggunakan tipe data `set`.

Set digunakan karena:

* Tidak menyimpan data duplikat.
* Pencarian kata lebih cepat.
* Cocok untuk memeriksa apakah sebuah kata tersedia.

Contoh pemeriksaan:

```python
kata = "bagus"

if kata in KATA_POSITIF:
    print("Kata positif ditemukan")
```

---

### Bagian 4 — Membuat Daftar Kata Negatif

```python
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
}
```

**Penjelasan:**

Setiap kata yang ditemukan dalam `KATA_NEGATIF` akan dihitung sebagai kata negatif.

Contohnya:

```python
kata = "lambat"

if kata in KATA_NEGATIF:
    print("Kata negatif ditemukan")
```

---

### Bagian 5 — Membuat Daftar Stopwords

```python
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
}
```

**Penjelasan:**

Stopwords adalah kata umum yang biasanya tidak terlalu penting dalam analisis frekuensi.

Contohnya:

```text
yang, dan, di, ke, dari
```

Kata-kata tersebut dihapus agar hasil frekuensi lebih berfokus pada kata penting.

---

### Bagian 6 — Membuat Fungsi Tampilan

```python
def tampilkan_garis(panjang=60):
    print("=" * panjang)


def tampilkan_judul():
    tampilkan_garis()
    print(NAMA_PROGRAM.center(60))
    print(f"Versi {VERSI_PROGRAM}".center(60))
    tampilkan_garis()


def tampilkan_menu():
    print()
    print("MENU UTAMA")
    print("-" * 60)
    print("1. Analisis teks")
    print("2. Lihat daftar kata sentimen")
    print("3. Keluar")
    print("-" * 60)
```

**Penjelasan:**

| Fungsi              | Kegunaan                           |
| ------------------- | ---------------------------------- |
| `tampilkan_garis()` | Menampilkan garis pembatas         |
| `tampilkan_judul()` | Menampilkan nama dan versi program |
| `tampilkan_menu()`  | Menampilkan pilihan menu utama     |

Bagian berikut:

```python
"=" * panjang
```

digunakan untuk mengulang simbol `=` sesuai jumlah yang ditentukan.

Sedangkan:

```python
NAMA_PROGRAM.center(60)
```

digunakan untuk menempatkan tulisan di tengah.

---

### Bagian 7 — Membersihkan Teks

```python
def bersihkan_spasi(teks):
    teks_bersih = re.sub(r"\s+", " ", teks)

    return teks_bersih.strip()


def ubah_ke_huruf_kecil(teks):
    return teks.lower()
```

**Penjelasan:**

Fungsi `bersihkan_spasi()` menghapus spasi berlebihan.

Contoh:

```text
Program     ini     bagus
```

menjadi:

```text
Program ini bagus
```

Bagian:

```python
re.sub(r"\s+", " ", teks)
```

mengganti satu atau lebih karakter kosong menjadi satu spasi.

Fungsi `ubah_ke_huruf_kecil()` menggunakan:

```python
lower()
```

Contoh:

```text
BAGUS
Bagus
bagus
```

semuanya menjadi:

```text
bagus
```

---

### Bagian 8 — Mengambil Kata dari Teks

```python
def ambil_daftar_kata(teks):
    teks = ubah_ke_huruf_kecil(teks)

    daftar_kata = re.findall(
        r"\b[a-zA-ZÀ-ÿ0-9]+\b",
        teks
    )

    return daftar_kata
```

**Penjelasan:**

Fungsi ini mengambil semua kata dari teks menggunakan:

```python
re.findall()
```

Contoh input:

```text
Program ini bagus!
```

Hasilnya:

```python
["program", "ini", "bagus"]
```

Tanda seru tidak dimasukkan karena bukan bagian dari kata.

---

### Bagian 9 — Mengambil Kata Penting

```python
def ambil_kata_penting(teks):
    semua_kata = ambil_daftar_kata(teks)

    kata_penting = []

    for kata in semua_kata:
        if kata not in STOPWORDS and len(kata) > 1:
            kata_penting.append(kata)

    return kata_penting
```

**Penjelasan:**

Fungsi ini memeriksa semua kata menggunakan perulangan:

```python
for kata in semua_kata:
```

Kata hanya dimasukkan jika:

```python
kata not in STOPWORDS
```

dan panjang kata lebih dari satu karakter:

```python
len(kata) > 1
```

Method:

```python
append()
```

digunakan untuk menambahkan kata ke dalam list.

---

### Bagian 10 — Mengambil Kalimat dari Teks

```python
def ambil_daftar_kalimat(teks):
    hasil_pemisahan = re.split(r"[.!?]+", teks)

    daftar_kalimat = []

    for kalimat in hasil_pemisahan:
        kalimat = kalimat.strip()

        if kalimat:
            daftar_kalimat.append(kalimat)

    return daftar_kalimat
```

**Penjelasan:**

Fungsi ini memisahkan kalimat berdasarkan:

* Titik `.`
* Tanda tanya `?`
* Tanda seru `!`

Fungsi yang digunakan adalah:

```python
re.split()
```

Contoh:

```text
Program ini bagus. Apakah mudah? Sangat mudah!
```

Hasilnya adalah tiga kalimat.

---

### Bagian 11 — Menghitung Statistik Dasar

```python
def hitung_jumlah_karakter(teks):
    return len(teks)


def hitung_karakter_tanpa_spasi(teks):
    teks_tanpa_spasi = teks.replace(" ", "")
    teks_tanpa_spasi = teks_tanpa_spasi.replace("\n", "")
    teks_tanpa_spasi = teks_tanpa_spasi.replace("\t", "")

    return len(teks_tanpa_spasi)


def hitung_jumlah_kata(teks):
    daftar_kata = ambil_daftar_kata(teks)

    return len(daftar_kata)


def hitung_jumlah_kata_unik(teks):
    daftar_kata = ambil_daftar_kata(teks)
    kata_unik = set(daftar_kata)

    return len(kata_unik)


def hitung_jumlah_kalimat(teks):
    daftar_kalimat = ambil_daftar_kalimat(teks)

    return len(daftar_kalimat)
```

**Penjelasan:**

| Fungsi                          | Kegunaan                         |
| ------------------------------- | -------------------------------- |
| `hitung_jumlah_karakter()`      | Menghitung semua karakter        |
| `hitung_karakter_tanpa_spasi()` | Menghitung karakter selain spasi |
| `hitung_jumlah_kata()`          | Menghitung seluruh kata          |
| `hitung_jumlah_kata_unik()`     | Menghitung kata yang berbeda     |
| `hitung_jumlah_kalimat()`       | Menghitung jumlah kalimat        |

Fungsi:

```python
len()
```

digunakan untuk menghitung panjang data.

Sedangkan:

```python
set()
```

digunakan untuk menghapus data duplikat.

---

### Bagian 12 — Menghitung Frekuensi Kata

```python
def hitung_frekuensi_kata(teks, hapus_stopword=True):
    if hapus_stopword:
        daftar_kata = ambil_kata_penting(teks)
    else:
        daftar_kata = ambil_daftar_kata(teks)

    frekuensi = Counter(daftar_kata)

    return frekuensi
```

**Penjelasan:**

Parameter:

```python
hapus_stopword=True
```

berarti stopwords akan dihapus secara otomatis.

Jika nilainya `False`, seluruh kata akan dihitung.

Frekuensi dihitung menggunakan:

```python
Counter()
```

Contoh:

```python
Counter(["bagus", "mudah", "bagus"])
```

menghasilkan:

```python
{
    "bagus": 2,
    "mudah": 1
}
```

---

### Bagian 13 — Menampilkan Seluruh Frekuensi Kata

```python
def tampilkan_semua_frekuensi(teks):
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
```

**Penjelasan:**

Fungsi:

```python
sorted()
```

digunakan untuk mengurutkan frekuensi dari jumlah terbesar.

Fungsi:

```python
enumerate()
```

digunakan untuk memberikan nomor urut.

Contoh output:

```text
1. program               3 kali
2. bagus                 2 kali
3. mudah                 1 kali
```

---

### Bagian 14 — Menampilkan Kata Paling Sering

```python
def ambil_kata_tersering(teks, jumlah=10):
    frekuensi = hitung_frekuensi_kata(
        teks,
        hapus_stopword=True
    )

    return frekuensi.most_common(jumlah)


def buat_batang_frekuensi(jumlah, panjang_maksimal=30):
    panjang_batang = min(jumlah, panjang_maksimal)

    return "#" * panjang_batang


def tampilkan_kata_tersering(teks, jumlah=10):
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
```

**Penjelasan:**

Method:

```python
most_common()
```

digunakan untuk mengambil kata dengan frekuensi tertinggi.

Contoh output:

```text
1. program               3 kali | ###
2. bagus                 2 kali | ##
3. mudah                 1 kali | #
```

Fungsi:

```python
min()
```

digunakan agar panjang batang tidak lebih dari 30 karakter.

---

### Bagian 15 — Mencari Frasa Sentimen

```python
def cari_frasa_sentimen(teks, daftar_sentimen):
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
```

**Penjelasan:**

Fungsi ini mencari sentimen yang terdiri dari lebih dari satu kata.

Contohnya:

```text
luar biasa
tidak nyaman
terima kasih
```

Bagian:

```python
if " " in kata:
```

memeriksa apakah kata sentimen memiliki spasi.

---

### Bagian 16 — Melakukan Analisis Sentimen

```python
def analisis_sentimen(teks):
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

    total_sentimen = jumlah_positif + jumlah_negatif

    if total_sentimen == 0:
        persentase_positif = 0
        persentase_negatif = 0

    else:
        persentase_positif = (
            jumlah_positif / total_sentimen * 100
        )

        persentase_negatif = (
            jumlah_negatif / total_sentimen * 100
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
```

**Penjelasan:**

Setiap kata positif memiliki nilai `+1`.

Setiap kata negatif memiliki nilai `-1`.

Rumus skor:

```python
skor_sentimen = jumlah_positif - jumlah_negatif
```

Aturan kategori:

|            Skor | Kategori |
| --------------: | -------- |
|  Lebih dari `0` | Positif  |
| Kurang dari `0` | Negatif  |
| Sama dengan `0` | Netral   |

Semua hasil disimpan dalam tipe data `dictionary`.

---

### Bagian 17 — Menerima Input Teks

```python
def input_teks_multibaris():
    print()
    print("Masukkan teks yang ingin dianalisis.")
    print("Ketik SELESAI untuk menyelesaikan input.")
    print("-" * 60)

    kumpulan_baris = []

    while True:
        baris = input()

        if baris.strip().upper() == "SELESAI":
            break

        kumpulan_baris.append(baris)

    teks = "\n".join(kumpulan_baris)

    return teks.strip()
```

**Penjelasan:**

Program menerima input menggunakan:

```python
input()
```

Perulangan:

```python
while True
```

membuat program terus menerima teks.

Bagian:

```python
baris.strip().upper()
```

membuat beberapa penulisan berikut dianggap sama:

```text
SELESAI
selesai
Selesai
```

* `.strip()` menghapus spasi.
* `.upper()` mengubah teks menjadi huruf kapital.
* `break` menghentikan perulangan.
* `join()` menggabungkan seluruh baris teks.

---

### Bagian 18 — Menampilkan Statistik Dasar

```python
def tampilkan_statistik_dasar(teks):
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
    print(f"Jumlah karakter       : {jumlah_karakter}")
    print(f"Karakter tanpa spasi  : {karakter_tanpa_spasi}")

    print()
    print("B. JUMLAH KATA")
    print("-" * 60)
    print(f"Jumlah seluruh kata   : {jumlah_kata}")
    print(f"Jumlah kata unik      : {jumlah_kata_unik}")

    print()
    print("C. JUMLAH KALIMAT")
    print("-" * 60)
    print(f"Jumlah kalimat        : {jumlah_kalimat}")
```

**Penjelasan:**

Fungsi ini menampilkan hasil:

* Jumlah karakter.
* Karakter tanpa spasi.
* Jumlah kata.
* Jumlah kata unik.
* Jumlah kalimat.

Output ditampilkan menggunakan:

```python
print()
```

Sedangkan nilai variabel dimasukkan ke dalam teks menggunakan `f-string`.

---

### Bagian 19 — Menampilkan Hasil Sentimen

```python
def tampilkan_hasil_sentimen(hasil_sentimen):
    print()
    print("F. HASIL ANALISIS SENTIMEN")
    print("-" * 60)

    print(
        f"Kategori sentimen   : "
        f"{hasil_sentimen['kategori']}"
    )

    print(
        f"Skor sentimen       : "
        f"{hasil_sentimen['skor']}"
    )

    print(
        f"Jumlah positif      : "
        f"{hasil_sentimen['jumlah_positif']}"
    )

    print(
        f"Jumlah negatif      : "
        f"{hasil_sentimen['jumlah_negatif']}"
    )

    print(
        f"Persentase positif  : "
        f"{hasil_sentimen['persentase_positif']:.2f}%"
    )

    print(
        f"Persentase negatif  : "
        f"{hasil_sentimen['persentase_negatif']:.2f}%"
    )
```

**Penjelasan:**

Data diambil dari dictionary menggunakan nama key.

Contoh:

```python
hasil_sentimen["kategori"]
```

Format:

```python
:.2f
```

digunakan untuk menampilkan dua angka di belakang koma.

---

### Bagian 20 — Menampilkan Kata Positif dan Negatif

```python
def tampilkan_kata_sentimen_ditemukan(hasil_sentimen):
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
        print("- Tidak ada kata positif.")

    print()
    print("Kata negatif:")

    if kata_negatif:
        frekuensi_negatif = Counter(kata_negatif)

        for kata, jumlah in frekuensi_negatif.most_common():
            print(f"- {kata}: {jumlah} kali")

    else:
        print("- Tidak ada kata negatif.")
```

**Penjelasan:**

Fungsi ini menampilkan kata positif dan negatif yang ditemukan.

`Counter()` digunakan agar program dapat mengetahui berapa kali setiap kata muncul.

Contoh output:

```text
Kata positif:
- bagus: 2 kali
- mudah: 1 kali

Kata negatif:
- lambat: 1 kali
- bug: 1 kali
```

---

### Bagian 21 — Menampilkan Kesimpulan

```python
def tampilkan_kesimpulan(hasil_sentimen):
    kategori = hasil_sentimen["kategori"]

    print()
    print("KESIMPULAN")
    print("-" * 60)

    if kategori == "POSITIF":
        print(
            "Teks cenderung memiliki sentimen positif."
        )

    elif kategori == "NEGATIF":
        print(
            "Teks cenderung memiliki sentimen negatif."
        )

    else:
        print(
            "Teks memiliki sentimen netral."
        )

    print()
    print(
        "Catatan: Program menggunakan pencocokan kata sederhana."
    )

    tampilkan_garis()
```

**Penjelasan:**

Fungsi ini menggunakan percabangan:

```python
if
elif
else
```

Kesimpulan ditentukan berdasarkan kategori sentimen.

---

### Bagian 22 — Menjalankan Seluruh Analisis

```python
def proses_analisis(teks):
    teks = bersihkan_spasi(teks)

    if not teks:
        print()
        print("Teks kosong. Tidak ada teks yang dapat dianalisis.")
        return

    hasil_sentimen = analisis_sentimen(teks)

    tampilkan_statistik_dasar(teks)
    tampilkan_semua_frekuensi(teks)
    tampilkan_kata_tersering(teks, jumlah=10)
    tampilkan_hasil_sentimen(hasil_sentimen)
    tampilkan_kata_sentimen_ditemukan(hasil_sentimen)
    tampilkan_kesimpulan(hasil_sentimen)
```

**Penjelasan:**

Fungsi `proses_analisis()` menjadi pengatur utama proses analisis.

Urutannya:

1. Membersihkan teks.
2. Memeriksa apakah teks kosong.
3. Menganalisis sentimen.
4. Menampilkan statistik.
5. Menampilkan frekuensi kata.
6. Menampilkan kata paling sering.
7. Menampilkan hasil sentimen.
8. Menampilkan kesimpulan.

---

### Bagian 23 — Menampilkan Daftar Kata Sentimen

```python
def tampilkan_daftar_kata_sentimen():
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
```

**Penjelasan:**

Fungsi:

```python
sorted()
```

mengurutkan kata secara alfabet.

Fungsi:

```python
enumerate()
```

memberikan nomor urut pada setiap kata.

---

### Bagian 24 — Membuat Menu Utama

```python
def main():
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
            print("Program selesai.")
            break

        else:
            print()
            print("Pilihan tidak valid.")
```

**Penjelasan:**

Pilihan pengguna diterima menggunakan:

```python
input()
```

Pilihan diperiksa menggunakan:

```python
if
elif
else
```

Menu terus diulang menggunakan:

```python
while True
```

Ketika pengguna memilih menu `3`, perulangan dihentikan menggunakan:

```python
break
```

---

### Bagian 25 — Menjalankan Program

```python
if __name__ == "__main__":
    main()
```

**Penjelasan:**

Bagian tersebut memastikan bahwa fungsi `main()` dijalankan ketika file Python dibuka secara langsung.

Urutan program:

```text
Program dijalankan
        ↓
main()
        ↓
tampilkan_judul()
        ↓
tampilkan_menu()
        ↓
Pengguna memilih menu
        ↓
Program menjalankan fungsi sesuai pilihan
```

---

## Contoh Input

```text
Aplikasi ini sangat bagus dan mudah digunakan.
Tampilannya menarik dan saya merasa puas.
Namun, aplikasi ini terkadang lambat dan memiliki bug.
SELESAI
```

## Contoh Hasil Sentimen

```text
Kategori sentimen   : POSITIF
Skor sentimen       : 2
Jumlah positif      : 4
Jumlah negatif      : 2
Persentase positif  : 66.67%
Persentase negatif  : 33.33%
```

## Ringkasan Fungsi yang Digunakan

| Fungsi atau Method   | Kegunaan                          |
| -------------------- | --------------------------------- |
| `print()`            | Menampilkan output                |
| `input()`            | Menerima input pengguna           |
| `len()`              | Menghitung jumlah data            |
| `lower()`            | Mengubah huruf menjadi kecil      |
| `upper()`            | Mengubah huruf menjadi kapital    |
| `strip()`            | Menghapus spasi awal dan akhir    |
| `append()`           | Menambahkan data ke list          |
| `extend()`           | Menambahkan beberapa data ke list |
| `join()`             | Menggabungkan beberapa string     |
| `replace()`          | Mengganti atau menghapus karakter |
| `set()`              | Menghapus data duplikat           |
| `sorted()`           | Mengurutkan data                  |
| `enumerate()`        | Memberikan nomor urut             |
| `Counter()`          | Menghitung frekuensi              |
| `most_common()`      | Mengambil data paling sering      |
| `re.findall()`       | Mengambil kata berdasarkan pola   |
| `re.split()`         | Memisahkan kalimat                |
| `re.sub()`           | Mengganti pola dalam teks         |
| `if`, `elif`, `else` | Membuat percabangan               |
| `for`                | Mengulang kumpulan data           |
| `while`              | Mengulang proses                  |
| `break`              | Menghentikan perulangan           |
| `return`             | Mengembalikan hasil fungsi        |


## AI Usage

Dalam proses pengembangan **Tool Analisis Teks**, AI digunakan untuk membantu penyusunan data, dokumentasi fungsi, dan perapian struktur kode.

| No. | Penggunaan AI | Prompt yang Digunakan | Hasil Penggunaan |
| :-: | ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  1  | Membuat daftar kata sentimen dan stopwords | `Buatkan daftar kata positif, kata negatif, dan stopwords yang dapat digunakan dalam program Python analisis teks sederhana. Daftar tersebut akan digunakan untuk menghitung sentimen dan frekuensi kata pada kodingan ini, [input codingan].` | AI membantu membuat kumpulan `KATA_POSITIF`, `KATA_NEGATIF`, dan `STOPWORDS` yang digunakan dalam proses analisis teks.                                   |
|  2  | Menjelaskan seluruh fungsi dalam program   | `Jelaskan fungsi dari setiap fungsi yang terdapat dalam kode Python Tool Analisis Teks ini. Jelaskan parameter, proses, dan nilai yang dikembalikan dengan bahasa yang sederhana dan mudah dipahami.` | AI membantu memberikan komentar dan dokumentasi untuk menjelaskan tujuan serta cara kerja setiap fungsi dalam program. |
|  3  | Memperbaiki format dan struktur kode       | `Perbagus format codingan Python berikut agar lebih rapi, konsisten, dan mudah dibaca tanpa mengubah fungsi utama program. Kelompokkan kode berdasarkan kegunaannya, gunakan penamaan yang jelas, tambahkan komentar seperlunya, dan ikuti gaya penulisan Python yang baik.` | AI membantu merapikan indentasi, penamaan variabel, komentar, pembagian bagian kode, dan struktur program agar lebih mudah dipelajari serta dikembangkan. |
|  4  | Memeperbaiki format penulisan dari keseluruhan github | `Tolong rapihkan penjelasan dari kodingan ini [pasted bagian fungsi terpisah.` | Ai membantu format github lebih rapih. |

