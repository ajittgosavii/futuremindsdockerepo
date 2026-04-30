# Python API backend
FROM python:3.11-slim

WORKDIR /app

# Dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# SECURITY: All secrets have been removed from the Dockerfile.
# Secrets must be injected at runtime via one of the following methods:
#
# 1. Docker / Compose:  use an env_file or --env-file flag pointing to a
#    file that is NOT committed to version control.
# 2. Kubernetes:        reference a Secret object via envFrom or secretKeyRef.
# 3. AWS ECS / Fargate: use Secrets Manager / Parameter Store secret injection.
# 4. Local dev:         copy .env.example -> .env, populate values, and add
#    .env to .gitignore.
#
# Required environment variables (no defaults – startup will fail if absent):
#   DATABASE_URL          – full PostgreSQL DSN
#   API_KEY               – third-party API key
#   AWS_ACCESS_KEY_ID     – AWS credentials (prefer IAM roles where possible)
#   AWS_SECRET_ACCESS_KEY – AWS credentials (prefer IAM roles where possible)
#   REDIS_PASSWORD        – Redis AUTH password

# Declare the variables so they are visible to the application but carry
# NO default values.  The empty assignment makes the intent explicit while
# ensuring no secret is ever baked into an image layer.
ENV DATABASE_URL="" \
    API_KEY="" \
    AWS_ACCESS_KEY_ID="" \
    AWS_SECRET_ACCESS_KEY="" \
    REDIS_PASSWORD=""

COPY . .

EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
