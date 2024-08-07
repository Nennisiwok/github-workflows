# GitHub Workflows for Creating and Publishing Docker Images

This repository contains two GitHub Actions workflows for building and pushing Docker images to GitHub Container Registry (GHCR). Both workflows share the majority of their steps, with the primary difference being the use of Github secrets in `deploy-image-pco`.

## Common Steps in Both Workflows

1. **Checkout Repository**: Retrieves the code from the repository.
2. **Log in to the Container Registry**: Authenticates to GHCR using GitHub credentials.
3. **Extract Metadata**: Gathers metadata (tags, labels) for the Docker image.
4. **Build and Push Docker Image**: Builds the Docker image and pushes it to the container registry.

## Using the Workflows

### Manually Triggering the Workflows

1. Go to the Actions tab in your GitHub repository.
2. Select the desired workflow (`deploy-image-pco` or `deploy-image`).
3. Click the "Run workflow" button.

### Calling the Workflows from Another Workflow

To call them from another workflow, use the `workflow_call` event and ensure the required secrets (for `deploy-image-pco.yml`) are provided.

## Conclusion

These workflows help automate the process of building and publishing Docker images, streamlining the CI/CD pipeline.


