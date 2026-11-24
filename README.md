# Kitameraki — Task Management App

| Folder | Project |
| --- | --- |
| [`backend/`](backend/README.md) | Task API — Express 5 + TypeScript + Azure Cosmos DB + Azure Blob Storage (files), deployable to Azure Function App |
| [`frontend/`](frontend/README.md) | Web client — React 18 + TypeScript + Vite + Fluent UI v9 + dnd-kit, form editor modelled after the bpmn.io form editor |
| [`docs/`](docs/) | Test case sheet and browser test evidence |

## Repositories

- **Root repository:** https://github.com/zulkifliraihan/test_kitameraki
- **Frontend repository (private):** https://github.com/zulkifliraihan/test_kitameraki-fe
  Access invitations have been sent to me@abdulhalimzhr.com, muhammadfaisalmaulanaputra2024@gmail.com, and faiz.sulistiyo@gmail.com. The invitation can be accepted through the following link: https://github.com/zulkifliraihan/test_kitameraki-fe/invitations
- **Backend repository:** https://github.com/zulkifliraihan/test_kitameraki-be
- **Backend pull request to the `main` branch:** https://github.com/MuhammadFaisalMaulanaPutra/kitameraki-be-test/pull/50

## Run everything with one command

Requirements: Docker (Docker Desktop / OrbStack). Works on x64 and Apple Silicon.

```bash
docker compose up --build
```

| What | URL |
| --- | --- |
| Web app | http://localhost:3000 |
| API | http://localhost:7071/api |
| Swagger UI | http://localhost:7071/api/docs |
| Cosmos DB emulator — Data Explorer | http://localhost:1234 |
| Azurite (Blob Storage emulator, uploaded files) | http://localhost:10000 |

The first start pulls the Cosmos DB emulator and Azurite images and waits for them to be healthy (~30 s). Optional sample data:

```bash
docker compose exec api node dist/scripts/seed.js
```

Stop with `docker compose down` (add `-v` to also delete the emulator data and uploaded files).

## Testing

| | Command | |
| --- | --- | --- |
| Backend unit + integration | `cd backend && npm test` | Jest + supertest (288 tests) |
| Frontend unit + component | `cd frontend && npm test` | Vitest + Testing Library (140 tests) |
| Lint | `npm run lint` (in each project) | ESLint + Prettier |
| API (manual / runner) | `backend/postman/*.postman_collection.json` | Postman / Newman (36 requests) |
| API (interactive) | http://localhost:7071/api/docs | Swagger UI |
| End-to-end (browser) | `docs/` | Test case sheet (55 cases) with Pass/Fail and screenshots |
