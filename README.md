# College Management System (Django)

A web-based *College Management System* built with *Django* and *SQLite. It provides separate dashboards for **HOD, **Staff, and **Students* with features like registration/login, attendance, leave Requests, feedback, profile management, and results.


---

## Features

- *HOD (Admin/HOD)*
  - Add/Manage Staff, Students, Courses, Subjects, Sessions
  - Approve/Reject leaves
  - View attendance and basic analytics
  - Update HOD profile

- *Staff*
  - Take/Update attendance
  - Apply for leave and submit feedback
  - Add/Update student results
  - View dashboard stats

- *Student*
  - View attendance and results
  - Apply for leave and submit feedback
  - Update own profile

---

## Tech Stack

- *Backend:* Python 3.x, Django
- *Frontend:* HTML, CSS, JavaScript, Bootstrap, jQuery
- *Database:* SQLite (default)
- *Auth:* CustomUser model with user_type (HOD, Staff, Student)

---

## Quick Start

> Windows-friendly steps (also work on macOS/Linux by replacing the activation command).

1) *Create a project folder and open in VS Code*  
   text
   College_Management_System/
   

2) *Create & activate virtual environment*
   bash
   python -m venv venv
   venv\Scripts\activate    # Windows
   # source venv/bin/activate  # macOS/Linux
   

3) *Install Django*
   bash
   pip install django
   

4) *Create Django project and app*
   bash
   django-admin startproject student_management_project
   cd student_management_project
   python manage.py startapp student_management_app
   

5) *Add app to INSTALLED_APPS* in student_management_project/settings.py
   python
   INSTALLED_APPS = [
       # ...
       'student_management_app',
   ]
   

6) *Set Template & Static directories* in settings.py
   python
   from pathlib import Path
   import os

   BASE_DIR = Path(__file__).resolve().parent.parent

   TEMPLATES[0]['DIRS'] = [BASE_DIR / 'templates']

   STATIC_URL = '/static/'
   STATIC_ROOT = BASE_DIR / 'static'     # for collectstatic (prod)
   MEDIA_URL = '/media/'
   MEDIA_ROOT = BASE_DIR / 'media'
   

7) *Use custom user model*
   python
   AUTH_USER_MODEL = 'student_management_app.CustomUser'
   

8) *Project-level folders*
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

   

10) *URL routing*  
   In project student_management_project/urls.py:
   python
   from django.contrib import admin
   from django.urls import path, include
   from django.conf import settings
   from django.conf.urls.static import static

   urlpatterns = [
       path('admin/', admin.site.urls),
       path('', include('student_management_app.urls')),
   ] + (static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
        + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT))
   

   Create app urls at student_management_app/urls.py:
   python
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
   

10) *Migrate & run*
   bash
   python manage.py makemigrations
   python manage.py migrate
   python manage.py createsuperuser   # optional
   python manage.py runserver
   

11) *Open in browser*  
    Go to http://127.0.0.1:8000/

---



## Common Errors & Fixes

- *TemplateNotFound*  
  Ensure TEMPLATES[0]['DIRS'] = [BASE_DIR / 'templates'] and the file path exists.

- *ImportError: cannot import name 'views'*  
  Make sure your from . import views refers to the app’s views.py file (inside student_management_app), not the project folder.

- *Static files not loading*  
  Confirm STATIC_URL, STATIC_ROOT, and that you’ve added the static() helpers in urls.py during development.

---
