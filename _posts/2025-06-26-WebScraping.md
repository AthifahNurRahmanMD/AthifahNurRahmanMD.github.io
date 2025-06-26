---
title: "Web Scraping Menggunakan BeautifulSoup"
image:
  path: "/assets/images/WebScraping.png"
categories: [Blogs]
---

## Apa Itu Web Scraping?

Web scraping adalah teknik otomatisasi untuk mengumpulkan sejumlah besar data dari situs web. Umumnya, data yang dikumpulkan masih dalam bentuk tidak terstruktur (HTML), lalu diubah menjadi format yang lebih terstruktur seperti spreadsheet (CSV) atau database agar dapat dianalisis lebih lanjut. Teknik ini banyak digunakan ketika API tidak tersedia atau tidak memadai untuk mengakses data dalam jumlah besar.

Web scraping dapat dilakukan dengan berbagai cara, seperti menggunakan API yang disediakan oleh situs, layanan online khusus scraping, atau membuat kode sendiri. Meskipun API adalah cara paling ideal, tidak semua situs menyediakannya—sehingga web scraping menjadi solusi praktis.

## Dasar Web Scraping: Proses, Perangkat, dan Penyimpanan Data

Proses web scraping melibatkan tiga tahapan utama:

1. **Pengambilan Data dari Halaman Web**  
   Saat kita mengunjungi sebuah situs web, browser akan menerjemahkan kode HTML menjadi tampilan visual. Web scraping bekerja dengan cara mengakses langsung kode HTML mentah dari halaman tersebut.

2. **Perangkat untuk Web Scraping**  
   Untuk melaksanakan proses ini, kita memanfaatkan pustaka (library) khusus di Python, di antaranya:
   - **BeautifulSoup**: Membantu membaca dan mengambil data dari kode HTML.
   - **Selenium**: Berguna untuk situs yang memuat konten dengan JavaScript, karena bisa membuka browser dan berinteraksi seperti manusia.

3. **Penyimpanan dan Pengelolaan Data**  
   Setelah data berhasil dikumpulkan, langkah selanjutnya adalah menyimpannya dalam format terstruktur agar mudah dianalisis. Data dapat disimpan sebagai:
   - **CSV**: Untuk data tabel sederhana, bisa dibuka di Excel.
   - **JSON**: Untuk data kompleks, umum digunakan pada aplikasi web.
   - **Database**: Jika datanya besar atau perlu diintegrasikan dengan aplikasi lain.

Data yang telah tersimpan dengan rapi kemudian siap digunakan untuk analisis, visualisasi, otomatisasi, atau model prediksi.

## Apa yang Akan Kita Lakukan Dalam Tutorial Ini?

Dalam tutorial ini, kita akan belajar bagaimana melakukan web scraping menggunakan Python untuk mengambil data dari situs:

[Situs Web](https://www.scrapethissite.com/pages/simple/)

![Tampilan halaman web](/assets/images/Pagewebscraping.png)

Situs di atas digunakan karena menyediakan halaman-halaman sederhana yang cocok untuk latihan scraping data berbasis HTML.

Pada halaman web tersebut, kita dapat menemukan informasi tentang berbagai negara di seluruh dunia. Setiap negara ditampilkan dalam sebuah kotak yang berisi: Nama negara, Nama ibu kota, Jumlah populasi, dan Luas wilayah.

## Persiapan: Tools yang Diperlukan

Sebelum memulai, pastikan Anda sudah menginstal tools berikut:
- **Python**: Dapat diunduh di [python.org](https://www.python.org/)
- **BeautifulSoup4** dan **requests**: Untuk melakukan scraping dari situs web.
- **pandas**: Untuk menyimpan dan mengolah data dalam bentuk CSV.

### Instalasi Library

Jalankan perintah berikut di terminal:

```bash
pip install beautifulsoup4 requests pandas
```

## Langkah-langkah Web Scraping

### 1. Mengambil dan Membaca Halaman Web

```python
import requests
from bs4 import BeautifulSoup

url = 'https://www.scrapethissite.com/pages/simple/'
response = requests.get(url)
html = response.text

soup = BeautifulSoup(html, 'html.parser')
```

### 2. Mengambil Data Negara

```python
# Temukan semua elemen yang mewakili setiap negara
countries = soup.find_all('div', class_='country')

# Siapkan list untuk menyimpan data
names, capitals, populations, areas = [], [], [], []

for country in countries:
    name = country.find('h3', class_='country-name').text.strip()
    capital = country.find('span', class_='country-capital').text.strip()
    population = country.find('span', class_='country-population').text.strip()
    area = country.find('span', class_='country-area').text.strip()
    
    names.append(name)
    capitals.append(capital)
    populations.append(population)
    areas.append(area)
```

### 3. Menyimpan Data ke CSV

```python
import pandas as pd

df = pd.DataFrame({
    'Country': names,
    'Capital': capitals,
    'Population': populations,
    'Area': areas
})

print(df)
df.to_csv('countries_data.csv', index=False)
```

---

## 🎯 Kesimpulan

Dengan mengikuti langkah-langkah di atas, kamu sudah berhasil melakukan web scraping—mengambil data langsung dari website dan mengubahnya menjadi dataset yang rapi dan siap digunakan.

Berikut ringkasan proses yang sudah dilakukan:
- ✅ **Memahami konsep dasar web scraping:**  
  Web scraping adalah teknik untuk mengambil data dari halaman web secara otomatis, terutama saat API tidak tersedia.
- ✅ **Menyiapkan tools yang dibutuhkan:**  
  Menginstal dan menggunakan library penting seperti Requests, BeautifulSoup, dan Pandas untuk mengambil dan mengelola data.
- ✅ **Mengambil halaman HTML dari website target:**  
  Menggunakan `requests.get()` untuk mengunduh konten HTML dari website latihan scraping.
- ✅ **Menelusuri dan mengekstrak data dari elemen HTML:**  
  Dengan bantuan BeautifulSoup, menelusuri struktur HTML dan mengekstrak data seperti nama negara, ibu kota, populasi, dan luas wilayah.
- ✅ **Mengolah dan menyimpan data dalam format terstruktur:**  
  Data yang sudah dikumpulkan disusun dalam bentuk tabel menggunakan Pandas dan kemudian disimpan ke file `.csv` agar bisa digunakan untuk analisis lebih lanjut.

🌐 Selamat mencoba, bereksplorasi, dan semoga scraping-mu bermanfaat! 🚀
