# LAPORAN PRAKTIKUM METODE KOMPUTASI

## Judul
**Implementasi Metode STA/LTA (Short Term Average / Long Term Average) pada Sinyal Audio Menggunakan Python dan GUI (Tkinter)**

## Laporan
Pada praktikum metode komputasi ini, kelompok kami belajar bagaimana menerapkan metode **STA/LTA (Short Term Average / Long Term Average)** untuk menganalisis perubahan energi pada sinyal audio. Metode STA/LTA ini sering digunakan dalam bidang pemrosesan sinyal, seperti pada sinyal audio, getaran, maupun seismik, untuk mendeteksi adanya kejadian signifikan atau perubahan mendadak pada amplitudo sinyal.

**Tujuan utama dari praktikum ini adalah:**
- Memahami konsep dasar metode STA/LTA sebagai detektor perubahan amplitudo sinyal.
- Mengimplementasikannya menggunakan bahasa pemrograman **Python**.
- Membangun antarmuka **GUI (Graphical User Interface)** dengan modul **Tkinter** agar analisis menjadi lebih interaktif.
- Menginterpretasikan hasil visualisasi perbandingan antara sinyal asli dan rasio STA/LTA terhadap waktu.

---

### Teori
Secara teoritis, metode STA/LTA bekerja dengan membandingkan dua nilai rata-rata energi sinyal yang diukur dalam rentang waktu berbeda:

- **STA (Short Term Average)**: rata-rata energi sinyal dalam jangka waktu pendek → merepresentasikan kondisi terkini sinyal.
- **LTA (Long Term Average)**: rata-rata energi dalam jangka waktu panjang → menggambarkan latar belakang sinyal.

Ketika terjadi **lonjakan energi**, nilai STA meningkat lebih cepat daripada LTA, sehingga **rasio STA/LTA naik tajam**. Nilai rasio tinggi menandakan adanya *event* signifikan (contoh: suara keras, hentakan, gempa).

---

### Rumus Matematis
Metode STA/LTA dapat dituliskan sebagai berikut:

$$
STA(t) = \frac{1}{N_{STA}} \sum_{i=0}^{N_{STA}-1} x^2(t - i)
$$

$$
LTA(t) = \frac{1}{N_{LTA}} \sum_{i=0}^{N_{LTA}-1} x^2(t - i)
$$

$$
R(t) = \frac{STA(t)}{LTA(t)}
$$

> **Keterangan:**
> - $ x(t) $: amplitudo sinyal pada waktu $ t $
> - $ N_{STA} $: jumlah sampel jendela STA
> - $ N_{LTA} $: jumlah sampel jendela LTA
> - $ R(t) > 1 $ (jauh di atas 1) → **event signifikan terdeteksi**

---

### Implementasi Program
Kami menggunakan pustaka Python berikut:

| Pustaka | Fungsi |
|--------|--------|
| `numpy` | Perhitungan numerik & konvolusi |
| `matplotlib` | Visualisasi grafik |
| `tkinter` | GUI interaktif |
| `scipy.io.wavfile` | Membaca file `.wav` |
| `pydub` | Konversi `.mp3` ke data numerik |

**Data uji:**  
File audio `.wav` dan `.mp3` berisi percakapan dan musik.

---

### Langkah Implementasi
1. **Impor pustaka** yang diperlukan.
2. Buat kelas `STALTA`:
   - Menghitung STA, LTA, dan rasio menggunakan **konvolusi kuadrat sinyal**.
3. Buat kelas `STA_LTA_App` (GUI dengan Tkinter):
   - Pilih file audio.
   - Atur panjang jendela STA & LTA.
   - Tampilkan grafik:
     - Grafik 1: **Sinyal asli vs waktu**
     - Grafik 2: **Rasio STA/LTA vs waktu** (dengan arsiran merah/biru untuk jendela)

---

### Hasil dan Analisis
Metode STA/LTA **berhasil mendeteksi** bagian sinyal dengan peningkatan energi mendadak:
- Lonjakan rasio STA/LTA → menandai suara keras atau transisi musik.
- Efektif pada sinyal **percakapan** dan **musik**.
- GUI Tkinter membuat analisis **lebih interaktif dan mudah digunakan**.

> Metode ini dapat diadaptasi untuk **sinyal seismik** atau **getaran** dalam geofisika.

---

## Kesimpulan
Penerapan metode **STA/LTA dengan Python** memberikan pengalaman berharga dalam:
- Memahami **teori deteksi sinyal**.
- Praktik **pemrograman ilmiah**.
- Pengaruh parameter jendela terhadap **sensitivitas deteksi**.
- Pentingnya **visualisasi dan GUI** dalam interpretasi data.

Melalui praktikum ini, kami tidak hanya menguasai konsep matematis, tetapi juga mampu membuat **aplikasi nyata** untuk mendeteksi peristiwa pada sinyal audio — siap dikembangkan untuk aplikasi seismik atau monitoring getaran.

---