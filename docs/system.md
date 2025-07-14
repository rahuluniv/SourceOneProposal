# Software Architecture
This page includes a short description of the overall architecture style of the system, its high-level system components, and their logical (what data they exchange) and control (how they invoke each other) dependencies. Mostly described using diagrams.

## Architecture Diagram

A NextJS-Django stack built on Docker and hosted on AWS. The frontend will be statically built, the django server will be running on a separate container. The server will be running the business and persistence layers. The DB is postgres and will be a docker volume attached to the Django container. In addition emails will be sent through [Sendgrid](https://sendgrid.com/). The frontend will communicate with the backend using REST in JSON (header + body) format. 

![Arch](https://user-images.githubusercontent.com/34993025/196225758-6a9c2718-0148-4e6e-a7f6-5fc573fcc4e7.png)
## System Workflow
```mermaid
graph TD
    A[RFQ Received Client submits RFQ] --> B[Procurement Gather SKU specs, source manufacturers]
    B -->|Log manufacturer data Store catalogs| C[Quoting Create quotation]
    B --> D[Sampling Manage samples]
    C --> E[Terms & PO Draft terms, issue SO/PO]
    D --> E
    E --> F[Accounting Handle invoices, payments]
    E --> G[Logistics Manage production, shipping]
    F --> H[Inventory Monitor stock, POs]
    G --> H
    H --> I[Delivery Confirm delivery to client]

    B --> B1[Gather SKU Details Dimensions, weight, quantity, material]
    B1 --> B2[Source Manufacturers Global, competitive pricing, high quality]
    B2 --> B3[Log Data Company, address, website, email, phone, status]
    B3 --> B4[Store Catalogs Shared drive]

    C --> C1[Product Listing List products, estimate annual cases]
    C1 --> C2[Verify Details Quantity, price, dimensions, pallet fit]
    C2 --> C3[Source Missing Products Request pricing, dimensions]
    C3 --> C4[Compute Costs CBM, pallet, fulfillment, freight, duties]
    C4 --> C5[Consult Logistics Validate delivery, freight costs]
    C5 --> C6[Finalize Quotation Landed cost, selling price, margin]

    D --> D1[Check Samples Available or create molds]
    D1 --> D2[QA Samples Internal quality assurance]
    D2 --> D3[Client Approval Send for testing]

    E --> E1[Draft Term Sheet Prepare terms]
    E1 --> E2[Legal Review Ensure compliance]
    E2 --> E3[Client Signature Send to client]
    E3 --> E4[Issue SO/PO Send to manufacturer]

    F --> F1{Order Type Client or inventory-triggered}
    F1 -->|Client-Initiated| F2[Receive Client PO]
    F1 -->|Inventory-Triggered| F3[Flag Replenishment]
    F2 --> F4[Generate Invoice Source One invoice]
    F3 --> F5[Place Order With manufacturer]
    F4 --> F6[Receive Manufacturer Invoice]
    F5 --> F6
    F6 --> F7[Categorize Invoices AP: Manufacturer, freight AR: Client]
    F7 --> F8[Process Payments Deposit, final payment, wire confirmation]
    F8 --> F9[Track Client Payments Delivery, amounts, discounts]

    H --> H1[Daily Start Open Gmail, Roam, Sheets]
    H1 --> H2[Review Emails Follow-ups, PO drafts]
    H2 --> H3[Check POs Delivery windows, delays]
    H3 --> H4[Review Inventory Stock levels, arrivals]
    H4 --> H5[Monitor SKUs Low stock, sampling]
    H5 --> H6[Track Containers Production, shipping]
    H6 --> H7[Check 60-Day Plan Adjust stock goals]
    H7 --> H8[Daily Report Concise, bold key info]

    G --> G1[Production Order Issue PO, confirm lead time]
    G1 --> G2[5-Day Check Verify production, request RFQs]
    G2 --> G3[Freight Booking Select forwarder, collect CI/PL]
    G3 --> G4[Port Handover ISF, draft BL to customs]
    G4 --> G5[In-Transit Monitoring Track shipment, ETA updates]
    G5 --> G6[Pre-Arrival Obtain Arrival Notice]
    G6 --> G7[Financial Settlement Pay supplier, freight, secure BL]
    G7 --> G8[Customs Clearance Send CI/PL, resolve queries]
    G8 --> G9[Drayage & Pickup Arrange trucker or 3PL]
    G9 --> G10[Final Fulfillment Pick, pack, deliver]

    classDef process fill:#f9f,stroke:#333,stroke-width:2px;
    class A,B,C,D,E,F,G,H,I process;
    classDef subprocess fill:#bbf,stroke:#333,stroke-width:1px;
    class B1,B2,B3,B4,C1,C2,C3,C4,C5,C6,D1,D2,D3,E1,E2,E3,E4,F2,F3,F4,F5,F6,F7,F8,F9,H1,H2,H3,H4,H5,H6,H7,H8,G1,G2,G3,G4,G5,G6,G7,G8,G9,G10 subprocess;
    classDef decision fill:#ff9,stroke:#333,stroke-width:2px;
    class F1 decision;
```

## Sequence Diagram
> - ![Sequence Diagram](assets/sq.svg)

## MindMap
> - ![MindMap](assets/mindmap.svg)
