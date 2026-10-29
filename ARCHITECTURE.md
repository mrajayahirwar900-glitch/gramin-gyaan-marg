```markdown
# 🏗️ Technical Design Document: Gramin Gyaan Marg

## 1. System Overview
Gramin Gyaan Marg is a high-availability, low-latency web platform engineered for users in low-bandwidth rural environments. It facilitates seamless access to educational guidance, government scholarship matching, and peer mentorship.

---

## 2. Architecture Diagram (Mermaid.js)

```mermaid
graph TD
    %% User Tier
    subgraph Client Tier [Rural User / Mobile Devices]
        A[Mobile Web Browser] -->|HTTPS Request| B[React Single Page App]
        B -->|Service Worker| C[Offline Cache]
    end

    %% Gateway Tier
    subgraph Gateway Tier
        B -->|REST API Requests| D[Express API Gateway]
        D -->|Auth Middleware| E[JWT Validator]
    end

    %% Application Tier
    subgraph Application Service Tier
        E --> F[User Management Service]
        E --> G[Scholarship Matcher Service]
        E --> H[Educational Roadmap Engine]
        E --> I[Mentorship Q&A Module]
    end

    %% Data Tier
    subgraph Database Tier
        F --> J[(MongoDB Atlas / PostgreSQL)]
        G --> J
        H --> J
        I --> J
