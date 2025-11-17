# Kelompok 1

**Anggota:**

1. Mutiara Putri Setyawan (2304220007)  
2. Pradytha Galuh Putranti (2304220013)  
3. Rafadel Bramanta Arianto (2304220017)  
4. Ahmad Hikmah Ali Pahrizi (2304220018)  
5. Muhammad Faza Farizqi (2304220024)  
6. Muhammad Fathan Helmi Robbani (2304220032)  
7. Chandy Anugra Pratama (2304220038)  
8. Zulfa Laela Maulida (2304220043)  

---

# Twitter Scraping & Sentiment Analysis - KCIC / Whoosh

Proyek ini bertujuan untuk **mengambil data tweet terbaru tentang Whoosh / KCIC** dari Twitter menggunakan Python dan Tweepy.  
Selain pengambilan data, proyek ini juga menambahkan **analisis sentimen** sebagai fitur opsional untuk mengetahui apakah tweet bersifat positif, netral, atau negatif.  

## Tujuan

- Mengambil tweet terbaru tentang Whoosh / KCIC.  
- Menyusun dataset terstruktur dari tweet yang dikumpulkan.  
- (Opsional) Menambahkan analisis sentimen menggunakan model `twitter-xlm-roberta-base-sentiment`.  
- Memvisualisasikan kata-kata populer berdasarkan kategori sentimen menggunakan WordCloud.  

## Kolom Data yang Dikumpulkan

| Kolom       | Deskripsi                                         |
|------------|--------------------------------------------------|
| date       | Tanggal dan waktu tweet diposting                |
| author_id  | ID pengguna Twitter                               |
| text       | Isi tweet                                        |
| likes      | Jumlah like                                      |
| retweets   | Jumlah retweet                                   |
| replies    | Jumlah reply                                     |
| sentiment  | Label sentimen (positif, netral, negatif) – opsional |
| confidence | Skor keyakinan model – opsional                  |

---

## Tools dan Library

- **Tweepy** — akses Twitter API (v1.1 & v2)  
- **Pandas** — menyusun dan mengekspor dataset  
- **Transformers & Torch** — analisis sentimen opsional  
- **WordCloud & Matplotlib** — visualisasi kata populer  

---

## Cara Kerja Program

1. **Autentikasi Twitter API**  
   Masukkan **Consumer Key, Consumer Secret, Access Token, Access Token Secret, dan Bearer Token** untuk akses penuh.  

2. **Disable Widgets & Progress Bars**  
   Agar notebook aman untuk GitHub/VSCode, semua progress bar dan widget HuggingFace dinonaktifkan.  

3. **Set Bearer Token & Initialize Twitter Client**  
   Gunakan API v2 untuk membaca tweet terbaru dengan kolom `date`, `author_id`, `text`, dan `public_metrics`.  

4. **Search Recent Tweets**  
   Filter berdasarkan kata kunci/hashtag: `#Whoosh`, `#KCIC`, `#KeretaCepat`.  
   Gunakan `-is:retweet` untuk menghindari duplikasi dari retweet.  

5. **Create Clean DataFrame**  
   Simpan tweet ke Pandas DataFrame, bersihkan teks dari `@username`, URL, dan spasi berlebih.  
   Sertakan kolom opsional `likes`, `retweets`, `replies` dari `public_metrics`.  

6. **Load Sentiment Model**  
   Model `twitter-xlm-roberta-base-sentiment` digunakan untuk klasifikasi negatif, netral, atau positif.  

7. **Detect Sentiment & Add to DataFrame**  
   Setiap tweet dianalisis sentimennya dan ditambahkan ke DataFrame bersama skor keyakinan (confidence).  

8. **Count & Proportion of Sentiments**  
   Menampilkan jumlah dan persentase tweet berdasarkan kategori sentimen untuk overview cepat.  

9. **WordCloud Visualization**  
   Membuat WordCloud berdasarkan tiap kategori sentimen untuk melihat kata populer.  

10. **Export Data**  
    Simpan dataset ke file `tweets_sentiment.txt` (TSV) atau `tweets_sentiment.html` untuk tampilan rapi di browser.  

---



## Cara Menjalankan Proyek

### Option 1 — Google Colab

1. Upload notebook ke Colab.  
2. Jalankan semua sel.  
3. DataFrame akan muncul, bisa diekspor ke CSV/HTML.  

### Option 2 — Lokal Jupyter Notebook

1. Clone repository:

```bash
git clone https://github.com/username/twitter-scraping-kcic-whoosh.git
cd twitter-scraping-kcic-whoosh
````

2. Install dependencies:

```bash
pip install tweepy pandas matplotlib wordcloud transformers torch
```

3. Jalankan notebook:

```bash
jupyter notebook Fix_Kelompok1_PMML.ipynb
```

---

## Struktur Proyek

```text
twitter-scraping-kcic-whoosh/
│
├── Fix_Kelompok1_PMML.ipynb  # Notebook utama (Python + Tweepy)
├── tweets_sentiment.txt       # Dataset hasil scraping (TSV)
├── tweets_sentiment.html      # Dataset hasil scraping (HTML rapi)
└── README.md                  # Dokumentasi proyek
```

---

## Contoh Output

| date             | author_id  | text                              | likes | retweets | replies | sentiment | confidence |
| ---------------- | ---------- | --------------------------------- | ----- | -------- | ------- | --------- | ---------- |
| 2025-11-17 16:37 | 43476922   | Ilmu itu bisa berkembang…         | 0     | 0        | 0       | neutral   | 0.49       |
| 2025-11-17 16:25 | 1665235202 | Lebih tepatnya sengaja dipelihara | 0     | 0        | 0       | negative  | 0.44       |
| 2025-11-17 16:06 | 8877435875 | Dirut KCIC soal Utang Whoosh…     | 8     | 6        | 0       | neutral   | 0.83       |

```
