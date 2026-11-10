# Careers Website

A careers website modelled on Jovian's, built with **Flask** and a **MySQL** database. Visitors can browse open jobs, read a job's details and apply online. Built while following Jovian's "Build a Python Web App" course, and hosted on Replit.

## Features

- **Home page:** lists all open jobs from the database
- **Job page:** shows the job's location, salary, responsibilities and requirements
- **Application form:** name, email, LinkedIn, education, work experience and résumé link, saved to the `applications` table
- **JSON API:** `/api/jobs` (all jobs) and `/api/job/<id>` (one job)

## Routes

| Route | Method | What it does |
|---|---|---|
| `/` | GET | Home page with the list of jobs |
| `/job/<id>` | GET | Job details page (404 if the job doesn't exist) |
| `/job/<id>/apply` | POST | Saves an application and shows a confirmation page |
| `/api/jobs` | GET | All jobs as JSON |
| `/api/job/<id>` | GET | One job as JSON |

## Project structure

```
app.py          # Flask routes
database.py     # SQLAlchemy queries (load jobs, load one job, save an application)
templates/      # Jinja2 pages: home, job page, application form, confirmation, nav, footer
static/         # Logo and banner images
```

## Database

The app expects a MySQL database with two tables:

- `jobs`: `id`, `title`, `location`, `salary`, `currency`, `responsibilities`, `requirements`
- `applications`: `id`, `job_id`, `full_name`, `email`, `linkedin_url`, `education`, `work_experience`, `resume_url`

## How to run

1. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

2. Set the database connection string as an environment variable (never commit it):

   ```bash
   export DB_CONNECTION_STRING="mysql+pymysql://USER:PASSWORD@HOST/DATABASE?charset=utf8mb4"
   ```

   `database.py` connects with SSL using the certificate at `/etc/ssl/cert.pem` (the Linux/Replit location); change it if your system keeps certificates elsewhere.

3. Start the app:

   ```bash
   python app.py
   ```

   Then open <http://localhost:5000>.

## Technologies

Python, Flask, SQLAlchemy 2, PyMySQL, MySQL, Jinja2, Bootstrap, Replit
