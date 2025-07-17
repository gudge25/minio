# minio
Minio - розподілене сховище (erasure-coded pool) на 4 дисках






# MC
docker exec -it minio mc alias set local http://localhost:9000 admin CHANGE_ME
docker exec -it minio mc admin info local
