# Local MinIO — Quick start

1. Copy the example env and set credentials:

```bash
cp .env.example .env
# edit .env and set MINIO_ROOT_USER and MINIO_ROOT_PASSWORD
```

2. Start MinIO:

```bash
cd container/docker-minio
docker compose up -d
```

3. Access:

- Console: http://localhost:9001
- S3 endpoint: http://localhost:9000

4. Quick verify (optional):

```bash
# replace placeholders with values from your .env
aws configure set aws_access_key_id <MINIO_ROOT_USER> --profile minio
aws configure set aws_secret_access_key <MINIO_ROOT_PASSWORD> --profile minio
aws --endpoint-url http://localhost:9000 --profile minio s3 ls
```

That's it — MinIO should now be running locally.
