# fast-api-sample
Example using Fast API server (with REST) and PostgreSQL

# Introduction
This is a sample project to show how to use Fast API server (with REST) and PostgreSQL based on a tutorial

# Techstack
- SQLAlchemy for ORM, Alembic for data migration
- JWT authentication
- FastAPI with REST API
- 

# Additional things to do prior to starting

- Adding an .env file with the following variables:

  **PostgreSQL server parameters**
  - DATABASE_PORT=6500
  - POSTGRES_PASSWORD=password123
  - POSTGRES_USER=postgres
  - POSTGRES_DB=fastapi
  - POSTGRES_HOST=postgres
  - POSTGRES_HOSTNAME=127.0.0.1
  - ACCESS_TOKEN_EXPIRES_IN=15
  - REFRESH_TOKEN_EXPIRES_IN=60

  - CLIENT_ORIGIN=http://localhost:3000
  - VERIFICATION_SECRET=my-email-verification-secret

  **create an account for email testing here, add params to env file: [Link](//mailtrap.io/)**
  - EMAIL_HOST=smtp.mailtrap.io
  - EMAIL_PORT=587
  - EMAIL_USERNAME=xxxxxxx
  - EMAIL_PASSWORD=xxxxxxx
  - EMAIL_FROM= admin(at)admin.com

  **generate JWT public and private key here: [Link]('https://travistidwell.com/jsencrypt/demo/')**
    - JWT_ALGORITHM=RS256
    - JWT_PRIVATE_KEY=
    - JWT_PUBLIC_KEY=

- Install UUID for OSSP in the postgreSQL database:
  - Login into docker image with postgreSQL image installed
  - Install UUID OSSP
  - login with username and db to the postgre database
  - select * from pg_available_extensions;
  - check whether UUID OSSP version is installed
  - CREATE EXTENSION IF NOT EXISTS "uuid-ossp"

- How to get data migration tool Alembic working:
1. Init alembic data migration with `alembic init alembic`
2. Go to the env.py file and make sure the model with metadata is imported and also change the location of the migration folder
3. `alembic revision --autogenerate -m "creat users table"` to create the migration file
4. `alembic upgrade head` to apply the migration

# How to run guide
- Spin up Docker container with PostgreSQL database if you have not done yet
  - `docker-compose up -d`
- Create virtual environment using `pipenv shell` and activate it
- In the virtual environment install dependencies `pipenv install`
- Run `uvicorn app.main:app --host localhost --port 8000 --reload` to start the REST API server


# Learnings
- [SQL Alchemy - declarative mapping](https://docs.sqlalchemy.org/en/14/orm/mapping_styles.html#orm-declarative-mapping)
- [Alembic Data migration](https://alembic.sqlalchemy.org/en/latest/tutorial.html)
- [Pydantic Data validation](https://pydantic-docs.helpmanual.io/usage/models/)
- [Postman - Testing REST API endpoints](https://www.postman.com/)
- [pgadmin - PostgreSQL GUI](https://www.pgadmin.org/)
- [JWT authentication](https://indominusbyte.github.io/fastapi-jwt-auth/)