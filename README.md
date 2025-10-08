# Middle Full-Stack engineer test assessment - Description of the BE + FE Application Architecture

## Task overview

You need to prepare a document describing how you would design an error logging service from scratch. Explain which technologies you would choose for the client library (SDK), backend API, database, web dashboard, and DevOps solution, and justify why these choices are optimal. Additionally, compile a list of questions you would ask the client to better understand the project requirements and expectations.

### 🏗️ System Architecture

```mermaid
graph TD
flowchart LR
    subgraph Client Side
        A[Client Application]
        B[Client SDK]
    end

    subgraph API Service
        C[API Gateway]
        D[Auth + REST API (Nest.js)]
        E[(RabbitMQ Producer)]
    end

    subgraph Worker Service
        F[(RabbitMQ Consumer)]
        G[Processing Logic]
        H[Google Spanner]
        I[Elasticsearch]
        J[Alert Service]
    end

    subgraph Frontend
        K[Web Dashboard (Next.js)]
    end

    subgraph DevOps
        L[Monitoring: Prometheus + Grafana]
        M[CI/CD: GitHub Actions]
        N[Deployment: Kubernetes]
    end

    %% Flows
    A --> B --> C --> D --> E
    E --> F --> G --> H
    G --> I
    G --> J
    K --> D
    J --> K
    G --> L
```
