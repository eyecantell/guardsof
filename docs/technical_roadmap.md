# Technical Roadmap: Building Guardsof.com and Nowfree.org with Flutter and FastAPI

## Purpose
To outline the development plan for guardsof.com (Guardian operations hub) and nowfree.org (public Gospel resource site) using Flutter for cross-platform frontend and FastAPI for a scalable backend, prioritizing an MVP for Woodland Park, CO, with scalability to thousands of simultaneous users.

## Core Technologies
- **Frontend**: Flutter (Dart) for cross-platform UI (mobile, web, desktop); Material Design for responsive, accessible interfaces.
- **Backend**: FastAPI (Python) for async, lightweight APIs; integrates with AI for queue scanning and opener suggestions.
- **Database**: PostgreSQL (via Supabase/Neon) for CRM and resource storage; Redis for caching high-read data.
- **AI**: Python-based models (e.g., Hugging Face’s BERT, xAI’s Grok via API) for sentiment analysis and opener suggestions.
- **Integrations**: X.com API for queue/#nowfree tracking; Airtable/HubSpot for CRM; Firebase Analytics for user insights.
- **Hosting**: AWS/GCP with free tiers for MVP; auto-scaling for growth.

## Phase 1: Planning and Prototyping (1-2 months)
- **Tasks**:
  - Wireframe guardsof.com (queue, CRM dashboard, discussion board) and nowfree.org (Gospel walkthrough, resource search) using Flutter’s Material widgets.
  - Define data schema: anonymized conversation logs, opener styles, resource metadata (Pydantic for validation).
  - Secure X.com API developer account; validate TOS-compliant pulling for #nowfree and keyword scans.
  - Partner with Woodland Park churches for initial resource list.
  - Plan scalability: Modular Flutter architecture (feature modules, Riverpod state); async FastAPI endpoints; Docker setup.
- **Deliverables**:
  - Flutter mockups for both sites.
  - Ethical data policy (Pydantic schemas for anonymization).
  - Church partner list for nowfree.org.

## Phase 2: MVP Build (2-3 months)
- **Guardsof.com**:
  - Build Flutter UI: Queue page (ListView.builder for posts), CRM integration (Airtable/HubSpot via API), discussion board with sprout (🌱) ratings.
  - Implement manual upload form with TOS compliance checklist; use Flutter’s `http` for X.com API pulls.
  - Develop FastAPI backend: Async endpoints for queue (X.com posts), CRM logging, and AI-driven opener suggestions (e.g., validation-based: "I hear you").
  - Use PostgreSQL for logs/resources; Redis for caching queue data.
- **Nowfree.org**:
  - Static Flutter site: Gospel walkthrough, next steps, Woodland Park church list; mobile-optimized with semantics for accessibility.
  - Integrate Firebase Analytics for anonymized click tracking (e.g., resource clicks).
- **Scalability Setup**:
  - Deploy with Docker + Gunicorn/Uvicorn for FastAPI; AWS Amplify for Flutter apps/web.
  - Use async FastAPI endpoints; connection pooling (PgBouncer) for DB.
  - Optimize Flutter: Lazy-load queue data, code-split for web performance.
- **Testing**:
  - Pilot with small Guardian group (you and wife); manual scans to validate AI.
  - Test with Locust for 1K concurrent users; profile Flutter Web with DevTools.

## Phase 3: Testing and Iteration (Ongoing)
- **Tasks**:
  - Refine AI accuracy (queue flagging, opener suggestions) using sprout ratings and Guardian feedback.
  - Enhance #nowfree hashtag tracking via FastAPI async endpoints.
  - Add moderation for shared logs; expand CRM with opener style analytics (response rates, depth).
  - Optimize Flutter: Offline storage (Hive) for mobile; CDN (Cloudflare) for nowfree.org assets.
  - Stress-test scalability: Simulate 5K users with Locust; monitor with Prometheus/Grafana.
- **Deliverables**:
  - Updated queue with improved AI filters.
  - Analytics dashboard for style success and engagement metrics.

## Phase 4: Scaling
- **Tasks**:
  - Integrate additional platforms (Reddit, Nextdoor APIs) with FastAPI endpoints.
  - Add campaign modules (e.g., voting awareness) with Guardian opt-ins via Flutter profiles.
  - Expand nowfree.org: Multilingual support, dynamic resource search (ZIP code filter).
  - Scale FastAPI with Kubernetes/ECS auto-scaling; add Celery for heavy AI tasks.
  - Grow Guardian community via online recruitment (e.g., inspired by Need Him).
- **Deliverables**:
  - Multi-platform queue; campaign-specific UIs in Flutter.
  - Regional resource database beyond Woodland Park.

## Budget and Resources
- **Initial**: AWS/GCP free tiers (Amplify for Flutter, Elastic Beanstalk for FastAPI); open-source AI (Hugging Face) to keep costs ~$0-50/month.
- **Scaling**: Budget $100-500/month for 100K users (auto-scaling, DB, CDN). Seek church grants for hosting/AI compute.
- **Partnerships**: Collaborate with Nerdy Nonprofit for AI setup; churches for resource vetting.

## Scalability Plan
- **Horizontal Scaling**: Multiple FastAPI instances (Gunicorn + Uvicorn, 4-8 workers); load balance with NGINX/AWS ELB for 10K+ concurrent users.
- **Caching**: Redis for queue/resources; Cloudflare CDN for nowfree.org static assets.
- **Performance**: Async FastAPI endpoints; Flutter code splitting, lazy loading. Offload AI to Celery workers.
- **Monitoring**: Prometheus/Grafana for metrics (requests/sec, CPU); Firebase for user behavior.
- **Modularity**: Feature-based Flutter modules; microservice-ready FastAPI to avoid rewrites.

## Success Metrics
- 100% uptime and X.com API TOS compliance.
- 5-10 active Guardians in pilot; scale to 1K users without performance degradation.
- High resource click-throughs on nowfree.org; sprout-rated conversations for quality.