# Workflows

This repository contains reusable GitHub Actions workflows.

## Workflow List

### Build Node.js Workflow

**File Path**: [`.github/workflows/build-nodejs.yml`](.github/workflows/build-nodejs.yml)

#### Description
This workflow builds a Node.js project and uploads the build artifacts.

#### Inputs
- `path-to-artifact` (required): The path to the build artifact(s) to be uploaded.

#### Example Usage
You can call this workflow from another workflow:

```yml
jobs:
  build:
    uses: postboys/workflows/.github/workflows/build-nodejs.yml@main
    with:
      path-to-artifact: 'dist/**'
```

### Deploy Workflow

**File Path**: [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml)

### Description

This workflow deploys the project to a server using SSH.

#### Inputs

- `SSH_HOST` (required): The SSH host of the server.
- `SSH_PRIVATE_KEY` (required): The private SSH key for authentication.
- `SSH_USER` (required): The SSH user for authentication.
- `VAULT_ADDR` (required): The address of the Vault server.
- `VAULT_ROLE_ID` (required): The role ID for Vault authentication.
- `VAULT_SECRET_ID` (required): The secret ID for Vault authentication.

#### Example Usage

You can call this workflow from another workflow:

```yml
jobs:
  deploy:
    uses: postboys/workflows/.github/workflows/deploy.yml@main
    with:
      SSH_HOST: ${{ secrets.SSH_HOST }}
      SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
      SSH_USER: ${{ secrets.SSH_USER }}
      VAULT_ADDR: ${{ secrets.VAULT_ADDR }}
      VAULT_ROLE_ID: ${{ secrets.VAULT_ROLE_ID }}
      VAULT_SECRET_ID: ${{ secrets.VAULT_SECRET_ID }}
```
