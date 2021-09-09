
# Chapter 1. Introduction
- Database management system (DBMS) is a collection of interrelated data and a set of programs to access those data.
- Database is a collection of data contains information relevant to an enterprise.
- DBMS is used in providing a way to store and retrieve database information in a convenient and efficient way.
## Section 1. Database-System Applications
- Database systems are used to manage collections of data that:
	-  are highly valuable,
	- are relatively large, and
	- are accessed by multiple users and applications, often at the same time.
- Abstraction is the key to manage the complexity
	- Abstraction allows a person to use a complex device or system without having to know the details of how that device or system is constructed.
- There are two broad modes which use database
	- Online Transaction Processing
	- Data Analytics
## Section 2. Purpose of Database Systems
- The problems of file-based databases in early days of computing
	- Data redundancy and inconsistency.
		- Duplication of data
		- Change in structure of files.
	- Difficulty in accessing data.
		- Do not allow needed data to be retrieved in a convenient and efficient manner.
	- Data isolation.
	- Integrity problems.
	- Atomicity problems.
		- Failures may leave database in an inconsistent state with partial updates carried out. 
		- A transaction of a bank must happen in its entirety or not at all.
	- Concurrent-access anomalies.
	- Security problems.
## Section 3. View of Data
- Data Model: a collection of conceptual tools for describing data, data relationships, data semantics, and consistency constraints.
- Data model classification
	- Relational Model
		- Data are represented in the form of tables. Each table has multiple columns, and each column has a unique name.
		- Tables are also known as relations
		- Each row of the table represents one piece of information.
	- Entity-Relationship Model
		- Uses a collection of basic objects, called entities, and relationships among these objects.
	- Semi-structured Data Model
		- Permits the specification of data where individual data items of the same type may have different sets of attributes.
		- For example; JSON and XML
	- Object-Based Data Model
		- Database systems allow procedures to be stored in the database system and executed by the database system.
- Data abstraction levels in DBMS
	- Physical level: The lowest level of abstraction describes how the data are actually stored. The physical level describes complex low-level data structures in detail.
	- Logical level: describes what data are stored in the database, and what relationships exist among those data.
	- View level: The highest level of abstraction describes only part of the entire database.
- Instance of a database: The collection of information stored in the database at a particular moment.
- Database schema: The overall design of the database.
## Section 4. Database Languages
- The database system provides two ways to interact with it
	- Data-definition language (DDL): to specify the database schema
	- Data-manipulation language (DML):  to express database queries and updates
- Data-Definition Language is used to specify the storage structure and access methods used by the database system by a set of statements in a special type of DDL called a data storage and definition language.
- Integrity constraints implemented by the database system
	- Domain Constraints: a domain of possible values must be associated with every attribute (for example, integer types, character types, date/time types).
	- Referential Integrity: ensure that a value that appears in one relation for a given set of attributes also appears in a certain set of attributes in another relation.
	- Authorization: differentiate among the users as far as the type of access they are permitted on various data values in the database.
		- Read only
		- Write only
		- Update only
		- Combination of the last actions
- The output of the DDL is placed in the data dictionary, which contains metadata (data about data).
- A data-manipulation language (DML) is a language that enables users to access or manipulate data as organized by the appropriate data model.
	- Retrieval of information stored in the database.
	- Insertion of new information into the database.
	- Deletion of information from the database.
	- Modification of information stored in the database.
- DMLs are categorized into:
	- Procedural DMLs: require a user to specify what data are needed and how to get those data.
	- Declarative DMLs: require a user to specify what data are needed without specifying how to get those data.
## Section 5. Database Design
## Section 6. Database Engine 
## Section 7. Database and Application Architecture
## Section 8. Database Users and Administrators
## Section 9. History of Database Systems
