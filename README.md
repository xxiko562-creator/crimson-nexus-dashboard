# Crimson Nexus Dashboard

A responsive analytics dashboard starter using React, Tailwind CSS, Express, and PostgreSQL.

## Requirements
- Node.js 20+
- npm 10+
- Docker (recommended for local PostgreSQL), or a PostgreSQL 14+ server

## Quick start
1. Copy `server/.env.example` to `server/.env` and set a long random `JWT_SECRET` and your database URL.
2. Start PostgreSQL: `docker compose up -d postgres`
3. Install dependencies: `npm install`
4. Create tables: `npm run migrate -w server`
5. Start both apps: `npm run dev`

Client: http://localhost:5173  
API: http://localhost:4000/api

## Demo account
Register a new account at `/register`. The dashboard is protected and redirects unauthenticated users to sign in.

## Production checklist
- Use HTTPS and secure cookie settings behind a trusted proxy.
- Set a strong, unique JWT_SECRET (at least 32 random bytes).
- Use a managed PostgreSQL instance, backups, and least-privilege DB credentials.
- Configure exact CORS origins; never use `*` with credentials.
- Add email verification, password reset, rate limiting at the edge, audit logging, and monitoring before public launch.
- Replace sample analytics with real, authorization-scoped business data.
- Add CSRF protection if changing auth to cookie-based sessions.
- Keep secrets out of source control.

## Architecture
- `client/src/app`: routing and app providers
- `client/src/components`: shared UI and shell
- `client/src/features`: auth and dashboard feature modules
- `server/src/routes`: HTTP endpoints
- `server/src/middleware`: authentication and error handling
- `server/src/db`: PostgreSQL pool and migrations
- `server/src/services`: business logic

Authentication uses bcrypt password hashing and short-lived signed JWTs. The starter stores the token in sessionStorage for simplicity; for production, prefer secure, HttpOnly, SameSite cookies with CSRF protections.
