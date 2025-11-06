# Car Service Dashboard — C# WinForms Exam (Variant 2)

**Duration:** 2 hours  
**Tools:** Visual Studio 2019 or 2022, .NET Framework 4.x, C# WinForms    
**Internet:** Allowed  
**GUI:** Mandatory (working user interface required for passing)

---

## 1. Objectives

Create a **Car Service Dashboard** application that imports data from a complex JSON file, stores it in a local database, and provides a working GUI for managing clients, cars, work orders, diagnostics, and invoices.

---

## 2. Data Source

Use the provided file: `data_car_service.json`, but it needs to be downloaded from https://cdn.shopify.com/s/files/1/0883/3282/8936/files/data_car_service.json?v=1762418871 while the app is running.

It includes:

- Garage and mechanics  
- Clients and nested cars  
- Work orders (nested tasks, parts, invoices)  
- Diagnostics (OBD + test results)  
- Meta information  
- **Invalid records are embedded naturally** (e.g. negative values, bad VINs, malformed email, missing fields)

---

## 3. Requirements

### A. Application Structure

- **Classes:** Client, Car, WorkOrder, Task, Part, Mechanic, Invoice, Diagnostic, Test.  
- **Database Tables:** `Clients`, `Cars`, `WorkOrders`, `Tasks`, `Parts`, `Mechanics`, `Invoices`, `Diagnostics`, `Tests`.  
- Use **Entity Framework** or **ADO.NET + SQLite**.

### B. GUI Requirements

1. **Tab 1 — Work Orders**
   - Grid of all work orders with:
     - Computed total cost = Σ(laborH × rate) + Σ(parts.qty × unitPrice)
     - Paid/unpaid indicator (color code)
   - Buttons: *Add*, *Edit*, *Delete*, *Export Summary*.

2. **Tab 2 — Clients & Cars**
   - Master-detail display: select client → see all cars.
   - Filter by car make or year (ComboBox + TextBox).
   - Option to add new client and link a car.

3. **Tab 3 — Diagnostics**
   - Show OBD codes and test results per car.
   - Highlight failed tests (ok=false).

4. **Reset DB + Reimport JSON** button.

---

## 4. Validation and Error Handling

- Detect and ignore invalid data:
  - Bad VINs or negative odometer values
  - Negative labor hours or rates
  - Malformed email or phone numbers
  - Wrong data types (e.g., invoice currency as number)
- Log all invalid data to `invalid_car_service.txt` with a short reason per line.
- The app must continue functioning even when invalid data is skipped.

---

## 5. Example Output (workorder_summary.txt)

```
WORK ORDER SUMMARY - AUTOFIX CENTRAL
=====================================
W1 | Dacia Duster | Total: 122.5 EUR | Paid: NO
W2 | VW Golf 7     | Total: 85.0 EUR | Paid: YES
-------------------------------------
Unpaid Orders: 1
Invalid Entries Skipped: 1
```

---

## 6. Grading (max 10 points)

| Criterion | Points |
|------------|--------|
| JSON parsing and validation | 2 |
| Database schema and import logic | 2 |
| GUI: Work Orders, Clients-Cars, Diagnostics (must work) | 3 |
| Cost computation + filters | 2 |
| Reset + Export functions | 1 |

---

_This exam is part of the MIP C# WinForms module at UMFST Târgu Mureș._
