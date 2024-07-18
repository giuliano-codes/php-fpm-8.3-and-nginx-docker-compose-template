# How to run:

1. Clone the project repository;
2. Navigate to the cloned project directory.
3. Build and start the Docker containers using Docker Compose: `docker compose up --build`
4. Once the containers are up and running, install composer packages running: `docker exec -it -u 1000 php-nginx-template-php composer install`
5. Access the project at http://localhost:8000

## Additional Information

**Customizing Port Number**

If you need to change the port number to access the application, modify the `ports` section in the `docker-compose.yml` file:
```
...
ports:
    - "8000:80"
...
```
**Using Composer**

The project includes Composer for package management and the user composer to run the commands and avoid problems with permissions. You can execute Composer commands inside the PHP container.
  1. Enter the PHP container shell: `docker exec -it -u 1000 php-nginx-template-php /bin/bash`;
  2. Once inside the container, you can run Composer commands as needed.
