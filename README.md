# PRAKTIKUM 3

### Pada line 1 dan 2 ini untuk mengimpor pustaka OpenCV (cv2) untuk pemrosesan gambar dan Matplotlib (plt) untuk visualisasi.
1. import cv2

2. import matplotlib.pyplot as plt

### Lalu line 3 dan 4 dibawah ini untuk membaca gambar dengan cv2.imread dan mengubahnya menjadi gambar grayscale dengan cv2.cvtColor
3. img = cv2.imread("gambar.png") # Ganti dengan path gambar Anda

4. gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

### Line 5,6,7,8,9,10 dibawah untuk membuat histogram dari gambar grayscale dan menampilkan hasil thresholding.
5. fix, axs = plt.subplots(1, 2, figsize = (10,5))

6. ax = axs.ravel()

7. ax[0].hist(gray.ravel(), bins=256)

8. ax[0].set_title("Histogram")

9. ax[1].imshow(thresh, cmap = 'gray')

10. ax[1].set_title("Gambar Threshold")

### Line 11,12,13,14,15,16,17 di bawah untuk menampilkan gambar grayscale dan gambar dengan edges yang dideteksi.
11. gray1 = cv2.cvtColor(img_line, cv2.COLOR_BGR2RGB)

12. fix, axs = plt.subplots(1, 2, figsize = (10,10))

13. ax = axs.ravel()

14. ax[0].imshow(gray, cmap = 'gray')

15. ax[0].set_title("Gambar Grayscale")

16. ax[1].imshow(gray1, cmap = 'gray')

17. ax[1].set_title("Gambar Edges")

### Lalu pada line 18 dibawah ini menggunakan cv2.findContours untuk mendeteksi kontur pada gambar hasil edge detection.
18. cnts = cv2.findContours(edges.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)

### line 19,20,21 dibawah untuk menampilkan gambar asli dengan kontur yang telah dideteksi
19. fix, ax = plt.subplots(figsize=(10,10))

20. ax.imshow(img_contours)

21. ax.set_title("Gambar dengan Kontur")

### kemudian line 22,23,24,25,26,27,28 dibawah merupakan kodingan akhir dari notebook menampilkan dua gambar: satu dalam grayscale dan satu lagi dengan hasil deteksi edges.
22. gray1 = cv2.cvtColor(img_line, cv2.COLOR_BGR2RGB)

23. fix, axs = plt.subplots(1, 2, figsize = (10,10))

24. ax = axs.ravel()

25. ax[0].imshow(gray, cmap = 'gray')

26. ax[0].set_title("gambar grayscale")

27. ax[1].imshow(gray1, cmap = 'gray')

28. ax[1].set_title("gambar edges")

# ____________________________________________________________
# PRAKTIKUM 4
### Line 1,2,3,4,5 untuk mengimpor pustaka yang diperlukan: OpenCV (cv2) untuk pemrosesan gambar, Matplotlib (plt) untuk visualisasi, Numpy (np) untuk komputasi numerik, dan skimage untuk data dan fitur citra.
1. import cv2

2. import matplotlib.pyplot as plt

3. import numpy as np

4. from skimage import data

5. from skimage.feature import graycomatrix, graycoprops

### Line 6,7,8,9,10,11,12,13 untuk membaca gambar astronaut dari dataset skimage dan mengubahnya menjadi gambar grayscale menggunakan OpenCV. Gambar asli (RGB) dan gambar grayscale ditampilkan berdampingan.
6. img = skimage.data.astronaut()

7. img_gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)


8. fig, axs = plt.subplots(1, 2, figsize = (10, 10))


9. ax = axs.ravel()


10. ax[0].imshow(img)

11. ax[0].set_title("RGB")


12. ax[1].imshow(img_gray, cmap="gray")

13. ax[1].set_title("GRAY")

### Line 14,15,16 ini untuk menghitung mean (rata-rata) dan standar deviasi dari intensitas piksel pada gambar grayscale.
14. mean = np.mean(img_gray.ravel())

15. std = np.std(img_gray.ravel())


16. print(mean, std)

### Line 17 ini untuk menghitung Gray Level Co-occurrence Matrix (GLCM) untuk gambar grayscale dengan jarak 1 piksel dan sudut 0 derajat. GLCM digunakan untuk mengukur tekstur citra.
17. glcm = graycomatrix(img_gray, distances=[1], angles=[0], levels=256, symmetric=True, normed=True)

### Kemudian pada line 18,19,20,21,22 untuk mengekstraksi beberapa properti tekstur dari GLCM, yaitu kontras, dissimilarity, homogenitas, energi, dan korelasi.
18. contrast = graycoprops(glcm, 'contrast')[0,0]

19. dissimilarity = graycoprops(glcm, 'dissimilarity')[0,0]

20. homogeneity = graycoprops(glcm, 'homogeneity')[0,0]

21. energy = graycoprops(glcm, 'energy')[0,0]

22. correlation = graycoprops(glcm, 'correlation')[0,0]

### Lalu pada line 23,24,25,26,27 untuk menampilkan nilai-nilai dari properti tekstur yang telah diekstraksi.
23. print(f'contrast : {contrast}')

24. print(f'dissimilarity : {dissimilarity}')

25. print(f'homogeneity : {homogeneity}')

26. print(f'energy : {energy}')

27. print(f'correlation : {correlation}')

