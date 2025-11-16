# SmartCafe — Technologies Overview

This document describes the key technologies and implementation details for SmartCafe, including internationalization (i18n) support.

---

## Key Technologies

- **Backend:** .NET 10 (Clean Architecture)
- **Frontend:** Angular 20 (Material, Flex Layout)
- **Cloud:** Azure Kubernetes Service (AKS), Azure Blob Storage, Azure ServiceBus
- **Database:** Azure PostgreSQL or SQL Server

---

## Internationalization (i18n)

SmartCafe is designed with internationalization in mind:

- **Default language:** English
- **Future support:** Ukrainian and other languages
- **Frontend:**
  - Uses Angular i18n tools for translation and localization
  - All UI text is externalized for easy translation
  - Language switcher planned for future releases
- **Backend:**
  - API responses and error messages default to English
  - Future support for localized content (e.g., menu descriptions)

---

## References

- [Architecture Overview](../20-architecture/README.md)
- [Business Domain](../10-business-domain/README.md)
