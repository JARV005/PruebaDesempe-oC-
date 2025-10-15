# 🏥 Hospital Management System

A comprehensive web application for managing patients, doctors, and medical appointments in a hospital environment. Built with ASP.NET Core MVC, Entity Framework, and MySQL.

# By: 
- Johan Alexander Rivera Vasquez
- C#
- johanalexanderriveravasquez@gmail.com
- 1025644849
  

## 📋 Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Troubleshooting](#troubleshooting)

## ✨ Features

### Core Modules
- **Patients Management**: Complete CRUD operations with unique identification
- **Doctors Management**: Complete CRUD operations with unique license numbers
- **Appointments Management**: Schedule, confirm, and track medical appointments

### Advanced Features
- **Appointment Status System**: Programmed → Confirmed → Attended/Cancelled
- **Working Hours Validation**: Prevents scheduling outside doctor's working hours
- **Email Notifications**: Automatic confirmation emails with professional HTML templates
- **Specialized Filters**: Filter doctors by specialty, view appointments by patient/doctor
- **Unique Constraints**: Prevents duplicate patients/doctors
- **Professional UI**: Bootstrap 5 responsive design

### Email System
- Automatic appointment confirmation emails
- Complete email history with status tracking
- Professional HTML email templates
- Robust error handling

## 🛠 Prerequisites

### Required Software
- **.NET 8.0 SDK** or later
- **MySQL Server** 8.0 or later


### Recommended Development Tools
- **JetBrains Raider**
- **MySQL Workbench** or **DBeaver**

## 📥 Installation

### 1. Clone the Repository
git clone https://github.com/JARV005/PruebaDesempe-oC-.git
cd PruebaDesempeñoC#
### 2. Restore Dependencies
dotnet restore
### 3. Install Required Packages
# Entity Framework with MySQL
dotnet add package Pomelo.EntityFrameworkCore.MySql --version 8.0.0
dotnet add package Microsoft.EntityFrameworkCore.Design --version 8.0.0
dotnet add package Microsoft.EntityFrameworkCore.Tools --version 8.0.0

# Email System
dotnet add package MailKit
dotnet add package MimeKit


### ⚙️ Configuration
1. Database Connection
Update appsettings.json with your MySQL credentials:


{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Port=3306;Database=HospitalDB;Uid=your_username;Pwd=your_password;"
  }
}
2. Email Configuration 
Add email settings to appsettings.json:

{
  "EmailSettings": {
    "SmtpServer": "smtp.gmail.com",
    "Port": 587,
    "Username": "your_email@gmail.com",
    "Password": "your_app_password",
    "FromEmail": "your_email@gmail.com",
    "FromName": "Hospital Management System"
  }
}
Gmail Setup Instructions:
Enable 2-Step Verification in your Google Account

Generate an App Password:

Go to Google App Passwords

Select "Mail" as app

Select "Other" as device, name it "Hospital System"

Copy the 16-character generated password

Use this app password in the configuration

# 🗄 Database Setup
1. Create Database Manually
sql
CREATE DATABASE HospitalDB;
2. Apply Migrations
```bash
# Create initial migration
dotnet ef migrations add InitialCreate

# Apply migration to database
dotnet ef database update

# For additional features (if needed)
dotnet ef migrations Add AppointmentStatus
dotnet ef migrations Add EmailSystem
dotnet ef database update

```
3. Verify Database
Check that the following tables were created:

Patients

Doctors

Appointments

EmailHistories

🚀 Running the Application

```bash
dotnet watch run
```
Application will be available at: https://localhost:5235 or http://localhost:7283

# 💻 Usage
Getting Started
Access the Application: Open your browser and go to https://localhost:5235

Navigate the System: Use the top navigation menu to access different modules

Managing Patients
Click "Pacientes" in the navigation menu

Click "Registrar nuevo paciente" to add a patient

Fill in the required information (Name, Identification, Birth Date, Address, Phone, Email)

Save the patient - the system will prevent duplicate identifications

Managing Doctors
Click "Medicos" in the navigation menu

Click "Registar nuevo medico" to add a doctor

Fill in the required information including working hours and days

Save the doctor - the system will prevent duplicate license numbers

Scheduling Appointments
Click "Citas" in the navigation menu

Click "Programar cita medica"

Select a patient and doctor

Choose a date and time - the system will validate:

Future dates only

Doctor's working hours

No scheduling conflicts

The system will automatically send a confirmation email

Managing Appointment Status
View appointment details by clicking "Details"

Use the action buttons to change status:

Confirm → Changes from "Programmed" to "Confirmed"

Mark as Attended → Changes from "Confirmed" to "Attended"

Cancel → Cancels the appointment


### 📁 Project Structure
HospitalManagementSystem/
├── Controllers/
│   ├── PatientsController.cs
│   ├── DoctorsController.cs
│   ├── AppointmentsController.cs
│   └── EmailHistoryController.cs
├── Models/
│   ├── Patient.cs
│   ├── Doctor.cs
│   ├── Appointment.cs
│   └── EmailHistory.cs
├── Views/
│   ├── Patients/
│   ├── Doctors/
│   ├── Appointments/
│   └── EmailHistory/
├── Data/
│   └── HospitalContext.cs
├── Services/
│   └── EmailService.cs
├── Migrations/
├── wwwroot/
│   └── css/
│       └── site.css
├── Program.cs
└── appsettings.json

# 🔌 API Endpoints
Patients
GET /Patients - List all patients

GET /Patients/Create - Show create form

POST /Patients/Create - Create new patient

GET /Patients/Edit/{id} - Show edit form

POST /Patients/Edit/{id} - Update patient

GET /Patients/Details/{id} - Show patient details

GET /Patients/Delete/{id} - Show delete confirmation

POST /Patients/Delete/{id} - Delete patient

Doctors
GET /Doctors - List all doctors (with specialty filter)

GET /Doctors/Create - Show create form

POST /Doctors/Create - Create new doctor

GET /Doctors/Edit/{id} - Show edit form

POST /Doctors/Edit/{id} - Update doctor

GET /Doctors/Details/{id} - Show doctor details

Appointments
GET /Appointments - List all appointments

GET /Appointments/Create - Show create form

POST /Appointments/Create - Create new appointment

GET /Appointments/Details/{id} - Show appointment details

POST /Appointments/UpdateStatus - Update appointment status

GET /Appointments/ByPatient/{id} - List appointments by patient

GET /Appointments/ByDoctor/{id} - List appointments by doctor

# 🐛 Troubleshooting
Common Issues
Database Connection Errors
```bash
# Check MySQL service is running
sudo systemctl status mysql

# Start MySQL if not running
sudo systemctl start mysql
```
Migration Errors
```bash
# Remove and recreate migrations
dotnet ef migrations remove
dotnet ef migrations add InitialCreate
dotnet ef database update
```

Email Sending Issues
1. Verify Gmail credentials in appsettings.json

2. Ensure 2-Step Verification is enabled

3. Use App Password, not regular password
Email Sending Issues
Verify Gmail credentials in appsettings.json

Ensure 2-Step Verification is enabled

Use App Password, not regular password

Check email history for specific error messages

Build Errors
4. Check email history for specific error messages

Build Errors
```bash
# Clean and rebuild
dotnet clean
dotnet build
```


# Images 

<img width="1855" height="960" alt="image" src="https://github.com/user-attachments/assets/64b2b7ef-2ccc-4148-88e1-9590c464a472" />



