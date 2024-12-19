# GeoDjango Tutorial Project

A tutorial project to gain familiarity with using GeoDjango and PostGIS to build an application with geospatial support.

## Prerequisites

- Docker
- Docker Compose

## Setup

1. **Clone the repository:**

    ```sh
    git clone https://github.com/brandonxu360/geodjango-tutorial.git
    cd geodjango-tutorial
    ```

2. **Create a `.env` file:**

    Create a `.env` file in the root directory with the following content:

    ```env
    POSTGRES_USER=admin
    POSTGRES_PW=password
    POSTGRES_DB=pg4django
    PGADMIN_MAIL=admin@example.com
    PGADMIN_PW=password
    ```

3. **Build and start the Docker containers:**

    ```sh
    docker compose up
    ```

    This command will build the Docker images and start the containers for the web application, PostgreSQL database, and pgAdmin.

4. **Apply database migrations:**

    Open a new terminal and run the following command to apply the database migrations:

    ```sh
    docker compose exec web python manage.py migrate
    ```

5. **Create a superuser:**

    Run the following command to create a superuser for the Django admin interface:

    ```sh
    docker compose exec web python manage.py createsuperuser
    ```

6. **Access the application:**

    Run the following command to start the Django development server:

    ```sh
    docker compose exec web python manage.py runserver 0.0.0.0:8000
    ```

    - The web application will be available at [http://localhost:8000](http://localhost:8000).
    - The Django admin interface will be available at [http://localhost:8000/admin](http://localhost:8000/admin).
    - pgAdmin will be available at [http://localhost:5050](http://localhost:5050).

## Notes

- The database is configured to use PostgreSQL with PostGIS for geospatial data support.
- The Docker setup includes a volume mount to sync the project files between the host and the container.
- Ensure that the `requirements.txt` file includes all necessary dependencies for the project.

For more information on Django and GeoDjango, refer to the [Django documentation](https://docs.djangoproject.com/en/5.1/) and the [GeoDjango documentation](https://docs.djangoproject.com/en/5.1/ref/contrib/gis/).