# Global API Platform

_A next-generation multi-region, event-driven platform for the financial/fintech sector._

---

## 🚀 Objective

Design and deliver a highly-resilient API platform enabling:
- Account & transaction management
- Real-time event publishing
- Intelligent API discovery
- Semantic observability
- Hybrid cloud-ready deployments

---

## 🛠️ Architecture Overview

### High-level architecture diagram:
```
+-------------------+       +-------------------+       +-------------------+
|   API Gateway     |       |   Event Backbone   |       |   Observability   |
|   (Kong)          |       |   (Kafka)         |       |   (OpenTelemetry) |
+-------------------+       +-------------------+       +-------------------+
        |                       |                       |
        v                       v                       v
+-------------------+       +-------------------+       +-------------------+
|   Accounts API    |       |   Payments API    |       |   Transaction     |
|   Transaction API  |       |   Event Streaming  |       |   Ledger API      |
+-------------------+       +-------------------+       +-------------------+
        |                       |                       |
        v                       v                       v
+-------------------+       +-------------------+       +-------------------+
|   Multi-Region    |       |   Hybrid Cloud     |       |   AI-Native       |
|   Deployment      |       |   Platform         |       |   Observability   |
+-------------------+       +-------------------+       +-------------------+
```


The platform is organized into the following core modules:

### 1. **API Layer (Contract-First)**

- **OpenAPI 3.x** for HTTP API contracts
- **AsyncAPI** for asynchronous/event specifications
- **Semantic versioning** for all APIs
- **API Gateway:** Kong

**Primary APIs:**
- `Accounts API`
- `Payments API`
- `Transaction Ledger API`
- `Event Streaming API`

**Security:**
- OAuth 2.1
- JWT validation
- Internal mTLS (mutual TLS)

---

### 2. **Event-Driven Core**

- **Event Backbone:** Apache Kafka for distributed messaging
- **Event Types:**
  - `accounts.created`
  - `payments.authorized`
  - `transactions.settled`
  - `fraud.detected`

---

### 3. **Multi-Region Deployment Model**

- **Regions Simulated:** EU, APAC
- **Deployment Patterns:**
  - Active-Active data replication
  - Kafka replication across regions
  - Automatic regional failover
  - Intelligent API routing (geolocation-aware)
- **IaC:** Terraform

---

### 4. **Hybrid Cloud Platform**

- Deploys to:
  - **Google Cloud Platform (GCP)**
  - **Microsoft Azure**

---

### 5. **Kubernetes & GitOps**

- **Orchestration:** Kubernetes
- **GitOps Deployment:** ArgoCD
- **CI/CD Automation:** GitHub Actions
  - Lint OpenAPI specs
  - Contract testing
  - Docker image build/push
  - Security scanning
  - Automated deployment via GitOps

---

### 6. **AI-Native Observability**

- **Telemetry:** OpenTelemetry (Java)
- **Tracing:** Jaeger
- **Metrics:** RED method
- **Logging:** JSON structured logs
- **Alert Simulation:**
  - High latency
  - 5xx error rates

  Features: 
  - AI-driven anomaly detection for proactive monitoring
  - Semantic monitoring (e.g., rejected transactions, fraud patterns)

---

## API Usage Examples

### Accounts API
```http
POST /accounts
Content-Type: application/json

{
  "accountHolderName": "John Doe",
  "accountType": "savings",
  "initialDeposit": 1000
}
```

### Payments API
```http
POST /payments
Content-Type: application/json

{
  "fromAccountId": "12345",
  "toAccountId": "67890",
  "amount": 250,
  "currency": "USD"
}
```


---
### Event Streaming API
```http
POST /events
Content-Type: application/json

{
  "eventType": "payments.authorized",
  "payload": {
    "paymentId": "abc123",
    "amount": 250,
    "currency": "USD",
    "timestamp": "2024-06-01T12:00:00Z"
  }
}
```


