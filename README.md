# Student Complaint Management System

A simple, easy-to-read Markdown document for a Student Complaint Management System (SCMS). This document provides an overview, features, modules, tech stack, database schema, usage, and author information.

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

The Student Complaint Management System (SCMS) is a lightweight application for students to raise complaints, track their status, and for administrators to manage and resolve them. It helps centralize feedback and improves transparency in complaint handling.

---

## Features

- Student complaint submission with category  
- Complaint tracking (status and remarks)  
- Admin dashboard for managing complaints  
- Category / subcategory management  
- Role-based access (Student / Admin)

---

## System Modules

### Student (User) Module
- Register / Login  
- Submit a complaint  
- View complaint status and history  

### Admin Module
- View all complaints  
- Update status and remarks  
- Assign complaints to staff  
- Manage categories  

### Complaint Management Module
- Create / Edit / Close complaints  
- Manage categories and subcategories  

---

## Tech Stack

- **Backend:** PHP  
- **Database:** MySQL  
- **Frontend:** HTML, CSS (Bootstrap), JavaScript  
- **Storage:** Local filesystem for attachments  

---

## Database Schema (Simple)

### students
- id  
- name  
- email  
- password  
- created_at  

### admins
- id  
- name  
- email  
- password  
- role  
- created_at  

### categories
- id  
- name  
- description  

### complaints
- id  
- student_id  
- category_id  
- title  
- description  
- attachment  
- status  
- assigned_to  
- created_at  
- updated_at  

### remarks
- id  
- complaint_id  
- admin_id  
- remark  
- created_at  

---

## Usage

### Student Flow
1. Register / Login  
2. Submit a complaint  
3. Select category and description  
4. Track complaint status  
5. View admin remarks  

### Admin Flow
1. Login  
2. View and filter complaints  
3. Add remarks and update status  
4. Assign complaint to staff  
5. Close complaint  

---

## Author

**Nishita Kamble**

