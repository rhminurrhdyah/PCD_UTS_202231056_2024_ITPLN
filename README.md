# PCD_UTS_202231056_2024_ITPLN

## UTS NO 1
### Mendeklarasikan Library

```bash
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
Disini kita menggunakan tiga pustaka yaitu Open Cv(cv2), Numpy('numpy), dan Matplotlib('matplotlib.pyplot'). pusetka open vc digunakan untuk membaca dan manioulasi citra, pustaka numpy digunakan untuk oprasi array, dan Pustaka Matplotlib digunakan untuk visualisasi

### Mendeklarasikan Membaca dan Mengubah Gambar ke format RGB
```bash
img = cv2.imread('nama.jpg')
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
Kita menggunakan fungsi 'cv2.imread()' untuk membaca file/citra yang diberikan. Citra yang diberikan (di imporkan) awalanya akan dibaca dalam mode BGR(Blue, Green, Red) lalu disini kita mengubahnya ke mode RGB(red, green, blue) agar citra bisa ditampilkan dan diproses dengan benar, dengan menggunakan fungsi 'cv2.cvtColor()'.

### Membagi Citra Menjadi Komponen R, G, B
```bash
R, G, B = cv2.split(img)
```
Setelah mengonversi citra dari mode brg ke mode brg, kita memisahkan tiga komponen warna utamal(Red, Green, Blue) menggunakan fungsi 'cv2.split()'. Dimana setelah kita memisahkan tiga komponen warna tersebut  akan menghasilkan tiga matrix Numpy yang mewakili masing maaing komponen warna.

### Menampilkan Citra yang sudah dibagi
```bash
fig, axs = plt.subplots(1, 4, figsize=(20,20))

axs[0].imshow(img)
axs[0].set_title('Citra Asli')

axs[1].imshow(R, cmap='gray')
axs[1].set_title('Komponen Merah')

axs[2].imshow(G, cmap='gray')
axs[2].set_title('Komponen Hijau')

axs[3].imshow(B, cmap='gray')
axs[3].set_title('Komponen Biru')

for ax in axs:
    ax.axis('off')

plt.show()
```
Disini kita menampilkan gambar serta tiga komponen warna lainnya (Red, Green, Blue) dalam empat bagian yang berbeda pada output. Pertama, kita membuat tempatnya (figur) seukuran besar di mana gambar akan ditampilkan. Kemudian, kita bagi tempat ini menjadi empat bagian kecil, yang masing-masing akan menampilkan sesuatu yang berbeda. Bagian pertama menampilkan gambar aslinya. Kemudian, bagian-bagian berikutnya menampilkan masing-masing warna utama dari gambar tersebut (merah, hijau, dan biru) dalam bentuk abu-abu. Lalu, kita hapus sumbu-sumbu agar tampilan menjadi lebih bersih.

Ketika kita memisahkan dan menampilkan komponen warna dari sebuah gambar, seperti merah, hijau, dan biru, kita bisa melihat bagaimana masing-masing warna berkontribusi terhadap gambar aslinya. Misalnya, jika gambar tersebut memiliki banyak warna merah yang kuat, ketika kita melihat komponen merah (R), kita akan melihat area yang berwarna merah cerah. Namun, jika ada area dalam gambar yang kurang memiliki warna merah, maka pada komponen merah (R) tersebut, area tersebut akan terlihat lebih gelap atau memiliki nilai piksel yang rendah. 

### Membuat Histogram
```bash
#membuat Histogram untuk citra asli 
histimg = cv2.calcHist([img],[0],None,[256],[0,256])

#membuat histogram untuk komponen R (merah)
histR = cv2.calcHist([R],[0],None,[256],[0,256])

#membuat histogram untuk komponen G (Hijau)
histG = cv2.calcHist([G],[0],None,[256],[0,256])

#membuat histogram untuk komponen B (biru)
histB = cv2.calcHist([B],[0],None,[256],[0,256])
```
Disini kita menghitung dan dan membuat histogram untuk gambar asli serta untuk masing masing komponen warna(Red, Green, Blue). Pertama, histogram untuk gambar asli dihitung menggunakan cv2.calcHist() dengan parameter gambar asli (img). Hasilnya akan menunjukkan distribusi intensitas piksel dalam skala abu-abu dari 0 hingga 255. Selanjutnya, histogram untuk setiap komponen warna diproses secara terpisah. Misalnya, histR menghitung histogram untuk komponen warna merah (R) dari gambar. Proses ini diulangi untuk komponen hijau (G) dan biru (B). Hasilnya adalah empat histogram yang mewakili distribusi intensitas piksel dari masing-masing komponen warna. 

### Menampilkan Histogram
```bash
fig, axs = plt.subplots(2, 2, figsize=(20, 10))

axs[1,1].plot(histimg, color='black')
axs[1,1].set_title('Histogram Gambar Asli')

axs[0,0].plot(histR, color='red')
axs[0,0].set_title('Histogram Komponen Merah')

axs[0,1].plot(histG, color='green')
axs[0,1].set_title('Histogram Komponen Hijau')

axs[1,0].plot(histB, color='blue')
axs[1,0].set_title('Histogram Komponen Biru')

plt.show()
```
Lalu kita menampilkan empat histogram dalam satu tampilan menggunakan subplot. Pertama, kita membuat sebuah figur dengan empat subplot menggunakan plt.subplots(2, 2, figsize=(20, 10)). Ini berarti kita memiliki empat bagian di layar, yang akan menampilkan histogram gambar asli serta histogram untuk masing-masing komponen warna (merah, hijau, dan biru). Kemudian, kita memplot histogram gambar asli dan masing-masing histogram komponen warna pada subplot yang sesuai. Misalnya, axs[1,1].plot(histimg, color='black') memplot histogram gambar asli pada subplot di baris kedua dan kolom kedua. Setelah memplot histogram, kita memberikan judul untuk setiap subplot menggunakan set_title(), misalnya, 'Histogram Gambar Asli' untuk histogram gambar asli. Setiap histogram diplot dengan warna yang sesuai dengan komponen warna yang direpresentasikan, seperti merah untuk komponen merah, hijau untuk komponen hijau, dan biru untuk komponen biru. Lalu kita menggunakan plt.show() untuk menampilkan plot yang telah dibuat. Hasilnya kita bisa membandingkan distribusi intensitas piksel dari gambar asli serta masing-masing komponen warnanya.


## UTS NO 2
### Mendeklarasikan Library
```bash
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
Disini kita menggunakan tiga pustaka yaitu Open Cv(cv2), Numpy('numpy), dan Matplotlib('matplotlib.pyplot'). pusetka open vc digunakan untuk membaca dan manioulasi citra, pustaka numpy digunakan untuk oprasi array, dan Pustaka Matplotlib digunakan untuk visualisasi

### Membaca dan Mengubah Gambar dari format RGB ke Gray
```bash
img = cv2.imread('nama.jpg')
gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
```
Disini kita membaca sebuah gambar menggunakan OpenCv dengan fungsi 'cv2.imread()', yang memungkinkan untuk membaca gambar dari file yang disediakan dan menyimpannya dalam variabel'img'. Proses ini menghasilkan representasi digital dari gambar dalam bentuk array Numpy. Selanjutnya citra yang telah dibaca('img') diubah menjadi citra grayscale dengan menggunakan fungsi 'cv2.cvtColor(), fungsi ini mengonversi citra dari mode warna rgb ke gratscale dengan menggunakan 'cv2.COLOR_RGB2GRAY, yang berarti menghilangkan informasi warna dan menyimpan hanya informasi intensitas piksel dalam gambar.

### Membagi dan Menambilkan citra menjadi beberapa kategori warna dari Nilai Ambang Batas
```bash
fig, axs = plt.subplots (2, 2, figsize=(15,15))

(thresh, binary1) = cv2.threshold(gray, 0, 0, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')

(thresh, binary2) = cv2.threshold(gray, 104, 255, cv2.THRESH_BINARY)
axs[0,1].imshow(binary2, cmap = 'binary')
axs[0,1].set_title('BLUE')

(thresh, binary3) = cv2.threshold(gray, 150, 255, cv2.THRESH_BINARY)
axs[1,0].imshow(binary3, cmap = 'binary')
axs[1,0].set_title('RED-BLUE')

(thresh, binary4) = cv2.threshold(gray, 190, 255, cv2.THRESH_BINARY)
axs[1,1].imshow(binary4, cmap = 'binary')
axs[1,1].set_title('RED-GREEN-BLUE')
```
Lalu kita menggunakan Matplotlib untuk membuat subplot 2x2 dengan ukuran 15x15 inci, yang akan menampung empat citra biner yang dihasilkan dari proses thresholding. Thresholding adalah teknik dalam pemrosesan citra yang digunakan untuk mengonversi citra grayscale menjadi citra biner, di mana piksel dengan intensitas di atas ambang tertentu akan diubah menjadi putih, sedangkan piksel dengan intensitas di bawah ambang tersebut akan diubah menjadi hitam. Kemudian, kita melakukan thresholding pada citra grayscale (gray) dengan menggunakan nilai ambang yang berbeda untuk setiap citra **dengan cara mengatur nilai ambang batasnya dengan manual** untuk mendapatkan citra yang diinginkan. Pertama, pada citra biner pertama (binary1), kita menggunakan nilai ambang 0, yang tidak akan menyebabkan perubahan apa pun pada citra karena semua piksel akan diubah menjadi hitam karena ambang bawahnya juga 0. Pada citra biner kedua (binary2), nilai ambang 104 digunakan, yang akan menyebabkan piksel dengan intensitas di bawah 104 diubah menjadi hitam, sedangkan piksel dengan intensitas di atasnya diubah menjadi putih. Proses ini diulangi untuk citra biner ketiga (binary3) dengan nilai ambang 150 dan citra biner keempat (binary4) dengan nilai ambang 190. Setiap citra biner ditampilkan pada subplot yang sesuai, dengan menggunakan imshow() untuk menampilkan citra dan set_title() untuk memberikan judul pada setiap subplot, yang mencerminkan nilai ambang yang digunakan dalam proses thresholding. Penambahan atribut cmap='gray' atau cmap='binary' pada imshow() digunakan untuk menentukan skema warna yang digunakan untuk menampilkan citra, yaitu abu-abu untuk citra biner yang dihasilkan dari thresholding dan biner untuk citra biner dengan judul "BLUE", "RED-BLUE", dan "RED-GREEN-BLUE".

### Teori yang Mendukung
Pemrosesan citra menggunakan Python dan pustaka-pustaka seperti OpenCV, NumPy, dan Matplotlib. Pertama, konsep dasar pemrosesan citra melibatkan pembacaan dan manipulasi gambar. Dalam Projek ini, Pustaka OpenCV digunakan untuk membaca dan memanipulasi gambar, termasuk konversi antara format citra seperti BGR dan RGB. Ini penting untuk memastikan gambar dapat ditampilkan dan diproses dengan benar. Selanjutnya, konversi warna merupakan langkah penting dalam pemrosesan citra untuk memastikan konsistensi dan kelayakan analisis. Selanjutnya konversi warna dilakukan dari format BGR ke RGB untuk memudahkan interpretasi dan visualisasi citra. Pisah komponen warna adalah konsep lain yang penting, memungkinkan kita untuk menganalisis kontribusi masing-masing warna terhadap citra secara terpisah. Dalam projek ini, komponen warna utama (merah, hijau, dan biru) dipisahkan menggunakan pustaka NumPy, penting dalam analisis warna dan deteksi objek. Kemudian, visualisasi citra dan histogramnya menjadi langkah berikutnya yang esensial. Pustaka Matplotlib digunakan untuk menampilkan citra dan histogramnya dengan jelas. Histogram citra memberikan informasi tentang distribusi intensitas piksel dalam citra, sementara visualisasi citra memungkinkan kita untuk memahami struktur dan konten visual dari citra tersebut. Terakhir, teknik thresholding juga diterapkan dalam kedua skrip untuk memisahkan objek dari latar belakang. Proses thresholding dilakukan untuk menghasilkan citra biner berdasarkan nilai ambang batas yang ditentukan, memungkinkan kita untuk memisahkan objek dari latar belakang atau mengidentifikasi fitur tertentu dalam citra.
