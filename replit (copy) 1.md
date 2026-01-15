# CampusHub - Campus Real Life Problem Solver

## Overview

CampusHub is a centralized student utility platform designed to solve common campus problems. It provides a unified hub for marketplace transactions, lost & found reporting, academic resource sharing, internship discovery, and alumni networking. The platform targets students, juniors, seniors, and alumni within a college campus ecosystem.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight client-side routing)
- **State Management**: TanStack React Query for server state, local React hooks for UI state
- **Styling**: Tailwind CSS with custom design system using CSS variables
- **Component Library**: shadcn/ui components built on Radix UI primitives
- **Build Tool**: Vite with hot module replacement

The frontend follows a feature-based organization with pages (`client/src/pages/`), reusable components (`client/src/components/`), and custom hooks (`client/src/hooks/`) for data fetching and business logic.

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript (ESM modules)
- **API Pattern**: RESTful API with typed route definitions in `shared/routes.ts`
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Validation**: Zod schemas for input validation, drizzle-zod for database schema integration

The backend uses a simple layered architecture:
- `server/routes.ts` - API endpoint handlers
- `server/storage.ts` - Data access layer with database operations
- `server/db.ts` - Database connection pool management

### Shared Code
The `shared/` directory contains code used by both frontend and backend:
- `schema.ts` - Drizzle database schema definitions and Zod validation schemas
- `routes.ts` - API route contracts with typed inputs and outputs

### Data Models
The platform manages six core entities:
1. **Users** - Students and alumni with profiles
2. **Marketplace Items** - Buy/sell listings with categories and conditions
3. **Lost & Found Items** - Reported lost or found items with status tracking
4. **Academy Resources** - Study notes, PDFs, and educational materials
5. **Internships** - Job postings with domain and location filters
6. **Referrals** - Alumni-provided job referral opportunities

### Build System
- Development: `tsx` for direct TypeScript execution with Vite dev server
- Production: esbuild bundles server code, Vite builds static frontend assets
- Database migrations: Drizzle Kit with `db:push` command

## External Dependencies

### Database
- **PostgreSQL** - Primary data store, connection via `DATABASE_URL` environment variable
- **Drizzle ORM** - Type-safe database queries and schema management
- **connect-pg-simple** - PostgreSQL session store (available but session management is simplified for MVP)

### UI Framework
- **Radix UI** - Accessible component primitives (dialog, dropdown, tabs, etc.)
- **shadcn/ui** - Pre-styled component library configured in `components.json`
- **Tailwind CSS** - Utility-first CSS with custom theme in `tailwind.config.ts`
- **Lucide React** - Icon library

### Form & Validation
- **React Hook Form** - Form state management
- **Zod** - Schema validation for API inputs and form data
- **@hookform/resolvers** - Zod integration with React Hook Form

### Data Fetching
- **TanStack React Query** - Server state management with caching and optimistic updates

### Date Handling
- **date-fns** - Date formatting and manipulation utilities

### Development Tools
- **Vite** - Frontend build tool with HMR
- **esbuild** - Fast server bundling for production
- **TypeScript** - Type safety across the stack