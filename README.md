<div align="center">

# DSMS: Driving School Management System

**One platform for running driving schools: lesson scheduling, instructor commissions, two-way payouts and expense reimbursements, with a web admin panel and a Flutter app for instructors and school admins.**

![Status](https://img.shields.io/badge/status-live-2ea44f?style=flat-square)
![Platform](https://img.shields.io/badge/platform-web%20%7C%20flutter%20mobile-informational?style=flat-square)
![NestJS](https://img.shields.io/badge/NestJS-11-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-PostgreSQL-2D3748?style=flat-square&logo=prisma&logoColor=white)
![Vue](https://img.shields.io/badge/Vue_3-Vite-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-mobile-02569B?style=flat-square&logo=flutter&logoColor=white)

[Live app (sign-in required)](https://dsms.everbuild.cloud) · [Portfolio](https://portfolio.everbuild.cloud) · [LinkedIn](https://linkedin.com/in/dafallah-ibrahim)

</div>

> [!NOTE]
> This is a showcase repository. The source code is private because this is company work, built for the HRM-Platform organization and shared with permission. This repo covers what the product does, how it's built and what I did on it. I'm happy to walk through the code in an interview.

<p align="center">
  <img src="docs/screenshots/super-admin-dashboard.png" width="100%" alt="Super admin dashboard (dark theme) with all-time revenue, total paid out, net balance, monthly and weekly revenue, today's bookings, payout balance and counts of schools, instructors, students and pending expenses">
</p>

<p align="center">
  <img src="docs/screenshots/school-overview-fuel-settings.png" width="49%" alt="School overview page with the school profile, trade license, fuel-charge-per-class settings with eligible lesson types, appointment metrics and the school's payout balance">
  <img src="docs/screenshots/instructor-profile-earnings.png" width="49%" alt="Instructor overview with license details, commission rate, weekly, monthly and all-time earnings, and a balance breakdown between school and instructor">
</p>
<p align="center">
  <img src="docs/screenshots/instructor-balance-payout-ledger.png" width="49%" alt="Instructor payout ledger listing approved payouts in both directions (school to instructor and instructor to school), with method, date, who recorded each one, and edit, history and delete actions">
  <img src="docs/screenshots/appointments-calendar.png" width="49%" alt="Monthly appointments calendar with a booking-count badge on each day">
</p>
<p align="center">
  <img src="docs/screenshots/appointments-list.png" width="49%" alt="Appointments list showing student, instructor, lesson type, start time, lesson status and payment status, with pagination">
  <img src="docs/screenshots/new-appointment-drawer.png" width="49%" alt="New appointment drawer: school, instructor, existing or new student, lesson type, start and end time, number of classes and total amount in AED">
</p>
<p align="center">
  <img src="docs/screenshots/expenses-review.png" width="98%" alt="Expenses page with total, pending and approved summaries, filters by type, status, school and date, and a pending fuel expense with approve and reject actions">
</p>
<p align="center">
  <img src="docs/screenshots/mobile-appointments.png" width="250" alt="Appointments list on a phone with status and payment badges">
  <img src="docs/screenshots/mobile-navigation.png" width="250" alt="Admin panel navigation drawer on a phone">
  <img src="docs/screenshots/mobile-dashboard.png" width="250" alt="Admin panel dashboard on a phone, showing stacked revenue and balance cards">
</p>
<p align="center">
  <img src="docs/screenshots/admin-login.png" width="60%" alt="Admin login page with email and password fields">
</p>

<sub>All screenshots are real captures of the live admin panel. Every record shown is seed or test data. Screens that held test records naming real people were left out or cropped, and an ID number on the instructor profile is masked.</sub>

## Features

**Multi-school administration (super admin)**
- Create and manage driving schools: trade license and expiry, school category (light vehicle, motorcycle, heavy vehicle, combined, all categories), address, status.
- Create school admins and assign them to schools.
- Cross-school dashboard with a date range: all-time, monthly and weekly revenue, today's bookings, total paid out, net balance, money owed in each direction, counts of schools, instructors and students, pending expenses, a revenue trend chart and a top-instructors chart.
- A school overview with profile, metrics (revenue, appointments, completed and cancelled), the school's payout balance, assigned instructors and recent appointments.

**School operations**
- Instructors: license number and expiry, years of experience, per-instructor commission rate, status, and an overview page with earnings and balance.
- Students: create during booking or ahead of time, look up by traffic code with autocomplete. Students without an email get one generated automatically.
- Vehicles: registration, make, model, year and colour, status (active, inactive, maintenance), and vehicle types limited to what the school's category allows.
- School settings: a fuel charge per class, plus the lesson types it applies to.

**Scheduling**
- Bookings with lesson types (theory, practical, road test, parking test, assessment test), one or more classes, a total amount and an optional vehicle.
- Lesson lifecycle: pending, in progress, completed, cancelled, no-show. Payment status (paid, unpaid, partial) and payment method (cash, card, online).
- Instructor double-booking is rejected when appointments are created or updated.
- List view and monthly calendar view.

**Money: commissions, payouts and expenses**
- Each booking splits automatically into an instructor share and a school share. The fuel charge is taken out first and goes to the school.
- Payouts run in both directions. A school pays an instructor, or an instructor settles cash they collected on the school's behalf.
- Instructors submit settlements. Admins approve or reject them, and every create, update, review and delete goes into an audit log.
- Expenses (fuel, vehicle maintenance, phone, materials and supplies, other): an instructor submits, an admin approves or rejects, then marks it reimbursed.
- Earnings reports for each instructor and each school.

**Mobile app (Flutter, "Drive Mentor")**
- Instructor and school-admin apps in one Flutter codebase, with push notifications. See [Mobile app (Flutter)](#mobile-app-flutter) below for screens, features and stack.

## Mobile app (Flutter)

**Drive Mentor** is the Flutter app for the people who work in the school day to day. After picking a role on the start screen, a driving instructor gets their lessons, schedule and money, and a school administrator gets the school's dashboard, staff, bookings and approvals. Both talk to the same NestJS API as the web panel.

<p align="center">
  <img src="docs/screenshots/mobile-app/cover-trio.png" width="100%" alt="Three Drive Mentor screens fanned out on a green background: the school admin dashboard in the centre, the instructor month calendar with today's lessons on the left and the admin revenue report on the right">
</p>
<p align="center">
  <img src="docs/screenshots/mobile-app/framed/role-selection.png" width="31%" alt="Drive Mentor start screen where the user picks Driving Instructor or School Administrator">
  <img src="docs/screenshots/mobile-app/framed/instructor-dashboard.png" width="31%" alt="Instructor dashboard with today's lesson count, net balance with the school, what each side owes, total paid out, and weekly and monthly earnings">
  <img src="docs/screenshots/mobile-app/framed/instructor-schedule-calendar.png" width="31%" alt="Instructor month calendar with coloured lesson dots per day and today's lessons marked completed, in progress or pending">
</p>
<p align="center">
  <img src="docs/screenshots/mobile-app/framed/instructor-bookings.png" width="31%" alt="Instructor bookings list with name search and status filter chips, showing lesson type, date, time, location and price">
  <img src="docs/screenshots/mobile-app/framed/booking-details.png" width="31%" alt="Booking details with the student, call and message buttons, lesson time and duration, payment status, price, lesson type, and Start Lesson and Cancel Lesson buttons">
  <img src="docs/screenshots/mobile-app/framed/instructor-earnings-report.png" width="31%" alt="Instructor earnings report with weekly, monthly and custom ranges, total earnings, bookings, completed and cancelled tiles and a daily earnings bar chart">
</p>
<p align="center">
  <img src="docs/screenshots/mobile-app/framed/instructor-expenses.png" width="31%" alt="Instructor expense claims by category (fuel, materials, phone, vehicle maintenance) with pending, approved and reimbursed statuses">
  <img src="docs/screenshots/mobile-app/framed/instructor-payouts-settlement.png" width="31%" alt="Instructor payouts screen with school-owes, instructor-owes, net and pending-settlement amounts, payout history and a Settle button">
  <img src="docs/screenshots/mobile-app/framed/instructor-notifications.png" width="31%" alt="In-app notification inbox with lesson assigned, rescheduled and cancelled messages and a Mark all read action">
</p>
<p align="center">
  <img src="docs/screenshots/mobile-app/framed/admin-dashboard.png" width="31%" alt="School admin dashboard with instructor and student counts, all-time revenue, money owed in each direction, total paid out and net balance">
  <img src="docs/screenshots/mobile-app/framed/admin-instructors.png" width="31%" alt="Admin instructor list with search, active and inactive filters, license numbers and lesson counts; one email is masked">
  <img src="docs/screenshots/mobile-app/framed/admin-instructor-report.png" width="31%" alt="Per-instructor report with overview, schedule and earnings tabs, balances, total paid, contact details, license and commission rate; the phone number is masked">
</p>
<p align="center">
  <img src="docs/screenshots/mobile-app/framed/admin-bookings.png" width="31%" alt="School-wide bookings for admins with student, teacher, lesson type, time, location and price">
  <img src="docs/screenshots/mobile-app/framed/admin-revenue-report.png" width="31%" alt="Admin revenue report with total revenue, bookings, completed and cancelled counts and a revenue trend chart">
  <img src="docs/screenshots/mobile-app/framed/admin-vehicles.png" width="31%" alt="Vehicles list with status filters (active, inactive, maintenance) and type filters (light vehicle, motorcycle, heavy vehicle)">
</p>
<p align="center">
  <img src="docs/screenshots/mobile-app/framed/admin-expense-approval.png" width="31%" alt="Admin expense detail for a pending fuel claim with Reject and Approve buttons">
  <img src="docs/screenshots/mobile-app/framed/schedule-light-theme.png" width="31%" alt="Instructor schedule calendar in the light theme">
  <img src="docs/screenshots/mobile-app/framed/admin-reports-light-theme.png" width="31%" alt="Admin revenue report in the light theme">
</p>

**Store-style previews**

<p align="center">
  <img src="docs/screenshots/mobile-app/cards/card-1-schedule.png" width="31%" alt="Store-style preview card headed 'Every lesson, at a glance' showing the instructor month calendar with today's lessons and their status">
  <img src="docs/screenshots/mobile-app/cards/card-2-payouts.png" width="31%" alt="Store-style preview card headed 'Know who owes whom' showing the instructor payouts screen with balances and cash settlements with the school">
</p>

<sub>These screens are rendered from the Flutter codebase in a phone viewport: the real app compiled for Flutter web and captured in headless Chrome at 390×844 (3x), not on a device or emulator, then placed in a drawn phone frame (the 9:41 status bar and home indicator are part of the frame, not the app). Firebase push setup is skipped in that build because it has no web Firebase config. Every screen loads live data from a throwaway copy of the API and database seeded with invented demo data (school, people, phone numbers and plates), never production. One instructor email that matches a seed login and one demo phone number are masked, and one notification whose text came from the backend with a different currency format was cut from the inbox capture.</sub>

### What it does

**Instructor**
- Dashboard with today's lessons, the running balance with the school (who owes whom, total paid out) and weekly and monthly earnings.
- Month calendar schedule, and a bookings list with search and status filters.
- Booking details with call and message shortcuts, payment status, and starting, completing or cancelling a lesson.
- Create and edit appointments: look up the student by traffic code, then pick lesson type, number of classes and price.
- Earnings reports (weekly, monthly or a custom range) with charts.
- Expense claims with receipt photo upload, and payouts with cash settlement back to the school.
- Notification inbox, profile, password change, and dark and light themes.

**School admin**
- School dashboard with revenue and the balances between the school and its instructors.
- Instructor management, with a per-instructor report (overview, schedule, earnings).
- School-wide bookings, and revenue reports with top instructors.
- Vehicles (create, edit, status and type).
- Expense approval and reimbursement, payouts and settlements, fuel charges and school settings.

**Both roles**
- Separate sign-in per role with JWT access and refresh tokens and "remember me".
- Firebase push notifications that open the related screen when tapped.

### How it's built

- **Clean Architecture:** domain, data and presentation layers. Use cases and repository interfaces sit in the domain layer, and failures come back as dartz `Either` values instead of exceptions.
- **State, routing and DI:** GetX for state management and routing, get_it for dependency injection.
- **Networking:** a single Dio client with a `QueuedInterceptorsWrapper`. It attaches the bearer token to every request, and on a 401 it refreshes the token once through the role's refresh endpoint while other requests wait on the same refresh, then retries.
- **Storage:** tokens live in flutter_secure_storage, with a one-time migration out of GetStorage from earlier versions. get_storage holds preferences such as theme and role.
- **Notifications:** firebase_messaging and flutter_local_notifications. The app registers its FCM token with the API and reads the unread count and inbox from it.
- **UI:** Syncfusion calendar and calendar_view, fl_chart, skeletonizer loading states, cached_network_image, image_picker, pull_to_refresh, google_nav_bar, timeago, pinput, flutter_gen for assets.

### How it connects to the backend

The app calls the versioned REST API (`/api/v1`) over HTTPS, the same API the web panel uses. Instructors and admins each have their own login, refresh, logout and profile endpoints (`/instructor/*`, `/admin/*`), so a token only works for its role. Bookings, expenses, payouts, vehicles, reports and notifications go through the shared resource endpoints, where the API's JWT and role guards and its school-scoped checks decide what each user can see. When a booking, payout or expense changes, the API's notification listener stores an inbox entry and sends a push through FCM to the user's registered devices.

## Architecture

```mermaid
flowchart TB
    WEB["Admin panel<br/>Vue 3 + Vite SPA"]
    APP["Drive Mentor<br/>Flutter app (Android / iOS)<br/>GetX · get_it · Dio"]
    GHA["GitHub Actions<br/>build · test · deploy"]

    subgraph Server["VPS (Docker)"]
        FE["nginx container<br/>static SPA + /api reverse proxy"]
        subgraph API["NestJS API · /api/v1"]
            HTTP["HTTP layer<br/>JWT guard · RBAC · validation · interceptors"]
            AUTH["Auth<br/>JWT access + refresh"]
            DOMAIN["Domain modules<br/>schools · instructors · students<br/>vehicles · appointments"]
            MONEY["Money modules<br/>payouts · expenses · reports"]
            EVT(["Event emitter"])
            NOTIF["Notifications<br/>listener + FCM sender"]
        end
        DB[("PostgreSQL<br/>(Prisma ORM)")]
    end

    FCM["Firebase Cloud Messaging"]

    WEB -->|HTTPS| FE
    FE -->|/api| HTTP
    APP -->|"HTTPS REST /api/v1<br/>JWT per role (instructor / admin)"| HTTP
    HTTP --> AUTH
    HTTP --> DOMAIN
    HTTP --> MONEY
    DOMAIN -- booking events --> EVT
    MONEY -- payout / expense events --> EVT
    EVT --> NOTIF
    AUTH --> DB
    DOMAIN --> DB
    MONEY --> DB
    NOTIF --> DB
    NOTIF --> FCM
    FCM -. push .-> APP
    GHA -. SSH deploy + health check .-> Server
```

There is more detail, including the data model and the settlement flow, in [docs/architecture.md](docs/architecture.md).

### Key engineering decisions

- **The commission split is fixed when a lesson is booked.** At creation the API reads the instructor's commission rate and the school's fuel settings, works out `instructor_share`, `school_share` and the total fuel charge, and stores them on the appointment along with who collected the money (school or instructor). Changing a rate later doesn't rewrite past earnings. Booking edits recompute the split from the stored rate.
- **The settlement ledger runs both ways.** Balances aren't stored. They're aggregated from completed appointments (split by who collected the money) minus approved payouts in each direction, so the school-owes and instructor-owes figures can't drift out of sync. Settlements an instructor submits start as `PENDING`, are checked against what the instructor actually owes, and only count once an admin approves them. Every payout action goes into a `PayoutLog` audit trail.
- **One user table, role-based access.** Super admin, manager, admin, instructor and student all share one `User` model, with role-specific tables linked to it. A global JWT guard protects every route unless it's marked `@Public()`. `@Roles` with `RolesGuard` enforces RBAC, and school-scoped checks keep admins inside their own school's data.
- **Notifications are event-driven.** Booking, payout, expense and instructor-status changes emit domain events. An async listener stores the in-app notification, checks the user's settings for that category, sends to all of the user's devices through FCM, and deletes device tokens FCM reports as invalid.
- **One consistent API contract.** An interceptor converts request and response bodies between snake_case on the wire and camelCase in the code, and every response uses the same `{ status, message, code, data, meta }` envelope. The API also has URI versioning, three-tier rate limiting, Helmet, soft deletes, refresh tokens stored as bcrypt hashes, and Swagger docs. The web client refreshes tokens silently on a 401 and dedupes concurrent refreshes.
- **Automated delivery.** GitHub Actions builds and tests each repo, then deploys over SSH with `docker compose` (multi-stage images, non-root users). Prisma migrations run when the container starts, and each deploy has to pass a health check. If the frontend's health check fails, the deploy rolls back to the previous commit.

## Tech stack

| Layer | Tech |
|---|---|
| API | NestJS 11, TypeScript, Passport JWT (access + refresh), bcrypt, class-validator, @nestjs/throttler, Helmet, Swagger (OpenAPI) |
| Data | PostgreSQL, Prisma 7 (`@prisma/adapter-pg` driver adapter), versioned Prisma migrations, seed script |
| Events and notifications | @nestjs/event-emitter, Firebase Admin SDK (FCM multicast) |
| Web admin panel | Vue 3, Vite, TypeScript, Tailwind CSS 4, shadcn-vue (Reka UI), TanStack Table, Pinia, vee-validate + Zod, Chart.js (vue-chartjs), vue-sonner |
| Mobile app | Flutter (Dart ^3.6), Clean Architecture (use cases, repositories, dartz `Either`), GetX (state management + routing), get_it (DI), Dio with queued auth/refresh interceptors, flutter_secure_storage + get_storage, firebase_messaging + flutter_local_notifications, fl_chart, Syncfusion calendar, calendar_view, skeletonizer |
| Testing | Jest unit tests with a mocked Prisma service, supertest e2e (API). Vitest and Playwright set up on the web panel |
| Infra and CI/CD | Docker multi-stage builds, nginx (SPA + reverse proxy), GitHub Actions (lint, type-check, test, SSH deploy with health checks) |

## My role

I'm the main engineer on DSMS, across the API, the web admin panel and the mobile app:

- **Backend (NestJS + Prisma):** I wrote the large majority of the commits. That includes the initial schema and seed, the auth module (login, refresh-token rotation, logout), the RBAC setup, and the appointments flow with traffic-code lookup and status management. I also built the expense workflow, earnings and dashboard reports, the commission-split and two-way payout settlement design, school settings with fuel charges, the vehicles module, the FCM notification system, and the Docker and GitHub Actions deployment.
- **Web admin panel (Vue 3):** I connected it to the API and rebuilt the UI on shadcn-vue. I built the dashboard, the school and instructor overview pages, payouts with balance breakdowns, vehicles, payment status and school settings, plus the CI/CD.
- **Mobile app (Flutter):** I'm the sole developer of the Drive Mentor app. All 200 commits in its history (December 2025 to May 2026) are mine, a few of them made through my own automation identity. That covers the architecture, both role apps, the auth and token-refresh layer, and push notifications.
- A teammate added early pieces: the global validation pipe, a first student module and appointment-creation flow on the API, and the first admin-panel scaffold for creating schools and admins.

## Status

- **Live:** the admin panel runs at [dsms.everbuild.cloud](https://dsms.everbuild.cloud) (sign-in required).
- **Timeline:** API work started in December 2025. The web panel followed in February 2026, and most feature work landed between January and April 2026. The mobile app reached v1.1.0 in May 2026. The API has had occasional maintenance commits through August 2026.

---

<sub>© 2026 HRM-Platform. Shared with permission. Source code is private.</sub>
