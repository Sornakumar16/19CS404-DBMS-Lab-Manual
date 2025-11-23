
# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1275" height="1650" alt="image" src="https://github.com/user-attachments/assets/180301f9-8b56-40bb-a389-b7d4614b2430" />


### Entities and Attributes
| Entity      | Attributes (PK, FK)                                                            | Notes                                  |
| ----------- | ------------------------------------------------------------------------------ | -------------------------------------- |
| GYM FACULTY | —                                                                              | Represents the overall facility        |
| MEMBER      | MEMBER\_ID (PK), MEMBER\_NAME, MEMBER\_CONTACT, MEMBER\_EMAIL, MEMBER\_ADDRESS | Represents club members                |
| TRAINER     | TR\_ID (PK), TR\_NAME, TR\_CONTACT, TR\_ADDRESS                                | Represents the trainers in the club    |
| STAFF       | ST\_ID (PK), ST\_NAME, ST\_CONTACT, ST\_ADDRESS                                | Represents other staff members         |
| EQUIPMENT   | EQ\_ID (PK), EQ\_TYPE, EQ\_NAME                                                | Represents gym equipment               |
| FEE         | FEE\_ID (PK), FEE\_DATE, FEE\_AMOUNT                                           | Represents fee payments                |
| SEHUDULE    | SEH\_ID (PK), SEH\_DATE, SEH\_TIME, SEH\_DURATION, SEH\_DETAILS                | Represents scheduled training sessions |


### Relationships and Constraints

| Relationship            | Cardinality | Participation | Notes                                        |
| ----------------------- | ----------- | ------------- | -------------------------------------------- |
| MEMBER HAS FEE          | 1\:N        | Total         | Each member can have multiple fee records    |
| MEMBER HAS SEHUDULE     | 1\:N        | Total         | Members can have multiple scheduled sessions |
| TRAINER TRAINS SEHUDULE | 1\:N        | Total         | Each trainer handles multiple schedules      |
| STAFF HAS EQUIPMENT     | 1\:N        | Total         | Staff manages multiple equipment             |


### Assumptions
* Each Member can pay multiple Fees over time (for different durations, services, etc.).

* Each Member can have multiple Scheduled Training Sessions (SEHUDULE).

* Each Trainer can handle multiple SEHUDULE entries.

* Each Staff is responsible for maintaining multiple pieces of Equipment.

* Every entity has a unique identifier as the primary key (e.g., MEMBER_ID, TR_ID).

* All relationships have total participation (i.e., mandatory).

* No inheritance or specializations are considered in this ER model.


# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1275" height="1650" alt="image" src="https://github.com/user-attachments/assets/93fc326c-7468-4b1c-b15b-949b744414fd" />

### Entities and Attributes

| Entity      | Attributes (PK, FK)                                             | Notes                             |
| ----------- | --------------------------------------------------------------- | --------------------------------- |
| USER        | LIB.ID (PK), NAME, MO.NO, NO OF BOOKS ISSUED, ADDRESS           | Represents library users          |
| BOOK        | BOOK BARCODE NO (PK), TITLE, AUTHOR, PLACE, STATUS              | Represents library books          |
| ADMIN       | ADMIN ID (PK), NAME, PHONE NO                                   | Represents library administrators |
| LOGIN       | LOGIN ID (PK), PASSWORD                                         | Login credentials                 |
| BOOK RECORD | TOTAL BOOKS AVAILABLE, ADD RECORD, DELETE RECORD, UPDATE RECORD | Tracks book inventory actions     |


### Relationships and Constraints

| Relationship                     | Cardinality | Participation | Notes                                                                            |
| -------------------------------- | ----------- | ------------- | -------------------------------------------------------------------------------- |
| USER HAVE TO LOGIN               | 1:1         | Total         | Each user must have a login credential                                           |
| USER BORROW BOOK                 | M\:N        | Total         | Users can borrow multiple books, and each book can be borrowed by multiple users |
| BOOK ISSUED BY ADMIN             | M\:N        | Total         | Admin manages the issuance of multiple books                                     |
| LOGIN MAINTAINS ADMIN            | 1:1         | Total         | Each login is tied to an admin                                                   |
| USER GET BOOKS ISSUED FROM ADMIN | M\:N        | Total         | Users get books issued from the admin                                            |

### Assumptions
* Each USER must have exactly one LOGIN credential.

* Each BOOK can be borrowed by multiple USERS, and each USER can borrow multiple BOOKS.

* ADMIN manages BOOK RECORD actions like adding, deleting, updating, and total count.

* Every USER and ADMIN is uniquely identifiable by LIB.ID and ADMIN ID, respectively.

* Every interaction involving borrowing, login, or issuing is mandatory for system operation.

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1275" height="1650" alt="image" src="https://github.com/user-attachments/assets/5e2b341e-e267-4833-8127-ac4f4ed22d71" />


### Entities and Attributes

| Entity            | Attributes (PK, FK)                                                                             | Notes                                       |
| ----------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------- |
| Customer      | C\_ID (PK), Name, Address, Mobile\_No, Email                                                    | A customer can make reservations & reviews  |
| Restaurant    | Res\_ID (PK), Res\_Name, Type, Contact\_No, Address, City, E\_Menu, Description                 | Each restaurant may have multiple tables    |
| Table         | T\_ID (PK), Res\_ID (FK), Capacity, Vacancy(YN)                                                 | Each table belongs to a restaurant          |
| Reservation   | R\_ID (PK), C\_ID (FK), Res\_ID (FK), T\_ID (FK), R\_Date, R\_Time, No\_of\_Guests, Reserve(YN) | Reservation links Customer–Table–Restaurant |
| Review        | Review\_ID (PK), C\_ID (FK), Res\_ID (FK), Review                                               | Review is written by customers              |
| Administrator | A\_ID (PK), Name, Email, Mobile\_No                                                             | Manages the system                          |
| Login         | User\_ID (PK), C\_ID (FK), Password                                                             | Authentication entity                       |


### Relationships and Constraints

| Relationship                        | Cardinality                                                        | Participation                                   | Notes                                       |
| ----------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------- | ------------------------------------------- |
| Customer–Makes–Reservation      | 1\:N (One customer can make many reservations)                     | Total (Customer must exist to make reservation) | Links customers to reservations             |
| Reservation–Reserves–Table      | M:1 (Many reservations per table, but table is reserved at a time) | Partial                                         | Prevents double booking (constraint needed) |
| Restaurant–Has–Table            | 1\:N                                                               | Total                                           | A restaurant must have tables               |
| Restaurant–Has–Review           | 1\:N                                                               | Partial (review optional)                       | A restaurant can have many reviews          |
| Customer–Writes–Review          | 1\:N                                                               | Partial                                         | A customer can write multiple reviews       |
| Administrator–Establishes–Login | 1:1 or 1\:N                                                        | Total                                           | Admin manages login creation                |
| Customer–Performs–Login         | 1:1                                                                | Total                                           | Each customer must login to reserve         |


### Assumptions
* A reservation must be linked to a valid Customer, Restaurant, and Table.

* A table cannot be double-booked for the same time slot.

* A customer may or may not leave a review after visiting.

* Login credentials are unique per customer.

* An administrator oversees system operations and user account creation.

* Restaurants must have at least one table.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
