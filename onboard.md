---
argument-hint: "[focus-area]"
description: "Quick project onboarding and architecture overview"
model: claude-opus-4-5-20251101
allowed-tools: ["Bash", "Read", "Glob", "Grep", "AskUserQuestion"]
---

**If `$ARGUMENTS` is empty or not provided:**

Generate a comprehensive project overview for onboarding.

**Usage:** `/onboard [focus-area]`

**Examples:**
- `/onboard` - Full project overview
- `/onboard api` - Focus on API layer
- `/onboard auth` - Focus on authentication
- `/onboard database` - Focus on data layer

**Workflow:**
1. Analyze project structure and tech stack
2. Identify key architectural patterns
3. Map out important files and directories
4. Generate getting started guide
5. Create personal cheat sheet

Proceed with full project overview.

---

**If `$ARGUMENTS` is provided:**

Generate a focused onboarding guide for the specified area.

## Configuration

- **Focus Area**: `$ARGUMENTS` (optional: api, auth, database, frontend, etc.)

## Steps

1. **Analyze Project Structure**

   ```bash
   # Get directory structure
   tree -L 3 -I 'node_modules|vendor|.git|dist|build' --dirsfirst

   # Count files by type
   fd -e ts -e js -e go -e py | wc -l
   ```

   Identify:
   - Project type (web app, API, CLI, library)
   - Primary language(s)
   - Framework(s) in use
   - Directory organization pattern

2. **Detect Tech Stack**

   Check for:
   - **Frontend**: React, Vue, Angular, Svelte
   - **Backend**: Express, Gin, Django, FastAPI
   - **Database**: PostgreSQL, MongoDB, Redis
   - **Infrastructure**: Docker, Kubernetes, Terraform
   - **Testing**: Jest, pytest, go test
   - **CI/CD**: GitHub Actions, GitLab CI, Jenkins

   Read key config files:
   - `package.json`, `go.mod`, `requirements.txt`
   - `docker-compose.yml`, `Dockerfile`
   - `.github/workflows/`

3. **Identify Key Files**

   Find and read:
   - Entry points (`main.ts`, `index.js`, `main.go`)
   - Configuration (`config/`, `.env.example`)
   - Route definitions (API endpoints)
   - Database schemas/models
   - README and documentation

4. **Map Architecture**

   Create a mental model:
   ```markdown
   ## Architecture Overview

   ```
   ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
   │   Client    │────▶│   API       │────▶│  Database   │
   │  (React)    │     │  (Express)  │     │  (Postgres) │
   └─────────────┘     └─────────────┘     └─────────────┘
                              │
                              ▼
                       ┌─────────────┐
                       │   Cache     │
                       │   (Redis)   │
                       └─────────────┘
   ```

   ### Data Flow
   1. Client makes request
   2. API validates and processes
   3. Database query/mutation
   4. Response returned
   ```

5. **Document Key Patterns**

   Identify patterns used:
   - **Repository pattern** for data access
   - **Service layer** for business logic
   - **Middleware** for cross-cutting concerns
   - **Event-driven** for async processing

6. **Create Getting Started Guide**

   ```markdown
   # Getting Started

   ## Prerequisites
   - Node.js 18+
   - PostgreSQL 14+
   - Redis 7+

   ## Setup

   ```bash
   # Clone and install
   git clone <repo>
   npm install

   # Configure environment
   cp .env.example .env
   # Edit .env with your values

   # Database setup
   npm run db:migrate
   npm run db:seed

   # Start development
   npm run dev
   ```

   ## Key Commands

   | Command | Description |
   |---------|-------------|
   | `npm run dev` | Start dev server |
   | `npm test` | Run tests |
   | `npm run lint` | Lint code |
   | `npm run build` | Production build |

   ## Project Structure

   ```
   src/
   ├── api/          # API routes and controllers
   ├── services/     # Business logic
   ├── models/       # Database models
   ├── middleware/   # Express middleware
   ├── utils/        # Shared utilities
   └── config/       # Configuration
   ```
   ```

7. **Generate Cheat Sheet**

   ```markdown
   # Project Cheat Sheet

   ## Quick Reference

   ### API Endpoints
   - `GET /api/users` - List users
   - `POST /api/users` - Create user
   - `GET /api/users/:id` - Get user

   ### Database Models
   - `User` - User accounts
   - `Post` - User content
   - `Comment` - Post comments

   ### Key Files to Know
   - `src/api/routes.ts` - All API routes
   - `src/services/auth.ts` - Authentication logic
   - `src/models/user.ts` - User model

   ### Environment Variables
   - `DATABASE_URL` - PostgreSQL connection
   - `REDIS_URL` - Redis connection
   - `JWT_SECRET` - Auth secret

   ### Common Tasks

   **Add a new API endpoint:**
   1. Add route in `src/api/routes.ts`
   2. Create handler in `src/api/controllers/`
   3. Add service logic in `src/services/`
   4. Write tests in `__tests__/`

   **Add a database migration:**
   1. Create migration: `npm run db:migration:create`
   2. Edit migration file
   3. Run: `npm run db:migrate`
   ```

8. **Area-Specific Deep Dive**

   If focus area provided, go deeper:

   **For `api`:**
   - List all endpoints with methods
   - Show request/response formats
   - Explain authentication flow

   **For `auth`:**
   - Explain auth mechanism (JWT, sessions)
   - Show login/logout flow
   - Document permissions/roles

   **For `database`:**
   - List all tables/collections
   - Show relationships
   - Explain migration process

## Output Structure

```markdown
# Project Onboarding: [Project Name]

## Overview
[2-3 sentence summary]

## Tech Stack
[Languages, frameworks, databases]

## Architecture
[Diagram and explanation]

## Getting Started
[Setup instructions]

## Project Structure
[Directory layout with explanations]

## Key Concepts
[Important patterns and conventions]

## Cheat Sheet
[Quick reference for common tasks]

## Next Steps
[Suggested areas to explore]
```

## Notes

- Prioritize information new developers need most
- Include both high-level overview and practical details
- Reference existing documentation if available
- Highlight conventions and coding standards
- Point out potential gotchas or surprises
