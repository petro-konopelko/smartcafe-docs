# Azure App Service Deployment — SmartCafe

Step-by-step guide to deploy SmartCafe to Azure App Service (Phase 1).

---

## Prerequisites

- Azure subscription and CLI authenticated
- Resource group created (e.g., `rg-smartcafe-dev`)

---

## Create Core Resources

- Storage Account for images (Blob service)
- Service Bus namespace and queue/topic
- Database: Azure PostgreSQL Flexible Server or Azure SQL

---

## Deploy Backend APIs (.NET)

- Create two App Services (Linux) for `menu-api` and `order-api`
- Configure App Settings:
  - `ConnectionStrings__Db`
  - `ServiceBus__Connection`
  - `Images__BaseUrl`
  - Optional: Managed Identity for Storage & DB access
- Deploy with GitHub Actions or `az webapp deploy`

---

## Deploy Frontend (Angular)

Option A — App Service (Linux):

- Create an App Service for the frontend
- Build: `ng build --configuration=production`
- Deploy `dist/` contents
- Configure startup to serve static files (Node or NGINX container) or switch to Static Web Apps

Option B — Azure Static Web Apps (recommended for cost):

- Create Static Web App
- Connect repo and build (Angular preset)
- Set `API_BASE_URL` as an environment/config

---

## CORS & Networking

- Allow frontend origin on APIs
- Enforce HTTPS-only

---

## Validation Checklist

- Frontend loads and fetches menu
- Orders can be placed and status updates are visible
- Image upload/read via Blob Storage works
- Service Bus events emit on order create/update

---

## References

- [Deployment Overview](./deployment.md)
- [Technologies Overview](./README.md)
- [Architecture Overview](../20-architecture/README.md)
- [Business Domain](../10-business-domain/README.md)
