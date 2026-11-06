# Manajemen Asrama BE

Backend Spring Boot untuk manajemen asrama, user, izin, jadwal kegiatan, asrama, kategori, dan kegiatan.

## Prasyarat

- Java 17
- Maven Wrapper (`mvnw.cmd`)
- PostgreSQL
- PowerShell di Windows

## Konfigurasi database

Konfigurasi default ada di `src/main/resources/application.properties`.

Jika ingin memakai profile lokal dari `src/main/resources/application-local.properties`, jalankan aplikasi dengan profile `local`.

Contoh environment variable yang bisa dipakai:

```powershell
$env:SPRING_PROFILES_ACTIVE = 'local'
$env:SPRING_DATASOURCE_URL = 'jdbc:postgresql://localhost:5432/manajemenasrama'
$env:SPRING_DATASOURCE_USERNAME = 'postgres'
$env:SPRING_DATASOURCE_PASSWORD = 'postgres'
```

## Menjalankan aplikasi

```powershell
$env:JAVA_HOME = 'C:\Program Files\Java\jdk-17'
$env:Path = "$env:JAVA_HOME\bin;$env:Path"
$env:SPRING_PROFILES_ACTIVE = 'local'
.\mvnw.cmd spring-boot:run
```

Jika tidak ingin memakai profile `local`, hapus baris `SPRING_PROFILES_ACTIVE` dan pastikan environment variable database sudah sesuai.

## Menjalankan test

```powershell
$env:JAVA_HOME = 'C:\Program Files\Java\jdk-17'
$env:Path = "$env:JAVA_HOME\bin;$env:Path"
.\mvnw.cmd test
```

## Postman

File Postman ada di:

- `docs/postman/manajemen-asrama.postman_collection.json`
- `docs/postman/manajemen-asrama.postman_environment.json`

### Cara pakai

1. Import collection dan environment ke Postman.
2. Pilih environment `Manajemen Asrama Local`.
3. Jalankan request `Auth / Login` terlebih dahulu.
4. Token `access_token` akan disimpan otomatis oleh script test pada request login.
5. Request lain yang butuh autentikasi akan memakai Bearer token dari environment.

## Dokumentasi tambahan

- `docs/whitebox.md`
- `docs/blackbox.md`

## Endpoint penting

- `POST /api/auth/login`
- `POST /api/auth/register`
- `GET /api/users/me`
- `GET /api/asrama`
- `GET /api/ijin`
- `GET /api/jadwal-kegiatan`
- `GET /api/kategori`
- `GET /api/kegiatan`

## Catatan

- Endpoint login memakai username/password di body.
- Endpoint protected membutuhkan `Authorization: Bearer <token>`.
- Endpoint `POST /api/generate-password/{password}` tersedia untuk kebutuhan utilitas development.

