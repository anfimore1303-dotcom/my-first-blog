# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Django blog application following the Django Girls tutorial structure. It uses Django 5.1.12 with Python 3.10 and SQLite as the database.

**Project name**: mysite
**Main application**: blog
**Virtual environment**: `.venv/`

## Architecture

### Django Project Structure

- **mysite/**: Django project configuration
  - `settings.py`: Project settings (language: ru-ru, timezone: Asia/Bangkok, configured for PythonAnywhere deployment)
  - `urls.py`: Root URL configuration (currently only admin routes configured)
  - `wsgi.py` / `asgi.py`: WSGI/ASGI application entry points

- **blog/**: Main Django application
  - `models.py`: Contains `Post` model with author, title, text, created_date, published_date fields and a `publish()` method
  - `views.py`: Empty - views not yet implemented
  - `admin.py`: Empty - admin registration not yet configured
  - `migrations/`: Database migrations (no migrations created yet beyond initial)

### Database

- SQLite database at `db.sqlite3`
- Post model uses ForeignKey to Django's AUTH_USER_MODEL for author relationship

## Common Commands

### Running the Development Server
```bash
python manage.py runserver
```

### Database Operations
```bash
# Create migrations after model changes
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Create superuser for admin access
python manage.py createsuperuser
```

### Django Shell
```bash
# Interactive Python shell with Django context
python manage.py shell
```

### Testing
```bash
# Run all tests
python manage.py test

# Run tests for specific app
python manage.py test blog
```

### Static Files
```bash
# Collect static files for deployment
python manage.py collectstatic
```

## Development Notes

### Virtual Environment
Always activate the virtual environment before running commands:
```bash
source .venv/bin/activate
```

### Deployment Configuration
- `ALLOWED_HOSTS` includes `127.0.0.1` and `.pythonanywhere.com`
- `STATIC_ROOT` is set to `BASE_DIR / 'static'` for production static file serving
- `DEBUG = True` (should be False in production)

### Current State
- Post model is defined but admin interface not configured
- No URL routes defined for blog app yet
- No views or templates implemented yet
- Database migrations may need to be created/applied for the Post model
