# Dokumentasi Praktik ETL menggunakan Knime

## Business Understanding
Data yang digunakan merupakan data game yang tersedia pada platform steam. Dengan Data ini dapat didapatkan berbagai informasi seperti, rata-rata harga game pada platform steam, berbagai informasi detil game seperti deskripsi, tanggal release, genre dan juga bisa mendapatkan informasi mengenai review dari game-game tersebut

## Data Understanding
Jumlah Baris : 40,833
Jumlah Kolom : 20
1. url: berisikan link url dari game tersebut pada steam store (String)
2. types: menunjukan apakah suatu judul merupakan bundle atau aplikasi saja (string)
3. name: Nama dari game nya (String)
4. desc_snippets: deskripsi singkat dari game nya
5. all_reviews: kesimpulan skor review 
6. release_date: tanggal game di release
7. developer: nama developer game nya
8. publisher: nama publisher yang mempublish game
9. popular_tags: kumpulan tag yang sering digunakan user untuk menulis review game nya
10. game_details: tag yang dibuat oleh steam untuk mengkategorikan game
11. languages: list bahasa yang disediakan oleh game
12. achievement: jumlah achievement yang terdapat pada game
13. genre: genre game nya
14. game_description: deskripsi lengkap suatu game
15. mature_content: deskripsi tambahan apa bila suatu game dikategorikan konten dewasa
16. minimum_requirements: deskripsi spek minimum untuk menjalankan game
17. recommended_requirements: deskripsi spek yang direkomendasikan untuk menjalankan game
18. original_price: harga game dalam dollar
19. discount_price: harga game saat diskon dalam dollar

## Data preparation

### Splitting
1. Load data dari csv yang ada
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-18-20.png)
2. Lakukan formating data untuk kolom tanggal
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-19-13.png)
3. split data dari hasil formating tadi menggunakan column splitter
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-20-13.png)

### Writing
1. tulis salah satu hasil ke dalam csv
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-21-09.png)
2. Untuk menulis ke dalam database memerlukan **mysql connector**, **db table remover** untuk menghapus table yang sudah ada, **db table creator** untuk membuat table, dan **db insert** untuk menulis data nya.
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-24-19.png)
3. kita perlu menyesuaikan pengaturan kolom pada db creator agar seluruh data nya muat dan tepat tipe nya
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-25-09.png)

## Data modeling

### Reading CSV
mengimport node kemudian memilih file csv yang akan dimasukan
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-26-30.png)

### Reading Table database
membuat **db connection**, kemudian memilih table nya menggunakan **db table selector**, dan menggunaka **db reader** untuk membaca seluruh row pada table nya
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-28-45.png)

### Join
menggunakan **Joiner** untuk menyambungkan dua data yang sudah di baca dari csv dan table database
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-29-51.png)

## Evaluation
Hasil join berhasil dan data akhir nya sama seperti hasil data preparation sebelum di split
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2009-31-26.png)

## Deployment
Hasil join akan ditulis kedalam file excel dengan menggunakan node **excel writer**
![](https://github.com/adhityairvan/knime-bigdata/raw/master/Screenshot%20from%202020-02-17%2023-39-46.png)
