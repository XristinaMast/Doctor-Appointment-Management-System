# Doctor Appointment Management System

## Table of Contents
1. [Introduction](#introduction)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Project Structure](#project-structure)
5. [Prerequisites](#prerequisites)
6. [How to Run the System](#how-to-run-the-system)
7. [API Endpoints](#api-endpoints)
8. [How to Use the System (Examples)](#how-to-use-the-system-examples)

## Introduction

The **Doctor Appointment Management System** is a web application designed to facilitate online scheduling and management of doctor appointments for patients and doctors. Patients can view available doctors, book appointments, and manage their bookings. Doctors can manage their schedules, approve or reject appointment requests, and view their daily appointments.

This project is built using **Flask** for the web framework, **MongoDB** for data storage, and **Docker** to containerize the application for easy deployment.

## Features

### Patient Features:
- User registration and login
- View a list of available doctors and their specialties
- Book appointments by selecting a doctor and time slot
- View and manage booked appointments
- Cancel appointments

### Doctor Features:
- Doctor login
- Manage appointment requests (approve/reject appointments)
- View daily appointment schedules
- Manage availability and schedule

### Other Features:
- Secure password encryption and session management
- Persistent data storage using MongoDB
- Role-based access for patients and doctors

## Technologies Used

- **Flask**: Web framework for handling HTTP requests and rendering templates.
- **MongoDB**: Database to store user, doctor, and appointment data.
- **Flask-PyMongo**: To interact with MongoDB from Flask.
- **Docker**: Containerization for easy deployment.
- **Python 3.x**: Backend logic development.
- **Werkzeug**: Provides password hashing for secure user authentication.

## Project Structure

```
Doctor-Appointment-Management-System/
│
├── app.py                 # Main application file with API routes
├── Dockerfile             # Docker instructions for building the image
├── docker-compose.yml     # Docker Compose file to set up multiple containers
├── requirements.txt       # Python dependencies for the project
├── static/                # Static files like CSS, images
├── templates/             # HTML templates for rendering pages
├── config.py              # Configuration file for database and app settings
└── README.md              # This readme file
```

## Prerequisites

Make sure you have the following installed:

- **Python 3.8+**
- **Docker**
- **Docker Compose**

### Python Libraries

To install the necessary Python libraries if you're not using Docker:

```bash
pip install -r requirements.txt
```

### Docker

To install Docker, follow the instructions provided on the [official Docker website](https://www.docker.com/).

## How to Run the System

### Clone the Repository

```bash
git clone https://github.com/XristinaMast/Doctor-Appointment-Management-System.git
cd Doctor-Appointment-Management-System
```

### Running with Docker

1. Build and run the Docker containers:

```bash
docker-compose up --build
```

2. Access the application in your web browser:

```bash
http://localhost:5000
```

3. To stop the containers, use `Ctrl + C` and run:

```bash
docker-compose down
```

### Running without Docker

1. Install Python dependencies:

```bash
pip install -r requirements.txt
```

2. Start the Flask application:

```bash
python app.py
```

3. Open your browser and navigate to:

```bash
http://localhost:5000
```

## API Endpoints

### Patient Endpoints

- **Register User (Patient)**:
  - `POST /register`
  - Example request:
    ```bash
    curl -X POST http://localhost:5000/register -H "Content-Type: application/json" -d '{"username": "john_doe", "password": "password123"}'
    ```

- **Login User**:
  - `POST /login`
  - Example request:
    ```bash
    curl -X POST http://localhost:5000/login -H "Content-Type: application/json" -d '{"username": "john_doe", "password": "password123"}'
    ```

- **View Available Doctors**:
  - `GET /doctors`
  - Example request:
    ```bash
    curl -X GET http://localhost:5000/doctors
    ```

- **Book Appointment**:
  - `POST /appointments/book`
  - Example request:
    ```bash
    curl -X POST http://localhost:5000/appointments/book -H "Content-Type: application/json" -d '{"doctor_id": "12345", "time": "10:00 AM", "date": "2024-12-25"}'
    ```

- **Cancel Appointment**:
  - `DELETE /appointments/cancel/<appointment_id>`
  - Example request:
    ```bash
    curl -X DELETE http://localhost:5000/appointments/cancel/67890
    ```

### Doctor Endpoints

- **Login Doctor**:
  - `POST /doctor/login`
  - Example request:
    ```bash
    curl -X POST http://localhost:5000/doctor/login -H "Content-Type: application/json" -d '{"username": "dr_smith", "password": "password456"}'
    ```

- **Approve Appointment**:
  - `POST /appointments/approve/<appointment_id>`
  - Example request:
    ```bash
    curl -X POST http://localhost:5000/appointments/approve/67890
    ```

- **Reject Appointment**:
  - `POST /appointments/reject/<appointment_id>`
  - Example request:
    ```bash
    curl -X POST http://localhost:5000/appointments/reject/67890
    ```

- **View Daily Schedule**:
  - `GET /doctor/schedule`
  - Example request:
    ```bash
    curl -X GET http://localhost:5000/doctor/schedule
    ```

## How to Use the System (Examples)

### 1. **User Registration and Login**
   - **Register**: Patients can register by sending a `POST` request to the `/register` endpoint.
   - **Login**: Patients and doctors can log in using the `/login` and `/doctor/login` endpoints, respectively.

### 2. **Booking Appointments**
   - **Search for Doctors**: Patients can view a list of available doctors based on specialty and location.
   - **Book Appointment**: After selecting a doctor, the patient can book an appointment by specifying a date and time.
   - **Cancel Appointment**: Patients can cancel their appointments via the `/appointments/cancel` endpoint.

### 3. **Managing Appointments (Doctors)**
   - **Approve/Reject Appointments**: Doctors can approve or reject appointment requests via the `/appointments/approve` or `/appointments/reject` endpoints.
   - **View Schedule**: Doctors can view their schedule to see upcoming appointments for the day.
