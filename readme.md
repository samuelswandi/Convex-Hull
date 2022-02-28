    # Pencarian convex hull dengan menggunakan algoritma divide and conquer

    ## requirements
    dibutuhkan depedencies berupa
    ```py
    # numpy
    # pandas
    # matplotlib
    # sklearn

    # command untuk menginstall depedencies :
    py3 -m pip install numpy pandas matplotlib sklearn
    ```
    setelah depedencies di install, maka tinggal menggunakan ipynb untuk menjalankannya

    ## cara menjalankannya

    1. Ke folder bin untuk melihat file "Tucil2_13520075.ipynb"
    2. Untuk menjalankan ipynb, tinggal menekan tombol "run all" yang tertera pada masing-masing IDE
    3. Setelah tombol dijalankan, maka dapat terlihat hasil grafik yang telah dibuat

    ## algoritma secara garis besar

    Ide:
    membagi dataset menjadi dua bagian yaitu atas dan bawah, dengan dibatasi oleh sebuah garis yaitu garis paling kiri dan paling kanan di ruang Eucledian berderajat 2

    Implementasi:
    ```
    leftmost <- titik paling kiri pada dataset
    rightmost <- titik paling kanan pada dataset

    function convexHull(data, leftmost, rightmost):
        garis <- membuat garis dari titik leftmost dan rightmost

        titikTerjauhAtas <- mencari titik terjauh dari atas garis 
        titikTerjauhBawah <- mencari titik terjauh dari bawah garis

        # jika sudah tidak ada lagi titik terjauh di atas garis, maka garis tersebut merupakan bagian convexhull
        if titikTerjauhAtas == None:
            return [leftmost, rightmost]
        if titikTerjauhBawah == None:
            return [leftmost, rightmost]

        { mencari garis convexhull untuk setiap himpupnan subset (kiri dan titik atas terjauh; titik atas terjauh dan kanan) }
        atas <- convexHull(data, leftmost, titikTerjauhAtas) + convexHull(data, titikTerjauhAtas, rightmost)
        bawah <- convexHull(data, leftmost, titikTerjauhBawah) + convexHull(data, titikTerjauhBawah, rightmost)

        return atas + bawah

    ```