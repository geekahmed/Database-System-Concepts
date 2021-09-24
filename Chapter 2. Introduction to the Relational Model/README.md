
# Chapter 2. Introduction to the Relational Model
- The relational model remains the primary data model for commercial data-processing applications.
- The relational model’s independence from any speciﬁc underlying low-level data structures has allowed it to persist despite the advent of new approaches to data storage, including modern column-stores that are designed for large-scale data mining.

## Section 1. Structure of Relational Databases
- A relational database consists of a collection of tables, each of which is assigned a unique name.
- A row in a table represents a relationship among a set of values.
- In the relational model the term relation is used to refer to a table, while the term tuple is used to refer to a row. Similarly, the term attribute refers to a column of a table.
- We use the term relation instance to refer to a speciﬁc instance of a relation, that is, containing a speciﬁc set of rows.
- For each attribute of a relation, there is a set of permitted values, called the domain of that attribute.
- A domain is atomic if elements of the domain are considered to be indivisible units.
- The null value is a special value that signiﬁes that the value is unknown or does not exist.

## Section 2. Database Schema
- Database Schema is the logical design of the database.
- Database Instance is a snapshot of the data in the database at a given instant of time.
- The concept of a relation corresponds to the programming-language notion of a variable, while the concept of a relation schema corresponds to the programming-language notion of type deﬁnition.

## Section 3. Keys
- The values of the attribute values of a tuple must be such that they can uniquely identify the tuple.
	- no two tuples in a relation are allowed to have exactly the same value for all attributes.
	- Commercial database systems relax the requirement that a relation is a set and instead allow duplicate tuples.
- A superkey is a set of one or more attributes that, taken collectively, allow us to identify uniquely a tuple in the relation.
- Candidate keys are superkeys for which no proper subset is a superkey.
- The term primary key to denote a candidate key that is chosen by the database designer as the principal means of identifying tuples within a relation.
	- primary keys are also referred to as primary key constraints.
- Foreign-key constraint from attribute(s) A of relation r_1 to the primary-key B of relation r_2 states that on any database instance, the value of A for each tuple in r_1 must also be the value of B for some tuple in r_2 .
	- Attribute set A is called a foreign key from r 1 , referencing r 2 . The relation r 1 is also called the referencing relation of the foreign-key constraint, and r 2 is called the referenced relation.
- A referential integrity constraint requires that the values appearing in speciﬁed attributes of any tuple in the referencing relation also appear in speciﬁed attributes of at least one tuple in the referenced relation.
- Foreign-key constraints are a special case of referential integrity constraints, where the referenced attributes form the primary key of the referenced relation.

## Section 4. Schema Diagrams
- A database schema, along with primary key and foreign-key constraints, can be depicted by schema diagrams.

## Section 5. Relational Query Languages
- A query language is a language in which a user requests information from the database.
- In an imperative query language, the user instructs the system to perform a speciﬁc sequence of operations on the database to compute the desired result.
- In a functional query language, the computation is expressed as the evaluation of functions that may operate on data in the database or on the results of other functions.
	- The relational algebra.
- In a declarative query language, the user describes the desired information without giving a speciﬁc sequence of steps or function calls for obtaining that information.
	- The tuple relational calculus and domain relational calculus.
- 
