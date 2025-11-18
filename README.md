Use the Product Requirements Document I uploaded to generate the complete frontend of Replay, a Spotify-integrated social music diary. Build it using Next.js (App Router), Tailwind CSS, TypeScript, and Vercel best practices. The backend will be hosted separately, so all API calls should point to the environment variable NEXT_PUBLIC_API_URL. Never embed secrets — all secure actions must call the backend.

Requirements:

App Architecture
	•	Use Next.js App Router
	•	Use server components for static/SEO content, client components for interactive UI
	•	Implement full PWA support:
	•	/public/manifest.json
	•	/public/service-worker.js
	•	push notification subscription UI (calls backend)
	•	Include proper SEO defaults, OG tags, and metadata routes

Core Pages to Generate
	•	/feed — main social feed
	•	/calendar — personal music calendar
	•	/profile/[username] — user profiles with stats
	•	/settings — settings & privacy page
	•	/auth/callback — Spotify OAuth callback screen (UI only)
	•	/ — landing page with product explanation & CTA

UI Requirements
	•	Use Tailwind + a minimal dark theme matching the PRD
	•	Use Framer Motion for animations
	•	Use responsive layouts for:
	•	mobile (primary)
	•	tablet
	•	desktop
	•	Implement reusable components:
	•	AlbumArt
	•	SongCard
	•	ReactionRing
	•	BottomNav (mobile)
	•	SidebarNav (desktop)
	•	ProfileHeader
	•	CalendarGrid
	•	NotificationButton
	•	LoadingSkeleton components

API Requirements

All API interactions must:
	•	Use fetch() from /lib/api.ts
	•	Read NEXT_PUBLIC_API_URL
	•	Assume backend routes such as:
	•	/auth/status
	•	/feed
	•	/calendar
	•	/profile/:username
	•	/reactions
	•	/notifications/subscribe
	•	Never store secrets in the client

State Management
	•	Use React Query for server data
	•	Use Context for global user state (auth, theme)

Spotify Requirements
	•	The frontend should NOT handle token exchange
	•	The OAuth callback page should only:
	•	display a loading state
	•	call NEXT_PUBLIC_API_URL/auth/callback
	•	redirect to /feed on success

Push Notifications
	•	Add:
	•	Firebase client setup
	•	Permission request modal
	•	Backend call: /notifications/register

Real-Time Updates
	•	Add WebSocket client using NEXT_PUBLIC_WS_URL
	•	Implement:
	•	updates in feed
	•	reaction animations
	•	live comments count

File Storage
	•	Load album art & profile images using:
	•	Cloudflare R2 public URLs
	•	fallback placeholders

Error Handling
	•	Use Sentry client SDK (DSN from env)
	•	Add error boundary pages:
	•	/error
	•	/not-found

Misc
	•	Provide clean folder structure
	•	Follow accessibility standards (WCAG 2.1)
	•	Include loading states, empty states & skeletons
	•	Use optimistic UI updates for reactions & comments

The goal is to generate a complete, production-quality frontend scaffold fully aligned with the PRD, ready to integrate with my backend.
