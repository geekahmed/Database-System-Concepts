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
## Section 2. SQL Data Definition
 - The SQL DDL allows speciﬁcation of not only a set of relations, but also information about each relation, including:
	- The schema for each relation.
	- The types of values associated with each attribute.
	- The integrity constraints.
	- The set of indices to be maintained for each relation.
	- The security and authorization information for each relation.
	- The physical storage structure of each relation on disk.
 - The SQL standard supports a variety of built-in types, including:
	- char(n): A ﬁxed-length character string with user-speciﬁed length n.
	- varchar(n): A variable-length character string with user-speciﬁed maximum length n.
	- int: An integer (a ﬁnite subset of the integers that is machine dependent).
	- smallint: A small integer (a machine-dependent subset of the integer type).
	- numeric(p, d): A ﬁxed-point number with user-speciﬁed precision. The number consists of p digits (plus a sign), and d of the p digits are to the right of the decimal point.
	- real, double precision: Floating-point and double-precision ﬂoating-point numbers with machine-dependent precision.
	- float(n): A ﬂoating-point number with precision of at least n digits.
 - SQL also provides the **nvarchar** type to store multilingual data using the Unicode representation.
 - We deﬁne an SQL relation by using the create table command.
 - The general form of the create table command is:
 - 

    create table r
    		(A1 D1 ,
    		A2 D 2 ,
    		...,
    		An D n ,
    		⟨integrity-constraint1 ⟩,
    		…,
    		⟨integrity-constraintk ⟩);


	- r is the name of the relation
	- Ai is the name of an attribute in the schema of relation r
	- Di is the domain of attribute Ai
 - SQL supports a number of diﬀerent integrity constraints, such that:
	 - primary key (Aj1 , Aj2 , … , Ajm ): The primary-key speciﬁcation says that attributes Aj1 , Aj2 , … , Ajm form the primary key for the relation. The primary-key attributes are required to be nonnull and unique.
	 - foreign key (Ak1 , Ak2 , … , Akn ) references s: The foreign key speciﬁcation says that the values of attributes (Ak1 , Ak2 , … , Akn ) for any tuple in the relation must correspond to values of the primary key attributes of some tuple in relation s.
	 - not null: The not null constraint on an attribute speciﬁes that the null value is not allowed for that attribute.
 - SQL prevents any update to the database that violates an integrity constraint.
 - A newly created relation is empty initially.
	 - Inserting tuples into a relation, updating them, and deleting them are done by data manipulation statements insert, update, and delete.
 - To remove a relation from an SQL database, we use the drop table command.
	 - `drop table r;`
 - The command `delete from r` retains relation r, but deletes all tuples in r.
 - We use the alter table command to add attributes to an existing relation.
	 - All tuples in the relation are assigned null as the value for the new attribute.
	 - `alter table r add A D;`
	 - r is the name of an existing relation
	 - A is the name of the attribute to be added
	 - D is the type of the added attribute
 - We can drop attributes from a relation by the command `alter table r drop A;`
 - Many database systems do not support dropping of attributes, although they will allow an entire table to be dropped.
