
# Cloud Run Mapping

## Configuration Variables

- `DATABASE_URL`: Supplied at runtime for the application to connect to its database. Treat it as non-secret only when it contains no credentials or sensitive connection details.
- `LOG_LEVEL`: Controls the application's logging level, such as `info`. Set using `--set-env-vars`.

Example:

```bash
gcloud run deploy SERVICE_NAME \
  --image IMAGE_URL \
  --region REGION \
  --set-env-vars LOG_LEVEL=info
```

## Secrets

- `API_KEY`: Store the API key in Google Cloud Secret Manager and reference it from Cloud Run. Never hardcode it in the Dockerfile or commit it to Git.
- Database credentials, if present in `DATABASE_URL`, should also be protected as secrets.

Example:

```bash
gcloud run deploy SERVICE_NAME \
  --image IMAGE_URL \
  --region REGION \
  --set-secrets API_KEY=api-key:latest
```

`SERVICE_NAME`, `IMAGE_URL`, and `REGION` are placeholders to be replaced with the actual deployment details. These commands document the configuration only; no Cloud Run deployment is required for this assignment.
