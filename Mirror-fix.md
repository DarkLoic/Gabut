 Untuk menyambungkan layar Kali Linux (dual boot) di laptop Sony Vaio ke proyektor, ikuti langkah-langkah berikut:


---

1. Hubungkan Laptop ke Proyektor

Gunakan kabel HDMI atau VGA (tergantung port yang tersedia di laptop dan proyektor).

Jika laptop hanya memiliki HDMI, tetapi proyektor hanya mendukung VGA, gunakan konverter HDMI ke VGA.

Pastikan proyektor sudah dinyalakan dan diatur ke input yang sesuai (misalnya, HDMI 1 atau VGA 1).



---

2. Cek Koneksi di Kali Linux

Setelah kabel terhubung, pastikan Kali Linux mendeteksi proyektor dengan perintah:

xrandr

Perintah ini akan menampilkan daftar layar yang terdeteksi. Biasanya, output seperti berikut akan muncul:

eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)

Jika HDMI-1 atau VGA-1 muncul sebagai "connected", berarti Kali Linux sudah mendeteksi proyektor.


---

3. Konfigurasi Tampilan

a. Gunakan GUI (Graphical Interface)

1. Buka Settings → Displays


2. Pilih layar proyektor yang terdeteksi


3. Pilih opsi Mirror (untuk menampilkan layar yang sama) atau Extend (untuk memperluas layar)


4. Klik Apply



b. Gunakan Terminal

Jika tampilan tidak muncul secara otomatis, jalankan perintah berikut:

Untuk Mirror Display (Menampilkan Layar yang Sama)

xrandr --output HDMI-1 --same-as eDP-1

Untuk Extended Display (Layar Terpisah)

xrandr --output HDMI-1 --right-of eDP-1 --auto

Gantilah HDMI-1 dengan VGA-1 jika menggunakan kabel VGA.


---

4. Potensi Masalah dan Solusi


---

Kalau ada error atau layar tetap tidak muncul, coba restart laptop dan coba lagi.

