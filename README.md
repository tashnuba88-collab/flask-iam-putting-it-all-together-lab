Flask: Putting It All Together Lab

A full-stack backend application built with Flask, Flask-SQLAlchemy, Flask-RESTful, and Marshmallow. This project demonstrates password hashing with Bcrypt, session-based user authentication, database model validation, and serialized API endpoints designed to serve a recipe-sharing platform.

🛠 Tech Stack & Tools

Framework: Flask & Flask-RESTful

ORM & Database: Flask-SQLAlchemy (SQLite)

Authentication & Hashing: Flask-Bcrypt & HTTP Sessions

Serialization & Validation: Marshmallow

Testing: Pytest

📁 Project Structure

├── server/
│   ├── app.py           # RESTful API routes & HTTP request handlers
│   ├── config.py        # App, database, and Bcrypt configuration
│   ├── models.py        # SQLAlchemy models and Marshmallow schemas
│   ├── seed.py          # Database seeding script
│   └── testing/         # Pytest test suite & fixtures
├── Pipfile              # Pipenv dependencies
└── README.md            # Project documentation

 

 
 Features & Functionality

1. User Authentication & Authorization

Password Hashing: Uses Flask-Bcrypt via hybrid_property getters/setters to keep raw passwords out of the database.

Session Persistence: Manages user session state using Flask's session object across authentication routes (/signup, /login, /logout, /check_session).

2. Database Models & Schema Validation

User Model: Stores user credentials and profile information (username, _password_hash, image_url, bio). Features custom @validates logic to enforce non-empty usernames.

Recipe Model: Stores recipe details (title, instructions, minutes_to_complete) associated with a user_id. Validates that instructions are at least 50 characters long.

Serialization: Employs Marshmallow UserSchema and RecipeSchema to output structured JSON data and handle field restrictions.




Running the Test Suite

To run all unit and integration tests, execute the following command in your terminal:

pipenv run pytest




Key API Endpoints Test CoverageMethodEndpointDescriptionAuth RequiredPOST/signupRegisters a new user and sets sessionNoPOST/loginAuthenticates existing user credentialsNoDELETE/logoutClears current user sessionYesGET/check_sessionFetches logged-in user profileYesGET/recipesLists all published recipesYesPOST/recipesCreates a new recipe for active userYes



Setup & InstallationInstall dependencies:pipenv install
pipenv shell
Seed the database:python server/seed.py
Start the server:python server/app.py
