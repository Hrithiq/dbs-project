# Resource Booking System (Flask + OracleDB)

A robust, full-stack web application built using Flask and Oracle Database that manages event creation, room reservations, and resource allocation across an institution. The system integrates PL/SQL stored procedures, triggers, and functions to maintain business logic, data consistency, and transactional integrity.

![Tech Stack](https://img.shields.io/badge/Python-Flask-blue) ![DB](https://img.shields.io/badge/OracleDB-PLSQL-red) ![License](https://img.shields.io/badge/License-MIT-green)

---

## Features

- **Role-based Access**  
  - Admin: View and approve all bookings  
  - Faculty: Approval of bookings 
  - Student: Create events and submit room/resource booking requests  

- **Dynamic Event Creation**  
  - Events are created by students using a PL/SQL stored procedure `create_event`.

- **Booking Request System**  
  - Students can book rooms/resources for events.  
  - Uses `create_booking` procedure with triggers checking real-time availability.

- **Approval Workflow**  
  - Admins can approve bookings via `approve_booking` procedure.  
  - Triggers and procedures ensure atomic updates to availability and status.

- **PL/SQL Integration**  
  - Stored Procedures: `create_event`, `create_booking`, `approve_booking`  
  - Triggers: `trg_check_resource_availability`, `trg_update_room_status`, etc.  
  - Functions: `get_upcoming_events`  

---

## Technologies Used

- **Backend:** Flask, cx_Oracle
- **Frontend:** HTML, Bootstrap, Jinja2 Templates
- **Database:** Oracle SQL, PL/SQL
- **Authentication:** Flask-Login
- **ORM/Drivers:** Direct cx_Oracle integration with procedures

---

## How It Works

- Students login → Create events using `create_event` procedure
- Students fill booking form → Calls `create_booking`
- Trigger `trg_check_resource_availability` ensures stock
- Admins approve → `approve_booking` logs in approval table and updates booking
