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
```bash
git clone <your-repo-url>

```
2️⃣ Create Virtual Environment
```bash
python -m venv venv
```
3️⃣ Activate Virtual Environment
```bash
venv\Scripts\activate   # On Windows
# source venv/bin/activate   # On macOS/Linux
```
4️⃣ Install Requirements
```bash
pip install -r requirements.txt
```
5️⃣ Apply Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```
6️⃣ Create Superuser
```bash
python manage.py createsuperuser
```
7️⃣ Run Development Server
```bash
python manage.py runserver
```
Project will be available at:
```bash
👉 http://127.0.0.1:8000/
```
📂 Project Structure
```bash
College_Management_System/
student_management_project/
   ├─ student_management_app/
   ├─ templates/
   │  ├─ base.html
   │  ├─ home.html
   │  ├─ login_page.html
   │  ├─ registration.html
   │  ├─ student_template/
   │  ├─ staff_template/
   │  └─ hod_template/
   ├─ static/
   └─ media/
```
9️⃣ URL routing 
```bash
In project student_management_project/urls.py:

from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('student_management_app.urls')),
   ] + (static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
        + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT))
```
Create app urls at student_management_app/urls.py:
```bash
from django.urls import path
from . import views, HodViews, StaffViews, StudentViews

urlpatterns = [
    path('', views.home, name='home'),
    path('login', views.loginUser, name='login'),
    path('logout_user', views.logout_user, name='logout_user'),
    path('registration', views.registration, name='registration'),
    path('doLogin', views.doLogin, name='doLogin'),
    path('doRegistration', views.doRegistration, name='doRegistration'),
    # add more from HodViews/StaffViews/StudentViews as you build
]
```
🔟 Migrate & run
```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser   # optional
python manage.py runserver
```

11) Open in browser
```bash
Go to http://127.0.0.1:8000/
```

## Common Errors & Fixes
```bash
- *TemplateNotFound*  
  Ensure TEMPLATES[0]['DIRS'] = [BASE_DIR / 'templates'] and the file path exists.

- *ImportError: cannot import name 'views'*  
  Make sure your from . import views refers to the app’s views.py file (inside student_management_app), not the project folder.

- *Static files not loading*  
  Confirm STATIC_URL, STATIC_ROOT, and that you’ve added the static() helpers in urls.py during development.
```
---
