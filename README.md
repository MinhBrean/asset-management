# Asset Management System

Monorepo: NestJS (backend) + React/Vite (frontend) + PostgreSQL.

## Requirements
- Docker (and Docker Compose)

## Quick start (Docker-only dev)
1) Copy env files

- backend:
  - Copy `backend/.env.example` to `backend/.env` and fill values.

2) Start stack
```bash
docker compose up -d --build
```

3) Run database migrations (inside backend container)
```bash
docker compose exec backend npx prisma migrate dev
```

4) Seed admin user (reads ADMIN_EMAIL/ADMIN_PASSWORD from `backend/.env`)
```bash
docker compose exec backend npm run seed
```

5) Open app
- Frontend: http://localhost:3001
- Backend: http://localhost:3000/api

## Notes
- Admin is created only via `npm run seed`.
- Asset update uses optimistic concurrency via `version` (409 on conflict) and writes `AssetLog`.