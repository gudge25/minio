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
