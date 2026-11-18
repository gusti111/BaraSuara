<div align="center">

# BARASUARA — FAN COMMUNITY & TICKETING PROJECT

**A PHP and MySQL web application for music content, community accounts, and event-style ticket workflows.**

</div>

> **Project disclosure**  
> This is an independent fan-made development project. It is not an official Barasuara website, official ticketing service, or an endorsed product of the band or its management. Event details and purchase links must be independently verified.

---

## Overview

BaraSuara is a server-rendered PHP website that combines music and editorial content with member accounts and an event-oriented ticket ordering flow. The repository includes public-facing pages and an AdminLTE-based administration area for managing content, users, orders, and ticket scanning workflows.

## Application areas

### Public website

- Home page with database-driven news, album, and tour highlights.
- About and contact pages.
- Music and album content.
- Tour and event listings.
- Member registration, login, and account session handling.
- Ticket order and order-status pages.
- Newsletter subscription handling.

### Administration

- Administrator login and logout.
- User and account management.
- Music / album content management.
- News and tour management.
- Order management and inquiry handling.
- Gate-scanner role and ticket scanning interface.

The actual behavior of order and scan workflows depends on the configured database schema and the current data in the local environment.

## Technology

| Layer | Implementation |
| --- | --- |
| Server-side application | Native PHP |
| Database access | PDO |
| Database | MySQL / MariaDB |
| Admin interface | AdminLTE assets |
| Front end | HTML, CSS, JavaScript |
| Local development | PHP built-in server, XAMPP, or Laragon |

## Requirements

- PHP 8.1+ recommended.
- MySQL or MariaDB.
- PHP PDO MySQL extension (pdo_mysql).
- A modern browser.
- XAMPP, Laragon, or an equivalent local PHP/MySQL environment.

## Database setup

The application uses the db_barasuara database by default. The connection configuration is currently defined in config/database.php:

- Host: 127.0.0.1
- Port: 3306
- Database: db_barasuara
- Local default user: root

The checked-in configuration uses local-development defaults. Replace them with environment-specific credentials and a dedicated least-privilege database user before any shared or hosted deployment.

The repository includes multiple SQL files:

- database.sql — primary schema / seed structure.
- database_update_ticketing.sql — ticketing-related schema update.
- crud_operations.sql — additional data operations and setup material.

**Important:** inspect each SQL file before importing. The primary database script contains table drop and recreation statements. Back up existing data and use a disposable database when testing the initial schema.

## Run locally

1. Clone the repository into your local web workspace.
2. Create a MySQL database named db_barasuara.
3. Review the SQL files and import the schema required by the version you are running.
4. Configure config/database.php for your local MySQL instance.
5. Ensure the PHP PDO MySQL extension is enabled.
6. From the project root, start the PHP development server:

       php -S 127.0.0.1:8000

7. Open:

       http://127.0.0.1:8000/index.php

For XAMPP or Laragon, you can instead place the repository inside the configured web root and open the corresponding local project URL.

## Repository structure

    BaraSuara/
    ├── admin/             # AdminLTE-based management area
    ├── config/            # Database connection configuration
    ├── includes/          # Shared layout, bootstrap, and ticketing helpers
    ├── images/            # Website media
    ├── style/             # Front-end styles
    ├── lib/               # Client-side scripts
    ├── index.php
    ├── login.php
    ├── register.php
    ├── music.php
    ├── tour.php
    ├── order.php
    ├── process-order.php
    ├── my-orders.php
    └── database*.sql

## Security and operational notes

- Move database credentials out of committed source before deployment.
- Use prepared statements and validate all user-submitted data server-side.
- Keep CSRF protection enabled for state-changing forms.
- Restrict uploaded files by MIME type, extension, and size if upload features are enabled.
- Require authenticated and role-authorized access for administrative and scanner functions.
- Never treat a static event listing as proof of a real event or ticket inventory.
- Do not use real customer records or payment information in a public demo database.

## Project status

An in-development PHP/MySQL project with public content pages, account workflows, administration modules, and ticket-ordering source. Production payment integration, live ticket inventory, real-world event authorization, and deployment readiness must be verified separately.

## Repository

[github.com/gusti111/BaraSuara](https://github.com/gusti111/BaraSuara)