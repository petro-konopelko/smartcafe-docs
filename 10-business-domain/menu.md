

# Menu Service — Business Documentation

This document details the business logic and user flows for menu management in SmartCafe.

---

## Menu Overview

Each cafe can create **multiple menus** (e.g., Summer Menu, Winter Menu, Holiday Special) but only **one menu is active** at a time. This allows cafes to prepare seasonal menus in advance and switch between them as needed.

**Menu States:**
- **Draft**: Work in progress, not visible to customers
- **Published**: Ready to be activated, but not currently active
- **Active**: Currently displayed to customers (only one per cafe)

**Menu Lifecycle:**
1. Create menu as draft (e.g., "Summer Menu 2025")
2. Add sections and items
3. Publish menu (makes it available for activation)
4. Activate menu (shows to customers, deactivates previous menu)
5. When season changes, activate different menu (e.g., switch to "Winter Menu")

**Use Cases:**
- **Seasonal menus**: Summer menu, Winter menu, Spring menu
- **Holiday specials**: Valentine's Day menu, Christmas menu
- **Event menus**: Brunch menu, Happy Hour menu
- **A/B testing**: Test different menu layouts or pricing

---

## Sections

- Organize menu items by meal type or theme (e.g., breakfast, starters, lunch, dinner)
- Each section has:
  - Name
  - Availability hours (e.g., breakfast: 9:00–13:00)
  - Up to 100 items

---

## Menu Items

Each menu item includes:

- Name
- Description
- Price
- Images:
  - Big image (main display)
  - Cropped image (for fast scrolling)
  - Default image if none provided
- Categories (multiple allowed):
  - Default categories: Vegetarian, Spicy
  - Additional categories can be configured by the cafe
  - Each category may have a small icon/image
- Ingredient customization:
  - Customers can include or exclude ingredients when ordering

---

## Item Management

- Cafes can add, update, or remove items from sections
- Items must belong to one section and one or more categories
- Images can be updated or deleted; default image used if none provided
- Menu preview available before publishing changes

---

## Category Management

- Default categories: Vegetarian, Spicy
- Cafes can configure additional categories as needed
- Categories can have small images/icons for visual cues
- Each item can be assigned multiple categories

---

## References

- [Orders](./orders.md)
- [Business Domain Overview](./README.md)
- [Menu Service Architecture](../20-architecture/menu-service.md)
- [Root README](../README.md)
