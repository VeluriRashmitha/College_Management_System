# 🎓 College Management System (Django)

A web-based **College Management System** built with **Django** and **SQLite**.  
It provides separate dashboards for **HOD**, **Staff**, and **Students** with features like registration/login, attendance, leave requests, feedback, profile management, and results.

---

## 🚀 Features

### 🔹 HOD (Admin/HOD)
- Add/Manage Staff, Students, Courses, Subjects, Sessions
- Approve/Reject leaves
- View attendance and analytics
- Update HOD profile

### 🔹 Staff
- Take/Update attendance
- Apply for leave and submit feedback
- Add/Update student results
- View dashboard stats

### 🔹 Student
- View attendance and results
- Apply for leave and submit feedback
- Update own profile

---

## 🛠 Tech Stack
- **Backend:** Python 3.x, Django  
- **Frontend:** HTML, CSS, JavaScript, Bootstrap, jQuery  
- **Database:** SQLite (default)  
- **Authentication:** CustomUser model with `user_type` (HOD, Staff, Student)  

---

## ⚡ Quick Start

Follow these steps to set up the project locally.

### 1️⃣ Clone the Repository
git clone <your-repo-url> 
2️⃣ Create Virtual Environment
python -m venv venv

3️⃣ Activate Virtual Environment
venv\Scripts\activate   # On Windows
# source venv/bin/activate   # On macOS/Linux

4️⃣ Install Requirements
pip install -r requirements.txt

5️⃣ Apply Migrations
python manage.py makemigrations
python manage.py migrate

6️⃣ Create Superuser
python manage.py createsuperuser

7️⃣ Run Development Server
python manage.py runserver


Project will be available at:
👉 http://127.0.0.1:8000/

📂 Project Structure
College_Management_System/
├── manage.py
├── student_management_project/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── student_management_app/
│   ├── migrations/
│   ├── templates/
│   │   ├── base.html
│   │   ├── home.html
│   │   ├── login_page.html
│   │   ├── registration.html
│   │   ├── student_template/
│   │   ├── staff_template/
│   │   └── hod_template/
│   ├── static/
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── views.py
│   └── urls.py
├── db.sqlite3
└── requirements.txt

📸 Screenshots

Add screenshots of dashboards for HOD, Staff, and Students here.

Example:

![HOD Dashboard](screenshots/hod_dashboard.png)
![Staff Dashboard](screenshots/staff_dashboard.png)
![Student Dashboard](screenshots/student_dashboard.png)

🤝 Contribution

Fork the repository

Create a new branch (feature-branch)

Commit your changes

Push to your branch

Open a Pull Request

📜 License

This project is licensed under the MIT License.
You’re free to use, modify, and distribute this project.


✅ This is a **complete Markdown README** — with headings, formatting, code blocks, and placeholders for screenshots.  

Do you also want me to add a **database schema diagram (ERD)** section in the README so others can understand models easily?
