

# Chapter 2. Introduction to the Relational Model - Exercises

## Practice Exercises
- Consider the employee database of Figure 2.17. What are the appropriate primary keys?
	- employee (<u>person name</u>, street, city)
	- works (<u>person name</u>, company name, salary)
	- company (<u>company name</u>, city)
- Consider the foreign-key constraint from the dept name attribute of instructor to the department relation. Give examples of inserts and deletes to these relations that can cause a violation of the foreign-key constraint.
	- Inserting an instructor with unvalid department name or unexisted one.
	- Delete a tuple from depratment table with at least referenced one in another tables like instructor table.
- Consider the time slot relation. Given that a particular time slot can meet more than once in a week, explain why day and start time are part of th primary key of this relation, while end time is not.
	- The attributes day and start time are part of the primary key since a particular class will most likely meet on several different days, and may even meet more than once in a day. However, end time is not part of the primary key since a particular class that starts at a particular time on a particular day cannot end at more than one time.
- In the instance of instructor shown in Figure 2.1, no two instructors have the same name. From this, can we conclude that name can be used as a superkey (or primary key) of instructor?
	- No. For this possible instance of the instructor table the names are unique, but in general this may not be always the case (unless the university has a rule that two instructors cannot have the same name, which is a rather unlikey scenario).
- What is the result of ﬁrst performing the Cartesian product of student and advisor, and then performing a selection operation on the result with the predicate s_id = ID ? (Using the symbolic notation of relational algebra, this query can be written as σ _(s_id=ID) (student × advisor).)
	- The result will be a relation which contains the data of students with coressponding advisor for each.
- Consider the employee database of Figure 2.17. Give an expression in the relational algebra to express each of the following queries:
	- Find the name of each employee who lives in city “Miami”.
		- Πperson_name (σ_(city="Miami")(employee)
	- Find the name of each employee whose salary is greater than $100000.
		- Πperson_name (σ_(salary>100000)(employee ⋈ works)
	- Find the name of each employee who lives in “Miami” and whose salary is greater than $100000.
		- Πperson_name (σ_(salary>100000 ^ city="Miami")(employee ⋈ works)
- Consider the bank database of Figure 2.18. Give an expression in the relational algebra for each of the following queries:
	- Find the name of each branch located in “Chicago”.
		- Πbranch_name (σ_(city="Chicago")(branch)
	- Find the ID of each borrower who has a loan in branch “Downtown”.
		- Π_ID(σ_(branch_name = "Downtown) (borrower ⋈_(borrower.loan_number = loan.loan_number) loan))
- Consider the employee database of Figure 2.17. Give an expression in the relational algebra to express each of the following queries:
	- Find the ID and name of each employee who does not work for “BigBank”.
	- Find the ID and name of each employee who earns at least as much as every employee in the database.

## Exercises
- Describe the diﬀerences in meaning between the terms relation and relation schema.
	- A reltation is like a variable in a programming language which changes during its lifetime.
	- A relation schema is like a type definition which considers static during the lifetime of the reltation.
- Consider the advisor relation shown in the schema diagram in Figure 2.9, with s_id as the primary key of advisor. Suppose a student can have more than one advisor. Then, would s_id still be a primary key of the advisor relation? If not, what should the primary key of advisor be?
	- No. the primary key should be a combination of the student id and the instuctor id.
- Consider the bank database of Figure 2.18. Assume that branch names and customer names uniquely identify branches and customers, but loans and accounts can be associated with more than one customer.
	- What are the appropriate primary keys?
		- branch(<u>branch name</u>, branch city, assets)
		- customer ( <u>ID</u> , customer name, customer street, customer city)
		- loan (<u>loan number</u>, branch name, amount)
		- borrower ( <u>ID</u> , <u>loan number</u>)
		- account (<u>account number</u>, branch name, balance)
		- depositor ( <u>ID</u> , <u>account number</u>)
	- Given your choice of primary keys, identify appropriate foreign keys.
		- loan_number
		- customer_ID
		- account_number
- List two reasons why null values might be introduced into a database.
	- The null value is a special value that signiﬁes that the value is unknown or does not exist.
