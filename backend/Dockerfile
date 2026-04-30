# Python API backend
FROM python:3.11-slim

WORKDIR /app

# Dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# SECURITY: All secrets have been removed from the Dockerfile.
# Secrets must be injected at runtime via one of the following methods:
#
#   1. Docker secrets (Swarm):   docker secret create ...
#   2. Kubernetes secrets:       envFrom.secretRef in pod spec
#   3. AWS Secrets Manager:      retrieved at runtime via boto3 / envconsul
#   4. HashiCorp Vault:          agent sidecar or envconsul
#   5. Docker run (dev only):    --env-file .env  (never commit .env to VCS)
#
# Required environment variables at runtime:
#   DATABASE_URL        - PostgreSQL connection string
#   API_KEY             - External API authentication key
#   AWS_ACCESS_KEY_ID   - AWS IAM access key (prefer IAM roles/IRSA instead)
#   AWS_SECRET_ACCESS_KEY - AWS IAM secret key (prefer IAM roles/IRSA instead)
#   REDIS_PASSWORD      - Redis authentication password

COPY . .

EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
