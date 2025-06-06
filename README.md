# Fitness Booking API

A Flask-based REST API for managing fitness class bookings.

## Features
- List all available fitness classes
- Book a class for a client
- View bookings by client email
- Centralized error handling
- Payload validation
- Interactive API documentation with Swagger UI
- Logging to file and console

## Requirements
- Python 3.9+
- Flask
- flask-swagger-ui

Install dependencies:
```
pip install -r requirements.txt
```

## Running the Application
```
python run.py
```

The API will be available at `http://localhost:5000/`.

## API Endpoints

### List Classes
- **GET** `/classes`
- Returns a list of all fitness classes.

### Book a Class
- **POST** `/book`
- Request body (JSON):
  ```json
  {
    "class_id": 1,
    "client_name": "John Doe",
    "client_email": "john@example.com"
  }
  ```
- Returns booking details or an error message.

### Get Bookings by Email
- **GET** `/bookings?email=client@example.com`
- Returns a list of bookings for the specified email.

## API Documentation

Interactive Swagger UI is available at:
- [http://localhost:5000/apidocs](http://localhost:5000/apidocs)

The OpenAPI spec is in `swagger.yaml`.

## Project Structure
```
fitness_booking_api/
    app/
        __init__.py
        crud.py
        db.py
        models.py
        routes/
            bookings.py
            classes.py
        utils/
            errors.py
            validators.py
    fitness.db
    requirements.txt
    run.py
    seed_data.json
    swagger.yaml
```

## Logging

Logs are written to both `app.log` and the console. You can use the logger via:
```python
from app.utils.errors import setup_logger
logger = setup_logger()
logger.info("Your log message")
```

## Error Handling

All errors are returned in a consistent JSON format:
```json
{
  "message": "Error description"
}
```

## License
MIT
