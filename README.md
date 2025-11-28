# Dagster-coba-coba

### Entity Relationship Diagram (ERD)

Berikut adalah desain skema database untuk sistem E-Wallet ini. Skema didesain menggunakan pendekatan **3NF (Third Normal Form)** pada sisi transaksional (MySQL) untuk menjamin integritas data.

```mermaid
erDiagram
    USERS {
        int user_id PK
        varchar full_name
        varchar email
        varchar phone
        timestamp created_at
    }

    MERCHANTS {
        int merchant_id PK
        varchar merchant_name
        enum category
        boolean is_active
    }

    TRANSACTIONS {
        bigint transaction_id PK
        int user_id FK
        int merchant_id FK
        decimal amount
        enum status
        timestamp transaction_time
    }

    USERS ||--o{ TRANSACTIONS : "makes"
    MERCHANTS ||--o{ TRANSACTIONS : "receives"
```
