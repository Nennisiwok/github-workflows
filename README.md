# GitHub Workflows for Creating and Publishing Docker Images

This repository contains two GitHub Actions workflows for building and pushing Docker images to GitHub Container Registry (GHCR). Both workflows share the majority of their steps, with the primary difference being the use of Azure secrets in `deploy-image-pco`.

## Workflows Overview

### Workflow 1: `deploy-image-pco.yml`

- **Purpose**: Builds and pushes a Docker image with additional Azure secrets.
- **Triggers**: Can be triggered manually or called by another workflow.
- **Secrets Required**:
  - `AZURE_PCO_SECRETS_KEYVAULT_CLIENT_ID`
  - `AZURE_RESOURCE_GROUP_TENANT_ID`
  - `AZURE_PCO_SECRETS_KEYVAULT_CLIENT_SECRET`
  - `AZURE_PCO_SECRETS_KEYVAULT_URL`

### Workflow 2: `deploy-image.yml`

- **Purpose**: Builds and pushes a Docker image without requiring Azure secrets.
- **Triggers**: Can be triggered manually or called by another workflow.
  
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

## Notes

The workflow `deploy-image-pco.yml` is created to be used in AppDataQuality repository.

## Conclusion

These workflows help automate the process of building and publishing Docker images, streamlining the CI/CD pipeline.


