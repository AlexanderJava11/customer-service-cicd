# 🚀 DevOps – Customer Service

Customer Service är en av två tjänster som används i min individuella DevOps-uppgift.

## CI/CD

Projektet använder en CI/CD-pipeline med:

- GitHub Actions för Continuous Integration
- Maven för automatiska tester
- Docker för containerisering
- Docker Hub för lagring av Docker-image
- Railway för automatisk deployment

## Pipeline

Vid varje push till `master` startar GitHub Actions automatiskt.

Pipelinen:

1. Checkar ut projektet
2. Installerar Java
3. Kör Maven-tester
4. Loggar in på Docker Hub
5. Bygger en Docker-image
6. Pushar Docker-imagen till Docker Hub

Docker-steget körs endast om testerna lyckas.

## Docker

Docker-imagen publiceras på Docker Hub:

`acomaco/devops-customer-service`

## Deployment

Tjänsten deployas automatiskt till Railway när ny kod pushas till `master`.

Production:

`https://devops-customer-service-production-d3fc.up.railway.app`

## Secrets och Environment Variables

Känsliga värden är inte hårdkodade i applikationens produktionskonfiguration.

GitHub Secrets används för Docker Hub-inloggning.

Railway Environment Variables används bland annat för:

- Databasanslutning
- Databasanvändare och lösenord
- JWT secret
- Admin credentials

`.env`-filer ignoreras via `.gitignore` och pushas inte till GitHub.
