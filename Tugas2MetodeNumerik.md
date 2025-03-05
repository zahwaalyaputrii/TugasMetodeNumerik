ZAHWA ALYA PUTRI - 140710230003

# TUGAS 1

Tulis text berikut, menggunakan vim, simpan dalam file bernama paulo.txt:

**For every sunset, there is a sunrise;**
**for every dream that ends, one is born;**
**for every door that closes, another one opens;**
**for every love that ends there is a new beginning;**
**for every departure there is an arrival;**
**for every defeat there is a victory.**

**Nothing is ever finished, as long as there is life.**

Jelaskan bagaimana mengerjakan hal-hal berikut dengan menggunakan awk dan perintah shell lain.

1. Menghitung baris, kata, dan karakter yang terdapat dalam teks.
2. Menemukan baris-baris yang mengandung token teks tertentu, misalnya: ‘love’ ‘victory’, ‘dream’, dan lain-lain.
3. Mengganti bagian dari teks dalam baris, misalnya ‘every’ dengan ‘each’.
4. Menghitung kata dan huruf per baris.

**JAWAB :**
Langkah pertama untuk membuat ke-4 hal diatas adalah sebagai berikut :
1. Membuka command promt Ubuntu
2. Membuat directory atau folder untuk tugas ini dengan memberikan perintah ```mkdir metodenumerik``` kemudian *change directory* dengan perintah ```cd metodenumerik```.
3. Install VIM jika belum ada dengan perintah ```sudo apt install vim```
4. Setelah itu berikan perintah kode sumber dengan format vim namafile.typefile seperti ```vim paulo.txt```.
5. Setelah itu copy dan paste kalimat diatas pada windows vim dengan menekan tombol i untuk insert, jika ingin menyimpan tekan esc --> shift+w, dan shift+q untuk keluar.

## Menghitung Baris, kata, dan karakter yang terdapat dalam teks

Kode berikut menggunakan AWK untuk menghitung jumlah baris, kata, dan karakter dalam file *paulo.txt*.
```awk '{chars += length($0) + 1; words += NF; lines++} END {print "Baris:", lines, "Kata:", words, "Karakter:", chars}' paulo.txt```
 Dimana :
 1. *length($0) + 1* : untuk menghitung jumlah karakter dalam setiap baris termasuk newline.
 2. *NF* : untuk menghitung jumlah kata dalam setiap baris.
 3. *lines++* : untuk menambah jumlah baris.
 4. *END {print "Baris:", lines, "Kata:", words, "Karakter:", chars}' paulo.txt* : untuk mencetak hasil setelah semua baris diproses dalam file paulo.txt.

## Menemukan baris-baris yang mengandung token teks tertentu, misalnya: ‘love’ ‘victory’, ‘dream’, dan 'for'
Kode berikut menggunakan AWK untuk menemukan baris-baris yang mengandung token teks tertentu, misalnya: ‘love’ ‘victory’, ‘dream’, dan 'for' dalam file *paulo.txt*.
```awk "/\b(love|victory|dream)\b/" paulo.txt```
Dimana :
1. *\b* : merupakan batas kata untuk memastikan pencocokan hanya kata lengkap, bukan bagian dari kata lain.
2. | : sebagai operator OR, sehingga cocok dengan salah satu kata dalam daftar.
3. *awk* : mencetak hanya baris yang mengandung setidaknya satu dari kalimat diatas.

## Mengganti bagian dari teks dalam baris, misalnya 'every' dengan 'each'
Kode berikut menggunakan AWK untuk mengganti bagian dari teks dalam baris, misalnya 'every' dengan 'each' dalam file *paulo.txt*.
```awk "{gsub(/\<every\>/, \"each\"); print}" paulo.txt```
Dimana :
1. *awk* untuk menjalankan program awk.
2. *gsub()* merupakan fungsi awk yang mengganti semua kemunculan pola dalam setiap baris.
3. */\<every\>/* menandakan bahwa kata "every" akan diganti.
4. *\"each\"* kata pengganti every.
5. *print}" paulo.txt* mencetak setiap baris setelah perubahan yang terdapat pada file paulo.txt.

## Menghitung kata dan huruf per baris
Kode berikut menggunakan AWK untuk menghitung kata dan huruf per baris dalam file *paulo.txt*.
```awk '{gsub(/\bevery\b/, "each"); print $0, "- Kata:", NF, "Huruf:", length($0)}' paulo.txt```
Dimana :
1. *gsub(/\bevery\b/, "each")* untuk mengganti kata 'every' dengan 'each'.
2. *NF* untuk menghitung kata dalam setiap baris.
3. *print 0, "- Kata:", NF, "Huruf:", length(0)* untuk mencetak baris yang telah dimodifikasi dengan informasi tambahan.
4. *length($0)* untuk menghitung jumlah karakter dalam baris.

# TUGAS 2
Jelaskan dan beri contoh dari pekerjaan-pekerjaan berikut :

1. Melakukan plot dari data yang tersimpan dalam file
2. Menyimpan hasil plot ke dalam file
3. Konversi data menjadi CSV
4. Konversi data menjadi JSON

**JAWAB :**
 ## Melakukan plot dari data yang tersimpan dalam file, Menyimpan plot, dan konversi data menjadi CSV
1. Membuat file dalam format *(.csv)*
2. Install gnuplot dengan perintah *sudo apt install gnuplot*
3. Isi file format *(.csv)* dengan ID, Nama, Score. Seperti berikut
```ID,Name,Score
1,Mark,85
2,Jaemin,90
3,Jeno,78
4,Haechan,100
5,Jisung,66
6,Chenle,53
7,Renjun,48
```
4. Setelah itu berikan perintah seperti berikut, yang dijalankan perbaris
```gnuplot -p -e "
set datafile separator ',';
set title 'Score Line Chart';
set xlabel 'ID';
set ylabel 'Score';
set xtics rotate by -45;
set grid;
plot 'data.csv' using 1:3 with linespoints title 'Scores' lc rgb 'blue'"
```
5. Setelah menjalankan perintah diatas perbaris, akan muncul windows baru berupa plot data yang terdapat dalam file csv sebelumnya berupa garis, dan simpan dalam bentuk file pdf

   ## Konversi Data menjadi JSON
1. Untuk mengkonversi data csv menjadi data dengan format (.json) kita hanya memerlukan perubahan format penulisan sesuai dengan perintah json agar dapat dibaca sebagai berikut, dan jangan lupa berikan perintah berupa **vim data.json**
```[
    {
        "ID": 1,
        "Name": "Mark",
        "Score": 85
    },
    {
        "ID": 2,
        "Name": "Jaemin",
        "Score": 90
    },
    {
        "ID": 3,
        "Name": "Jeno",
        "Score": 78
    },
    {
        "ID": 4,
        "Name": "Haechan",
        "Score": 100
    },
    {
        "ID": 5,
        "Name": "Jisung",
        "Score": 66
    },
    {
        "ID": 6,
        "Name": "Chenle",
        "Score": 53
    },
    {
        "ID": 7,
        "Name": "Renjun",
        "Score": 48
    }
]
```

# TUGAS 3

1. Buat program untuk mencetak kalimat “Komputasi Geofisika” ke layar, dan jelaskan setiap baris programnya, dalam,
- Bahasa C/C++
- Shell script
- Skrip awk
2. Buat agar skrip yang ditulis menjadi program yang dapat dijalankan langsung (executable). Jelaskan tahap-tahapnya.

**JAWAB :**

## Mencetak kalimat "Komputasi Geofisika"

### Bahasa C/C++
1. Membuat file baru dengan memberikan perintah **vim metnum.cc**. Kemudian ketik perintah seperti berikut :
   ```#include <stdio.h>
        int main() {
        printf("Komputasi Geofisika\n");
        return 0;
        }
    ```
Keterangan :
- *#include <stdio.h>* merupakan preprocessor directive yang digunakan untuk menyertakan file header.
- *stdio.h* yang merupakan standar input output dalam bahasa C.
- *int main()* merupakan fungsi utama dalam bahasa C dan int memberikan fungsi untuk mengembalikan nilai integer.
- *printf("Komputasi Geofisika\n");* merupakan fungsi dari stdio.h yang digunakan untuk mencetak kalimat ke layar. \n merupakan karakter newline untuk membuat garis baru setelah teks dicetak.
- *return 0* berfungsi untuk mengembalikan nilai 0 ke sistem operasi yang menandakan bahwa program telah berjalan dengan sukses.

2. Kemudian jalankan perintah berikut *g++ metnum.cc -o hasil* dan *./hasil* untuk mendapatkan output dari bahasa C yang ditulis dalam file metnum.cc

### Shell Script
1. Membuat file baru dengan format **vim metnum.sh**. Kemudian ketik perintah seperti berikut :
```
   #!/bin/bash
   echo "Komputasi Geofisika"
```
Keterangan :
- *#!/bin/bash* merupakan perintah untuk menentukan Bash sebagai interpreter scripnt
- *echo "Komputasi Geofisika"* merupakan perintah untuk mencetak teks ke terminal

2. Setelah itu berikan perintah seperti berikut untuk menjalankan program secara langsung serta memberikan izin eksekusi ke script ```chmod +x metnum.sh``` dan menjalankan scipt serta memberikan output dengan perintah ```./metnum.sh```

### Skip AWK
1. Membuat file baru dengan format **vim metnum.awk**. Kemudian ketik perintah seperti berikut yang akan mencetak teks ke terminal
```
BEGIN {
    print "Komputasi Geofisika"
}
```
2. Untuk menjalankan program secara langsung diberikan perintah ```awk -f metnum.awk```. Tetapi untuk menjalankan program secara langsung tanpa memberikan perintah seperti diatas harus merubah format penulisan pada file metnum.awk menjadi seperti berikut agar dapat dijalankan langsung
```
#!/usr/bin/awk -f
BEGIN {
    print "Komputasi Geofisika"
}
```
3. Berikan perintah berikut ```chmod +x metnum.awk``` untuk memberikan izin eksekusi secara langsung dari file metnum.awk kemudian berikan perintah ```./metnum.awk``` untuk melihat outputnya.


# TUGAS 4

Diberikan tugas untuk membuat akun dan repositori baru pada github.com serta buat salinan berkas-berkas pada program yang telah dibuat pada repositori baru di github.com. Jelaskan tahap-tahapnya!

**JAWAB :**
## Membuat Akun serta Repositori Baru di GitHub.com
1. Buka *GitHub.com* di browser
2. Klik "Sign up" dan isi username, email, dan password
3. Verifikasi email yang dikirim ke alamat email yang telah didaftarkan
4. Masuk ke akun GitHub setelah berhasil mendaftar
5. Untuk membuat repositori baru klik ikon "+" dipojok kanan atas
6. Pilih "New Repository"
7. Isi informasi repositori seperti nama, deskripsi, visibility, dan centang "Add a README file"
8. Klik tombol "Create repository" untuk membuat repositori

## Menyalin Berkas Program ke Repositori Baru dari Ubuntu
1. Pastikan git sudah terinstall dengan perintah ```git --version```. Jika belum download terlebih dahulu dengan perintah ```sudo apt install git```
2. Jalankan perintah berikut untuk mengatur identitas git
   ```
   git config --global user.name "NamaAnda"
   git config --global user.email "email@example.com"
   ```
3. Clone repositori GitHub ke komputer dengan perintah ```git clone https://github.com/<username>/<repositori>.git```
4. Pindah direktori repositori dengan perintah ```cd <repositori>```
5. Salin semua berkas kedalam folder repositori lokas yang sudah dibuat di cd
6. Berikan perintah ```git add .``` untuk menambahkan semua berkas yang telah disalin kedalam sistem Git.
7. Buat Commit untuk menyimpan perubahan dengan perintah ```git commit -m "Menambahkan berkas program"```
8. Sebelum melakukan push git harus membuat token baru sebagai password push git karena password akun GitHub tidak mendukung untuk melakukan push jadi harus membuat token baru pada bagian Settings --> Developer Settings --> Personal Acces Tokens --> Tokens (classics), jangan lupa salin token.
9. Berikan perintah seperti berikut sebelum melakukan git push ```git remote set-url origin https://<personal access token>@github.com/<nama akun>/<repositori>```
10. Berikan perintah ```git push origin main``` dan file pun sudah terupdate pada repositori baru yang dibuat pada GitHub.
