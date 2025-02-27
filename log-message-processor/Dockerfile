# Use an official Python runtime as a parent image
FROM python:3.5-slim

# Set the working directory in the container
WORKDIR /app

# Install system dependencies (gcc and other build tools)
RUN apt-get update && \
    apt-get install -y --no-install-recommends gcc python3-dev && \
    rm -rf /var/lib/apt/lists/*

# Copy the requirements file
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Set environment variables
ENV REDIS_HOST=redis-queue \
    REDIS_PORT=6379 \
    REDIS_CHANNEL=log_channel

# Run the application
CMD ["python", "main.py"]