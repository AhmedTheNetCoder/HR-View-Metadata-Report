# HR Data Warehouse View Metadata Report

This project generates a structured metadata snapshot for selected database views.  
Originally developed during my Eidaad training program at PDO, this is a **sanitized version** that uses dummy data for demonstration.

---

## 📌 Overview
Metadata reporting is crucial for data governance, analysis, and compliance.  
This pipeline retrieves key information about each column in a set of views, including:

- Column Name  
- Data Type  
- Nullable Status  
- Length, Precision, and Scale  

The process is designed for **reusability and scalability**, allowing it to be applied across any Oracle database, not only HR.

---

## 🚀 Features
- Extracts metadata for specified views from Oracle.
- Records details such as column name, type, length, precision, and nullability.
- Generates a professional Excel report with a clean structure.
- Can be easily extended to additional databases and schemas.

---

## 🔄 Pipeline
1. **Connect to Oracle Database**  
   - Using `cx_Oracle` library (requires Oracle Client installed).  
   - Credentials and DSN details must be updated in the script (hidden in this repo for confidentiality).

2. **Retrieve Metadata**  
   - Query Oracle’s `ALL_TAB_COLUMNS` to fetch column details for each view.  
   - Capture attributes: Data Type, Nullability, Length, Precision, and Scale.

3. **(Optional) Sample Data**  
   - In the internal PDO version, up to 10 non-null sample rows per column were included.  
   - This sanitized version omits sample values for confidentiality.

4. **Export Results**  
   - Save results into `View_Structure_Snapshot_Dummy.xlsx` for easy review.  

---

## 📊 Example Output
The report is delivered as an Excel file with the following fields:

| Instance           | View       | Attribute     | Data Type | Nullable | Length | Precision | Scale |
|--------------------|-----------|--------------|-----------|----------|--------|-----------|-------|
| WH_HR (Sanitized)  | V_PERSON  | EMPLOYEE_ID  | NUMBER    | N        | 6      | 6         | 0     |
| WH_HR (Sanitized)  | V_POSITION| POSITION_CODE| VARCHAR2  | Y        | 20     |           |       |
| WH_HR (Sanitized)  | V_OVERTIME| HOURS_WORKED | NUMBER    | Y        | 5      | 5         | 2     |

📂 A sample Excel output is included in the `outputs/` folder:  
**`View_Structure_Snapshot_Dummy.xlsx`**

---

## 🛠 Requirements

### Python Libraries
Install the required Python packages:
```bash
pip install pandas cx_Oracle openpyxl xlsxwriter
