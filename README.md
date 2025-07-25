# PL/SQL Debugging Framework

## 🧠 Overview

This project defines a modular debugging framework in PL/SQL, allowing detailed logging and tracking of events and errors in Oracle applications. The system supports multiple severity levels and is useful for debugging and internal auditing in procedures, functions, or complex packages.

---

## 🚀 Key Features

- Support for log levels: `DEBUG`, `INFO`, `WARN`, `ERROR`, `FATAL`
- Message logging with timestamp, error codes, and source
- Centralized message storage in a `log_messages`-type table
- Easy to integrate into existing procedures
- Can be disabled easily for production environments

---

## ⚙️ File Structure

- **Types and constants**: defined for log levels
- **Public procedures**:
  - `log_message(p_level, p_msg, p_proc)` – custom logging
  - `log_error(p_err, p_proc)` – automatic exception logging
- **Supporting tables**:
  - `debug_log` – stores all log messages and execution context
- **Usage examples**:
  - `BEGIN log_message('INFO', 'Start procedure X', 'proc_test'); END;`

---

## 🧪 Example Usage

```sql
BEGIN
  debug_utils.log_message('INFO', 'Starting salary adjustment procedure', 'adjust_salaries');

  -- main logic
  ...

  debug_utils.log_message('INFO', 'Procedure completed successfully', 'adjust_salaries');
EXCEPTION
  WHEN OTHERS THEN
    debug_utils.log_error(SQLERRM, 'adjust_salaries');
    RAISE;
END;
```

---

## 🛠️ Requirements

- Oracle Database 11g or newer
- Permissions to create PL/SQL packages and tables
- Access to `DBMS_OUTPUT` for testing

---

## 📦 Installation

1. Open SQL Developer or another Oracle client
2. Run the `Framework_Debugging_PL_SQL.sql` script
3. Verify that the `debug_log` table exists
4. Integrate the `debug_utils` package into your procedures

---

## 📚 Recommendations

- Enable logging only in development/testing environments
- You can extend the framework with features like:
  - User-based filtering
  - JSON/CSV export
  - Automatic notifications for `FATAL` errors

---

## 🧑‍💻 Author

Developed by: **@dumitru-andrei.iroftei**  
Organization: **Endava**

---

## 📜 License

This project is provided "as-is". You may use and adapt the code freely within your organization.
