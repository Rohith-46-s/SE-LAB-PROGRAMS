# SE LAB 01: Requirements Engineering & UML Use-Case Modelling

## PROBLEM STATEMENT

### Dropshipping Inventory & Order Orchestrator

An automated e-commerce backend that receives storefront order webhooks, validates incoming orders, checks third-party supplier inventory in real time, splits multi-vendor orders, automatically dispatches supplier purchase orders, handles out-of-stock items, and tracks shipment tracking numbers.

---

## Stakeholders / Actors

* **Storefront Platform**: Sends customer order information to the system through webhooks.


* **E-Store Owner**: Monitors orders, handles exceptions, and updates tracking information.


* **Supplier Partner**: Provides supplier inventory information and receives purchase orders.



---

## Deliverables & Summary of Your Submission (`LAB1_SE_PES2UG24CS409.pdf`)

### 1. Requirements Table

* **Functional Requirements (FR-001 to FR-007):**
* **FR-001**: Receive and register order webhooks from configured storefront platforms.


* **FR-002**: Validate incoming order webhooks by checking payloads, fields, authentication signatures, and product details.


* **FR-003**: Process multi-vendor orders by mapping items to suppliers and verifying stock availability in real time.


* **FR-004**: Automatically split multi-vendor orders and generate distinct supplier purchase orders.


* **FR-005**: Identify out-of-stock items and handle them according to configured business policies.


* **FR-006**: Allow the E-Store Owner to update and maintain shipment tracking numbers.


* **FR-007**: Allow the E-Store Owner to view order status, supplier fulfillment status, and tracking information.




* **Non-Functional Requirements (NFR-001 to NFR-004):**
* **NFR-001**: Acknowledge valid storefront webhooks within 200 ms under normal operating conditions to prevent retry storms.


* **NFR-002**: Secure communication channels, authenticate endpoints, and protect order and customer data from unauthorized access.


* **NFR-003**: Ensure repeated delivery of the same webhook/event ID does not result in duplicate order processing or purchase orders.


* **NFR-004**: Maintain detailed audit logs for order processing, stock checks, and status changes for auditing and troubleshooting.





### 2. UML Use-Case Model & Relationships

* **Core Use Cases:**
* `UC-01` Receive Order Webhook


* `UC-02` Validate Order Webhook


* `UC-03` Process Multi-Vendor Order


* `UC-04` Check Supplier Stock


* `UC-05` Split/Dispatch Purchase Orders


* `UC-06` Handle Out-of-Stock Item


* `UC-07` Update Tracking Number


* `UC-08` View Order & Tracking Status




* **Key Relationships:**
* `Receive Order Webhook` includes `Validate Order Webhook`.


* `Validate Order Webhook` includes `Process Multi-Vendor Order`.


* `Process Multi-Vendor Order` includes `Check Supplier Stock` and `Split/Dispatch Purchase Orders`.


* `Split/Dispatch Purchase Orders` is extended by `Handle Out-of-Stock Item` when products are unavailable.





### 3. Use-Case Flow Specification (`UC-001`: Process Multi-Vendor Order)

* **Preconditions:** Storefront platform is configured, webhook endpoint is live, supplier inventories/APIs are set up, and order details are valid.


* **Main Success Scenario:** Webhook is received $\rightarrow$ Unique ID generated $\rightarrow$ Validated $\rightarrow$ Order stored $\rightarrow$ Items and suppliers identified $\rightarrow$ Stock checked $\rightarrow$ Items grouped by supplier $\rightarrow$ Purchase orders generated and dispatched $\rightarrow$ Fulfillment status updated and tracking details maintained.


* **Alternate Flows:** Covers invalid webhooks (`AF-01`), out-of-stock items (`AF-02`), multi-vendor separation (`AF-03`), supplier API failures (`AF-04`), duplicate webhooks (`AF-05`), and tracking updates (`AF-06`).
