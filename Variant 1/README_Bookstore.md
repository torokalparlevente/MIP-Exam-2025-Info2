# BookStore Manager — C# WinForms Exam (Variant 1)

**Duration:** 2 hours  
**Tools:** Visual Studio 2019 or 2022, .NET Framework 4.x, C# WinForms  
**Internet:** Allowed  
**GUI:** Mandatory (working user interface required for passing)

---

## 1. Objectives

Demonstrate practical OOP and database skills in C# WinForms by building a fully functional **BookStore Manager** application that imports data from a complex JSON, stores it into a local database, and provides a working GUI for browsing, filtering, and reporting.

---

## 2. Data Source

Use the provided file: `data_bookstore.json` which has been uploaded to a server, you must download it with your app - https://cdn.shopify.com/s/files/1/0883/3282/8936/files/data_bookstore_final.json?v=1762418524 .

It includes:

- Store info (employees, address, currency)
- Authors
- Books (nested dimensions, categories, stock)
- Orders (nested items and payments)
- Payments (standalone)
- Meta

---

## 3. Requirements

### A. Application Structure

- **Classes:** Author, Book, Order, OrderItem, Customer, Payment, Employee, Store.
- **Database:** `Authors`, `Books`, `Orders`, `OrderItems`, `Customers`, `Payments`.
- **Relations:** `Book` → `Author`, `OrderItem` → `Book`, `Order` → `Customer`.
- Use **Entity Framework** or **ADO.NET + SQLite** for persistence.

### B. Mandatory GUI

1. **Tab 1 — Books**
   - Display books and authors (joined).
   - Search by title/author (TextBox + Button).
   - Button “Restock +10” updates stock in DB.

2. **Tab 2 — Orders**
   - Master-detail view: orders and items.
   - Show order total = Σ(qty × unitPrice − discount).
   - Highlight unpaid or invalid orders.

3. **Tab 3 — Reports**
   - Compute and display:
     - Total sales (sum of completed orders)
     - Books with low stock (<5)
     - Best-selling book title
   - Button “Export Report” → `sales_report.txt`.

4. **Reset Database** button:
   - Drops all tables, recreates schema, and reimports JSON.

---

## 4. Validation and Error Handling

- Ignore and log entries under `invalidSamples` → file `invalid_bookstore.txt`.
- Catch malformed data, missing fields, or failed conversions.
- The application must continue running even if invalid data exists.

---

## 5. Example Output (sales_report.txt)

```
BOOKVERSE REPORT (2025)
=======================
Total sales: 192.9 EUR
Books below stock threshold (5):
- Design Patterns (3 left)
Best-selling: Clean Code (2 units sold)
```

---

## 6. Grading (max 10 points)

| Criterion | Points |
|------------|--------|
| JSON parsing and validation | 2 |
| Database schema and import logic | 2 |
| GUI: books + orders with search/filter (must work) | 3 |
| Reports: total sales, low stock, best-seller | 2 |
| Reset + Export functions | 1 |

---

_This exam is part of the MIP C# WinForms module at UMFST Târgu Mureș._
