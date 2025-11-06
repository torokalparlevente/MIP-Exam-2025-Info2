# Warehouse Management — C# WinForms Exam (Variant 3, Offline Edition)

**Duration:** 2 hours  
**Tools:** Visual Studio 2019 or 2022, .NET Framework 4.x, C# WinForms  
**Internet:** Not allowed  
**AI:** Not allowed (no ChatGPT, Copilot, Gemini, etc.)  
**GUI:** Mandatory (must compile and work fully offline)

---

## 1. Objectives

Develop a **Warehouse Management** application that can import data from a local JSON file, save it into a database, and display product information using WinForms controls.  
The app must run **completely offline** and include full CRUD and reporting functionality.

---

## 2. Data Source

Use the provided file: `data_warehouse.json`.

It includes:

- Warehouse info  
- Suppliers  
- Products (with dimensions and weight)  
- Stock movements (IN / OUT)  
- Taxes and meta data  
- **Invalid entries are mixed inside normal data** (missing IDs, negative stock, wrong dates, etc.)

---

## 3. Requirements

### A. Application Structure

- **Classes:** Supplier, Product, StockMovement, Warehouse.  
- **Database:** `Suppliers`, `Products`, `Movements`.  
- Use **ADO.NET** or **EF6 with SQLite** (works offline).  
- Foreign key relationships required (Product → Supplier, Movement → Product).

### B. GUI Requirements

1. **Main window**
   - Load JSON (local file only, no HTTP).  
   - Display warehouse name and total number of products.  
   - Buttons: *Import Data*, *Apply Movements*, *Show Low Stock*, *Reset Database*.

2. **Data grids**
   - Products grid with computed **current stock** after applying movements.  
   - Highlight low-stock products (stock < reorderPoint).  
   - Optional filter by supplier (ComboBox).

3. **Export**
   - Button “Export Report” → creates `stock_report.txt`.

---

## 4. Validation and Error Handling

- Skip and log invalid data to `invalid_warehouse.txt`.  
- Detect errors such as:  
  - Missing SKU or supplierId  
  - Negative stock or reorderPoint  
  - Invalid date or type in movements  
  - Nonexistent supplier references  
- App must continue execution even when invalid rows are skipped.

---

## 5. Example Output (stock_report.txt)

```
WAREHOUSE: Offline Depot (Târgu Mureș)
=======================================
HAM-100 | Hammer 16oz | 75 | OK
NAI-50  | Nails 50mm  | 70 | REORDER
GLV-M   | Work Gloves M | 20 | REORDER
---------------------------------------
Total products: 3
Products below reorder: 2
Invalid entries skipped: 2
```

---

## 6. Grading (max 10 points)

| Criterion | Points |
|------------|--------|
| JSON parsing and validation | 2 |
| Database schema and import logic | 2 |
| GUI: stock grid + filters (must work) | 3 |
| Movement application + low-stock logic | 2 |
| Reset + Export functions | 1 |

---

_This exam is part of the MIP C# WinForms module at UMFST Târgu Mureș (Offline Edition)._
