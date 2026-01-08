## Install service docker
Pastikan Anda menggunakan akun dengan hak akses sudo atau root.

### Update System
Mulai dengan memperbarui paket sistem Anda:
```
apt update && sudo apt upgrade -y
```

### Install Support Packages
Docker membutuhkan beberapa paket pendukung. Instal paket-paket ini:
```
apt install apt-transport-https ca-certificates curl software-properties-common -y

```

### Add Docker GPG Key
Unduh kunci GPG resmi Docker dan tambahkan ke sistem:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

```

### Add Docker Repository
Tambahkan repository Docker ke daftar sumber paket:
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

```

### Instal Docker
Perbarui daftar paket dan instal Docker:
```
apt update
apt install docker-ce docker-ce-cli containerd.io
```
Or

```
apt update
apt install docker-ce -y
```

`apt install docker-ce docker-ce-cli containerd.io`:

Menginstal tiga paket:
-   `docker-ce`: Docker Community Edition, yang merupakan paket utama untuk menjalankan Docker.
-   `docker-ce-cli`: Command Line Interface untuk Docker, yang memungkinkan Anda menjalankan perintah Docker dari terminal.
-   `containerd.io`: Daemon yang bertanggung jawab untuk mengelola kontainer. Ini adalah bagian penting dari ekosistem Docker.

`apt install docker-ce -y`:

-   Menginstal hanya paket `docker-ce`.
-   Opsi `-y` otomatis menjawab "yes" untuk semua pertanyaan selama proses instalasi, sehingga Anda tidak perlu mengkonfirmasi setiap kali.

### Check Docker Installation
Verifikasi apakah Docker telah terpasang dengan benar:
```
docker --version
```

### Docker Configuration
Agar Docker selalu berjalan saat sistem dihidupkan:
```
systemctl enable docker
systemctl start docker

```
Jika semua step by step sudah di lakukan dan hasil seperti gambar di bawah, maka service docker sudah berhasil terinstall

![image](https://github.com/user-attachments/assets/6671ee09-c83b-4246-a1e6-6f9f8fc41355)
