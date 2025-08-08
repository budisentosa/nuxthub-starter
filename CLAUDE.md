# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a NuxtHub starter template that demonstrates full-stack application development on Cloudflare's edge infrastructure. It showcases NuxtHub's storage capabilities including blob storage, database, and key-value store.

## Development Commands

- `pnpm install` - Install dependencies
- `pnpm dev` - Start development server on localhost:3000
- `pnpm build` - Build for production
- `pnpm preview` - Preview production build locally with NuxtHub
- `pnpm lint` - Run ESLint
- `pnpm typecheck` - Run TypeScript type checking

## Deployment Commands

- `npx nuxthub deploy` - Deploy to Cloudflare via NuxtHub

## Architecture

### NuxtHub Integration
This project uses NuxtHub with the following storage features enabled:
- **Database**: SQLite with `hubDatabase()` for persistent data storage
- **Blob Storage**: File upload handling with `hubBlob()` for images
- **Key-Value Store**: Simple data storage with `hubKV()` for redirects
- **Cache**: API response caching with `cachedEventHandler()`

### Application Structure
- **Frontend**: Single page application with three main components:
  - `ImageGallery`: Image upload and display using blob storage
  - `MessagesPanel`: Chat interface using SQLite database
  - `RedirectsPanel`: URL redirects management using KV store

### Server API Organization
API routes are organized by feature:
- `server/api/images/` - Image upload, retrieval, and deletion
- `server/api/messages/` - Message CRUD operations
- `server/api/redirects/` - Redirect management
- `server/api/cached.get.ts` - Demonstrates API response caching

### Database Schema
The messages table is auto-created with:
```sql
CREATE TABLE IF NOT EXISTS messages (
  id INTEGER PRIMARY KEY, 
  text TEXT, 
  created_at INTEGER
)
```

### Configuration Notes
- Uses Nuxt 4 compatibility features
- OpenAPI documentation is enabled for server routes
- Image uploads are restricted to PNG/JPEG, max 8MB
- TypeScript configuration extends from Nuxt's generated config