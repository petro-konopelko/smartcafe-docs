# SmartCafe Documentation

Welcome to the **SmartCafe documentation repository**.  
This repository contains all the design, architecture, and domain documentation for the SmartCafe project — a **microservices-based smart ordering system for cafes and restaurants**.

---

## 🚀 Overview

SmartCafe allows customers to:

- View menus via QR codes or links  
- Place orders directly to the restaurant  
- (Future) Pay bills, split orders, call waiters, and get AI recommendations

The system is built with **microservices**, **Azure Kubernetes deployment**, and **blob storage for menu assets**.

> For a detailed high-level overview, see [`00-overview/README.md`](./00-overview/README.md)

---

## 📁 Documentation Structure

| Folder | Description |
|--------|-------------|
| `00-overview` | Project vision, MVP scope, glossary, and high-level diagrams |
| `10-business-domain` | Domain modeling: Orders, Menu, Payments, Waiter Calls |
| `20-architecture` | System architecture, microservices, communication, security |
| `30-technologies` | Tech stack details: backend, frontend, DevOps, infrastructure |
| `LICENSE.md` | Project license (Apache 2.0) |

> Each folder contains Markdown files with detailed explanations and Mermaid diagrams where applicable.

---

## 📌 Getting Started

1. Browse the [`00-overview/README.md`](./00-overview/README.md) for a high-level introduction.  
2. Explore the MVP and business domain in `10-business-domain`.  
3. Review the architecture and technologies in `20-architecture` and `30-technologies`.  

---

## 📅 Roadmap / Future Features

- Split payments for group orders  
- AI-powered dish recommendations  
- Waiter call integration  
- Analytics for restaurants  

> The system is designed to be extensible without rewriting core services.

---

## ⚖ License

This project is licensed under the **Apache License 2.0**.  
See [`LICENSE.md`](./LICENSE.md) for full terms.
