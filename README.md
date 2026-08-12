A full-stack ERP and CRM web application designed for a wholesale/distribution business. The application provides role-based access, customer management, inventory tracking, stock movement history, and sales challan management.

## 🚀 Features

* 🔐 JWT-based authentication
* 👥 Role-based access control
* 📊 Dashboard with business summary
* 🤝 Customer CRM management
* 📦 Product and inventory management
* 🔄 Stock movement tracking
* 🧾 Sales challan creation and management
* ✅ Stock-safe challan confirmation
* 🚫 Prevention of negative inventory
* 🗃️ PostgreSQL database
* 🐳 Docker Compose support
* 📡 RESTful backend APIs

## 🛠️ Tech Stack

### Frontend

* React
* TypeScript
* Vite
* CSS
* Lucide React

### Backend

* Node.js
* TypeScript
* Express.js
* JWT
* Zod
* PostgreSQL

### Development & Infrastructure

* Docker
* Docker Compose
* npm Workspaces

## 📁 Project Structure

```text
mini-erp-crm-portal/
│
├── frontend/
│   ├── src/
│   │   ├── App.tsx
│   │   └── style.css
│   ├── index.html
│   ├── package.json
│   └── vite.config.ts
│
├── backend/
│   ├── src/
│   │   ├── server.ts
│   │   └── seed.ts
│   ├── schema.sql
│   └── package.json
│
├── docs/
│   └── postman_collection.json
│
├── docker-compose.yml
├── package.json
└── README.md
```

## ⚙️ Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/mini-erp-crm-portal.git
cd mini-erp-crm-portal
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start PostgreSQL

Make sure Docker is installed and running, then execute:

```bash
docker compose up -d
```

### 4. Configure environment variables

Create the required `.env` files using the provided `.env.example` files.

#### Backend

```env
PORT=4000
DATABASE_URL=postgres://erp_user:erp_password@localhost:5432/mini_erp_crm
JWT_SECRET=local-development-secret-change-me
FRONTEND_ORIGIN=http://localhost:5173
```

#### Frontend

```env
VITE_API_URL=http://localhost:4000
```

> **Important:** Never commit your actual `.env` files or production secrets to GitHub.

### 5. Seed the database

```bash
npm run seed
```

### 6. Start the application

```bash
npm run dev
```

The application will be available at:

* Frontend: `http://localhost:5173`
* Backend API: `http://localhost:4000`

## 🔑 Demo Login Credentials

All demo accounts use:

```text
Password: Password@123
```

| Role      | Email                                                 |
| --------- | ----------------------------------------------------- |
| Admin     | [admin@example.com](mailto:admin@example.com)         |
| Sales     | [sales@example.com](mailto:sales@example.com)         |
| Warehouse | [warehouse@example.com](mailto:warehouse@example.com) |
| Accounts  | [accounts@example.com](mailto:accounts@example.com)   |

## 📡 API Endpoints

### Authentication

```text
POST /auth/login
```

### Dashboard

```text
GET /dashboard/summary
```

### Customers

```text
GET /customers
POST /customers
PUT /customers/:id
POST /customers/:id/followups
```

### Products

```text
GET /products
POST /products
PUT /products/:id
POST /products/:id/movements
GET /products/movements/log
```

### Sales Challans

```text
GET /challans
POST /challans
GET /challans/:id
PATCH /challans/:id/confirm
```

A Postman collection is available in:

```text
docs/postman_collection.json
```

## 💼 Business Logic

The application implements several important business rules:

* Confirming a sales challan decreases product stock.
* Stock updates are performed inside a database transaction.
* Product stock cannot become negative.
* Insufficient stock returns a `409 Conflict` response.
* Challans store product snapshot information such as:

  * Product name
  * SKU
  * Category
  * Price
  * Quantity
  * Line total
* Stock movements record:

  * Product
  * Quantity
  * Movement type
  * Reason
  * User
  * Timestamp

## 🧪 Build for Production

Build both frontend and backend:

```bash
npm run build
```

Start the backend production server:

```bash
npm run start --workspace backend
```

## 🌐 Deployment

The application can be deployed using services such as:

* Frontend: Vercel / Netlify
* Backend: Render / Railway / Fly.io
* Database: Neon / Supabase / Railway PostgreSQL

Production environment variables should be configured securely on the hosting platform.

## 🔮 Future Improvements

* Invoice PDF generation
* AWS S3 document uploads
* Advanced reporting and analytics
* Pagination and filtering
* Email notifications
* Audit log dashboard
* Automated testing
* CI/CD pipeline
* Production cloud deployment

## 👨‍💻 Project Purpose

This project demonstrates full-stack application development with:

* React and TypeScript
* REST API development
* Authentication and authorization
* PostgreSQL database design
* Transaction-safe business logic
* Inventory management
* CRM workflows
* Docker-based local development

---

⭐ If you find this project useful, consider giving the repository a star.
