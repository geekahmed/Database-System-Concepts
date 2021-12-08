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
## Section 3. Basic Structure of SQL Queries
 - The basic structure of an SQL query consists of three clauses: select, from, and where.
 - A query takes as its input the relations listed in the from clause, operates on them as speciﬁed in the where and select clauses, and then produces a relation as the result.
 - In the formal, mathematical deﬁnition of the relational model, a relation is a set.
	- In practice, duplicate elimination is time-consuming. Therefore, SQL allows duplicates in database relations as well as in the results of SQL expressions.
	- Any database relation whose schema includes a primary-key declaration cannot contain duplicate tuples, since they would violate the primary-key constraint.
 - If we want to force the elimination of duplicates, we insert the keyword distinct after select.
 - SQL allows us to use the keyword all to specify explicitly that duplicates are not removed.
 - The select clause may also contain arithmetic expressions involving the operators +, −, ∗, and / operating on constants or attributes of tuples.
 - The where clause allows us to select only those rows in the result relation of the from clause that satisfy a speciﬁed predicate.
 - SQL allows the use of the logical connectives and, or, and not in the where clause.
	- The operands of the logical connectives can be expressions involving the comparison operators <, <=, >, >=, =, and <>.
 - In SQL, we list the relations that need to be accessed in the from clause and specify the matching condition in the where clause.
 - The relation name is used as a preﬁx to make clear to which attribute we are referring.
 - The select clause is used to list the attributes desired in the result of a query.
 - The from clause is a list of the relations to be accessed in the evaluation of the query.
 - The where clause is a predicate involving attributes of the relation in the from clause.
 - A typical SQL query has the form:
 - 

    select A1 , A2 , … , An
    from r1 , r2 , … , rm
    where P;

 - Ai represents an attribute
 - ri a relation. 
 - P is a predicate.
	 - If the where clause is omitted, the predicate P is true.
 - The from clause by itself deﬁnes a Cartesian product of the relations listed in the clause.
 - The predicate in the where clause is used to restrict the combinations created by the Cartesian product to those that are meaningful for the desired answer.
 - In general, the meaning of an SQL query can be understood as follows:
	 - 1. Generate a Cartesian product of the relations listed in the from clause.
	 - 2. Apply the predicates speciﬁed in the where clause on the result of Step 1.
	 - 3. For each tuple in the result of Step 2, output the attributes (or results of expressions) speciﬁed in the select clause.
 - This sequence of steps helps make clear what the result of an SQL query should be, not how it should be executed.
 - A real implementation of SQL would not execute the query in this fashion; it would instead optimize evaluation by generating (as far as possible) only elements of the Cartesian product that satisfy the where clause predicates.
 - When writing queries, you should be careful to include appropriate where clause conditions.
	 - If you omit the where clause condition in the preceding SQL query, it will output the Cartesian product, which could be a huge relation.
## Section 4. Additional Basic Operations
- There several reasons for not doing the convnient way in deriving names of relations and attributes:
	- Two relations in the from clause may have attributes with the same name, in which case an attribute name is duplicated in the result.
	- If we use an arithmetic expression in the select clause, the resultant attribute does not have a name.
	- if an attribute name can be derived from the base relations, we may want to change the attribute name in the result.
- In order to re-naming an attribute or relation, we can use the **as clause**.
	- old-name as new-name
	- The as clause can appear in both the select and from clauses.
- Reasons of using as clause in renaming:
	- To rename a relation is to replace a long relation name with a shortened version that is more convenient to use elsewhere in the query.
	- To rename a relation is a case where we wish to compare tuples in the same relation.
- An identiﬁer, such as T and S, that is used to rename a relation is referred to as a correlation name in the SQL standard.

	    select distinct T .name
	    from instructor as T , instructor as S
	    where T.salary > S.salary and S.dept name = 'Biology';

- The SQL standard speciﬁes that the equality operation on strings is case sensitive.
- Pattern matching can be performed on strings using the operator like.
	- Percent (%): The % character matches any substring.
	- Underscore ( ): The character matches any character.
- SQL allows the speciﬁcation of an escape character.
	- The escape character is used immediately before a special pattern character to indicate that the special pattern character is to be treated like a normal character.
	- We deﬁne the escape character for a like comparison using the escape keyword.
- SQL allows us to search for mismatches instead of matches by using the not like comparison operator.
- The asterisk symbol “ * ” can be used in the select clause to denote “all attributes.”
- A select clause of the form select * indicates that all attributes of the result relation of the from clause are selected.
- The order by clause causes the tuples in the result of a query to appear in sorted order.
- To specify the sort order, we may specify desc for descending order or asc for ascending order.
- Ordering can be performed on multiple attributes.
- 

    select *
    from instructor
    order by salary desc, name asc;
- SQL includes a between comparison operator to simplify where clauses that specify that a value be less than or equal to some value and greater than or equal to some other value.
- SQL permits us to use the notation (v1 , v2 , … , vn ) to denote a tuple of arity n containing values v1 , v2 , … , vn ; the notation is called a row constructor.
- 

    select name, course id
    from instructor, teaches
    where instructor.ID= teaches.ID and dept name = 'Biology';
- **Is equivalent to:**
- 

    select name, course id
    from instructor, teaches
    where (instructor.ID, dept name) = (teaches.ID, 'Biology');

