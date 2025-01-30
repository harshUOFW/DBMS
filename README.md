# DBMS
# Library Management Database System

## Project Description
This Library Management Database System is designed to capture the linkages and exchanges between various entities, including authors, books, categories, departments, publishers, loans, members, staff members, and payments. The goal is to facilitate efficient tracking of library resources, member activities, and financial transactions while ensuring data integrity and efficient querying.

## Database Entities and Attributes

### 1. Author
- **AuthorID** (Primary Key, Number): Unique identifier for an author.
- **FirstName, LastName** (Short Text): Stores author's first and last names.
- **Birthdate** (Date/Time): Author's birthdate.
- **Country** (Short Text): Author's country of residence.

### 2. BookAuthor (Association Table)
- **BookAuthorID** (Primary Key, Number): Unique identifier for a book-author relationship.
- **ISBN** (Foreign Key, Number): References Books entity.
- **AuthorID** (Foreign Key, Number): References Author entity.
- **Co-Author** (Foreign Key, Integer): References another author for co-authored books.

### 3. Books
- **ISBN** (Primary Key, Number): Unique identifier for each book.
- **Title** (Short Text): Stores book titles.
- **PublishedDate** (Date/Time): Date of publication.
- **PublisherID** (Foreign Key, Number): References Publisher entity.
- **CategoryID** (Foreign Key, Number): References Category entity.

### 4. Category
- **CategoryID** (Primary Key, Number): Unique identifier for each category.
- **CategoryName** (Short Text): Stores category names.
- **CreationDate** (Date/Time): Date of category creation.
- **Status** (Lookup): Active or inactive status.

### 5. Department
- **DepartmentID** (Primary Key, Number): Unique identifier for each department.
- **DepartmentName** (Short Text): Stores department names.
- **DepartmentCreationDate** (Date/Time): Date of department creation.

### 6. Loan
- **LoanID** (Primary Key, Number): Unique identifier for each loan.
- **MemberID** (Foreign Key, Number): References Member entity.
- **BookID** (Foreign Key, Number): References Books entity.
- **LoanDate** (Date/Time): Loan date.
- **ReturnDate** (Date/Time): Return date.
- **StaffID** (Foreign Key, Number): References Staff entity.
- **Amount Paid, Amount Owe** (Currency): Tracks payments and dues.
- **Amount Due** (Calculated): Amount Owe - Amount Paid.

### 7. Member
- **MemberID** (Primary Key, Number): Unique identifier for each member.
- **FirstName, LastName** (Short Text): Stores member's first and last names.
- **DOB** (Date/Time): Date of birth.
- **Address** (Short Text): Member's address.
- **Phone** (Number): Member's phone number.

### 8. Publisher
- **PublisherID** (Primary Key, Number): Unique identifier for each publisher.
- **Name** (Short Text): Stores publisher names.
- **Address** (Short Text): Publisher address.
- **Phone** (Number): Publisher phone number.

### 9. Staff
- **StaffID** (Primary Key, Number): Unique identifier for each staff member.
- **FirstName, LastName** (Short Text): Stores staff names.
- **SupervisorID** (Foreign Key, Number): References another Staff member.
- **DepartmentID** (Foreign Key, Number): References Department entity.
- **BirthDate** (Date/Time): Staff birthdate.

### 10. Payment
- **PaymentID** (Partial Key, Short Text): Identifies payments.
- **PaymentDate** (Date/Time): Date of payment.
- **Payment Method** (Lookup): Type of transaction.

### 11. PhoneNumber
- **MemberID, PhoneNumber** (Composite Primary Key): Identifies multiple phone numbers for members.
- **Extension** (Short Text): Phone extension.
- **isPrimary** (Short Text): Indicates primary number.

## Relationships in the Database
- **Author - BookAuthor**: One-to-many (AuthorID).
- **Book - BookAuthor**: One-to-many (ISBN).
- **Book - Category**: Many-to-one (CategoryID).
- **Loan - Member**: Many-to-one (MemberID).
- **Books - Publisher**: Many-to-one (PublisherID).
- **Department - Staff**: One-to-many (DepartmentID).
- **Staff - Loan**: One-to-many (StaffID).
- **Staff - Staff (Self-referential)**: One-to-many (SupervisorID).
- **Author - Book**: Many-to-many (via BookAuthor).
- **Loan - Payment**: One-to-many (LoanID).
- **Member - PhoneNumber**: One-to-many (MemberID).

## Assumptions and Scope Limits
- Each book is identified by ISBN, members by MemberID, and staff by StaffID.
- One book is assigned only one category.
- The database is for a single library branch.
- Advanced features such as book reviews and ratings are not included.
- Financial tracking is limited to basic loan payments.
- Focus is on managing books, authors, members, and staff efficiently.

## How to Use
1. Clone the repository:
   ```sh
   git clone https://github.com/YOUR_USERNAME/library-management-db.git
   ```
2. Navigate to the project folder and set up your database schema using SQL scripts.
3. Use a database management system (DBMS) like MySQL or PostgreSQL to run the schema.

## Contribution
Feel free to contribute by creating pull requests or opening issues.

## License
This project is licensed under the MIT License.

