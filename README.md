
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

import cv2, mengimport modul OpenCV. import numpy as np, mengimport modul NumPy. NumPy merupakan library yang digunakan untuk komputasi numerik dalam Python. import matplotlib.pyplot as plt, mengimport modul pyplot dari library Matplotlib dengan alias plt. Matplotlib adalah library untuk visualisasi data dalam Python

    image = cv2.imread("hp.jpeg")

cv2.imread("hp.jpeg") mengambil gambar dengan nama file "hp.jpeg" dan membacanya ke dalam bentuk matriks/array menggunakan fungsi imread dari OpenCV dengan variabel image.

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
    tepi = cv2.Canny(gray, 30, 150)
    kontur,_= cv2.findContours(tepi,cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY), mengkonversi gambar image dari mode warna BGR (Blue-Green-Red) ke mode grayscale (skala keabuan) menggunakan fungsi cvtColor dari OpenCV.
tepi = cv2.Canny(gray, 30, 150), menggunakan metode Canny pada gambar gray untuk mendeteksi tepi gambar.kontur, _ = cv2.findContours(tepi, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE), menggunakan fungsi cv2.findContours untuk menemukan kontur pada gambar tepi tepi

    imgor = np.copy(image)
    cv2.drawContours(imgor, kontur, -1, (0, 0, 255), 3)
    imgwhite = np.ones_like(image)*255
    cv2.drawContours(imgwhite, kontur, -1, (0, 0, 255), 3)

imgor = np.copy(image), membuat salinan dari gambar image menggunakan fungsi np.copy dari NumPy.cv2.drawContours(imgor, kontur, -1, (0, 0, 255), 3) ,menggambar kontur pada gambar imgor menggunakan fungsi cv2.drawContours dari OpenCV,imgwhite = np.ones_like(image)*255, membuat gambar berukuran dan jenis yang sama dengan image menggunakan fungsi np.ones_like dari NumPy.cv2.drawContours(imgwhite, kontur, -1, (0, 0, 255), 3)menggambar kontur pada gambar imgwhite menggunakan fungsi cv2.drawContours

    fig, axes = plt.subplots(1, 3, figsize = (10, 11))
    ax = axes.ravel()

    ax[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    ax[0].set_title('Original Image')
    ax[1].imshow(cv2.cvtColor(imgwhite, cv2.COLOR_BGR2RGB))
    ax[1].set_title('Image With Contur')
    ax[2].imshow(cv2.cvtColor(imgor, cv2.COLOR_BGR2RGB))
    ax[2].set_title('Image With Contur2')

fig, axes = plt.subplots(1, 3, figsize=(10, 11)): Membuat sebuah figure (fig) dengan tiga sumbu (axes) yang disimpan dalam variabel axes. 1, 3 menunjukkan bahwa akan ada 1 baris dan 3 kolom untuk tiga sumbu, dan figsize=(10, 11) mengatur ukuran figure menjadi 10 inci lebar dan 11 inci tinggi. ax[0, 1, 2] untuk menampilkan gambar dengan memanggil variabel gambar, dan titlenya.

