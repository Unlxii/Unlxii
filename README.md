# Ronnachai Sitthichoksathit

**Platform Engineering · DevSecOps · Cloud Infrastructure**

Computer Engineering Graduate — Chiang Mai University (2026)
Open to Cloud Engineer, DevOps Engineer, and Platform Engineer roles · on-site or Remote

[LinkedIn](https://linkedin.com/in/tent-ronnachai) · ronnachaisitti@gmail.com | temt.ronnachai@outlook.com

---

## About

I design and operate CI/CD pipelines, container infrastructure, and cloud-provisioned environments. My
focus is on building systems that are reproducible, observable, and secure by default — from the first
`git push` to a verified image in production.

During my internship at CMU's IT Services Centre (ITSC), I led a GitOps migration to ArgoCD that reduced
manual deployment steps by approximately 80% and delivered zero-downtime rollouts across three
microservices running on an on-premise Kubernetes cluster.

My capstone project, VisScan, is a production-deployed DevSecOps platform that runs an 8-stage GitLab CI
pipeline on every code push — running Gitleaks, Semgrep, and Trivy in parallel, building container images
with Kaniko, and blocking promotion of any image carrying unresolved CRITICAL CVEs through a hard-gated
release stage.

---

## Core Competencies

| Domain | Tools and Technologies |
|---|---|
| CI/CD and GitOps | GitLab CI/CD, GitHub Actions, ArgoCD |
| Containers and Orchestration | Docker, Kubernetes, Kaniko |
| Infrastructure as Code | Terraform (AWS), Docker Compose |
| Cloud | AWS (VPC, EC2, RDS, IAM, S3), Huawei Cloud |
| Message Queues | RabbitMQ (priority queues, dead-letter queues) |
| Databases | PostgreSQL 15, Prisma ORM |
| Application Layer | Next.js 16, tRPC, Node.js, TypeScript |
| DevSecOps | Trivy, Semgrep, Gitleaks, Cosign, OpenTelemetry |
| Scripting | Bash, Python |

---

## Featured Work

### VisScan — DevSecOps Scanning Platform
[github.com/Unlxii/VisScan](https://github.com/Unlxii/VisScan)

An open-source SaaS platform that automates container security scanning across an 8-stage GitLab CI
pipeline. Engineers trigger scans from a web dashboard; a TypeScript worker consumes jobs from a
RabbitMQ priority queue, fires a GitLab pipeline trigger, and streams live stage progress back to the
browser via Server-Sent Events.

Key technical decisions:
- Daemon-less Kaniko builds allow container image construction inside a rootless runner environment
  without requiring Docker-in-Docker
- Dual-lane RabbitMQ queues (`scan_jobs_build` / `scan_jobs_scan`) with per-channel `prefetch(5)` and a
  worker-side concurrency gate prevent runner oversubscription
- AES-256-CBC encryption of all stored Git and Docker credentials, decrypted only in-memory at job
  construction time
- Verified Release Gate blocks image promotion if Trivy reports any CRITICAL-severity CVEs; a CycloneDX
  SBOM is generated as a pipeline artifact on every successful build
- OpenTelemetry instrumentation activates via environment variable with zero code changes

**Stack:** Next.js 16 · tRPC · TypeScript · RabbitMQ · PostgreSQL · GitLab CI · Kaniko · Trivy · Semgrep ·
Gitleaks · Cosign · Docker Compose

---

<!-- ### terraform-aws-demo — AWS Infrastructure as Code
[github.com/Unlxii/terraform-aws-demo](https://github.com/Unlxii/terraform-aws-demo)

Modular Terraform configuration for provisioning a production-ready AWS environment. Demonstrates remote
state management with S3 backend and DynamoDB locking, IAM least-privilege role definitions, and
parameterized module composition.

**Stack:** Terraform · AWS (VPC · EC2 · RDS · IAM · S3) -->

---

## Certifications

| Certification | Status |
|---|---|
| AWS Solutions Architect Associate (SAA-C03) | In Preparation |
| AWS Cloud Practitioner | Earned |
| Huawei HCCDA Tech Essentials | Earned |
| Linux Essentials (Cisco) | Earned |

---

## Currently Working On

- AWS SAA-C03 exam preparation
- Extending VisScan with a `LOCAL_DEMO_MODE` for offline evaluation
- Exploring Helm chart packaging for VisScan's production deployment

---

*Open to Cloud Engineer, DevOps Engineer, and Platform Engineer roles in Bangkok or remote.*
*ronnachaisitti@gmail.com · tent.ronnachai@outlook.com*
