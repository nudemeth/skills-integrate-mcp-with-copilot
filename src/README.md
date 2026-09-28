# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teacher login for managing registrations
- Teacher-only signup and unregister operations
- Public viewing of activities and participants

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/auth/login`                                                      | Log in as a teacher                                                 |
| POST   | `/auth/logout`                                                     | Log out the current teacher                                         |
| GET    | `/auth/me`                                                         | Get the current login state                                         |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up a student as an authenticated teacher                       |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Remove a student as an authenticated teacher                     |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.

### Local teacher account

The development account is stored in `teachers.json`:

- Username: `teacher`
- Password: `change-me`

Set `SESSION_SECRET` in production to replace the development session secret.
