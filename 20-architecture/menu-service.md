
# Menu Service — Technical Documentation

This document describes the technical details of the Menu Service in SmartCafe.

---

## Overview

The Menu Service manages digital menus for each cafe, including sections, items, categories, images, and availability.

---

## API Endpoints (Example)

- `GET /cafes/{cafeId}/menus` — Retrieve menu for a cafe
- `POST /cafes/{cafeId}/menus` — Create a new menu
- `PUT /cafes/{cafeId}/menus/{menuId}` — Update menu
- `DELETE /cafes/{cafeId}/menus/{menuId}` — Delete menu
- `GET /cafes/{cafeId}/menus/{menuId}/sections` — List menu sections
- `POST /cafes/{cafeId}/menus/{menuId}/sections` — Add section
- `GET /cafes/{cafeId}/menus/{menuId}/items` — List menu items
- `POST /cafes/{cafeId}/menus/{menuId}/items` — Add menu item
- `PUT /cafes/{cafeId}/menus/{menuId}/items/{itemId}` — Update menu item
- `DELETE /cafes/{cafeId}/menus/{menuId}/items/{itemId}` — Delete menu item

---

## Data Model (PostgreSQL Schema)

- **Cafe**: id (uuid PK), name, contact_info, created_at
- **Menu**: id (uuid PK), cafe_id (FK), name, is_active, is_published, published_at, activated_at, is_deleted, created_at, updated_at
  - **Constraint**: Only one active menu per cafe (unique partial index on cafe_id where is_active = true AND is_deleted = false)
- **Section**: id (uuid PK), menu_id (FK), name, display_order, available_from, available_to, created_at
- **MenuItem**: id (uuid PK), section_id (FK), name, description, price, image_big_url, image_cropped_url, ingredient_options (jsonb), is_active, created_at, updated_at
- **Category**: id (uuid PK), name, icon_url, is_default, created_at
- **MenuItemCategory**: menu_item_id (uuid FK), category_id (uuid FK) — join table for many-to-many

**Business Rules:**
- Each cafe can have **multiple menus** (e.g., seasonal menus)
- Only **one menu is active** at any time
- Menu states: Draft → Published → Active
- Must publish before activating
- Activating a menu automatically deactivates the previous active menu
- Soft delete for draft menus only (cannot delete published/active menus)

**Technology Stack:**
- PostgreSQL with Entity Framework Core 10
- UUID (Guid) primary keys using .NET's `Guid.CreateVersion7()` for time-ordered globally unique identifiers
- JSONB column type for flexible data (ingredient options)
- Foreign key constraints for referential integrity
- Check constraints for business rules (price > 0)
- Full-text search indexes on item names and descriptions
- B-tree indexes optimized for UUID queries

---

## Image Handling

- Images are stored in Azure Blob Storage.
- Each item can have a big image (main display) and a cropped image (for fast scrolling).
- Default image is used if none provided.

---

## Eventing

- Menu events (created, updated, deleted) are published to Azure ServiceBus for integration with other services.

---

## Security & Access

- Role-based access (admin, cafe owner) planned for future releases.
- For MVP, endpoints are open for demonstration purposes.

---

## References

- [Architecture Overview](./README.md)
- [Order Service Technical Docs](./order-service.md)
- [AKS Desired State](./aks-desired-state.md)
- [Business Domain - Menu](../10-business-domain/menu.md)
- [Technologies](../30-technologies/README.md)
