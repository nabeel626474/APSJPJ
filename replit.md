# School Management System

## Overview

This is a comprehensive school management system designed for Army Public Schools and Colleges (APSACS). The application provides student registration, fee management, challan generation, and parent portal functionality. It features a modern React frontend with a Node.js/Express backend, using PostgreSQL for data persistence.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack React Query for server state and caching
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS v4 with custom theme configuration
- **Forms**: React Hook Form with Zod validation
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Runtime**: Node.js with Express
- **Language**: TypeScript with tsx for execution
- **API Design**: RESTful API endpoints under `/api` prefix
- **Session Management**: Express sessions with PostgreSQL session store (connect-pg-simple)
- **Authentication**: Passport.js with local strategy, bcryptjs for password hashing

### Data Storage
- **Database**: PostgreSQL with Drizzle ORM
- **Schema Location**: `shared/schema.ts` contains all table definitions
- **Migrations**: Drizzle Kit for schema migrations (`npm run db:push`)
- **Session Storage**: PostgreSQL table for persistent sessions

### Authentication Flow
- Username/password authentication with Passport local strategy
- Session-based authentication stored in PostgreSQL
- Protected routes using `isAuthenticated` middleware
- Default admin account created on first run (admin/admin123)
- Separate parent portal authentication path

### Project Structure
```
├── client/           # React frontend application
│   ├── src/
│   │   ├── components/  # UI components (shadcn/ui + custom)
│   │   ├── pages/       # Route page components
│   │   ├── hooks/       # Custom React hooks
│   │   └── lib/         # Utilities and configurations
├── server/           # Express backend
│   ├── index.ts      # Server entry point
│   ├── routes.ts     # API route definitions
│   ├── auth.ts       # Authentication configuration
│   ├── db.ts         # Database connection
│   └── storage.ts    # Data access layer
├── shared/           # Shared code between client/server
│   └── schema.ts     # Drizzle database schema
```

### Build and Development
- **Development**: `npm run dev` runs the full-stack application with hot reload
- **Production Build**: `npm run build` compiles both client (Vite) and server (esbuild)
- **Database Sync**: `npm run db:push` pushes schema changes to PostgreSQL

## External Dependencies

### Database
- **PostgreSQL**: Primary database, connection via `DATABASE_URL` environment variable
- **Drizzle ORM**: Type-safe database queries and schema management

### Authentication & Security
- **Passport.js**: Authentication middleware framework
- **bcryptjs**: Password hashing
- **express-session**: Session management
- **connect-pg-simple**: PostgreSQL session store

### Environment Variables Required
- `DATABASE_URL`: PostgreSQL connection string
- `SESSION_SECRET`: Secret for session encryption

### Third-Party UI Libraries
- **Radix UI**: Accessible UI primitives (dialogs, dropdowns, forms, etc.)
- **Recharts**: Chart library for dashboard visualizations
- **react-to-print**: PDF/print functionality for fee challans
- **xlsx**: Excel file parsing for bulk student imports
- **date-fns**: Date formatting and manipulation

### Development Tools
- **Vite**: Frontend build tool with HMR
- **esbuild**: Server bundling for production
- **Drizzle Kit**: Database migration tooling