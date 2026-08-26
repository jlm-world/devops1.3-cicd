# Project 3 — CI/CD + Live Deployment

This project implements a fully automated CI/CD pipeline to deploy the Inventory API (Project 2) to AWS EC2 using GitHub Actions.

---

## Original Project Goal

> Deploy Project 2 to AWS EC2 automatically using GitHub Actions.

---

## What Was Built

- GitHub Actions workflow (`.github/workflows/deploy.yml`)
- Automatic build and push to Docker Hub
- SSH-based deployment to AWS EC2
- Live API accessible via public IP

---

## Pipeline Steps

The pipeline triggers on every push to the `main` branch and runs:

1. **Checkout** — pulls the latest code
2. **Test** — verifies the Flask app loads correctly
3. **Build** — builds the Docker image
4. **Push** — pushes the image to Docker Hub (`mfraj1/inventory-api:latest`)
5. **Deploy** — SSHs into EC2 and runs `docker-compose pull && up -d`

---

## Secrets Used

| Secret | Purpose |
|--------|---------|
| `DOCKER_USERNAME` | Docker Hub username (`mfraj1`) |
| `DOCKER_PASSWORD` | Docker Hub access token |
| `EC2_HOST` | EC2 public IP (`3.111.37.122`) |
| `EC2_SSH_KEY` | Private SSH key for EC2 access |

---

## Live API

The deployed application is live at:

[https://3.111.37.122:5000/products](https://3.111.37.122:5000/products)

---

## Technologies Used

- GitHub Actions
- Docker
- Docker Hub
- AWS EC2
- SSH
- Docker Compose

---

## Status

✅ Complete — pipeline runs automatically on push to `main` and deploys to EC2.
