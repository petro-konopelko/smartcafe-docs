
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

## Data Model (Simplified)

- **Cafe**: id, name, contact info
- **Menu**: id, cafeId, name, sections[]
- **Section**: id, menuId, name, availableFrom, availableTo, items[]
- **Item**: id, sectionId, name, description, price, categories[], imageBigUrl, imageCroppedUrl, ingredientOptions[]
- **Category**: id, name, iconUrl

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

- [Architecture Overview](README.md)
- [Order Service Technical Docs](order-service.md)
- [Business Domain](../10-business-domain/menu.md)
