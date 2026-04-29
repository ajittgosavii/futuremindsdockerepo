# Python API backend
FROM python:3.9-slim

WORKDIR /app

# Dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# SECURITY ISSUE: Hardcoded secrets baked into image layer
ENV DATABASE_URL=postgresql://admin:SuperSecret123@db.internal:5432/appdb
ENV API_KEY=sk-prod-a8f3k2m9x1p5q7r4w6y0z
ENV AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
ENV AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
ENV REDIS_PASSWORD=redis-prod-password-2024

COPY . .

EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
