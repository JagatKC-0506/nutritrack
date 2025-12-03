🍼 nutritrack

A full-stack mobile application built with React Native and a Python (FastAPI/Django) backend, designed to support expecting mothers and new parents with personalized guidance, reminders, tracking tools, and educational resources.

📌 Table of Contents

Overview

Features

System Architecture

Tech Stack

System Flow

Database Schema

API Overview

UI Screens

Installation & Setup

Project Structure

Future Enhancements

License

🧩 Overview

This project is a personalized mobile assistant created for pregnant women and new parents.
The app provides real-time guidance, nutrition tips, vaccine reminders, baby feeding recommendations, daily educational tips, and growth tracking — all in one place.

✨ Features
Core Features

🔐 User Authentication

🥗 Pregnancy Nutrition Tips

🛡️ Vaccine Reminders & Tracking

👶 Baby Feeding Guide

⚠️ Safe vs Unsafe Foods Education

Medium Complexity Add-ons

📈 Baby Growth Tracker (weight, height, head size)

📅 Appointment Reminders

💡 Daily Tip Cards

📝 Notes Section

🏗️ System Architecture
React Native App  →  Backend API (FastAPI/Django)  →  SQL Database


The mobile app communicates with the backend via RESTful APIs.
The backend handles authentication, schedules, tracking data, reminders, and content delivery.

🔁 System Flow (High-Level)
User Flow

User registers/logs in

Adds pregnancy or baby details

Navigates to dashboard

Pregnancy nutrition

Baby feeding

Vaccine schedule

Safe/unsafe foods

Growth tracker

Appointments

Daily tips

Personal notes

Backend Flow

App sends requests → Backend retrieves/stores data in SQL → Returns personalized content

🗂️ Database Schema (SQL)
users
Column	Type	Description
user_id	INT PK	Unique ID
name	VARCHAR	User name
email	VARCHAR	Unique login
password_hash	VARCHAR	Hashed password
created_at	DATETIME	Registration date
pregnancy_info
Column	Type
preg_id	INT PK
user_id	INT FK
trimester	INT
due_date	DATE
baby
Column	Type
baby_id	INT PK
user_id	INT FK
name	VARCHAR
birth_date	DATE
vaccines
Column	Type
vaccine_id	INT PK
name	VARCHAR
recommended_age_weeks	INT
description	TEXT
user_vaccines

Tracks taken/upcoming vaccines.

Column	Type	Description
uv_id	INT PK	
user_id	INT FK	
baby_id	INT FK	
vaccine_id	INT FK	
status	ENUM('taken','pending')	
date_taken	DATE NULL	
nutrition_tips
Column	Type
tip_id	INT PK
trimester	INT
food	VARCHAR
category	ENUM('recommended','avoid')
reason	TEXT
baby_feeding_guide
Column	Type
guide_id	INT PK
age_months	INT
food	VARCHAR
notes	TEXT
growth_records
Column	Type
record_id	INT PK
baby_id	INT FK
date	DATE
height_cm	FLOAT
weight_kg	FLOAT
head_cm	FLOAT
appointments
Column	Type
app_id	INT PK
user_id	INT FK
date	DATETIME
description	VARCHAR
notification_sent	BOOLEAN
notes
Column	Type
note_id	INT PK
user_id	INT FK
title	VARCHAR
content	TEXT
created_at	DATETIME
🔌 API Overview
Authentication

POST /auth/register

POST /auth/login

Pregnancy

GET /pregnancy/tips/:trimester

Vaccines

GET /vaccines/list

GET /vaccines/upcoming

POST /vaccines/mark-taken

Baby Feeding

GET /feeding/guide/:age_months

Growth Tracker

POST /growth/add

GET /growth/all

Appointments

POST /appointments/add

GET /appointments/all

Daily Tips

GET /tips/daily

Notes

POST /notes/add

GET /notes/list

📱 UI Screens (React Native)

Login / Signup

Home Dashboard

Pregnancy Nutrition Tips

Baby Feeding Guide

Vaccine Tracking (Taken/Pending)

Safe vs Unsafe Foods

Growth Tracker (Graph + Records)

Appointments Calendar

Daily Tip Cards

Notes Page

⚙️ Installation & Setup
Frontend (React Native)
git clone <your-repo-link>
cd <project-folder>
npm install
npx expo start   # or react-native run-android

Backend (FastAPI Example)
cd backend
pip install -r requirements.txt
uvicorn main:app --reload

Environment Variables

Create .env:

DATABASE_URL=...
JWT_SECRET=...
EMAIL_API_KEY=...

📁 Project Structure (Recommended)
project/
│── app/
│   ├── components/
│   ├── screens/
│   ├── navigation/
│   ├── services/ (API calls)
│   └── utils/
│
│── backend/
│   ├── main.py
│   ├── routers/
│   ├── models/
│   ├── schemas/
│   └── database.py
│
└── README.md

🚀 Future Enhancements

AI-powered nutrition recommendations

Smart vaccine reminder AI

Offline mode

Multi-language support

Cloud sync

Export growth charts (PDF)

📄 License

this is suiiii.
