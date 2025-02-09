Kalau Kali Linux di laptop Sony Vaio nggak bisa deteksi flash disk, coba langkah-langkah berikut:


---

1. Cek Apakah Flash Disk Terdeteksi oleh Sistem

Colok flash disk, lalu cek di terminal:

lsblk

atau

sudo fdisk -l

Kalau flash disk muncul (misalnya /dev/sdb), berarti cuma masalah mounting. Kalau nggak muncul, lanjut ke langkah berikutnya.


---

2. Cek Log Saat Colok Flash Disk

Jalankan perintah ini sebelum dan sesudah colok flash disk:

dmesg -w

Kalau ada error seperti "usb device not recognized" atau "unable to enumerate USB device", mungkin ada masalah di driver USB atau port-nya.


---

3. Restart Service USB & Udev

Coba restart layanan yang menangani USB:

sudo systemctl restart udev
sudo modprobe -r usb_storage && sudo modprobe usb_storage

Lalu colok ulang flash disk dan cek lagi dengan lsblk.


---

4. Coba Mount Manual

Kalau flash disk terdeteksi tapi nggak muncul di file manager, coba mount manual:

1. Buat folder untuk mount:

sudo mkdir /mnt/flashdisk


2. Cek nama perangkat flash disk:

lsblk

Misalnya /dev/sdb1, lalu mount:

sudo mount /dev/sdb1 /mnt/flashdisk


3. Cek isi flash disk:

ls /mnt/flashdisk


4. Kalau sudah selesai, unmount dengan:

sudo umount /mnt/flashdisk




---

5. Cek Format Flash Disk (NTFS, FAT32, exFAT, ext4, dll.)

Kalau flash disk pakai NTFS atau exFAT, Kali Linux mungkin butuh paket tambahan:

Install driver NTFS & exFAT:

sudo apt install ntfs-3g exfat-fuse exfat-utils

Setelah install, coba colok ulang flash disk dan cek dengan lsblk.



---

6. Cek Port USB Lain atau Coba di OS Lain

Coba colok di port USB lain (terutama kalau ada USB 2.0 & 3.0).

Coba di Windows atau OS lain buat pastiin flash disk nggak rusak.

Kalau hanya Kali Linux yang bermasalah, coba pakai Live USB Kali buat cek apakah masalahnya ada di sistem atau hardware.



---

Kalau setelah semua langkah ini masih nggak bisa, coba kasih info tambahan:

Hasil lsblk setelah colok flash disk

Tipe flash disk (merk, kapasitas)

Pesan error (jika ada) dari dmesg -w


Biar bisa cari solusi yang lebih spesifik.

