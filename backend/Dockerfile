# syntax=docker/dockerfile:1

FROM python:3.11-slim

# Prevent .pyc and enable unbuffered logs
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Workdir inside container
WORKDIR /app

# System deps (if you need others like libpq, add here)
RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install Python deps
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy project
COPY . .

# Set envs (Render will override PORT automatically)
ENV PORT=8000

# ⚠️ Replace `backend` with your Django project package (folder with settings.py)
CMD ["sh", "-c", "gunicorn backend.wsgi:application --bind 0.0.0.0:${PORT:-8000}"]
