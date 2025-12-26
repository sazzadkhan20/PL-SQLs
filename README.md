# PL/SQL Swimming Pool Management System

A comprehensive database project demonstrating advanced PL/SQL concepts through a Swimming Pool Management System.

## 📋 Project Overview

This project implements a complete swimming pool management database using Oracle PL/SQL, covering fundamental to advanced database concepts including procedures, functions, triggers, cursors, and transaction management.

## 🎯 Learning Objectives

### Core PL/SQL Concepts
- **Basic Syntax** - Variables, data types, and PL/SQL block structure
- **Operators & Conditionals** - IF-THEN-ELSE, CASE statements
- **Loops** - FOR, WHILE, LOOP with EXIT conditions
- **Stored Procedures** - Reusable code blocks with IN/OUT parameters
- **Functions** - Return value operations
- **Packages** - Encapsulation of procedures and functions
- **Cursors** - Row-by-row data processing (implicit & explicit)
- **Records** - Composite data structures
- **Triggers** - Automatic event-driven actions
- **Exception Handling** - Error management and recovery

### Database Management
- **Transactions** - COMMIT, ROLLBACK, SAVEPOINT operations
- **Locking** - Concurrency control and deadlock prevention
- **Relational Algebra** - Set operations and query optimization
- **Normalization** - 1NF, 2NF, 3NF, BCNF implementation
- **ER & Schema Diagrams** - Database design and modeling

## 🏊 System Features

The Swimming Pool Management System includes:

- Member registration and management
- Pool booking and scheduling
- Trainer assignment
- Payment processing
- Locker allocation
- Membership renewal tracking
- Usage statistics and reporting

## 📂 Project Structure

```
swimming-pool-db/
├── schema/
│   ├── er_diagram.png
│   ├── schema_diagram.sql
│   └── normalization_docs.md
├── tables/
│   └── create_tables.sql
├── procedures/
│   └── stored_procedures.sql
├── functions/
│   └── user_functions.sql
├── packages/
│   └── pool_management_pkg.sql
├── triggers/
│   └── audit_triggers.sql
├── cursors/
│   └── cursor_examples.sql
├── transactions/
│   └── transaction_examples.sql
└── queries/
    └── sample_queries.sql
```

## 🚀 Quick Start

### Prerequisites
- Oracle Database 11g or higher
- SQL*Plus or SQL Developer

### Installation

1. Connect to Oracle database:
```sql
sqlplus username/password@database
```

2. Execute schema creation:
```sql
@schema/create_tables.sql
```

3. Load sample data:
```sql
@data/insert_sample_data.sql
```

4. Compile packages and procedures:
```sql
@packages/pool_management_pkg.sql
```

## 💡 Key Implementations

### Example: Stored Procedure
```sql
CREATE OR REPLACE PROCEDURE register_member(
    p_name VARCHAR2,
    p_email VARCHAR2
) AS
BEGIN
    INSERT INTO members VALUES(...);
    COMMIT;
END;
```

### Example: Trigger
```sql
CREATE OR REPLACE TRIGGER audit_booking
AFTER INSERT ON bookings
FOR EACH ROW
BEGIN
    INSERT INTO audit_log VALUES(:NEW.booking_id, SYSDATE);
END;
```

### Example: Exception Handling
```sql
BEGIN
    -- operations
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Record not found');
    WHEN OTHERS THEN
        ROLLBACK;
        RAISE;
END;
```

## 📊 Sample Queries

```sql
-- Get active members
SELECT * FROM members WHERE status = 'ACTIVE';

-- Calculate monthly revenue
SELECT SUM(amount) FROM payments 
WHERE payment_date >= TRUNC(SYSDATE, 'MM');

-- Find available time slots
SELECT * FROM pool_schedule 
WHERE booking_status = 'AVAILABLE';
```

## 🔒 Transaction & Locking Examples

```sql
-- Transaction with savepoint
BEGIN
    INSERT INTO bookings...;
    SAVEPOINT sp1;
    UPDATE members...;
    IF condition THEN
        ROLLBACK TO sp1;
    END IF;
    COMMIT;
END;
```

## 🎓 Topics Covered

| Topic | Files | Description |
|-------|-------|-------------|
| Basic Syntax | `basics/*.sql` | Variables, blocks, declarations |
| Operators | `operators/*.sql` | Arithmetic, logical, comparison |
| Loops | `loops/*.sql` | FOR, WHILE, LOOP examples |
| Procedures | `procedures/*.sql` | Member, booking procedures |
| Functions | `functions/*.sql` | Calculate fees, validate data |
| Packages | `packages/*.sql` | Pool management package |
| Cursors | `cursors/*.sql` | Member reports, statistics |
| Records | `records/*.sql` | Custom data types |
| Triggers | `triggers/*.sql` | Audit, validation triggers |
| Exceptions | `exceptions/*.sql` | Error handling patterns |
| Transactions | `transactions/*.sql` | ACID properties demo |
| Locking | `locking/*.sql` | Concurrency examples |

## 📖 Documentation

Detailed documentation for each concept is available in the `docs/` directory:
- `PL_SQL_Basics.md`
- `Advanced_Features.md`
- `Database_Design.md`
- `Best_Practices.md`

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

## 📝 License

This project is for educational purposes.

## 👨‍💻 Author

Database Management System Course Project

---

**Note**: This is a learning project demonstrating PL/SQL concepts through a real-world application scenario.
