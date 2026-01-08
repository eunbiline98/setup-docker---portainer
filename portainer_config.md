## Portainer Installation
Portainer adalah GUI yang mempermudah manajemen Docker container.

### Create Volume for Portainer
Portainer menyimpan datanya di volume yang persisten. Buat volume baru:
```
docker volume create portainer_data
```

### Run Portainer in Docker with Default Port
Gunakan perintah berikut untuk menjalankan Portainer di Docker dengan port default 9000:
```
docker run -d -p 9000:9000 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

### Run Portainer in Docker with custom Port
Jalankan Portainer pada port 9443 (https) dan 8000:
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
**Penjelasan Perintah**
1. `docker run`: Memulai sebuah container baru.

2. `-d`: Menjalankan container dalam mode detached (background), sehingga terminal tetap bebas.

3. `-p 8000:8000`: Memetakan port 8000 di host ke port 8000 di dalam container.
    -   **Port 8000** pada Portainer digunakan untuk fitur "Edge Agent", yang memungkinkan manajemen jarak jauh dari lingkungan Docker lain yang telah diinstal Edge Agent Portainer.

4. `-p 9443:9443`: Memetakan port 9443 di host ke port 9443 di dalam container.
    -   **Port 9443** adalah port default yang digunakan Portainer untuk akses HTTPS (antarmuka web yang aman).

5. `--name portainer`: Memberikan nama pada container, yaitu "portainer". Nama ini digunakan untuk memudahkan identifikasi dan manajemen container (seperti `docker stop portainer` untuk menghentikannya).

6. `--restart=always:` Mengonfigurasi container agar selalu restart secara otomatis jika terjadi kegagalan atau jika server di-reboot.
    -   Pengaturan ini memastikan Portainer akan selalu tersedia setiap kali server dihidupkan.

7. `-v /var/run/docker.sock:/var/run/docker.sock`: Menghubungkan Docker socket host ke dalam container.

    -   Docker socket ini memungkinkan Portainer untuk mengakses daemon Docker di host, sehingga bisa mengelola container, volume, jaringan, dan lainnya.

8. -`v portainer_data:/data`: Menyimpan data Portainer dalam volume bernama `portainer_data`.
    -   Volume ini bersifat persisten, jadi data konfigurasi Portainer tidak akan hilang jika container dihapus atau dibuat ulang.

9. `portainer/portainer-ce:latest`: Menentukan image Portainer Community Edition yang akan digunakan.
    -   `latest` menunjukkan versi terbaru dari image yang akan diambil dari Docker Hub.

### Portainer Access
1. Buka browser Anda dan akses https://<IP_address>:<Port>. Gantilah <IP_address> dengan alamat IP server Anda dan <Port> yang sudah di konfigurasi

2. Buat akun admin untuk mengakses Portainer, dan setelah itu Anda akan masuk ke dashboard Portainer.
