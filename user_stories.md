# User Stories

# User Story Template

**Title:**
_As a [user role], I want [feature/goal], so that [reason]._

**Acceptance Criteria:**
1. [Criteria 1]
2. [Criteria 2]
3. [Criteria 3]

**Priority:** [High/Medium/Low]
**Story Points:** [Estimated Effort in Points]
**Notes:**
- [Additional information or edge cases]

---

# Personas
- admin
- doctor
- patient

---

## Admin User Stories

## Log into the portal with your username
and password to manage the platform securely

**Title:**
As an Admin, I want to perform log in, so that I can access
and manage the platform securely


**Acceptance Criteria:**
1. The system must allow the Admin to enter a valid username and password.
2. The system must authenticate the credentials and grant access if they are correct.
3. The system must display an error message if the username or password is incorrect.

**Priority:** High
**Story Points:** 3 - 5
**Notes:**
- Consider implementing password hashing.


## Log out of the portal to protect system access

**Title:**
As an Admin, 
I want to log out of the Portal, 
So that system access can be protected.


**Acceptance Criteria:**
1. The system must provide a visible “Log out” option when the Admin is authenticated.
2. When the Admin selects “Log out,” the system must terminate the active session.
3. After logout, the Admin must be redirected to the login page.

**Priority:** High
**Story Points:** 2 - 3
**Notes:**
- Ensure server-side session invalidation (not just client-side redirect).


## Add doctors to the portal

**Title:**
As an Admin, 
I want to add doctors to the portal, 
So that their profiles can be managed and made available within the system.


**Acceptance Criteria:**
1. The system must provide a form to create a new doctor profile.
2. The form must include required fields (e.g., full name, specialty, license number, email, phone).
3. After logout, the Admin must be redirected to the login page.

**Priority:** High
**Story Points:** 4 - 6
**Notes:**
- Ensure proper validation for medical license format.


## Delete doctor's profile from the portal

**Title:**
As an Admin, 
I want to delete a doctor's profile from the portal, 
So that I can remove inactive or incorrect records from the system.


**Acceptance Criteria:**
1. The system must allow the Admin to select a doctor’s profile and choose the “Delete” option.
2. The system must display a confirmation prompt before permanently deleting the profile.

**Priority:** High
**Story Points:** 3 - 5
**Notes:**
- Consider whether deletion should be soft delete (mark as inactive) instead of permanent removal.


## Run a stored procedure in MySQL CLI to get the number of appointments per month and track usage statistics

**Title:**
As an Admin, 
I want to execute a stored procedure in MySQL to retrieve the number of appointments per month, 
So that I can monitor platform usage and generate statistics.


**Acceptance Criteria:**
1. A stored procedure must exist in the database that returns the total number of appointments grouped by month.
2. The stored procedure must execute successfully via the MySQL CLI without errors.

**Priority:** Medium
**Story Points:** 3 - 5
**Notes:**
- Ensure the appointments table has proper indexing on the appointment date column.
- Confirm whether the report should support filtering by year.


---

## Patient User Stories

## View a list of doctors without logging in
**Title:**
As a Patient, 
I want to view a list of doctors without logging in, 
so that I can explore available options before registering.

**Acceptance Criteria:**
1. The system must allow unauthenticated users to access the doctors listing page.
2. The page must display each doctor’s name, specialty, and availability summary.
3. The system must prevent booking actions unless the user is authenticated.

**Priority:** Medium
**Story Points:** 3 - 5
**Notes:**
- Consider pagination for large doctor lists.


## Sign up using email and password
**Title:**
As a Patient,
As a Patient, 
I want to sign up using my email and password, 
so that I can create an account and book appointments.

**Acceptance Criteria:**
1. The system must allow a Patient to register using a valid email and password.
2. The system must validate that the email format is correct.
3. The system must prevent duplicate email registrations.

**Priority:** High
**Story Points:** 5
**Notes:**
- Define password policy (length, special characters, etc.).
- Consider email verification as a separate story.


## Log into the portal
**Title:**
As a Patient, I want to log into the portal, so that I can manage my bookings.

**Acceptance Criteria:**
1. The system must allow the Patient to enter valid credentials.
2. The system must grant access when credentials are correct.
3. The system must display an error message for invalid credentials.

**Priority:** High
**Story Points:** 3
**Notes:**
- Consider rate-limiting failed login attempts.


## Log out of the portal
**Title:**
As a Patient, I want to log out of the portal, so that my account remains secure.

**Acceptance Criteria:**
1. The system must provide a visible logout option when authenticated.
2. Selecting logout must terminate the active session.
3. The system must redirect the Patient to the login or home page.

**Priority:** High
**Story Points:** 2
**Notes:**
- Ensure server-side session invalidation.


## Log in and book an hour-long appointment
**Title:**
As a Patient, I want to log in and book an hour-long appointment with a doctor, so that I can schedule a consultation.

**Acceptance Criteria:**
1. The system must require authentication before booking.
2. The Patient must be able to select a doctor and view available time slots.
3. The system must allow booking only available one-hour time slots.

**Priority:** High
**Story Points:** 5 - 8
**Notes:**
- Define cancellation and rescheduling policies (separate story if needed).
- Ensure transactional consistency to prevent race conditions.


## View upcoming appointments
**Title:**
As a Patient, I want to view my upcoming appointments, 
so that I can prepare accordingly.

**Acceptance Criteria:**
1. The system must require authentication to access appointments.
2. The system must display all future scheduled appointments.
3. Each appointment must show date, time, doctor name, and status.

**Priority:** High
**Story Points:** 5 - 8
**Notes:**
- Define whether past appointments require a separate view.
- Consider pagination if appointment history is large.



---

## Doctor User Stories

## Log into the portal
**Title:**
As a Doctor, I want to log into the portal, so that I can manage my appointments.

**Acceptance Criteria:**
1. The system must allow the Doctor to enter valid credentials.
2. The system must authenticate the credentials and grant access if correct.
3. The system must display an error message for invalid credentials.

**Priority:** Medium
**Story Points:** 3 - 5
**Notes:**
- Implement secure password hashing.


## Log out of the portal
**Title:**
As a Doctor, I want to log out of the portal, so that my data remains protected.
**Acceptance Criteria:**
1. The system must provide a visible logout option when the Doctor is authenticated.
2. Selecting logout must terminate the active session.
3. The system must redirect the Doctor to the login or home page.

**Priority:** High
**Story Points:** 2
**Notes:**
- Ensure server-side session invalidation.


## View appointment calendar
**Title:**
As a Doctor, I want to view my appointment calendar, so that I can stay organized.
**Acceptance Criteria:**
1. The system must require authentication to access the calendar.
2. The calendar must display all scheduled appointments.
3. Each appointment must show patient name, date, time, and status.

**Priority:** High
**Story Points:** 5
**Notes:**
- Define timezone handling.


## Mark unavailability
**Title:**
As a Doctor, I want to mark my unavailability, so that patients can only book available time slots.

**Acceptance Criteria:**
1. The system must allow the Doctor to select dates and times to mark as unavailable.
2. Unavailable time slots must not appear as bookable for patients.
3. The system must prevent marking time slots that already have confirmed appointments.

**Priority:** High
**Story Points:** 5
**Notes:**
- Ensure transactional consistency to avoid double-booking.


## View patient details for upcoming appointments
**Title:**
As a Doctor, 
I want to view patient details for upcoming appointments, 
so that I can be prepared.

**Acceptance Criteria:**
1. The system must require authentication to access patient details.
2. The Doctor must only see patients assigned to their appointments.
3. The system must display relevant patient information (name, contact info, reason for visit).

**Priority:** High
**Story Points:** 5
**Notes:**
- Ensure compliance with healthcare data protection regulations.
- Consider logging access to patient records for audit purposes.


