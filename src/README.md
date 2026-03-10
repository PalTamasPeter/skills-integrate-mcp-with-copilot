# Mergington High School Activities API

A super simple FastAPI application that allows students to view extracurricular activities and teachers to manage registrations.

## Features

- View all available extracurricular activities
- Teacher login and logout flow
- Teacher-only sign up and unregister operations

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
| GET    | `/activities`                                                     | Get all activities with details and participant lists               |
| POST   | `/auth/login?username=teacher.alvarez&password=classroom123`     | Log in as teacher and get an auth token                             |
| POST   | `/auth/logout?token={token}`                                     | Log out the active teacher session                                  |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu&token={token}` | Sign up a student for an activity (teacher only)                    |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu&token={token}` | Unregister a student from an activity (teacher only)                |

## Teacher Credentials

Teacher usernames and passwords are stored in `teachers.json` and validated by the backend.

Example entries:

- `teacher.alvarez` / `classroom123`
- `teacher.khan` / `robotics456`

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
