# SSH Server Debian pada VMware

Dokumentasi instalasi dan konfigurasi SSH Server pada sistem operasi Debian menggunakan VMware serta menghubungkannya melalui Windows PowerShell.

## 1. Persiapan

Pastikan sudah tersedia:
- VMware Workstation.
- Debian Linux.
- Windows 10/11.
- Koneksi jaringan antara Windows dan Debian.

## 2. Update Sistem Debian

Buka Terminal Debian dan masuk sebagai root.

```bash
su -
```

Update daftar paket:

```bash
apt update
```

Upgrade sistem:

```bash
apt upgrade -y
```

## 3. Instalasi SSH Server

Jalankan perintah berikut untuk menginstal OpenSSH Server:

```bash
apt install openssh-server -y
```

## 4. Mengaktifkan SSH Server

Aktifkan SSH agar berjalan otomatis saat Debian dinyalakan:

```bash
systemctl enable ssh
```

Jalankan layanan SSH:

```bash
systemctl start ssh
```

Periksa status SSH:

```bash
systemctl status ssh
```

Jika muncul `active (running)`, berarti SSH Server berhasil dijalankan.

## 5. Mengetahui IP Address Debian

Gunakan perintah:

```bash
ip addr
```

Cari alamat IP pada interface jaringan Debian.

Contoh:

```text
192.168.1.10
```

Catatan: Alamat IP dapat berbeda sesuai konfigurasi jaringan VMware.

## 6. Menghubungkan Windows ke Debian

Buka Windows PowerShell.

Masukkan perintah:

```powershell
ssh username@192.168.1.10
```

Ganti `username` dengan nama pengguna Debian dan alamat IP sesuai hasil pemeriksaan.

Contoh:

```powershell
ssh hervayona@192.168.1.10
```

Jika muncul konfirmasi koneksi pertama kali, ketik:

```text
yes
```

Masukkan password akun Debian.

## 7. Pengujian Koneksi SSH

Jika koneksi berhasil, terminal PowerShell akan menampilkan shell Debian.

Untuk memastikan koneksi berhasil, jalankan:

```bash
hostname
```

Perintah tersebut menampilkan nama komputer Debian yang sedang diakses.

## 8. Perintah SSH yang Berguna

| Perintah | Fungsi |
|---|---|
| `systemctl start ssh` | Menjalankan SSH |
| `systemctl stop ssh` | Menghentikan SSH |
| `systemctl restart ssh` | Memulai ulang SSH |
| `systemctl status ssh` | Memeriksa status SSH |
| `ip addr` | Melihat IP Address |
| `hostname` | Melihat nama komputer |
| `exit` | Keluar dari koneksi SSH |

## Kesimpulan

SSH Server pada Debian memungkinkan pengguna mengakses dan mengelola sistem Linux dari komputer lain melalui jaringan secara jarak jauh. Dengan OpenSSH Server, pengelolaan Debian dapat dilakukan melalui Windows PowerShell tanpa harus selalu membuka terminal langsung di VMware.

---

**Author:** Hervayona  
**Project:** SSH Server Debian  
**Platform:** Debian Linux, VMware, Windows PowerShell
