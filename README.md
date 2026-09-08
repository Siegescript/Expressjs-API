# > Express.js MySQL REST API

A practice/template RESTful API built with Express.js, Sequelize ORM, and MySQL, feat. session-based authentication, input validation, rate limiting, and password hashing.

## > Tech Stack

* **Runtime:** Node.js (ES Modules)

* **Framework:** Express.js

* **Database & ORM:** MySQL, Sequelize

* **Authentication:** Passport.js (`LocalStrategy`), `express-session`, `bcrypt`

* **Validation & Security:** `express-validator`, `express-rate-limit`, `cors`

---

## > Project Architecture

```text
├── src/
│   ├── config/
│   │   ├── database.mjs     # Sequelize connection, sync, and seeding logic
│   │   └── passport.mjs     # Local strategy and serialization configuration
│   ├── controllers/
│   │   ├── authController.mjs # Authentication request handlers
│   │   └── userController.mjs # CRUD operations for users
│   ├── middlewares/
│   │   ├── auth.mjs         # Route protection middleware
│   │   ├── logger.mjs       # Request logging middleware
│   │   ├── rateLimiters.mjs # Global and auth rate limit definitions
│   │   ├── resolveUser.mjs  # Database lookup utility for ID parameters
│   │   └── validate.mjs     # Express-validator error handling middleware
│   ├── models/
│   │   ├── userModel.mjs    # Sequelize User model with lifecycle hooks
│   │   └── userModel_mock.mjs # Initial seeding dataset
│   ├── routes/
│   │   ├── authRoutes.mjs   # Authentication endpoints
│   │   └── userRoutes.mjs   # User resource endpoints
│   └── utils/
│       └── validationSchemas.mjs # validation rule definitions
└── index.mjs                # Application entry point and server startup

```

---

## > Getting Started

### Prerequisites

* Node.js

* MySQL Server installed and running locally

### Installation

1. Clone the repository:
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name

```

2. Install dependencies:
```bash
npm install

```

3. Configure your environment variables:
Create a `.env` file in the root directory matching this template:
```env
NODE_ENV=development
PORT=3000
SESSION_SECRET={your_super_secret_key_here}
DATABASE_PASSWORD={your_mysql_root_password}

```

4. Create the MySQL database:
Ensure you have a database named `expressjs_api` created in your MySQL instance.

5. Awaken the server:
```bash
npm run dev

```

*(The application automatically handles database connection, schema synchronization, and secure initial seed generation on first boot).*

---

## > API Endpoints

### Authentication (`/api/auth`)

* `POST /api/auth/login` - Authenticates user credentials and establishes a secure session. (Protected by rate limiting).

* `POST /api/auth/logout` - Destroys the active session and clears cookies.

* `GET /api/auth/status` - Returns the currently authenticated user payload or `401 Unauthorized`.

### Users (`/api/users`)

* `GET /api/users` - Retrieves a paginated, filterable list of users.

* `POST /api/users` - Registers a new user with automatic password hashing.

* `GET /api/users/:id` - Retrieves a single user by primary key.

* `PUT /api/users/:id` - Complete replacement of a user record.

* `PATCH /api/users/:id` - Partial update of a user record.

* `DELETE /api/users/:id` - Deletes a user record (Requires active authentication).
