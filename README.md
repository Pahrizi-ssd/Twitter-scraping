
Kelompok 1

Anggota:

1. Mutiara Putri Setyawan (2304220007)

2. Pradytha Galuh Putranti (2304220013)

3. Rafadel Bramanta Arianto (2304220017)

4. Ahmad Hikmah Ali Pahrizi (2304220018)

5. Muhammad Faza Farizqi (2304220024)

6. Muhammad Fathan Helmi Robbani (2304220032)

7. Chandy Anugra Pratama (2304220038)

8. Zulfa Laela Maulida (2304220043)

# Twitter Scraping - KCIC / Whoosh

Proyek ini bertujuan untuk **mengambil data tweet terbaru tentang Whoosh / KCIC** dari Twitter menggunakan Python dan Tweepy.  
Selain itu, proyek ini juga menambahkan **analisis sentimen** sebagai fitur opsional untuk melihat apakah tweet bersifat positif, netral, atau negatif.

## Tujuan

-   Mengambil tweet terbaru tentang Whoosh / KCIC dari Twitter.
    
-   Menyusun dataset terstruktur dari tweet yang dikumpulkan.
    
-   (Opsional) Analisis sentimen tweet menggunakan model `twitter-xlm-roberta-base-sentiment`.
    
-   Memvisualisasikan kata-kata populer berdasarkan sentimen menggunakan WordCloud.
    

## Kolom Data yang Dikumpulkan

Setiap tweet memiliki kolom berikut:
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


## Tools dan Library yang Digunakan

-   **Tweepy** — mengambil data dari Twitter API
    
-   **Pandas** — menyusun dan mengekspor dataset
    
-   **Transformers & Torch** — analisis sentimen opsional
    
-   **WordCloud & Matplotlib** — visualisasi opsional teks
    

## Cara Kerja Program

1.  **Autentikasi Twitter API**  
    Masukkan API Key dan Bearer Token.
    
2.  **Pengambilan Tweet**  
    Mengambil tweet terbaru berdasarkan kata kunci: `#Whoosh`, `#KCIC`, `#KeretaCepat`.
    
3.  **Menyusun Dataset**  
    Simpan data tweet (text, author, likes, retweet, dll.) ke Pandas DataFrame.
    
4.  **(Opsional) Analisis Sentimen**  
    Klasifikasikan tweet menjadi positif, netral, atau negatif.
    
5.  **(Opsional) Visualisasi**  
    Buat WordCloud untuk tiap kategori sentimen.
    
6.  **Mengekspor Data**  
    Simpan hasil ke file CSV (`tweets_data.csv`).
    

## Struktur Proyek

```
twitter-scraping-kcic-whoosh/
│
├── twitter_scraper.ipynb      # Notebook utama (Python + Tweepy)
├── tweets_data.csv            # Dataset hasil scraping
└── README.md                  # Dokumentasi proyek

```

## Cara Menjalankan Proyek

**Option 1 — Google Colab**

1.  Upload notebook ke Colab.
    
2.  Jalankan semua sel.
    
3.  Hasil akan muncul di DataFrame dan bisa disimpan sebagai CSV.
    

**Option 2 — Lokal Jupyter Notebook**

1.  Clone repository:
    

```bash
git clone https://github.com/username/twitter-scraping-kcic-whoosh.git
cd twitter-scraping-kcic-whoosh

```

2.  Install dependencies:
    

```bash
pip install tweepy pandas matplotlib wordcloud transformers torch tqdm

```

3.  Jalankan notebook:
    

```bash
jupyter notebook twitter_scraper.ipynb

```

## Contoh Output


| date               | author_id  | text                         | likes | retweets | replies | sentiment | confidence |
|-------------------|------------|------------------------------|-------|----------|---------|-----------|------------|
| 2025-11-17 16:00  | 123456789  | Whoosh akhirnya launching! 🚄 | 25    | 3        | 1       | positif   | 0.87       |
| 2025-11-17 15:50  | 987654321  | Banyak delay di KCIC 😕     | 12    | 2        | 0       | negatif   | 0.92       |
| 2025-11-17 15:30  | 112233445  | Update info Whoosh terbaru   | 5     | 0        | 0       | netral    | 0.70       |


