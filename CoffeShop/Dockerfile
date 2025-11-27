# Dockerfile
FROM python:3.12-slim

# Prevent Python from writing .pyc files and buffer logs
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Set work directory
WORKDIR /app

# Install dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Copy project
COPY . /app

# Create directories for static & media (match your settings)
RUN mkdir -p staticfiles media

# Expose port for Django
EXPOSE 8000

# Default command (overwritten in docker-compose to add migrate/collectstatic)
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
