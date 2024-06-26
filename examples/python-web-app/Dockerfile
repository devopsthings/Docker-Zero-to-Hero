# Use an official Ubuntu as a parent image
FROM ubuntu:20.04

# Set environment variables to avoid interactive installations and reduce size
ENV DEBIAN_FRONTEND=noninteractive

# Set the working directory
WORKDIR /app

# Copy the requirements file
COPY requirements.txt .

# Install dependencies and create a virtual environment
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    python3 -m venv /app/venv && \
    /app/venv/bin/pip install --no-cache-dir -r requirements.txt

# Copy the application code
COPY devops /app/devops

# Set the working directory for the application
WORKDIR /app/devops

# Activate the virtual environment and set the command to run the application
ENTRYPOINT ["/app/venv/bin/python"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
