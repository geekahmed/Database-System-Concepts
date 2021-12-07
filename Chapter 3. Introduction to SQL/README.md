# Chapter 3. Introduction to SQL
## Section 1. Overview of the SQL Query Language
- IBM developed the original version of SQL, originally called Sequel, as part of the System R project in the early 1970s.
- The Sequel language has evolved since then, and its name has changed to SQL (Structured Query Language).
- SQL has clearly established itself as the standard relational database language.
- The SQL language has several parts:
	- **Data-definition language (DDL):** The SQL DDL provides commands for deﬁning relation schemas, deleting relations, and modifying relation schemas.
	- **Data-manipulation language (DML):** The SQL DML provides the ability to query information from the database and to insert tuples into, delete tuples from, and modify tuples in the database.
	- **Integrity:** The SQL DDL includes commands for specifying integrity constraints that the data stored in the database must satisfy. Updates that violate integrity constraints are disallowed.
	- **View definition:** The SQL DDL includes commands for deﬁning views.
	- **Transaction control:** SQL includes commands for specifying the beginning and end points of transactions.
	- **Embedded SQL and dynamic SQL:** Embedded and dynamic SQL deﬁne how SQL statements can be embedded within general-purpose programming languages, such as C, C++, and Java.
	- **Authorization:** The SQL DDL includes commands for specifying access rights to relations and views.
- Most implementations support some nonstandard features while omitting support for some of the more advanced and more recent features.
