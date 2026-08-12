# Example DevOps Projects: From Home Lab to Freelance-Ready

These are structured roughly by difficulty and realism — start with the portfolio-building ones to learn the tools, then use the "client-shaped" ones as templates for what an actual 8-hrs/week freelance engagement might look like.

---

## 1. CI/CD Pipeline for a Simple Web App (Portfolio project)
**Scenario:** You have (or build) a small web app — even a basic Node.js/Python API — and set up a full pipeline that tests, builds, and deploys it automatically on every code push.

**Tech stack:** GitHub Actions (easiest starting point) or GitLab CI, Docker, a free-tier cloud target (Render, Railway, or a small AWS/Azure instance)

**Deliverables:**
- Pipeline that runs automated tests on every push
- Automatic Docker image build and push to a registry (Docker Hub or GitHub Container Registry)
- Automatic deployment to a staging environment on merge to main

**Time estimate:** 15–20 hours total (2–3 weeks at 8 hrs/week)

**Skills demonstrated:** YAML pipeline authoring, Docker basics, environment variables/secrets management, understanding build vs. deploy stages

---

## 2. Infrastructure as Code: Reproducible Cloud Environment
**Scenario:** Take an environment you'd normally click together manually in a cloud console (a VM, a database, a load balancer, networking rules) and define it entirely in code so it can be destroyed and recreated identically.

**Tech stack:** Terraform, one cloud provider (AWS or Azure — Azure is worth prioritizing given NL/EU enterprise usage), remote state storage (S3 or Azure Blob)

**Deliverables:**
- A `terraform apply` that stands up a working environment from scratch
- Remote state configured (not just local state files)
- A README documenting variables, inputs, and how to tear it down safely

**Time estimate:** 20–25 hours

**Skills demonstrated:** IaC fundamentals, cloud provider basics, state management, the discipline of "everything is code, nothing is a manual click"

---

## 3. Containerize and Orchestrate an Existing Application
**Scenario:** Take an application with multiple parts (e.g., a web frontend, an API backend, and a database) and get it running as properly orchestrated containers rather than manually installed services.

**Tech stack:** Docker Compose (for local/small-scale), optionally graduate to a minimal Kubernetes setup (k3s or a managed service's free tier) once comfortable

**Deliverables:**
- Working `docker-compose.yml` with all services networked correctly
- Persistent data handled properly (volumes, not ephemeral containers losing data)
- Basic health checks configured

**Time estimate:** 15–20 hours for Compose; add 15+ more hours if extending to Kubernetes

**Skills demonstrated:** Container networking, volume/persistence concepts, multi-service orchestration — this is close to what a small client project ("dockerize our app") would actually look like

---

## 4. Monitoring & Observability Setup (Client-shaped project)
**Scenario:** A small company has an application running but no visibility into its health — no dashboards, no alerts when something breaks. You're brought in to fix that as a defined, time-boxed engagement.

**Tech stack:** Prometheus (metrics collection) + Grafana (dashboards), plus basic alerting (via email/Slack webhook)

**Deliverables:**
- Metrics collection running against the target application/infrastructure
- A dashboard showing key health indicators (CPU/memory, request rates, error rates)
- At least one working alert rule (e.g., "notify if error rate exceeds X%")
- Documentation so the client's team can maintain it after you leave

**Time estimate:** 25–30 hours (realistic as a genuine 3–4 week part-time engagement)

**Skills demonstrated:** This is a very realistic template for actual freelance work — scoped, deliverable-based, no ongoing ownership required after handoff. Good example of "project-shaped, not standby-shaped" work.

---

## 5. Cloud Migration / Environment Setup (Larger client-shaped project)
**Scenario:** A small business wants to move a manually-managed on-prem or single-VM setup into a properly structured cloud environment — this mirrors real small-business/startup asks.

**Tech stack:** Terraform or Bicep (Azure) for infrastructure, GitHub Actions/Azure DevOps for deployment automation, basic networking/security group setup

**Deliverables:**
- Migrated (or newly built) environment in the cloud, defined as code
- CI/CD pipeline so future deployments don't require manual steps
- A basic runbook: how to deploy, how to roll back, where logs live

**Time estimate:** 40+ hours — likely your first real multi-week engagement rather than a weekend project

**Skills demonstrated:** This is close to what a genuine first paid client engagement looks like — scoped, has a clear "done" state, and doesn't require you to be on call afterward as long as you're clear about scope ("I build and hand off, I don't operate this long-term") in your agreement.

---

## How to use these as a learning sequence

| Order | Project | Why here |
|---|---|---|
| 1 | CI/CD Pipeline | Fastest feedback loop, teaches core tools |
| 2 | Containerize an app | Builds directly on project 1 |
| 3 | Infrastructure as Code | Adds the "cloud environment" dimension |
| 4 | Monitoring/Observability | Teaches you to think about *operating* systems, not just building them |
| 5 | Cloud Migration | Combines everything above into a realistic client engagement |

## A note on scoping real client work
Projects 4 and 5 above are deliberately written the way you'd want to *pitch* actual freelance work: a defined deliverable, a documented handoff, and an explicit boundary that you're not providing ongoing operational support. When you eventually talk to a real client, use this same framing — "I'll build X, document it, and hand it off" — to keep the engagement project-shaped rather than accidentally becoming an unpaid on-call resource.
