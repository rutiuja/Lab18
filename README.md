# Personal Portfolio

A small, responsive personal portfolio website built with plain HTML and CSS. It runs in an Nginx container, so there is no application build step or runtime dependency to install.

## Personalize the page

Open `index.html` and replace the sample name, introduction, location, project descriptions, and email address with your own details. You can also add project links and update the page title.

## Requirements

- Git
- Docker Desktop, or Docker Engine with Docker Compose plugin (Docker Engine alone is enough for the commands below)

Check that Docker is available:

```bash
docker --version
docker info
```

## Create the Docker image

From the project directory, build an image named `personal-portfolio`:

```bash
docker build -t personal-portfolio:latest .
```

Confirm that the image was created:

```bash
docker image ls personal-portfolio
```

## Run the container

Start the website in the background and map port 8080 on your computer to port 80 in the container:

```bash
docker run --name personal-portfolio-site -d -p 8080:80 personal-portfolio:latest
```

Open <http://localhost:8080> in a browser. To verify the server from a terminal:

```bash
curl http://localhost:8080
```

The response should contain the portfolio page's HTML. You can also inspect the running container and its logs:

```bash
docker ps
docker logs personal-portfolio-site
```

Stop and remove the container when you are finished:

```bash
docker stop personal-portfolio-site
docker rm personal-portfolio-site
```

## Rebuild after editing

After changing `index.html`, stop and remove the existing container, then rebuild and run the updated image:

```bash
docker stop personal-portfolio-site
docker rm personal-portfolio-site
docker build -t personal-portfolio:latest .
docker run --name personal-portfolio-site -d -p 8080:80 personal-portfolio:latest
```

## Store the project on GitHub

If you cloned this project from GitHub, save and push your changes to your repository:

```bash
git add index.html Dockerfile .dockerignore README.md
git commit -m "Create personal portfolio website"
git push origin main
```

If you are starting from a local copy instead, first create an empty GitHub repository, then connect it and push:

```bash
git init
git add index.html Dockerfile .dockerignore README.md
git commit -m "Create personal portfolio website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

Replace the example URL with your repository's URL. Sign in to GitHub when prompted; never put a password or access token in the remote URL.
