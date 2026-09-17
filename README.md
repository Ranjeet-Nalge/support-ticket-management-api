# Support Ticket Management System

A backend REST API built using Django and Django REST Framework for managing support tickets.

## Features

* Create, retrieve, update and delete support tickets
* JWT authentication
* User-based ticket reporting and assignment
* Ticket status management
* Ticket priority management
* Ticket date tracking
* Filtering by status and priority
* Search by ticket title
* Ordering support
* Pagination
* PostgreSQL database
* Docker support
* Docker Compose support
* Django Admin interface

## Tech Stack

* Python
* Django
* Django REST Framework
* PostgreSQL
* Simple JWT
* django-filter
* Docker
* Docker Compose
* Postman

## Project Structure

```
support_ticket_management_system/
│
├── config/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── tickets/
│   ├── migrations/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── serializers.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
│
├── manage.py
├── Dockerfile
├── docker-compose.yml
├── requirement.txt
├── .env.example
├── .gitignore
└── README.md
```

## Ticket Status

The system supports the following ticket statuses:

* Open
* In Progress
* Closed

## Ticket Priority

The system supports the following priority levels:

* Low
* Medium
* High
* Critical

## Ticket Fields

Each ticket contains information such as:

* Title
* Description
* Status
* Priority
* Reported By
* Assigned To
* Created At
* Updated At

`Reported By` identifies the user who reported the ticket.

`Assigned To` identifies the user assigned to handle the ticket.

## API Endpoints

### Authentication

#### Obtain JWT Token

```
POST /api/token/
```

Used to obtain an access token and refresh token using valid user credentials.

#### Refresh JWT Token

```
POST /api/token/refresh/
```

Used to obtain a new access token using a refresh token.

### Tickets

#### List Tickets

```
GET /api/tickets/
```

Returns the available support tickets.

#### Create Ticket

```
POST /api/tickets/
```

Creates a new support ticket.

Example request body:

```
{
    "title": "Login issue",
    "description": "Unable to login to the application",
    "status": "Open",
    "priority": "High",
    "reported_by": 1,
    "assigned_to": 2
}
```

#### Retrieve Ticket

```
GET /api/tickets/<id>/
```

Returns a specific ticket using its ID.

#### Update Ticket

```
PUT /api/tickets/<id>/
```

Updates an existing ticket.

#### Delete Ticket

```
DELETE /api/tickets/<id>/
```

Deletes an existing ticket.

## Filtering

Tickets can be filtered using status and priority.

### Filter by Status

```
GET /api/tickets/?status=Open
```

### Filter by Priority

```
GET /api/tickets/?priority=High
```

## Search

Tickets can be searched using the ticket title.

Example:

```
GET /api/tickets/?search=login
```

## Ordering

Tickets can be ordered using supported ordering fields.

Example:

```
GET /api/tickets/?ordering=-created_at
```

The `-` prefix is used for descending order.

## Pagination

The API supports pagination for ticket results.

Example:

```
GET /api/tickets/?page=2
```

## Authentication

The API uses JWT authentication.

First obtain an access token:

```
POST /api/token/
```

Then include the access token in the request header:

```
Authorization: Bearer <access_token>
```

Protected API endpoints require authentication.

## Serializer

The project uses Django REST Framework's `ModelSerializer` to:

* Convert Ticket model data into JSON-compatible API response data
* Validate incoming request data
* Convert validated request data into model objects

## Database

The project uses PostgreSQL for data storage.

Database configuration is provided through environment variables.

Example:

```
DB_NAME=ticket_db
DB_USER=postgres
DB_PASSWORD=your-password
DB_HOST=localhost
DB_PORT=5432
```

## Environment Variables

Create a `.env` file using `.env.example` as a reference.

Example:

```
SECRET_KEY=your-secret-key
DEBUG=True

DB_NAME=ticket_db
DB_USER=postgres
DB_PASSWORD=your-password
DB_HOST=localhost
DB_PORT=5432
```

Do not commit the actual `.env` file or sensitive credentials to the repository.

## Django Admin

The project includes Django Admin for managing and viewing tickets.

The admin interface provides:

* Ticket listing
* Status filtering
* Priority filtering
* Ticket title search
* Ticket information display

The admin interface is available at:

```
/admin/
```

## Installation

Clone the repository and navigate to the project directory.

Install the required dependencies:

```
pip install -r requirement.txt
```

## Database Migration

Run Django migrations:

```
python manage.py migrate
```

## Run the Development Server

Start the Django development server:

```
python manage.py runserver
```

The API will be available at:

```
http://127.0.0.1:8000/
```

## Docker

The project includes Docker and Docker Compose configuration.

Build and start the containers:

```
docker compose up --build
```

Stop the containers:

```
docker compose down
```

## API Testing

The API can be tested using Postman.

Typical testing flow:

1. Obtain a JWT access token using `/api/token/`.
2. Use the access token as a Bearer token.
3. Create a support ticket using `POST /api/tickets/`.
4. Retrieve tickets using `GET /api/tickets/`.
5. Retrieve, update or delete a ticket using its ID.
6. Test filtering by status and priority.
7. Test ticket search.
8. Test ordering and pagination.
9. Verify authentication on protected endpoints.

## Project Purpose

This project was built to practice backend REST API development using Django and Django REST Framework.

The project demonstrates:

* Django models and ORM
* Django REST Framework serializers
* Class-based API views
* CRUD operations
* JWT authentication
* Permissions
* PostgreSQL database integration
* Filtering
* Search
* Ordering
* Pagination
* Django Admin
* Docker and Docker Compose

## Author
` Ranjeet Tanajirao Nalge `