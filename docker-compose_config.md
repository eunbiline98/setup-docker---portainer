## Instalasi Docker Compose
Docker Compose adalah alat yang memungkinkan Anda menjalankan aplikasi multi-container. Berikut cara menginstalnya.

### Unduh Docker Compose
Unduh versi terbaru Docker Compose (sesuaikan versi jika diperlukan):
```
curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep -Po '"tag_name": "\K.*?(?=")')/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

```
`latest ` akan mengunduh versi terbaru dari Docker Compose secara otomatis.

### Berikan Izin Eksekusi
Ubah izin file agar dapat dieksekusi:
```
chmod +x /usr/local/bin/docker-compose
```

### Cek Instalasi Docker Compose
Verifikasi instalasi Docker Compose:
```
docker-compose --version
```

Jika semua step by step sudah di lakukan dan hasil seperti gambar di bawah, maka service docker-compose sudah berhasil terinstall

![image](https://github.com/user-attachments/assets/855f1dd6-2bc8-40f2-8f83-f35007672d68)
