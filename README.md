
## Deteksi Gambar Contur

Deteksi gambar kontur adalah proses untuk mengidentifikasi dan mengekstraksi garis-garis tepi yang ada dalam suatu gambar. Garis tepi ini mewakili perubahan signifikan dalam intensitas piksel pada gambar, dan deteksi kontur dapat digunakan untuk berbagai tujuan seperti pengenalan objek, segmentasi gambar, atau pengolahan citra lainnya.

Metode deteksi kontur umumnya melibatkan analisis intensitas piksel dalam gambar. Beberapa algoritma yang umum digunakan dalam deteksi kontur antara lain:

Deteksi Tepi Sobel: Algoritma ini menggunakan operasi konvolusi pada gambar dengan kernel Sobel untuk menghitung gradien intensitas piksel dalam arah horizontal dan vertikal. Gradien ini kemudian digunakan untuk menentukan piksel mana yang berada di tepi.

Deteksi Tepi Canny: Algoritma Canny adalah metode deteksi tepi yang populer dan memiliki beberapa langkah. Pertama, gambar dihaluskan menggunakan filter Gaussian untuk mengurangi derau. Kemudian, gradien intensitas piksel dihitung, dan tepi kuat diidentifikasi berdasarkan ambang batas atas dan batas bawah yang ditentukan. Langkah terakhir melibatkan penyatuan dan penyempurnaan garis tepi yang dihasilkan.

Transformasi Hough: Metode ini mengubah ruang piksel menjadi ruang parameter garis. Pada transformasi Hough, setiap piksel yang terletak pada garis akan memberikan suara untuk parameter garis yang sesuai. Ini memungkinkan deteksi garis secara akurat dalam gambar, bahkan jika garis tersebut tidak sempurna atau terputus.

## Penjelasan Program

    import cv2
    import numpy as np
    import matplotlib.pyplot as plt

Import library Program dimulai dengan mengimpor library yang diperlukan, yaitu cv2 (OpenCV) dan numpy. OpenCV adalah library populer untuk pengolahan citra dan komputerisasi penglihatan, sedangkan numpy digunakan untuk manipulasi array numerik

    ray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
    tepi = cv2.Canny(gray, 30, 150)
    kontur,_= cv2.findContours(tepi,cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)

Program ini melanjutkan dari tahap sebelumnya, di mana gambar telah dikonversi ke skala keabuan (grayscale) dan tepi telah terdeteksi menggunakan algoritma Canny. Fungsi cv2.findContours() adalah untuk menemukan kontur (bentuk atau garis tepi) dalam gambar menggunakan pendekatan tertentu

imgor = np.copy(image): Membuat salinan dari gambar asli (image) menggunakan fungsi np.copy(). Hal ini dilakukan untuk menghindari mengubah gambar asli saat menggambar kontur.

cv2.drawContours(imgor, kontur, -1, (0, 0, 255), 3): Menggambar kontur pada gambar imgor dengan menggunakan fungsi cv2.drawContours(). Argumen yang digunakan adalah imgor sebagai gambar target, kontur sebagai daftar kontur yang ditemukan sebelumnya, -1 untuk menggambar semua kontur dalam daftar, (0, 0, 255) sebagai warna garis (dalam urutan BGR, yaitu warna merah), dan 3 sebagai ketebalan garis.

    fig, axes = plt.subplots(1, 3, figsize = (10, 11))
    ax = axes.ravel()

    ax[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    ax[0].set_title('Original Image')
    ax[1].imshow(cv2.cvtColor(imgwhite, cv2.COLOR_BGR2RGB))
    ax[1].set_title('Image With Contur')
    ax[2].imshow(cv2.cvtColor(imgor, cv2.COLOR_BGR2RGB))
    ax[2].set_title('Image With Contur2')

fig, axes = plt.subplots(1, 3, figsize=(10, 11)): Membuat sebuah figure (fig) dengan tiga sumbu (axes) yang disimpan dalam variabel axes. 1, 3 menunjukkan bahwa akan ada 1 baris dan 3 kolom untuk tiga sumbu, dan figsize=(10, 11) mengatur ukuran figure menjadi 10 inci lebar dan 11 inci tinggi. ax[0, 1, 2] untuk menampilkan gambar dengan memanggil variabel gambar, dan titlenya.

