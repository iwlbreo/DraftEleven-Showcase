DraftEleven

A real-time multiplayer football draft, auction, and season simulation game built for browser play with friends.

🌐 Live Demo: https://drafteleven.online

Note: The source code of this project is kept private. Code samples or a technical walkthrough can be provided on request.

Show Image

About

DraftEleven is an online multiplayer football management game where friends create private rooms, build squads within a budget via snake draft or live auction, set formations and tactics, and compete across league and knockout fixtures.

I built it to turn local football draft nights into a fast, zero-install web application that works across desktop and mobile browsers. It is live in production at drafteleven.online and actively played by real users, supporting both instant guest sessions and registered accounts for tracking career history.

Features
Multiplayer Rooms & Instant Guest Play: Create or join private rooms with a room code as a guest, or sign in with email verification to save past seasons and career stats.
Snake Draft & Live Auction Modes: Build a squad under budget and position constraints with real-time turn timers and bidding synchronized via SignalR.
Tactical Lineup & Transfer Window: Choose formations, assign player roles, and buy or sell players during mid-season transfer windows.
League, Standings & Knockout Rounds: Compete in automated round-robin league fixtures with live standings, goal difference tie-breakers, and semifinal/final brackets.
2D Pitch Simulation & Match Events: Watch matches play out on a 2D canvas with live commentary, substitutions, half-time team talks, and post-match ratings.
Multi-Language Support: Built the i18n infrastructure with i18next and automated translation key validation. The app is available in 8 languages (Turkish, English, German, French, Spanish, Dutch, Russian, Chinese), with translations generated using AI tools.
Tech Stack
Frontend: React 18, TypeScript, Vite, Tailwind CSS, React Router, TanStack React Query, React Hook Form, Zod, i18next
Backend: C#, .NET 9 (ASP.NET Core Minimal APIs), REST API, SignalR (WebSockets for real-time room and match synchronization)
Database & ORM: PostgreSQL 16, Entity Framework Core
DevOps & Deployment: Docker, Docker Compose, Nginx, GitHub Actions (CI/CD), Linux VPS, Resend HTTP API (transactional email)
Screenshots
Draft & Squad Building	Live Match Simulation	Mobile View
Show Image	Show Image	Show Image
What I Learned / Challenges
Real-Time State Synchronization with SignalR: Keeping draft timers, auction bids, and league rounds in sync across multiple browsers required making the server the single source of truth and reconciling state via React Query when a player reconnects or refreshes the page.
Database Concurrency & Race Conditions: Simultaneous actions, such as two users bidding at the last millisecond or joining the same seat, could cause inconsistent state. I solved this using database transactions, unique constraints in PostgreSQL, and optimistic concurrency handling in EF Core.
Offloading Match Simulation to Web Workers: Running 2D physics and match decision logic directly on the main UI thread caused frame drops on mobile devices. Moving the match simulation engine into a dedicated Web Worker kept the React UI responsive at 60 FPS.
Modular Monolith Boundaries: Organizing the backend into separate modules (Rooms, Draft, Competitions, Matches, PlayerCatalog) with isolated DbContext schemas made it much easier to debug domain rules without tightly coupling every table.
Author

İzzet Buğra Kandemir – Computer Engineering Student

GitHub: @iwlbreo
