# Climb Now
## Product Design Proposal — Version 1.0

**Tagline:** Less Planning. More Climbing.

**Project Type:** Independent Personal Software Project  
**Status:** Concept / Early Product Design  
**Platform:** Web Application (MVP), with potential mobile expansion  
**Product Category:** Availability-Based Activity Coordination

---

## 1. Executive Summary

Climb Now is an availability-first climbing partner matching application designed to help indoor climbers find compatible climbing partners based on overlapping schedules and gym locations.

Unlike traditional social networking platforms, which often require users to browse profiles, initiate conversations, and manually coordinate schedules, Climb Now prioritizes availability before introducing users to potential climbing partners.

The core concept is simple:

**Set Availability → Automatic Matching → Confirm Session → Climb Together**

Users select when and where they plan to climb. The system automatically identifies compatible availability, proposes a potential climbing session, and allows participants to confirm without unnecessary scheduling conversations.

If no compatible climber is immediately available, the system keeps the request active and continues searching until a match is found or the request expires.

Climb Now is not intended to become another climbing social network. Its primary purpose is to reduce the time and effort required to coordinate climbing sessions.

## 2. Problem Statement

Indoor climbing can be enjoyed individually or with others. However, climbers who prefer company may struggle to find partners whose schedules align with theirs.

Existing coordination methods often rely on group chats, social media communities, or climbing-specific networking applications.

These approaches typically involve several steps:

1. Find potential climbing partners.
2. Initiate a conversation.
3. Compare schedules.
4. Agree on a gym and time.
5. Confirm the climbing session.

This process can be time-consuming and may fail when participants cannot find mutually available times.

**Core Problem:** Climbers who want company may struggle to find available partners without spending significant time searching, messaging, and coordinating schedules.

Climb Now addresses this problem by reversing the traditional process: match schedules first, then introduce compatible climbers.

## 3. Product Vision

### Vision Statement

To make finding a climbing partner as simple as selecting a time and location.

### Product Mission

Build a lightweight, scheduling-first matching system that automatically connects climbers based on overlapping availability and climbing gym preferences.

### Core Design Principles

**Availability First**

Matching begins with the user's availability rather than browsing profiles or searching for people.

**Automatic Matching**

The system identifies compatible climbing partners without requiring users to manually browse or compare profiles.

**Minimal Social Interaction**

Climb Now focuses on coordinating climbing sessions rather than building a social network.

**Privacy and Safety**

Communication is restricted to confirmed climbing sessions, with appropriate privacy controls and safety mechanisms.

**Low-Friction Experience**

Users should be able to submit availability and receive a potential match with minimal effort.

**Asynchronous Matching**

Users do not need to remain online while the system searches for compatible availability.

**Optional Participation**

The application serves climbers who want company without assuming that all solo climbers need partners.

## 4. Target Users

### Primary Audience

Indoor bouldering and climbing enthusiasts who:

- Frequently climb alone but occasionally prefer a partner or group.
- Have irregular schedules that make coordinating with friends difficult.
- Want to climb with others without extensive social interaction.
- Prefer a quick and practical scheduling solution.
- Are open to meeting other climbers at established indoor climbing gyms.

### Initial Market

Starting with a limited number of gyms would allow the project to evaluate matching performance and user adoption before expanding.

Future expansion could include additional gyms and larger metropolitan areas, depending on user interest and validation results.

## 5. Proposed User Experience

Climb Now follows an availability-first interaction model.

Users do not need to browse profiles, search for climbing partners, or initiate conversations before submitting their schedules.

### Step 1 — Set Availability

Users submit a climbing request containing:

| Field | Example | Requirement |
|---|---|---|
| Climbing Gym | XXX | Required |
| Date | Thursday, October 29 | Required |
| Start Time | 3:00 PM | Required |
| End Time | 5:00 PM | Required |
| Climbing Level | V0–V2 | Optional |
| Session Preference | One-on-one / Group / Either | Optional |

The system validates and stores the request before automatically searching for compatible availability.

For the initial MVP, one-on-one sessions will be prioritized.

### Step 2 — Automatic Matching

After availability is submitted, the system automatically identifies compatible climbing requests.

Primary matching conditions:

- Same climbing gym.
- Compatible date and time.
- Sufficient overlapping availability.
- Active requests from different users.
- Both users are eligible and seeking a climbing partner.

Secondary preferences may include climbing level and session type.

For example:

**User A:** Thursday, 3:00–5:00 PM  
**User B:** Thursday, 4:00–6:00 PM

Both users are available from 4:00–5:00 PM.

The system identifies this shared time window as a potential climbing session.

The proposed minimum overlap duration is 60 minutes, subject to future user testing.

### Step 3 — Match Notification

When compatible availability is detected, the system creates a potential match and notifies the participants.

The notification includes:

- Proposed climbing gym.
- Shared available time.
- Basic compatibility information.
- Options to accept or decline.

Users do not need to browse a list of potential partners.

For the MVP, the system will prioritize presenting one compatible match at a time to reduce unnecessary decisions.

If multiple matches exist, the system may rank them based on overlap duration and other relevant preferences.

### Step 4 — Asynchronous Matching

If no compatible request exists when a user submits availability, the request remains active.

The system continues checking for compatible availability whenever new requests are submitted or existing requests change.

When a compatible request becomes available, the system generates a potential match and sends a notification.

Users can close the application without losing their place in the matching process.

Requests remain active until they are matched, canceled, or expired.

### Step 5 — Session Confirmation

A potential match becomes a confirmed climbing session only after both participants accept.

If either participant declines or the invitation expires, the system can continue searching for other compatible requests.

After confirmation, the system creates a session record containing:

- Gym location.
- Confirmed date and time.
- Participants.
- Session status.

The system should prevent users from confirming conflicting sessions.

### Step 6 — Session Communication

After a session is confirmed, participants may communicate through a session-specific conversation.

Messaging is intended for practical coordination, including:

Confirming meeting points.

Discussing minor schedule changes.

Communicating cancellations or delays.

Climb Now will not include public messaging, social feeds, or unrestricted profile browsing.

Session-based messaging is a planned extension and may be implemented after the core matching and confirmation workflow is validated.

6. Minimum Viable Product (MVP)

The MVP will focus on validating the application's primary value proposition:

Can users find and confirm compatible climbing sessions with less effort than traditional scheduling methods?

7. Matching Engine Design

The initial matching engine will use deterministic algorithms rather than machine learning.

7.1 Matching Conditions

Two availability requests are potentially compatible when:

They belong to different users.

They refer to the same climbing gym.

Their availability intervals overlap.

Their overlap duration meets the minimum requirement.

Both requests are active.

Neither user is blocked or otherwise ineligible for the proposed match.

The proposed session does not conflict with either user's existing confirmed sessions.

For the MVP, sessions will be one-on-one.

7.2 Time Overlap Algorithm

Given two availability intervals:

User A: [StartA, EndA]

User B: [StartB, EndB]

Calculate:

OverlapStart = max(StartA, StartB)

OverlapEnd = min(EndA, EndB)

OverlapDuration = OverlapEnd - OverlapStart

A valid time match requires:

OverlapDuration >= MinimumRequiredDuration

The initial proposed threshold is 60 minutes.

Example

User A: 3:00–5:00 PM
User B: 4:00–6:00 PM

Shared availability: 4:00–5:00 PM

Overlap duration: 60 minutes

Result: Potential Match

Time values should be stored and compared consistently, accounting for gym-local time zones and daylight saving time.

7.3 Matching Priority

If multiple compatible requests exist, the system should select one candidate using a simple, explainable ranking approach.

Proposed ranking priorities:

Longer overlapping availability.

Compatible user preferences, when provided.

Earlier request submission time as a tie-breaker.

The ranking criteria are provisional and may be revised after testing.

7.4 Matching Lifecycle

Request Created → Searching → Potential Match → Invitation Pending → Confirmed / Declined / Expired

When both participants accept:

Confirmed Match → Climbing Session Created

When a match is declined or expires:

Invitation Closed → Eligible Requests Return to Searching

Requests that are canceled or whose availability has passed are no longer eligible for matching.

8. Proposed Technical Architecture

The following architecture is a preliminary recommendation.

8.1 Frontend

React + TypeScript

Responsibilities:

User registration and login.

Gym selection.

Availability submission.

Match status display.

Match acceptance and rejection.

Session dashboard.

Responsive web interface.

8.2 Backend

Node.js + Express

Responsibilities:

REST API development.

Authentication and authorization.

Availability request management.

Matching engine execution.

Match invitation management.

Session confirmation.

Notification processing.

Input validation and error handling.

8.3 Database

PostgreSQL

Proposed entities:

Entity

Purpose

Users

Account and basic profile information

Gyms

Supported climbing locations

AvailabilityRequests

User-submitted availability and request status

MatchInvitations

Proposed matches and participant responses

Sessions

Confirmed climbing sessions

SessionParticipants

Users associated with confirmed sessions

Notifications

Match and session-related notifications

UserBlocks

Records used to prevent unwanted future matching

The exact schema, relationships, indexes, and constraints will be defined during implementation.

8.4 Initial API Design

The following endpoints are proposed for the MVP.

Authentication

POST   /api/auth/register
POST   /api/auth/login
POST   /api/auth/logout
GET    /api/auth/me

Climbing Gyms

GET    /api/gyms
GET    /api/gyms/:id

Availability

POST   /api/availability
GET    /api/availability/me
PATCH  /api/availability/:id
DELETE /api/availability/:id

Matching

GET    /api/matches
GET    /api/matches/:id
POST   /api/matches/:id/accept
POST   /api/matches/:id/decline

Sessions

GET    /api/sessions
GET    /api/sessions/:id
POST   /api/sessions/:id/cancel

Notifications

GET    /api/notifications
PATCH  /api/notifications/:id/read

All user-specific endpoints must enforce authentication and authorization.

These routes are preliminary and may change as the application architecture evolves.

8.5 Matching and Notification Processing

The initial implementation may trigger matching when:

A new availability request is created.

An existing availability request is updated.

A pending match is declined or expires.

A background job may be introduced for invitation expiration and other scheduled operations.

The system should avoid sending duplicate notifications for the same match event.

8.6 Deployment

Potential hosting options include Render or another suitable cloud hosting provider.

The deployment configuration will depend on implementation requirements, available resources, and cost.

Environment variables should be used for sensitive configuration values.

9. Privacy and Safety Considerations

Because Climb Now coordinates real-world meetings between users, privacy and safety are important product requirements.

Proposed Safety Measures

Minimize publicly visible personal information.

Do not expose personal contact details.

Restrict communication to confirmed session participants.

Allow users to decline matches without explanation.

Provide blocking and reporting mechanisms.

Allow users to cancel sessions.

Encourage meetings at established public climbing gyms.

Enforce authentication and authorization.

Protect stored user information.

Avoid exposing precise personal locations.

The MVP should prioritize basic privacy controls even if advanced moderation features are deferred.

These measures can reduce certain risks but cannot guarantee personal safety.

10. Product Differentiation

Climb Now's intended differentiation is its availability-first matching workflow.

Traditional Social Coordination

Find People → Start Conversation → Compare Schedules → Agree on Time → Meet

Climb Now

Set Availability → Automatically Find Overlap → Confirm Session → Climb Together

Key Differences

Time Before People

Users begin by submitting their availability rather than searching for other users.

Automatic Partner Discovery

The system identifies compatible climbers without requiring profile browsing.

Session-Oriented Interaction

Interactions are centered on a specific climbing session rather than ongoing social networking.

Minimal Communication

Users only need to communicate after a session is confirmed, reducing unnecessary scheduling conversations.

Asynchronous Experience

Users can submit availability and return later when a compatible match is found.

Existing climbing platforms may offer similar individual features, including partner discovery, scheduling, and messaging.

Climb Now's proposed differentiation lies in combining these features into a focused, automatic, availability-first workflow.

The uniqueness and practical value of this approach remain subject to competitive research and user validation.

11. Key Challenges and Risks

11.1 Limited User Density

The largest potential challenge is attracting enough active users at the same gym during compatible time windows.

Without sufficient participation, users may frequently receive no matches.

12. Validation Strategy

Before investing in a complete application, the concept should be tested with potential users.

Phase 1 — User Discovery

Interview approximately 10–15 indoor climbers.

Suggested questions:

How often do you climb alone?

Do you ever want a climbing partner but struggle to coordinate schedules?

How do you currently arrange climbing sessions?

Would you submit your availability to an automatic matching system?

Would you prefer automatic matching over browsing potential partners?

What information would you need before accepting a match?

How long would you be willing to wait for a potential match?

What would make you feel comfortable meeting a new climbing partner?

Phase 2 — Interactive Prototype

Build a lightweight prototype demonstrating:

Gym selection.

Availability input.

Automatic time-overlap detection.

Match notification.

Match confirmation.

Test whether users understand the workflow and can complete it without assistance.

Phase 3 — Small Pilot

Invite a small group of interested climbers to test the application at one gym.

Measure actual usage, successful confirmations, and participant feedback.

The initial pilot does not require a formal gym partnership, although any on-site recruitment should respect gym policies.

13. Success Metrics

The primary success metric will be:

Confirmed Climbing Sessions Created Through Automatic Matching

Additional metrics:

Metric

Purpose

Match Success Rate

Percentage of submitted requests resulting in confirmed sessions

Time to Match

Time between request submission and a compatible match

Time to Confirmation

Time between a proposed match and confirmation

Session Attendance Rate

Percentage of confirmed sessions that actually take place

Repeat Usage Rate

Percentage of users who submit additional requests

Cancellation Rate

Percentage of confirmed sessions canceled

No-Match Rate

Percentage of requests that expire without a compatible match

These metrics will help determine whether Climb Now solves a meaningful coordination problem.

14. Proposed Development Roadmap

Phase 1 — Product Definition

Finalize requirements.

Conduct initial user interviews.

Review competing products.

Create UI wireframes.

Define initial database models.

Phase 2 — Matching Prototype

Build basic gym and availability input.

Implement the time-overlap algorithm.

Test matching between two users.

Test overlapping and non-overlapping requests.

Handle basic edge cases.

Phase 3 — Functional MVP

Implement authentication.

Add persistent database storage.

Implement match invitations.

Add acceptance and rejection workflows.

Build session management.

Deploy a functional web application.

Phase 4 — Asynchronous Matching and Notifications

Keep unmatched requests active.

Trigger matching when new availability is submitted.

Handle invitation expiration.

Implement notifications.

Test concurrent matching behavior.

Phase 5 — User Testing

Recruit initial users.

Gather usability feedback.

Evaluate matching success.

Identify scheduling and reliability problems.

Refine the application.

Phase 6 — Potential Expansion

Add session-specific messaging.

Introduce group matching.

Support additional climbing gyms.

Improve notification delivery.

Explore intelligent scheduling recommendations.

Consider native mobile development.

These phases are flexible and depend on available time, project interest, and user feedback.

15. Future AI Opportunities

Artificial intelligence is not required for the initial product.

The core matching functionality can be implemented using deterministic algorithms.

Potential future AI applications include:

Intelligent Scheduling Recommendations

Suggest alternative time windows that may have a higher likelihood of finding compatible climbing partners.

Personalized Match Ranking

Use preferences and historical participation patterns to improve the ordering of compatible matches.

Natural Language Availability Input

Allow users to submit requests such as:

"I want to climb Thursday afternoon for about two hours."

The system could interpret the request and convert it into structured availability information.

These features should only be introduced when they provide measurable improvements over simpler solutions.

16. Project Goals and Expected Outcomes

Climb Now is currently intended as an independent personal software engineering project rather than a committed commercial startup.

The primary goals are to:

Explore a personally meaningful problem.

Practice end-to-end product development.

Design and implement a practical matching algorithm.

Develop backend APIs and database systems.

Gain experience with asynchronous workflows and notifications.

Build and deploy a functional web application.

Test the concept with potential real-world users.

Create a technically substantial portfolio project if the prototype proves useful.

