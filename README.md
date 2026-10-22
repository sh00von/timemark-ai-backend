# TimeMark AI — Backend API (Express.js, YouTube Subtitle Extraction, Google Gemini AI)

The **backend REST API** for **TimeMark AI**, built with **Node.js and Express**. It provides user authentication, **YouTube subtitle extraction**, and **AI-powered processing with Google Gemini**, with data handled through **Supabase** and interactive **Swagger / OpenAPI documentation** served from the API root.

> 🖥️ **Frontend:** the companion web app lives in the [`timemark-ai-frontend`](https://github.com/sh00von/timemark-ai-frontend) repository.

## Features

- **YouTube subtitle extraction API** — fetch subtitles/captions from YouTube videos (SRT format, via `youtube-dl-exec`)
- **AI endpoints** — Google Gemini integration (`@google/genai` / `@google/generative-ai`) for AI-powered content processing
- **JWT authentication** — signup/login routes with JSON Web Token based route protection
- **Supabase integration** — `@supabase/supabase-js` client for database and backend services
- **Interactive API docs** — Swagger UI with a generated OpenAPI spec served at the server root
- **Production-minded middleware** — Helmet security headers, CORS, Morgan request logging, centralized error handling, and Winston logging
- **Docker support** — a `Dockerfile` is included for containerized deployment
- **Clean project layout** — routes, controllers, middleware, validations, and utilities kept in separate modules under `src/`

## Tech Stack

- **Runtime:** Node.js
- **Framework:** Express 4
- **AI:** Google Gemini (`@google/genai`, `@google/generative-ai`)
- **Database / BaaS:** Supabase
- **Auth:** JSON Web Tokens (jsonwebtoken)
- **Subtitles:** youtube-dl-exec
- **Docs:** Swagger UI Express + swagger-jsdoc (OpenAPI)
- **Other:** Axios, Helmet, Morgan, Winston, dotenv

## Getting Started

### Prerequisites

- Node.js 18+ and npm (or pnpm)
- A Supabase project and a Google Gemini API key for the AI features

### Installation

```bash
git clone https://github.com/sh00von/TimeMark-AI-Backend.git
cd TimeMark-AI-Backend
npm install
```

Create a `.env` file in the project root with the keys the server expects (see the configuration under `src/config/` and the Supabase folder), then start the server:

```bash
# production
npm start

# development (auto-reload with nodemon)
npm run dev
```

The API runs on **port 5000** by default (`PORT` environment variable).

## Usage

Once running, open the interactive documentation in your browser:

```text
http://localhost:5000/
```

Main route groups:

| Route           | Purpose                                  |
| --------------- | ---------------------------------------- |
| `/api/auth`     | User registration and login (JWT)        |
| `/api/subtitles`| YouTube subtitle extraction              |
| `/api/ai`       | AI-powered processing (Google Gemini)    |
| `/`             | Swagger UI / OpenAPI documentation       |

Regenerate the OpenAPI spec with:

```bash
npm run docs
```

Run it with Docker:

```bash
docker build -t timemark-ai-backend .
docker run -p 5000:5000 --env-file .env timemark-ai-backend
```

## Project Structure

```text
TimeMark-AI-Backend/
├── src/
│   ├── index.js        # Express app entry point
│   ├── config/         # configuration & OpenAPI generation
│   ├── routes/         # auth, subtitles, and AI routes
│   ├── controllers/    # request handlers
│   ├── middleware/     # auth & error handling
│   ├── validations/    # request validation
│   └── utils/          # logger and helpers
├── supabase/           # Supabase-related setup
├── Dockerfile
└── package.json
```

---

⭐ If you find this API useful, a star is appreciated! For the web interface, check out the companion repo: [`timemark-ai-frontend`](https://github.com/sh00von/timemark-ai-frontend).
