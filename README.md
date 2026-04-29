# FutureMinds Docker Demo Repo

Sample containerized application for security vulnerability demonstration.

## Services
- `backend/` — Python FastAPI backend
- `frontend/` — React + Nginx frontend  
- `worker/` — Celery background worker

## Security Vulnerabilities (for demo)
This repo intentionally contains security issues for ContainerVul AI demonstration:
- Hardcoded secrets in ENV instructions
- Outdated base images with known CVEs
- EOL runtime versions

The ContainerVul AI Pipeline Fix agent will automatically detect, plan, and fix these.
