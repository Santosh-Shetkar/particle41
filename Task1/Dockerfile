# Use slim Python image
FROM python:3.11-slim

# Create non-root user
RUN useradd -m appuser

# Set working directory
WORKDIR /app

# Copy and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy app source
COPY app/ ./app

# Change ownership and switch to non-root user
RUN chown -R appuser:appuser /app
USER appuser

# Set the default command
CMD ["python", "app/main.py"]
