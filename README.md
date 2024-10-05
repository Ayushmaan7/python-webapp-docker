# Python Web App in Docker

This repository demonstrates how to run a simple Python web application in Docker. The app is based on the Flask framework, which is lightweight and perfect for microservices and simple web applications.

## Prerequisites

Ensure you have the following installed on your machine:

- [Docker](https://docs.docker.com/get-docker/)
- Python 3.7+ (for local testing)

## Getting Started

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/python-webapp-docker.git
cd python-webapp-docker
```

### Step 2: Build the Docker Image

Use the Dockerfile provided to build the Docker image for the Python web app.

```bash
docker build -t python-webapp .
```

### Step 3: Run the Docker Container

Now run the Docker container using the built image.

```bash
docker run -d -p 5000:5000 python-webapp
```

### Step 4: Access the Web App

Open your web browser and go to:

```
http://localhost:5000
```

You should see the running Python web app.

## App Details

- **app.py**: This is the main file containing the simple Flask web app code.
- **requirements.txt**: Specifies the Flask dependency required to run the app.
- **Dockerfile**: Contains the instructions to containerize the application.

## Dockerfile Explanation

```dockerfile
# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Define environment variable
ENV FLASK_APP=app.py

# Run the application
CMD ["flask", "run", "--host=0.0.0.0"]
```

### How It Works

- **Build Phase**: During the build, the Dockerfile sets up a Python environment and installs Flask.
- **Run Phase**: When the container is run, it exposes port 5000 for external access and launches the Flask web server.

## Conclusion

This example shows how Docker simplifies the process of deploying and running applications in isolated environments. You can further customize the app or scale it for production using Docker Compose or Kubernetes.
