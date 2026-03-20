# Smart Clinic Management System
---

## Project Scenario

Imagine you’ve just joined SmartCare Solutions, a fast-growing digital health startup dedicated to transforming outpatient clinic operations with modern software. Several small and mid-sized clinics still rely on spreadsheets or outdated tools to manage appointments, patient records, and administrative tasks. By developing an intuitive online portal that empowers doctors and patients to manage schedules and health information seamlessly, SmartCare aims to gain a strong competitive edge in the healthcare tech space.

As their newly hired full-stack developer, you’re tasked with designing and implementing a robust, secure, and scalable Smart Clinic Management System from scratch. This includes both the frontend (built using HTML, CSS, and JavaScript) and the backend (developed in Java with Spring Boot). You will also design the databases, implement APIs, handle authentication, and deploy the final application in a containerized environment with continuous integration to ensure quality code gets committed into the repository.

Additionally, you will gather requirements, define system architecture, design relational and document databases, and implement key modules such as user management, appointment scheduling, medical history tracking, and role-based access control.

Your mission is to:

    - Analyze and list multiple user roles (admin, doctor, patient) and define respective user stories.
    
    - Identify role-specific permissions and restrictions
    
    - Develop RESTful APIs for each core resource (Doctors, Patients, Appointments, Prescriptions)
    
    - Perform integration, allowing CRUD operations through RESTful APIs.
    
    - Design the structured (MySQL) and unstructured (NoSQL) data to store relational data such as patients, doctors, admin, and appointments in MySQL, and store flexible data such as prescriptions in MongoDB.
    
    - Deploy the app using Docker and CI workflows to run tests, check APIs, scan for security issues, and ensure it builds correctly.
    
    - Document the files and carry out version control through GitHub.
---

## Screenshots

![Searching Doctor](screenshots/Searching%20Doctor.png)
*Figure 1: Searching for doctors - Patient role*

![Adding Doctor](screenshots/Adding%20Doctor.png)
*Figure 2: Adding Doctor - Admin role*

![Appointments List](screenshots/Appointments%20List.png)
*Figure 3: Appointments List - Doctor role*

![Admin Portal](screenshots/Admin%20Portal.png)
*Figure 4: Login screen of the application*

---

## Important Documents

[User Stories](user_stories.md)

[Schema Architecture](schema-architecture.md)

[Schema Design](schema-design.md)

[Sample Data MySql](sample-data-mysql.sql)

[Sample Data MongoDB](sample-data-mongo.js)

[Stored Procedures](stored-procedures.sql)

---

## Architecture summary
This Spring Boot application uses both MVC and REST controllers. Thymeleaf
templates are used for the Admin and Doctor dashboards, while REST APIs serve
all other modules. The application interacts with two databases—MySQL (for patient,
doctor, appointment, and admin data) and MongoDB (for prescriptions).
All controllers route requests through a common service layer, which in turn
delegates to the appropriate repositories. MySQL uses JPA entities while
MongoDB uses document models.

## Numbered flow of data and control
1. User accesses AdminDashboard or Appointment pages.
2. The action is routed to the appropriate Thymeleaf or REST controller.
3. The controller calls the service layer
4. The service layer delegates to the appropriate repository
5. The repositories access their respective databases
6. Databases access their appropriate models
7. The models are used at the response layer

## Reference diagram
![Architecture](architecture.png)

---

## Testing endpoints

A) Sign Up- This command registers a new patient in the system

```shell
curl -X POST <URL>/patient -H "Content-Type: application/json" -d '{"name":"name","email":"useremail","phone":"phonenumber","password":"password","age":age,"address":"address","gender":"gender"}'
curl -X POST http://localhost:8080/patient -H "Content-Type: application/json" -d '{"name":"name","email":"useremail@email.com","phone":1234567899,"password":"password","address":"address"}'
```


B) Login This command authenticates the patient and returns a JWT token which will be used tio fetch all the appointments for any patient.

```shell
curl -X POST <URL>/patient/login -H "Content-Type: application/json" -d '{"email":"email","password":"password"}'
curl -X POST http://localhost:8080/patient/login -H "Content-Type: application/json" -d '{"email":"useremail@email.com","password":"password"}'
```


C) Get Appointments This command fetches appointments for the patient using the JWT token

```shell
curl -i -X GET <URL>/patient/1/patient/<JWT-TOKEN> -H "Accept: application/json"
curl -i -X GET http://localhost:8080/patient/1/patient/eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyZW1haWxAZW1haWwuY29tIiwiaWF0IjoxNzczODQ1NzM2LCJleHAiOjE3NzQ0NTA1MzZ9.1QIr1ykrLLy7ov8i7mlDGKG0pn4Hb_4VYQq2nujYNCQ -H "Accept: application/json"
```

Test the endpoint using a curl command to retrieve all doctor details for any specialty and time (you can choose any speciality)
```shell
curl -X GET <URL>/doctor/filter/null/09:00-10:00/Cardiologist
curl -X GET http://localhost:8080/doctor/filter/null/09:00-10:00/Cardiologist
```

## Build and run the container

```shell
docker build -t smart-clinic-backend .
docker run -d -p 8080:8080 --name smart-clinic smart-clinic-backend
```

## Push to a Container Registry

```shell
docker tag smart-clinic-backend your-docker-username/smart-clinic-backend:latest
docker login
docker push your-docker-username/smart-clinic-backend:latest
```

## Cleaning up the container

```shell
docker stop smart-clinic
docker rm smart-clinic
docker rmi smart-clinic-backend
```

