# crown-card
An express app with a postgres database to administer the cards of crown bar costumers.

## Running with Docker

Prerequisites: Docker and Docker Compose installed.

- Build and start the stack:
  docker compose up --build

- The API will be available at http://localhost:3000
- Postgres will be exposed on localhost:5432 (default user/password: postgres/postgres, db: crown)

You can override credentials by exporting environment variables before running compose:
- POSTGRES_USER, POSTGRES_PASSWORD, POSTGRES_DB
- AUTH_TOKEN, ADMIN_AUTH_TOKEN

Example:
  POSTGRES_PASSWORD=secret AUTH_TOKEN=mytoken ADMIN_AUTH_TOKEN=admin docker compose up --build

## CI/CD: Build and publish Docker image

A GitHub Actions workflow is included at .github/workflows/docker-publish.yml.
It is configured to run only manually (on workflow_dispatch). Use the Actions tab in GitHub, select "Build and Publish Docker image", and click "Run workflow" to start a build/publish.

By default it targets GitHub Container Registry (ghcr.io). To use it:
- Ensure the repository is public or grant read permissions to the package if private.
- Optionally set these repository secrets to use a custom registry:
  - REGISTRY (default ghcr.io)
  - REGISTRY_USERNAME
  - REGISTRY_PASSWORD

Image name defaults to <owner>/<repo>. Published reference for GHCR will be:
  ghcr.io/<owner>/<repo>:latest (on default branch)
  ghcr.io/<owner>/<repo>:<git-sha>
  ghcr.io/<owner>/<repo>:<tag> (for version tags)