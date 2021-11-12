# Deteksi Plat Nomor Kendaraan Indonesia
Deteksi Plat Nomor Kendaraan Indonesia dari potongan gambar plat nomor yang sudah di melewati proses Pengambilan *Region of Interest* (ROI) Plat nomor kendaraan dari penangkapan citra gambar di lapangan (proses pengambilan ROI tidak dilampirkan pada repository ini)

## Masters.ipynb
File ini berisi algoritma *image processing* untuk mendeteksi bagian citra gambar yang merupakan plat kendaraan bermotor hasil pemngambilan *Region of Interest* (ROI) sebelumnya , sekaligus menggunakan model dari Keras-OCR untuk membaca tulisan pada plat nomor kendaraan.

![image](https://github.com/maulanaisa/plate-detector/blob/main/Alur_proses.png)

Dua metode digunakan pada proses kali ini, yaitu menggunakan proses *closed contour & edge detection* dan yang kedua menggunakan *morphological operation*. Dimana metode pertama diprioritaskan terlebih dahulu dibanding metode kedua untuk memaksimalkan akurasi hasil pembacaan.

Hal ini kemudian akan dimasukkan ke dalam fungsi yang berguna untuk melakukan perubahan perspektif gambar dengan hanya mengambil 4 titik sudut kontur sehingga dihasilkan transformasi gambar “bird view” yang akan memetakan gambar ke bentuk quadrilateral yang sesuai, hal ini dilakukan dengan menggunakan fungsi warpPerspective di OpenCV.

![image](https://github.com/maulanaisa/plate-detector/blob/main/Deteksi_metode1.png)

![image](https://github.com/maulanaisa/plate-detector/blob/main/Deteksi_metode2.png)

Setelah itu dilakukan koreksi sudut pada gambar hasil transformasi warp dengan mengambil nilai kemiringan kontur plat kendaraan yang sebelumnya terdeteksi. Sehingga sudut dapat dikoreksi agar hasil pembacaan benar dari kiri ke kanan (plat nomor kendaraan di Indonesia).

Pembacaan karakter dari gambar yang sudah melewati proses *preprocessing* selanjutnya menggunakan Keras-OCR yang sudah di *training* kembali menggunakan dataset plat kendaraan bermotor di Indonesia (tidak dilampirkan dalam repository ini). User bisa menggunakan model lainnya untuk membaca karakter pada gambar.

Berikut ini adalah *flow chart* umum dari sistem

![image](https://github.com/maulanaisa/plate-detector/blob/main/Flow_chart.jpg)


### Credit :
- https://www.pyimagesearch.com/2020/09/21/opencv-automatic-license-number-plate-recognition-anpr-with-python/, diakses 9 April 2021

- https://www.pyimagesearch.com/2014/05/05/building-pokedex-python-opencv-perspective-warping-step-5-6/, diakses 9 April 2021

- https://medium.com/programming-fever/license-plate-recognition-using-opencv-python-7611f85cdd6c#:~:text=1.,location%20of%20the%20number%20plate, diakses 9 April 2021

