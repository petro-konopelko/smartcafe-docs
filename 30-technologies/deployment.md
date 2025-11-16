# Deployment — SmartCafe

This document outlines deployment options and steps for SmartCafe.

---

## Phased Approach

- Phase 1 (Now): Azure App Service (cheapest path for MVP)
- Phase 2 (Future): Azure Kubernetes Service (AKS) desired state

---

## Phase 1 — Azure App Service (MVP)

### Components

- App Service (Linux) for Menu Service API
- App Service (Linux) for Order Service API
- App Service (Linux) for Angular frontend (or Azure Static Web Apps as an alternative)
- Azure Blob Storage for menu images
- Azure ServiceBus for events
- Azure PostgreSQL or Azure SQL

### App Settings (examples)

- APIs
  - `ConnectionStrings__Db`: database connection string
  - `Storage__BlobConnection`: blob connection string (or use Managed Identity)
  - `ServiceBus__Connection`: Service Bus connection string
  - `Images__BaseUrl`: public blob base URL for images
- Frontend
  - `API_BASE_URL`: API gateway/base endpoint

### Recommended SKUs (cost-driven)

- App Service (Linux) B1 for APIs, F1/B1 for frontend (or Static Web Apps Free/Basic)
- Azure PostgreSQL Flexible Server (Burstable) or Azure SQL Basic
- Service Bus Basic/Standard (choose Standard if topics are needed)
- Storage Account: Standard GPv2 with Hot tier

### High-Level Steps

1. Create resource group and core resources (Storage, Service Bus, DB)
2. Create App Services for Menu and Order APIs; configure app settings
3. Deploy .NET APIs (zip deploy, GitHub Actions, or Azure DevOps)
4. Create App Service for Angular or use Static Web Apps; deploy built artifacts
5. Point frontend to API base URL; verify CORS
6. Test image upload/read from Blob Storage

---

## Phase 2 — AKS (Desired State)

- See [AKS Desired State](../20-architecture/aks-desired-state.md)

Key additions:

- ACR for images, Ingress (NGINX), cert-manager for TLS
- Key Vault CSI Driver for secrets; KEDA for autoscaling
- GitHub Actions for image build/deploy and manifests rollout

---

## References

- [App Service Deployment](./app-service-deployment.md)
- [Technologies Overview](./README.md)
- [Architecture Overview](../20-architecture/README.md)
- [AKS Desired State](../20-architecture/aks-desired-state.md)
