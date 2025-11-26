# command-onboard

A Claude Code slash command for quick project onboarding and architecture overview.

## Installation

```bash
# Clone to your preferred location
git clone git@github.com:claude-commands/command-onboard.git <clone-path>/command-onboard

# Symlink (use full path to cloned repo)
ln -s <clone-path>/command-onboard/onboard.md ~/.claude/commands/onboard.md
```

## Usage

```
/onboard              # Full project overview
/onboard api          # Focus on API layer
/onboard auth         # Focus on authentication
/onboard database     # Focus on data layer
```

## What it does

1. Analyzes project structure and tech stack
2. Identifies key architectural patterns
3. Maps out important files and directories
4. Generates getting started guide
5. Creates personal cheat sheet for quick reference

## Output Format

```markdown
# Project Onboarding: my-app

## Overview
A Node.js API for managing user content...

## Tech Stack
- TypeScript, Express, PostgreSQL, Redis

## Architecture
┌─────────┐     ┌─────────┐     ┌──────────┐
│ Client  │────▶│  API    │────▶│ Database │
└─────────┘     └─────────┘     └──────────┘

## Getting Started
```bash
npm install
cp .env.example .env
npm run dev
```

## Project Structure
```
src/
├── api/        # Routes and controllers
├── services/   # Business logic
├── models/     # Database models
└── utils/      # Shared utilities
```

## Cheat Sheet
- Add endpoint: Edit `src/api/routes.ts`
- Add migration: `npm run db:migration:create`
```

## Focus Areas

| Area | Content |
|------|---------|
| `api` | Endpoints, authentication, request/response |
| `auth` | Login flow, JWT/sessions, permissions |
| `database` | Tables, relationships, migrations |
| `frontend` | Components, state management, routing |

## Requirements

- Git repository with source code
- Claude Code with Opus 4.5 model access

## Updates

```bash
cd <clone-path>/command-onboard && git pull
```
