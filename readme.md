# > Sanctum Expressus: The Omnissiah's REST API

*"There is no truth in flesh, only betrayal. There is no strength in flesh, only weakness. There is no constancy in flesh, only decay. There is only certainty in the Machine Spirit and a `200 OK` response."* — *Canticles of the Fabricator-General*

A sacred RESTful shrine built with Express.js, Sequelize ORM, and MySQL. This noospheric interface has been consecrated with session-based authentication, validation rites, rate-limiting wards, and cryptographic seals to protect against scrapcode and heresy.

## > Sacred STC Patterns (Tech Stack)

* **The Motive Force (Runtime):** Node.js (ES Modules)

* **Routing Canticles (Framework):** Express.js

* **Data-Crypts & Relational Matrix (Database):** MySQL, Sequelize

* **Wards of Identity (Auth):** Passport.js (`LocalStrategy`), `express-session`, `bcrypt`

* **Purity Seals (Sanitization):** `express-validator`, `express-rate-limit`, `cors`


---


## > Architecture of the Data-Loom (Project Structure)

```text
├── src/
│   ├── config/
│   │   ├── database.mjs     # Cogitator linkage, sync, and unique-hash seeding rites
│   │   └── passport.mjs     # Local strategy and soul-serialization configuration
│   ├── controllers/
│   │   ├── authController.mjs # Authentication and session management handlers
│   │   └── userController.mjs # CRUD operations for adept entities
│   ├── middlewares/
│   │   ├── auth.mjs         # Route safeguarding against scrapcode and unauthorized access
│   │   ├── logger.mjs       # Vox-net request logging ritual
│   │   ├── rateLimiters.mjs # Global and auth brute-force deflector shields
│   │   └── validate.mjs     # Purity seal verification and error interception
│   ├── models/
│   │   ├── userModel.mjs    # Schema inscribed with cryptographic hooks
│   │   └── userModel_mock.mjs # Initial raw dataset for the Machine Spirit
│   ├── routes/
│   │   ├── authRoutes.mjs   # Rites of passage endpoints
│   │   └── userRoutes.mjs   # Adept resource endpoints
│   └── utils/
│       └── validationSchemas.mjs # DRY field validation and sanitization runes
└── index.mjs                # Application entry point and server startup liturgy
```


---


## > Litany of Activation (Getting Started)


### Augmetic Requirements


* Node.js (v18+ recommended by the Tech-Priests)
* MySQL Server installed and operational


### Rites of Assembly


1. **Download the STC to your local cogitator:**

```bash
git clone https://github.com/Siegescript/Express.js-API.git
cd Express.js-API
```

2. **Invoke the Fabricator (Package Installation):**

```bash
npm install
```

3. **Inscribe the sacred runes of configuration.** Create a `.env` file in the root sanctum matching this template:

```env
NODE_ENV=development
PORT=3000
SESSION_SECRET=[sacred_machine_key]
DATABASE_PASSWORD=[your_mysql_root_password]
```

4. **Prepare the Data-Crypt:**

Ensure a schema named `expressjs_api` exists within your MySQL instance before proceeding.

5. **Awaken the Machine Spirit:**

```bash
npm run dev
```


> **Note from the Lexmechanics:** *The application automatically establishes database communication, synchronizes models, and seeds the initial mock users with uniquely hashed passwords on first ignition. Do not interrupt this holy process.*


---


## > Noospheric Vox-Channels (API Endpoints)


### Rites of Access (`/api/auth`)


* `POST /api/auth/login` - Validates credentials, compares cryptographic hashes, and establishes a secure session cookie (Shielded by strict rate limiting).

* `POST /api/auth/logout` - Severs the noospheric tether, destroying the active session and purging the cookie.

* `GET /api/auth/status` - Consults the Machine Spirit to return the active user payload, or returns `401 Unauthorized` if the spirit finds you lacking.


### Servitor & Adept Registry (`/api/users`)


* `GET /api/users` - Divines a paginated, filterable manifest of users utilizing fuzzy search operators.

* `POST /api/users` - Registers a new adept with automatic password hashing rites.

* `GET /api/users/:id` - Retrieves a single entity's data slate by primary key.

* `PUT /api/users/:id` - The Rite of Replacement; completely overwrites a user record.

* `PATCH /api/users/:id` - The Rite of Modification; partially updates a user record.

* `DELETE /api/users/:id` - Administers the Rite of Purging (Requires blessed authentication to execute).