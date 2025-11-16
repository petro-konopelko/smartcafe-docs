

# Menu Service — Business Documentation

This document details the business logic and user flows for menu management in SmartCafe.

---

## Menu Overview

Cafes create and manage digital menus, which are divided into sections (e.g., breakfast, lunch, dinner). Each section has configurable availability hours and can contain up to 100 items.

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
