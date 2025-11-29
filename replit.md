# FinEdu AZ

## Overview

FinEdu AZ is a personal finance management web application designed for users in Azerbaijan. The platform enables users to track expenses, manage budgets, set financial goals, and receive personalized financial advice. It features multilingual support (Azerbaijani, English, Russian), dark/light themes, and regional expense comparisons based on user demographics.

The application provides an intuitive dashboard for monitoring monthly income and expenses, a transaction management system with categorization, goal tracking with progress visualization, and an AI-powered financial advisor ("Finny") that provides contextual advice based on user spending patterns and regional averages.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React with TypeScript for type-safe component development
- Vite as the build tool and development server for fast HMR (Hot Module Replacement)
- Wouter for lightweight client-side routing instead of React Router
- React Query (@tanstack/react-query) for server state management and data fetching

**UI Component System**
- shadcn/ui component library with Radix UI primitives for accessible, unstyled components
- Tailwind CSS for utility-first styling with custom design tokens
- "New York" style variant from shadcn/ui
- Custom color system supporting light/dark themes via CSS variables
- Component aliases configured for clean imports (@/components, @/lib, @/hooks)

**State Management**
- Context API for global state (Authentication, Language, Theme)
- React Query for server state with aggressive caching (staleTime: Infinity)
- Local Storage for persisting user preferences (language, theme)
- Session-based authentication state

**Internationalization**
- Custom i18n implementation supporting Azerbaijani (az), English (en), and Russian (ru)
- Language switching via LanguageContext with localStorage persistence
- All UI text, error messages, and content fully translated

**Styling Approach**
- Premium fintech aesthetic inspired by Stripe, Revolut, N26
- Gradient backgrounds and smooth animations
- Consistent spacing system (Tailwind units: 2, 4, 6, 8, 12, 16, 20, 24)
- Typography: Inter and Plus Jakarta Sans fonts from Google Fonts
- Responsive design with mobile-first approach

### Backend Architecture

**Server Framework**
- Express.js with TypeScript for the API server
- HTTP server creation for potential WebSocket support
- Session-based authentication using express-session with MemoryStore
- Custom middleware for request logging and authentication

**Data Storage**
- In-memory storage implementation (IStorage interface)
- No database dependency - data stored in runtime memory
- Regional averages hardcoded from Azerbaijani demographic data
- User data, transactions, goals, and regional statistics managed in-memory

**API Design**
- RESTful API structure with `/api` prefix
- Authentication endpoints: `/api/auth/login`, `/api/auth/register`, `/api/auth/me`
- Resource endpoints: `/api/transactions`, `/api/goals`, `/api/averages`, `/api/finny`
- Protected routes requiring session authentication
- Consistent error handling and response formats

**Security**
- bcryptjs for password hashing
- Session-based authentication with httpOnly cookies
- CORS configuration for cross-origin requests
- Input validation using Zod schemas

**Business Logic**
- "Finny" financial advisor generates contextual advice based on:
  - Monthly income vs expenses
  - Category-wise spending patterns
  - Comparison with regional averages (age group + city)
  - Goal progress tracking
  - Savings rate calculations

### Data Models

**User Schema**
- Fields: id, fullName, age, region, password (hashed), language, theme, createdAt
- Regions: 10 major Azerbaijani cities (Bakı, Gəncə, Şəki, etc.)
- Age validation: 14-100 years
- Multi-language and theme preferences

**Transaction Schema**
- Fields: id, userId, date, category, amount, type (income/outcome), description
- Categories: food, transport, entertainment, education, health, shopping, utilities, other
- Date-based filtering for monthly reports

**Goal Schema**
- Fields: id, userId, title, targetAmount, currentAmount, createdAt
- Progress tracking with percentage calculations
- Incremental savings additions

**Regional Average Schema**
- Pre-populated demographic expense data
- Dimensions: region (city), ageGroup (14-18, 19-25, 26-35, 35+), averageExpense
- Used for comparative financial analysis

### External Dependencies

**UI Component Libraries**
- @radix-ui/* - 20+ accessible UI primitives (dialogs, dropdowns, popovers, etc.)
- lucide-react - Icon library for consistent iconography
- react-day-picker - Calendar component for date selection
- cmdk - Command palette component

**Form Management**
- react-hook-form - Form state and validation
- @hookform/resolvers - Zod integration for schema validation
- zod - Runtime type validation and schema definition

**Utility Libraries**
- date-fns - Date manipulation and formatting
- clsx & tailwind-merge - Conditional className composition
- class-variance-authority - Component variant management
- nanoid - Unique ID generation

**Development Tools**
- tsx - TypeScript execution for development
- esbuild - Production server bundling
- @replit/vite-plugin-* - Replit-specific development enhancements

**Authentication & Security**
- bcryptjs - Password hashing
- express-session - Session management
- memorystore - In-memory session store
- connect-pg-simple - PostgreSQL session store (configured but not actively used)

**Database (Configured)**
- @neondatabase/serverless - Neon PostgreSQL driver
- drizzle-orm - TypeScript ORM
- drizzle-kit - Database migration toolkit
- Note: Database is configured but the application currently uses in-memory storage

**Fonts & Styling**
- Google Fonts: Inter, Plus Jakarta Sans
- Tailwind CSS with PostCSS and Autoprefixer
- Custom CSS variables for theming