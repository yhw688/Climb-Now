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

The proposed initial testing location is **Orlando, Florida**, potentially beginning with climbers at Blue Swan Boulders.

This is a proposed pilot location, not a confirmed partnership with the gym.

Starting with a limited number of gyms would allow the project to evaluate matching performance and user adoption before expanding.

Future expansion could include additional gyms and larger metropolitan areas, depending on user interest and validation results.

## 5. Proposed User Experience

Climb Now follows an availability-first interaction model.

Users do not need to browse profiles, search for climbing partners, or initiate conversations before submitting their schedules.

### Step 1 — Set Availability

Users submit a climbing request containing:

| Field | Example | Requirement |
|---|---|---|
| Climbing Gym | Blue Swan Boulders | Required |
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

