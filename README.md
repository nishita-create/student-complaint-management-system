# student-complaint-management-system
A digital solution to record, manage, and resolve student complaints efficiently.
```html
<!-- README for: Student Complaint Management System -->
<!-- Tip: GitHub READMEs prefer Markdown, but HTML works for custom layout/components -->

<h1 align="center">🎓 Student Complaint Management System</h1>

<p align="center">
  A streamlined web app for students to submit, track, and resolve complaints with role-based workflows and clear audit trails.
</p>

<p align="center">
  <a href="https://github.com/nishita-create/student-complaint-management-system/stargazers">
    <img alt="Stars" src="https://img.shields.io/github/stars/nishita-create/student-complaint-management-system?style=social">
  </a>
  <a href="https://github.com/nishita-create/student-complaint-management-system/issues">
    <img alt="Issues" src="https://img.shields.io/github/issues/nishita-create/student-complaint-management-system">
  </a>
  <a href="https://github.com/nishita-create/student-complaint-management-system/blob/main/LICENSE">
    <img alt="License" src="https://img.shields.io/badge/license-MIT-blue.svg">
  </a>
</p>

<hr />

<h2>📌 Overview</h2>
<p>
  This project enables <strong>students</strong> to submit complaints, while <strong>admins</strong> can triage, update status, and resolve them. It focuses on simplicity, transparency, and efficient communication across roles.
</p>

<ul>
  <li><strong>Roles:</strong> Student, Admin</li>
  <li><strong>Core functions:</strong> Submit complaints, attach files, track status, admin dashboard, filters, activity logs</li>
  <li><strong>Tech stack:</strong> PHP, MySQL, HTML/CSS, JavaScript (vanilla), XAMPP</li>
</ul>

<hr />

<h2>✨ Features</h2>
<ul>
  <li><strong>Secure authentication:</strong> Role-based access for students and admins</li>
  <li><strong>Complaint lifecycle:</strong> New → In Review → In Progress → Resolved → Closed</li>
  <li><strong>Attachments:</strong> Optional file upload with validations</li>
  <li><strong>Dashboard:</strong> Metrics, latest complaints, quick actions</li>
  <li><strong>Search & filters:</strong> Status, category, date range</li>
  <li><strong>Activity log:</strong> Who changed what, when</li>
  <li><strong>Export:</strong> CSV export (admin)</li>
  <li><strong>Email notifications (optional):</strong> Send updates to students</li>
</ul>

<hr />

<h2>🧰 Tech stack</h2>
<table>
  <thead>
    <tr>
      <th>Layer</th>
      <th>Technology</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Frontend</td>
      <td>HTML, CSS, JavaScript</td>
      <td>Responsive layout, minimal dependencies</td>
    </tr>
    <tr>
      <td>Backend</td>
      <td>PHP (>= 7.4)</td>
      <td>Procedural or lightweight MVC</td>
    </tr>
    <tr>
      <td>Database</td>
      <td>MySQL / MariaDB</td>
      <td>Relational schema, indexes for search</td>
    </tr>
    <tr>
      <td>Server</td>
      <td>XAMPP / Apache</td>
      <td>Local dev with XAMPP</td>
    </tr>
  </tbody>
</table>

<hr />

<h2>📂 Project structure</h2>
<pre><code>.
├── /public
│   ├── index.php
│   ├── login.php
│   ├── register.php
│   ├── submit-complaint.php
│   ├── complaint-view.php
│   ├── dashboard-admin.php
│   ├── assets/
│   │   ├── css/
│   │   └── js/
├── /includes
│   ├── db.php
│   ├── auth.php
│   ├── helpers.php
│   └── mailer.php
├── /uploads
│   └── complaints/
├── /sql
│   └── schema.sql
└── README.md
</code></pre>

<hr />

<h2>🗄️ Database schema (simplified)</h2>
<pre><code>-- sql/schema.sql
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(120) UNIQUE,
  password_hash VARCHAR(255),
  role ENUM('student','admin') DEFAULT 'student',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE complaints (
  id INT AUTO_INCREMENT PRIMARY KEY,
  student_id INT,
  title VARCHAR(150),
  description TEXT,
  category VARCHAR(80),
  status ENUM('new','in_review','in_progress','resolved','closed') DEFAULT 'new',
  attachment_path VARCHAR(255),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  FOREIGN KEY (student_id) REFERENCES users(id)
);

CREATE TABLE complaint_activity (
  id INT AUTO_INCREMENT PRIMARY KEY,
  complaint_id INT,
  actor_id INT,
  action VARCHAR(80),
  notes TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (complaint_id) REFERENCES complaints(id),
  FOREIGN KEY (actor_id) REFERENCES users(id)
);
</code></pre>

<hr />

<h2>🚀 Quick start (XAMPP)</h2>
<ol>
  <li><strong>Clone:</strong> <code>git clone https://github.com/nishita-create/student-complaint-management-system.git</code></li>
  <li><strong>Move to htdocs:</strong> Place project folder in <code>&lt;XAMPP&gt;/htdocs</code></li>
  <li><strong>Create DB:</strong> In phpMyAdmin, create a database (e.g., <code>scms</code>) and import <code>sql/schema.sql</code></li>
  <li><strong>Configure:</strong> Update <code>includes/db.php</code> with your DB credentials</li>
  <li><strong>Run:</strong> Start Apache &amp; MySQL in XAMPP, visit <code>http://localhost/student-complaint-management-system/public</code></li>
</ol>

<hr />

<h2>🧪 Demo credentials (sample)</h2>
<ul>
  <li><strong>Admin:</strong> admin@example.com / <code>Admin@123</code></li>
  <li><strong>Student:</strong> student@example.com / <code>Student@123</code></li>
</ul>
<p><em>Note: Replace with secure credentials in production.</em></p>

<hr />

<h2>🧭 Usage</h2>
<details>
  <summary><strong>Students</strong></summary>
  <ul>
    <li><strong>Register/Login</strong> → Submit complaint with details and optional file</li>
    <li><strong>Track status</strong> on dashboard and receive updates</li>
    <li><strong>Comment</strong> for clarifications (if enabled)</li>
  </ul>
</details>
<details>
  <summary><strong>Admins</strong></summary>
  <ul>
    <li><strong>Review</strong> new complaints and assign categories</li>
    <li><strong>Update status</strong> through lifecycle</li>
    <li><strong>Filter &amp; export</strong> data for reporting</li>
    <li><strong>Log actions</strong> for audit and transparency</li>
  </ul>
</details>

<hr />

<h2>🔌 API endpoints (optional module)</h2>
<table>
  <thead>
    <tr>
      <th>Method</th>
      <th>Endpoint</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>POST</td>
      <td><code>/api/complaints</code></td>
      <td>Create a new complaint</td>
    </tr>
    <tr>
      <td>GET</td>
      <td><code>/api/complaints?status=...</code></td>
      <td>List complaints with filters</td>
    </tr>
    <tr>
      <td>PATCH</td>
      <td><code>/api/complaints/:id</code></td>
      <td>Update complaint status/details</td>
    </tr>
    <tr>
      <td>GET</td>
      <td><code>/api/complaints/:id</code></td>
      <td>Fetch a single complaint</td>
    </tr>
  </tbody>
</table>

<hr />

<h2>🖼️ Screenshots</h2>
<p>
  <!-- Replace with actual image paths in your repo -->
  <img src="assets/screenshots/login.png" alt="Login page" width="600" />
  <img src="assets/screenshots/student-dashboard.png" alt="Student dashboard" width="600" />
  <img src="assets/screenshots/admin-dashboard.png" alt="Admin dashboard" width="600" />
</p>

<hr />

<h2>🔐 Security notes</h2>
<ul>
  <li><strong>Sanitize inputs</strong> (SQL injection, XSS protection)</li>
  <li><strong>Validate uploads</strong> (size, type, storage path)</li>
  <li><strong>Hash passwords</strong> using <code>password_hash()</code></li>
  <li><strong>Use CSRF tokens</strong> on state-changing requests</li>
</ul>

<hr />

<h2>🛠️ Development scripts</h2>
<pre><code># Setup
cp includes/db.example.php includes/db.php

# Lint PHP (if you add tools)
vendor/bin/phpcs --standard=PSR12 public includes

# Export CSV (example script)
php scripts/export-complaints.php --status=resolved --out=resolved.csv
</code></pre>

<hr />

<h2>🤝 Contributing</h2>
<p>
  Contributions are welcome! Please open an issue for feature requests or bugs. For pull requests, include clear descriptions and test steps.
</p>

<hr />

<h2>📄 License</h2>
<p>
  This project is licensed under the <a href="LICENSE">MIT License</a>.
</p>

<hr />

<h2>🙌 Acknowledgements</h2>
<ul>
  <li><strong>Bootstrap (optional):</strong> For quicker responsive UI</li>
  <li><strong>PHPMailer (optional):</strong> For email notifications</li>
</ul>

<hr />

<h2>🔗 Links</h2>
<ul>
  <li><strong>Repository:</strong> <a href="https://github.com/nishita-create/student-complaint-management-system">nishita-create/student-complaint-management-system</a></li>
</ul>
```
