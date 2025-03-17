# Use an official lightweight Python image
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy necessary files
COPY app.py  /app/

# Install dependencies
RUN pip install --no-cache-dir flask requests

# Set a non-root user
RUN useradd -m myuser
USER myuser

# Expose the application port
EXPOSE 5000

# Start the Flask app
CMD ["python3", "app.py"]
