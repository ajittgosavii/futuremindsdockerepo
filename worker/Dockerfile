# Background worker service
FROM python:3.8

WORKDIR /worker

# SECURITY ISSUE 1: python:3.8 is EOL (end of life Oct 2024)
# SECURITY ISSUE 2: Hardcoded credentials
ENV CELERY_BROKER_URL=redis://:celery-secret-key@redis:6379/0
ENV SENTRY_DSN=https://abc123secretkey@o123456.ingest.sentry.io/789
ENV SLACK_WEBHOOK=https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXX

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["celery", "-A", "worker.tasks", "worker", "--loglevel=info"]
