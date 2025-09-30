Project Requirements: StockGrid
1. Executive Summary
This document outlines the functional and non-functional requirements for "StockGrid," a new inventory management system. The system is inspired by the operational model of retailers like CEX, focusing on the buying, selling, and tracking of unique, second-hand items.

Key features include multiple secure login options for staff (NFC card, QR Code, password) accessible from both desktop and mobile devices, and unique QR code generation for every inventory item to streamline tracking. The backend will be powered by Python, with a relational SQL database for robust data management. The architecture will be web-based to ensure it can be hosted locally for development and deployed online for live use, with a mobile-responsive interface allowing staff to use their smartphones as terminals.

2. System Scope
2.1. In-Scope
User authentication via traditional credentials, NFC cards, and QR codes.

Role-based access control (Admin, Staff).

Comprehensive inventory management (adding, searching, updating, grading).

Automatic generation and printing of QR codes for item serial numbers.

Point-of-Sale (POS) functionality for sales and customer buy-ins.

A responsive web application for accessing core system features on desktops and smartphones.

Basic reporting on sales and stock levels.

2.2. Out-of-Scope
Native mobile applications (iOS/Android). The focus is on a web-based experience.

Customer-facing e-commerce website.

Advanced analytics and business intelligence dashboards.

Integration with third-party accounting software.

Employee payroll and HR management.

3. User Roles & Permissions
Administrator:

Full access to all system functionalities.

Can add, edit, and delete staff accounts.

Can assign NFC cards and generate login QR codes for staff.

Can override prices and modify system settings.

Can view and export all reports.

Staff Member:

Can log in using their assigned NFC card, QR code, or username/password.

Can process sales and buy-ins.

Can add new items to the inventory.

Can search for and view item details.

Can print QR code labels for items.

Can view their own sales data for the day.

4. Functional Requirements
4.1. User Management & Authentication
FR-001: The system shall allow administrators to create, view, update, and deactivate staff accounts.

FR-002: Each new staff account must be associated with a unique username and a secure password.

FR-003: The system shall provide a secure login screen for username/password authentication.

FR-004: The system shall interface with a USB NFC reader for desktop use. The web application should also leverage the Web NFC API to allow login via a compatible mobile device's NFC reader.

FR-005: The system shall allow staff to log in by scanning a personal QR code using either a USB barcode scanner (on desktop) or the device's camera via the web app.

FR-006: Administrators must have a dedicated interface to pair a new NFC card's unique ID with a staff account.

FR-007: Administrators must have an interface to generate and print a QR code and/or barcode associated with each staff account for login and reference purposes.

4.2. Inventory Management
FR-008: The system must allow staff to add new items acquired from customers (buy-ins).

FR-009: When adding an item, the user must input the following details:

Category (e.g., Consoles, Games, Phones)

Product Name

Model/Version

Condition/Grade (e.g., A - Mint, B - Good, C - Fair)

Buy-in Price

Suggested Sale Price (can be auto-calculated or manually set)

Customer's Serial Number (if applicable)

FR-010: Upon successful submission of a new item, the system shall:

Generate a unique internal Stock Keeping Unit (SKU).

Generate a QR code that encodes the unique internal SKU.

FR-011: The system shall provide a feature to print the generated QR code onto a physical label for the item.

FR-012: The system must provide a powerful search and filter function to find items based on SKU, name, category, or serial number.

FR-013: Staff must be able to update an item's status (e.g., "In Stock", "Sold", "Awaiting Repair", "Faulty").

4.3. Point of Sale (POS)
FR-014: The POS interface must allow staff to scan an item's QR code (using a USB scanner or phone camera) to add it to a sales transaction.

FR-015: The system shall calculate the total cost of a transaction, including multiple items.

FR-016: Upon completion of a sale, the system shall:

Update the status of the sold items to "Sold".

Log the transaction details (items, total price, date, time, staff member).

Provide an option to print a customer receipt.

FR-017: The POS interface must also handle the buy-in process, linking it to the inventory addition workflow (FR-009).

4.4. Reporting
FR-018: The system shall be able to generate a daily sales report showing total revenue and items sold.

FR-019: The system shall be able to generate an inventory report showing all items currently "In Stock", organized by category.

FR-020: Administrators must be able to filter reports by date range and by staff member.

5. Non-Functional Requirements
NFR-001 (Performance): Item lookups via QR code scan should complete in under 1 second. NFC/QR Code login should authenticate the user in under 2 seconds on a stable connection.

NFR-002 (Security): All passwords must be hashed and salted. The database must be protected from SQL injection attacks. For a future SaaS model, data for different tenants (stores) must be strictly isolated.

NFR-003 (Usability): The user interface (UI) must be clean, intuitive, and require minimal training. The web interface must be responsive, providing a seamless experience on both desktop and mobile devices.

NFR-004 (Reliability): The system should be designed to run continuously during business hours. The database should be backed up automatically on a daily basis. The architecture must be scalable to handle multiple tenants in a SaaS environment.

NFR-005 (Hardware Compatibility): The system must be compatible with standard USB NFC readers and QR code scanners. The web application must be compatible with modern mobile browsers (e.g., Chrome on Android, Safari on iOS) that support the necessary Web APIs for camera and NFC access.

6. Proposed Technology & Hardware Stack
6.1. Software
Backend Language: Python 3.8+

Backend Framework: Django is highly recommended for its built-in admin, ORM, security features, and scalability for SaaS.

Database: PostgreSQL or MySQL (recommended for production), SQLite (for initial local development).

Frontend (GUI): A responsive web application built with HTML/CSS/JavaScript. Using a modern front-end framework like React or Vue.js is strongly advised to manage application state and create a polished user experience on both desktop and mobile.

Key Python Libraries:

psycopg2-binary or mysql-connector-python (database connection).

qrcode (for generating QR codes).

Pillow (for handling QR code images).

pyscard (for direct hardware communication with OMNIKEY reader on the server or a local client).

reportlab (for generating PDF receipts and reports).

6.2. Hardware
Server: A PC for local hosting and testing, with the capability to deploy the application to a cloud server (e.g., AWS, DigitalOcean, Heroku) in the future.

Desktop Terminals: Standard computers with USB ports for scanners and readers.

Mobile Terminals: Staff-owned or company-provided smartphones (iOS/Android) for using the web application on the go.

NFC Reader: A USB-based NFC card reader (e.g., OMNIKEY series) for desktop use.

NFC Cards/Tags: One per staff member (e.g., NTAG215 cards).

2D Barcode Scanner: A USB-based scanner for desktop use (e.g., Symbol 2D scanner).

Printers:

Item Label Printer: A thermal label printer for adhesive QR code stickers.

Reference/Card Printer: A small-format printer for employee login QR codes/barcodes (e.g., Fun Print).

Receipt Printer: A standard POS thermal receipt printer.
