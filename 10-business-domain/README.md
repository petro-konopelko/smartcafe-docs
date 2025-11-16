

# Cafe Domain Documentation

This folder contains documentation focused on the core processes and flows of SmartCafe, including menu management, order placement, and future features. It is designed for cafe stakeholders and developers to understand how the system works from a user perspective.

---

## Cafe Domain Overview

SmartCafe streamlines digital menu management and customer ordering for cafes. The domain is organized by service:

- **Menu Service**: Cafes create and manage digital menus, divided into sections (e.g., breakfast, lunch, dinner). Each section has configurable hours and up to 100 items. Menu items have a name, description, price, images (big and cropped), and can belong to multiple categories (e.g., vegetarian, spicy). Categories are configurable, with default options and optional small icons/images. Items support ingredient inclusion/exclusion and menu preview before publishing.

- **Order Service**: Customers browse menus, select items, customize ingredients, and place orders. Orders are processed in real time, with status updates and event-driven backend integration.

- **(Future) Payment Service**: Handles payments and split bills.

- **(Future) AI Assistant**: Assists customers in selecting dishes based on preferences.

---

## Contents

- `menu.md`: Menu service details
- `orders.md`: Order service details
- `README.md`: This overview

---

## Audience

- **Cafe:** Explore cafe flows, use cases, and user experience
- **Developers:** Reference for domain requirements and process flows

---

## References

- [Menu](./menu.md)
- [Orders](./orders.md)
- [Root README](../README.md)
