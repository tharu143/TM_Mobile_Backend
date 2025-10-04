# Retail Management System - Backend API

## Overview
This is a Flask-based backend API for a retail management system that handles inventory, sales, customers, and product management for a mobile and accessories retail business. The application uses MongoDB (Atlas) as the database and GridFS for image storage.

## Project Architecture

### Technology Stack
- **Framework**: Flask 3.1.2
- **Database**: MongoDB Atlas (Cloud-hosted)
- **File Storage**: GridFS (for product images)
- **Image Processing**: Werkzeug for secure file uploads
- **Excel Support**: openpyxl for import/export functionality
- **CORS**: Flask-CORS for cross-origin requests
- **Production Server**: Gunicorn

### Project Structure
```
.
├── app.py                  # Main Flask application
├── requirements.txt        # Python dependencies
├── uploads/               # Directory for uploaded images
│   └── cofee-removebg-preview.png
├── .gitignore            # Git ignore file
└── replit.md             # This documentation file
```

## Core Features

### 1. Product Management
- CRUD operations for products (mobiles and accessories)
- Image upload and storage using GridFS
- Stock management with automatic tracking
- Barcode generation and management
- Category-based organization (Mobile/Accessories)
- Minimum stock level alerts

### 2. Sales Management
- Sales transaction recording
- Customer purchase history
- Sales analytics and reports
- Monthly and yearly sales reports

### 3. Inventory Management
- Stock addition tracking
- Low stock alerts
- Excel import/export for bulk operations
- Stock movement reports

### 4. Customer Management
- Customer information storage
- Purchase history tracking
- Customer analytics

### 5. Settings Management
- GST configuration (enable/disable, percentage)
- Print settings (shop name, address, GSTIN)

## API Endpoints

### Products
- `GET /api/products` - Get all products
- `POST /api/products` - Add new product
- `PUT /api/products/<id>` - Update product
- `DELETE /api/products/<id>` - Delete product
- `PUT /api/products/<id>/stock` - Update product stock

### Mobiles
- `GET /api/mobiles` - Get all mobile types
- `POST /api/mobiles` - Add new mobile type
- `PUT /api/mobiles/<id>` - Update mobile type
- `DELETE /api/mobiles/<id>` - Delete mobile type

### Accessories
- `GET /api/accessories` - Get all accessory types
- `POST /api/accessories` - Add new accessory type
- `PUT /api/accessories/<id>` - Update accessory type
- `DELETE /api/accessories/<id>` - Delete accessory type

### Sales
- `GET /api/sales` - Get all sales
- `POST /api/sales` - Record new sale
- `GET /api/sales/<id>` - Get specific sale
- `DELETE /api/sales/<id>` - Delete sale

### Customers
- `GET /api/customers` - Get all customers
- `POST /api/customers` - Add new customer
- `PUT /api/customers/<id>` - Update customer
- `DELETE /api/customers/<id>` - Delete customer

### Reports
- `GET /api/reports/monthly?year=<year>&month=<month>` - Monthly stock report
- `GET /api/reports/yearly?year=<year>` - Yearly stock report

### Settings
- `GET /api/settings` - Get GST settings
- `POST /api/settings` - Update GST settings
- `GET /api/print` - Get print settings
- `POST /api/print` - Update print settings

### Import/Export
- `POST /api/import/products` - Import products from Excel
- `GET /api/export/mobiles-template` - Export mobile products template
- `GET /api/export/accessories-template` - Export accessories products template

### Images
- `GET /api/images/<image_id>` - Serve image from GridFS
- `GET /Uploads/<filename>` - Serve uploaded files

## Database Collections

1. **products** - Product information
2. **mobiles** - Mobile device types
3. **accessories** - Accessory types
4. **sales** - Sales transactions
5. **customers** - Customer information
6. **settings** - Application settings (GST)
7. **print** - Print settings (shop details)
8. **stock_additions** - Stock movement tracking
9. **fs.files** & **fs.chunks** - GridFS file storage

## Environment Variables

### MongoDB Connection
- `MONGODB_URI` - MongoDB Atlas connection string (optional, defaults to embedded URI)

**Important**: For production use, set the `MONGODB_URI` environment variable to secure your database credentials.

## Development

### Running Locally
The application is configured to run on port 5000:
```bash
python app.py
```

### Production Deployment
The application uses Gunicorn for production deployment:
```bash
gunicorn --bind=0.0.0.0:5000 --reuse-port app:app
```

## Security Considerations

1. **Database Credentials**: MongoDB credentials are currently embedded in the code but can be overridden with the `MONGODB_URI` environment variable
2. **CORS**: Currently configured to allow all origins (`*`) - should be restricted in production
3. **File Uploads**: Limited to image files (png, jpg, jpeg, gif)
4. **Debug Mode**: Disabled for production use

## Recent Changes

- **2025-10-04**: Initial Replit setup
  - Installed Python 3.11 and dependencies
  - Configured Flask to bind to 0.0.0.0:5000
  - Set up development workflow
  - Configured deployment with Gunicorn
  - Added .gitignore for Python project
  - Moved MongoDB credentials to environment variable support

## Notes

- This is a backend API only - frontend must be developed separately
- All API routes are prefixed with `/api/`
- Images can be stored either in GridFS or the local uploads folder
- The application supports Excel import/export for bulk product management
