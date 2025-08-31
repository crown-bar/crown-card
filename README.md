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