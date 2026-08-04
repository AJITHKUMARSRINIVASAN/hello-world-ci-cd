# Hello World CI/CD with Docker and GitHub Actions

This project builds a small Python Docker image and pushes it to Docker Hub with GitHub Actions.

## Local test with Rancher Desktop

Make sure Rancher Desktop is running, then run:

```powershell
docker build -t hello-world-local:test .
docker run --rm hello-world-local:test
```

Expected output:

```text
Hello, World! This is a simple Python application. Developed by AK
```

## GitHub Actions setup

The workflow file is:

```text
.github/workflows/docker-image.yml
```

Add these repository secrets in GitHub:

```text
DOCKER_USERNAME
DOCKER_PASSWORD
```

Use your Docker Hub username for `DOCKER_USERNAME`.
For `DOCKER_PASSWORD`, use a Docker Hub access token instead of your normal account password.

After pushing to the `main` branch, GitHub Actions will:

1. Log in to Docker Hub.
2. Build the Docker image.
3. Run the image as a test.
4. Push `DOCKER_USERNAME/hello-world:latest` to Docker Hub.
