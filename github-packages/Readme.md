
# GitHub Packages: Docker Image Push Guide

This guide explains how to build, tag, and push a Docker image to GitHub Packages using the GitHub Container Registry (`ghcr.io`).

## Prerequisites
- Docker installed and running
- GitHub account
- A personal access token (PAT) with `write:packages`, `read:packages`, and `delete:packages` scopes

## Steps

1. **Set environment variables:**
	```bash
	export GH_USERNAME='<your-github-username>'
	export GH_TOKEN='<your-github-token>'
	export GH_IMAGE_NAME='<your-image-name>'
	export GH_VER='<image-version>'
	```

2. **Authenticate Docker to GitHub Container Registry:**
	```bash
	echo "$GH_TOKEN" | docker login ghcr.io -u "$GH_USERNAME" --password-stdin
	```

3. **Tag your Docker image:**
	```bash
	docker tag ${GH_IMAGE_NAME}:latest ghcr.io/${GH_USERNAME}/${GH_IMAGE_NAME}:${GH_VER}
	```

4. **Push the image to GitHub Packages:**
	```bash
	docker push ghcr.io/${GH_USERNAME}/${GH_IMAGE_NAME}:${GH_VER}
	```

## Notes
- Never commit your personal access token to source control.
- Replace placeholders (e.g., `<your-github-username>`) with your actual values.
- For more details, see [GitHub Docs: Working with the Container registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry).