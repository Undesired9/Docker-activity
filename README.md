This project is a Dockerized Node.js and PostgreSQL application that serves as a simple Address Book API. It allows users to create, retrieve, and delete person records from a PostgreSQL database using Express routes. The project is designed to demonstrate container-based development and testing using Docker Compose.

The application is built with Node.js and Express for the backend, PostgreSQL for database management, and Sequelize as the Object Relational Mapper (ORM). Jest is used for running automated tests. Docker and Docker Compose are used to containerize the application and database, making it easy to set up and run in any environment.

To get started, make sure Docker Desktop and Git are installed on your system. Clone the repository from GitHub and navigate into the “docker activity” folder using the command line. Then, build and start the services using the command:
docker compose up -d --build.
This will create and start two containers — one for PostgreSQL and one for the Node.js application. Once running, the API will be available at http://localhost:3000.

The main routes include:

PUT /persons to create a new person entry

GET /persons/all to retrieve all person records

DELETE /persons/:id to delete a person by ID

You can test these endpoints using cURL or Postman. For example, to create a new person, use:
curl -X PUT -H "Content-Type: application/json" -d "{\"firstName\":\"Bobbie\",\"lastName\":\"Draper\"}" http://localhost:3000/persons

To run automated tests, execute:
docker compose run --rm addressbook npm test
This runs the Jest tests in a temporary container and removes it afterward.

To stop and remove containers, networks, and volumes, use:
docker compose down --volumes --remove-orphans.

The main configuration variables used by the application include database host, port, username, password, and schema. These are defined in the docker-compose.yml file and are automatically used by Sequelize to connect the Node.js application to PostgreSQL.

The project structure includes the Express app file (app.js), route definitions in the routes folder, database models in the models folder, and configuration files such as the Dockerfile and docker-compose.yml. Together, they define how the application and database interact within their respective containers.

This project was developed for academic purposes by Muhammad Hashir and is meant to provide hands-on experience with containerized application development using Node.js, PostgreSQL, and Docker.
