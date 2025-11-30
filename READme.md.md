# Student Complaint Management System

A simple, easy-to-read Markdown README for a Student Complaint Management System (SCMS). This document provides an overview, features, modules, installation steps, database schema, and basic usage instructions.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Features](#features)
3. [System Modules](#system-modules)
4. [Tech Stack](#tech-stack)
5. [Database Schema (Simple)](#database-schema-simple)
6. [Usage](#usage)
7. [Author](#author)

---

## Project Overview

The Student Complaint Management System (SCMS) is a lightweight application for students to raise complaints/requests, track their status, and for administrators to manage and resolve them. It helps centralize feedback and speeds up resolution through categorized routing and status updates.


## Features

- Student complaint submission with category and optional attachment
- Complaint tracking (status updates, remarks)
- Admin dashboard for viewing, assigning, and resolving complaints
- Department/category-based routing
- Simple reporting: number of open/closed complaints
- Role-based access (Student, Admin)


## System Modules

- **Student (User) Module**
  - Register / Login
  - Submit complaint
  - View complaint history & status

- **Admin Module**
  - View all complaints
  - Update status and add remarks
  - Assign complaints to departments or staff
  - Generate simple reports

- **Complaint Management Module**
  - Create / Edit / Close complaints
  - Category & Subcategory management


## Tech Stack

A simple recommended stack (you can swap as needed):

- Backend: PHP (or Node.js / Python Flask)
- Database: MySQL / MariaDB
- Frontend: HTML5, CSS (Bootstrap), JavaScript
- File storage: Local filesystem for attachments


## Database Schema (Simple)

### students

- `id` INT PRIMARY KEY AUTO_INCREMENT
- `name` VARCHAR(100)
- `email` VARCHAR(150) UNIQUE
- `password` VARCHAR(255) (hashed)
- `created_at` TIMESTAMP


### admins

- `id` INT PRIMARY KEY AUTO_INCREMENT
- `name` VARCHAR(100)
- `email` VARCHAR(150) UNIQUE
- `password` VARCHAR(255) (hashed)
- `role` VARCHAR(50)
- `created_at` TIMESTAMP


### categories

- `id` INT PRIMARY KEY AUTO_INCREMENT
- `name` VARCHAR(100)
- `description` TEXT


### complaints

- `id` INT PRIMARY KEY AUTO_INCREMENT
- `student_id` INT (FK -> students.id)
- `category_id` INT (FK -> categories.id)
- `title` VARCHAR(200)
- `description` TEXT
- `attachment` VARCHAR(255) NULL
- `status` ENUM('Open','In Progress','Resolved','Closed') DEFAULT 'Open'
- `assigned_to` INT NULL (FK -> admins.id)
- `created_at` TIMESTAMP
- `updated_at` TIMESTAMP


### remarks

- `id` INT PRIMARY KEY AUTO_INCREMENT
- `complaint_id` INT (FK -> complaints.id)
- `admin_id` INT NULL (FK -> admins.id)
- `remark` TEXT
- `created_at` TIMESTAMP


## Usage

- **Student flow**
  1. Register and login
  2. Click "New Complaint"
  3. Select category, write title and description, attach a file (optional)
  4. Submit and note complaint ID for tracking
  5. Check dashboard for status and admin remarks

- **Admin flow**
  1. Login to admin panel
  2. View all complaints or filter by status/category
  3. Assign complaint to a staff/admin
  4. Change status and add a remark
  5. Resolve and close the complaint


## Author

**Nishita Kamble**

