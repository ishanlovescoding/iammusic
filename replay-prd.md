# Product Requirements Document (PRD)

## Replay - Your Daily Music Diary

**Version:** 1.0  
**Last Updated:** November 18, 2025  
**Document Owner:** Product Team  
**Status:** Draft  
**Platform:** Web Application (Mobile & Desktop)

---

## 1. Executive Summary

### 1.1 Product Overview
Replay is a social music tracking web application that transforms daily Spotify listening into shareable moments. The app automatically tracks users' listening habits throughout the day and reveals their most-played song at 9:30pm, creating a visual music diary through a BeReal-style calendar interface. Accessible via any web browser on mobile and desktop devices.

### 1.2 Problem Statement
- Spotify users lack a daily ritual to reflect on their music consumption
- Music discovery through friends is fragmented and relies on manual sharing
- Spotify Wrapped only happens once per year
- No elegant way to visualize and archive personal music history
- Social music sharing lacks the immediacy and engagement of modern social apps
- No native cross-platform solution that works seamlessly on mobile and desktop

### 1.3 Solution
A web-based passive tracking application that:
- Automatically monitors Spotify listening throughout the day
- Reveals a "song of the day" at 9:30pm
- Creates a visual calendar archive of daily top songs
- Enables social music discovery through friend connections
- Uses BeReal-style reactions (profile pictures + emojis) for engagement
- Works seamlessly across mobile browsers and desktop browsers
- No app store download required - instant access via URL

### 1.4 Success Metrics
- **Daily Active Users (DAU):** 60%+ of registered users check at 9:30pm
- **Retention:** 70%+ D7 retention, 50%+ D30 retention
- **Social Engagement:** Average 3+ reactions per user per week
- **Viral Growth:** Organic registration rate of 1.5+ new users per existing user
- **Session Time:** Average 2-3 minutes per daily session
- **Cross-Platform Usage:** 50%+ users access from both mobile and desktop

---

## 2. Goals & Objectives

### 2.1 Product Goals
1. Create a compelling daily music ritual at 9:30pm
2. Build a social network around authentic music discovery
3. Provide users with a nostalgic, visual archive of their listening history
4. Achieve organic viral growth through friend invitations and social sharing
5. Deliver seamless experience across mobile and desktop browsers

### 2.2 Business Goals
- Reach 10,000 users within 3 months of launch
- Achieve 60%+ daily active user rate
- Generate organic social media buzz and word-of-mouth growth
- Establish foundation for future monetization (premium features)
- Build a scalable web platform without app store dependencies

### 2.3 User Goals
- Effortlessly track daily music consumption
- Discover new music through friends' genuine listening habits
- Create a visual archive of musical memories
- Share music taste with friends in a low-pressure way
- Engage with friends' music choices authentically
- Access from any device without downloading an app

---

## 3. Target Audience

### 3.1 Primary Users
**Music-Forward Gen Z & Millennials (Ages 16-32)**
- Active Spotify users (daily listeners)
- Socially engaged on Instagram, TikTok, BeReal
- Value music as part of their identity
- Enjoy sharing and discovering music
- Comfortable with daily-ritual apps
- Use both mobile and desktop devices

### 3.2 User Personas

**Persona 1: "The Music Sharer" - Emma, 22**
- Uses Spotify 3+ hours daily on her phone
- Constantly shares songs on Instagram stories
- Has strong opinions about music taste
- Wants to be seen as having good taste
- Values what friends are listening to
- Checks social apps throughout the day on mobile

**Persona 2: "The Nostalgic Listener" - Marcus, 26**
- Loves looking back at old playlists
- Associates songs with specific memories/periods of life
- Enjoys journaling and tracking personal data
- Less social, more introspective
- Wants a personal music archive
- Prefers desktop for deeper browsing, mobile for quick checks

**Persona 3: "The Discoverer" - Aisha, 19**
- Always looking for new music
- Follows music influencers
- Trusts friend recommendations over algorithms
- Active in group chats sharing songs
- FOMO around missing out on trends
- Uses phone throughout day, desktop for homework/work

### 3.3 Secondary Users
- Music enthusiasts who want to build a public following
- Friend groups who want a shared music space
- Casual listeners curious about their habits
- Desktop workers who listen while working

---

## 4. Platform Requirements

### 4.1 Web Application Specifications

#### 4.1.1 Browser Support
**Priority:** P0 (Must Have)

**Desktop Browsers:**
- Chrome 90+ (primary)
- Firefox 88+
- Safari 14+
- Edge 90+

**Mobile Browsers:**
- iOS Safari 14+
- Chrome Mobile (Android & iOS)
- Samsung Internet
- Firefox Mobile

**Requirements:**
- Responsive design that adapts to screen sizes from 320px to 4K displays
- Touch-friendly interface for mobile browsers
- Keyboard navigation support for desktop
- Progressive Web App (PWA) capabilities for "add to home screen"

**Acceptance Criteria:**
- [ ] Works on all specified browsers
- [ ] No critical layout breaks on any screen size
- [ ] Touch gestures work on mobile browsers
- [ ] Keyboard shortcuts work on desktop
- [ ] Can be installed as PWA

---

#### 4.1.2 Responsive Design Breakpoints
**Priority:** P0 (Must Have)

**Breakpoints:**
- Mobile: 320px - 767px (portrait phones)
- Tablet: 768px - 1023px (tablets, landscape phones)
- Desktop: 1024px+ (laptops, desktops)

**Layout Adaptations:**

**Mobile (320-767px):**
- Single column layout
- Bottom navigation bar (sticky)
- Full-width album art
- Stacked content
- Hamburger menu for secondary nav
- Swipe gestures for calendar navigation

**Tablet (768-1023px):**
- Two-column layout where appropriate
- Side navigation visible
- Larger album art and touch targets
- Grid layouts for calendar

**Desktop (1024px+):**
- Multi-column layouts
- Persistent sidebar navigation
- Hover states on all interactive elements
- Larger content cards
- Mouse-optimized interactions

**Acceptance Criteria:**
- [ ] Seamless experience at all breakpoints
- [ ] No horizontal scrolling on any device
- [ ] Touch targets at least 44x44px on mobile
- [ ] Readable text at all sizes (min 14px on mobile)
- [ ] Images load appropriately sized for viewport

---

#### 4.1.3 Progressive Web App (PWA) Features
**Priority:** P1 (Should Have)

**Requirements:**
- Service worker for offline capability
- Web app manifest for "add to home screen"
- App icon and splash screens
- Push notification support (via service worker)
- Offline mode shows cached content
- Background sync for tracking data

**Benefits:**
- Users can "install" to home screen (feels like native app)
- Push notifications work on supported browsers
- Faster load times with caching
- Works offline (view cached calendar, etc.)

**Acceptance Criteria:**
- [ ] PWA installable on iOS Safari and Chrome
- [ ] Service worker caches critical assets
- [ ] Push notifications work on desktop Chrome/Firefox
- [ ] Offline mode gracefully handles no connection
- [ ] Install prompt appears appropriately

---

### 4.2 Technical Architecture

#### 4.2.1 Frontend Stack
**Priority:** P0 (Must Have)

**Framework:** React 18+
- Component-based architecture
- Hooks for state management
- React Router for navigation
- Context API for global state

**Styling:** Tailwind CSS + CSS Modules
- Utility-first for rapid development
- Custom design system
- Dark mode support
- Responsive utilities

**State Management:**
- React Context for global state (user, auth)
- React Query for server state
- Local storage for persistence

**Additional Libraries:**
- Framer Motion (animations)
- Day.js (date handling)
- React Hook Form (forms)
- Axios (HTTP client)
- Socket.io-client (real-time updates)

**Acceptance Criteria:**
- [ ] Fast initial load (<3 seconds)
- [ ] Smooth animations (60fps)
- [ ] No memory leaks
- [ ] Efficient re-renders

---

#### 4.2.2 Backend Stack
**Priority:** P0 (Must Have)

**Runtime:** Node.js + Express
- RESTful API endpoints
- WebSocket support for real-time
- JWT authentication
- Rate limiting

**Database:** PostgreSQL
- User data
- Song history
- Social connections
- Relational data integrity

**Caching:** Redis (Upstash Redis Free Tier: 10K commands/day or Redis Cloud 30MB free)
- Session storage
- API response caching
- Real-time data

**File Storage:** Cloudflare R2 (10GB free) or Supabase Storage (1GB free)
- Profile pictures
- Cached album art
- Alternative: Store external URLs only (no storage cost)

**Background Jobs:** Bull Queue or node-cron (both free, open source)
- Scheduled 9:30pm notifications
- Stats calculations
- Weekly recaps
- Backend polling for Spotify API (every 30-60 min)

**Hosting:**
- Frontend: Vercel Free Tier or Netlify Free Tier
- Backend: Render.com Free Tier or Fly.io (3 VMs free)
- Database: Neon Serverless Postgres (Free) or Supabase Free Tier
- CDN: Cloudflare Free Tier

**Acceptance Criteria:**
- [ ] API response times <200ms
- [ ] 99.9% uptime
- [ ] Handles 1000+ concurrent users
- [ ] Secure data transmission (HTTPS)

---

#### 4.2.3 Real-Time Features
**Priority:** P0 (Must Have)

**WebSocket Implementation:**
- Real-time feed updates when friends post
- Live reaction animations
- Instant comment notifications
- Presence indicators (who's online)

**Use Cases:**
- Friend posts song of the day → Appears in your feed immediately
- Friend reacts to your song → See reaction appear in real-time
- New comment → Notification badge updates instantly

**Fallback:**
- Polling every 30 seconds if WebSocket unavailable
- Graceful degradation

**Acceptance Criteria:**
- [ ] Real-time updates within 1 second
- [ ] Connection recovery on network interruption
- [ ] Minimal battery drain on mobile browsers
- [ ] Fallback works seamlessly

---

## 5. Core Features & Requirements

### 5.1 Spotify Integration & Tracking

#### 5.1.1 Spotify Web Authentication
**Priority:** P0 (Must Have)

**Requirements:**
- OAuth 2.0 flow with Spotify
- Authorization Code Flow with PKCE (more secure for web)
- Request scopes:
  - `user-read-currently-playing`
  - `user-read-recently-played`
  - `user-top-read`
  - `user-modify-playback-state` (for queue feature)
- Store tokens securely (httpOnly cookies)
- Automatic token refresh
- Handle authorization errors

**User Flow:**
1. User clicks "Connect Spotify"
2. Redirected to Spotify authorization page
3. User authorizes Replay
4. Redirected back to app with auth code
5. Backend exchanges code for tokens
6. Tokens stored securely
7. User sees success confirmation

**Web-Specific Considerations:**
- Handle redirect URLs properly
- Clear error messages in browser
- Work across different domains (dev, staging, prod)
- Session persistence across browser tabs

**Acceptance Criteria:**
- [ ] OAuth flow completes successfully
- [ ] Tokens stored securely (not accessible via JS)
- [ ] Token refresh happens automatically
- [ ] Works on all supported browsers
- [ ] Clear error messages for auth failures

---

#### 5.1.2 Passive Listening Tracking
**Priority:** P0 (Must Have)

**Requirements:**
- Poll Spotify API periodically throughout the day
- Track from first user interaction until 9:30pm
- Record:
  - Song name, artist, album, Spotify ID
  - Timestamp of play
  - Duration listened
  - Album art URL
- Store in database with user ID
- **Dual-tracking system: Backend polling + Client-side tracking**

**Polling Strategy (Backend - Primary):**
- **Backend server polls every 30-60 minutes** for all active users
- Uses Spotify's `recently-played` endpoint (returns last 50 tracks)
- Adaptive polling frequency based on user listening volume:
  - Heavy listeners (>20 songs/hour): Poll every 30 minutes
  - Moderate listeners (10-20 songs/hour): Poll every 60 minutes
  - Light listeners (<10 songs/hour): Poll every 120 minutes
- Deduplication using `played_at` timestamps to avoid storing duplicates
- **Critical: Solves Spotify's 50-item API limit by polling before data falls out of window**

**Polling Strategy (Client-side - Supplementary):**
- When user has app/tab open:
  - Active tab: Poll every 2 minutes
  - Inactive tab: Poll every 15 minutes
- Syncs with backend to fill gaps
- Provides real-time updates when app is open

**Web-Specific Challenges:**
- Page Visibility API to detect tab visibility
- Service Worker for background sync (PWA)
- Local Storage for temporary data before sync
- Handle browser being closed (backend polling continues)
- Gap detection: Flag if timestamp gap > polling window (potential data loss)

**Logic:**
- Count plays: A "play" = listening to >30 seconds
- Handle repeats: Same song multiple times = multiple plays
- Handle partial plays: <30 seconds = don't count
- Daily reset at 9:30pm

**Acceptance Criteria:**
- [ ] Backend polling captures 95%+ of all plays (no 50-item limit loss)
- [ ] Accurately tracks songs even when browser is closed
- [ ] Adaptive polling adjusts based on user listening patterns
- [ ] Deduplication prevents duplicate entries
- [ ] Data syncs to server regularly from both backend and client
- [ ] Minimal battery/CPU usage on client-side
- [ ] Handles browser close/reopen gracefully
- [ ] Gap detection alerts if potential data loss detected

---

#### 5.1.3 Song of the Day Calculation
**Priority:** P0 (Must Have)

**Requirements:**
- Backend job runs at 9:30pm user's local time
- Calculate most-played song for the day
- Algorithm:
  1. Count total plays for each unique song
  2. If tie, use total time listened as tiebreaker
  3. If still tied, use most recently played
- Store result with metadata
- Trigger notification/alert

**Backend Implementation:**
- Scheduled jobs for each timezone
- Bull Queue for job scheduling
- Store results immediately
- Trigger WebSocket event to connected clients

**Edge Cases:**
- No songs played → "No song of the day" empty state
- Only 1 song played → That's the song
- User plays songs after 9:30pm → Count toward next day

**Acceptance Criteria:**
- [ ] Correct song calculated at exactly 9:30pm
- [ ] Works across all timezones
- [ ] Results stored permanently
- [ ] Triggers notification system
- [ ] Handles edge cases properly

---

### 5.2 Daily Reveal & Notifications

#### 5.2.1 Web Notifications
**Priority:** P0 (Must Have)

**Requirements:**
- Browser push notifications (via service worker)
- Request permission during onboarding
- Daily notification at 9:30pm
- Notification content:
  - Title: "Your song of the day is ready! 🎵"
  - Body: "[Song Name] by [Artist]"
  - Icon: App logo
  - Badge: Album art thumbnail
- Click notification → Opens web app to reveal screen

**Web Notification Challenges:**
- Not all browsers support notifications (fallback: in-app alert)
- iOS Safari has limited notification support
- Need service worker for push notifications
- User must grant permission

**Supported Platforms:**
- ✅ Desktop: Chrome, Firefox, Edge, Safari
- ✅ Android: Chrome, Firefox
- ⚠️ iOS Safari: Limited (requires PWA installed)

**Fallback Strategy:**
- If notifications not supported/denied: In-app notification badge
- Email notification option (via **Resend** - 3K emails/month free or **Brevo** - 300 emails/day free)
- Browser tab title update ("🎵 Song ready!")

**User Settings:**
- Enable/disable browser notifications
- Enable/disable email notifications
- Custom notification time
- Notification sound preference (if supported)

**Acceptance Criteria:**
- [ ] Notifications send at correct time
- [ ] Clicking opens app to reveal screen
- [ ] Works across timezones
- [ ] Fallbacks work on unsupported browsers
- [ ] User can manage preferences

---

#### 5.2.2 Reveal Screen
**Priority:** P0 (Must Have)

**Requirements:**
- Full-screen experience (on mobile, fills viewport)
- Displays:
  - Large album art (responsive sizing)
  - Song name (bold, prominent)
  - Artist name
  - Total plays today
  - Total listening time
  - "Share" button
  - "Add to Queue" button
- Smooth animations on load
- Responsive design for mobile and desktop

**Mobile Design (320-767px):**
- Full-screen album art
- Text overlay at bottom
- Swipe up to see more details
- Large touch-friendly buttons

**Desktop Design (1024px+):**
- Centered layout with max-width
- Album art on left, info on right
- Hover effects on buttons
- Keyboard shortcuts (Space = share, Q = queue)

**Animations:**
- Fade-in album art
- Gentle zoom effect
- Text slides up
- Confetti or sparkles on first reveal (celebratory)

**Acceptance Criteria:**
- [ ] Beautiful on all screen sizes
- [ ] Animations are smooth (60fps)
- [ ] All information displays correctly
- [ ] Share and queue features work
- [ ] Accessible (keyboard navigation, screen readers)

---

### 5.3 Calendar View (Personal Archive)

#### 5.3.1 Monthly Grid Calendar
**Priority:** P0 (Must Have)

**Requirements:**
- BeReal-style grid layout
- One month visible at a time
- Each day shows:
  - Album art (fills square)
  - Small play count badge
  - Hover effect (desktop) / Long-press (mobile)
- Navigate between months
- Current day highlighted
- Empty squares for no-data days
- Completely private (only visible to user)

**Responsive Design:**

**Mobile (320-767px):**
- 7 columns (tight spacing)
- Smaller squares (40-50px each)
- Swipe left/right between months
- Tap to open day detail
- Month/year selector at top

**Tablet (768-1023px):**
- 7 columns (comfortable spacing)
- Medium squares (60-80px each)
- Swipe or arrow navigation
- Tap to open day detail

**Desktop (1024px+):**
- 7 columns (spacious)
- Large squares (80-100px each)
- Arrow buttons or keyboard navigation
- Hover preview on squares
- Click to open day detail modal

**Performance:**
- Lazy load album art (only visible squares)
- Virtual scrolling for year view
- Image caching
- Optimize for 1000+ days of data

**Acceptance Criteria:**
- [ ] Grid displays correctly at all sizes
- [ ] Month navigation is smooth
- [ ] Album art loads efficiently
- [ ] Current day is highlighted
- [ ] Works with incomplete data (first month)

---

#### 5.3.2 Day Detail View
**Priority:** P1 (Should Have)

**Requirements:**
- Opens in modal/overlay on desktop
- Full-screen on mobile
- Displays:
  - Full album art
  - #1 song with play count and time
  - #2 and #3 songs (if available)
  - Total listening time for day
  - Optional: Add note/memory
  - Date header
- Navigate between days (arrows or swipe)
- Close button returns to calendar

**Mobile:**
- Full-screen overlay
- Swipe down to close
- Swipe left/right for prev/next day
- Bottom sheet for additional info

**Desktop:**
- Centered modal (max 800px width)
- ESC key to close
- Arrow keys for navigation
- Backdrop darkens background

**Acceptance Criteria:**
- [ ] All information displays correctly
- [ ] Navigation between days is smooth
- [ ] Notes save properly (if implemented)
- [ ] Modal/overlay is accessible
- [ ] Works on all devices

---

### 5.4 Social Features

#### 5.4.1 User Profiles
**Priority:** P0 (Must Have)

**Requirements:**
- Profile page displays:
  - Profile picture (uploaded or default avatar)
  - Username (unique, 3-20 characters)
  - Bio (optional, 150 characters max)
  - Join date
  - **Long-term stats:**
    - Top 3 tracks (with album art + play counts)
    - Top 3 artists (with artist images)
    - Top 3 genres (with colorful badges)
  - Today's song of the day (prominent card)
  - Last 7 days mini-calendar grid
  - Friend count
  - Settings button (own profile only)
- Privacy toggle: Private / Friends-only / Public
- Edit profile button (own profile only)

**Stats Calculation:**
- Pull from Spotify API `user-top-read`
- Time range: long_term or medium_term (user choice)
- Update weekly (cron job)
- Cache results for performance

**Responsive Design:**

**Mobile:**
- Vertical stack layout
- Profile pic at top center
- Stats in cards below
- Full-width elements
- Bottom navigation

**Desktop:**
- Header with profile info
- Stats in 3-column grid
- Today's song prominent on right
- Sidebar navigation

**Profile URL:**
- Format: `replay.app/u/username`
- Shareable link
- SEO optimized

**Acceptance Criteria:**
- [ ] All profile elements display correctly
- [ ] Stats accurately reflect Spotify data
- [ ] Privacy settings enforce properly
- [ ] Profile is viewable by others (per settings)
- [ ] User can edit their profile
- [ ] Responsive on all devices

---

#### 5.4.2 Friend System
**Priority:** P0 (Must Have)

**Requirements:**
- Search users by username
- Send friend requests
- Accept/decline requests
- Friends list page
- Unfriend option
- Friend suggestions (mutual friends)

**Friend Discovery:**
- Search bar with autocomplete
- "People you may know" section
- Import from contacts (optional, with permission)
- Shareable profile link for invites
- QR code for in-person adds (mobile)

**Friend Request Flow:**
1. User A searches for User B
2. Clicks "Add Friend"
3. Request sent
4. User B receives notification
5. User B accepts or declines
6. If accepted, both see each other's content

**Notifications:**
- Browser push notification
- In-app notification badge
- Optional: Email notification

**Friends List:**
- Searchable/filterable
- Alphabetical order
- Show online status (green dot if active)
- Last song posted preview
- Quick actions (view profile, message, unfriend)

**Acceptance Criteria:**
- [ ] Search works quickly and accurately
- [ ] Friend requests send properly
- [ ] Accept/decline works
- [ ] Friends list displays correctly
- [ ] Unfriend works with confirmation
- [ ] Notifications trigger appropriately

---

#### 5.4.3 Social Feed
**Priority:** P0 (Must Have)

**Requirements:**
- Main landing page after login
- Vertical scrolling feed
- Each post shows:
  - Friend's profile picture + username (linked)
  - "Song of the day" timestamp (e.g., "2h ago")
  - Large album art (square, responsive)
  - Song name + artist (linked to Spotify)
  - Play count for the day
  - BeReal-style reaction ring
  - Comment count
  - Action buttons (React, Comment, Add to Queue, Share)
- Posts appear at 9:30pm when friends reveal
- Infinite scroll (load more)
- Pull-to-refresh on mobile
- Real-time updates via WebSocket

**Feed Algorithm:**
- Reverse chronological (newest first)
- Optional: Boost friends you interact with most
- Show "You're all caught up!" when at end

**Responsive Design:**

**Mobile (320-767px):**
- Single column
- Full-width posts
- Album art fills width (square crop)
- Touch-friendly buttons
- Fixed bottom navigation

**Desktop (1024px+):**
- Centered feed (max 600px width)
- Sidebar with friend suggestions
- Right sidebar with trending songs
- Hover effects on all interactions
- Keyboard shortcuts

**Empty States:**
- No friends yet: Prompt to add friends
- Friends haven't posted: "Waiting for songs..."
- First time user: Tutorial overlay

**Acceptance Criteria:**
- [ ] Feed loads quickly (<1 second)
- [ ] Infinite scroll works smoothly
- [ ] Real-time updates appear instantly
- [ ] Posts display correctly on all devices
- [ ] Empty states are helpful

---

#### 5.4.4 BeReal-Style Reactions
**Priority:** P0 (Must Have)

**Requirements:**
- Click/tap reaction button on any post
- Modal/popover shows emoji options:
  - 🔥 Fire
  - ❤️ Heart
  - 💀 Skull
  - 😭 Crying
  - 🎯 Target
  - 👀 Eyes
  - 🤔 Thinking
  - 😍 Heart Eyes
- Select emoji → User's circular profile picture + emoji appears around album art
- Multiple reactions stack in ring around album art
- Click reaction ring → See all reactors in list
- Notification to post owner

**Visual Implementation:**
- Circular profile pictures (30x30px on mobile, 40x40px on desktop)
- Position in ring around album art
- Max ~12 visible in ring, then "+X more"
- Smooth animation when adding reaction
- Hover on desktop shows name tooltip

**Interaction:**
- One reaction per user per post
- Can change reaction (replaces previous)
- Click your own reaction to remove it

**Notification:**
- Real-time WebSocket event
- Push notification: "[Friend] reacted 🔥 to your song"
- In-app notification badge

**Responsive:**

**Mobile:**
- Bottom sheet for emoji picker
- Large touch targets (50x50px)
- Smooth slide-up animation

**Desktop:**
- Popover below album art
- Hover effects on emojis
- Keyboard shortcuts (1-8 for emojis)

**Acceptance Criteria:**
- [ ] Reaction UI matches BeReal aesthetic
- [ ] Profile pictures display in ring correctly
- [ ] Multiple reactions layer properly without overlap
- [ ] Animations are smooth
- [ ] Notifications trigger correctly
- [ ] Works on all devices/browsers

---

#### 5.4.5 Comments
**Priority:** P1 (Should Have)

**Requirements:**
- Click comment button on post
- Opens comment section (expands inline or modal)
- Text input (280 characters max)
- Display comments:
  - Profile picture + username
  - Comment text
  - Timestamp (e.g., "2h ago")
  - Like button (simple heart)
  - Delete button (own comments only)
- Real-time updates (WebSocket)
- Mention users with @username
- Notification to post owner

**Responsive Design:**

**Mobile:**
- Bottom sheet slides up
- Full-screen on smaller phones
- Keyboard pushes content up
- Swipe down to close

**Desktop:**
- Expands inline below post
- Fixed textarea at bottom
- Scrollable comment list
- ESC to close

**Features:**
- Auto-link @mentions
- Auto-link song titles
- Emoji picker for comments
- Character counter
- "Post" button disabled until text entered

**Acceptance Criteria:**
- [ ] Comments post and display correctly
- [ ] Real-time updates work
- [ ] Can delete own comments
- [ ] Character limit enforced
- [ ] Mentions work properly
- [ ] Accessible on all devices

---

#### 5.4.6 Quick Actions
**Priority:** P1 (Should Have)

**Requirements:**

**"Add to Queue" Feature:**
- Button on every post
- Adds song to user's Spotify queue
- Uses Spotify Web Playback SDK or API
- Requires Spotify Premium (free users see upgrade prompt)
- Success toast: "Added to your Spotify queue ✓"
- Error handling if Spotify not connected

**"Share" Feature:**
- Share button on posts
- Options:
  - Copy link to post
  - Share to Twitter (pre-filled text)
  - Share to Instagram (copies and opens app if mobile)
  - Download image (album art with text overlay)
- Include app attribution for viral growth

**Link Preview:**
- When sharing, generate rich Open Graph preview
- Shows album art, song name, friend's name
- "See what [Friend] is listening to on Replay"

**Acceptance Criteria:**
- [ ] Songs add to Spotify queue successfully
- [ ] Share options work on all platforms
- [ ] Link previews render correctly
- [ ] Error handling is graceful
- [ ] Share attribution drives installs

---

### 5.5 Privacy & Settings

#### 5.5.1 Privacy Controls
**Priority:** P0 (Must Have)

**Requirements:**
- Three privacy tiers:
  1. **Private:** Only user sees their data
  2. **Friends-only (default):** Friends see daily song + last 7 days + stats
  3. **Public:** Anyone can follow and see activity
- Toggle: "Share my daily song" (on/off)
- Full calendar is ALWAYS private
- Block/report users
- Control who can send friend requests

**What's Shared:**

| Feature | Private | Friends-only | Public |
|---------|---------|--------------|--------|
| Daily song | ❌ | ✅ | ✅ |
| Last 7 days | ❌ | ✅ | ✅ |
| Profile stats | ❌ | ✅ | ✅ |
| Full calendar | ❌ | ❌ | ❌ |
| Appear in search | ❌ | ✅ | ✅ |
| Receive friend requests | ❌ | ✅ | ✅ |

**Privacy Settings Page:**
- Clear explanations of each tier
- Visual diagram of what's shared
- Change anytime
- Confirmation modal when making public

**Acceptance Criteria:**
- [ ] Privacy settings enforce correctly
- [ ] Calendar remains private always
- [ ] Block/report works
- [ ] Clear UI explains implications
- [ ] Settings persist across sessions

---

#### 5.5.2 Settings Menu
**Priority:** P0 (Must Have)

**Requirements:**

**Account Settings:**
- Edit profile (picture, username, bio)
- Connected accounts (Spotify)
- Email preferences
- Privacy settings
- Blocked users
- Download my data
- Delete account

**App Settings:**
- Daily reveal time (default 9:30pm)
- Timezone (auto-detect)
- Stats time range (long-term vs medium-term)
- Theme (auto/dark/light)
- Language (future)
- Accessibility options

**Notification Settings:**
- Browser push notifications (on/off)
- Email notifications (on/off)
- Which events trigger notifications:
  - Daily song reveal
  - Friend requests
  - Reactions
  - Comments
  - Weekly recap
  - Music Twins

**Support & Legal:**
- Help Center / FAQ
- Contact Support
- Report a Bug
- Privacy Policy
- Terms of Service
- About Replay

**Acceptance Criteria:**
- [ ] All settings are functional
- [ ] Changes save immediately
- [ ] Delete account removes all data
- [ ] Support links work
- [ ] Legal pages accessible

---

### 5.6 Onboarding Flow

#### 5.6.1 First-Time User Experience
**Priority:** P0 (Must Have)

**Landing Page (Not logged in):**
- Hero section with compelling headline
- Animated preview of app (calendar scrolling, etc.)
- Social proof (user count, testimonials)
- "Get Started" CTA button
- "How it works" section (3 steps)
- Example profiles/feed
- FAQ section
- Footer (privacy, terms, contact)

**Onboarding Screens:**

**1. Welcome Modal**
- Logo + tagline
- "Track your music. Share with friends. Build your diary."
- "Sign up with Spotify" button
- "See how it works" button (optional tour)

**2. Spotify Authorization**
- Redirect to Spotify OAuth
- Clear explanation of permissions
- "Why we need this" tooltip
- Authorize → Return to app

**3. Create Profile (Single Page)**
- Choose username (real-time availability check)
- Upload profile picture (optional, drag-drop or click)
- Write bio (optional)
- Continue button

**4. Find Friends (Skippable)**
- Search by username
- Invite via link/email
- "Skip for now" button prominent
- Import from contacts (optional)

**5. Privacy Selection**
- Choose tier with visual explanation
- Default: Friends-only
- "You can change this later"
- Continue

**6. Notification Permission**
- Request browser notification permission
- Explain value ("Don't miss your 9:30pm reveal!")
- Allow / Maybe Later buttons

**7. Ready Screen**
- "You're all set! 🎉"
- "Start listening on Spotify..."
- "We'll reveal your first song at 9:30pm today"
- "Go to Feed" button (main app)

**Tour (Optional):**
- Interactive tooltips on first use
- Highlight: Feed, Calendar, Profile, Settings
- Dismissible, can skip
- "Got it" on each step

**Acceptance Criteria:**
- [ ] Onboarding is quick (<3 minutes)
- [ ] Can skip optional steps
- [ ] Clear explanations at each step
- [ ] Profile created successfully
- [ ] User lands in working app
- [ ] Works on mobile and desktop

---

### 5.7 Additional Features

#### 5.7.1 Weekly Recap
**Priority:** P1 (Should Have)

**Requirements:**
- Generated every Monday morning
- Displays:
  - Top 5 songs of the week
  - Total listening time
  - Genre breakdown (pie chart)
  - New artists discovered
  - "Week at a glance" (7 days of album art)
  - Comparison to last week
- Shareable graphic
- Browser notification on Monday
- Accessible from profile ("View Recaps")

**Shareable Format:**
- Downloadable image (1080x1920 for stories)
- Custom design with branding
- "Made with Replay" watermark

**Acceptance Criteria:**
- [ ] Recap generates every Monday
- [ ] All stats are accurate
- [ ] Shareable graphic looks great
- [ ] Notification triggers
- [ ] Accessible on all devices

---

#### 5.7.2 Music Twins
**Priority:** P2 (Nice to Have)

**Requirements:**
- Detect when user + friend have same song of the day
- Trigger notification: "You and [Friend] both had [Song] as your song of the day! 🎵"
- Badge on both posts: "Music Twin with [Friend]"
- Stats page showing:
  - Total Music Twin days with each friend
  - Songs you've both loved
  - "Most compatible friend" ranking

**Acceptance Criteria:**
- [ ] Correctly identifies matching songs
- [ ] Notifications sent to both users
- [ ] Badge appears on posts
- [ ] Stats track over time

---

#### 5.7.3 Friend Playlist (Auto-Generated)
**Priority:** P2 (Nice to Have)

**Requirements:**
- Weekly auto-generated Spotify playlist
- Contains friends' top songs from the week
- Playlist name: "Friends' Picks - [Week]"
- Created in user's Spotify account
- Viewable in app with embedded player
- Option to customize (remove songs, etc.)

**Acceptance Criteria:**
- [ ] Playlist creates in Spotify
- [ ] Contains correct songs
- [ ] Updates weekly
- [ ] User can disable feature

---

#### 5.7.4 Explore Page (Public Accounts)
**Priority:** P2 (Nice to Have)

**Requirements:**
- Discover tab in main navigation
- Sections:
  - **Trending:** Most common songs today (public users)
  - **Genres:** Browse by genre tag
  - **Rising:** New users with interesting taste
  - **Unique Picks:** Songs only 1-2 people played
- Follow public accounts
- View public profiles
- Search public users

**Acceptance Criteria:**
- [ ] Explore page loads quickly
- [ ] Trending data is accurate
- [ ] Can follow/unfollow
- [ ] Only public accounts visible
- [ ] Search works well

---

## 6. User Flows

### 6.1 Core User Flow (Daily Usage)

```
1. User listens to Spotify throughout the day (on any device)
   ↓
2. Replay tracks in background (web app open in browser tab)
   ↓
3. 9:30pm - Browser notification received (or in-app alert)
   ↓
4. User clicks notification
   ↓
5. Browser tab opens/focuses to Reveal Screen
   - Album art animation
   - Song of the day + stats displayed
   ↓
6. User clicks "Go to Feed" or nav to Feed
   ↓
7. Scrolls through friends' songs (vertical feed)
   ↓
8. Reacts to 2-3 friends' songs (click emoji, face appears)
   ↓
9. Clicks "Add to Queue" on one song
   - Song added to Spotify
   ↓
10. Leaves comment on another song
   ↓
11. Navigates to Profile to see updated stats
   ↓
12. (Optional) Opens Calendar to browse past months
   ↓
13. Closes browser tab or keeps open in background
```

**Time spent:** 2-4 minutes per session  
**Devices:** Can start on mobile, continue on desktop seamlessly

---

### 6.2 Onboarding Flow

```
1. User visits replay.app (landing page)
   ↓
2. Clicks "Get Started"
   ↓
3. Modal opens: "Sign up with Spotify"
   ↓
4. Redirected to Spotify OAuth page
   ↓
5. Authorizes Replay
   ↓
6. Returns to app → Create Profile page
   - Enter username (check availability)
   - Upload photo (optional)
   - Add bio (optional)
   ↓
7. Find Friends page (skippable)
   - Search by username
   - Or click "Skip for now"
   ↓
8. Choose Privacy Level
   - Defaults to Friends-only
   - Explanation shown
   ↓
9. Request notification permission
   - "Allow" or "Maybe later"
   ↓
10. "You're all set!" screen
   ↓
11. Click "Go to Feed" → Main app loads
    - If no friends: Empty state with "Add friends" prompt
    - If has friends: See their recent posts
```

**Time spent:** 2-3 minutes  
**Works on:** Mobile or desktop browsers

---

### 6.3 Cross-Device Experience

```
SCENARIO: User at work (desktop) → Later on phone (mobile)

Morning (Desktop - 10am):
1. Opens replay.app on work computer
2. Checks friend feed from yesterday
3. Leaves a few comments
4. Keeps tab open in background while listening to Spotify

Afternoon (Mobile - 2pm):
5. Opens replay.app on phone browser (or PWA)
6. Automatically logged in (session synced)
7. Sees same data, up to date
8. Continues listening to Spotify on phone
9. Tracking continues seamlessly

Evening (Mobile - 9:30pm):
10. Receives push notification on phone
11. Opens app to see song of the day
12. Shares to Instagram story
13. Reacts to friends' songs

Night (Desktop - 11pm):
14. Opens laptop, replay.app still open
15. Sees updated feed with evening posts
16. Browses calendar for nostalgia
```

**Key Point:** Seamless sync across devices

---

## 7. Technical Requirements

### 7.1 Frontend Technical Specs

#### 7.1.1 Performance Requirements
**Priority:** P0 (Must Have)

**Load Times:**
- Initial page load: <3 seconds (3G connection)
- Time to interactive: <5 seconds
- Feed infinite scroll: New items <1 second
- Navigation between pages: <500ms (instant feel)
- Image loading: <500ms per image

**Optimization:**
- Code splitting (React lazy loading)
- Image optimization (WebP with fallback)
- Lazy loading for below-fold content
- Minified CSS/JS bundles
- CDN for static assets
- Service worker caching

**Bundle Size:**
- Initial JS bundle: <200KB (gzipped)
- CSS bundle: <50KB (gzipped)
- Total page weight: <1MB initial load

**Acceptance Criteria:**
- [ ] Lighthouse score >90 (Performance)
- [ ] Core Web Vitals pass (LCP, FID, CLS)
- [ ] Works smoothly on 3G connection
- [ ] No layout shifts on load

---

#### 7.1.2 Browser Compatibility
**Priority:** P0 (Must Have)

**Required Support:**
- Chrome 90+ ✅
- Firefox 88+ ✅
- Safari 14+ ✅
- Edge 90+ ✅
- Chrome Mobile (Android/iOS) ✅
- Safari iOS 14+ ✅

**Feature Detection:**
- Check for WebSocket support
- Check for notification API
- Check for service worker support
- Graceful degradation if not supported

**Polyfills:**
- IntersectionObserver (for infinite scroll)
- Fetch API (older browsers)
- CSS Grid (IE11 if needed - though not primary target)

**Testing:**
- BrowserStack for cross-browser testing
- Real device testing (iOS, Android)
- Automated testing suite

**Acceptance Criteria:**
- [ ] Core features work on all listed browsers
- [ ] No critical bugs on any browser
- [ ] Graceful degradation where needed
- [ ] Touch works on mobile browsers

---

#### 7.1.3 Responsive Design System
**Priority:** P0 (Must Have)

**Design Tokens:**
```css
/* Spacing */
--spacing-xs: 4px
--spacing-sm: 8px
--spacing-md: 16px
--spacing-lg: 24px
--spacing-xl: 32px
--spacing-2xl: 48px

/* Typography */
--font-size-xs: 12px
--font-size-sm: 14px
--font-size-base: 16px
--font-size-lg: 18px
--font-size-xl: 24px
--font-size-2xl: 32px

/* Colors (Dark Mode Default) */
--bg-primary: #0A0A0A
--bg-secondary: #1A1A1A
--bg-tertiary: #2A2A2A
--text-primary: #FFFFFF
--text-secondary: rgba(255,255,255,0.7)
--accent-primary: #1DB954 (Spotify Green)
--accent-secondary: #8B5CF6 (Purple)

/* Border Radius */
--radius-sm: 4px
--radius-md: 8px
--radius-lg: 12px
--radius-full: 9999px
```

**Component Library:**
- Button (primary, secondary, ghost)
- Card (elevated, flat, interactive)
- Input (text, search, textarea)
- Modal (centered, bottom-sheet)
- Navigation (top, bottom, sidebar)
- Album Art (small, medium, large, hero)
- Profile Picture (xs, sm, md, lg)

**Acceptance Criteria:**
- [ ] Consistent design across all pages
- [ ] Components reusable
- [ ] Accessible (ARIA labels, keyboard nav)
- [ ] Dark mode looks great

---

### 7.2 Backend Technical Specs

#### 7.2.1 API Architecture
**Priority:** P0 (Must Have)

**RESTful Endpoints:**

**Authentication:**
- `POST /auth/spotify` - Initiate Spotify OAuth
- `GET /auth/callback` - Handle OAuth callback
- `POST /auth/refresh` - Refresh tokens
- `POST /auth/logout` - Logout user

**Users:**
- `GET /users/me` - Get current user
- `PUT /users/me` - Update profile
- `GET /users/:username` - Get user profile
- `DELETE /users/me` - Delete account

**Tracking:**
- `POST /tracking/sync` - Sync listening data from client
- `GET /tracking/today` - Get today's listening data
- `GET /tracking/history` - Get historical data

**Social:**
- `GET /feed` - Get friend feed
- `POST /friends/request` - Send friend request
- `POST /friends/accept` - Accept request
- `DELETE /friends/:id` - Remove friend
- `GET /friends` - Get friends list

**Reactions:**
- `POST /posts/:id/react` - Add reaction
- `DELETE /posts/:id/react` - Remove reaction
- `GET /posts/:id/reactions` - Get all reactions

**Comments:**
- `POST /posts/:id/comments` - Add comment
- `GET /posts/:id/comments` - Get comments
- `DELETE /comments/:id` - Delete comment

**Stats:**
- `GET /stats/me` - Get personal stats
- `GET /stats/weekly` - Get weekly recap

**Rate Limiting:**
- 100 requests per minute per user
- 1000 requests per hour per user
- Stricter limits on expensive operations

**Acceptance Criteria:**
- [ ] All endpoints documented (OpenAPI/Swagger)
- [ ] Response times <200ms (p95)
- [ ] Proper error codes (400, 401, 403, 404, 500)
- [ ] Rate limiting enforced
- [ ] CORS configured correctly

---

#### 7.2.2 Database Schema
**Priority:** P0 (Must Have)

**PostgreSQL Tables:**

**users**
```sql
id: UUID (PK)
username: VARCHAR(20) UNIQUE
email: VARCHAR(255) UNIQUE
spotify_id: VARCHAR(255) UNIQUE
profile_picture_url: TEXT
bio: VARCHAR(150)
privacy_level: ENUM('private', 'friends', 'public')
timezone: VARCHAR(50)
notification_time: TIME (default '21:30')
created_at: TIMESTAMP
updated_at: TIMESTAMP
```

**spotify_tokens**
```sql
id: UUID (PK)
user_id: UUID (FK → users)
access_token: TEXT (encrypted)
refresh_token: TEXT (encrypted)
expires_at: TIMESTAMP
created_at: TIMESTAMP
updated_at: TIMESTAMP
```

**listening_history**
```sql
id: UUID (PK)
user_id: UUID (FK → users)
spotify_track_id: VARCHAR(50)
track_name: VARCHAR(255)
artist_name: VARCHAR(255)
album_name: VARCHAR(255)
album_art_url: TEXT
played_at: TIMESTAMP
duration_ms: INTEGER
date: DATE (indexed)
created_at: TIMESTAMP
```

**daily_songs**
```sql
id: UUID (PK)
user_id: UUID (FK → users)
date: DATE
spotify_track_id: VARCHAR(50)
track_name: VARCHAR(255)
artist_name: VARCHAR(255)
album_art_url: TEXT
play_count: INTEGER
total_duration_ms: INTEGER
created_at: TIMESTAMP
UNIQUE(user_id, date)
```

**friendships**
```sql
id: UUID (PK)
user_id: UUID (FK → users)
friend_id: UUID (FK → users)
status: ENUM('pending', 'accepted', 'blocked')
created_at: TIMESTAMP
updated_at: TIMESTAMP
UNIQUE(user_id, friend_id)
```

**reactions**
```sql
id: UUID (PK)
daily_song_id: UUID (FK → daily_songs)
user_id: UUID (FK → users)
emoji: VARCHAR(10)
created_at: TIMESTAMP
UNIQUE(daily_song_id, user_id)
```

**comments**
```sql
id: UUID (PK)
daily_song_id: UUID (FK → daily_songs)
user_id: UUID (FK → users)
content: TEXT
likes_count: INTEGER (default 0)
created_at: TIMESTAMP
updated_at: TIMESTAMP
```

**Indexes:**
- `listening_history.user_id, date`
- `daily_songs.user_id, date`
- `friendships.user_id, status`
- `reactions.daily_song_id`
- `comments.daily_song_id`

**Acceptance Criteria:**
- [ ] Schema supports all features
- [ ] Proper foreign keys and constraints
- [ ] Indexes optimize common queries
- [ ] Migrations versioned and tracked

---

#### 7.2.3 Real-Time Infrastructure
**Priority:** P0 (Must Have)

**WebSocket Server:**
- Socket.io for WebSocket connections
- Rooms per user for targeted events
- Authentication via JWT

**Events:**
- `feed:new_post` - Friend posted new song
- `reaction:added` - Someone reacted to your song
- `comment:added` - Someone commented
- `friend:request` - New friend request
- `friend:accepted` - Friend request accepted
- `music_twin:detected` - Music Twin with friend

**Connection Management:**
- Reconnection logic on client
- Heartbeat to keep connection alive
- Graceful fallback to polling

**Scalability:**
- Redis adapter for multi-server Socket.io
- Horizontal scaling of WebSocket servers
- Load balancing

**Acceptance Criteria:**
- [ ] Real-time events <1 second latency
- [ ] Handles 1000+ concurrent connections
- [ ] Reconnection works seamlessly
- [ ] Events only sent to relevant users

---

### 7.3 Third-Party Integrations

#### 7.3.1 Spotify Web API
**Priority:** P0 (Must Have)

**Endpoints Used:**
- `GET /me/player/currently-playing`
- `GET /me/player/recently-played`
- `GET /me/top/tracks`
- `GET /me/top/artists`
- `POST /me/player/queue`

**Authentication:**
- OAuth 2.0 Authorization Code with PKCE
- Scopes: `user-read-currently-playing`, `user-read-recently-played`, `user-top-read`, `user-modify-playback-state`
- Token refresh every 50 minutes

**Rate Limiting:**
- Respect Spotify's rate limits
- Implement exponential backoff
- Cache responses where appropriate

**Error Handling:**
- 429 (Rate limit) → Wait and retry
- 401 (Unauthorized) → Refresh token
- 403 (Forbidden) → Prompt user to reconnect
- 500 (Server error) → Retry with backoff

**Acceptance Criteria:**
- [ ] OAuth flow works perfectly
- [ ] Token refresh is automatic
- [ ] Rate limits respected
- [ ] Error handling is robust

---

#### 7.3.2 Web Push Notifications
**Priority:** P0 (Must Have)

**Service:**
- Web Push Protocol (standard, 100% free)
- VAPID keys for identification
- Service worker handles push events

**Implementation:**
- Request permission during onboarding
- Store subscription in database
- Send via **Firebase Cloud Messaging** (completely free) or native Web Push API

**Notification Types:**
- Daily song reveal (9:30pm)
- Friend request
- Reaction to your song
- Comment on your song
- Weekly recap
- Music Twin detected

**Browser Support:**
- ✅ Chrome, Firefox, Edge (desktop + Android)
- ⚠️ Safari (limited, requires PWA installed)
- ❌ iOS Safari (very limited)

**Fallback:**
- Email notifications for iOS users (via Resend or Brevo free tier)
- In-app notification center

**Acceptance Criteria:**
- [ ] Notifications send reliably
- [ ] Clicking opens correct page
- [ ] User can manage preferences
- [ ] Works across supported browsers

---

### 7.4 Security Requirements

#### 7.4.1 Authentication & Authorization
**Priority:** P0 (Must Have)

**Authentication:**
- JWT tokens (httpOnly cookies)
- Refresh token rotation
- Session management
- CSRF protection

**Authorization:**
- Role-based access (user, admin)
- Privacy level enforcement
- Friend-only content gated properly

**Password Security:**
- N/A (OAuth only, no passwords stored)

**Token Security:**
- Spotify tokens encrypted at rest
- Short-lived access tokens (1 hour)
- Refresh tokens expire after 30 days

**Acceptance Criteria:**
- [ ] Secure authentication flow
- [ ] Tokens stored securely
- [ ] Privacy enforced correctly
- [ ] CSRF protection active

---

#### 7.4.2 Data Privacy & Compliance
**Priority:** P0 (Must Have)

**GDPR Compliance:**
- Clear consent during onboarding
- Data export feature
- Right to be forgotten (account deletion)
- Privacy policy and terms

**CCPA Compliance:**
- Do not sell personal information
- Opt-out mechanisms
- Data disclosure

**Data Minimization:**
- Only collect necessary data
- Retain listening history only as needed
- Delete inactive accounts after 2 years

**User Rights:**
- Export all data (JSON format)
- Delete account (permanent)
- Revoke Spotify access
- Change privacy settings anytime

**Acceptance Criteria:**
- [ ] GDPR/CCPA compliant
- [ ] Data export works
- [ ] Account deletion removes all data
- [ ] Privacy policy clear and accessible

---

#### 7.4.3 API Security
**Priority:** P0 (Must Have)

**HTTPS Only:**
- Force HTTPS on all connections
- TLS 1.3
- HSTS headers

**Rate Limiting:**
- Per-user limits
- Per-IP limits
- Exponential backoff

**Input Validation:**
- Sanitize all inputs
- Parameterized SQL queries (prevent injection)
- XSS protection

**Security Headers:**
- Content-Security-Policy
- X-Frame-Options
- X-Content-Type-Options
- Referrer-Policy

**Monitoring:**
- Log suspicious activity
- Alert on repeated failed auth
- Track API abuse

**Acceptance Criteria:**
- [ ] All connections encrypted
- [ ] Rate limiting enforced
- [ ] No SQL injection vulnerabilities
- [ ] Security headers configured

---

## 8. Design Requirements

### 8.1 Design Principles
1. **Music-first:** Album art is always the hero element
2. **Clean & minimal:** Avoid UI clutter, let content shine
3. **Dark by default:** Optimized for music app aesthetic
4. **Responsive:** Perfect experience on mobile and desktop
5. **Smooth & delightful:** Every interaction should feel polished
6. **Social but tasteful:** BeReal's casual vibe, not Instagram's perfection
7. **Fast:** No waiting, instant feedback

### 8.2 Visual Style

**Color Palette (Dark Mode Default):**
```css
Background:
- Primary: #0A0A0A (near black)
- Secondary: #1A1A1A (cards)
- Tertiary: #2A2A2A (hover states)

Text:
- Primary: #FFFFFF (white)
- Secondary: rgba(255,255,255,0.7) (muted)
- Tertiary: rgba(255,255,255,0.5) (disabled)

Accent:
- Primary: #1DB954 (Spotify green)
- Secondary: #8B5CF6 (purple gradient)
- Success: #10B981
- Error: #EF4444
- Warning: #F59E0B

Borders:
- Default: rgba(255,255,255,0.1)
- Hover: rgba(255,255,255,0.2)
```

**Light Mode (Optional Future):**
- Inverted color scheme
- User preference toggle

**Typography:**
- Font Family: Inter, -apple-system, system-ui
- Headings: 600-700 weight
- Body: 400-500 weight
- Line Height: 1.5 (body), 1.2 (headings)

**Imagery:**
- Album art: Always square, 12px border radius
- Profile pictures: Circular
- Shadows: Subtle, soft (0 4px 12px rgba(0,0,0,0.3))
- Gradients: Used sparingly for accents

---

### 8.3 Responsive Layout Specifications

#### Mobile (320-767px)
**Navigation:**
- Bottom tab bar (sticky)
- Icons: Feed, Calendar, Profile
- Active tab highlighted
- Swipe between tabs (optional)

**Feed:**
- Full-width posts
- Vertical scroll
- Pull-to-refresh
- Infinite scroll

**Calendar:**
- 7-column grid
- Smaller squares (40-50px)
- Swipe between months
- Tap to open detail

**Profile:**
- Vertical stack
- Full-width cards
- Stats in single column

---

#### Tablet (768-1023px)
**Navigation:**
- Side navigation bar
- Icons + labels
- Collapsible on smaller tablets

**Feed:**
- Centered content (max 600px width)
- Margins on sides
- Larger album art

**Calendar:**
- Larger grid squares (60-80px)
- More comfortable spacing

---

#### Desktop (1024px+)
**Layout:**
- Three-column when appropriate:
  - Left: Navigation sidebar
  - Center: Main content (feed, calendar, etc.)
  - Right: Suggestions, trending, etc.

**Navigation:**
- Persistent sidebar
- Icons + labels
- Hover effects

**Feed:**
- Centered (max 600px)
- Hover effects on all interactions
- Keyboard shortcuts
- Smooth transitions

**Calendar:**
- Large grid (80-100px squares)
- Hover preview
- Keyboard navigation

---

### 8.4 Interaction Design

**Animations:**
- Duration: 200-300ms
- Easing: ease-in-out
- Purposeful, not gratuitous
- Reduced motion support (respect OS setting)

**Hover States (Desktop):**
- Subtle color change
- Slight scale (1.02)
- Shadow increase
- Cursor change

**Touch Feedback (Mobile):**
- Haptic feedback (if available in browser)
- Visual feedback (button press effect)
- Ripple effect on tap

**Loading States:**
- Skeleton screens (not spinners)
- Progressive loading
- Optimistic updates

**Gestures:**
- Swipe left/right: Navigate months (calendar)
- Pull down: Refresh feed
- Long press: Context menu (mobile)
- Pinch: N/A (no zoom needed)

**Keyboard Shortcuts (Desktop):**
- `?` - Show shortcuts
- `N` - Compose new post (future)
- `F` - Go to feed
- `C` - Go to calendar
- `P` - Go to profile
- `←/→` - Navigate in calendar
- `ESC` - Close modals

---

### 8.5 Component Specifications

#### Album Art Display
**Sizes:**
- Thumbnail: 40x40px (in lists)
- Small: 80x80px (calendar squares)
- Medium: 200x200px (feed posts on mobile)
- Large: 400x400px (feed posts on desktop)
- Hero: Full-width responsive (reveal screen)

**Style:**
- Always square (1:1 aspect ratio)
- Border radius: 12px
- Shadow on hover/focus
- Lazy loading
- Fallback: Gradient placeholder

---

#### Profile Picture
**Sizes:**
- XS: 24x24px (inline mentions)
- SM: 32x32px (comments, small reactions)
- MD: 48x48px (posts, friend lists)
- LG: 80x80px (profile headers)
- XL: 120x120px (own profile page)

**Style:**
- Always circular
- Border: 2px solid background color
- Fallback: Initials on gradient background

---

#### Buttons
**Primary:**
- Background: Accent gradient
- Text: White
- Border radius: 8px
- Padding: 12px 24px
- Hover: Slight brighten

**Secondary:**
- Background: Transparent
- Border: 1px solid border color
- Text: Primary text color
- Hover: Border brightens

**Ghost:**
- Background: Transparent
- No border
- Text: Secondary text color
- Hover: Text brightens

---

## 9. Non-Functional Requirements

### 9.1 Accessibility
**Priority:** P0 (Must Have)

**WCAG 2.1 AA Compliance:**
- Color contrast ratios: 4.5:1 (text), 3:1 (large text)
- Keyboard navigation for all features
- Screen reader support (ARIA labels)
- Focus indicators clearly visible
- Alt text for all images
- Skip navigation links

**Features:**
- VoiceOver (iOS) support
- NVDA/JAWS (desktop) support
- Keyboard-only navigation
- Adjustable text size
- High contrast mode
- Reduced motion mode

**Testing:**
- Automated testing (axe, Lighthouse)
- Manual screen reader testing
- Keyboard-only testing
- User testing with disabilities

**Acceptance Criteria:**
- [ ] WCAG 2.1 AA compliant
- [ ] Lighthouse accessibility score >90
- [ ] Keyboard navigation works everywhere
- [ ] Screen reader friendly

---

### 9.2 Performance Targets

**Load Times:**
- First Contentful Paint (FCP): <1.5s
- Largest Contentful Paint (LCP): <2.5s
- Time to Interactive (TTI): <3.5s
- First Input Delay (FID): <100ms
- Cumulative Layout Shift (CLS): <0.1

**Runtime Performance:**
- 60fps scrolling
- <50ms response to interactions
- Efficient memory usage (<100MB)

**Network:**
- Works on 3G (slow 3G degrades gracefully)
- Offline mode for cached content
- Background sync when online

**Acceptance Criteria:**
- [ ] Core Web Vitals: All green
- [ ] Lighthouse Performance score >90
- [ ] Works smoothly on slow connections

---

### 9.3 SEO Requirements
**Priority:** P1 (Should Have)

**Meta Tags:**
- Unique title and description per page
- Open Graph tags (for social sharing)
- Twitter Card tags
- Canonical URLs
- Structured data (JSON-LD)

**Dynamic SEO:**
- Server-side rendering (SSR) for public pages
- Dynamic meta tags based on content
- Sitemap.xml
- Robots.txt

**URLs:**
- Clean, readable URLs
- Format: `/u/[username]`, `/feed`, `/explore`
- No query parameters for core pages

**Content:**
- Semantic HTML (h1, h2, article, etc.)
- Alt text on images
- Internal linking

**Acceptance Criteria:**
- [ ] Public profiles indexable by Google
- [ ] Rich previews when shared
- [ ] Lighthouse SEO score >90
- [ ] Listed on Google within 1 week

---

### 9.4 Analytics & Monitoring

**User Analytics (Free Options):**
- **Umami** (self-hosted, open source) or **PostHog** (1M events/month free)
- Page views
- User actions (clicks, reactions, comments)
- User flows and funnels
- Retention cohorts
- A/B test results

**Performance Monitoring (Free Tiers):**
- **Sentry** (5K errors/month free) - Error tracking
- **Better Stack** (1GB logs/month free) - Logging
- Performance metrics
- User feedback

**Backend Monitoring (Free Options):**
- **Sentry** (covers backend errors)
- **Better Stack** (free tier logging)
- Custom metrics dashboard (self-built)
- API response times
- Database query performance
- Server health
- Uptime monitoring via **UptimeRobot** (free: 50 monitors)

**Events to Track:**
- Sign up completed
- Spotify connected
- Friend added
- Song of day revealed
- Reaction added
- Comment posted
- Calendar viewed
- Share initiated
- Notification clicked

**Acceptance Criteria:**
- [ ] All key events tracked
- [ ] Error rate <0.1%
- [ ] 99.9% uptime
- [ ] Performance dashboards set up

---

## 10. Release Strategy

### 10.1 Development Phases

#### Phase 1: MVP (Months 1-3)
**Goal:** Core functionality for internal testing

**Features:**
- Spotify connection & OAuth
- Tracking system (client + server)
- Song of the day calculation
- Basic reveal screen
- Personal calendar view
- User profiles (basic)
- Responsive design (mobile + desktop)

**Deliverable:** Staging environment for team testing

---

#### Phase 2: Beta (Month 4)
**Goal:** Friends & family testing

**Added Features:**
- Friend system (add, accept, remove)
- Social feed
- BeReal-style reactions
- Comments
- Privacy settings
- Real-time updates (WebSocket)
- Browser notifications

**Deliverable:** Public beta URL for 50-100 testers

---

#### Phase 3: Public Launch (Month 5)
**Goal:** Public release

**Polish:**
- UI/UX refinement based on feedback
- Performance optimization
- Bug fixes
- SEO optimization
- Landing page
- Marketing materials

**Deliverable:** v1.0 public release at replay.app

---

#### Phase 4: Post-Launch (Months 6-12)
**Goal:** Growth & iteration

**Added Features:**
- Weekly recaps
- Music Twins
- Friend playlists
- Explore page
- Profile customization
- PWA enhancements

**Focus:** User growth, engagement optimization

---

### 10.2 Beta Testing Plan

**Recruitment:**
- Internal team: 10 people
- Friends & family: 30 people
- Reddit/Discord communities: 20 people
- Music enthusiasts: 40 people

**Duration:** 4 weeks

**Testing Focus:**
- Cross-browser compatibility
- Mobile vs desktop experience
- Real-world usage patterns
- Network conditions (3G, 4G, WiFi)
- Different screen sizes

**Feedback Collection:**
- In-app feedback form
- Weekly survey
- Private Discord channel
- 1-on-1 user interviews
- Analytics review

**Success Criteria:**
- <10 critical bugs
- >70% beta users active daily
- >4.0 average satisfaction rating
- Positive qualitative feedback

---

### 10.3 Launch Plan

**Pre-Launch (2 weeks before):**
- Landing page live
- SEO optimization complete
- Social media accounts created
- Press kit prepared
- Beta feedback addressed

**Launch Day:**
- Product Hunt launch
- Reddit posts (r/Music, r/Spotify, r/InternetIsBeautiful)
- Twitter announcement thread
- Email beta testers
- Press release to tech blogs

**Post-Launch (First 2 weeks):**
- Daily monitoring of feedback
- Quick bug fixes
- Engage with users on social media
- Share user testimonials
- Track growth metrics

---

## 11. Success Metrics & KPIs

### 11.1 Primary Metrics

**User Acquisition:**
- Total users: 10,000+ in 3 months
- Organic growth: >70% of signups
- Viral coefficient: 1.5+ (each user brings 1.5 new users)
- Landing page conversion: >10%

**Engagement:**
- Daily Active Users (DAU): 60%+ of registered users
- 9:30pm notification open rate: >70%
- Average session time: 2-4 minutes
- Sessions per day: 1-2
- Feed engagement: 5+ actions per session

**Retention:**
- D1: 80%+
- D7: 70%+
- D30: 50%+
- D90: 35%+

**Social Engagement:**
- Average friends per user: 5+
- Reactions per user per week: 3+
- Comments per user per week: 1+
- Songs added to queue per week: 2+

---

### 11.2 Secondary Metrics

**Content Creation:**
- % users sharing publicly: 20%+
- % users with public profiles: 15%+
- Daily share actions: 10% of users

**Discovery:**
- New songs discovered via friends: 3+ per week
- Click-through to Spotify: 40%+ of queue adds
- Explore page usage: 20% of users weekly

**Platform Usage:**
- Mobile vs desktop split: 60/40
- Cross-device usage: 30% use both
- Average devices per user: 1.5

**Product Quality:**
- Error rate: <0.1%
- Crash rate: <0.01%
- Lighthouse score: >90 all categories
- Average load time: <2 seconds

---

### 11.3 Leading Indicators

**Good signs:**
- High notification open rate
- Users returning to calendar often
- Organic social media shares
- Friend invites sent
- Time spent in app increasing
- Positive app store/social reviews

**Red flags:**
- Low 9:30pm engagement
- High drop-off during onboarding
- Low friend connection rate
- Short session times
- High churn after week 1

---

## 12. Risks & Mitigations

### 12.1 Technical Risks

**Risk:** Browser limitations affect tracking accuracy
- **Mitigation:** Use Page Visibility API, service workers, local storage sync
- **Backup:** Prompt users to keep tab open, increase polling frequency

**Risk:** Spotify API rate limiting
- **Mitigation:** Smart caching, optimized polling, batch requests
- **Backup:** Reduce polling frequency if needed

**Risk:** WebSocket scaling issues
- **Mitigation:** Redis adapter, horizontal scaling, load balancing
- **Backup:** Fallback to polling

**Risk:** Performance on slow connections
- **Mitigation:** Aggressive optimization, lazy loading, compression
- **Backup:** Progressive loading, offline mode

---

### 12.2 Product Risks

**Risk:** Users don't check daily
- **Mitigation:** A/B test notifications, make reveal satisfying
- **Backup:** Weekly recaps, email digests

**Risk:** Low friend adoption (network effects don't kick in)
- **Mitigation:** Viral invite mechanics, make solo mode valuable
- **Backup:** Public explore page, starter community

**Risk:** Privacy concerns
- **Mitigation:** Clear communication, strong defaults, calendar always private
- **Backup:** Private mode with stats, no social

**Risk:** Users don't find friend discovery valuable
- **Mitigation:** Beta test heavily, refine discovery UI
- **Backup:** Pivot to personal analytics angle

---

### 12.3 Business Risks

**Risk:** Low user growth
- **Mitigation:** Strong viral mechanics, marketing push, influencer partnerships
- **Backup:** Focus on retention with smaller base, add premium features

**Risk:** Spotify changes API/ToS
- **Mitigation:** Stay updated, maintain good relationship with Spotify
- **Backup:** Adapt features, communicate with users

**Risk:** Competitor launches similar product
- **Mitigation:** Move quickly, differentiate on UX and social
- **Backup:** Emphasize unique aspects (BeReal reactions, calendar aesthetic)

---

### 12.4 Platform-Specific Risks

**Risk:** iOS Safari notification limitations
- **Mitigation:** Offer email notifications, in-app alerts
- **Backup:** Promote PWA installation for better notifications

**Risk:** Browser compatibility issues
- **Mitigation:** Extensive testing, progressive enhancement
- **Backup:** Graceful degradation, clear browser requirements

**Risk:** Ad blockers interfere with tracking
- **Mitigation:** No ads on Replay, clear explanation that tracking is core feature
- **Backup:** Whitelist instructions, alternative tracking methods

---

### 12.5 Infrastructure & Cost Risks

**Risk:** Free tier limits exceeded during growth
- **Mitigation:** Monitor usage closely, prepare upgrade path
- **Backup:** Implement usage alerts at 80% capacity, optimize before hitting limits

**Risk:** Render.com cold starts hurt UX
- **Mitigation:** Use Fly.io (no cold starts) or upgrade to paid Render
- **Backup:** Keep-alive ping service, migrate to paid tier ($7/mo)

**Risk:** Database storage fills up (512MB limit)
- **Mitigation:** Archive old data, implement data retention policy
- **Backup:** Upgrade to Neon paid ($19/mo) or migrate to self-hosted Postgres

**Risk:** Backend polling exceeds API rate limits
- **Mitigation:** Implement smart batching, respect rate limits, exponential backoff
- **Backup:** Reduce polling frequency temporarily, prioritize active users

**Risk:** Sudden traffic spike breaks free tier
- **Mitigation:** Implement queue system, rate limiting on signup
- **Backup:** Emergency upgrade to paid tiers, communicate with users

---

## 13. Future Considerations

### 13.1 Potential Features (6-12 months)

**Enhanced Social:**
- Direct messaging about songs
- Group listening rooms
- Collaborative playlists
- Voice notes on reactions

**Advanced Stats:**
- Yearly "Wrapped" style videos
- Compare with friends
- Listening personality quiz
- Mood tracking

**Platform Expansion:**
- Native iOS app (if web proves concept)
- Native Android app
- Desktop app (Electron)
- Browser extension

**Music Platform Integration:**
- Apple Music support
- YouTube Music
- Tidal
- SoundCloud

**Community Features:**
- Public communities/groups
- Genre-based discovery
- Artist verification
- Concert discovery

---

### 13.2 Monetization Strategy

**Premium Subscription ($2.99/month or $19.99/year):**

**Features:**
- Extended stats (all-time, lifetime hours)
- Unlimited friends (free = 100 limit)
- Custom calendar themes
- Advanced analytics dashboard
- Early access to features
- Export data as PDF
- No ads (if added to free tier)
- Priority support

**Other Revenue:**
- Spotify affiliate (if available)
- Sponsored playlists (tasteful)
- Artist partnerships
- Physical products (calendar prints)

**Note:** Keep free tier valuable. Premium = "nice to have."

---

### 13.3 Technical Debt to Address

**Post-Launch:**
- Migrate to microservices (if needed for scale)
- Implement caching layer (Redis)
- Database optimization (indexing, query tuning)
- CDN for static assets
- Monitoring improvements

---

## 14. Appendix

### 14.1 Competitive Analysis

**Last.fm:**
- Pros: Established, detailed stats
- Cons: Outdated UI, not social, no daily ritual
- **Our advantage:** Modern design, social, daily engagement

**Stats.fm:**
- Pros: Beautiful stats, Spotify-focused
- Cons: Not social, stats-heavy
- **Our advantage:** Social discovery, calendar, casual

**Spotify Wrapped:**
- Pros: Massive engagement yearly, beautiful
- Cons: Once a year only
- **Our advantage:** Daily, year-round, social

**BeReal:**
- Pros: Proven daily ritual, viral growth
- Cons: Losing momentum, photo-based
- **Our advantage:** Music (stronger identity), better retention

---

### 14.2 Tech Stack Summary (100% Free)

**Frontend:**
- React 18
- Tailwind CSS
- React Router
- React Query
- Socket.io-client
- Framer Motion

**Backend:**
- Node.js + Express
- PostgreSQL
- Redis (Upstash Free or Redis Cloud Free)
- Socket.io
- Bull Queue or node-cron

**Hosting (All Free Tiers):**
- Vercel Free or Netlify Free (frontend)
- Render.com Free or Fly.io (backend - 3 VMs free)
- Neon Serverless Postgres Free or Supabase Free (database)
- Cloudflare Free (CDN)
- Cloudflare R2 Free (file storage - 10GB)

**Third-Party (All Free):**
- Spotify Web API (free)
- Firebase Cloud Messaging (push notifications - free)
- Umami self-hosted or PostHog Free (analytics - 1M events/month)
- Sentry Free (error tracking - 5K errors/month)
- Better Stack Free (logging - 1GB/month)
- UptimeRobot Free (uptime monitoring - 50 monitors)

**Total Cost: $0/month** (supports ~1,000 active users)

---

### 14.3 Free Tier Limitations & Scale Considerations

**Current Free Tier Limits:**

**Render.com Free Tier:**
- Apps spin down after 15 minutes of inactivity (cold starts ~30s)
- 750 hours/month shared across all services
- Limited to web services only

**Neon Postgres Free:**
- 512MB storage (estimated ~50K-100K daily song entries)
- Databases pause after 5 minutes of inactivity
- 10 projects maximum

**Upstash Redis Free:**
- 10,000 commands/day
- ~417 commands/hour (may need optimization for high traffic)

**Vercel/Netlify Free:**
- 100GB bandwidth/month
- With 10K users averaging 10MB each = 100GB (at limit)

**Cloudflare R2 Free:**
- 10GB storage
- 10M Class A operations/month
- 100M Class B operations/month

**PostHog Free:**
- 1M events/month
- With 1K users × 50 events/user/month = 50K events (well within limits)

**When You'll Need to Upgrade:**

| Users | Issue | Solution | Cost |
|-------|-------|----------|------|
| 1K-5K | Render cold starts annoying | Upgrade to paid ($7/mo) or switch to Fly.io | $7/mo |
| 5K-10K | Database > 512MB | Upgrade Neon ($19/mo) or Supabase ($25/mo) | $19-25/mo |
| 10K+ | Bandwidth > 100GB | Stay on Vercel (CDN handles it) or upgrade | $0-20/mo |
| 20K+ | Redis commands > 10K/day | Upgrade Upstash ($10/mo) | $10/mo |
| 50K+ | Analytics > 1M events | Self-host Umami (free) or upgrade PostHog | $0-49/mo |

**Estimated Monthly Costs:**
- **0-1K users**: $0/month (100% free)
- **1K-10K users**: $7-50/month
- **10K-50K users**: $50-150/month
- **50K-100K users**: $150-400/month

**Cost Optimization Strategies:**
1. Keep frontend on Vercel/Netlify free (Cloudflare CDN handles bandwidth)
2. Self-host analytics (Umami) instead of paid services
3. Use Fly.io (3 free VMs) instead of Render to avoid cold starts
4. Optimize Redis usage to stay under 10K commands/day
5. Archive old listening data to reduce database size
6. Use Cloudflare R2 (stays free longer than S3)

---

### 14.4 Open Questions

1. Should we allow manual song logging?
2. Share with branding vs. clean share?
3. Limit emoji reactions or allow custom?
4. What if no songs played that day?
5. Show friends' full stats or just top 3?
6. Backend polling frequency: Start with 60min or 30min for all users?
7. How to handle users who exceed free tier limits?

**Decision deadline:** Phase 2 (Beta)

---

### 14.5 Success Stories (Aspirational)

**6 months:**
- Featured on Product Hunt #1
- 50,000+ users
- Written up in TechCrunch
- Community forming

**1 year:**
- 500,000+ users
- Verified artists joining
- Community events/meetups
- Approaching profitability

**2 years:**
- 5M+ users
- Native apps launched
- Artist partnerships
- Acquisition interest

---

## 15. Approval & Sign-off

**Document Status:** Draft  
**Version:** 1.0  
**Date:** November 18, 2025  
**Platform:** Web Application (Mobile & Desktop Browsers)

**Stakeholders:**
- [ ] Product Manager
- [ ] Engineering Lead (Frontend)
- [ ] Engineering Lead (Backend)
- [ ] Design Lead
- [ ] Marketing Lead
- [ ] Legal/Compliance

**Next Steps:**
1. Review and approve PRD
2. Create technical specification
3. Design mockups (mobile + desktop)
4. Set up development environment
5. Estimate timeline
6. Kickoff sprint

---

**End of PRD**

Total Pages: 42  
Total Words: ~11,500  
Platform: Web Application (Responsive)  
Primary Target: Music-loving Gen Z & Millennials  
Launch Timeline: 5 months to public release
