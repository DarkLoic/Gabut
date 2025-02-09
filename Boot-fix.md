 Kalau boot ke Kali Linux masih lama meskipun sudah pakai nomodeset, kemungkinan masalahnya ada di salah satu dari ini:

1. Driver GPU (Terutama NVIDIA atau AMD)

Coba boot pakai recovery mode atau nomodeset dulu.

Install driver GPU yang sesuai.

sudo apt update && sudo apt upgrade -y
sudo apt install firmware-linux-nonfree

Kalau pakai NVIDIA, coba:

sudo apt install nvidia-driver

Kalau pakai AMD, coba:

sudo apt install firmware-amd-graphics



2. Cek Log Booting

Pas boot, tekan ESC atau F2 buat lihat prosesnya.

Atau setelah masuk, cek dengan:

journalctl -b -1 --no-pager | less



3. Hapus quiet splash di Grub

Edit grub:

sudo nano /etc/default/grub

Ubah ini:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Jadi:

GRUB_CMDLINE_LINUX_DEFAULT=""

Simpan (CTRL+X, Y, Enter), lalu update grub:

sudo update-grub



4. Matikan Services yang Lambat

Cek service mana yang lama start-nya:

systemd-analyze blame

Kalau ada yang mencurigakan, bisa coba disable atau mask service itu.



5. Coba Kernel Lama

Di menu boot GRUB, pilih Advanced options for Kali Linux.

Pilih kernel yang lebih lama kalau ada.



6. Gunakan systemd-bootchart (Opsional)

Bisa cek delay saat boot dengan:

sudo apt install systemd-bootchart
sudo reboot

Hasilnya bisa dilihat di /var/log/bootchart.svg.




Kalau setelah coba semua masih lemot, coba kasih detail lebih lanjut soal hardware (CPU, GPU, HDD/SSD) dan kira-kira proses mana yang bikin lama.

