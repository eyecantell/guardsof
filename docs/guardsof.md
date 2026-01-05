# Guardsof.com: Guardian Operations Hub

## Purpose
A secure, internal platform for Guardians to manage proactive outreach, track conversations ethically, share anonymized learnings ("iron sharpens iron"), and build a supportive community. It centralizes AI-assisted tools while ensuring all engagements remain human-led, empathetic, and focused on helping people find hope and local church fellowship.

## Key Features
- **Conversation Queue**:
  - AI-curated list of public posts (starting with X.com API) flagged for signals of isolation, struggle, or need.
  - Human curation required: Guardians review and provide feedback on queue item quality (e.g., false positives, sarcasm handling) to continuously refine accuracy.
  - Previews are anonymized; full context accessed only via public deep links (e.g., direct URL to open post in native app).

- **Opener Suggestions**:
  - AI-generated starters tailored to post context, categorized by style (validation-first, encouragement, question-based, etc.).
  - Designed for experimentation: Guardians tag engagements by displayed situation/attitude to build data-informed best practices over time.
  - Workflow: Guardian selects/edits opener → clicks prominent "Copy Message" button → uses provided "Open Post in App" deep link for manual paste/reply in native social app.

- **CRM Integration**:
  - Track conversations with explicit recipient consent only.
  - Log opening styles, situation tags, outcomes (e.g., response received, resource shared, church interest expressed).
  - Auto-detection of sent outreach: After "Copy Message", create pending record; scheduled backend checks (via guardian read-only OAuth) scan timeline for matching reply → capture exact sent text/timestamp and confirm status.
  - Optional anonymized follow-up survey links for recipients to share impact (e.g., church connections).
  - Schedule reminders for gentle follow-ups with pre-filled suggestions and direct links to conversation threads.

- **Iron Sharpens Iron Section**:
  - Share fully anonymized conversation logs (links preferred over transcripts; names/locations redacted).
  - Guardians award sprout 🌱 ratings for "good seed" examples and provide constructive, encouraging feedback.
  - Moderated to ensure sensitivity, compliance, and positivity.

- **Manual Uploads**:
  - Form for submitting public post links or redacted excerpts.
  - Required TOS compliance checklist and moderator review before sharing.

- **Hashtag Tracking**:
  - Monitor #nowfree across platforms to automatically pull Guardian-initiated chats into the queue/CRM for learning and celebration.

- **Analytics Dashboard**:
  - Track opener style success by situation (response rates, conversation depth, church connections).
  - Queue accuracy trends from guardian feedback.
  - Overall impact metrics: engagements leading to nowfree.org visits, reported church connections, survey responses, and outreach confirmation rates.

## Guardian Support & Community
- **Recruitment**:
  - Begin with volunteers from local church (Woodland Park pilot).
  - Expand through partnerships with like-minded churches benefiting from referred new members.
  - Future: targeted ads or broader recruitment once proven.

- **Onboarding & Growth**:
  - Start informal: in-person meetings, phone/video calls to brainstorm ideas, share successes/failures, and pray together.
  - Include one-time optional X account connection via OAuth (read-only scopes) – clearly explained benefits: automatic logging of sent messages for accurate metrics, reduced manual entry, and better team learning.
  - Scale to structured video training series covering ethics, empathy, opener styles, manual copy/paste workflow, burnout prevention, and OAuth connection.
  - Form small encouragement groups for ongoing story-sharing, debriefing, and mutual support.

## Design Principles
- **Security & Privacy**: Login required; data encrypted (especially OAuth tokens); minimal storage (links over full transcripts); full anonymization for sharing.
- **Usability**: Mobile-first Flutter interface; intuitive queue selection and feedback forms with prominent copy/deep-link buttons.
- **Ethics First**: Built-in consent prompts, TOS disclaimers, moderation queues, and guardian wellness checks.
- **Scalability**: Modular architecture for adding platforms (Reddit, Nextdoor) and campaigns; human oversight remains central; future hooks for semi-automated posting.

## Development Plan
- **Phase 1**: X.com API queue, basic CRM, opener suggestions with manual copy/paste and deep links, discussion board with sprout ratings.
- **Phase 2**: Read-only OAuth integration for auto-detection of sent replies, enhanced feedback forms (queue quality + situation tagging), manual uploads, hashtag tracking refinements, timed follow-up reminders.
- **Phase 3**: Advanced analytics for best-practice insights, video onboarding integration, multi-platform support, and preparation for optional semi-automated posting.

## Safeguards
- Comprehensive training on ethical outreach, emotional validation, and handling difficult responses.
- Burnout prevention through workload caps, small groups, and anonymous wellness check-ins.
- Moderation team to review shared content and ensure ongoing TOS/privacy compliance.
- Iterative improvements driven by real guardian experience and wisdom from established ministries.

*Updated: December 23, 2025 – Reflects emphasis on church connections as primary impact, human-curated AI refinement, guardian community support evolution, and situation-based experimentation.*

*Updated: January 04, 2026 – Fully incorporated manual copy/paste MVP workflow with deep links, read-only OAuth for auto-logging sent replies, updated CRM/follow-up flow, onboarding details, and future automation hooks while preserving original structure and emphasis on human-centered, ethical design.*