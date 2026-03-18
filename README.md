# Smart Clinic Managemenrt System

mvn clean install

mvn spring-boot:run


---

INSERT INTO admin (username, password)
VALUES ('admin', 'admin@1234');


---


curl http://localhost:8080/doctor


---

## testing endpoints

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