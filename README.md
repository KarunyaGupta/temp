erDiagram
    Books ||--o{ Transactions : has
    Members ||--o{ Transactions : makes
    Books {
        PK isbn STRING
        title STRING
        author STRING
        category STRING
        available BOOLEAN
        due_date DATE
    }

    Members {
        PK member_id STRING
        name STRING
        fine_amount DOUBLE
        email_address STRING
        phone_number STRING
    }

    Transactions {
        PK transaction_id STRING
        FK book_isbn STRING
        FK member_id STRING
        borrow_date DATE
        due_date DATE
        return_date DATE
        fine_amount DOUBLE
    }

    Books ||--o{ Reservations : has
    Members ||--o{ Reservations : makes
    Reservations {
        PK reservation_id STRING
        FK book_isbn STRING
        FK member_id STRING
        reservation_date DATE
        status STRING
    }

    Categories {
        PK category_id STRING
        category_name STRING
        description STRING
    }

    Books }|--|| Categories : belongs_to

    FineRecords {
        PK fine_id STRING
        FK member_id STRING
        FK transaction_id STRING
        amount DOUBLE
        date_issued DATE
        date_paid DATE
        status STRING
    }

    Members ||--o{ FineRecords : has
    Transactions ||--o{ FineRecords : generates
