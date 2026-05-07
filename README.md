# Local MinIO (S3) with Docker Compose

Copy `.env.example` to `.env` and set secure credentials:

```bash
cp .env.example .env
# edit .env to set MINIO_ROOT_USER and MINIO_ROOT_PASSWORD
```

Start MinIO:

```bash
cd container/docker-minio
docker compose up -d
```

Console: http://localhost:9001
S3 endpoint: http://localhost:9000

Verify with AWS CLI (example):

```bash
# configure a profile named 'minio' using values from .env
aws configure set aws_access_key_id $(grep MINIO_ROOT_USER .env | cut -d'=' -f2) --profile minio
aws configure set aws_secret_access_key $(grep MINIO_ROOT_PASSWORD .env | cut -d'=' -f2) --profile minio
aws --endpoint-url http://localhost:9000 --profile minio s3 ls
```

Optional: use the MinIO Client (`mc`) to create buckets and manage objects.
