# Cybersecurity Incident Management System  

A **Flask-based web application** for tracking and managing cybersecurity incidents with user authentication, PostgreSQL database integration, and secure password handling.  

## Features  
✔ **User Authentication** – Register, login, and logout.  
✔ **Incident Management** – Report, resolve, or delete incidents with severity levels.  
✔ **Database Integration** – PostgreSQL for secure data storage.  
✔ **Security** – Password hashing (Werkzeug) & environment variables (`.env`).  
✔ **User Roles** – Supports different access levels (e.g., admin, analyst).  

## Technologies  
- **Backend**: Python, Flask  
- **Database**: PostgreSQL (via `psycopg2`)  
- **Security**: Werkzeug password hashing, `.env` for secrets  
- **Frontend**: HTML, CSS (Bootstrap optional)  

## Setup  
1. **Install dependencies**:  
   ```sh
   pip install flask psycopg2-binary python-dotenv

2. **Configure .env file**:
   DB_HOST=localhost  
DB_PORT=5432  
DB_NAME=Cybersecurity_db  
DB_USER=postgres  
DB_PASSWORD=root
SECRET_KEY=your_secret_key

3.**Run the app**:
python app.py

4.**Database Setup**:
Ensure PostgreSQL is running and create the required tables (users and incidents). Example schema:
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    full_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    role VARCHAR(50) NOT NULL,
    password_hash VARCHAR(200) NOT NULL
);

CREATE TABLE incidents (
    id SERIAL PRIMARY KEY,
    title VARCHAR(100) NOT NULL,
    description TEXT,
    severity VARCHAR(50) NOT NULL,
    status VARCHAR(50) DEFAULT 'Open',
    reporter_id INTEGER REFERENCES users(id)
);
