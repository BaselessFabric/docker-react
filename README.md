# Docker-React

This project is a simple React application created for testing and experimenting with Docker. The main goal is to understand how Docker works, dockerize a React app, and implement CI/CD processes using a Docker image repository.

## Table of Contents
- [About the Project](#about-the-project)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running Locally](#running-locally)
- [Dockerization](#dockerization)
  - [Building Docker Image](#building-docker-image)
  - [Running Docker Container](#running-docker-container)
- [CI/CD Pipeline](#ci-cd-pipeline)
  - [Setup](#setup)
  - [Workflow](#workflow)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About the Project

This project is a simple React application designed for learning and experimenting with Docker. It focuses on:
- Dockerizing a React application
- Using Docker image repositories
- Implementing CI/CD processes with Docker

## Getting Started

### Prerequisites

To run this project locally, you need to have the following installed:

- [Node.js](https://nodejs.org/en/download/)
- [Docker](https://www.docker.com/get-started)
- [Git](https://git-scm.com/)

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/BaselessFabric/docker-react.git
   cd docker-react
   ```

2. Install NPM packages:
   ```sh
   npm install
   ```

### Running Locally

To run the application locally, use the following command:
```sh
npm start
```
This will start the development server and open the application in your default web browser.

## Dockerization

### Building Docker Image

To build a Docker image of the React application, use the following command:
```sh
docker build -t docker-react .
```

### Running Docker Container

To run the Docker container, use the following command:
```sh
docker run -p 3000:3000 docker-react
```
This will start the application in a Docker container and make it accessible at `http://localhost:3000`.

## CI/CD Pipeline

### Setup

For the CI/CD pipeline, you can use a service like GitHub Actions, GitLab CI, or Jenkins. This project includes a basic GitHub Actions workflow file.

### Workflow

1. The workflow will trigger on push and pull request events.
2. It will build the Docker image.
3. It will run tests (if any).
4. It will push the Docker image to a Docker image repository (Docker Hub, AWS ECR, etc.).

Example GitHub Actions workflow file (`.github/workflows/docker.yml`):

```yaml
name: Docker CI/CD

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v1

    - name: Log in to Docker Hub
      uses: docker/login-action@v1
      with:
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

    - name: Build and push Docker image
      uses: docker/build-push-action@v2
      with:
        context: .
        push: true
        tags: your-username/docker-react:latest
```

## Contributing

Contributions are welcome! Please fork this repository and create a pull request with your changes. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact

Alex Walls

Project Link: [https://github.com/BaselessFabric/docker-react.git](ttps://github.com/BaselessFabric/docker-react.git)
