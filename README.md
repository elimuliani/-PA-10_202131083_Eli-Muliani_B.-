
# Word Segmentation (UAS PENGCIT)
Word segmentation pada pengolahan citra adalah proses untuk memisahkan teks dalam gambar menjadi unit-unit kata yang terpisah. Tujuan dari word segmentation adalah untuk mengidentifikasi batas antara setiap kata dalam gambar teks sehingga teks tersebut dapat dianalisis atau diproses lebih lanjut secara individual.

# Langkah-Langkah Pengerjaan
## 1. Memasukkan Foto
karena saya mendapat bagian "e (Word Segmentation)" jadi tugas saya adalah menggunakan nama lengkap saya yaitu 'Eli Muliani' saya membuatnya di notes hp saya tipe A32 merk SAMSUNG. Setelah itu saya memasukkan gambar nama yang telah saya buat kedalam folder python yang diberi nama "UAS".
## 2. Membuat Program di jupyternotebok
Klik bagian pojok kanan "new" lalu pilih " python 3 (ipykernel), setelah itu halaman langsung pada bagian untuk mulai meng-coding.
## 3. Start 
saya mengubah nama judulnya yang awalnya "untitled" klik "Rename" diubah menjadi "UAS PENGCIT BAGIAN (e)". setelah itu mulai saya mulai dengan mengimpor gambar "Inport Gambar", setelah itu "Convert to Binary", yang terakhir "Kontur Pada Gambar", .
## 4. END
Untuk penjelasan codingan ada dibawah. dan link halaman tugas sudah saya cantumkan pada bagian bawah.

# ------------------------------------

## Penjelasan Codingan
#### Mengimpor Library, Membaca dan Mengatur gambar
Di bagian ini, gambar dengan nama file 'eli.jpg' dibaca menggunakan 'cv.imread()'. Kemudian, ukuran gambar asli diambil menggunakan gambar.shape, yaitu tinggi, lebar, dan jumlah saluran warna (channels). Jika lebar gambar melebihi 1000 piksel, maka gambar akan diubah ukurannya agar lebarnya menjadi 1000 piksel dan tingginya disesuaikan agar menjaga rasio aspek gambar. Hal ini dilakukan untuk menghindari gambar yang terlalu besar saat ditampilkan
#### Membuat fungsi thresholding
Fungsi 'thresholding()' digunakan untuk mengubah gambar menjadi citra biner menggunakan metode thresholding. Pertama, gambar diubah menjadi citra grayscale menggunakan 'cv.cvtColor()'. Kemudian, dengan menggunakan 'cv.threshold()', citra grayscale tersebut diterapkan threshold dengan nilai ambang 80. Hasilnya adalah citra biner dengan piksel hitam dan putih yang ditampilkan menggunakan 'plt.imshow()'.
#### Dilasi dan mencari kontur eksternal pada gambar hasil thresholding
Di sini, kita membuat kernel dengan ukuran (3, 85) yang akan digunakan dalam operasi dilasi menggunakan 'np.ones()'. Gambar hasil thresholding thresh_img kemudian diperoleh dengan mengaplikasikan operasi dilasi pada citra biner menggunakan 'cv.dilate()'. Hasil dilasi disimpan dalam variabel dilated. Selanjutnya, dilakukan pencarian kontur eksternal pada gambar dilated menggunakan 'cv.findContours()', dengan mode 'cv.RETR_EXTERNAL' untuk mencari kontur eksternal saja. Kontur-kontur tersebut diurutkan berdasarkan koordinat y dari bounding rectangle yang melingkupi setiap kontur menggunakan 'sorted()', dan hasilnya disimpan dalam variabel 'sorted_contours_line'.
#### Menggambar persegi panjang pada setiap kontur garis
Di bagian ini, kita membuat salinan gambar asli dengan 'gambar2 = gambar.copy()'. Kemudian, menggunakan loop 'for', untuk setiap kontur garis dalam 'sorted_contours_line', kita mendapatkan koordinat batas persegi panjang menggunakan 'cv.boundingRect()'. Dengan menggunakan 'cv.rectangle()', persegi panjang dengan batas yang telah diperoleh tersebut digambar pada gambar 'gambar2' dengan warna (4, 100, 250) dan ketebalan garis 2. Akhirnya, gambar 'gambar2' yang telah memiliki persegi panjang pada setiap kontur garis ditampilkan menggunakan 'plt.imshow()'.
#### Dilasi dan word segmentation pada setiap garis
Di bagian ini, kita membuat kernel dengan ukuran (3, 5) yang akan digunakan dalam operasi dilasi selanjutnya menggunakan 'np.ones()'. Gambar hasil thresholding 'thresh_img' diperoleh dengan mengaplikasikan operasi dilasi pada citra biner menggunakan 'cv.dilate()', dan hasilnya disimpan dalam variabel dilated2. Salinan gambar asli dibuat dengan 'gambar3 = gambar.copy()'. Selanjutnya, untuk setiap garis dalam 'sorted_contours_line', kita mendapatkan koordinat batas garis menggunakan 'cv.boundingRect()', dan bagian garis tersebut diambil dari gambar dilated dilated2 menggunakan slicing untuk mendapatkan region of interest (ROI) dengan nama 'roi_line'. Selanjutnya, pada ROI 'roi_line', dilakukan pencarian kontur eksternal menggunakan 'cv.findContours()', dan kontur-kontur tersebut diurutkan berdasarkan koordinat x dari bounding rectangle yang melingkupi setiap kontur menggunakan 'sorted(). Dalam loop nested', untuk setiap kontur kata dalam 'sorted_contours_word', dilakukan pemotongan huruf dari gambar asli menggunakan slicing dengan koordinat yang diperoleh, dan persegi panjang dengan batas yang telah diperoleh tersebut digambar pada gambar gambar3 dengan warna (255, 255, 100) dan ketebalan garis 2 menggunakan 'cv.rectangle()'. Akhirnya, gambar gambar3 yang telah memiliki persegi panjang pada setiap huruf ditampilkan menggunakan 'plt.imshow()'.




## 🔗 Links
[![UAS](https://img.shields.io/badge/my_Tugas-000?style=for-the-badge&logo=ko-fi&logoColor=white)](http://localhost:8888/notebooks/UAS/UAS%20PENGCIT%20BAGIAN%20(e).ipynb)



