# SPEC.md — MeuBolso

## 1. Project Name

**MeuBolso — Controle Financeiro Pessoal**

---

## 2. Project Description

MeuBolso is a simple mobile application for personal financial organization. The application allows users to register, view, edit, and delete income and expenses, helping them understand how their money is being used.

The main problem addressed by the application is the difficulty of keeping small daily financial transactions organized. The target audience is people who want a simple way to record their personal expenses and income directly from their mobile device.

The application will be developed as an individual university project. Its first version will focus on a realistic and manageable set of features while still providing meaningful opportunities to learn mobile development, local data persistence, device APIs, and AI-assisted development.

---

## 3. Main Features

### 3.1 Dashboard

The home screen will present a summary of the user's financial information.

The user should be able to see:

- Current balance.
- Total income.
- Total expenses.
- Number of registered transactions.
- A short list of recent transactions.

The values shown on the dashboard must be calculated from the transactions stored in the local database.

### 3.2 Register Transaction

The user will be able to register a financial transaction.

Each transaction will contain:

- Description.
- Amount.
- Type: income or expense.
- Category.
- Date.
- Optional location information obtained from the device's GPS.

The application must validate required fields before saving the transaction.

### 3.3 List Transactions

The application will provide a screen containing all registered transactions.

The user should be able to:

- View transaction details.
- Distinguish income from expenses.
- See the transaction date.
- See the category.
- See the registered location when available.

The list should be ordered with the most recent transactions first.

### 3.4 Edit Transaction

The user will be able to modify an existing transaction.

The application must allow the user to change:

- Description.
- Amount.
- Type.
- Category.
- Date.
- Location.

### 3.5 Delete Transaction

The user will be able to delete a transaction.

Before permanently deleting the record, the application should display a confirmation message to prevent accidental deletion.

### 3.6 Categories

Transactions will use predefined categories.

Initial categories:

- Food.
- Transportation.
- Housing.
- Education.
- Health.
- Entertainment.
- Shopping.
- Salary.
- Other.

The category system should make it easier to understand where money is being spent.

### 3.7 Transaction Location

When registering a transaction, the user may request the application's current location.

The application will use the device's location service to obtain approximate geographic coordinates.

The coordinates will be stored with the transaction when permission is granted.

The location feature is optional for individual transactions, so the application remains functional if the user denies location permission.

### 3.8 Local Data Persistence

Transactions must remain available after the application is closed and reopened.

The application will use a local database to store transaction data.

The first version will not require a remote backend or user account.

---

## 4. Native APIs and Device Capabilities

### 4.1 GPS / Location Services

**Capability:** Device GPS/location services.

**Why it is needed:** The application will allow the user to associate a financial transaction with the place where it occurred.

**Contribution to functionality:** When the user chooses to use the location feature, the application requests location permission and obtains the device's current latitude and longitude. These values can be associated with the transaction.

Example:

> Restaurant — R$ 35.00 — Food — 24/10/2026 — Location available

The application must continue working normally when the user denies location permission.

### 4.2 Native Permission API

**Capability:** Android/iOS runtime permission system for location access.

**Why it is needed:** Access to the device's location requires explicit permission from the user.

**Contribution to functionality:** The application will request permission only when the user attempts to use the location feature and will handle both granted and denied permission states.

---

## 5. Technical Architecture

### 5.1 Development Framework

The proposed framework is **Flutter** with the **Dart** programming language.

Flutter is appropriate because it allows the project to target Android from a single codebase and provides a practical environment for building the required mobile interface.

The initial target platform will be **Android**.

### 5.2 Local Database

The application will use **SQLite** for local data persistence.

A Flutter SQLite package such as `sqflite` may be used during implementation.

The main table will be:

```text
transactions
--------------------------------
id              INTEGER PRIMARY KEY
description     TEXT
amount          REAL
type            TEXT
category        TEXT
date            TEXT
latitude        REAL NULL
longitude       REAL NULL
```

`latitude` and `longitude` may be null when the user does not use the location feature or does not grant permission.

### 5.3 Application Structure

The project should be organized into simple layers:

```text
lib/
├── main.dart
├── models/
│   └── transaction.dart
├── database/
│   └── database_helper.dart
├── screens/
│   ├── home_screen.dart
│   ├── transactions_screen.dart
│   └── transaction_form_screen.dart
├── services/
│   └── location_service.dart
└── widgets/
    ├── transaction_card.dart
    └── summary_card.dart
```

The exact structure may be adjusted by the AI coding agent if a simpler and more maintainable organization is identified.

### 5.4 Navigation

The first version will contain three main screens:

1. **Dashboard**
2. **Transactions**
3. **Add/Edit Transaction**

Navigation should be simple and appropriate for a mobile application.

A bottom navigation bar may be used for the Dashboard and Transactions sections.

### 5.5 External Services

No remote backend is required for the functional first version.

No external financial API is required.

This decision keeps the project achievable for a single student within the available development time.

---

## 6. Functional Requirements

The application will be considered functional and complete when the following requirements are implemented:

- [ ] Application launches successfully on Android.
- [ ] User can access the Dashboard.
- [ ] User can create an income transaction.
- [ ] User can create an expense transaction.
- [ ] User can view all transactions.
- [ ] User can edit a transaction.
- [ ] User can delete a transaction.
- [ ] Transactions persist after restarting the application.
- [ ] Dashboard calculates income, expenses, and balance.
- [ ] User can select a transaction category.
- [ ] Application requests location permission when the location feature is used.
- [ ] Application can obtain device location when permission is granted.
- [ ] Location coordinates can be stored with a transaction.
- [ ] Application remains functional if location permission is denied.
- [ ] Required form fields are validated.
- [ ] Application can run on a real Android device or Android emulator.

---

## 7. Optional Improvements

The following features are intentionally outside the essential scope. They may be implemented only if sufficient development time remains:

- Monthly spending charts.
- Filtering transactions by category.
- Searching transactions.
- Exporting transactions to CSV.
- Dark mode.
- Custom categories.
- Monthly budgets.
- Notifications for budget limits.
- Displaying transactions on a map.
- Cloud synchronization.
- User authentication.
- Backup and restore.

These features must not delay or compromise the required first version.

---

## 8. Scope and Time Management

The application is designed for an individual student and should prioritize a small, complete, functional product instead of a large application with unfinished features.

### Priority 1 — Essential

The following features have the highest priority:

1. Basic Flutter project setup.
2. Dashboard.
3. Transaction registration.
4. Transaction listing.
5. Transaction editing.
6. Transaction deletion.
7. SQLite persistence.
8. Income/expense calculations.
9. Location API integration.
10. Permission handling.
11. Basic validation and error handling.

### Priority 2 — Improvements

After all essential functionality is complete, optional features may be considered.

The project must always prioritize a stable and demonstrable first version over additional functionality.

---

## 9. AI-Assisted Development

The application will be implemented with assistance from an AI coding agent during the following development phases of the course.

The AI agent may assist with:

- Project structure.
- Flutter and Dart implementation.
- SQLite integration.
- CRUD operations.
- Location API integration.
- Permission handling.
- UI components.
- Debugging.
- Testing.
- Documentation.

The student will review, test, and validate the generated implementation rather than blindly accepting generated code.

Important implementation decisions and significant AI-assisted development steps should be documented during the implementation phase.

---

## 10. Testing Requirements

The following scenarios should be tested before the project is considered complete:

### Transaction tests

- Create an income.
- Create an expense.
- Edit an existing transaction.
- Delete a transaction.
- Restart the application and confirm that transactions remain saved.

### Calculation tests

- Confirm that total income is calculated correctly.
- Confirm that total expenses are calculated correctly.
- Confirm that balance equals income minus expenses.

### Location tests

- Grant location permission and create a transaction with location.
- Deny location permission and confirm that the transaction can still be created.
- Confirm that location data is stored when available.

### Validation tests

- Attempt to save an empty transaction.
- Attempt to enter an invalid amount.
- Confirm that appropriate validation messages are displayed.

---

## 11. Expected Final Result

At the end of the implementation phases, MeuBolso should be a functional Android mobile application that allows a user to manage personal income and expenses using local SQLite storage and optionally associate transactions with the device's current location.

The project should demonstrate practical knowledge of:

- Mobile UI development.
- Flutter and Dart.
- Local database persistence.
- CRUD operations.
- Device-specific APIs.
- Runtime permissions.
- Basic application architecture.
- Input validation.
- Testing.
- AI-assisted software development.

The scope is intentionally limited so that a single student can complete the required functionality within the available course time while still having meaningful opportunities for learning and experimentation.
