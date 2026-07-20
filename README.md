# 🧾 Invoice Generator

A clean, offline-first Flutter app for creating, managing, and exporting professional invoices — built with Provider state management, local storage, and PDF generation.

---

## 📌 Project Overview

Invoice Generator is a cross-platform Flutter application that lets freelancers and small businesses create professional invoices in minutes. Users can add business and customer details, list multiple products/services with quantity, price, and discount, and the app automatically calculates subtotal, tax, and grand total. Invoices are saved locally on the device, can be exported as PDF, shared via WhatsApp/Email/etc., or printed directly — no internet connection or backend server required.

The project follows a clean folder structure (`screens`, `widgets`, `models`, `services`, `utils`, `database`, `pdf`) and uses the **Provider** package for state management throughout.

---

## ✨ Features

### Invoice Creation
- Auto-generated, sequential invoice numbers (e.g. `INV-001`, `INV-002`, ...)
- Invoice Date and Due Date pickers
- Business information: company name, address, email, phone
- Customer information: name, address, email, phone
- Multiple product/service line items with quantity, unit price, and optional discount
- Auto-calculated **Subtotal**, **Tax**, and **Grand Total**
- Notes / payment instructions field
- Full form validation on all required fields

### Invoice Management
- View all invoices in a scrollable, card-based list
- Search invoices by invoice number or customer name
- Edit existing invoices
- Delete invoices with a confirmation dialog (swipe-to-delete)
- Duplicate an invoice (auto-assigns a new invoice number)
- Change invoice status: **Paid / Unpaid / Overdue**
- Empty state UI when no invoices exist yet

### Export & Sharing
- Generate a polished, branded PDF for any invoice
- Share the PDF via WhatsApp, Email, or any installed app
- Print invoices directly from the device

### Dashboard
- Total Invoices
- Paid Invoices count
- Unpaid Invoices count
- Total Revenue (sum of paid invoices)
- Recent invoices list

### Settings
- Upload a company logo (used on generated PDFs)
- Configure company details (name, address, email, phone)
- Select currency symbol
- Set a default tax percentage
- Customize the invoice number prefix (e.g. `INV-`)

### UI/UX
- Clean, modern Material 3 design
- Responsive layouts for phones and tablets
- Bottom navigation between Dashboard, Invoices, and Settings
- Status chips (Paid/Unpaid/Overdue) with color coding
- Reusable cards, stat tiles, and empty states

---

## 📦 Packages Used

| Package | Purpose |
|---|---|
| [`provider`](https://pub.dev/packages/provider) | App-wide state management (`InvoiceProvider`, `SettingsProvider`) |
| [`sqflite`](https://pub.dev/packages/sqflite) | Local SQLite database for storing invoices |
| [`path`](https://pub.dev/packages/path) | Building file/database paths |
| [`path_provider`](https://pub.dev/packages/path_provider) | Locating the app's documents directory for saving PDFs |
| [`shared_preferences`](https://pub.dev/packages/shared_preferences) | Persisting app settings (company info, currency, tax, prefix) |
| [`pdf`](https://pub.dev/packages/pdf) | Generating invoice PDF documents |
| [`printing`](https://pub.dev/packages/printing) | Printing and previewing generated PDFs |
| [`share_plus`](https://pub.dev/packages/share_plus) | Sharing generated PDF invoices via other apps |
| [`intl`](https://pub.dev/packages/intl) | Date and currency formatting |
| [`uuid`](https://pub.dev/packages/uuid) | Generating unique IDs for invoices and product line items |
| [`image_picker`](https://pub.dev/packages/image_picker) | Uploading a company logo from the gallery |
| [`open_filex`](https://pub.dev/packages/open_filex) | Opening saved PDF files from the device |
| [`cupertino_icons`](https://pub.dev/packages/cupertino_icons) | iOS-style icon set |

Dev dependency: [`flutter_lints`](https://pub.dev/packages/flutter_lints) for static analysis and code quality.

---

## 🛠 Setup Instructions

### Prerequisites
- [Flutter SDK](https://docs.flutter.dev/get-started/install) 3.x or later
- Dart SDK >= 3.0.0
- Android Studio / VS Code with Flutter & Dart plugins
- An emulator or physical device (Android/iOS)

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd invoice_generator
```

### 2. Install dependencies
```bash
flutter pub get
```

### 3. Run the app
```bash
flutter run
```

To run on a specific device:
```bash
flutter devices          # list available devices
flutter run -d <device-id>
```

### 4. Build a release APK (Android)
```bash
flutter build apk --release
```
The output APK will be located at:
```
build/app/outputs/flutter-apk/app-release.apk
```

### 5. Build for iOS
```bash
flutter build ios --release
```

---

## 📁 Project Structure

```
lib/
├── main.dart              # App entry point, providers & theme setup
├── models/                # Invoice, Product, AppSettings
├── database/               # sqflite CRUD helper
├── services/               # InvoiceProvider, SettingsProvider, PdfService
├── pdf/                     # PDF layout builder
├── screens/                 # Dashboard, Invoice List, Form, Detail, Settings
└── widgets/                 # Reusable UI components (cards, chips, empty state)
```

---

## 📝 Notes

- All data is stored **locally on-device** — no backend, no internet connection required.
- Invoices are stored via `sqflite`; settings are stored via `shared_preferences`.
- State management is handled entirely with the `provider` package (`ChangeNotifier`).
