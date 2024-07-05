# PRAKTIKUM 3

import cv2
import matplotlib.pyplot as plt

Bagian ini mengimpor pustaka OpenCV (cv2) untuk pemrosesan gambar dan Matplotlib (plt) untuk visualisasi.

img = cv2.imread("gambar.png") # Ganti dengan path gambar Anda
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

Kode ini membaca gambar dengan cv2.imread dan mengubahnya menjadi gambar grayscale dengan cv2.cvtColor

fix, axs = plt.subplots(1, 2, figsize = (10,5))
ax = axs.ravel()
ax[0].hist(gray.ravel(), bins=256)
ax[0].set_title("Histogram")
ax[1].imshow(thresh, cmap = 'gray')
ax[1].set_title("Gambar Threshold")

kode diatas membuat histogram dari gambar grayscale dan menampilkan hasil thresholding.

gray1 = cv2.cvtColor(img_line, cv2.COLOR_BGR2RGB)
fix, axs = plt.subplots(1, 2, figsize = (10,10))
ax = axs.ravel()
ax[0].imshow(gray, cmap = 'gray')
ax[0].set_title("Gambar Grayscale")
ax[1].imshow(gray1, cmap = 'gray')
ax[1].set_title("Gambar Edges")

Kode di atas menampilkan gambar grayscale dan gambar dengan edges yang dideteksi.

cnts = cv2.findContours(edges.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)

Bagian diatas menggunakan cv2.findContours untuk mendeteksi kontur pada gambar hasil edge detection.

fix, ax = plt.subplots(figsize=(10,10))
ax.imshow(img_contours)
ax.set_title("Gambar dengan Kontur")

Kode diatas menampilkan gambar asli dengan kontur yang telah dideteksi

gray1 = cv2.cvtColor(img_line, cv2.COLOR_BGR2RGB)
fix, axs = plt.subplots(1, 2, figsize = (10,10))
ax = axs.ravel()
ax[0].imshow(gray, cmap = 'gray')
ax[0].set_title("gambar grayscale")
ax[1].imshow(gray1, cmap = 'gray')
ax[1].set_title("gambar edges")

Bagian akhir dari notebook menampilkan dua gambar: satu dalam grayscale dan satu lagi dengan hasil deteksi edges.


# PRAKTIKUM 4
