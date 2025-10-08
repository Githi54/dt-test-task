# Middle Full-Stack engineer test assessment - Description of the BE + FE Application Architecture

## Task overview

You need to prepare a document describing how you would design an error logging service from scratch. Explain which technologies you would choose for the client library (SDK), backend API, database, web dashboard, and DevOps solution, and justify why these choices are optimal. Additionally, compile a list of questions you would ask the client to better understand the project requirements and expectations.

### 🏗️ System Architecture
```mermaid
flowchart LR
    %% === Client Side ===
    subgraph CLIENT[Client Side]
        A[Client Application]
        B[Client SDK]
    end

    %% === API Service ===
    subgraph API[API Service]
        C[API Gateway]
        D[Auth + REST API: Nest.js]
        E[(RabbitMQ Producer)]
    end

    %% === Worker Service ===
    subgraph WORKER[Worker Service]
        F[RabbitMQ Consumer]
        G[Processing Logic]
        H[Google Spanner]
        J[Alert Service]
    end

    %% === Frontend ===
    subgraph FRONTEND[Web Dashboard]
        K[Next.js Dashboard]
    end

    %% === DevOps ===
    subgraph DEVOPS[DevOps]
        L[Monitoring: Prometheus + Grafana]
        M[CI/CD: GitHub Actions]
        N[Deployment: Kubernetes]
    end

    %% === Data Flows ===
    A --> B --> C --> D --> E
    E --> F --> G --> H
    G --> J
    K --> D
    J --> K
    G --> L
```
