# SE LAB 03: Architecture Selection & UML Component Diagram

## PROJECT OVERVIEW

* **Project Name / Topic:** Dropshipping Inventory & Order Orchestrator (DIOO)


* **Selected Architecture:** Event-Driven Layered Microservices Architecture (optimized into a decoupled Event-Driven Orchestration model)


* **Objective:** Choose and justify a software architecture capable of handling asynchronous multi-vendor integrations, secure webhook processing, and high-performance real-time inventory checks, and model it as a UML component diagram.



---

## 1. Architecture Selection & Justification

### **Architecture Chosen:** Event-Driven Layered Orchestration Model



* **Reason 1: Clear separation of concerns for asynchronous multi-vendor integration**
* Unlike a single-warehouse system, dropshipping coordinates independent external entities (e.g., Shopify/WooCommerce storefronts, 3PL suppliers, and operators).


* The system decouples cleanly into three operational layers:


1. **Presentation Layer:** Storefront Webhooks, Admin Web Interface, and Supplier Dashboards.


2. **Business / Event Orchestrator Layer:** Order Routing Engine, Supplier Inventory Sync, and Real-time Stock Allocation.


3. **Data Layer:** Unified Inventory Ledger, Order Lifecycle DB, and Supplier Catalog Mappings.






* **Reason 2: Adapts to scale and asynchronous nature of dropshipping operations**
* Dropshipping experiences volatile traffic surges (flash sales) and unpredictable third-party supplier API response times.


* Combining a layered structure with asynchronous event orchestration (Message Queue/Event Bus) ensures incoming orders are immediately ingested and acknowledged without blocking user checkouts or risking cascading API failures.





---

## 2. Security Advantage

* **Strict Boundary Enforcement:** The Presentation Layer (external storefronts and supplier webhooks) never interacts directly with the Data Layer.


* **Gatekeeping:** All traffic flows through an API Gateway and the Business/Order Orchestration Layer, where **OAuth2 authentication**, **HMAC webhook signature verification**, payload validation, and **Role-Based Access Control (RBAC)** are strictly enforced. This minimizes attack surfaces and protects sensitive supplier pricing and margin data.



---

## 3. Performance Benefit

* **Virtual Stock Caching:** To prevent overselling across 100,000+ SKUs from multiple supplier feeds, the system uses an asynchronous caching pipeline.


* **Sub-50 ms Latency:** The Inventory Sync component maintains an in-memory Redis cache backed by the primary database, ensuring inventory lookups and reservation checks complete in under 50 ms during peak loads while supplier syncs run asynchronously.



---

## 4. UML Component Diagram Breakdown

The system is structured across three core tiers:

* **Presentation Layer:**
* **User Interface Component:** Interacts with external actors including **E-Commerce Merchants** and **Operations Managers**.




* **Business / Services Layer:**
* **Supplier Gateway Component:** Handles incoming supplier APIs and webhook feeds.


* **Order Orchestration & Inventory Component:** Manages order routing, webhook parsing, and stock verification interfaces.


* **Supplier Settlement & Analytics Component:** Processes analytics and supplier settlement queries.




* **Data Layer:**
* **Database Component:** Houses the unified database interface, order ledger, and inventory mappings.
