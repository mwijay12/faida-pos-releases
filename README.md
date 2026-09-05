# 🧾 Faida HQ POS / NexaBill — Offline-First Point of Sale & Smart Retail Copilot for Tanzania

> **Current Version:** v1.0.0 | **Status:** 🟢 Production Ready | **Platform:** Android (Primary), Web, iOS
> **Application Package:** `com.faida.app` | **Target Architecture:** Clean Architecture with BLoC & Hive

---

## 📦 SECTION 1: PROJECT IDENTITY

### 🧾 Faida HQ POS — Biashara Yako Mkononi Mwako

**To a shopkeeper:** Ni mfumo kamili wa kisasa wa kusimamia mauzo, stoo, madeni ya wateja (Deni Notebook), matumizi, na kutoa risiti za Bluetooth bila kutegemea intaneti. Una uwezo wa kuskani barcode, kuoanisha malipo ya simu (M-Pesa, Tigo Pesa, Airtel Money), na msaidizi mahiri wa AI (Faida AI Copilot) anayekushauri jinsi ya kukuza faida ya duka lako.

**To a developer:** Faida HQ POS is an enterprise-grade Flutter offline-first point-of-sale application adhering to strict Clean Architecture (Presentation, Domain, Data) with `flutter_bloc` state management, zero-latency Hive local storage as the single source of truth, `get_it` dependency injection, `fpdart` functional error handling, and `go_router` declarative routing. It features hardware integrations with `mobile_scanner` (camera barcode engine) and `print_bluetooth_thermal` (ESC/POS protocol), combined with optional cloud mirroring to Firebase Firestore and high-speed LLM integration (Gemini 2.5 Flash & Groq Qwen 3.6).

**The business problem it solves:** Small and medium retail shops in Tanzania frequently lose sales and inventory accountability when internet connections fail, power outages occur, or when credit debts written in paper notebooks are lost or forgotten. Existing cloud-only POS systems require monthly subscriptions and specialized POS terminals. Faida HQ POS turns any standard Android phone into an independent, offline-first, all-in-one POS terminal with zero recurring cloud fees.

---

## 🌟 KEY CAPABILITIES & KILLER FEATURES

1. **📒 Tanzanian "Deni" (Credit) Tracker:**

   - Digitizes the traditional duka credit notebook with zero paper clutter.
   - Normalizes Tanzanian phone numbers (`+255`, `07...`, `06...`).
   - Real-time running balance tracking and partial payment settlements with banknote chips (1k, 2k, 5k, 10k, full).
   - Urgency visual color coding: Green (<14 days), Orange (14–30 days), Red (>30 days).
   - 1-Tap Swahili SMS Payment Reminders pre-filled to launch the native SMS app.
2. **🧠 Faida AI Advisor & Financial Copilot:**

   - Multi-provider AI generation powered by Google Gemini 2.5 Flash and Groq Qwen 3.6 with sub-2s responses.
   - Natural language expense recording: type or speak *"Nimelipa 5,000 ya usafi"* or *"Rent 150000"* to auto-categorize and deduct from net profit.
   - Bilingual financial insights and actionable retail recommendations.
   - 100% deterministic offline fallback advisor when network is unavailable.
3. **☁️ Hybrid Cloud Mirroring & Google OAuth (`com.faida.app`):**

   - Hive local database serves as the instantaneous source of truth.
   - Automated `sync_pending_queue` that flushes local updates to Firebase Firestore whenever an internet connection is detected.
   - Google Sign-In with validated SHA-1 and SHA-256 Android keystore fingerprints.
4. **🖨️ ESC/POS Thermal Printer Hub:**

   - Connects to Bluetooth Thermal Printers (POS-5802, Sunmi, Xprinter 58/80), Wi-Fi Network Socket (:9100), and USB OTG.
   - Supports 58mm, 72mm, and 80mm roll sizes with TRA VAT (18%) and TIN formatting.
5. **🔔 In-App Notifications & Promotional Offers Hub (`/notifications`):**

   - Header notification bell with live unread badge counter replaces redundant scanner buttons.
   - Categorized tabs: All, Offers & Promos (hardware discounts, partner offers), Alerts (stock & debt warnings), Tips (store intelligence).
   - Dismissible cards, one-tap actions, and "Mark all read" with Hive offline persistence.
6. **🏆 Gamification & Store Achievements:**

   - 10+ business milestone achievements with XP points (AI Pioneer, First Expense Logged, Super Scanner, Debt Recovery Master, Inventory Master).
   - Clean Material 3 vector badges and level progression without emoji clutter.
7. **🛡️ Cart Safety, Clean Vector Iconography & Fluid UI:**

   - `PopScope` safeguards preventing accidental cart clearing on Android back press.
   - 100% Vector Iconography: standard Material Design icons across Onboarding, Business Type selection (Pharmacy, Supermarket, Hardware, etc.), Slide-to-Launch POS, and Home indicators.
   - Overflow-free layout architecture tested across various screen densities and mobile orientations.

---

## 🎨 SECTION 2: BRAND DESIGN SYSTEM & DEFAULT SYSTEM COLORS

When a merchant installs and opens Faida HQ POS for the very first time, the application initializes with its signature **Faida Royal Identity** palette. Designed specifically for retail and kiosk environments, this default palette pairs financial authority with glare-free outdoor readability:

### 🌟 Default Installation Color Palette (Fresh Install)

| UI Role                         | Color Name                           | Hex Code                  | Visual Token                        | Description & Usage                                                                                                                                  |
| ------------------------------- | ------------------------------------ | ------------------------- | ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Primary Brand**         | **Faida Royal Blue**           | `#1E40AF`               | `AppTheme.primaryBlue`            | The anchor brand color. AppBars, primary CTAs ("Slide to Launch POS", "Review Order", "Complete & Print"), active tab indicators, and brand headers. |
| **Active / Focus Accent** | **Electric Blue**              | `#2563EB`               | `AppTheme.electricBlue`           | Interactive highlights, focused input borders, elevated badges, and button gradient accents.                                                         |
| **Promotions & Offers**   | **Warm Amber / Gold / Yellow** | `#F59E0B` / `#D97706` | `NotificationCategory.offer`      | In-app promotional banners, partner hardware discounts, notification badges, and star ratings.                                                       |
| **Alert & Accent Orange** | **Accent Orange**              | `#E8590C`               | `AppTheme.accentOrange`           | High-visibility action badges, pending cloud sync indicators, and special promotional callouts.                                                      |
| **Card & Surface Base**   | **Pure White**                 | `#FFFFFF`               | `Colors.white` / `surfaceColor` | Clean card containers, modal dialogue backgrounds, receipt previews, and slider thumb handles.                                                       |
| **Application Canvas**    | **Clean Slate Off-White**      | `#F8FAFC`               | `AppTheme.backgroundColor`        | Eye-friendly, anti-glare scaffold background preventing glare in sunny kiosk environments while giving pure white cards crisp visual elevation.      |
| **Primary Text**          | **Midnight Slate Dark**        | `#0F172A`               | `AppTheme.textDark`               | High-contrast typography for large prices, product titles, invoice totals, and headings (exceeds WCAG AAA accessibility standards).                  |
| **Muted Labels**          | **Slate Grey**                 | `#64748B` / `#94A3B8` | `Colors.grey[600]`                | Timestamps, secondary subtitles, units (`pcs`, `kg`), and table headers.                                                                         |
| **Success & Profit**      | **Emerald Green**              | `#059669` / `#10B981` | `AppTheme.emeraldGreen`           | Net profit metrics, completed sales confirmation, full debt clearance, and online sync status.                                                       |
| **Urgent & Overdue**      | **Crimson Red**                | `#EF4444` / `#DC2626` | `AppTheme.errorColor`             | Overdue credit (>30 days), expense deductions, low-stock warnings, and delete confirmations.                                                         |

### 🎛️ Storefront Theme Customization (Settings → Appearance)

Merchants can change their theme color or typography at any time from **Settings → Appearance & Theme**, instantly updating the entire app:

- **Preset Palettes:**
  - 🔵 **Sapphire (Default)** (`#1E40AF` / `#0284C7`) — Classic financial blue & sky blue.
  - 🟢 **Emerald** (`#059669` / `#10B981`) — Rich green for grocers, pharmacies, and agro-vet shops.
  - 🌑 **Midnight** (`#0F172A` / `#334155`) — Deep obsidian slate for high-end retail and electronics.
  - 🌊 **Ocean** (`#2563EB` / `#06B6D4`) — Vibrant electric blue with cyan accents.
  - 🍯 **Amber** (`#D97706` / `#F59E0B`) — Warm golden amber for bakeries, cafes, and restaurants.
  - 🔴 **Ruby** (`#DC2626` / `#F87171`) — Rich crimson red for fast-moving retail.
  - 🟣 **Indigo** (`#4F46E5` / `#818CF8`) — Regal indigo for contemporary storefronts.
  - 🩵 **Teal** (`#0D9488` / `#14B8A6`) — Deep sea teal for health and beauty shops.
  - 🔮 **Plum** (`#7E22CE` / `#A855F7`) — Luxury purple for salons and boutique fashion.
- **Dynamic Google Fonts Engine:** Inter (default), Outfit, Poppins, Roboto, and Plus Jakarta Sans.

---

## 📊 SECTION 3: LIVE SYSTEM SNAPSHOT

### Component Status Table

| Component                          | Status           | What It Does                                               | Tech Used                              |
| ---------------------------------- | ---------------- | ---------------------------------------------------------- | -------------------------------------- |
| **Deni (Credit) Tracker**    | ✅ Fully Working | Manages customer credit, partial payments, SMS reminders   | Hive, BLoC, url_launcher               |
| **Faida AI Advisor**         | ✅ Fully Working | Conversational financial intelligence & expense logger     | Gemini 2.5 Flash, Groq                 |
| **Barcode Scanner**          | ✅ Fully Working | Real-time camera scanner with custom quantity preview      | `mobile_scanner`                     |
| **Cart Management**          | ✅ Fully Working | Add/remove/update quantity with PopScope safety            | BLoC State,`equatable`               |
| **Product CRUD & Stock**     | ✅ Fully Working | Inventory management with instant search & AI descriptions | Hive, BLoC                             |
| **In-App Notifications Hub** | ✅ Fully Working | In-app alerts, partner offers & promos, store tips         | Hive, ValueNotifier, GoRouter          |
| **Gamification & Badges**    | ✅ Fully Working | Business milestones, XP levels, operational achievements   | Hive, Clean Vector Icons               |
| **Thermal Receipt Printing** | ✅ Fully Working | ESC/POS receipt generation for 58/72/80mm rolls            | `print_bluetooth_thermal`, ESC/POS   |
| **Analytics & Reports**      | ✅ Fully Working | Visual donut charts, PDF reports, CSV export               | `printing`, `pdf`, `csv`         |
| **Firebase Cloud Sync**      | ✅ Fully Working | Offline queue with background Firestore sync & Auth        | `cloud_firestore`, `firebase_auth` |
| **Mobile Money QR**          | ✅ Fully Working | Dynamic payment QR for M-Pesa, Tigo Pesa, Airtel Money     | `pretty_qr_code`                     |

---

## 🏗️ SECTION 4: SYSTEM ARCHITECTURE

### ASCII Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                     USER INTERFACE                            │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌─────────────┐  │
│  │Onboarding│  │  Home    │  │ Checkout │  │  Settings    │  │
│  │  Page    │  │  Page    │  │  Page    │  │   Page      │  │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └──────┬──────┘  │
│       │             │             │               │          │
│  ┌────┴─────────────┴─────────────┴───────────────┴──────┐  │
│  │               GoRouter (Declarative Routing)           │  │
│  └───────────────────────────┬───────────────────────────┘  │
│                              │                              │
│  ┌───────────────────────────┴───────────────────────────┐  │
│  │              PRESENTATION LAYER (BLoCs)                │  │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌────────┐ │  │
│  │  │ProductBloc│  │ShopBloc  │  │BillingBloc│  │Printer │ │  │
│  │  │          │  │          │  │          │  │Bloc    │ │  │
│  │  └────┬─────┘  └────┬─────┘  └────┬─────┘  └───┬────┘ │  │
│  └──────────┼──────────┼──────────────┼────────────┼──────┘  │
│             │          │              │            │         │
│  ┌──────────┴──────────┴──────────────┴────────────┴──────┐  │
│  │              DOMAIN LAYER (Use Cases + Entities)         │  │
│  │  ┌────────────────┐  ┌────────────────┐                 │  │
│  │  │ GetProductsUC  │  │ AddProductUC   │                 │  │
│  │  │ UpdateProductUC│  │ DeleteProductUC│                 │  │
│  │  │ GetProductByBC │  │ GetShopUC      │                 │  │
│  │  │ UpdateShopUC   │  │                │                 │  │
│  │  └────────────────┘  └────────────────┘                 │  │
│  └───────────────────────┬─────────────────────────────────┘  │
│                          │                                    │
│  ┌───────────────────────┴─────────────────────────────────┐  │
│  │              REPOSITORY LAYER (Contracts + Impl)         │  │
│  │  ┌────────────────┐  ┌────────────────┐                 │  │
│  │  │ ProductRepo    │  │ ShopRepo       │                 │  │
│  │  │ ProductRepoImpl│  │ ShopRepoImpl   │                 │  │
│  │  └───────┬────────┘  └───────┬────────┘                 │  │
│  └───────────┼──────────────────┼──────────────────────────┘  │
│              │                  │                             │
│  ┌───────────┴──────────────────┴──────────────────────────┐  │
│  │              DATA LAYER (Hive Database)                   │  │
│  │  ┌──────────────┐  ┌──────────┐  ┌────────────────────┐ │  │
│  │  │ Products Box  │  │ Shop Box│  │ Settings/Trans Box │ │  │
│  │  │ (Hive)        │  │ (Hive)  │  │ (Hive)             │ │  │
│  │  └──────────────┘  └──────────┘  └────────────────────┘ │  │
│  └──────────────────────────────────────────────────────────┘  │
│                              │                                 │
│  ┌───────────────────────────┴──────────────────────────────┐  │
│  │              HARDWARE INTEGRATIONS                        │  │
│  │  ┌──────────────────┐  ┌──────────────────────────┐      │  │
│  │  │ MobileScanner    │  │ PrintBluetoothThermal    │      │  │
│  │  │ (Camera)         │  │ (Bluetooth Printer)      │      │  │
│  │  └──────────────────┘  └──────────────────────────┘      │  │
│  └──────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────┘
```

### Step-by-Step: What Happens When a User Checks Out

1. **User taps "Review Order"** on the HomePage bottom sheet button
2. The scanner stops (`_scannerController.stop()`) and GoRouter navigates to `/checkout`
3. The `CheckoutPage` widget mounts and reads `BillingState` via `BlocBuilder<BillingBloc, BillingState>`
4. It also reads `ShopState` via `BlocBuilder<ShopBloc, ShopState>` to get shop name and UPI ID
5. The user selects a payment method — default is "M-Pesa" — by tapping one of 4 `_buildPaymentOption` chips
6. If a non-cash method is selected and the shop has a UPI ID, a QR code renders via `PrettyQrView.data()` with UPI intent string: `upi://pay?pa={upiId}&pn={shopName}&am={total}&cu=TZS`
7. User taps **"Complete & Print"** — this dispatches `PrintReceiptEvent` with shop details
8. `BillingBloc._onPrintReceipt()` fires:
   - Checks if printer is connected via `PrinterHelper.isConnected`
   - If not connected, attempts auto-connect using saved MAC from `HiveDatabase.settingsBox`
   - If connection fails, emits error state → snackbar shows "Failed to connect to printer!"
9. If connected, emits `isPrinting: true` → button shows loading spinner
10. Constructs `items` list as `List<Map<String, dynamic>>` for each cart item
11. Calls `printerHelper.printReceipt()` which builds ESC/POS byte commands:
    - Init sequence `[0x1B, 0x40]`
    - Shop name centered, bold, large font
    - Address lines, phone number
    - Date/time formatted `dd-MM-yyyy hh:mm a`
    - Dashed separator line
    - Item rows: "2x Sugar 3,500 7,000"
    - Dashed separator
    - Right-aligned bold TOTAL
    - Centered footer text
    - Additional line feeds for paper cutting
12. **Post-sale processing** executes after printing (not on print failure):
    - Calls `ProductRepository.updateStock()` for each cart item to reduce stock
    - Creates a `Transaction` object with UUID, timestamp, items, total, payment method
    - Saves transaction via `TransactionRepository.saveTransaction()` → Hive transactions box
    - Emits `printSuccess: true` → snackbar "Printed successfully"
13. After completion, `PrintReceiptEvent` state update triggers UI to show success

---

## 📁 SECTION 5: COMPLETE FILE STRUCTURE

```
flutter_billing_app-main/
│
├── .gitignore                              # Git ignore rules (platform builds, .env, etc.)
├── .metadata                               # Flutter project metadata (auto-generated)
├── analysis_options.yaml                   # Dart linting rules and static analysis config
├── pubspec.yaml                            # Project manifest: dependencies, SDK constraints, assets
├── pubspec.lock                            # Locked dependency versions (auto-generated)
├── README.md                               # ← You are here (project documentation)
│
├── android/                                # Android platform files (Gradle, manifest, Kotlin)
│   ├── app/
│   │   ├── build.gradle.kts                # App-level Gradle config (minSdk, targetSdk, etc.)
│   │   └── src/main/
│   │       ├── AndroidManifest.xml          # Permissions (camera, bluetooth, location)
│   │       └── kotlin/.../MainActivity.kt  # Flutter Android entry point
│   ├── build.gradle.kts                    # Project-level Gradle config
│   ├── settings.gradle.kts                 # Gradle settings
│   └── gradle.properties                   # Gradle properties (AGP version, etc.)
│
├── ios/                                    # iOS platform files (Xcode project, Swift)
│   ├── Runner/                             # iOS app target
│   │   ├── Info.plist                      # Permissions strings (camera, bluetooth)
│   │   ├── AppDelegate.swift               # Flutter iOS entry point
│   │   └── Runner-Bridging-Header.h        # Swift/ObjC bridging header
│   └── Podfile                             # CocoaPods dependencies for iOS
│
├── web/                                    # Web platform files
│   ├── index.html                          # Web entry point, PWA meta tags, favicon
│   ├── manifest.json                       # PWA manifest for installable web app
│   └── icons/                              # PWA icons (192x192, 512x512, etc.)
│
├── test/                                   # Unit and widget tests
│   └── widget_test.dart                    # Default Flutter widget test
│
├── lib/                                    # ── MAIN APPLICATION CODE ──
│   │
│   ├── main.dart                           # App entry: init Hive, DI, run MyApp with MultiBlocProvider
│   │
│   ├── config/
│   │   └── routes/
│   │       └── app_routes.dart             # GoRouter config: all route definitions (/, /checkout, /settings, etc.)
│   │
│   ├── core/
│   │   ├── service_locator.dart            # get_it DI: registers all BLoCs, use cases, repositories as singletons/factories
│   │   │
│   │   ├── data/
│   │   │   └── hive_database.dart          # Hive init: registers adapters, opens product/shop/settings/transaction boxes
│   │   │
│   │   ├── error/
│   │   │   └── failure.dart                # Failure abstraction (fpdart-compatible): CacheFailure, etc.
│   │   │
│   │   ├── theme/
│   │   │   └── app_theme.dart              # Dynamic Material 3 theme: Faida Royal Blue (#1E40AF), Electric Blue (#2563EB), 9 palettes, 5 fonts
│   │   │
│   │   ├── usecase/
│   │   │   └── usecase.dart                # Base UseCase<Result, Params> abstract class + NoParams class
│   │   │
│   │   ├── utils/
│   │   │   ├── ai_suggestion_service.dart   # Product pairing engine: suggests complementary items based on cart
│   │   │   ├── app_validators.dart          # Form validators: required field, etc.
│   │   │   └── printer_helper.dart          # PrinterHelper singleton + EscPos ESC/POS byte command definitions
│   │   │
│   │   └── widgets/
│   │       ├── input_label.dart            # Reusable form field label widget
│   │       └── primary_button.dart         # Reusable elevated button with loading state + icon
│   │
│   └── features/
│       │
│       ├── billing/                        # ── CORE POS FEATURE ──
│       │   ├── data/
│       │   │   └── repositories/
│       │   │       └── transaction_repository.dart  # Saves/loads transactions from Hive transactions box
│       │   │
│       │   ├── domain/
│       │   │   └── entities/
│       │   │       ├── cart_item.dart              # CartItem: product + quantity + total calculation
│       │   │       └── transaction.dart            # Transaction + CartItemSnapshot: completed sale record
│       │   │
│       │   └── presentation/
│       │       ├── bloc/
│       │       │   ├── billing_bloc.dart           # BillingBloc: scan barcode, add/remove/update cart, print receipt
│       │       │   ├── billing_event.dart          # ScanBarcode, AddProductToCart, RemoveProduct, UpdateQty, ClearCart, PrintReceipt
│       │       │   └── billing_state.dart          # BillingState: cartItems, totalAmount, error, isPrinting, suggestedProducts
│       │       │
│       │       └── pages/
│       │           ├── home_page.dart              # Main POS screen: camera scanner + cart list + suggestions + dashboard
│       │           ├── checkout_page.dart          # Checkout: item table, payment selection, QR code, print button
│       │           ├── scanner_page.dart           # Standalone full-screen scanner (alternative entry point)
│       │           ├── analytics_page.dart         # Transaction history viewer + dashboard stats
│       │           ├── transactions_page.dart      # Full dual-tab Ledger (Sales history & Expense accounting)
│       │           └── onboarding_page.dart        # Onboarding: business type selector (vector icons), slide-to-launch
│       │
│       ├── notifications/                  # ── IN-APP NOTIFICATIONS & OFFERS HUB ──
│       │   ├── data/
│       │   │   └── in_app_notification_service.dart # Persistent Hive storage, unread counter notifier, seed offers
│       │   ├── domain/
│       │   │   └── entities/
│       │   │       └── in_app_notification.dart    # InAppNotification entity: offer, alert, system, tip
│       │   └── presentation/
│       │       └── pages/
│       │           └── notifications_page.dart     # Notifications & Offers Hub (/notifications) with category filter tabs
│       │
│       ├── gamification/                   # ── STORE ACHIEVEMENTS & MILESTONES ──
│       │   ├── data/
│       │   │   └── achievement_service.dart        # Tracks XP progress, unlocked milestones, and award criteria
│       │   ├── domain/
│       │   │   └── achievement_model.dart          # Achievement definitions with vector badge icons
│       │   └── presentation/
│       │       └── pages/
│       │           └── achievements_page.dart      # Achievements showcase page with level cards and progress bars
│       │
│       ├── product/                        # ── PRODUCT/INVENTORY FEATURE ──
│       │   ├── data/
│       │   │   ├── models/
│       │   │   │   ├── product_model.dart          # ProductModel: Hive-compatible Product + toEntity()
│       │   │   │   └── product_model.g.dart        # Generated: Hive TypeAdapter for ProductModel
│       │   │   └── repositories/
│       │   │       └── product_repository_impl.dart # ProductRepositoryImpl: Hive CRUD, barcode lookup, stock update
│       │   │
│       │   ├── domain/
│       │   │   ├── entities/
│       │   │   │   └── product.dart                # Product: id, name, price, barcode, stockQuantity
│       │   │   ├── repositories/
│       │   │   │   └── product_repository.dart     # ProductRepository abstract: getProducts, add, update, delete, getByBarcode, updateStock
│       │   │   └── usecases/
│       │   │       └── product_usecases.dart       # GetProductsUC, AddProductUC, UpdateProductUC, DeleteProductUC, GetProductByBarcodeUC
│       │   │
│       │   └── presentation/
│       │       ├── bloc/
│       │       │   ├── product_bloc.dart           # ProductBloc: loads, adds, updates, deletes products
│       │       │   ├── product_event.dart          # LoadProducts, AddProduct, UpdateProduct, DeleteProduct
│       │       │   └── product_state.dart          # ProductState: status (initial/loading/loaded/error), products list, message
│       │       │
│       │       └── pages/
│       │           ├── product_list_page.dart      # Product list with search, FAB to add, swipe to delete
│       │           ├── add_product_page.dart       # Form: name, price, barcode, stock quantity
│       │           └── edit_product_page.dart      # Same form pre-filled for existing product
│       │
│       ├── settings/                       # ── SETTINGS & HARDWARE FEATURE ──
│       │   ├── data/
│       │   │   └── repositories/
│       │   │       └── printer_repository_impl.dart # PrinterRepositoryImpl: wraps PrinterHelper, Hive adapter for saved MAC
│       │   │
│       │   ├── domain/
│       │   │   └── repositories/
│       │   │       └── printer_repository.dart     # PrinterRepository abstract: scan, connect, disconnect, getStatus
│       │   │
│       │   └── presentation/
│       │       ├── bloc/
│       │       │   ├── printer_bloc.dart           # PrinterBloc: init, refresh, scan, connect, disconnect, test print
│       │       │   ├── printer_event.dart          # InitPrinter, Refresh, Scan, Connect, Disconnect, TestPrint
│       │       │   └── printer_state.dart          # PrinterState: status (idle/scanning/connecting/connected/disconnected/error)
│       │       │
│       │       └── pages/
│       │           └── settings_page.dart          # Settings: shop profile, analytics link, products link, Bluetooth printer
│       │
│       └── shop/                            # ── SHOP DETAILS FEATURE ──
│           ├── data/
│           │   ├── models/
│           │   │   ├── shop_model.dart             # ShopModel: Hive-compatible Shop + toEntity()
│           │   │   └── shop_model.g.dart           # Generated: Hive TypeAdapter for ShopModel
│           │   └── repositories/
│           │       └── shop_repository_impl.dart   # ShopRepositoryImpl: Hive CRUD for shop details
│           │
│           ├── domain/
│           │   ├── entities/
│           │   │   └── shop.dart                   # Shop: name, addressLine1, addressLine2, phoneNumber, upiId, footerText
│           │   ├── repositories/
│           │   │   └── shop_repository.dart        # ShopRepository abstract: getShop, updateShop
│           │   └── usecases/
│           │       └── shop_usecases.dart          # GetShopUC, UpdateShopUC
│           │
│           └── presentation/
│               ├── bloc/
│               │   ├── shop_bloc.dart              # ShopBloc: load, update shop
│               │   ├── shop_event.dart             # LoadShopEvent, UpdateShopEvent
│               │   └── shop_state.dart             # ShopState: initial, loading, loaded, error, operationSuccess
│               │
│               └── pages/
│                   └── shop_details_page.dart      # Shop form: name, address line 1/2, phone, UPI ID, footer text
```

---

## 🚀 SECTION 6: INSTALLATION & SETUP

### Prerequisites

| Tool                         | Version                               | Download                                                        |
| ---------------------------- | ------------------------------------- | --------------------------------------------------------------- |
| **Flutter SDK**        | ^3.1.0 or higher (recommended: 3.16+) | [Download Flutter](https://docs.flutter.dev/get-started/install) |
| **Dart SDK**           | Included with Flutter ^3.1.0          | —                                                              |
| **Android Studio**     | Hedgehog (2023.1.1) or newer          | [Download Android Studio](https://developer.android.com/studio)  |
| **Xcode** (macOS only) | 15.0+                                 | [Mac App Store](https://apps.apple.com/app/xcode/id497799835)    |
| **Git**                | Any recent version                    | [Download Git](https://git-scm.com/downloads)                    |

### 📥 Step 1: Clone the Repository

```bash
git clone <your-repository-url>
cd flutter_billing_app-main
```

**Expected output:**

```
Cloning into 'flutter_billing_app-main'...
remote: Enumerating objects: ...
Receiving objects: 100% (.../...), done.
```

### 📦 Step 2: Install Dependencies

```bash
flutter pub get
```

**Expected output:**

```
Resolving dependencies...
  _fe_analyzer_shared 61.0.0
  analyzer 5.13.0
  ...
Got dependencies!
```

If you see a warning about `fpdart` version conflicts, run:

```bash
flutter pub upgrade fpdart
```

### 🔧 Step 3: Run Code Generation

This generates Hive TypeAdapters and JSON serializers from annotations:

```bash
dart run build_runner build --delete-conflicting-outputs
```

**Expected output:**

```
[INFO] Generating build script...
[INFO] Running build...
[INFO] 2.0s elapsed, 4/4 actions completed.
[INFO] Build completed successfully.
```

**⚠️ Common Error:** If you get a `Conflicting outputs` error, add `--delete-conflicting-outputs` flag (already included above).

### 📱 Step 4: Run the App

**On an emulator:**

```bash
flutter emulators --launch <emulator-name>
flutter run
```

**On a physical device:**

```bash
flutter devices
# Find your device ID
flutter run -d <device-id>
```

**Expected output:**

```
Launching lib/main.dart on Android SDK built for x86 in debug mode...
Running Gradle task 'assembleDebug'...
✓ Built build/app/outputs/flutter-apk/app-debug.apk
Installing build/app/outputs/flutter-apk/app-debug.apk...
Waiting for device to start...
Syncing files to device...
Flutter run key commands.
  r - Hot reload
  R - Hot restart
  h - List all interactive commands
```

### ✅ How to Verify It's Working

1. **Onboarding Screen:** App launches into the onboarding flow styled in default **Faida Royal Blue (`#1E40AF`)**, **Clean Slate (`#F8FAFC`)**, and **Pure White (`#FFFFFF`)**.
2. Select your business type using the high-contrast vector icon cards (e.g. Pharmacy, Supermarket, Hardware, Restaurant, Boutique).
3. Slide the **"Slide to Launch POS"** slider widget to enter the main dashboard.
4. On the **Home / Sales Page**, you should see:
   - Top navigation row featuring your shop name and the **Notification Bell** with unread count badge.
   - **Today's Sales** summary card with quick balance metrics and barcode scanner button.
   - Quick action shortcuts (Quick Sale, Deni Notebook, Expenses, Inventory).
   - Bottom navigation bar switching smoothly between **Sales**, **Ledger (Transactions & Expenses)**, **Deni**, and **AI Copilot**.
5. Tap the **Notification Bell** to verify the In-App Notifications & Promotions Hub (`/notifications`).
6. Test natural language expense logging in the AI Copilot: type or speak *"I have paid 5000 for electricity"* or *"Nimelipa 5000 ya umeme"* → tap *"Tazama Orodha ya Matumizi"* to directly view the expense recorded in the Ledger.
7. Open **Settings → Appearance & Theme** to preview and customize preset palettes (Emerald, Midnight, Sapphire, Amber, etc.) and fonts.

### ❌ Common Setup Errors & Fixes

| Error                                                  | Cause                                                | Fix                                                                                         |
| ------------------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `No devices found`                                   | No emulator/device running                           | `flutter emulators --launch <name>` or connect USB device with debugging enabled          |
| `Could not find a file named "flutter_bootstrap.js"` | Web build incomplete                                 | Run`flutter create --platforms=web .` to regenerate web files                             |
| `The named parameter 'withValues' isn't defined`     | Outdated Flutter SDK                                 | Upgrade Flutter:`flutter upgrade`                                                         |
| `HiveError: No TypeAdapter found`                    | Missing build_runner step                            | Run`dart run build_runner build --delete-conflicting-outputs`                             |
| `Permission denied: CAMERA`                          | Android/iOS permissions not granted                  | App will request on first use; if denied, go to Settings → Apps → NexaBill → Permissions |
| `Unhandled Exception: Binding does not exist`        | Missing`WidgetsFlutterBinding.ensureInitialized()` | This is already in`main.dart` — ensure you're on Flutter 3.10+                           |
| `Error: Cannot run with sound null safety`           | Dart SDK < 3.0                                       | Upgrade Flutter SDK to 3.x series                                                           |
| Gradle build fails with "Failed to find Build Tools"   | Missing Android SDK components                       | Open Android Studio → SDK Manager → Install Android SDK Build-Tools                       |

---

## 🎯 SECTION 7: HOW TO USE IT

### 1. 📷 Scan a Barcode

**What it does:** Opens the camera and automatically detects QR/barcode. On detection, looks up product in local Hive database and adds it to cart.

**How to use:** Simply point the camera at a product barcode on the Home page. The app will vibrate, and the item appears in the cart below.

**Edge cases:**

- **Barcode not found:** A red snackbar appears: "Product not found: {barcode}"
- **Same barcode scanned twice in 2 seconds:** Ignored (cooldown prevents duplicates)
- **Camera off:** Tap "Turn on Camera" button or press the camera toggle overlay button

### 2. 📋 Manage Cart

**What it does:** The cart at the bottom half of the Home page shows all scanned products with quantities, individual prices, and total amount.

**How to use:**

- Each cart item shows product name, unit price, quantity selector (- / number / +), and total
- Tap **+** to increase quantity, **-** to decrease. At 0, the item is removed
- The **TOTAL PRICE** at the top-right updates in real-time
- **Smart Suggestions** bar appears at the bottom of the cart when AI detects complementary products — tap a suggestion to add it instantly

**Code example (adding a product to cart):**

```dart
// In home_page.dart — triggered on barcode scan success
context.read<BillingBloc>().add(AddProductToCartEvent(product));

// Inside BillingBloc._onAddProductToCart:
// If product already in cart → increment quantity
// If product not in cart → add new CartItem with quantity=1
```

### 3. 💳 Complete a Checkout

**What it does:** Review your cart, select a payment method (M-Pesa, Tigo Pesa, Airtel Money, or Cash), view a payment QR code, and print a receipt.

**How to use:**

1. Tap **"Review Order"** button at the bottom of the Home page
2. Review the itemized table on the checkout page
3. Select a payment method by tapping one of the colored chips
4. If a mobile money option is selected and a UPI ID is configured in Shop Details, a payment QR code appears
5. Tap **"Complete & Print"** to print the receipt and save the transaction

**Edge cases:**

- **No printer connected:** App attempts auto-reconnect if a MAC address was previously saved
- **Print failure:** Error snackbar shows "Print failed: {error}"
- **Shop details not loaded:** Red snackbar: "Shop details not loaded" — go to Settings → Shop Details first
- **Empty cart:** "Review Order" button is disabled

### 4. ➕ Add a Product

**What it does:** Creates a new product record in the local Hive database with name, price, barcode, and stock quantity.

**How to use:**

1. Go to Settings (gear icon on scanner overlay) → **Products**
2. Tap the **+** floating action button (FAB)
3. Fill in: Product Name, Price (in TSh), Barcode (optional — can be scanned later), Stock Quantity
4. Tap **"Save Product"**

**Code example (adding a product):**

```dart
// In add_product_page.dart
final product = Product(
  id: const Uuid().v4(),
  name: nameController.text,
  price: double.parse(priceController.text),
  barcode: barcodeController.text,
  stockQuantity: int.parse(stockController.text),
);
context.read<ProductBloc>().add(AddProduct(product));
```

### 5. 🔍 Search & Filter Products

**What it does:** The product list page includes a search bar that filters products by name or barcode in real-time.

**How to use:** On the Products page, tap the search bar at the top and type a product name or partial barcode. Results filter as you type.

### 6. 🏪 Configure Shop Details

**What it does:** Sets the shop name, address, phone, UPI ID (for mobile money QR codes), and receipt footer text — all printed on every receipt.

**How to use:**

1. Settings → **Shop Details**
2. Fill in: Shop Name, Address Line 1, Address Line 2, Phone Number, UPI ID (for QR payments), Footer Text (e.g., "Thank you for your business!")
3. Tap **"Update Shop"**

### 7. 🖨️ Connect a Bluetooth Printer

**What it does:** Scans for paired Bluetooth devices, connects to a thermal printer, and saves the MAC address for future auto-connects.

**How to use:**

1. Settings → scroll to **Hardware** section
2. Tap the **Refresh** icon to scan for paired Bluetooth devices
3. If no devices appear, tap the **Settings gear** to open your phone's Bluetooth settings and pair a printer
4. Return to the app and tap **Refresh** again
5. Once a printer is detected, tap **Connect**
6. A green "Connected to printer" snackbar confirms success

**When a printer MAC is saved**, the app auto-reconnects on checkout — no manual reconnection needed.

### 8. 📊 View Analytics

**What it does:** Shows transaction history with total sales, item counts, and per-transaction details.

**How to use:** Settings → **Business Analytics**. Scroll through past transactions. Each entry shows: timestamp, items purchased, total amount, and payment method.

### 9. 🔔 In-App Notifications & Promotions Hub

**What it does:** Centralized notification inbox for retail promotions, system announcements, inventory warnings, and tips.

**How to use:**

1. Tap the **Notification Bell** in the top navigation bar of the Sales screen. The badge counter dynamically displays unread counts.
2. Filter through categories: **All**, **Offers & Promos** (hardware bundles, discounts), **Alerts** (low-stock alerts, backup reminders), or **Tips** (store performance advice).
3. Swipe any card horizontally to dismiss, tap **Open** to navigate to the feature, or tap **Mark all read** in the top bar.

### 10. ⚡ Natural Language AI Expense Recording & Ledger

**What it does:** Log business expenses simply by typing or speaking in natural Swahili or English.

**How to use:**

1. Open **AI Copilot** (bottom navigation tab) or tap the mic/chat shortcut.
2. Type or say an expense: *"I have paid 5000 for electricity"* or *"Nimelipa 15,000 ya usafi"*.
3. The AI Copilot detects the amount, categorizes it (e.g. `Umeme / LUKU`, `Usafi & Utunzaji`), stores it directly in the encrypted Hive ledger, and deducts it from your net profit.
4. Tap the button **"Tazama Orodha ya Matumizi"** to jump directly to `/transactions?tab=Expenses` to view the expense entry and running balance.

### 11. 🏆 Store Achievements & Operational Milestones

**What it does:** Motivates storekeepers and staff through gamified milestones, unlocking badges and earning experience points (XP) as your business grows.

**How to use:**

1. Navigate to **Achievements** from the side drawer or settings menu.
2. Track your merchant tier progress (Bronze, Silver, Gold, Platinum, Diamond) with vector badges.
3. Complete achievements such as **First Sale**, **AI Copilot Pioneer**, **Super Scanner Pro**, **Debt Recovery Master**, and **Balanced Books**.

---

## 🗄️ SECTION 8: DATABASE SCHEMA

### Hive Database Overview

Hive is an offline-first NoSQL key-value database. NexaBill uses 4 boxes (equivalent to tables in SQL):

```
┌─────────────────────────────────────────────────────┐
│                  Hive Database                        │
│  ┌──────────────┐  ┌──────────────┐                 │
│  │  products     │  │  shop        │                 │
│  │  Box<Product> │  │  Box<Shop>   │                 │
│  └──────────────┘  └──────────────┘                 │
│  ┌──────────────┐  ┌──────────────────┐             │
│  │  settings    │  │  transactions    │             │
│  │  Box<dynamic>│  │  Box<dynamic>    │             │
│  └──────────────┘  └──────────────────┘             │
└─────────────────────────────────────────────────────┘
```

### Collection: `products` (Hive Box<ProductModel></productmodel>)

| Field         | Type       | Example             | Description                        |
| ------------- | ---------- | ------------------- | ---------------------------------- |
| id            | `String` | "a1b2c3d4-e5f6-..." | UUID v4, auto-generated            |
| name          | `String` | "Unilever Tea 100g" | Product display name               |
| price         | `double` | 3500.0              | Price in Tanzanian Shillings (TSh) |
| barcode       | `String` | "8901234567890"     | EAN/UPC barcode for scanner lookup |
| stockQuantity | `int`    | 50                  | Current inventory count            |

**Indexed by:** barcode (scanned during checkout lookup)

### Collection: `shop` (Hive Box<ShopModel></shopmodel>)

| Field        | Type       | Example                   | Description                      |
| ------------ | ---------- | ------------------------- | -------------------------------- |
| name         | `String` | "Elite Groceries"         | Business name on receipts        |
| addressLine1 | `String` | "123 Mpakani Road"        | First address line on receipts   |
| addressLine2 | `String` | "Mwenge, Dar es Salaam"   | Second address line on receipts  |
| phoneNumber  | `String` | "+255 712 345 678"        | Contact phone on receipts        |
| upiId        | `String` | "example@tza"             | UPI ID for QR payment generation |
| footerText   | `String` | "Thank you! Visit again." | Receipt footer message           |

**Note:** Only one shop document exists (singleton pattern). Overwrites on update.

### Collection: `settings` (Hive Box<dynamic></dynamic>)

| Key              | Type        | Example             | Description                                  |
| ---------------- | ----------- | ------------------- | -------------------------------------------- |
| printer_mac      | `String?` | "00:11:22:AA:BB:CC" | Saved Bluetooth printer MAC for auto-connect |
| (any future key) | ...         | ...                 | Extensible key-value settings store          |

### Collection: `transactions` (Hive Box<dynamic></dynamic>)

| Field         | Type          | Example                                               | Description                 |
| ------------- | ------------- | ----------------------------------------------------- | --------------------------- |
| id            | `String`    | UUID                                                  | Unique transaction ID       |
| timestamp     | `DateTime`  | 2025-03-15 14:30:00                                   | When the sale was completed |
| items         | `List<Map>` | [{"product":{...}, "quantity":2, "priceAtTime":3500}] | Snapshot of purchased items |
| totalAmount   | `double`    | 12500.0                                               | Total transaction value     |
| paymentMethod | `String`    | "M-Pesa"                                              | Payment method used         |

**Relationships:**

- `transactions.items[].product` references a snapshot of the Product at time of sale (not a live reference, to preserve historical price data)
- No foreign keys — Hive is a document store, not relational

---

## 🤖 SECTION 9: AI INTEGRATION & COPILOT ARCHITECTURE

Faida HQ POS implements a **dual-tier AI architecture**: a high-speed cloud LLM tier for conversational retail intelligence and natural language command execution, backed by a 100% deterministic, zero-dependency offline advisor.

### 1. Cloud LLM Copilot (Online Mode)

- **Primary Engines:** Google Gemini 2.5 Flash and Groq Qwen 3.6 (sub-1.5s latency).
- **Service Layer:** `lib/core/services/ai/ai_assistant_service.dart` and `lib/core/services/ai/ai_action_executor.dart`.
- **Key Rotation Engine:** Built-in automatic API key rotation pool (`GEMINI_API_KEYS`, `GROQ_API_KEYS`) with graceful quota rollover.
- **Capabilities:**
  - **Natural Language Expense Recording:** Parses Swahili and English natural language (e.g. *"Paid 5,000 for electricity"*, *"Nimelipa 15,000 ya usafi"*), auto-maps the category (e.g., `Umeme / LUKU`, `Usafi`), saves to Hive, deducts from net profit, and directs merchants to `/transactions?tab=Expenses`.
  - **Conversational Business Advisor:** Provides bilingual store advice, identifies dead stock, suggests profit optimization tactics, and reviews margins.
  - **Stock & Inventory Auditing:** Answers inventory queries like *"Do we have Azam milk?"* and summarizes units on hand, cost price, and sales margin.

### 2. Offline Deterministic Advisor & Product Pairing (Offline Fallback)

- **Engine:** `lib/core/services/ai/offline_advisor.dart` & `lib/core/utils/ai_suggestion_service.dart`.
- **Zero Internet Requirement:** Instant regex-based natural language parsing and deterministic recommendation heuristics.
- **Sub-10ms Latency:** Zero latency or API cost; works seamlessly in remote or network-deprived retail kiosks.
- **Cross-Selling Pairing Engine:** Intelligently analyzes items in the live cart and suggests matching inventory (e.g., Sugar → Tea/Coffee/Milk; Rice → Cooking Oil/Beans).

---

## ⚠️ SECTION 10: CURRENT LIMITATIONS & KNOWN BUGS

### Known Bugs

| Bug                                                   | Steps to Reproduce                                                                                                            | Impact                              | Status     |
| ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | ---------- |
| **Camera flash toggle doesn't persist**         | Turn on flash → navigate to checkout → return to home → flash is off                                                       | Low — cosmetic                     | Unresolved |
| **Analytics dashboard shows hardcoded data**    | Open app → see "Today's Sales: TSh 4,250" — this is static, not from real transactions                                      | Medium — misleading                | Unresolved |
| **Web build broken**                            | Run`flutter build web` → `mobile_scanner` and `print_bluetooth_thermal` fail because they require native platform APIs | High — web platform unusable       | Unresolved |
| **No loading state on product list**            | Open Products page with 1000+ products → UI freezes until all items are loaded                                               | Medium — UX issue                  | Unresolved |
| **Printer MAC not persisted after app restart** | Connect printer → close app → reopen → printer MAC may not auto-reconnect                                                  | Medium — requires manual reconnect | Unresolved |
| **Stock can go negative**                       | Sell more of a product than available stock → stockQuantity becomes negative                                                 | High — data integrity issue        | Unresolved |

### Performance Bottlenecks

1. **No pagination on product list:** Loading 10,000+ products into a single ListView will consume ~200MB+ RAM and cause jank. The product list page loads ALL products at once.
2. **No database indexing on product name:** Product search does a full scan of all products. At 10,000+ products, search latency will exceed 500ms.
3. **Single-threaded receipt printing:** The ESC/POS byte construction and Bluetooth write happen on the main isolate. Large receipts (50+ items) may cause UI jank.
4. **No transaction pagination:** The analytics page loads ALL transactions into memory. At 100,000+ transactions, this will crash the app.

### Security Issues

1. **No authentication:** Anyone with the device can access all products, transactions, and settings. No login screen, no PIN, no biometric auth.
2. **No data encryption:** Hive database files are stored in plaintext on the device filesystem. Anyone with file system access can read all product and transaction data.
3. **No audit log:** There is no record of who performed which action. If multiple people use the same device, there's no accountability.
4. **No input sanitization:** Product names, shop names, and footer text are stored and printed as-is. A malicious user could inject ESC/POS control characters through form fields.

### Features That Work But Work Badly

- **Stock management:** Stock quantity is tracked and decremented on sale, but there's no low-stock alert, no restock date tracking, no stock report, and no batch update
- **Analytics:** The analytics page shows a transaction list but has no charts, no date filtering, no export, and no meaningful aggregation
- **Search:** Product search is case-sensitive and does not support fuzzy matching or partial barcode search
- **Error messages:** Some error messages are technical (e.g., "Print failed: SocketException") rather than user-friendly

### Technical Debt

1. **Hardcoded demo data in home_page.dart** — lines 148-153 contain static values for dashboard stats
2. **No error handling in some BLoC event handlers** — `_onAddProductToCart` and `_onUpdateQuantity` don't handle edge cases like null products
3. **PrinterHelper is a singleton** — makes unit testing difficult; should be injectable via get_it
4. **No repository interface for TransactionRepository** — it's a concrete class, not an abstract contract, breaking Clean Architecture
5. **Missing Hive TypeAdapter for Transaction** — transactions are stored as raw Maps instead of typed objects
6. **No separation of web/native code** — `mobile_scanner` and `print_bluetooth_thermal` imports will break web builds

---

## 🔧 SECTION 11: MODIFICATION & ADDON GUIDE

### MOD 1: Add a New AI Model (e.g., Switch from Local Engine to Gemini API)

- **Difficulty:** ⭐⭐⭐ (3/5)
- **Time to implement:** 4-6 hours
- **Files to modify:**
  - `lib/core/utils/ai_suggestion_service.dart`
  - `lib/core/service_locator.dart`
  - `pubspec.yaml`
- **New files to create:**
  - `lib/core/utils/gemini_suggestion_service.dart`
- **Dependencies to add:**
  ```bash
  flutter pub add google_generative_ai
  ```
- **Step-by-step:**
  1. Create `GeminiSuggestionService` class that takes a `GenerativeModel` via constructor
  2. Define a prompt template:
     ```
     You are a retail suggestion engine. Given a list of products in a customer's cart
     and a list of all available products, suggest 3-5 complementary products that the
     customer might also want to buy. Return only product names as a comma-separated list.

     Cart items: {cart_product_names}
     Available products: {all_product_names}
     ```
  3. Implement `suggestProducts()` that calls `model.generateContent()` with the prompt
  4. Parse the response and map product names back to `Product` objects
  5. In `service_locator.dart`, register `GeminiSuggestionService` as a lazy singleton
  6. In `billing_bloc.dart`, inject the service and call it in `_updateSuggestions()`
- **How to test:** Add products to cart and verify suggestions appear from Gemini instead of the local engine

### MOD 2: Add a New Content Type (e.g., Add Service/Repair Orders)

- **Difficulty:** ⭐⭐ (2/5)
- **Time to implement:** 2-3 hours
- **Files to modify:**
  - `lib/features/product/domain/entities/product.dart` — add `type` field
  - `lib/features/product/data/models/product_model.dart` — add `type` field
  - `lib/features/product/presentation/pages/add_product_page.dart` — add type dropdown
  - `lib/features/billing/presentation/pages/checkout_page.dart` — show type in receipt
- **New files to create:** None
- **Dependencies to add:** None
- **Step-by-step:**
  1. Add `String type` field to `Product` entity (values: "product", "service", "repair")
  2. Add corresponding field to `ProductModel` and regenerate adapter
  3. Add a dropdown in `AddProductPage` for product type selection
  4. In `checkout_page.dart`, display product type next to name in the table
  5. In `printer_helper.dart`, include type in receipt item lines
- **How to test:** Create a service-type product, add to cart, verify it appears correctly on checkout and receipt

### MOD 3: Add User Authentication

- **Difficulty:** ⭐⭐⭐⭐ (4/5)
- **Time to implement:** 8-12 hours
- **Files to modify:**
  - `lib/main.dart` — add auth check before app loads
  - `lib/config/routes/app_routes.dart` — add login route, redirect logic
  - `lib/core/service_locator.dart` — register auth services
  - `pubspec.yaml`
- **New files to create:**
  - `lib/features/auth/` — full auth feature with data/domain/presentation layers
  - `lib/features/auth/presentation/pages/login_page.dart`
  - `lib/features/auth/presentation/bloc/auth_bloc.dart`
  - `lib/features/auth/domain/entities/user.dart`
  - `lib/features/auth/data/repositories/auth_repository_impl.dart`
- **Dependencies to add:**
  ```bash
  flutter pub add firebase_core firebase_auth
  # OR for local-only auth:
  flutter pub add local_auth  # biometric/PIN auth
  ```
- **Step-by-step:**
  1. Create `User` entity with id, name, role (admin/cashier), pinHash
  2. Create `AuthRepository` with `login(pin)`, `logout()`, `getCurrentUser()`
  3. Create `AuthBloc` with states: unauthenticated, authenticated, loading, error
  4. Create `LoginPage` with PIN input (6 digits)
  5. In `main.dart`, wrap app in `BlocBuilder<AuthBloc, AuthState>` — show login or main app
  6. In `app_routes.dart`, add redirect guard: if not authenticated → redirect to `/login`
  7. Store user data in Hive `settings` box (or Firebase if using cloud auth)
- **How to test:** Launch app → should show login screen → enter correct PIN → should navigate to home → restart app → should require PIN again

### MOD 4: Add Payment/Subscription System

- **Difficulty:** ⭐⭐⭐⭐⭐ (5/5)
- **Time to implement:** 2-4 weeks
- **Files to modify:** Many — this is a major feature
- **New files to create:**
  - Backend API (Node.js/Python) for license validation
  - `lib/features/subscription/` — full feature
- **Dependencies to add:**
  ```bash
  flutter pub add flutter_secure_storage  # store license key securely
  flutter pub add http                    # call license validation API
  ```
- **Step-by-step:**
  1. Build a simple license server (Firebase Functions or a small Node.js API)
  2. Generate unique license keys tied to device ID
  3. On app launch, check for stored license key in `flutter_secure_storage`
  4. If no key, show a paywall/subscription page
  5. On payment (via M-Pesa API or mobile money), generate and store license key
  6. Periodically validate license (daily check with grace period for offline use)
- **How to test:** Install app on new device → should show paywall → enter valid license → should unlock full app

### MOD 5: Add a New Social Media Platform (e.g., Share Receipt on WhatsApp)

- **Difficulty:** ⭐ (1/5)
- **Time to implement:** 1-2 hours
- **Files to modify:**
  - `lib/features/billing/presentation/pages/checkout_page.dart`
  - `pubspec.yaml`
- **New files to create:** None
- **Dependencies to add:**
  ```bash
  flutter pub add share_plus
  ```
- **Step-by-step:**
  1. After successful print, add a "Share Receipt" button
  2. Format receipt text as a string
  3. Call `Share.share(receiptText)` to open system share sheet
  4. User can share to WhatsApp, Telegram, SMS, email, etc.
- **How to test:** Complete a checkout → tap "Share Receipt" → system share sheet opens → select WhatsApp → receipt text appears in chat

### MOD 6: Make It Faster / More Scalable

- **Difficulty:** ⭐⭐⭐ (3/5)
- **Time to implement:** 4-6 hours
- **Files to modify:**
  - `lib/features/product/presentation/pages/product_list_page.dart`
  - `lib/features/product/data/repositories/product_repository_impl.dart`
  - `lib/features/billing/presentation/pages/analytics_page.dart`
- **New files to create:** None
- **Dependencies to add:** None
- **Step-by-step:**
  1. **Add pagination to product list:** Modify `ProductRepositoryImpl.getProducts()` to accept `limit` and `offset` parameters. Update `ProductBloc` to load products in batches of 50. Add scroll listener to `product_list_page.dart` to load more on scroll end.
  2. **Add search indexing:** Create a separate Hive box for search index mapping lowercase product names to IDs. Update search to use the index instead of full scan.
  3. **Add transaction pagination:** Same approach as product pagination — load transactions in batches of 20.
  4. **Move printer I/O to isolate:** Use `Isolate.run()` or `compute()` for ESC/POS byte construction to avoid UI jank.
- **How to test:** Add 10,000 test products → verify product list loads in <1 second and scrolls smoothly

### MOD 7: Add a Mobile App Frontend (Already Done — This IS the Flutter App)

NexaBill is already a Flutter mobile app. For a **web dashboard** companion:

- **Difficulty:** ⭐⭐⭐⭐ (4/5)
- **Time to implement:** 1-2 weeks
- **Files to create:** Separate Flutter web project or use existing with conditional imports
- **Approach:** Use `dart:html` conditionally or build a separate Flutter web app that reads from a shared backend (Firebase)

### MOD 8: Add an Admin Dashboard

- **Difficulty:** ⭐⭐⭐ (3/5)
- **Time to implement:** 3-5 days
- **Files to create:**
  - `lib/features/admin/presentation/pages/dashboard_page.dart`
  - `lib/features/admin/presentation/bloc/admin_bloc.dart`
  - `lib/features/admin/domain/usecases/` — sales reports, top products, etc.
- **Dependencies to add:** `fl_chart` for charts
  ```bash
  flutter pub add fl_chart
  ```
- **Step-by-step:**
  1. Create `AdminBloc` that aggregates data from `TransactionRepository` and `ProductRepository`
  2. Build dashboard with: total sales (today/week/month), top 10 products, sales trend line chart, payment method breakdown pie chart
  3. Add date range picker for filtering
  4. Add export button (CSV/PDF)
- **How to test:** Complete several transactions → open admin dashboard → verify charts show correct data

### MOD 9: Add Analytics Tracking

- **Difficulty:** ⭐⭐ (2/5)
- **Time to implement:** 2-3 hours
- **Files to modify:**
  - `lib/main.dart` — init analytics
  - `lib/core/service_locator.dart` — register analytics service
  - `lib/config/routes/app_routes.dart` — track screen views
- **New files to create:**
  - `lib/core/utils/analytics_service.dart`
- **Dependencies to add:**
  ```bash
  flutter pub add firebase_analytics
  # OR for privacy-first:
  flutter pub add posthog_flutter
  ```
- **Step-by-step:**
  1. Create `AnalyticsService` wrapper class
  2. Log events: `product_added`, `barcode_scanned`, `checkout_completed`, `receipt_printed`, `printer_connected`
  3. Log screen views via GoRouter listener
  4. In `main.dart`, initialize analytics service
- **How to test:** Use app for 5 minutes → check Firebase/PostHog dashboard for events

### MOD 10: Add Scheduled/Automated Jobs

- **Difficulty:** ⭐⭐⭐ (3/5)
- **Time to implement:** 4-6 hours
- **Files to modify:**
  - `lib/main.dart` — register background tasks
  - `pubspec.yaml`
- **New files to create:**
  - `lib/core/utils/background_tasks.dart`
- **Dependencies to add:**
  ```bash
  flutter pub add workmanager
  ```
- **Step-by-step:**
  1. Create background task: "Daily backup" — export transactions and products to a JSON file
  2. Register task with `Workmanager()` to run daily at midnight
  3. Create task: "Low stock alert" — check all products with stock < 5 and send notification
  4. Register to run every 4 hours
  5. Handle Android foreground service permissions
- **How to test:** Set stock of a product to 2 → wait for next scheduled check (or trigger manually) → verify notification appears

### MOD 11: Add Email Notifications

- **Difficulty:** ⭐⭐ (2/5)
- **Time to implement:** 2-3 hours
- **Files to modify:**
  - `lib/features/shop/domain/entities/shop.dart` — add `email` field
  - `lib/features/billing/presentation/bloc/billing_bloc.dart` — send email after checkout
  - `pubspec.yaml`
- **New files to create:**
  - `lib/core/utils/email_service.dart`
- **Dependencies to add:**
  ```bash
  flutter pub add mailer  # SMTP email
  # OR use Firebase Extensions for email
  ```
- **Step-by-step:**
  1. Add `email` field to Shop entity
  2. Create `EmailService` that sends receipt as email body via SMTP
  3. In `_onPrintReceipt()`, after successful print, call `EmailService.sendReceipt()`
  4. Handle errors gracefully (email failure should not block checkout)
- **How to test:** Set shop email → complete checkout → verify email arrives with receipt details

### MOD 12: Add a Waitlist/Landing Page

- **Difficulty:** ⭐ (1/5)
- **Time to implement:** 1-2 hours
- **Files to create:**
  - `web/landing.html` — standalone landing page
- **Dependencies to add:** None (pure HTML/CSS/JS)
- **Step-by-step:**
  1. Create a simple landing page with: hero section, feature highlights, screenshots, email signup form
  2. Style with Tailwind CSS (CDN) or plain CSS
  3. Add email signup form that POSTs to a Google Form or Firebase Function
  4. Host on Firebase Hosting or GitHub Pages
- **How to test:** Open landing page → submit email → verify it appears in your signup list

---

## 🚢 SECTION 12: DEPLOYMENT GUIDE

### Deploying to Android (Play Store)

1. **Generate a signing key:**

   ```bash
   keytool -genkey -v -keystore upload-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias upload
   ```
2. **Create `key.properties`** in `android/`:

   ```
   storePassword=<your-password>
   keyPassword=<your-password>
   keyAlias=upload
   storeFile=../upload-keystore.jks
   ```
3. **Build the release APK:**

   ```bash
   flutter build apk --release
   ```

   Output: `build/app/outputs/flutter-apk/app-release.apk`
4. **Build the App Bundle (recommended for Play Store):**

   ```bash
   flutter build appbundle --release
   ```

   Output: `build/app/outputs/bundle/release/app-release.aab`
5. **Upload to Play Console:**

   - Go to [Google Play Console](https://play.google.com/console/)
   - Create a new app
   - Fill in store listing (description, screenshots, category)
   - Upload the `.aab` file
   - Complete the app content questionnaire
   - Submit for review

### Deploying to iOS (App Store)

1. **Set up certificates and profiles** in Apple Developer account
2. **Configure signing** in Xcode:
   ```bash
   open ios/Runner.xcworkspace
   ```

   - Select "Runner" target → Signing & Capabilities → select your team
3. **Build the archive:**
   ```bash
   flutter build ios --release
   ```
4. **Open Xcode → Product → Archive** → upload to App Store Connect
5. **Submit for review** via App Store Connect

### Deploying to Web

> **⚠️ Warning:** The web build is currently broken due to native plugin dependencies (`mobile_scanner`, `print_bluetooth_thermal`). To make web work, you must conditionally import these plugins.

1. **Fix web compatibility** (see Section 9 — Technical Debt item 6)
2. **Build for web:**
   ```bash
   flutter build web --release
   ```
3. **Deploy to Firebase Hosting:**
   ```bash
   npm install -g firebase-tools
   firebase init hosting
   # Select "build/web" as public directory
   # Configure as single-page app: yes
   firebase deploy --only hosting
   ```

### Environment Variables in Production

NexaBill has **no environment variables** because it has no cloud dependencies. If you add cloud features (Firebase, Gemini API, etc.), use:

```bash
flutter run --dart-define=GEMINI_API_KEY=your_key_here
```

For release builds, use `--dart-define` flags or a `.env` file with `flutter_dotenv`:

```bash
flutter pub add flutter_dotenv
# Create .env file (never commit!)
# In main.dart: await dotenv.load();
```

### Database Security Rules

Since NexaBill uses **local Hive only**, there are no cloud database security rules to configure. If you add Firebase:

```javascript
// firestore.rules
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

### Custom Domain Setup

For web deployment only:

1. Buy a domain (e.g., nexabill.app)
2. In Firebase Hosting: add custom domain
3. Update DNS records (A record and TXT record as specified by Firebase)
4. Wait for SSL certificate provisioning (up to 24 hours)

### Monitoring After Deployment

| What to Monitor | Tool                 | How                                      |
| --------------- | -------------------- | ---------------------------------------- |
| Crash reports   | Firebase Crashlytics | `flutter pub add firebase_crashlytics` |
| Performance     | Firebase Performance | `flutter pub add firebase_performance` |
| Usage analytics | Firebase Analytics   | `flutter pub add firebase_analytics`   |
| Uptime (web)    | UptimeRobot          | Free tier: 5-minute checks               |
| Error logging   | Sentry               | `flutter pub add sentry_flutter`       |

### Rollback Plan

**If a release breaks:**

1. **Android:** Google Play Console → Release → Rollback to previous version
2. **iOS:** App Store Connect → Build → Remove from sale → Re-submit old build
3. **Web:** Firebase Hosting → `firebase hosting:clone <version>` to rollback
4. **Local app:** User must reinstall the previous APK (keep signed APKs in version control)

---

## 💰 SECTION 13: COST CALCULATOR

### Current Costs (No Cloud Dependencies)

| Service                      | Free Tier          | Paid Tier          | Cost at 100 Users  | Cost at 1,000 Users |
| ---------------------------- | ------------------ | ------------------ | ------------------ | ------------------- |
| **Flutter SDK**        | ✅ Free            | —                 | $0                 | $0                  |
| **Hive Database**      | ✅ Free (local)    | —                 | $0                 | $0                  |
| **Barcode Scanner**    | ✅ Free (plugin)   | —                 | $0                 | $0                  |
| **Bluetooth Printing** | ✅ Free (plugin)   | —                 | $0                 | $0                  |
| **Google Fonts**       | ✅ Free            | —                 | $0                 | $0                  |
| **Total**              | **$0/month** | **$0/month** | **$0/month** | **$0/month**  |

### If You Add Firebase (Optional)

| Service                        | Free Tier                        | Paid Tier                            | Cost at 100 Users | Cost at 1,000 Users    |
| ------------------------------ | -------------------------------- | ------------------------------------ | ----------------- | ---------------------- |
| **Firebase Auth**        | 50K MAU free                     | $0.0055/MAU beyond                   | $0                | $0 (under 50K)         |
| **Firestore**            | 1GB stored, 10GB/month download  | $0.108/GB stored, $0.12/GB download  | $0                | ~$5-10/month           |
| **Firebase Hosting**     | 10GB storage, 360MB/day download | $0.026/GB storage, $0.15/GB download | $0                | $0                     |
| **Firebase Crashlytics** | Free                             | —                                   | $0                | $0                     |
| **Firebase Analytics**   | Free                             | —                                   | $0                | $0                     |
| **Total with Firebase**  | **$0/month**               | **~$5-15/month**               | **$0**      | **~$5-15/month** |

### If You Add Gemini API (Optional)

| Service                    | Free Tier           | Paid Tier                        | Cost at 100 Users     | Cost at 1,000 Users |
| -------------------------- | ------------------- | -------------------------------- | --------------------- | ------------------- |
| **Gemini 1.5 Flash** | 1M tokens/min free  | $0.075/1M input, $0.30/1M output | ~$0 (under free tier) | ~$5-20/month        |
| **Gemini 1.5 Pro**   | 32K tokens/min free | $1.25-2.50/1M tokens             | ~$0                   | ~$30-100/month      |

### Hardware Costs (One-Time)

| Item                                    | Price (USD)        | Notes                               |
| --------------------------------------- | ------------------ | ----------------------------------- |
| **Android device**                | $80-200            | Any Android 8+ phone/tablet         |
| **Bluetooth thermal printer**     | $25-50             | e.g., Rongta RP80, Bixolon SPP-R200 |
| **Thermal paper rolls (50-pack)** | $5-10              | 58mm x 30mm rolls                   |
| **Total hardware**                | **$110-260** | One-time cost per shop              |

---

## 🗺️ SECTION 14: ROADMAP

### SHORT TERM (Next 2 Weeks)

1. **[P1] Fix stock going negative** — Add validation in `_onPrintReceipt()` to check stock before sale
2. **[P1] Connect analytics dashboard to real data** — Replace hardcoded demo stats with actual transaction aggregation
3. **[P2] Add product search debouncing** — Prevent excessive rebuilds during search typing
4. **[P2] Add loading indicators** — Show shimmer/skeleton on product list and analytics page
5. **[P3] Add confirmation dialog on "Clear Cart"** — Prevent accidental cart clearing when pressing back from checkout

### MEDIUM TERM (Next 3 Months)

1. **User authentication** — PIN-based login for cashier/admin roles
2. **Low-stock alerts** — Visual warning on product list when stock < threshold
3. **Sales reports** — Daily/weekly/monthly sales charts with `fl_chart`
4. **Tax calculation** — VAT (18% Tanzania), NHIF, and other deductions
5. **Discount system** — Percentage and fixed-amount discounts per item or cart
6. **Customer management** — Save customer phone numbers, track purchase history
7. **Data export** — Export products and transactions to CSV/Excel
8. **Dark mode** — Theme toggle with persisted preference

### LONG TERM (6-12 Months)

1. **Multi-device sync** — Share inventory across multiple POS devices via a local network or cloud
2. **Cloud backup** — Optional Firebase/Firestore sync for data backup
3. **Multi-language support** — Swahili and English UI
4. **Bulk product import** — CSV/Excel import for initial inventory setup
5. **Supplier management** — Track suppliers, purchase orders, and restock dates
6. **Loyalty program** — Points-based customer loyalty with automatic discounts
7. **Offline-first cloud sync** — Work offline, sync when internet is available (like a proper offline-first app)
8. **Version 2.0 — NexaBill Cloud** — Full cloud-connected POS with:
   - Centralized dashboard for multi-branch management
   - Real-time inventory across all branches
   - Cloud-based analytics and reporting
   - Remote printer management
   - API for e-commerce integration

---

## 📝 SECTION 15: LESSONS LEARNED

### What Worked Better Than Expected

1. **Hive as a database:** For a single-device POS, Hive is incredibly fast. Reads are <1ms, writes are <5ms. No SQL schema migrations, no connection pooling, no server to maintain. Perfect for this use case.
2. **BLoC state management:** The separation of events, states, and blocs made the code easy to reason about. Debugging is straightforward — you can see exactly which event caused which state change.
3. **Clean Architecture with features:** Organizing by feature (billing, product, settings, shop) rather than by layer (all models together, all blocs together) made navigation much easier. Each feature is self-contained.
4. **Raw ESC/POS bytes:** Building receipt formatting with raw byte commands instead of a library like `esc_pos_utils` gave full control and zero dependency issues. The `EscPos` class with static const byte arrays is simple and effective.

### What Was Harder Than Expected

1. **Bluetooth printer compatibility:** Different thermal printers implement slightly different ESC/POS command sets. The `print_bluetooth_thermal` plugin works with most Chinese printers (Rongta, Xprinter) but some printers require vendor-specific initialization sequences.
2. **Camera scanner on different devices:** The `mobile_scanner` plugin works well on modern devices but struggles on low-end Android phones (e.g., Tecno, Infinix) with poor autofocus and low-light performance.
3. **Hive TypeAdapters:** The code generation with `build_runner` is fragile. Any change to model fields requires regeneration, and conflicting outputs are common. The `--delete-conflicting-outputs` flag became a necessity.
4. **State persistence across navigation:** Managing camera state (on/off, flash) when navigating between pages required careful lifecycle management. The scanner had to be stopped before navigation and restarted on return.

### What I Would Do Differently

1. **Add tests from day one:** The project has minimal test coverage. Writing tests after the fact is much harder than writing them alongside the code. I would add unit tests for BLoCs and repository implementations.
2. **Use freezed instead of equatable:** `equatable` works but `freezed` would have generated copyWith, union types, and JSON serialization automatically — reducing boilerplate significantly.
3. **Abstract platform dependencies earlier:** The tight coupling to `mobile_scanner` and `print_bluetooth_thermal` makes web support difficult. I would create platform interfaces and use `dart:io` checks or conditional imports from the start.
4. **Add proper error handling in BLoCs:** Several BLoC event handlers don't handle failure cases. The `Either<Failure, Success>` pattern from `fpdart` is used in use cases but not always properly handled in BLoCs.
5. **Use a proper state class for each BLoC:** Some BLoCs (like `BillingBloc`) have too many responsibilities. Splitting into `CartBloc` and `PrintBloc` would be cleaner.

### What I Learned That Applies to ALL Future Projects

1. **Offline-first is a feature, not a limitation.** Building for offline from the start forces better architecture. Cloud sync can always be added later, but removing cloud dependency is nearly impossible.
2. **Feature-first > Layer-first.** Organizing code by feature (billing, product, settings) rather than by layer (models, blocs, pages) makes the project navigable even at 50+ files. New developers can find what they need in seconds.
3. **Hardware integration is the hardest part.** Bluetooth, camera, and printer APIs vary wildly across devices. Abstract hardware behind interfaces and test on as many real devices as possible.
4. **Documentation is not optional.** Three months from now, you will not remember why you chose Hive over SQLite, or why the printer MAC is stored in settings instead of shop. Write it down.
5. **Build for the user's context, not yours.** This app is used by shopkeepers in Tanzania who may have limited technical literacy, unreliable electricity, and $50 Android phones. Every design decision should start with "will this work for them?"

---

## ⚡ SECTION 16: QUICK REFERENCE CARD

### Start the App

```bash
cd flutter_billing_app-main
flutter pub get
dart run build_runner build --delete-conflicting-outputs
flutter run
```

### Build for Production

```bash
# Android APK
flutter build apk --release

# Android App Bundle (Play Store)
flutter build appbundle --release

# iOS (macOS only)
flutter build ios --release

# Web (requires native plugin fixes first)
flutter build web --release
```

### Most Important API Endpoints

NexaBill has **no API endpoints** — it's a fully offline mobile app. All operations are local:

| Operation       | Location                   | How to Call                                                         |
| --------------- | -------------------------- | ------------------------------------------------------------------- |
| Scan barcode    | `home_page.dart`         | `context.read<BillingBloc>().add(ScanBarcodeEvent(barcode))`      |
| Add to cart     | `home_page.dart`         | `context.read<BillingBloc>().add(AddProductToCartEvent(product))` |
| Print receipt   | `checkout_page.dart`     | `context.read<BillingBloc>().add(PrintReceiptEvent(...))`         |
| Add product     | `add_product_page.dart`  | `context.read<ProductBloc>().add(AddProduct(product))`            |
| Update shop     | `shop_details_page.dart` | `context.read<ShopBloc>().add(UpdateShopEvent(shop))`             |
| Connect printer | `settings_page.dart`     | `context.read<PrinterBloc>().add(ConnectPrinterEvent(mac))`       |

### Most Important Environment Variables

**None.** NexaBill has zero environment variables. If you add cloud features:

```bash
# For Firebase
flutter run --dart-define=FIREBASE_API_KEY=xxx

# For Gemini API
flutter run --dart-define=GEMINI_API_KEY=xxx
```

### Most Common Fix Commands

```bash
# Fix Hive adapter issues
dart run build_runner build --delete
```

---

## 🚀 SECTION 17: RELEASES & UPDATES — GitHub Release Engine (mwijay12/faida-pos)

The app ships to merchants as APK releases published automatically to **GitHub Releases**.

- **Official Releases Web Page:** `https://github.com/mwijay12/faida-pos/releases/latest`
- **Direct 1-Tap APK Download:** `https://github.com/mwijay12/faida-pos/releases/latest/download/app-release.apk`

### 🔄 How user updates work

1. **Automated Cloud Builds:** Every release APK is built and published by **GitHub Actions** (`.github/workflows/release.yml`) whenever a `vX.Y.Z` tag is pushed. Both `Faida-POS-X.Y.Z.apk` and the static link `app-release.apk` are generated.
2. **Real-Time Stream Synchronization:** The app listens to Firestore (`system/app_config`) via a live snapshot stream (`SystemConfigService.startListening()`).
3. **Lock Screen & Status Bar Push Notifications:** The instant the creator publishes an announcement or update from the Creator Hub, connected devices sound a high-priority notification visible directly on the **Lock Screen** (`faida_announcements_channel` and `faida_updates_channel`).
4. **Creator Presets:** In the **Creator Admin Hub**, quick action chips allow 1-tap selection between **"GitHub Release Page"** and **"Direct APK Download"**.
5. **Two Enforcement Modes:**
   - **Flexible Recommendation:** When `currentAppVersion < latest_version`, users see an update prompt and can tap "Later" to continue using the app.
   - **Retire Older Versions (Force Update):** When the toggle is enabled (`min_supported_version == latest_version`), older builds **stop working** and present a non-dismissible barrier (`canPop: false`) directing users to download the update.

### 📦 Releasing a new version (maintainer checklist)

1. **Bump versions in BOTH places:**
   - `pubspec.yaml` → `version: X.Y.Z+N` — the `+N` build number **MUST increase every release** so Android performs the in-place upgrade.
   - `lib/core/services/system_config_service.dart` → `currentAppVersion = 'X.Y.Z'`.
2. Commit the changes: `git commit -am "chore: release vX.Y.Z"`
3. Tag and push:
   ```bash
   git tag vX.Y.Z
   git push origin master --tags
   ```
4. GitHub Actions builds both `Faida-POS-X.Y.Z.apk` and `app-release.apk`, then publishes the GitHub Release automatically — watch the **Actions** tab.
5. Open Faida POS → **Creator Admin Hub** (tap Version 5 times in About → PIN `9999`) → set **Latest Released Version** to `X.Y.Z` → tap **Direct APK Download** or **GitHub Release Page** preset → **🚀 Publish Broadcast & Config** (optionally toggle "Retire Older Versions").
6. Every merchant device receives the push notification immediately on their screen!

### 🔑 AI API Key Management (important)

API keys are **never stored in this repository** (GitHub Push Protection blocks such pushes). Keys are injected at **build time**:

```bash
# Local development
flutter run \
  --dart-define=GEMINI_API_KEYS=key1,key2 \
  --dart-define=GROQ_API_KEYS=key1,key2 \
  --dart-define=OPENROUTER_API_KEYS=key1 \
  --dart-define=OLLAMA_API_KEYS=key1
```

For CI release builds, add the same variables as **GitHub repo Secrets** (`Settings → Secrets and variables → Actions`): `GEMINI_API_KEYS`, `GROQ_API_KEYS`, `OPENROUTER_API_KEYS`, `OLLAMA_API_KEYS` (comma-separated rotation lists). The release workflow injects them automatically. If no keys are configured, the app degrades gracefully: merchants can still use the offline advisor or enter their own key in Settings (BYOK).

> ⚠️ Note: any key compiled into an APK lives inside that APK (extractable via reverse engineering). Prefer keys with strict provider-side quotas and rotate them periodically.

### 🔐 Signing note

Release APKs are signed with the project keystore committed at `android/app/debug.keystore`. Keeping it in-repo guarantees that CI builds remain **signature-compatible** with existing merchant installs (so updates install over old versions without uninstalling). If you later move to a private release keystore, store it as a GitHub Secret and load it in the workflow instead — note that changing the signing key requires users to uninstall/reinstall once.
