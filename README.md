




Title: GearTrack: Office Equipment Checkout System



Submission: Proposal
Team Members: Rishitha Karingula, Sai Bharadwaj Mukkera



 
Description:

GearTrack is a web-enabled database management system (DBMS) designed to streamline the process of tracking office equipment (e.g., laptops, projectors, monitors) borrowed by employees in a workplace. In many offices, equipment is shared among staff, but tracking who has what and when it’s due back is often chaotic, relying on spreadsheets or manual logs. GearTrack addresses this problem by providing a centralized system to record equipment checkouts, returns, and availability. Employees can check out items via a web interface, while managers can monitor usage and overdue returns. The system will support basic queries (e.g., available items) and reports (e.g., overdue checkouts), enhancing workplace organization and accountability.

Scope:
GearTrack targets a single office, managing 15–20 equipment items across categories (e.g., laptops, projectors) and 10–15 employees. Key features include:
I.	Equipment: ID, name, category, status (available, checked out, reserved).
II.	Employees: ID, name, department.
III.	Checkouts: Equipment-employee links with checkout date, due date, return date, and optional reservations.
IV.	Reports: Availability, overdue items, usage frequency.
V.	The system uses MySQL for storage with basic triggers (e.g., status updates), PHP for the backend, and a simple HTML/CSS/JavaScript front-end (e.g., form validation, overdue alerts). Test data will include 15 equipment items, 10 employees, and 20 checkout/reservation records for meaningful queries. Excluding multi-office or maintenance tracking keeps it focused, avoiding overlap with forbidden topics (e.g., libraries, sports stats).

 
Project Plan:

Phase 1	Conceptual Database Design and Proposal	4th April
Phase 2	Logical and Physical Database Design	15th April
Phase 3	Project Implementation	29th April
Phase 4	Project Demonstration	6th May
______________________________________________________________________________
Phase I: Conceptual Database Design (ER Modeling) 
Requirement Analysis:
1.	For each piece of equipment, store its unique ID, name, category (e.g., laptop, projector), and status (available or checked out).
2.	For each employee, store their ID, name, and department.
3.	For each checkout, record the equipment, employee, checkout date, due date, and return date (if returned).
4.	Ensure equipment can only be checked out by one employee at a time.
Entities:
✔ Equipment (item_id, name, category, status)
✔Employees (emp_id, name, department)
✔Checkouts (checkout_id, item_id, emp_id, checkout_date, due_date, return_date)

Relationships:
I.	Checkouts links Equipment (1:N) and Employees (1:N).
II.	Cardinality: One Equipment can have many Checkouts, but one Checkout ties to one Equipment.
III.	Cardinality: One Employee can have many Checkouts, but one Checkout ties to one Employee.

Constraints:
- item_id and emp_id are unique.
- status in Equipment is either 'available' or 'checked out'.
- checkout_date ≤ due_date.
- return_date is NULL until the item is returned.

Additional Constraint: An equipment item cannot be checked out if its status is already 'checked out'.
Why This One?
I.	Entities: Just three core tables (Equipment, Employees, Checkouts) with straightforward relationships (e.g., Equipment-to-Checkouts is one-to-many).
II.	Functionality: Basic CRUD operations (create, read, update, delete) for checking out/returning items—no advanced features like scheduling or workload balancing.
III.	Solves a real workplace problem (tracking equipment), which makes it relatable and demo-friendly and simplest design
______________________________________________________________________________
Phase II: Logical and Physical Database Design 
Relational Schema:
	Equipment(item_id: INT, name: VARCHAR(50), category: VARCHAR(20), status: VARCHAR(10)). Primary Key: item_id. Status defaults to ‘available’.
	Employees(emp_id: INT, name: VARCHAR(50), department: VARCHAR(30)). Primary Key: emp_id. Basic employee data.
	Checkouts(checkout_id: INT, item_id: INT, emp_id: INT, checkout_date: DATE, due_date: DATE, return_date: DATE, is_reservation: BOOLEAN) Primary Key: checkout_id. Foreign Keys: item_id -> Equipment, emp_id -> Employees. Tracks loans and reservations.
______________________________________________________________________________
Phase III: Project Implementation 
GUI Design:
Site Diagram: Home -> Available Equipment -> Checkout/Reserve -> Return -> Report.
Pages:
	Home: Navigation hub.
	Available Equipment: Lists items (SELECT from Equipment).
	Checkout/Reserve: Form for checkout or reservation (INSERT into Checkouts).
	Return: Updates return_date (UPDATE Checkouts, Equipment to ‘available’).
	Report: Overdue items (SELECT from Checkouts JOIN Employees).
Web Front-End:
PHP for CRUD operations, MySQLi for DB, Bootstrap CSS for styling, JavaScript for validation and overdue alerts 
______________________________________________________________________________
Phase IV: Project Demonstration
Demo:
	Problem: Equipment tracking woes.
	Solution: Show ER/schema, demo checkout/reserve/return, display report.
	Challenges: Trigger debugging; Lesson: Test incrementally.
	Future: Add email notifications.

______________________________________________________________________________
Self-Evaluation:
Limitation: No multi-user roles. Fix: Add role column.
Submission: Slides + code zip.
