# User Authentication API with Flask

This project implements a **User Authentication System** using Flask, SQLAlchemy, and SQLite. It includes features like user signup, login, and role-based access management.

---

## Features
- **User Signup**: Register new users with a username, email, password, and role.
- **User Login**: Authenticate users with email and password.
- **Role-Based Access**: Assign roles to users (e.g., Admin, User).
- **Database Management**: Use SQLite as the database backend.

---

## Technologies Used
- **Python** (Flask Framework)
- **Flask-SQLAlchemy**: For database ORM.
- **SQLite**: Lightweight database for development.
- **Flask-Migrate**: For database migrations.

---

## Setup and Installation
Follow the steps below to run the project locally:

### Prerequisites
Make sure you have **Python 3.8+** installed.

### 1. Clone the Repository
```bash
git clone https://github.com/aaryan4985/group-study-platform.git
cd your-repo
```

### 2. Create a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Initialize the Database
Use Flask-Migrate to set up the database schema.

```bash
flask db init
flask db migrate -m "Initial migration."
flask db upgrade
```

### 5. Run the Application
Start the development server:
```bash
flask run
```
The application will run on `http://127.0.0.1:5000/`.

---

## Project Structure
```
/your-repo
|-- app.py               # Main Flask application file
|-- models.py            # Database models
|-- routes.py            # API endpoints
|-- migrations/          # Database migration files
|-- users.db             # SQLite database file
|-- requirements.txt     # Project dependencies
|-- README.md            # Documentation
```

---

## API Endpoints

### 1. User Signup
**Endpoint**: `/signup`  
**Method**: `POST`  
**Request Body**:
```json
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "securepassword",
  "role": "user"
}
```
**Response**:
```json
{
  "message": "User created successfully!"
}
```

### 2. User Login
**Endpoint**: `/login`  
**Method**: `POST`  
**Request Body**:
```json
{
  "email": "john@example.com",
  "password": "securepassword"
}
```
**Response**:
```json
{
  "message": "Login successful!",
  "token": "JWT-TOKEN"
}
```

---

## Database Schema
**User Table**:
| Column       | Type          | Description               |
|--------------|---------------|---------------------------|
| id           | Integer       | Primary Key               |
| username     | String(50)    | User's unique name        |
| email        | String(120)   | User's unique email       |
| password     | String(128)   | Hashed password           |
| role         | String(20)    | Role (e.g., 'admin/user') |

---

## Troubleshooting
### Error: `no such column: user.role`
- Run migrations using Flask-Migrate to ensure your database schema is up-to-date:
  ```bash
  flask db migrate -m "Add role column"
  flask db upgrade
  ```

---

## Contributing
Feel free to fork this repository and submit pull requests. Contributions are always welcome!

---

## License
This project is licensed under the MIT License.
