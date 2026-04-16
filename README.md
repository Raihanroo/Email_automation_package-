# 📧 Email Automation Package

A Django-based email automation platform for sending personalized course enrollment emails to students with custom templates and real-time updates.

![Django](https://img.shields.io/badge/Django-5.2.1-blue)
![Python](https://img.shields.io/badge/Python-3.8+-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## ✨ Key Features

- **Excel File Upload** - Drag & drop or click to upload Excel files with student data
- **Custom Email Templates** - Create personalized emails with placeholders: `{name}`, `{course_name}`, `{link}`
- **Manual Email Control** - Full control over when emails are sent (NO auto-send on upload)
- **Real-Time Updates** - Table auto-refreshes every 1 second showing email status
- **Mobile-Optimized Design** - Beautiful responsive HTML emails
- **Brand Colors** - Dark Navy (#0a1628) + Orange (#ff6b35) theme

## 🛠️ Technology Stack

| Component | Technology |
|-----------|------------|
| Backend | Django 5.2.1, Django REST Framework |
| Database | SQLite (development) |
| Email | Gmail SMTP with TLS |
| Frontend | HTML5, CSS3, JavaScript (Vanilla) |
| Data Processing | pandas, openpyxl |

## 📋 Prerequisites

- Python 3.8+
- pip (Python package manager)
- Gmail account with App Password

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Raihanroo/Email_automation_package-.git
cd Email_automation_package-/files/email_automation_isbd_package/email_package
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

**Requirements:**
```
Django==5.2.1
djangorestframework==3.14.0
pandas==2.0.3
openpyxl==3.1.2
```

### 3. Configure Email Settings

Edit `email_project/settings.py`:

```python
# Email Configuration
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = 'your-email@gmail.com'  # Change this
EMAIL_HOST_PASSWORD = 'your-app-password'  # Change this
```

**Get Gmail App Password:**
1. Go to: https://myaccount.google.com/apppasswords
2. Create app password for "Mail"
3. Copy 16-character password
4. Paste in settings.py

### 4. Run Migrations

```bash
python manage.py migrate
```

### 5. Start Server

```bash
python manage.py runserver
```

### 6. Open Browser

```
http://127.0.0.1:8000/
```

## 📖 How to Use

### Workflow:

```
1. Upload Excel File
   ↓
2. Data Saved (NO email sent)
   ↓
3. Click "Create Template"
   ↓
4. Write Subject & Message
   ↓
5. Use Placeholders: {name}, {course_name}, {link}
   ↓
6. Click "Send to All Students"
   ↓
7. Emails Sent Immediately
   ↓
8. Table Auto-Refreshes (Real-time updates)
```

### Excel Format:

| Name | Email | Mobile | Course Name | Link |
|------|-------|--------|-------------|------|
| Raihan Islam | raihan@example.com | 01712345678 | Python Programming | https://course-link.com |

### Template Example:

```
Hello {name},

You are interested in {course_name}. 
Click the button below to enroll:

{link}

Best regards,
Innovative Skills BD
```

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/upload/` | Upload Excel file |
| GET | `/api/students/` | Get all students |
| POST | `/api/send-template/` | Send custom template to all |
| DELETE | `/api/delete-student/<id>/` | Delete single student |
| DELETE | `/api/delete-all/` | Delete all students |

## 📁 Project Structure

```
email_project/
├── email_project/          # Main project settings
│   ├── settings.py        # Django settings
│   ├── urls.py            # Main URL routing
│   └── wsgi.py            # WSGI config
├── emails/                # Main app
│   ├── models.py          # Database models
│   ├── views.py           # API views
│   ├── serializers.py     # DRF serializers
│   ├── urls.py            # App URL routing
│   ├── templates/         # HTML templates
│   │   ├── index.html     # Main UI
│   │   └── emails/
│   │       └── course_enrollment.html
│   └── migrations/        # Database migrations
├── db.sqlite3             # SQLite database
├── manage.py              # Django management
└── requirements.txt       # Python dependencies
```

## 🔧 Troubleshooting

### Emails Not Sending
- Check Gmail credentials in settings.py
- Verify App Password is correct
- Check internet connection

### Excel Upload Fails
- Ensure Excel has columns: Name, Email, Course Name, Link
- Column names are case-insensitive

### Database Errors
```bash
python manage.py migrate
```

## 📊 Performance

- **Students:** Tested with 100+ students
- **Email Speed:** ~1 email per second
- **Database:** SQLite (suitable for < 1000 students)

## 🔐 Security

- ✅ CSRF protection enabled
- ✅ TLS encryption for emails
- ✅ App Password (not plain password)
- ✅ Input validation
- ✅ XSS protection

## 📝 License

MIT License - Free for personal and commercial use

## 👨‍💻 Developer

**Project:** Email Automation System  
**Organization:** Innovative Skills BD  
**Developer:** Raihan  
**Email:** raihanroo21@gmail.com  
**GitHub:** https://github.com/Raihanroo
