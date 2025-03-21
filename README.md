# PSQL Docker Setup
This repository contains a Docker Compose configuration for setting up a MySQL database container with environment variables stored in a `.env` file. The database persists data using Docker volumes to ensure that data remains intact even after container recreation.
## Prerequisites
Ensure you have the following installed on your system:
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
## Getting Started
### 1. Clone the Repository
```sh
git clone <repository-url>
cd <repository-directory>
```
### 2. Create an `.env` File
Create a `.env` file in the project root directory and add the following environment variables:
```
DB_NAME=mydatabase
DB_USER=myuser
DB_PASSWORD=mypassword
DB_PORT=portnumber
```
Replace `mypassword`, `myuser`, `portnumber`, and `mydatabase` with your desired values.
### 3. Start the Database Container
Run the following command to start the MySQL container:
```sh
docker-compose up -d
```
This command will start the container in detached mode.
### 4. Verify the Container
To check if the MySQL container is running, use:
```sh
docker ps
```
To view logs, run:
```sh
docker-compose logs db
```
### 5. Connect to MySQL Database
#### Using MySQL CLI:
```sh
docker exec -it my_postgres_db psql -U myuser -d mydatabase
```
Replace `<container_id>` with the actual container ID, which can be found using `docker ps`.
#### Using DBeaver or Any Database Client:
- Host: `localhost`
- Port: `5432`
- User: `$MYSQL_USER` (as per `.env` file)
- Password: `$MYSQL_PASSWORD` (as per `.env` file)
- Database: `$MYSQL_DATABASE`
### 6. Stop and Remove the Container
To stop the MySQL container, use:
```sh
docker-compose down
```
This will remove the container but keep the data in the volume.
### 7. Remove Persistent Data (Optional)
If you want to remove all persistent data, run:
```sh
docker volume rm <volume_name>
```
Replace `<volume_name>` with `db_data` if using the provided `docker-compose.yml`.
## Contribution Guidelines
To contribute:
1. Make necessary changes.
2. Commit the changes and push to a new branch.
3. Create a Merge Request (MR) to the main branch.
## License
This project is open-source and available under the [MIT License](LICENSE).
## Author
Sambhav Sharma