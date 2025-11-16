
# SmartCafe Documentation

Welcome to the **SmartCafe documentation repository**. This repository contains all business, architecture, and technical documentation for SmartCafe—a microservices-based smart ordering system for cafes.

---

## High-Level Overview

SmartCafe enables:

- Digital menu management for businesses
- Customers to view menus and place orders via QR codes or links
- Real-time order status updates
- (Future) AI-powered dish recommendations, split payments, and waiter calls

The platform is built using microservices, Azure Kubernetes Service (AKS) for hosting, and Azure Blob Storage for menu images and assets.

---

## Business Domain Summary

SmartCafe is designed to streamline menu management and customer ordering for cafes. The business domain is split into distinct services:

- **Menu Service**: Cafes create and manage digital menus, organized into sections (e.g., breakfast, lunch, dinner). Each section has configurable hours and up to 100 items. Menu items have a name, description, price, images (big and cropped), and can belong to multiple categories (e.g., vegetarian, spicy). Categories are configurable, with default options and optional small icons/images. Items support ingredient inclusion/exclusion and menu preview before publishing.

- **Order Service**: Customers browse menus, select items, customize ingredients, and place orders. Orders are processed in real time, with status updates and event-driven backend integration.

- **(Future) Payment Service**: Handles payments and split bills.

- **(Future) AI Assistant**: Assists customers in selecting dishes based on preferences.

---

## Documentation Structure

| Folder              | Description                                               |
|---------------------|-----------------------------------------------------------|
| `00-overview`       | Project vision, MVP scope, glossary, and high-level docs  |
| `10-business-domain`| Business flows: Orders, Menu, Payments, Waiter Calls      |
| `20-architecture`   | System architecture, microservices, communication, security|
| `30-technologies`   | Tech stack details: backend, frontend, DevOps, infrastructure|
| `LICENSE.md`        | Project license (Apache 2.0)                              |

Each folder contains a `README.md` with base information and references for easy navigation. Business and technical documentation are clearly separated.

---

## Getting Started

1. Start with [`00-overview/README.md`](./00-overview/README.md) for project vision and MVP scope.
2. Explore business flows in [`10-business-domain/`](./10-business-domain/).
3. Review architecture and technical details in `20-architecture` and `30-technologies`.

---

## Roadmap / Future Features

- Split payments for group orders
- AI-powered dish recommendations
- Waiter call integration
- Analytics for cafes

The system is designed to be extensible without rewriting core services.

---

## License

This project is licensed under the **Apache License 2.0**. See [`LICENSE.md`](./LICENSE.md) for full terms.

---

## References

- [Project Overview](./00-overview/README.md)
- [Business Domain](./10-business-domain/README.md)
- [Architecture](./20-architecture/README.md)
- [Technologies](./30-technologies/README.md)
