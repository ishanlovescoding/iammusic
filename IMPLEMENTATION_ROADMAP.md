# Replay - Implementation Roadmap
## From PRD to Production

**Document Version:** 1.0
**Last Updated:** November 18, 2025
**Target Launch:** 5 months (Week 20)

---

## Overview

This roadmap breaks down the implementation of Replay into actionable phases, from setup to production deployment. Based on the PRD, we'll focus on MVP first, then iterate.

---

## Phase 0: Pre-Development Setup (Week 1)
**Goal:** Set up all development infrastructure

### 1. Development Environment Setup

**Version Control:**
- [x] GitHub repository created (`iammusic`)
- [ ] Set up branch protection rules (main branch)
- [ ] Create development branch
- [ ] Set up `.gitignore` for Node.js, React, environment files

**Project Structure:**
```
iammusic/
├── frontend/          # React app
├── backend/           # Node.js/Express API
├── docs/              # Documentation
├── .github/           # GitHub Actions workflows
└── README.md
```

**Tools Installation:**
- [ ] Install Node.js (v18+ LTS)
- [ ] Install PostgreSQL locally (for development)
- [ ] Install Redis locally (for development)
- [ ] Install VS Code + recommended extensions
- [ ] Set up ESLint + Prettier (code formatting)

**Accounts Setup (All Free Tiers):**
- [ ] Create Vercel account (frontend hosting)
- [ ] Create Render.com account (backend hosting) OR Fly.io
- [ ] Create Neon account (PostgreSQL database) OR Supabase
- [ ] Create Upstash account (Redis cache)
- [ ] Create Cloudflare account (CDN + R2 storage)
- [ ] Create Spotify Developer account
- [ ] Create Firebase account (Cloud Messaging for notifications)
- [ ] Create Sentry account (error tracking)
- [ ] Create PostHog account (analytics) OR set up Umami

**Spotify App Setup:**
- [ ] Create Spotify app in Developer Dashboard
- [ ] Set up OAuth redirect URIs (localhost, staging, production)
- [ ] Save Client ID and Client Secret
- [ ] Request required scopes:
  - `user-read-currently-playing`
  - `user-read-recently-played`
  - `user-top-read`
  - `user-modify-playback-state`

---

## Phase 1: Design & Planning (Week 2)
**Goal:** Create visual designs and finalize architecture

### 1. UI/UX Design

**Design Tools:**
- [ ] Set up Figma account (free)
- [ ] Create design system (colors, typography, components)

**Screens to Design (Mobile + Desktop):**
- [ ] Landing page (not logged in)
- [ ] Onboarding flow (5 screens)
- [ ] Login/OAuth screen
- [ ] Home/Feed page
- [ ] Reveal screen (9:30pm)
- [ ] Calendar view (monthly grid)
- [ ] Day detail view
- [ ] Profile page (own + others)
- [ ] Settings page
- [ ] Friends list
- [ ] Notifications center

**Design Deliverables:**
- [ ] Mobile mockups (320-767px)
- [ ] Desktop mockups (1024px+)
- [ ] Component library
- [ ] Interactive prototype (optional)

### 2. Technical Architecture

**Database Schema:**
- [ ] Design PostgreSQL schema (see PRD Section 7.2.2)
- [ ] Create ERD (Entity Relationship Diagram)
- [ ] Plan indexes and constraints

**API Design:**
- [ ] Document all REST endpoints (see PRD Section 7.2.1)
- [ ] Create API documentation (OpenAPI/Swagger)
- [ ] Define request/response formats

**WebSocket Events:**
- [ ] Define real-time events
- [ ] Plan Socket.io room structure

---

## Phase 2: Backend Development (Weeks 3-8)
**Goal:** Build fully functional backend API

### Week 3-4: Core Infrastructure

**Initialize Backend:**
```bash
cd backend
npm init -y
npm install express pg redis socket.io jsonwebtoken bcrypt dotenv cors
npm install --save-dev nodemon eslint prettier
```

**Set up Express Server:**
- [ ] Create `server.js` with basic Express app
- [ ] Set up middleware (CORS, body-parser, helmet)
- [ ] Configure environment variables (.env)
- [ ] Set up error handling middleware
- [ ] Create health check endpoint (`GET /health`)

**Database Setup:**
- [ ] Connect to Neon/Supabase PostgreSQL
- [ ] Create migration system (use `node-pg-migrate` or Prisma)
- [ ] Run initial migrations (create tables)
- [ ] Set up database connection pool

**Redis Setup:**
- [ ] Connect to Upstash Redis
- [ ] Test connection
- [ ] Create session store

**File Structure:**
```
backend/
├── src/
│   ├── config/          # Database, Redis configs
│   ├── controllers/     # Route controllers
│   ├── middleware/      # Auth, validation, error handling
│   ├── models/          # Database models
│   ├── routes/          # API routes
│   ├── services/        # Business logic
│   ├── jobs/            # Background jobs (cron)
│   └── utils/           # Helper functions
├── migrations/          # Database migrations
├── tests/               # Unit & integration tests
├── .env.example
├── package.json
└── server.js
```

### Week 5: Authentication & Spotify Integration

**Spotify OAuth:**
- [ ] Implement OAuth 2.0 flow with PKCE
- [ ] Create `/auth/spotify` endpoint
- [ ] Create `/auth/callback` endpoint
- [ ] Store tokens securely (encrypted in DB)
- [ ] Implement token refresh logic
- [ ] Create middleware to verify Spotify token

**JWT Authentication:**
- [ ] Generate JWT on successful Spotify auth
- [ ] Create auth middleware
- [ ] Implement token refresh endpoint
- [ ] Create logout endpoint

**User Management:**
- [ ] Create user registration endpoint
- [ ] Create profile update endpoint
- [ ] Create profile fetch endpoint
- [ ] Implement username uniqueness check

### Week 6: Tracking System

**Backend Polling System (CRITICAL):**
- [ ] Create background job using node-cron or Bull Queue
- [ ] Implement polling logic:
  - Poll Spotify `/me/player/recently-played` every 30-60 min
  - Store in `listening_history` table
  - Deduplication using `played_at` timestamp
- [ ] Implement adaptive polling:
  - Track user listening volume
  - Adjust frequency (30min/60min/120min)
- [ ] Add gap detection (flag potential data loss)

**Client Sync API:**
- [ ] Create `POST /tracking/sync` endpoint
- [ ] Accept client-side listening data
- [ ] Merge with backend data (deduplication)
- [ ] Return acknowledgment

**Listening History:**
- [ ] Create `GET /tracking/today` endpoint
- [ ] Create `GET /tracking/history` endpoint (with date range)
- [ ] Implement pagination

### Week 7: Song of the Day & Social Features

**Song of the Day Calculation:**
- [ ] Create background job for 9:30pm (per timezone)
- [ ] Implement calculation algorithm:
  - Count plays per song
  - Tiebreaker: total duration
  - Tiebreaker: most recent
- [ ] Store in `daily_songs` table
- [ ] Trigger WebSocket event
- [ ] Trigger notification

**Friend System:**
- [ ] Create `POST /friends/request` endpoint
- [ ] Create `POST /friends/accept` endpoint
- [ ] Create `DELETE /friends/:id` endpoint
- [ ] Create `GET /friends` endpoint
- [ ] Create user search endpoint

**Feed API:**
- [ ] Create `GET /feed` endpoint
- [ ] Implement pagination
- [ ] Filter to friends only
- [ ] Sort by timestamp (reverse chronological)

**Reactions:**
- [ ] Create `POST /posts/:id/react` endpoint
- [ ] Create `DELETE /posts/:id/react` endpoint
- [ ] Create `GET /posts/:id/reactions` endpoint

**Comments:**
- [ ] Create `POST /posts/:id/comments` endpoint
- [ ] Create `GET /posts/:id/comments` endpoint
- [ ] Create `DELETE /comments/:id` endpoint

### Week 8: Real-time & Notifications

**WebSocket Server:**
- [ ] Set up Socket.io server
- [ ] Implement authentication for WebSocket
- [ ] Create user rooms
- [ ] Implement events:
  - `feed:new_post`
  - `reaction:added`
  - `comment:added`
  - `friend:request`
  - `friend:accepted`

**Push Notifications:**
- [ ] Set up Firebase Cloud Messaging
- [ ] Create notification subscription endpoint
- [ ] Implement notification sending:
  - Daily 9:30pm reveal
  - Friend requests
  - Reactions
  - Comments
- [ ] Store notification preferences

**Email Notifications (Fallback):**
- [ ] Set up Resend or Brevo
- [ ] Create email templates
- [ ] Implement email sending for iOS users

**Testing:**
- [ ] Write unit tests for all endpoints
- [ ] Write integration tests
- [ ] Test error handling
- [ ] Test rate limiting

---

## Phase 3: Frontend Development (Weeks 9-14)
**Goal:** Build fully functional React web app

### Week 9-10: Core Setup & Infrastructure

**Initialize Frontend:**
```bash
npx create-react-app frontend
cd frontend
npm install react-router-dom react-query axios socket.io-client
npm install tailwindcss framer-motion day.js
npm install @headlessui/react react-hook-form
```

**Project Structure:**
```
frontend/
├── public/
│   ├── manifest.json    # PWA manifest
│   └── service-worker.js
├── src/
│   ├── components/      # Reusable UI components
│   ├── pages/           # Page components
│   ├── hooks/           # Custom React hooks
│   ├── context/         # React Context (auth, user)
│   ├── services/        # API calls, WebSocket
│   ├── utils/           # Helper functions
│   ├── styles/          # Global styles
│   ├── App.js
│   └── index.js
├── tailwind.config.js
└── package.json
```

**Setup Tailwind CSS:**
- [ ] Configure Tailwind
- [ ] Create design tokens (colors, spacing, etc.)
- [ ] Set up dark mode

**Routing:**
- [ ] Set up React Router
- [ ] Define routes:
  - `/` - Landing page
  - `/login` - OAuth redirect
  - `/onboarding` - Onboarding flow
  - `/feed` - Main feed (protected)
  - `/calendar` - Calendar view (protected)
  - `/profile/:username` - Profile page
  - `/settings` - Settings page (protected)

**State Management:**
- [ ] Set up React Context for auth
- [ ] Set up React Query for server state
- [ ] Create API service layer (axios)

### Week 11: Authentication & Onboarding

**OAuth Flow:**
- [ ] Create login page
- [ ] Implement "Connect with Spotify" button
- [ ] Handle OAuth callback
- [ ] Store JWT in httpOnly cookie or localStorage
- [ ] Create protected route wrapper

**Onboarding Screens:**
- [ ] Welcome modal
- [ ] Create profile screen (username, photo, bio)
- [ ] Find friends screen (skippable)
- [ ] Privacy selection screen
- [ ] Notification permission request
- [ ] "Ready" screen

**Components:**
- [ ] Button component (primary, secondary, ghost)
- [ ] Input component (text, textarea)
- [ ] Modal component
- [ ] Avatar/Profile Picture component

### Week 12: Main Features

**Feed Page:**
- [ ] Create feed layout (responsive)
- [ ] Create post card component:
  - Profile picture + username
  - Album art
  - Song name + artist
  - Play count
  - Reaction ring
  - Action buttons
- [ ] Implement infinite scroll
- [ ] Implement pull-to-refresh (mobile)
- [ ] Integrate WebSocket for real-time updates

**Reveal Screen (9:30pm):**
- [ ] Full-screen reveal component
- [ ] Album art animation
- [ ] Song info display
- [ ] Stats (play count, duration)
- [ ] Share button
- [ ] Add to Queue button

**Calendar View:**
- [ ] Create monthly grid layout (7 columns)
- [ ] Display album art in squares
- [ ] Month navigation (prev/next)
- [ ] Swipe gestures (mobile)
- [ ] Day detail modal
- [ ] Responsive sizing

**Profile Page:**
- [ ] Profile header (avatar, username, bio)
- [ ] Today's song card
- [ ] Last 7 days mini-calendar
- [ ] Top stats (tracks, artists, genres)
- [ ] Friend count
- [ ] Edit profile button (own profile)

### Week 13: Social Features

**Reactions:**
- [ ] Reaction button
- [ ] Emoji picker modal/popover
- [ ] Reaction ring around album art
- [ ] Profile picture + emoji display
- [ ] Click to see all reactors
- [ ] Real-time reaction animation

**Comments:**
- [ ] Comment button
- [ ] Comment section (expandable or modal)
- [ ] Comment input with character counter
- [ ] Comment list
- [ ] Real-time comment updates
- [ ] Delete own comments

**Friends:**
- [ ] Friend list page
- [ ] Search users
- [ ] Friend request button
- [ ] Accept/decline requests
- [ ] Unfriend button with confirmation

**Notifications:**
- [ ] Request browser notification permission
- [ ] Set up service worker for push
- [ ] In-app notification center
- [ ] Notification badge
- [ ] Mark as read functionality

### Week 14: Settings & Polish

**Settings Page:**
- [ ] Account settings tab
- [ ] Privacy settings tab
- [ ] Notification settings tab
- [ ] App settings tab
- [ ] Connected accounts (Spotify)
- [ ] Delete account button

**Polish:**
- [ ] Loading states (skeleton screens)
- [ ] Empty states
- [ ] Error states
- [ ] Toast notifications (success, error)
- [ ] Animations (Framer Motion)
- [ ] Accessibility (ARIA labels, keyboard nav)
- [ ] Dark mode (already default)

**PWA Setup:**
- [ ] Create manifest.json
- [ ] Create service worker
- [ ] Add app icons (multiple sizes)
- [ ] Test "Add to Home Screen"
- [ ] Test offline mode

---

## Phase 4: Integration & Testing (Week 15-16)
**Goal:** Connect frontend + backend, comprehensive testing

### Week 15: Integration

**Connect Frontend to Backend:**
- [ ] Update API base URL
- [ ] Test all API endpoints
- [ ] Implement error handling
- [ ] Test WebSocket connection
- [ ] Test real-time updates

**End-to-End Flows:**
- [ ] Test complete OAuth flow
- [ ] Test onboarding flow
- [ ] Test tracking system (backend + client)
- [ ] Test 9:30pm reveal
- [ ] Test friend request flow
- [ ] Test reactions and comments
- [ ] Test notifications

**Cross-Device Testing:**
- [ ] Test on mobile browsers (iOS Safari, Chrome)
- [ ] Test on desktop browsers (Chrome, Firefox, Safari, Edge)
- [ ] Test on tablets
- [ ] Test PWA installation
- [ ] Test responsive design at all breakpoints

### Week 16: Testing & Bug Fixes

**Backend Testing:**
- [ ] Unit tests (Jest)
- [ ] Integration tests
- [ ] Load testing (simulate 100+ users)
- [ ] Security testing (SQL injection, XSS, CSRF)

**Frontend Testing:**
- [ ] Component tests (React Testing Library)
- [ ] E2E tests (Cypress or Playwright)
- [ ] Accessibility testing (Lighthouse, axe)
- [ ] Performance testing (Lighthouse)

**Bug Fixes:**
- [ ] Fix all critical bugs
- [ ] Fix high-priority bugs
- [ ] Document known issues (low priority)

---

## Phase 5: Deployment Setup (Week 17)
**Goal:** Deploy to production environment

### Database Setup (Production)

**Neon/Supabase:**
- [ ] Create production database
- [ ] Run migrations
- [ ] Set up connection pooling
- [ ] Configure backups
- [ ] Set up monitoring

### Backend Deployment

**Render.com or Fly.io:**
- [ ] Create new web service
- [ ] Connect GitHub repository
- [ ] Set environment variables:
  - `DATABASE_URL`
  - `REDIS_URL`
  - `SPOTIFY_CLIENT_ID`
  - `SPOTIFY_CLIENT_SECRET`
  - `JWT_SECRET`
  - `FIREBASE_CONFIG`
  - etc.
- [ ] Configure build command: `npm install && npm run build`
- [ ] Configure start command: `npm start`
- [ ] Deploy
- [ ] Test health endpoint

**Redis Setup:**
- [ ] Create Upstash Redis production instance
- [ ] Copy connection URL to backend env
- [ ] Test connection

**Domain Setup:**
- [ ] Purchase domain (optional, or use free subdomain)
- [ ] Configure DNS (if custom domain)

### Frontend Deployment

**Vercel or Netlify:**
- [ ] Connect GitHub repository
- [ ] Configure build settings:
  - Build command: `npm run build`
  - Publish directory: `build`
- [ ] Set environment variables:
  - `REACT_APP_API_URL` (backend URL)
  - `REACT_APP_SPOTIFY_CLIENT_ID`
  - `REACT_APP_FIREBASE_CONFIG`
- [ ] Deploy
- [ ] Test production site

**CDN Setup:**
- [ ] Connect Cloudflare to domain
- [ ] Configure caching rules
- [ ] Enable HTTPS
- [ ] Test CDN

**File Storage:**
- [ ] Set up Cloudflare R2 bucket
- [ ] Configure CORS
- [ ] Generate access keys
- [ ] Add to backend environment variables

### Monitoring & Analytics

**Sentry:**
- [ ] Create project
- [ ] Add Sentry SDK to backend
- [ ] Add Sentry SDK to frontend
- [ ] Test error tracking

**PostHog or Umami:**
- [ ] Set up analytics project
- [ ] Add tracking code to frontend
- [ ] Define events to track
- [ ] Test analytics

**UptimeRobot:**
- [ ] Add backend health check monitor
- [ ] Add frontend monitor
- [ ] Set up alert notifications (email)

---

## Phase 6: Beta Testing (Week 18)
**Goal:** Test with real users

### Beta Recruitment

- [ ] Recruit 50-100 beta testers:
  - 10 internal team
  - 30 friends & family
  - 20 from Reddit/Discord
  - 40 music enthusiasts

**Beta Environment:**
- [ ] Create beta subdomain (beta.replay.app)
- [ ] Deploy beta version
- [ ] Ensure same setup as production

### Feedback Collection

- [ ] Create feedback form (in-app)
- [ ] Set up Discord channel for beta testers
- [ ] Schedule weekly survey
- [ ] Conduct 1-on-1 user interviews

**Monitoring:**
- [ ] Watch error rates (Sentry)
- [ ] Track usage metrics (PostHog)
- [ ] Monitor performance (Lighthouse)
- [ ] Check server health (UptimeRobot)

### Iterate Based on Feedback

- [ ] Fix critical bugs within 24 hours
- [ ] Address high-priority feedback
- [ ] Make UX improvements
- [ ] Optimize performance

---

## Phase 7: Pre-Launch Preparation (Week 19)
**Goal:** Prepare for public launch

### Landing Page

- [ ] Design landing page
- [ ] Write compelling copy
- [ ] Add CTA buttons
- [ ] Add "How it works" section
- [ ] Add FAQ section
- [ ] Optimize for SEO
- [ ] Add social proof

### Marketing Materials

- [ ] Create product screenshots
- [ ] Create demo video
- [ ] Write Product Hunt description
- [ ] Prepare social media posts
- [ ] Create press kit

### Legal & Compliance

- [ ] Write Privacy Policy
- [ ] Write Terms of Service
- [ ] Ensure GDPR compliance
- [ ] Ensure CCPA compliance
- [ ] Add cookie consent banner (if needed)

### Final Polish

- [ ] Final round of bug fixes
- [ ] Performance optimization:
  - Reduce bundle size
  - Optimize images
  - Lazy load components
  - Cache static assets
- [ ] SEO optimization:
  - Meta tags
  - Open Graph tags
  - Sitemap.xml
  - Robots.txt
- [ ] Accessibility audit

---

## Phase 8: Launch! 🚀 (Week 20)
**Goal:** Public release

### Launch Day Checklist

**Morning:**
- [ ] Final smoke test on production
- [ ] Check all monitoring tools
- [ ] Ensure error tracking is working
- [ ] Have team on standby

**Launch Activities:**
- [ ] Post on Product Hunt
- [ ] Post on Reddit (r/Music, r/Spotify, r/InternetIsBeautiful)
- [ ] Post on Twitter thread
- [ ] Email beta testers
- [ ] Submit to tech blogs (TechCrunch, The Verge, etc.)
- [ ] Post on Hacker News

**Throughout Day:**
- [ ] Monitor server health
- [ ] Watch error rates
- [ ] Respond to user feedback
- [ ] Engage on social media
- [ ] Fix critical bugs immediately

---

## Post-Launch (Weeks 21+)
**Goal:** Iterate and grow

### Week 1-2 After Launch

**Monitoring:**
- [ ] Daily review of metrics (DAU, signups, retention)
- [ ] Daily error review (Sentry)
- [ ] Daily feedback review
- [ ] Performance monitoring

**Quick Wins:**
- [ ] Fix reported bugs
- [ ] Make small UX improvements
- [ ] Optimize performance bottlenecks

### Month 2-3: Growth & Iteration

**Based on PRD Phase 4:**
- [ ] Implement weekly recaps
- [ ] Add Music Twins feature
- [ ] Enhance stats
- [ ] Improve onboarding based on drop-off data
- [ ] A/B test key features

**Marketing:**
- [ ] Share user testimonials
- [ ] Create content (blog posts, tutorials)
- [ ] Partner with music influencers
- [ ] Implement referral system

---

## Success Metrics to Track

### Week 1-4:
- Total signups
- Daily active users (DAU)
- Spotify connection success rate
- Onboarding completion rate
- 9:30pm notification open rate

### Month 2-3:
- D7 retention
- D30 retention
- Average friends per user
- Reactions per user per week
- Viral coefficient (new users per existing user)

### Month 4-6:
- Reach 10,000 users
- Achieve 60%+ DAU rate
- 70%+ D7 retention
- 50%+ D30 retention

---

## Risk Mitigation

### Technical Risks:
- **Backend polling fails**: Set up alerts, have manual recovery process
- **Database fills up**: Implement data archiving before hitting 512MB
- **Render cold starts**: Switch to Fly.io or upgrade to paid tier
- **Spotify rate limits**: Implement exponential backoff, queue system

### Product Risks:
- **Low engagement**: A/B test notifications, make reveals more exciting
- **Low friend adoption**: Make solo mode valuable, add public explore
- **High churn**: Analyze drop-off points, improve onboarding

---

## Development Best Practices

### Code Quality:
- Use ESLint + Prettier
- Write meaningful commit messages
- Code review before merging
- Keep functions small and focused
- Document complex logic

### Git Workflow:
- `main` branch: production-ready code
- `develop` branch: integration branch
- Feature branches: `feature/feature-name`
- Bug fixes: `fix/bug-name`
- Pull requests for all changes

### Security:
- Never commit secrets (.env in .gitignore)
- Use environment variables
- Sanitize all inputs
- Use parameterized queries (prevent SQL injection)
- Implement rate limiting
- Use HTTPS everywhere

---

## Budget Tracking

### Current (Free Tier):
- Hosting: $0
- Database: $0
- Storage: $0
- Analytics: $0
- **Total: $0/month**

### When to Upgrade:
Monitor usage weekly. Set alerts at:
- Database: 400MB (80% of 512MB)
- Redis: 8K commands/day (80% of 10K)
- Bandwidth: 80GB (80% of 100GB)

---

## Next Immediate Steps

**This Week:**
1. [ ] Complete Phase 0 setup (accounts, tools)
2. [ ] Set up Spotify Developer App
3. [ ] Create initial GitHub repository structure
4. [ ] Start Phase 1 design (Figma)

**Next Week:**
1. [ ] Complete designs for all core screens
2. [ ] Finalize database schema
3. [ ] Start backend development

---

## Summary

**Total Timeline:** 20 weeks (~5 months)
- Weeks 1-2: Setup & Design
- Weeks 3-8: Backend Development
- Weeks 9-14: Frontend Development
- Weeks 15-16: Integration & Testing
- Week 17: Deployment
- Week 18: Beta Testing
- Week 19: Pre-Launch
- Week 20: Launch

**Resources Needed:**
- 1-2 Full-stack developers (can be solo if experienced)
- 1 Designer (can use Figma templates if needed)
- ~20-30 hours/week commitment

**Cost:** $0 until you hit 1K+ users

---

**Ready to start? Begin with Phase 0, Task 1: Development Environment Setup! 🚀**
