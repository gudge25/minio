# MinIO

MinIO — високодоступне розподілене об’єктне сховище з підтримкою **erasure coding** на 4 дисках.

## ⚙️ Конфігурація

MinIO працює в режимі erasure-coded pool з такими характеристиками:
- 4 незалежних томи (наприклад: `/data1`, `/data2`, `/data3`, `/data4`)
- EC:2 (2 data + 2 parity)
- Надійне збереження даних навіть при втраті до 2 дисків

---

# MC (MinIO Client)

Початкове налаштування клієнта `mc`:

```bash
docker exec -it minio mc alias set local http://localhost:9000 admin CHANGE_ME
docker exec -it minio mc admin info local
```
# Samba as Storage

This guide explains how to mount multiple Samba shares for use as a storage backend (e.g., for MinIO).

---

## 🛠 Prerequisites

Install the required package:

```bash
sudo apt install cifs-utils -y
```

## ⚙️ Mount Configuration
Edit the /etc/fstab file and add the following lines to mount Samba shares at boot:
```
//192.168.2.2/share1 /mnt/minio-union/share1 cifs username=Username,password=Password,vers=3.0,iocharset=utf8,file_mode=0777,dir_mode=0777,nofail,_netdev,cache=none,actimeo=0,soft,rw,noserverino 0 0
//192.168.2.3/share2 /mnt/minio-union/share2 cifs username=Username,password=Password,vers=3.0,iocharset=utf8,file_mode=0777,dir_mode=0777,nofail,_netdev,cache=none,actimeo=0,soft,rw,noserverino 0 0
//192.168.2.4/share3 /mnt/minio-union/share3 cifs username=Username,password=Password,vers=3.0,iocharset=utf8,file_mode=0777,dir_mode=0777,nofail,_netdev,cache=none,actimeo=0,soft,rw,noserverino 0 0
//192.168.2.5/share4 /mnt/minio-union/share4 cifs username=Username,password=Password,vers=3.0,iocharset=utf8,file_mode=0777,dir_mode=0777,nofail,_netdev,cache=none,actimeo=0,soft,rw,noserverino 0 0
```
### Note: Replace Username and Password with your actual Samba credentials.
