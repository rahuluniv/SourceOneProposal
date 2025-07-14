# Project Requirements

**Executive Summary**

This project is to develop a software system to automate and streamline Source One's SysDev workflow, covering procurement, quoting, sampling, terms/PO, accounting, inventory, and logistics. It aims to reduce manual tasks, improve accuracy, and enable features like auto-PO generation and daily report automation, enhancing efficiency for sourcing and supply chain management.

### **Project Glossary**

*   **RFQ**: Request for Quotation – Client inquiry for product pricing.
    
*   **SKU**: Stock Keeping Unit – Unique product identifier.
    
*   **CBM**: Cubic Meter – Volume measurement for shipping.
    
*   **PO**: Purchase Order – Order placed with manufacturer.
    
*   **SO**: Sales Order – Order confirmation to client.
    
*   **AP**: Accounts Payable – Payments to suppliers/freight.
    
*   **AR**: Accounts Receivable – Invoices to clients.
    
*   **QA**: Quality Assurance – Sample/product testing.
    
*   **CI**: Commercial Invoice – Supplier billing document.
    
*   **PL**: Packing List – Shipment contents details.
    
*   **BL**: Bill of Lading – Shipping contract.
    
*   **ISF**: Importer Security Filing – Customs pre-arrival info.
    
*   **ETA**: Estimated Time of Arrival – Shipment delivery estimate.
    
*   **3PL**: Third-Party Logistics – External fulfillment provider.
    
*   **DC**: Distribution Center – Client's warehouse.
    

### **User Stories**

**Procurement Module:**

*   As a procurement specialist, I want to input RFQ details so that I can gather SKU specs like weight, quantity, and material.
    
*   As a procurement specialist, I want to search and log manufacturers worldwide with details (name, address, website, email, phone, status) in a database per SKU.
    
*   As a procurement specialist, I want to upload and store product catalogs in a shared digital repository for team access.
    

**Quoting Module:**

*   As a quoter, I want to list client-interested products and estimate annual cases based on business type/volume if not provided.
    
*   As a quoter, I want to verify product details (quantity/case, manufacturer price, case dimensions, pallet fit) from a quotation sheet.
    
*   As a quoter, I want to request missing product info (pricing, dimensions, quantity) from sourcing team via integrated notifications.
    
*   As a quoter, I want to auto-calculate CBM, cases/pallet, fulfillment costs, and selling price including margins, freight, duties.
    
*   As a quoter, I want to consult logistics for cost validation (delivery, fulfillment, freight, drayage) through system queries.
    
*   As a quoter, I want to compute final quotation with landed costs, profits, margins, and adjust for targets.
    

**Sampling Module:**

*   As a sampling coordinator, I want to check sample availability and send them immediately if in stock.
    
*   As a sampling coordinator, I want to request mold/template creation time if samples unavailable.
    
*   As a sampling coordinator, I want to QA samples internally and log approvals.
    
*   As a sampling coordinator, I want to send approved samples to clients and track testing/approval status.
    

**Terms & PO Module:**

*   As a sales admin, I want to draft term sheets, send for legal review, and finalize for client signature.
    
*   As a sales admin, I want to generate and send SO/PO to manufacturers upon term approval.
    

**Accounting Module:**

*   As an accountant, I want to handle client-initiated orders: receive PO, generate invoice, place manufacturer order, receive invoice.
    
*   As an accountant, I want to manage inventory-triggered orders: flag replenishment, initiate manufacturer order, receive deposit invoice.
    
*   As an accountant, I want to categorize invoices into AP (manufacturer, freight) and AR (client-grouped).
    
*   As an accountant, I want to process deposits/balances, send wire confirmations, and mark invoices paid.
    
*   As an accountant, I want to track client payments: record due/paid amounts, dates, status, discounts, and mark AR paid.
    

**Inventory Module (Daily Workflow):**

*   As an inventory manager, I want a dashboard to open tools (email, notes, sheets) and review emails for updates.
    
*   As an inventory manager, I want to monitor POs: delivery windows, delays, scheduled shipments.
    
*   As an inventory manager, I want to review inventory: on-hand levels, days projected, upcoming arrivals, reorder points.
    
*   As an inventory manager, I want to prioritize low-stock/volatile SKUs and those in sampling.
    
*   As an inventory manager, I want to track containers/production: builds, invoices, shipping, order placement.
    
*   As an inventory manager, I want to compare inventory with 60-day plan and adjust for shipments.
    
*   As an inventory manager, I want to auto-generate daily summaries with bolded key info.
    
*   As an inventory manager, I want auto-PO triggers for low stock and a recommendation engine.
    

**Logistics Module:**

*   As a logistics coordinator, I want to initiate PO/deposit and confirm supplier lead times/production progress.
    
*   As a logistics coordinator, I want 5-day pre-completion checks: status confirmation, RFQ to forwarders.
    
*   As a logistics coordinator, I want to book freight: select forwarder, coordinate container, collect CI/PL.
    
*   As a logistics coordinator, I want to handle port handover: receive ISF/BL, submit to broker.
    
*   As a logistics coordinator, I want daily in-transit tracking and ETA notifications.
    
*   As a logistics coordinator, I want pre-arrival setup: obtain Arrival Notice.
    
*   As a logistics coordinator, I want to settle finances: pay supplier/freight, secure BL/Telex.
    
*   As a logistics coordinator, I want customs clearance: send docs to broker, handle queries, confirm release.
    
*   As a logistics coordinator, I want drayage/pickup: arrange trucking to client DC or 3PL, confirm delivery/intake.
    
*   As a logistics coordinator, I want final fulfillment: submit PO to warehouse, coordinate pick/pack/delivery, confirm to client.
    

**Project Requirements** 

### **Procurement Module Sub-User Stories**

1.  **Sub-User Story: As a procurement specialist, I want to input RFQ details, including SKU specs (weight, quantity, material), to start sourcing.**
    
    *   **Explanation**: Allows entry of RFQ data to initiate manufacturer search with precise product specs.
        
    *   **Tickets**:
        
        *   PROC-001: Create RFQ input form.
            
        *   PROC-002: Validate SKU fields.
            
    *   **Acceptance Criteria**:
        
        *   Form saves RFQ with all specs.
            
        *   Validation errors shown for missing fields.
            
        *   Data persists in database.
            
2.  **Sub-User Story: As a procurement specialist, I want to search manufacturers by criteria (price, quality, location) and add them to the database.**
    
    *   **Explanation**: Enables querying global manufacturers and logging matches per SKU.
        
    *   **Tickets**:
        
        *   PROC-003: Integrate manufacturer search API.
            
        *   PROC-004: Add database entry functionality.
            
    *   **Acceptance Criteria**:
        
        *   Search returns filtered results.
            
        *   New entries added with all details.
            
        *   Duplicates prevented.
            
3.  **Sub-User Story: As a procurement specialist, I want to update manufacturer status (e.g., Contacted, Pending Quotation) in real-time.**
    
    *   **Explanation**: Tracks interaction progress with manufacturers for each SKU.
        
    *   **Tickets**:
        
        *   PROC-005: Implement status dropdown.
            
        *   PROC-006: Real-time update via WebSocket.
            
    *   **Acceptance Criteria**:
        
        *   Status changes saved instantly.
            
        *   Updates visible to all users.
            
        *   Audit log recorded.
            
4.  **Sub-User Story: As a procurement specialist, I want to upload catalogs and receive notifications for access requests.**
    
    *   **Explanation**: Stores catalogs digitally and alerts on team access needs.
        
    *   **Tickets**:
        
        *   PROC-007: File upload endpoint.
            
        *   PROC-008: Notification system integration.
            
    *   **Acceptance Criteria**:
        
        *   Uploads stored securely.
            
        *   Emails sent on access requests.
            
        *   File previews available.
            

### **Quoting Module Sub-User Stories**

1.  **Sub-User Story: As a quoter, I want to auto-populate product lists from client RFQ data.**
    
    *   **Explanation**: Pulls products from RFQ to pre-fill quoting sheet.
        
    *   **Tickets**:
        
        *   QUOT-001: RFQ data integration.
            
        *   QUOT-002: Auto-populate logic.
            
    *   **Acceptance Criteria**:
        
        *   List fills on RFQ selection.
            
        *   Editable if needed.
            
        *   No data loss on refresh.
            
2.  **Sub-User Story: As a quoter, I want to estimate annual cases using predefined business type templates.**
    
    *   **Explanation**: Applies templates based on client type for volume estimates.
        
    *   **Tickets**:
        
        *   QUOT-003: Template database setup.
            
        *   QUOT-004: Estimation algorithm.
            
    *   **Acceptance Criteria**:
        
        *   Estimates calculated accurately.
            
        *   Templates customizable.
            
        *   Results displayed per product.
            
3.  **Sub-User Story: As a quoter, I want to fetch and verify product details (quantity/case, manufacturer price, case dimensions, pallet fit) from integrated quotation sheets.**
    
    *   **Explanation**: Retrieves and checks details from sheets for accuracy.
        
    *   **Tickets**:
        
        *   QUOT-005: Sheet API connection.
            
        *   QUOT-006: Verification checks.
            
    *   **Acceptance Criteria**:
        
        *   Data fetched on demand.
            
        *   Mismatches flagged.
            
        *   Verified status logged.
            
4.  **Sub-User Story: As a quoter, I want to send automated requests to sourcing for missing info and track responses.**
    
    *   **Explanation**: Notifies sourcing team and monitors replies for gaps.
        
    *   **Tickets**:
        
        *   QUOT-007: Request notification system.
            
        *   QUOT-008: Response tracking dashboard.
            
    *   **Acceptance Criteria**:
        
        *   Requests emailed with details.
            
        *   Responses update status.
            
        *   Timeout alerts.
            
5.  **Sub-User Story: As a quoter, I want formulas to auto-calculate CBM and cases per pallet.**
    
    *   **Explanation**: Computes volume and pallet metrics from dimensions.
        
    *   **Tickets**:
        
        *   QUOT-009: Formula implementation.
            
        *   QUOT-010: Input validation.
            
    *   **Acceptance Criteria**:
        
        *   Calculations accurate.
            
        *   Updates on input change.
            
        *   Error for invalid inputs.
            
6.  **Sub-User Story: As a quoter, I want to input fulfillment costs and see real-time selling price adjustments.**
    
    *   **Explanation**: Allows cost entry with instant price recalculation.
        
    *   **Tickets**:
        
        *   QUOT-011: Cost input fields.
            
        *   QUOT-012: Real-time calc engine.
            
    *   **Acceptance Criteria**:
        
        *   Prices update live.
            
        *   Includes margins.
            
        *   History of adjustments.
            
7.  **Sub-User Story: As a quoter, I want to query logistics API for cost validation (delivery, fulfillment, freight, drayage) and log results.**
    
    *   **Explanation**: Validates costs via API and records outcomes.
        
    *   **Tickets**:
        
        *   QUOT-013: API integration.
            
        *   QUOT-014: Logging mechanism.
            
    *   **Acceptance Criteria**:
        
        *   API calls successful.
            
        *   Results logged and displayed.
            
        *   Errors handled gracefully.
            
8.  **Sub-User Story: As a quoter, I want to generate final quotation reports with breakdowns of costs, profits, and margins.**
    
    *   **Explanation**: Produces detailed quote documents.
        
    *   **Tickets**:
        
        *   QUOT-015: Report template.
            
        *   QUOT-016: Export to PDF.
            
    *   **Acceptance Criteria**:
        
        *   Reports include all breakdowns.
            
        *   Exportable formats.
            
        *   Customizable headers.
            

### **Sampling Module Sub-User Stories**

1.  **Sub-User Story: As a sampling coordinator, I want to query inventory for sample availability and auto-generate shipping labels.**
    
    *   **Explanation**: Checks stock and creates labels for immediate dispatch.
        
    *   **Tickets**:
        
        *   SAMP-001: Inventory query API.
            
        *   SAMP-002: Label generation.
            
    *   **Acceptance Criteria**:
        
        *   Availability shown accurately.
            
        *   Labels printable.
            
        *   Stock updated post-shipment.
            
2.  **Sub-User Story: As a sampling coordinator, I want to schedule mold creation timelines and notify teams.**
    
    *   **Explanation**: Sets timelines for custom samples and alerts stakeholders.
        
    *   **Tickets**:
        
        *   SAMP-003: Calendar integration.
            
        *   SAMP-004: Notification setup.
            
    *   **Acceptance Criteria**:
        
        *   Timelines saved and visible.
            
        *   Notifications sent on schedule.
            
        *   Conflicts flagged.
            
3.  **Sub-User Story: As a sampling coordinator, I want to log QA results with photos and approval timestamps.**
    
    *   **Explanation**: Records internal testing with evidence and times.
        
    *   **Tickets**:
        
        *   SAMP-005: QA form.
            
        *   SAMP-006: Photo upload.
            
    *   **Acceptance Criteria**:
        
        *   Logs include photos/timestamps.
            
        *   Approvals digital-signed.
            
        *   Searchable logs.
            
4.  **Sub-User Story: As a sampling coordinator, I want to track client sample receipt, testing feedback, and approval status via dashboard.**
    
    *   **Explanation**: Monitors client-side process on a central dashboard.
        
    *   **Tickets**:
        
        *   SAMP-007: Dashboard build.
            
        *   SAMP-008: Status updates.
            
    *   **Acceptance Criteria**:
        
        *   Real-time status.
            
        *   Feedback logged.
            
        *   Alerts on delays.
            

### **Terms & PO Module Sub-User Stories**

1.  **Sub-User Story: As a sales admin, I want to auto-draft term sheets from quotation data.**
    
    *   **Explanation**: Generates terms using quote info.
        
    *   **Tickets**:
        
        *   TERM-001: Drafting template.
            
        *   TERM-002: Data mapping.
            
    *   **Acceptance Criteria**:
        
        *   Drafts accurate.
            
        *   Editable sections.
            
        *   Version control.
            
2.  **Sub-User Story: As a sales admin, I want to route term sheets to legal for review and track revisions.**
    
    *   **Explanation**: Sends to legal and follows changes.
        
    *   **Tickets**:
        
        *   TERM-003: Routing workflow.
            
        *   TERM-004: Revision tracking.
            
    *   **Acceptance Criteria**:
        
        *   Routed via email/portal.
            
        *   Revisions highlighted.
            
        *   Approval workflow.
            
3.  **Sub-User Story: As a sales admin, I want to send finalized terms to clients and monitor signature status.**
    
    *   **Explanation**: Delivers terms and tracks e-signatures.
        
    *   **Tickets**:
        
        *   TERM-005: Sending integration.
            
        *   TERM-006: Signature monitoring.
            
    *   **Acceptance Criteria**:
        
        *   Sent securely.
            
        *   Status updates real-time.
            
        *   Reminders automated.
            
4.  **Sub-User Story: As a sales admin, I want to generate SO/PO documents and send them to manufacturers with one click.**
    
    *   **Explanation**: Creates and dispatches orders instantly.
        
    *   **Tickets**:
        
        *   TERM-007: Document generator.
            
        *   TERM-008: One-click send.
            
    *   **Acceptance Criteria**:
        
        *   Docs generated correctly.
            
        *   Sent and confirmed.
            
        *   Copies archived.
            

### **Accounting Module Sub-User Stories**

1.  **Sub-User Story: As an accountant, I want to receive client PO alerts and auto-generate Source One invoices.**
    
    *   **Explanation**: Notifies on POs and creates invoices.
        
    *   **Tickets**:
        
        *   ACCT-001: Alert system.
            
        *   ACCT-002: Invoice auto-gen.
            
    *   **Acceptance Criteria**:
        
        *   Alerts via email/dashboard.
            
        *   Invoices accurate.
            
        *   Linked to PO.
            
2.  **Sub-User Story: As an accountant, I want to link manufacturer orders to client POs for tracking.**
    
    *   **Explanation**: Connects orders for traceability.
        
    *   **Tickets**:
        
        *   ACCT-003: Linking logic.
            
        *   ACCT-004: Tracking view.
            
    *   **Acceptance Criteria**:
        
        *   Links created manually/auto.
            
        *   Tracking shows chain.
            
        *   Reports on links.
            
3.  **Sub-User Story: As an accountant, I want inventory flags to trigger replenishment orders automatically.**
    
    *   **Explanation**: Auto-orders on low stock flags.
        
    *   **Tickets**:
        
        *   ACCT-005: Flag triggers.
            
        *   ACCT-006: Auto-order setup.
            
    *   **Acceptance Criteria**:
        
        *   Triggers on thresholds.
            
        *   Orders placed.
            
        *   Approvals optional.
            
4.  **Sub-User Story: As an accountant, I want to categorize and group invoices by type (AP/AR) and client.**
    
    *   **Explanation**: Organizes invoices for easy management.
        
    *   **Tickets**:
        
        *   ACCT-007: Categorization.
            
        *   ACCT-008: Grouping filters.
            
    *   **Acceptance Criteria**:
        
        *   Auto-categorized.
            
        *   Grouped views.
            
        *   Searchable.
            
5.  **Sub-User Story: As an accountant, I want to process payments with wire confirmations and auto-mark as paid.**
    
    *   **Explanation**: Handles payments and updates status.
        
    *   **Tickets**:
        
        *   ACCT-009: Payment processor.
            
        *   ACCT-010: Auto-mark.
            
    *   **Acceptance Criteria**:
        
        *   Wires confirmed.
            
        *   Status updated.
            
        *   Receipts generated.
            
6.  **Sub-User Story: As an accountant, I want to track client AR with reminders for due dates and discounts.**
    
    *   **Explanation**: Monitors receivables with alerts.
        
    *   **Tickets**:
        
        *   ACCT-011: AR tracker.
            
        *   ACCT-012: Reminder automation.
            
    *   **Acceptance Criteria**:
        
        *   Due dates tracked.
            
        *   Reminders sent.
            
        *   Discounts applied.
            

### **Inventory Module Sub-User Stories**

1.  **Sub-User Story: As an inventory manager, I want a morning dashboard summarizing emails and updates.**
    
    *   **Explanation**: Provides daily start overview.
        
    *   **Tickets**:
        
        *   INV-001: Dashboard build.
            
        *   INV-002: Email integration.
            
    *   **Acceptance Criteria**:
        
        *   Summarizes key emails.
            
        *   Updates highlighted.
            
        *   Customizable widgets.
            
2.  **Sub-User Story: As an inventory manager, I want PO monitoring with alerts for delays and ETA changes.**
    
    *   **Explanation**: Tracks POs with notifications.
        
    *   **Tickets**:
        
        *   INV-003: Monitoring tools.
            
        *   INV-004: Alert system.
            
    *   **Acceptance Criteria**:
        
        *   Delays flagged.
            
        *   ETAs updated.
            
        *   Alerts emailed.
            
3.  **Sub-User Story: As an inventory manager, I want real-time views of on-hand levels, projections, and reorder suggestions.**
    
    *   **Explanation**: Shows current and future stock.
        
    *   **Tickets**:
        
        *   INV-005: Real-time data.
            
        *   INV-006: Projection calc.
            
    *   **Acceptance Criteria**:
        
        *   Live updates.
            
        *   Suggestions accurate.
            
        *   Graphs included.
            
4.  **Sub-User Story: As an inventory manager, I want priority flags for low-stock SKUs with custom thresholds.**
    
    *   **Explanation**: Highlights critical items.
        
    *   **Tickets**:
        
        *   INV-007: Flag logic.
            
        *   INV-008: Threshold settings.
            
    *   **Acceptance Criteria**:
        
        *   Flags auto-set.
            
        *   Thresholds per SKU.
            
        *   Prioritized list.
            
5.  **Sub-User Story: As an inventory manager, I want container tracking integrated with production status updates.**
    
    *   **Explanation**: Monitors shipments and production.
        
    *   **Tickets**:
        
        *   INV-009: Tracking API.
            
        *   INV-010: Status sync.
            
    *   **Acceptance Criteria**:
        
        *   Real-time tracking.
            
        *   Status linked.
            
        *   Maps if geo.
            
6.  **Sub-User Story: As an inventory manager, I want 60-day plan comparisons with adjustment tools.**
    
    *   **Explanation**: Compares actual vs plan and adjusts.
        
    *   **Tickets**:
        
        *   INV-011: Comparison engine.
            
        *   INV-012: Adjustment UI.
            
    *   **Acceptance Criteria**:
        
        *   Differences highlighted.
            
        *   Adjustments saved.
            
        *   Reports generated.
            
7.  **Sub-User Story: As an inventory manager, I want auto-generated daily reports emailed to stakeholders.**
    
    *   **Explanation**: Creates and sends summaries.
        
    *   **Tickets**:
        
        *   INV-013: Report generator.
            
        *   INV-014: Email automation.
            
    *   **Acceptance Criteria**:
        
        *   Reports formatted.
            
        *   Sent daily.
            
        *   Custom recipients.
            
8.  **Sub-User Story: As an inventory manager, I want AI-driven PO recommendations based on stock trends.**
    
    *   **Explanation**: Suggests orders using trends.
        
    *   **Tickets**:
        
        *   INV-015: AI model integration.
            
        *   INV-016: Recommendation display.
            
    *   **Acceptance Criteria**:
        
        *   Suggestions accurate.
            
        *   Based on data.
            
        *   Accept/reject options.
            

### **Logistics Module Sub-User Stories**

1.  **Sub-User Story: As a logistics coordinator, I want PO initiation with deposit processing and lead time confirmations.**
    
    *   **Explanation**: Starts POs with payments and times.
        
    *   **Tickets**:
        
        *   LOG-001: PO init form.
            
        *   LOG-002: Deposit integration.
            
    *   **Acceptance Criteria**:
        
        *   POs created.
            
        *   Deposits processed.
            
        *   Lead times confirmed.
            
2.  **Sub-User Story: As a logistics coordinator, I want automated 5-day pre-completion reminders and RFQ sends to forwarders.**
    
    *   **Explanation**: Reminds and requests quotes near end.
        
    *   **Tickets**:
        
        *   LOG-003: Reminder automation.
            
        *   LOG-004: RFQ sender.
            
    *   **Acceptance Criteria**:
        
        *   Reminders timed.
            
        *   RFQs sent.
            
        *   Responses tracked.
            
3.  **Sub-User Story: As a logistics coordinator, I want forwarder selection tools with cost comparisons.**
    
    *   **Explanation**: Chooses forwarders by comparing.
        
    *   **Tickets**:
        
        *   LOG-005: Selection UI.
            
        *   LOG-006: Comparison table.
            
    *   **Acceptance Criteria**:
        
        *   Costs compared.
            
        *   Selection saved.
            
        *   Filters applied.
            
4.  **Sub-User Story: As a logistics coordinator, I want document collection (CI/PL) and auto-submission to ports.**
    
    *   **Explanation**: Gathers and submits docs.
        
    *   **Tickets**:
        
        *   LOG-007: Doc collector.
            
        *   LOG-008: Auto-submit.
            
    *   **Acceptance Criteria**:
        
        *   Docs uploaded.
            
        *   Submitted auto.
            
        *   Confirmations received.
            
5.  **Sub-User Story: As a logistics coordinator, I want daily tracking updates with ETA notifications.**
    
    *   **Explanation**: Provides shipment tracking.
        
    *   **Tickets**:
        
        *   LOG-009: Tracking API.
            
        *   LOG-010: Notification setup.
            
    *   **Acceptance Criteria**:
        
        *   Daily updates.
            
        *   ETAs notified.
            
        *   History logged.
            
6.  **Sub-User Story: As a logistics coordinator, I want pre-arrival checklists for Arrival Notices.**
    
    *   **Explanation**: Manages pre-arrival tasks.
        
    *   **Tickets**:
        
        *   LOG-011: Checklist builder.
            
        *   LOG-012: Notice handling.
            
    *   **Acceptance Criteria**:
        
        *   Checklists completed.
            
        *   Notices processed.
            
        *   Tasks assigned.
            
7.  **Sub-User Story: As a logistics coordinator, I want payment settlement workflows for suppliers and freight.**
    
    *   **Explanation**: Handles final payments.
        
    *   **Tickets**:
        
        *   LOG-013: Workflow engine.
            
        *   LOG-014: Payment links.
            
    *   **Acceptance Criteria**:
        
        *   Payments settled.
            
        *   Workflows approved.
            
        *   Receipts issued.
            
8.  **Sub-User Story: As a logistics coordinator, I want customs document uploads and query resolution tracking.**
    
    *   **Explanation**: Uploads docs and tracks issues.
        
    *   **Tickets**:
        
        *   LOG-015: Upload system.
            
        *   LOG-016: Query tracker.
            
    *   **Acceptance Criteria**:
        
        *   Uploads secure.
            
        *   Queries resolved.
            
        *   Status updated.
            
9.  **Sub-User Story: As a logistics coordinator, I want drayage scheduling to DC or 3PL with confirmation logs.**
    
    *   **Explanation**: Schedules trucking with logs.
        
    *   **Tickets**:
        
        *   LOG-017: Scheduling tool.
            
        *   LOG-018: Confirmation logging.
            
    *   **Acceptance Criteria**:
        
        *   Schedules set.
            
        *   Confirmations logged.
            
        *   Conflicts avoided.
            
10.  **Sub-User Story: As a logistics coordinator, I want fulfillment PO submissions and delivery confirmations.**
    
    *   **Explanation**: Submits to warehouse and confirms delivery.
        
    *   **Tickets**:
        
        *   LOG-019: PO submit.
            
        *   LOG-020: Confirmation system.
            
    *   **Acceptance Criteria**:
        
        *   POs submitted.
            
        *   Deliveries confirmed.
            
        *   Status closed.