
# Order Service — Business Documentation

This document details the business logic and user flows for order placement and management in SmartCafe.

---

## Order Overview

Customers can open the order page, browse the menu, select items, customize ingredients, and place orders. Orders are processed in real time, with status updates and event-driven backend integration.

---

## Order Flow

1. Customer opens the order page.
2. Customer browses menu sections and items.
3. Customer selects items and customizes ingredients (include/exclude).
4. Customer reviews order summary and places the order.
5. System creates the order and sends an event to the backend (via ServiceBus).
6. Customer receives real-time status updates:

- Pending
- Accepted
- Preparing
- Ready
- Delivered
- Cancelled


---

## Order Management

- Customers can modify or cancel orders before processing begins.
- Orders are validated for item availability and business rules.
- No payment integration in MVP (future feature).
- Order history is available for customers to review past orders.

Note: Orders are never deleted. To remove an order from active processing, change its status to Cancelled.

---

## Eventing & Status Updates

- Order events are sent to the backend using Azure ServiceBus.
- Real-time status updates are provided to customers via the frontend.
- Notifications (email, SMS, in-app) are out of scope for MVP.

---

## References

- [Menu](./menu.md)
- [Business Domain Overview](./README.md)
- [Order Service Architecture](../20-architecture/order-service.md)
- [Root README](../README.md)
