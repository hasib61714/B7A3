# B7A3
# 🎟️ Football Ticket Booking System
### Database Design & SQL Queries — Apollo Level 2 | Batch 7 | Assignment 3

---

## 🔗 Submission Links

| Item | Link |
|------|------|
| 📊 ERD Diagram | [View on Draw.io][(https://app.diagrams.net)](https://drive.google.com/file/d/1Th_5PH67qzYumjSxiRYc2gfB5sDCW8A0/view?usp=sharing) |
| 💻 GitHub Repository | [hasib61714/B7A3](https://github.com/hasib61714/B7A3) |
| 🎤 Interview Video | [Watch on Google Drive][(#)](https://drive.google.com/file/d/1V7wuE1Id88Zlj_WOxbF-gkoDsMcoE5sg/view?usp=sharing) |


---

## 📋 Project Overview

A relational database system for managing football fans purchasing tickets, upcoming tournament matches, and individual ticket booking receipts.

---

## 🗃️ Database Schema

### 1. Users Table

| Column | Type | Constraints |
|--------|------|-------------|
| `user_id` | SERIAL | PRIMARY KEY |
| `full_name` | VARCHAR(100) | NOT NULL |
| `email` | VARCHAR(100) | NOT NULL, UNIQUE |
| `role` | VARCHAR(50) | CHECK: `Ticket Manager` or `Football Fan` |
| `phone_number` | VARCHAR(20) | NULLABLE |

### 2. Matches Table

| Column | Type | Constraints |
|--------|------|-------------|
| `match_id` | SERIAL | PRIMARY KEY |
| `fixture` | VARCHAR(200) | NOT NULL |
| `tournament_category` | VARCHAR(100) | NOT NULL |
| `base_ticket_price` | NUMERIC(10,2) | NOT NULL, CHECK ≥ 0 |
| `match_status` | VARCHAR(50) | CHECK: `Available`, `Selling Fast`, `Sold Out`, `Postponed` |

### 3. Bookings Table

| Column | Type | Constraints |
|--------|------|-------------|
| `booking_id` | SERIAL | PRIMARY KEY |
| `user_id` | INT | FOREIGN KEY → Users(user_id) |
| `match_id` | INT | FOREIGN KEY → Matches(match_id) |
| `seat_number` | VARCHAR(10) | NULLABLE |
| `payment_status` | VARCHAR(20) | CHECK: `Pending`, `Confirmed`, `Cancelled`, `Refunded` |
| `total_cost` | NUMERIC(10,2) | CHECK ≥ 0 |

---

## 🔗 ERD Relationships

```
USERS (1) ──────── (Many) BOOKINGS
MATCHES (1) ─────── (Many) BOOKINGS
```

- **One to Many:** One User → Many Bookings
- **Many to One:** Many Bookings → One Match
- **One to One (logical):** Each booking row maps exactly one user to one match

---

## 📝 SQL Queries Summary

| # | Description | Concepts Used |
|---|-------------|---------------|
| Query 1 | Champions League available matches | `WHERE`, multiple conditions |
| Query 2 | Search users by name pattern | `ILIKE`, `OR` |
| Query 3 | Bookings with NULL payment status | `IS NULL`, `COALESCE` |
| Query 4 | Booking details with user and match info | `INNER JOIN` |
| Query 5 | All users including those with no bookings | `LEFT JOIN` |
| Query 6 | Bookings above average cost | Subquery, `AVG` |
| Query 7 | Top 2 matches skipping the most expensive | `ORDER BY`, `LIMIT`, `OFFSET` |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| PostgreSQL | Relational Database |
| SQL DDL | Table creation with constraints |
| SQL DML | Data insertion (INSERT) |
| SQL DQL | Data retrieval (SELECT + JOINs) |

---

## 📁 Project Structure

```
B7A3/
├── QUERY.sql     # Full schema, sample data, and all 7 SQL queries
└── README.md     # Project documentation
```

---

## 🚀 How to Run

**1. Connect to PostgreSQL:**
```bash
psql -U postgres
```

**2. Create a database:**
```sql
CREATE DATABASE football_tickets;
\c football_tickets
```

**3. Run the SQL file:**
```bash
psql -U postgres -d football_tickets -f QUERY.sql
```

---

## 👤 Author

**Md. Hasibul Hasan**
Apollo Level 2 — Batch 7
Green University of Bangladesh
