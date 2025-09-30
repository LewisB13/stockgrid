# StockGrid: Inventory Management System

StockGrid is a web-based inventory management and Point-of-Sale (POS) system designed for retailers that buy, sell, and track unique, second-hand items. Inspired by the operational model of retailers like CEX, it streamlines inventory control by assigning a unique QR code to every item and offers flexible, secure login options for staff.

The application is built with a Python backend and a responsive frontend, allowing it to be used on both desktop terminals and mobile devices.

## ✨ Key Features

- [ ] **Multi-Factor Staff Authentication**: Secure login via username/password, scannable QR codes, or NFC cards.
- [ ] **Role-Based Access Control**: Differentiated permissions for **Administrator** and **Staff Member** roles.
- [ ] **Comprehensive Inventory Management**: Add, search, grade, and update the status of unique items.
- [ ] **Automatic QR Code Generation**: Instantly create and print unique QR code labels for every item upon intake, linking it to a unique SKU.
- [ ] **Integrated Point-of-Sale (POS)**: A unified interface to handle both customer sales and buy-ins.
- [ ] **Mobile-Responsive Design**: Enables staff to use their smartphones as mobile terminals for inventory management and sales.
- [ ] **Reporting**: Generate daily sales reports and current stock level reports.

---

## 💻 Proposed Technology Stack

### Software
- [ ] **Backend Language**: Python 3.8+
- [ ] **Backend Framework**: **Django** (Recommended)
- [ ] **Database**: **PostgreSQL** or **MySQL** (Production), **SQLite** (Development)
- [ ] **Frontend Framework**: **React** or **Vue.js** (Recommended) with HTML/CSS/JavaScript
- [ ] **Key Python Libraries**:
    - [ ] `psycopg2-binary` / `mysql-connector-python`: Database drivers
    - [ ] `qrcode`: For generating QR code images
    - [ ] `Pillow`: Image processing library
    - [ ] `pyscard`: NFC hardware communication
    - [ ] `reportlab`: PDF generation for reports and receipts

### Hardware
- [ ] **Server**: Local PC for development; cloud server (AWS, Heroku, etc.) for production.
- [ ] **Terminals**: Desktop computers and modern iOS/Android smartphones.
- [ ] **NFC Reader**: USB-based reader (e.g., OMNIKEY series).
- [ ] **Barcode Scanner**: Standard USB-based 2D QR code scanner.
- [ ] **Printers**:
    - [ ] **Label Printer**: For printing adhesive QR code stickers.
    - [ ] **Receipt Printer**: Standard POS thermal printer.

---

## 📋 System Scope

### In Scope ✔️
- [ ] User authentication (Password, NFC, QR code).
- [ ] Admin and Staff roles with distinct permissions.
- [ ] Full inventory lifecycle management (add, search, update status, grade items).
- [ ] Automated generation and printing of item QR codes.
- [ ] Point-of-Sale (POS) for sales and buy-ins.
- [ ] Responsive web application for desktop and mobile access.
- [ ] Basic sales and stock reports.

### Out of Scope ❌
- [ ] Native iOS/Android applications.
- [ ] A public, customer-facing e-commerce website.
- [ ] Advanced business intelligence or analytics dashboards.
- [ ] Integration with third-party accounting software.
- [ ] HR features like payroll management.

---

## 👤 User Roles & Permissions

### 👑 Administrator
- [ ] **Full System Access**: Can perform all actions.
- [ ] **User Management**: Create, edit, and delete staff accounts.
- [ ] **Credential Assignment**: Assign NFC cards and generate login QR codes for staff.
- [ ] **System Overrides**: Modify prices and adjust system settings.
- [ ] **Reporting**: View and export all system reports.

### 👥 Staff Member
- [ ] **Login**: Access the system with an assigned NFC card, QR code, or username/password.
- [ ] **Transactions**: Process customer sales and buy-ins.
- [ ] **Inventory**: Add new items, search the database, and print QR labels.
- [ ] **Reporting**: View their personal sales data for the current day.

---

## ⚙️ Functional Requirements

### FR-1: User Management & Authentication
- [ ] **FR-001**: Admins can create, view, update, and deactivate staff accounts.
- [ ] **FR-002**: Staff accounts require a unique username and a secure password.
- [ ] **FR-003**: A secure login screen for username/password authentication.
- [ ] **FR-004**: Support for USB NFC readers (desktop) and Web NFC API (mobile) for login.
- [ ] **FR-005**: Support for login by scanning a personal QR code via a USB scanner or mobile camera.
- [ ] **FR-006**: Admin interface to pair a new NFC card's ID with a staff account.
- [ ] **FR-007**: Admin interface to generate and print a unique login QR code for a staff member.

### FR-2: Inventory Management
- [ ] **FR-008**: Staff can add new items acquired from customers (buy-ins).
- [ ] **FR-009**: Adding an item requires: Category, Product Name, Model, Condition/Grade, Buy-in Price, and Sale Price.
- [ ] **FR-010**: The system must automatically generate a unique internal SKU and a corresponding QR code for each new item.
- [ ] **FR-011**: A feature to print the generated QR code onto a physical label.
- [ ] **FR-012**: A search function to find items by SKU, name, category, or serial number.
- [ ] **FR-013**: Staff can update an item's status (e.g., "In Stock", "Sold", "Awaiting Repair").

### FR-3: Point of Sale (POS)
- [ ] **FR-014**: Scan an item's QR code to add it to a sales transaction.
- [ ] **FR-015**: The system shall calculate the total cost for all items in a transaction.
- [ ] **FR-016**: On sale completion, the system must update item statuses to "Sold", log the transaction, and provide a receipt printing option.
- [ ] **FR-017**: The POS interface must support the buy-in workflow, linking directly to the item addition process.

### FR-4: Reporting
- [ ] **FR-018**: Generate a daily sales report (total revenue, items sold).
- [ ] **FR-019**: Generate an inventory report of all items currently "In Stock".
- [ ] **FR-020**: Admins can filter reports by date range and by staff member.

---

## 🚀 Non-Functional Requirements

- [ ] **Performance (`NFR-001`)**:
    - [ ] Item lookup via QR scan: **< 1 second**.
    - [ ] NFC/QR Code login authentication: **< 2 seconds**.
- [ ] **Security (`NFR-002`)**:
    - [ ] Passwords must be hashed and salted.
    - [ ] The application must be protected against SQL injection.
    - [ ] (Future) Data must be isolated for different tenants in a SaaS model.
- [ ] **Usability (`NFR-003`)**:
    - [ ] The UI must be clean, intuitive, and responsive on both desktop and mobile.
- [ ] **Reliability (`NFR-004`)**:
    - [ ] Designed for continuous operation during business hours.
    - [ ] Automated daily database backups.
- [ ] **Compatibility (`NFR-005`)**:
    - [ ] Must work with standard USB NFC readers and QR code scanners.
    - [ ] Web app must be compatible with modern mobile browsers (Chrome, Safari) that support Web APIs for camera and NFC access.