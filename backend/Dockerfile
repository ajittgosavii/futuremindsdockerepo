# Python API backend
FROM python:3.11-slim

WORKDIR /app

# Dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# SECURITY: All secrets have been removed from the Dockerfile.
# Secrets must be injected at runtime via one of the following methods:
#
#   1. Docker Secrets (Swarm):      docker secret create ...
#   2. Kubernetes Secrets:          envFrom.secretRef in pod spec
#   3. AWS Secrets Manager:         use a secrets init sidecar or SDK at startup
#   4. HashiCorp Vault:             use Vault Agent or SDK at startup
#   5. CI/CD environment injection: set env vars in your pipeline secrets store
#
# Required environment variables (must be provided at runtime):
#   DATABASE_URL          - PostgreSQL connection string
#   API_KEY               - External API key
#   AWS_ACCESS_KEY_ID     - AWS access key ID
#   AWS_SECRET_ACCESS_KEY - AWS secret access key
#   REDIS_PASSWORD        - Redis authentication password
#
# Example docker run:
#   docker run \
#     --env-file .env.secrets \
#     -e DATABASE_URL="$(aws secretsmanager get-secret-value --secret-id containervul/containervul-backend/database-url --query SecretString --output text)" \
#     containervul-backend:latest

COPY . .

EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
