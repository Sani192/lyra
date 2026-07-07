# Deployment Architecture

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design and specifications for Lyra deployments and scaling models.

## Purpose

Define the target deployment topology, sizing models, horizontal scaling triggers, and containerization constraints needed to run Lyra in high-concurrency production cloud environments.

## Cluster Topology

Lyra runs as a containerized microservices platform deployed onto standard managed Kubernetes services (e.g., GKE, EKS, AKS). The deployment is segregated across namespaces to enforce strict tenant boundary controls at the network and resource levels.

```
                  +-------------------------------------------------+
                  |               Ingress (TLS 1.3)                 |
                  +------------------------+------------------------+
                                           | Routing
                                           v
+-------------------------------------------------------------------+
| Kubernetes Cluster                                                |
|                                                                   |
|  +-------------------------------------------------------------+  |
|  | Namespace: lyra-system                                      |  |
|  |                                                             |  |
|  |  +-----------------+   +------------------+   +----------+  |  |
|  |  | ProtocolAdapter |   | ConversationEng. |   | Workflow |  |  |
|  |  +--------+--------+   +--------+---------+   +-----+----+  |  |
|  |           |                     |                   |       |  |
|  |           v                     v                   v       |  |
|  |  +-----------------+   +------------------+   +----------+  |  |
|  |  | CapRegistry Pod |   | Redis (Metadata) |   | Observa. |  |  |
|  |  +-----------------+   +------------------+   +----------+  |  |
|  +-------------------------------------------------------------+  |
|                                                                   |
+-------------------------------------------------------------------+
```

### 1. Kubernetes Namespace Structure
* **`lyra-system`:** Scopes the core operational components: Protocol Adapters, Conversation Engine, Workflow Engine, Capability Registry, and Observability services.
* **`lyra-tenant-apps`:** (Optional / Integration Testing) Host mock consumer services and test endpoints isolated from core platform runtimes via Kubernetes NetworkPolicies.

### 2. Service Sizing Guidelines
To maintain latency targets under concurrent load, the core pods require dedicated resource allocations:

| Component | Target Replicas | Min CPU | Max CPU | Min Memory | Max Memory |
| --- | --- | --- | --- | --- | --- |
| **Protocol Adapter** | 2 - 10 | 500m | 2.0 | 512Mi | 2Gi |
| **Conversation Engine** | 2 - 10 | 1.0 | 4.0 | 1Gi | 4Gi |
| **Capability Registry** | 2 - 5 | 250m | 1.0 | 256Mi | 1Gi |
| **Workflow Engine** | 2 - 8 | 500m | 2.0 | 512Mi | 2Gi |

### 3. Scaling Rules & Metrics
Horizontal Pod Autoscaler (HPA) policies are triggered on two vectors:
* **Protocol Adapter & Conversation Engine:** Scaled based on **concurrent WebSocket connection streams** (target: max 1,000 active streams per pod) and CPU utilization (target: 70% threshold).
* **Workflow & Registry Services:** Scaled based on standard CPU and Memory utilization thresholds (target: 80% threshold).

### 4. Container Image Policy
All platform services are compiled using multi-stage Dockerfiles. The production stages must:
* Use minimal base images (e.g., Python 3.11-slim or Google Distroless Python images) to reduce vulnerability surfaces.
* Exclude root user execution; containers run as a non-privileged `lyra` user (UID 10001).
* Pass vulnerability scanner audits (e.g., Trivy or Grype) with zero "Critical" or "High" findings before registration in private artifact stores.
