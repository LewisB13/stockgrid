# StockGrid Folder Structure

StockGrid/
├── backend/                    # Flask/FastAPI backend API
│   ├── app.py                  # Main API entry point
│   ├── routes/                 # API route modules
│   │   ├── auth.py             # Authentication endpoints (NFC/QR)
│   │   ├── inventory.py        # Inventory management endpoints
│   │   └── repairs.py          # Repair log endpoints
│   ├── models/                 # Database models
│   │   ├── user.py
│   │   ├── item.py
│   │   └── repair.py
│   ├── utils/                  # Utility scripts
│   │   ├── db.py               # Database connection & helper functions
│   │   └── helpers.py          # Misc utility functions
│   └── requirements.txt        # Backend dependencies
│
├── desktop_client/             # Python GUI desktop application
│   ├── main.py                 # Entry point for the GUI
│   ├── gui/                    # GUI modules
│   │   ├── nfc_reader.py       # NFC reading logic
│   │   ├── qr_scanner.py       # QR/barcode scanning logic
│   │   └── interface.py        # Tkinter/PyQt GUI layout
│   ├── api_client.py           # Communicates with backend API
│   ├── assets/                 # Images, icons, QR templates
│   └── requirements.txt        # Desktop client dependencies
│
├── mobile_dashboard/           # Optional lightweight web/mobile frontend
│   ├── index.html
│   ├── css/
│   └── js/
│
├── scripts/                    # Utility and deployment scripts
│   ├── uptime.py               # Script to ping Heroku backend and keep dyno awake
│   └── deploy.sh               # Deployment helper scripts (optional)
│
├── docs/                       # Documentation, notes, CV snippets
│   └── README.md
│
└── .gitignore                  # Git ignore file
