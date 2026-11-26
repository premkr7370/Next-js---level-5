# <span>⚡</span> Next.js Level 5

<div align="center">

![Next.js](https://img.shields.io/badge/Next.js-15.5.4-black?logo=nextdotjs)
![React](https://img.shields.io/badge/React-19.1.0-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-38B2AC?logo=tailwindcss&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

**A beginner-friendly Next.js App Router and JSON API learning project**

</div>

<p align="center">
  <img src="./public/next-level-demo.gif" alt="Next.js API demo" width="760">
</p>

---

## 🎯 Overview

This project is a compact example for learning how to:

- Build pages with the Next.js **App Router**
- Return JSON responses from Route Handlers
- Handle `GET` and `POST` HTTP methods
- Read URL query parameters
- Create dynamic API routes
- Use TypeScript with strict type checking
- Apply Tailwind CSS globally

> 🚧 The home page is currently minimal, while the API routes provide the main implemented functionality.

## 🧰 Technology Stack

| Technology | Version | Purpose |
| --- | --- | --- |
| Next.js | `15.5.4` | Framework and App Router |
| React | `19.1.0` | UI components |
| React DOM | `19.1.0` | React rendering |
| TypeScript | `5.x` | Static type checking |
| Tailwind CSS | `4.x` | Utility-first styling |
| ESLint | `9.x` | Code linting |

## ✨ Features

| Route | Description |
| --- | --- |
| `/` | Shared layout and minimal home page |
| `/api/user` | Fixed user data or echoed JSON body |
| `/api/search` | Read a `q` query parameter |
| `/api/post/[id]` | Return a dynamic post identifier |

### 👤 `/api/user`

- `GET` returns a fixed user object
- `POST` accepts a JSON body and echoes `name` and `age`

### 🔎 `/api/search`

- Reads the `q` URL query parameter
- Returns `null` when `q` is not provided

### 🆔 `/api/post/[id]`

- Uses a dynamic route segment named `id`
- Returns the supplied post ID as a JSON response

## 🚀 Getting Started

### Prerequisites

Install:

- Node.js 18.18 or newer
- npm, which is included with Node.js

### Installation

From the project directory, install dependencies:

```bash
npm install
```

### Run the Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

Next.js watches the source files and reloads changes automatically. The development server uses Turbopack.

### Production Build

Create an optimized production build:

```bash
npm run build
```

Start the production server:

```bash
npm run start
```

The production server defaults to [http://localhost:3000](http://localhost:3000).

### Run the Linter

```bash
npm run lint
```

## API Reference

All API routes return JSON. They do not currently require authentication and do not connect to a database.

### Get a sample user

```http
GET /api/user
```

Example response:

```json
{
  "name": "ayush",
  "age": 21
}
```

Example with `curl`:

```bash
curl http://localhost:3000/api/user
```

### Create or echo user data

```http
POST /api/user
Content-Type: application/json
```

Request body:

```json
{
  "name": "Ayush",
  "age": 22
}
```

Example response:

```json
{
  "name": "Ayush",
  "age": 22
}
```

Example with `curl`:

```bash
curl -X POST http://localhost:3000/api/user \
  -H "Content-Type: application/json" \
  -d "{\"name\":\"Ayush\",\"age\":22}"
```

### Search

```http
GET /api/search?q=nextjs
```

Example response:

```json
{
  "query": "nextjs"
}
```

Without a `q` parameter, `query` is `null`.

Example with `curl`:

```bash
curl "http://localhost:3000/api/search?q=nextjs"
```

### Get a dynamic post ID

```http
GET /api/post/[id]
```

Replace `[id]` with a post identifier:

```http
GET /api/post/42
```

Example response:

```json
{
  "postId": "42"
}
```

Example with `curl`:

```bash
curl http://localhost:3000/api/post/42
```

## Project Structure

```text
.
├── public/                 # Static assets
├── src/
│   └── app/
│       ├── api/
│       │   ├── post/[id]/route.ts
│       │   ├── search/route.ts
│       │   └── user/route.ts
│       ├── favicon.ico
│       ├── globals.css     # Tailwind import and base styles
│       ├── layout.tsx      # Shared root layout and metadata
│       └── page.tsx        # Home page
├── eslint.config.mjs       # ESLint configuration
├── next.config.ts          # Next.js configuration
├── package.json
├── postcss.config.mjs      # Tailwind/PostCSS configuration
└── tsconfig.json           # TypeScript configuration
```

## Configuration

### TypeScript

The project uses strict TypeScript mode. Source imports can use the configured `@/*` alias, which maps to `src/*`.

### Styling

`src/app/globals.css` imports Tailwind CSS and defines:

- Light and dark root color variables
- Geist font variables
- Default body background and foreground colors
- Automatic colors based on `prefers-color-scheme`

### Metadata

The default layout currently sets:

- Title: `Create Next App`
- Description: `Generated by create next app`

Update `metadata` in `src/app/layout.tsx` when customizing the application.

### Environment Variables

No environment variables are currently required. Files matching `.env*` are ignored by Git; add only the variables your implementation needs and provide an appropriate example file if more configuration is introduced.

## Development Notes

- The API routes use `NextRequest` and `NextResponse`.
- `POST /api/user` has no validation or persistence layer.
- `GET /api/search` reads the `q` parameter with `request.nextUrl.searchParams`.
- `GET /api/post/[id]` demonstrates a dynamic route segment.
- The API data is intentionally static or request-driven; no database, ORM, or external service is configured.
- There are no automated test scripts configured in `package.json`.

## Useful Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Turbopack development server |
| `npm run build` | Create a production build |
| `npm run start` | Start the production server |
| `npm run lint` | Run ESLint |

## Deployment

This project can be deployed anywhere that supports Next.js applications.

For a Vercel deployment:

1. Push the project to a Git repository.
2. Import the repository in Vercel.
3. Use the project root as the application directory.
4. Keep the default framework settings; no environment variables are currently required.

Alternatively, build and run it on a Node.js server:

```bash
npm run build
npm run start
```
