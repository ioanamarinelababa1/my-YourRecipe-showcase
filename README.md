# Culinardea (Showcase)

## Overview
Culinardea is a digital cooking journal web application that allows users to explore cooking-related content and create their own personalized recipes and notes.

The application focuses on usability, data persistence, and security, offering users a structured and interactive way to manage their cooking ideas.

## Status
https://culinardea.app/

## ! For branding point of view I renamed the app from YourRecipe to Culinardea.


---

## Tech Stack
- HTML, CSS, JavaScript
- Node.js (local development server)
- PostgreSQL (database)
- Supabase (backend services & database management)
- Docker (containerization)
- Git / GitHub (version control)
- iTerm2 (development environment)
- Cloudflare Turnstile (bot protection)
- VS Code (programming)
- Dynamic recipe catalog via Supabase (migrated from static JavaScript)
- Node.js + Express (backend API server, port 3001)
- Nodemailer (email service — configured)
- dotenv (environment variables management)

---

## Features
- User authentication (login & registration)
- Email verification system
- Add, edit, and delete personal recipes
- Persistent data storage using PostgreSQL
- Account deletion with complete data removal
- Feedback & issue reporting system
- Responsive UI with custom design (header, footer, layout)
- Responsive design complet
- Admin image management — upload or replace recipe images via URL or file upload, persisted in Supabase Storage
- Recipes loaded dynamically from Supabase PostgreSQL with local fallback
- Professional email routing via ImprovMX — contact@culinardea.app forwards to dedicated inbox

---

## Security

### Authentication & Authorization
- OAuth 2.0 Google Authentication via Supabase
- Email + Password authentication with JWT session management
- Secure email change — confirmation required on both addresses
- Secure password change — recent session required
- Password reset via signed email link
- Account selector forced at every Google login (prompt: select_account)

### Password Security
- Password strength checker — 5 levels: WEAK → MEDIUM → GOOD → STRONG → FORTRESS
- HaveIBeenPwned API integration — k-anonymity check against 600M+ compromised passwords
- Minimum 8 characters with complexity requirements (uppercase, lowercase, digits, special characters)
- Blacklist of 30 common/forbidden passwords
- Weak pattern detection (repetitions, sequences, keyboard patterns)

### Anti-Abuse & Bot Protection
- Cloudflare Turnstile — anti-bot protection (active on HTTPS deployment)
- Rate limiting with exponential backoff: 3 fails → 15s, 5 fails → 5min, 10 fails → 30min
- Supabase Attack Protection enabled

### Database Security
- Row Level Security (RLS) enforced on all 12 PostgreSQL tables
- Each user accesses exclusively their own data
- Automatic profile creation via database trigger
- Cascade delete — complete data removal on account deletion
- Foreign key constraints on all relational tables
- Admin role system via dedicated admins table — role-based access control for privileged operations
- Recipe images protected by RLS — only admin can upload, update or delete images
- Secure storage of sensitive data (environment variables, secrets)


### Frontend Security
- XSS protection: escapeHTML() global sanitizer on all user inputs
- Tips sanitizer: strict whitelist (only strong, em, br tags permitted)
- URL validation: only https:// permitted — blocks javascript:, data:, vbscript:
- Zero sensitive data in localStorage
- Local HTTP server (Node.js) replacing insecure file:// protocol

### Legal & Compliance
- GDPR compliant: Privacy Policy, Terms & Conditions, Cookie Policy
- Cookie consent banner with Accept/Reject options
- Explicit consent checkbox at registration
- Data operator identified (Art. 13 GDPR)
- Data retention periods documented
- User rights documented and accessible (access, rectification, deletion, portability)
- Supabase declared as third-party EU data processor (West EU, Ireland)

---

## Backend Architecture

- Supabase service key secured in server/.env — never exposed to browser
- Routes: /api/auth, /api/recipes, /api/email
- Middleware: rate limiting, admin-only protection
- Recipes loaded via backend API — not directly from browser
- Health check endpoint: GET /api/status

---

### Backend & API Security
- Backend API layer (Node.js + Express) separating frontend from database
- Admin-only middleware protecting sensitive endpoints
- Server-side rate limiting via express-rate-limit (5 req/15min login, 100 req/15min general)
- CORS configured to accept only trusted origins
- Helmet.js security headers on all API responses

---

## Advanced Security (Planned)
- Performing basic security testing (penetration testing principles)
- Identifying and mitigating common vulnerabilities (OWASP Top 10)
- Improving API security and access control mechanisms
- Enhancing overall application security posture
- Two-Factor Authentication (2FA)
- Secure API design and protection against common attacks
- Protection against SQL Injection
  
---

## PWA — Progressive Web App
- Installable on iPhone and Android as native app
- Offline support via Service Worker cache
- Custom theme color and splash screen
- Apple mobile web app optimized

---

## UI / UX
- Clean and modern interface
- Warm color palette
- Structured layout for intuitive navigation
- Focus on user-friendly experience
- 3D effect
- Split Login Page Transition

---

## Infrastructure
- Custom domain deployed: culinardea.app (Vercel + Namecheap)
- Professional email 
- HTTPS enforced automatically via Vercel

---

## What I’m Learning
- Full-stack web development fundamentals
- Authentication & security best practices
- Database design and integration (PostgreSQL)
- Containerization using Docker
- Debugging and problem solving
- Designing and UX
- How to manage security problems

---

## System
Users can:
- Send reviews
- Report bugs or issues
- Suggest improvements
- Add recipes to Favorites section
- Add recipes to Tried section
- Add their own recipes with images into a separate window, like a digital cooking book
- Add tips
- Check out season's fruits, vegetables
  
---

## Database Architecture
- 15 PostgreSQL tables with RLS (added: recipe_images, admins)- Automatic profile creation via database triggers
- 152 recipes migrated from static JavaScript to PostgreSQL (recipes_catalog)
- Cascade delete for complete data removal
- Foreign key constraints on all tables
  
---

## Next Improvements
- Advanced search functionality
- AI-based recipe suggestions
- Performance optimization
- Loading state optimization for Supabase recipe fetching
- Recipe order persistence from database

---

## Future Infrastructure & Security Improvements
- Deployment in a cloud environment (e.g., AWS / Azure / GCP)
- Implementation of scalable and highly available architecture
- Secure configuration of cloud resources (networking, access control)
- Continuous monitoring and logging

---

## Note
The full source code is maintained in a private repository for security and intellectual property protection.

© 2026 Culinardea. 
