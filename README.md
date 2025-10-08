# Middle Full-Stack engineer test assessment - Description of the BE + FE Application Architecture

### 🏗️ System Architecture (Mermaid)

```mermaid
graph TD

A[Client Application] --> B[Client SDK]
B -->|HTTP/gRPC| C[API Gateway]
C --> D[Ingestion Service]
D --> E[Message Queue (Kafka/Kinesis)]
E --> F[Processing Workers]
F --> G1[(Hot Storage: Elasticsearch)]
F --> G2[(Primary DB: Cassandra / DynamoDB)]
F --> G3[(Cold Storage: S3 / GCS)]
G1 --> H[Backend API]
H --> I[Web Dashboard (React/Next.js)]
F --> J[Alert Service]
J --> K[Email/Slack/Webhook]
subgraph DevOps
L[Monitoring: Prometheus/Grafana]
M[CI/CD: GitHub Actions]
N[Deployment: Kubernetes / ECS]
end
F --> L
