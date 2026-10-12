# Milestones: Nine Builds

Each Build is one weekly session, and each one ends with something you can run and show. A Build starts from the finished state of the one before it, so keep your `main` branch working.

| Build | Week | Milestone |
|---|---|---|
| 1 | 4 | Domain core in the terminal |
| 2 | 5 | Event search, sorting, backlog, first tests |
| 3 | 6 | Architecture, state machine, server skeleton |
| 4 | 7 | Working REST API (in memory) |
| 5 | 8 | SQLite and the overselling fix |
| 6 | 9 | Frontend on mock data |
| 7 | 10 | Login, roles and a connected app |
| 8 | 11 | Refunds, waitlist, expiry, real test suite |
| 9 | 12 | QR check-in, CI, security, demo-ready |

---

## Build 1: Domain core in the terminal

**You deliver:** events, ticket tiers, bookings with a capacity rule, a first-in-first-out waitlist, and fast lookup of a booking by its reference code. It runs in the terminal. No server, no database.

**You practise:** functions and objects, `Map`, a queue built as a linked list, Big O, errors, Git.

**Done when**
- `npm run demo` prints the whole story: an event sells out, a booking is refused, people join the waitlist, a booking is cancelled, and the next person in line is named.
- `npm run benchmark` shows a `Map` lookup far faster than `Array.find`, and you can explain why in Big O terms.
- Your first pull request is merged.

## Build 2: Event search, sorting, backlog, first tests

**You deliver:** search and filter events by text, city, date range and price; sort by date, price or availability using a merge sort you write yourself; the backlog written as user stories; your first automated tests.

**You practise:** sorting algorithms, stability, Big O, Agile and Scrum, writing user stories with acceptance criteria.

**Done when**
- Search, filter and sort work and never change the original list.
- Every user story you are building has acceptance criteria.
- `npm test` runs and passes.

## Build 3: Architecture, state machine, server skeleton

**You deliver:** a layered design (routes, services, rules, data), a booking life cycle written as an explicit state machine, and a web server that answers `/health` and serves static files.

**You practise:** requirements, system architecture, state diagrams, HTTP basics.

**Done when**
- A diagram of your architecture and your booking states is in `docs/`.
- Invalid state changes (for example paying a cancelled booking) are refused by tests.
- The server starts and `/health` responds.

## Build 4: Working REST API (in memory)

**You deliver:** an API that works end to end with data held in memory: create events and tiers, publish, search, book, pay with a mock payment, and cancel an unpaid booking.

**You practise:** REST design, status codes, validation, `async`/`await`, separating routes from rules.

**Done when**
- Every call in `docs/api-examples.md` works with `curl`.
- Errors always come back in the same shape.
- `npm test` includes API-level tests.

## Build 5: SQLite and the overselling fix

**You deliver:** data stored in SQLite, and the last-ticket problem reproduced and then fixed.

**You practise:** SQL, constraints, parameterised queries, atomic operations, concurrency.

**Done when**
- A script shows 50 people trying to buy the last ticket, and exactly one succeeds.
- A test proves it, and fails if the fix is removed.
- Data survives a server restart.

## Build 6: Frontend on mock data

**You deliver:** a website to browse, filter and sort events, view an event, choose tickets, check out with a countdown, and pay with a mock card. It runs on fake data for now.

**You practise:** the DOM, forms, ES modules in the browser, accessibility basics, keeping all data access in one file.

**Done when**
- You can browse, filter, book and "pay" in the browser.
- A sold-out tier is clearly marked and cannot be booked.
- A declined card shows an error and lets you try again.

## Build 7: Login, roles and a connected app

**You deliver:** signup and login with safely stored passwords and signed tokens, three roles, checks that people only see their own data, and the website talking to the real API. New pages: login, my tickets, organizer dashboard.

**You practise:** `fetch`, loading and error states, authentication versus authorization, password hashing, tokens.

**Done when**
- You can sign up as an organizer, publish an event, then sign up as an attendee, book and pay, all in the browser.
- One attendee cannot read another attendee's booking, and one organizer cannot edit another organizer's event.
- `npm test` includes login, bad-token and wrong-role tests.

## Build 8: Refunds, waitlist, expiry, real test suite

**You deliver:** a refund policy based on time to the event, cancelling and refunding paid bookings, a waitlist with timed offers, unpaid bookings that expire and release their seats, and a test suite that proves each rule. You finish with a debugging exercise.

**You practise:** unit and integration tests, boundary cases, a controllable clock, scheduled jobs, debugging method.

**Done when**
- Tests cover every refund boundary, cancelling twice, waitlist order, an offer expiring and passing to the next person, and an unpaid hold expiring.
- The website shows the refund amount before you confirm a cancel, offers "Join waitlist" on sold-out tiers, and shows offers with a countdown.
- Your debugging exercise write-up is complete.

## Build 9: QR check-in, CI, security, demo-ready

**You deliver:** a signed QR code for every paid booking, staff check-in, rejection of forged and repeated scans, security headers and rate limiting, automated tests on every push, and a project ready to demo.

**You practise:** signing and verification, continuous integration, web security basics, handling secrets.

**Done when**
- The full path works in the browser: organizer publishes, attendee books, pays and sees a QR code, staff scans it, and a second scan is rejected.
- `npm test` passes, including forged-code, duplicate-scan and simultaneous-scan tests.
- A push to GitHub runs the tests automatically and they pass.
- You have one "the AI got this wrong" story ready for the demo.
