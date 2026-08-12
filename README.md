# Mini ERP + CRM Operations Portal

Full-stack case study project for a wholesale/distribution company. It includes JWT login, role-based access, customer CRM, product inventory, stock movement logs, and sales challans with stock-safe confirmation.

## Tech Stack

- Backend: Node.js, TypeScript, Express.js, PostgreSQL
- Frontend: React, TypeScript, Vite, CSS
- Database: PostgreSQL
- Local infra: Docker Compose

## Run Locally

```bash
npm install
docker compose up -d
npm run seed
npm run dev
```

Frontend: `http://localhost:5173`

Backend: `http://localhost:4000`

## Login Credentials

All accounts use password `Password@123`.

| Role | Email |
| --- | --- |
| Admin | admin@example.com |
| Sales | sales@example.com |
| Warehouse | warehouse@example.com |
| Accounts | accounts@example.com |

## Environment Variables

Backend `.env`:

```bash
PORT=4000
DATABASE_URL=postgres://erp_user:erp_password@localhost:5432/mini_erp_crm
JWT_SECRET=local-development-secret-change-me
FRONTEND_ORIGIN=http://localhost:5173
```

Frontend `.env`:

```bash
VITE_API_URL=http://localhost:4000
```

## Main API Routes

- `POST /auth/login`
- `GET /dashboard/summary`
- `GET /customers`
- `POST /customers`
- `PUT /customers/:id`
- `POST /customers/:id/followups`
- `GET /products`
- `POST /products`
- `PUT /products/:id`
- `POST /products/:id/movements`
- `GET /products/movements/log`
- `GET /challans`
- `POST /challans`
- `GET /challans/:id`
- `PATCH /challans/:id/confirm`

## Business Rules

- Confirmed challans reduce product stock in a database transaction.
- Stock cannot go negative.
- Insufficient stock returns `409 Conflict`.
- Challan items store product snapshot data: name, SKU, category, price, quantity, and line total.
- Stock movements store product, quantity, movement type, reason, user, and timestamp.

## Deployment

Suggested free deployment:

- Frontend: Vercel or Netlify
- Backend: Render, Railway, or Fly.io
- Database: Neon, Supabase, Render Postgres, or Railway Postgres

Set production values for `DATABASE_URL`, `JWT_SECRET`, `FRONTEND_ORIGIN`, and `VITE_API_URL`.

## Assumptions And Limitations

- PostgreSQL was selected from the allowed database options.
- AWS deployment, invoice PDF export, and S3 upload are treated as optional bonus items.
- The UI uses compact local state navigation to keep the assignment small and reviewable.
