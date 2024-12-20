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

    - The web application will be available at [http://localhost:8000](http://localhost:8000).
    - The Django admin interface will be available at [http://localhost:8000/admin](http://localhost:8000/admin).
    - pgAdmin will be available at [http://localhost:5050](http://localhost:5050).

## Development Options

### Using Dev Container in VS Code (Recommended)

1. **Prerequisites:**
   - Visual Studio Code
   - Docker Desktop
   - Dev Containers extension for VS Code

2. **Open in Container:**
   - Open the project folder in VS Code
   - When prompted, click "Reopen in Container" or use Command Palette (F1) and select "Dev Containers: Reopen in Container"
   - VS Code will build and start the development container using the configuration in [.devcontainer/devcontainer.json](.devcontainer/devcontainer.json)

3. **Development Environment:**
   - The container provides a complete development environment with:
     - Python 3 with Django
     - GDAL, GEOS, and PROJ for GeoDjango
     - Direct access to PostgreSQL/PostGIS database
   - All project files are synced via the volume mount in [compose.yml](compose.yml)
   - Python extensions and debugging tools work seamlessly inside the container

4. **Using the Terminal:**
   - VS Code's integrated terminal runs inside the container
   - All Django management commands can be run directly:
     ```sh
     python manage.py migrate
     python manage.py createsuperuser
     python manage.py runserver 0.0.0.0:8000
     ```


## Notes

- The database is configured to use PostgreSQL with PostGIS for geospatial data support.
- The Docker setup includes a volume mount to sync the project files between the host and the container.
- Ensure that the `requirements.txt` file includes all necessary dependencies for the project.

For more information on Django and GeoDjango, refer to the [Django documentation](https://docs.djangoproject.com/en/5.1/) and the [GeoDjango documentation](https://docs.djangoproject.com/en/5.1/ref/contrib/gis/).