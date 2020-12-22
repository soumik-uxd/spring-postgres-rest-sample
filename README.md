# spring-postgres-rest-sample
A sample spring boot REST with a Postgres DB 

Before the application can be started the following checks need to be done:

#### 1. Clone the application
Clone the repository
```bash
git clone <repo>
```

#### 2. Adjust DB connection properties
Change the DB connection properties in the `application.properties`. The current values are listed as below:
```yaml
spring.datasource.url=jdbc:postgresql://localhost:5432/employeedb
spring.datasource.username=postgres
spring.datasource.password=root
spring.jpa.show-sql=true

# Hibernate properties
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

# Hibernate ddl auto
spring.jpa.hibernate.ddl-auto=update
```

#### 3. Start the DB
Either a locally installed or a local Docker image is required. In case a docker image is used (preferably Postgres 10), the below commands can be used as a sample.

```bash
docker run -d --name testdb -v testdb-data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=root -p 5432:5432 postgres:10.13
docker exec -it testdb psql -U postgres -c "CREATE DATABASE employeedb;"
docker exec -it testdb psql -U postgres -c "\c employeedb"               
```

To stop the DB run
```bash
docker stop testdb
```

#### 4. Start the application
```bash
./mvnw spring-boot:run
```

Once done the endpoint is available at `http:\\localhost:8080\api\v1\employees\`
