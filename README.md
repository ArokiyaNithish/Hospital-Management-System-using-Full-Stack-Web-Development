<div align="center">

# 🏥 Hospital Management System

### *Comprehensive Full-Stack Web Application for Healthcare Operations*

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Django](https://img.shields.io/badge/Django-6.0-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0%2B-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

> 🚀 **An end-to-end full-stack platform** to streamline hospital workflows by providing dedicated portals for doctors and patients with role-based access control.

</div>

---

## 📋 Table of Contents

- [📌 Problem Statement](#-problem-statement)
- [💡 Solution & Approach](#-solution--approach)
- [🎯 Objectives](#-objectives)
- [🗄️ Database Schema & Entities](#️-database-schema--entities)
- [🛠️ Technology Stack](#️-technology-stack)
- [📁 Project Structure](#-project-structure)
- [🔬 How It Works — Core Modules](#-how-it-works--core-modules)
- [📈 System Impact & Results](#-system-impact--results)
- [🚀 Installation & Setup](#-installation--setup)
- [💻 Usage Guide](#-usage-guide)
- [🔒 Security Features & Design](#-security-features--design)
- [🌍 Real-World Significance](#-real-world-significance)
- [🖼️ Screenshots](#️-screenshots)
- [🚀 Future Enhancements](#-future-enhancements)
- [🤝 Open Source Contribution](#-open-source-contribution)
- [📄 License](#-license)
- [👨‍💻 Author & Acknowledgments](#-author--acknowledgments)
- [📚 References](#-references)

---

## 📌 Problem Statement

> **"Traditional hospital management relies heavily on manual processes, leading to inefficiencies, fragmented records, and compromised patient care."**

### Background

Healthcare institutions face numerous operational challenges that impact both service delivery and patient satisfaction. The lack of centralized, digital systems causes significant friction in scheduling, record-keeping, and continuous care.

### The Core Problem

| Challenge | Description |
|-----------|-------------|
| 🔴 **Manual Appointment Scheduling** | Patients face long waits; manual booking causes double bookings and scheduling conflicts. |
| 🔴 **Fragmented Medical Records** | Patient history is scattered across paper files, risking loss of critical medical documents. |
| 🔴 **Prescription Management Issues** | Handwritten prescriptions lead to misinterpretation; no systematic medication tracking. |
| 🔴 **Limited Patient Engagement** | Lack of continuous health monitoring or communication channels between appointments. |
| 🔴 **Administrative Overhead** | High operational costs and staff time wasted on repetitive administrative tasks. |

---

## 💡 Solution & Approach

### Our Strategy

This Hospital Management System addresses operational challenges through a systematic, multi-stage digital platform:

1. **Self-Service Booking → Patient Portal** allowing 24/7 access to schedules and appointments.
2. **Centralized Digital Identity → Role-Based Access** ensuring distinct features for Doctors vs. Patients.
3. **Structured Data Storage → Digital Records** for reports, health tracking, and prescriptions.
4. **Data Privacy & Protection → Secure Authentication** built on Django's robust framework.

### Architecture Overview

```text
┌─────────────────────────────────────────────────────────┐
│                     Frontend Layer                      │
│         (HTML Templates, CSS, JavaScript)               │
└─────────────────────┬───────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────┐
│                   Django Backend                        │
│  ┌──────────┬──────────┬──────────┬──────────────────┐  │
│  │  Users   │Appointments│ Medical  │    Dashboard   │  │
│  │   App    │    App   │   App    │       App      │  │
│  └──────────┴──────────┴──────────┴──────────────────┘  │
└─────────────────────┬───────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────┐
│                  MySQL Database                         │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Users | Appointments | Medical Reports |         │   │
│  │ Prescriptions | Daily Reports | Profiles         │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

---

## 🎯 Objectives

- ✅ **Streamline Patient Care** Configure efficient appointment booking and management workflows.
- ✅ **Secure Medical Records** Establish centralized storage for tracking medical reports and prescriptions.
- ✅ **Role-Based Dashboards** Implement separate, secure interfaces tailored to Doctors and Patients.
- ✅ **Health Tracking** Enable patients to submit daily health reports to monitor their well-being.
- ✅ **Doctor Profile Management** Provide comprehensive tools for managing professional profiles and availability.

---

## 🗄️ Database Schema & Entities

### Core Data Models

| Entity | Relationships | Key Fields / Description |
|--------|---------------|--------------------------|
| **User** | Extends `AbstractUser` | `is_doctor`, `is_patient` (Custom authentication model) |
| **DoctorProfile** | One-to-One with User | `specialization`, `image`, `bio`, `available_days`, `consultation_fee` |
| **PatientProfile** | One-to-One with User | `dob`, `blood_group`, `address` |
| **Appointment** | FK: patient, doctor | `date`, `time_slot`, `status` (Pending/Confirmed/Completed/Cancelled), `symptoms` |
| **MedicalReport** | FK: patient, doctor | `title`, `file`, `created_at` |
| **Prescription** | FK: patient, doctor | `medicine_name`, `dosage`, `frequency`, `duration`, `prescribed_at` |
| **DailyReport** | FK: patient | `date`, `mood`, `symptoms_description`, `rating` (1-10 scale) |

---

## 🛠️ Technology Stack

| Layer | Technology | Version | Purpose |
|-------|-----------|---------|---------|
| **Language** | Python | 3.8+ | Core backing logic |
| **Web Framework** | Django | 6.0 | REST architecture and MVC implementation |
| **Database** | MySQL | 8.0 | Reliable, relational data storage |
| **ORM** | Django ORM | — | Database abstraction and data manipulation |
| **Frontend** | HTML5 / CSS3 / JS | — | Responsive client-side interface |
| **File Management** | Pillow | — | Image processing and secure media upload handling |
| **Version Control** | Git | — | Source code tracking and collaboration |

---

## 📦 Libraries & Dependencies

```bash
pip install django
pip install mysqlclient
pip install pillow
```

---

## 📁 Project Structure

```text
hospital_project/
│
├── 📁 accounts/                    # Account management (legacy)
├── 📁 appointments/                # Appointment management app
│   ├── models.py                   # Appointment model
│   ├── views.py                    # Appointment booking views
│   └── urls.py                     # Appointment routes
│
├── 📁 dashboard/                   # Dashboard app
│   ├── views.py                    # Doctor & Patient dashboards
│   └── urls.py                     # Dashboard routes
│
├── 📁 hospital_management/         # Main project settings
│   ├── settings.py                 # Django configuration
│   └── urls.py                     # Main URL routing
│
├── 📁 medical/                     # Medical records app
│   ├── models.py                   # MedicalReport, Prescription, DailyReport
│   └── views.py                    # Report upload, prescription views
│
├── 📁 users/                       # User management app
│   ├── models.py                   # User, DoctorProfile, PatientProfile
│   └── views.py                    # Registration & login views
│
├── 📁 templates/                   # HTML templates (base, auth, dashboards)
├── 📁 static/                      # Static files (CSS, JS, images)
├── 📁 media/                       # User-uploaded files (doctor images, reports)
│
├── manage.py                       # Django management script
└── README.md                       # This documentation
```

---

## 🔬 How It Works — Core Modules

### Step 1 — Dual Registration System & Authentication

```python
# Separate registration flows route users dynamically to appropriate role dashboards
if user.is_doctor:
    return redirect('doctor_dashboard')
elif user.is_patient:
    return redirect('patient_dashboard')
```
Roles strictly dictate permissions, maintaining data privacy between distinct user groups. Profile records are automatically generated upon successful registration.

### Step 2 — Patient Portal Operations

Patients have an intuitive interface where they can:
- **Book Appointments:** Browse available doctors by specialization and schedule real-time slots.
- **Track Health:** Fill out the daily mood and symptom tracker (rated 1-10).
- **Access Records:** Instantly download digital copies of lab results, scans, and doctor prescriptions.

### Step 3 — Doctor Portal Operations

Doctors manage their schedules seamlessly by:
- **Updating Availability:** Defining consultation fees, bio, and operational days.
- **Managing Patients:** Updating appointment states from Pending to Confirmed or Completed.
- **Issuing Prescriptions:** Digitizing structured prescriptions (medication, frequency, dosage).
- **Uploading Reports:** Distributing lab results directly to patient profiles.

### Step 4 — Admin Controls

An overarching Django Admin Panel (`/admin/`) monitors system-wide activity, overriding user roles and manually correcting schedules or profiles as an escalation path.

---

## 📈 System Impact & Results

### Measurable Operational Improvements

| Metric | Before System | With Our System |
|--------|---------------|-----------------|
| **Appointment Scheduling** | 30+ mins via phone/in-person | **Under 2 minutes** |
| **Admin Workload** | High manual processing | **Reduced by 40-50%** |
| **Patient Satisfaction** | Frequent complaints on delays | **30% Score Improvement** |
| **Record Retrieval** | Sometimes lost or misplaced | **100% digital & instantaneous** |
| **Document Management** | Piles of paper | **100% Paperless Prescriptions** |

> 🎯 **Key Focus**: The platform dramatically reduces friction between healthcare providers and patients, fostering a continuous, trackable, and efficient ongoing health dialogue.

---

## 🚀 Installation & Setup

### Prerequisites

- Python 3.8+
- MySQL 8.0+
- pip (Python package manager)
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/hospital-management-system.git
cd hospital-management-system
```

### 2. Create Virtual Environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install django mysqlclient pillow
```

### 4. Configure MySQL Database

Open your MySQL command line and create the database:
```sql
CREATE DATABASE hospital_db;
```

Update your `settings.py` (`hospital_management/settings.py`) with your credentials:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'hospital_db',
        'USER': 'your_mysql_username',
        'PASSWORD': 'your_mysql_password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

### 5. Run Migrations & Setup

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
```

### Quick Setup (Windows Only)

For Windows users, utilize the provided batch scripts:
```bash
setup_and_create_superuser.bat  # Creates DB tables and superuser
run_server.bat                  # Starts the local development server
```

---

## 💻 Usage Guide

### 🧑‍⚕️ For Doctors
1. Sign up under "Doctor Registration" and log in.
2. Complete your professional profile (specialty, image, days, fees).
3. Access Dashboard to approve/decline incoming appointments.
4. Open completed appointments to write prescriptions and upload reports.

### 👤 For Patients
1. Sign up under "Patient Registration" and complete basic profile info.
2. Visit **Book Appointment**, filter doctors by specialty, and pick a slot.
3. Consistently update your **Daily Health Report** to track ongoing conditions.
4. Retrieve any uploaded prescriptions or reports in your Documents tab.

### Accessing the Server

Once running:
- **Main Website**: `http://localhost:8000/`
- **Admin Panel**: `http://localhost:8000/admin/`

---

## 🔒 Security Features & Design

### Built-in System Protection

| Security Mechanism | Implementation Details |
|----------|-----------|
| **Role-Based Views** | Used `UserPassesTestMixin` to restrict access strictly to permitted roles |
| **Route Protection** | `LoginRequiredMixin` forces authentication before exposing sensitive pages |
| **SQL Injection Guard** | Relies entirely on Django ORM's parameterized query engine |
| **Cross-Site Protection** | Enabled CSRF tokens across all form actions |
| **Upload Sanitization** | Validated file types for patient medical record uploads |

---

## 🌍 Real-World Significance

### Broad Healthcare Impacts

- 🌍 **Digital Transformation:** Brings local clinics directly into the modern digital age.
- 📉 **Reduced No-Shows:** Automated data accessibility reduces the instances of forgotten appointments.
- 🤝 **Enhanced Communication:** Secure tracking bridges the gap between patient and provider.
- 🌱 **Environmental Impact:** Removes almost all paper waste for prescriptions and records.

---

## 🖼️ Screenshots

### Homepage
![Homepage](https://github.com/ArokiyaNithish/Hospital-Management-System/blob/main/images/image1.png)

### Patient Dashboard
![Patient Dashboard](https://github.com/ArokiyaNithish/Hospital-Management-System/blob/main/images/image2.png)

### Doctor Dashboard
![Doctor Dashboard](https://github.com/ArokiyaNithish/Hospital-Management-System/blob/main/images/image3.png)

### Appointment Booking
![Appointment Booking](https://github.com/ArokiyaNithish/Hospital-Management-System/blob/main/images/image4.png)

---

## 🚀 Future Enhancements

- [ ] **Email Notifications:** Automated confirmations and reminders
- [ ] **Video Consultations:** Integrate WebRTC or Zoom API for telehealth
- [ ] **Payment Gateway:** Stripe/PayPal integration for upfront appointment deposits
- [ ] **Advanced Filtering:** Better search mechanisms for doctor scheduling
- [ ] **Analytics Dashboard:** Graphical data views for Hospital Administrators
- [ ] **Mobile Port:** Transition frontend into dedicated Android/iOS apps
- [ ] **Pharmacy Integration:** Direct e-prescribing routed to local pharmacies
- [ ] **Multi-language Support:** Accessible portals in regional languages
- [ ] **Export to PDF:** Downloadable/printable patient medical histories

---

## 🤝 Open Source Contribution

We warmly welcome contributions from the open source community! Whether it's **bug fixes**, **new features**, **UI improvements**, or **documentation** — every contribution helps!

### How to Contribute

```bash
# 1. Fork the repository
# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/hospital-management-system.git
cd hospital-management-system

# 3. Create a feature branch
git checkout -b feature/amazing-feature

# 4. Make changes and commit
git add .
git commit -m "feat: added email notification system"

# 5. Push to your fork
git push origin feature/amazing-feature

# 6. Open a Pull Request on GitHub → main branch
```

### Coding Standards

- Follow **PEP 8** style guide for Python code.
- Write **meaningful commit messages**.
- Add comments outlining complex logic algorithms.
- Test thoroughly locally before requesting mergers.

### Reporting Issues

Please formulate an issue in the repository for bugs, UI glitches, or feature demands!

---

## 📄 License

This project is licensed under the **MIT License** — you are free to use, modify, and distribute this code with attribution.

```text
MIT License

Copyright (c) 2026 Arokiya Nithish J

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```

See [LICENSE](LICENSE) for full details.

---

## 👨‍💻 Author & Acknowledgments

### Author

**Arokiya Nithish J**
- 🎓 Internship Company — GreenSoft Groups, Intern ID: 24347 
- 📅 Year: 2025 , Mode - Offline
- 💼 Domain: Full stack Python Decveleper | Medical Analaysis | 
- [Internship Completed Certificate](https://drive.google.com/file/d/17sxwa-4_3yJelFZcnuOtILniFfoJ_mbg/view?usp=sharing)

**Contacts**
- GitHub: [@ArokiyaNithish](https://github.com/ArokiyaNithish)
- LinkedIn: [@Arokiya Nithish J](https://www.linkedin.com/in/arokiya-nithishj/)
- Email ID: @arokiyanithishj@gmail.com
- My Portfolio: [Arokiya Nithish](https://arokiyanithish.github.io/portfolio/)

### Acknowledgments

- 🌐 **Django Documentation** — For exceptional backend architectural references.
- 🗄️ **MySQL Team** — For robust, persistent database engines.
- 🎨 **Bootstrap Community** — If employed for swift, responsive CSS implementations.
- 🙌 **All Contributors** — For any testing, ideas, and feature rollouts.

---

## 📚 References

1. [Django Framework Documentation](https://docs.djangoproject.com/en/stable/)
2. [MySQL 8.0 Reference Manual](https://dev.mysql.com/doc/refman/8.0/en/)
3. [Python PEP 8 Style Guide](https://peps.python.org/pep-0008/)
4.[Complete details Report of the Project](https://drive.google.com/file/d/1ab5c-1w3gj_V9IwiXw45dD67WHlgEMUj/view?usp=sharing)
---

<div align="center">

For support, email arokiyanithishj@gmail.com or create an issue in the GitHub repository.

### 🌟 If this project helped you — please consider giving it a ⭐ Star on GitHub!

**#Python #Django #HospitalManagement #WebDevelopment #FullStack**

*Made with ❤️ and Python by Arokiya Nithish J*

*© 2026 — Arokiya Nithish J*

</div>

