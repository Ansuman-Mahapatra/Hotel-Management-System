
<div align="center">

# 🏨 Hotel Management System

> *Front desk. Room service. Check-ins. Check-outs. All from one desktop app — built in pure Java.*

[![Java](https://img.shields.io/badge/Java-SE-ED8B00?style=for-the-badge&logo=openjdk)](.)
[![Swing](https://img.shields.io/badge/GUI-Java%20Swing%20%2B%20AWT-007396?style=for-the-badge)](.)
[![MySQL](https://img.shields.io/badge/database-MySQL-4479A1?style=for-the-badge&logo=mysql)](.)
[![JDBC](https://img.shields.io/badge/connectivity-JDBC-red?style=for-the-badge)](.)
[![Built](https://img.shields.io/badge/built-from%20scratch-brightgreen?style=for-the-badge)](.)

---

**No frameworks. No web stack. No shortcuts. A real hotel backend — written entirely in Core Java.**

</div>

---

## 📸 Project Preview

<p align="center">
  <img src="icon/dashboard.jpg" alt="Hotel Management Dashboard" width="80%"/>
</p>
<p align="center"><em>Main Dashboard — rooms, customers, staff, and operations in one view</em></p>

---

## 💡 What Is This?

Walk into any mid-sized hotel and behind the front desk is software exactly like this — managing rooms, tracking guests, logging check-ins, and keeping staff records.

This project **replicates that real-world system** from the ground up using nothing but **Core Java, Swing, and MySQL**. No Spring. No Hibernate. No web browser. Just a desktop application that a receptionist could actually sit down and use.

Two roles. Live data. Real operations. Built entirely by one developer — line by line.

---

## 🎬 Application Flow

```
▶ Run Splash.java
       │
       ▼
  ✨ Splash Screen              ← branded launch experience
       │
       ▼
  🔐 Login Window               ← role-based authentication
       │
       ├──── 👑 Admin Login
       │          │
       │          ▼
       │     Full Dashboard      ← all modules unlocked
       │
       └──── 🛎️  Reception Login
                  │
                  ▼
             Reception View      ← check-in/out + customer ops
```

---

## ✨ Features

### 🛏️ Room Management
- Add new rooms with type, floor, and pricing details
- Update room information and availability status
- **Search rooms** by number, type, or availability
- Real-time availability check before every booking — no double-booking

### 👥 Customer Management
- **New Customer Registration** — full guest profile on first visit
- **Check-In** — links guest to room, logs date, sets status to occupied
- **Check-Out** — auto-frees the room, calculates billing duration
- Full guest history stored and queryable

### 👔 Employee & Driver Management
- Add and manage hotel staff records by department
- Driver management for guest transport and airport transfers
- Department-wise view — housekeeping, kitchen, front desk, and more

### 🔐 Role-Based Access
- **Admin** — full system control: rooms, staff, reports, settings
- **Reception** — focused on guest operations: check-in, check-out, customer lookup
- Each role gets a tailored dashboard — no clutter, no unauthorized access

### 🎨 Interface & Experience
- Animated **splash screen** on every launch
- Colorful, modern GUI with **custom icons per module**
- Live data in **JTable** — populated directly from MySQL via `rs2xml`
- **JDateChooser** for clean check-in and check-out date selection
- Scrollable, sortable tables across all list views

---

## 📦 Tech Stack

| Layer | Technology | Role |
|-------|-----------|------|
| Language | Java SE (Core Java) | Entire application logic |
| GUI | Swing + AWT | All windows, panels, and components |
| Database | MySQL | Persistent hotel data |
| DB Connectivity | JDBC | Manual Java ↔ MySQL bridge |
| Table Binding | rs2xml.jar | ResultSet → live JTable |
| Date Picker | JCalendar (JDateChooser) | Check-in / check-out dates |

> **Standalone desktop application. Runs anywhere Java runs. No internet required.**

---

## 🔐 Default Login Credentials

| Role | Username | Password |
|------|----------|----------|
| 👑 Admin | `admin` | `admin123` |
| 🛎️ Reception | `reception` | `12345` |

> 🔧 Credentials are hardcoded for demo use. Migrate them to a `users` table in MySQL when extending for production.

---

## 🗄️ Database Setup

**Database name:** `hotel`

### Quick Schema Reference

```sql
CREATE DATABASE hotel;
USE hotel;

-- Rooms table
CREATE TABLE room (
    room_no     VARCHAR(10) PRIMARY KEY,
    room_type   VARCHAR(50),
    price       DOUBLE,
    status      VARCHAR(20)   -- 'Available' / 'Occupied'
);

-- Customers table
CREATE TABLE customer (
    customer_id  VARCHAR(10) PRIMARY KEY,
    name         VARCHAR(100),
    phone        VARCHAR(15),
    id_proof     VARCHAR(50),
    room_no      VARCHAR(10),
    check_in     DATE,
    check_out    DATE
);

-- Employees table
CREATE TABLE employee (
    emp_id       VARCHAR(10) PRIMARY KEY,
    name         VARCHAR(100),
    department   VARCHAR(50),
    phone        VARCHAR(15),
    salary       DOUBLE
);

-- Drivers table
CREATE TABLE driver (
    driver_id    VARCHAR(10) PRIMARY KEY,
    name         VARCHAR(100),
    phone        VARCHAR(15),
    vehicle_no   VARCHAR(20)
);
```

---

## 🚀 Running the Application

### Prerequisites

- ✅ **JDK 8+** installed
- ✅ **MySQL** running locally
- ✅ Required JARs on classpath:
  - `mysql-connector-java.jar`
  - `rs2xml.jar`
  - `jcalendar.jar`

### Steps

```bash
# 1. Clone or download the project

# 2. Import into NetBeans / IntelliJ / Eclipse

# 3. Add all JARs to the project build path

# 4. Create the database:
#    Run the SQL schema above in MySQL Workbench or terminal

# 5. Update DB credentials in your connection class:
#    Host: localhost | DB: hotel | User: root | Password: <yours>

# 6. Run Splash.java — the app launches with the splash screen
```

---

## 🏗️ Project Structure

```
HotelManagementSystem/
│
├── Splash.java                  ← Entry point — animated splash screen
├── Login.java                   ← Role-based authentication
├── Dashboard.java               ← Main navigation hub (Admin)
├── ReceptionDashboard.java      ← Reception-specific view
│
├── Room/
│   ├── AddRoom.java
│   ├── UpdateRoom.java
│   ├── SearchRoom.java
│   └── RoomAvailability.java
│
├── Customer/
│   ├── NewCustomer.java
│   ├── CheckIn.java
│   └── CheckOut.java
│
├── Employee/
│   ├── AddEmployee.java
│   └── ViewEmployee.java
│
├── Driver/
│   ├── AddDriver.java
│   └── ViewDriver.java
│
├── conn.java                    ← JDBC connection handler
│
├── icon/                        ← All custom icons and images
│   └── dashboard.jpg
│
└── lib/
    ├── mysql-connector-java.jar
    ├── rs2xml.jar
    └── jcalendar.jar
```

---

## 🔍 What Makes This Stand Out

Hotel management software is a classic enterprise problem. Solving it without a single framework is a genuine skill demonstration.

- **Multi-role login with scoped dashboards** — not just a password check; each role sees a purpose-built UI
- **Real room availability logic** — status flips between Available and Occupied on check-in/check-out
- **Check-out billing awareness** — tracks duration from check-in date to calculate stay
- **Multi-department staff management** — housekeeping, kitchen, front desk, drivers — all separate, all linked
- **Live JTable with rs2xml** — no manual table population; the ResultSet *is* the table
- **JDateChooser integration** — date fields that actually prevent invalid input

This is production-level thinking applied to a college-project context — and that gap is exactly what makes a portfolio stand out.

---

## 🙌 Developed By

<p align="center">
  <strong>Ansuman</strong><br/>
  <em>Java Desktop Application Developer · 2025</em>
</p>

<p align="center">
  Every screen, every database query, every icon, every role —<br/>
  designed and coded from scratch, entirely in Core Java.
</p>

<p align="center">
  <a href="https://github.com/Ansuman-Mahapatra" target="_blank">GitHub</a>
  &nbsp;·&nbsp;
  <a href="https://www.linkedin.com/in/ansuman-mahapatra-30661a2b2/" target="_blank">LinkedIn</a>
</p>

---

<div align="center">

⭐ **Star this repo if it helped you** ⭐  
Fork it freely — it's a solid foundation for any Java desktop project, viva demo, or portfolio showcase.

**100% Pure Java · Standalone · No External Frameworks · Runs Anywhere**

*"Real software doesn't hide behind frameworks — it earns its features."*

</div>
