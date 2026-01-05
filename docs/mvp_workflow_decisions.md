# MVP Workflow Decisions: Guardians of Fellowship

## Overview
This document captures key technical and workflow decisions for the Minimum Viable Product (MVP) of guardsof.com, based on iterative planning and risk assessment. The focus is on launching a simple, ethical, and effective pilot in Woodland Park, CO, while preserving the core mission: AI-assisted queue curation, human-led empathetic outreach, and data-informed refinement of best practices.

These decisions prioritize speed to pilot, low development complexity, minimal costs, full TOS/privacy compliance, and guardian familiarity-while maintaining hooks for future automation and scaling.

## Key Decisions

### 1. Initial Outreach Workflow: Manual Copy/Paste with Deep Links
- Guardians review AI-curated queue items and suggested openers.
- On selection/edit: Prominent "Copy Message" button copies the tailored opener.
- System provides a deep link to the original post (e.g., `https://x.com/username/status/POST_ID`) with an "Open Post in App" button for seamless navigation in the native X app (mobile-first).
- Guardian pastes the message manually into the native app and posts the reply.
- Rationale: Eliminates posting automation risks (e.g., spam detection, app review delays); leverages guardians' existing familiarity with native apps; ensures 100% human tone and timing.

### 2. Auto-Logging of Sent Outreach via Read-Only Guardian OAuth
- During onboarding, guardians optionally authorize one-time OAuth 2.0 connection to their X account (minimal scopes: `tweet.read`, `users.read`, `offline.access`).
- Backend securely stores encrypted access token and refresh token (access expires ~2 hours; refresh is long-lived until revoked; auto-refresh handled server-side).
- When guardian clicks "Copy Message": Create pending CRM record with target post ID.
- Scheduled backend jobs (e.g., hourly via Celery) check the guardian's recent timeline for replies matching the target post ID (`in_reply_to_tweet_id`).
- On match: Auto-capture exact sent text, timestamp, and media; update CRM to "confirmed"; enable accurate metrics without manual re-entry.
- Fallback: Manual confirmation button if detection misses (e.g., quote tweets).

### 3. Defer Semi-Automated Posting and Third-Party Unified APIs
- No direct posting via app in MVP (no write scopes or third-party services like Ayrshare/Late).
- Future (Phase 3+): Add optional "Approve & Send" button (human review required → app posts via API) once pilot proves workflows and impact.
- Third-party unified APIs evaluated but deferred to scaling phase (when 20+ guardians and higher volume justify ~$30-500/month costs).

### 4. CRM and Follow-Up Preparation
- On outreach start (post-"Copy Message"): Auto-create CRM record with tags (situation, opener style).
- Schedule timed reminders (e.g., 3-7 days) with pre-filled follow-up suggestions and deep links to the conversation thread.
- Guardians handle follow-ups manually via copy/paste.

## Rationale
- **Lower Risk**: Zero automation in posting avoids TOS violations, bot detection, or intrusive appearance.
- **Faster MVP Launch**: Reduces dev effort (no complex posting OAuth, token management per action, or platform app reviews); focuses on core value (AI queue + openers).
- **Cost Savings**: Initial X API needs only read-focused Basic tier (~$100/month shared); no per-guardian premiums required early.
- **Guardian-Centric**: Manual paste feels natural and authentic; auto-logging reduces burden while improving data quality for sprout ratings and analytics.
- **Ethical Alignment**: Full human oversight; consent-based OAuth; only public/guardian-owned data accessed.
- **Data-Driven Evolution**: Still captures rich metrics (confirmed sends, response rates, opener effectiveness) for iterative improvements.

## Future Evolution
- **Phase 3**: Introduce semi-automated posting (add write scopes or third-party integration) based on pilot feedback.
- **Phase 4**: Multi-platform support (guardian choice: Instagram/Facebook/TikTok) with similar hybrid workflows.
- Revisit as guardian count grows and church partnerships provide funding/validation.

*Created: January 04, 2026 – Documenting MVP decisions for manual copy/paste workflow, read-only OAuth auto-logging, and deferred automation to ensure rapid, compliant pilot launch.*