# Docker Homework Solution: Multi-Container Web Application

This comprehensive guide outlines the step-by-step solution for the Docker homework assignment. The task involves creating a Dockerfile for a web application and using Docker Compose to manage a multi-container setup with Nginx and Redis.

## Task 1: Crafting a Dockerfile for Nginx Web Server

### Step 1: Designing the Dockerfile

We'll create a `Dockerfile` that builds upon the official Nginx image and incorporates our custom `index.html` file. Here's a detailed breakdown of the Dockerfile:

```dockerfile
# Use the official nginx image as the base
FROM nginx:latest

# Copy the custom index.html file to the appropriate directory in the container
COPY index.html /usr/share/nginx/html/

# Expose port 80 for incoming HTTP traffic
EXPOSE 80

# Optional: Add a health check to ensure the container is running properly
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
```

### Step 2: Creating a Custom index.html

Let's create an `index.html` file with more engaging content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Docker Homework - Nginx Container</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        h1 {
            color: #0066cc;
        }
    </style>
</head>
<body>
    <h1>Welcome to Our Docker-Powered Web Server!</h1>
    <p>This page is served by Nginx running in a Docker container. It's part of a multi-container application showcasing Docker's capabilities.</p>
    <ul>
        <li>Container: Nginx</li>
        <li>Base Image: nginx:latest</li>
        <li>Exposed Port: 80</li>
    </ul>
    <p>Explore the power of containerization and microservices architecture!</p>
</body>
</html>
```

### Step 3: Building and Running the Docker Image

To build and launch the Docker image:

1. Save both the `Dockerfile` and `index.html` in the same directory.
2. Open a terminal and navigate to this directory.
3. Build the Docker image with a tag:
   ```
   docker build -t my-nginx-app:v1 .
   ```
4. Run the container, mapping port 8080 on the host to port 80 in the container:
   ```
   docker run -d -p 8080:80 --name nginx-homework my-nginx-app:v1
   ```

After executing these commands, you can access the web page by opening a browser and navigating to `http://localhost:8080`.

![Nginx Container Web Page](https://github.com/user-attachments/assets/23224677-d9d3-41e4-9467-9604bcd6a524)

## Task 2: Orchestrating a Multi-Container Application with Docker Compose

### Step 1: Crafting the docker-compose.yml File

Create a `docker-compose.yml` file to define and manage both the Nginx and Redis containers:

```yaml
version: '3.8'

services:
  web:
    build: 
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:80"
    depends_on:
      - redis
    networks:
      - app-network
    restart: unless-stopped

  redis:
    image: "redis:alpine"
    ports:
      - "6379:6379"
    volumes:
      - redis-data:/data
    networks:
      - app-network
    restart: unless-stopped

networks:
  app-network:
    driver: bridge

volumes:
  redis-data:
```

This configuration:
- Defines two services: `web` (our Nginx container) and `redis`
- Sets up a custom network for inter-container communication
- Configures persistent storage for Redis data
- Implements automatic container restart policies

### Step 2: Launching the Multi-Container Application

To run the multi-container application:

1. Ensure the `docker-compose.yml` file is in the same directory as your `Dockerfile` and `index.html`.
2. Open a terminal and navigate to this directory.
3. Execute the following command:
   ```
   docker-compose up -d
   ```

This command builds the Nginx image (if not already built) and starts both the web and Redis containers in detached mode.

### Step 3: Verifying the Running Containers

To confirm that both containers are operational:

1. Open a terminal.
2. Run the following command:
   ```
   docker-compose ps
   ```

This will display a list of running containers, which should include both your Nginx web server and the Redis container.

![Docker Compose Running Containers](https://github.com/user-attachments/assets/657d9f38-d980-4d0a-be5a-8836692e3d10)

### Step 4: Testing the Setup

1. Access the Nginx web server:
   - Open a browser and navigate to `http://localhost:8080`
   - You should see the custom web page we created earlier

2. Verify Redis connectivity:
   - Use the following command to connect to the Redis CLI:
     ```
     docker-compose exec redis redis-cli
     ```
   - Once connected, try a simple Redis command:
     ```
     SET mykey "Hello from Redis!"
     GET mykey
     ```

This comprehensive setup demonstrates a basic multi-container application using Docker and Docker Compose, showcasing the power of containerization for web development and microservices architecture.
