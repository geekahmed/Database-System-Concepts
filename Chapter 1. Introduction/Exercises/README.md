
# Chapter 1. Introduction - Exercises

## Practice Exercises

 1. This chapter has described several major advantages of a database system. What are two disadvantages?
 - Setup of the database system requires more knowledge, money, skills, and time.
 - The complexity of the database may result in poor performance.
 2. List five ways in which the type declaration system of a language such as Java or C++ differs from the data definition language used in a database.
 - Executing an action in the DDL results in the creation of an object in the database; in contrast, a programming language type declaration is simply an abstraction used in the program.
 - Database DDLs allows consistency constraints to be specified, which programming language type systems generally do not allow. These include domain constraints and referential integrity constraints.
 - Database DDLs support authorization, giving different access rights to different users. Programming language type systems do not provide such protection (at best, they protect attributes in a class from being accessed by methods in another class).
 - Programming language type systems are usually much richer than the SQL type system. Most databases support only basic types such as different types of numbers and strings, although some databases do support some complex types such as arrays, and objects.
 - A database DDL is focussed on specifying types of attributes of relations; in contrast, a programming language allows objects, and collections of objects to be created.
 3. List six major steps that you would take in setting up a database for a particular enterprise.
- Define the high level requirements of the enterprise (this step generate a document known as the system requirements specification.)
- Define a model containing all appropriate types of data and data relationships.
- Define the integrity constraints on the data.
- Define the physical level.
- For each known problem to be solved on a regular basis (e.g., tasks to be carried out by clerks or Web users) define a user interface to carry out the task, and write the necessary application programs to implement the user interface.
- Create/initialize the database.
 4. Suppose you want to build a video site similar to YouTube. Consider each of the points listed in Section 1.2 as disadvantages of keeping data in a file-processing system. Discuss the relevance of each of these points to the storage of actual video data, and to metadata about the video, such as title, the user who uploaded it, tags, and which users viewed it.
 - Data redundancy and inconsistency. This would be relevant to metadata to some extent, although not to the actual video data, which is not updated. There are very few relationships here, and none of them can lead to redundancy.
 - Difficulty in accessing data. If video data is only accessed through a few predefined interfaces, as is done in video sharing sites today, this will not be a problem. However, if an organization needs to find video data based on specific search conditions (beyond simple keyword queries) if meta data were stored in files it would be hard to find relevant data without writing application programs. Using a database would be important for the task of finding data
 - Data isolation. Since data is not usually updated, but instead newly created, data isolation is not a major issue. Even the task of keeping track of who has viewed what videos is (conceptually) append only, again making isolation not a major issue. However, if authorization is added, there may be some issues of concurrent updates to authorization information.
 - Integrity problems. It seems unlikely there are significant integrity constraints in this application, except for primary keys. if the data is distributed, there may be issues in enforcing primary key constraints. Integrity problems are probably not a major issue.
 - Atomicity problems. When a video is uploaded, metadata about the video and the video should be added atomically, otherwise there would be an inconsistency in the data. An underlying recovery mechanism would be required to ensure atomicity in the event of failures.
 - Concurrent-access anomalies. Since data is not updated, concurrent access anomalies would be unlikely to occur.
 - Security problems. These would be a issue if the system supported authorization.
 5. Keyword queries used in web search are quite different from database queries. List key differences between the two, in terms of the way the queries are specified and in terms of what is the result of a query.
- Queries used in the Web are specified by providing a list of keywords with no specific syntax. The result is typically an ordered list of URLs, along with snippets of information about the content of the URLs. In contrast, database queries have a specific syntax allowing complex queries to be specified. And in the relational world the result of a query is always a table.

## Exercises
6. List four applications you have used that most likely employed a database system to store persistent data.
- Facebook.
- Instagram.
- Youtube.
- Universty's registration website.
7. List four significant differences between a file-processing system and a DBMS.
- Data isolation
- Data integrity
- Concurrent access
- Atomicity.
8. Explain the concept of physical data independence and its importance in database systems.
- It means the abstraction layer between different views of the database which enables different levels of users to intereact with the system without knowing about the underlying physical structure.
9. List five responsibilities of a database-management system. For each responsibility, explain the problems that would arise if the responsibility were not discharged.
- Interaction with the file manager.
- Integrity enforcement.
- Security enforcement.
- Backup and recovery.
- Concurrency control.
If these responsibilities were not met by a given DBM, the following problems can occur, respectively:
a. No DBM can do without this, if there is no file manager interaction then nothing stored in the files can be retrieved.
b. Consistency constraints may not be satisfied, account balances could go below the minimum  allowed, employees could earn too much overtime (e.g., hours > 80) or, airline pilots may fly more hours than allowed by law.
c. Unauthorized users may access the database, or users authorized to access part of the database may be able to access parts of the database for which they lack authority. For example, a high school student could get access to national defense secret codes, or employees could find out what their supervisors earn.
d. Data could be lost permanently, rather than at least being available in a consistent state that existed prior to a failure.
e. Consistency constraints may be violated despite proper integrity enforcement in each transaction. For example, incorrect bank balances might be reflected due to simultaneous withdrawals and deposits, and so on. 
10. List at least two reasons why database systems support data manipulation using a declarative query language such as SQL, instead of just providing a library of C or C++ functions to carry out data manipulation.
- To choose the best way to do the transaction effciently.
- Declarative DMLs are usually easier to learn and use than are procedural DMLs.
11. Assume that two students are trying to register for a course in which there is only one open seat. What component of a database system prevents both students from being given that last seat?
- Transaction manager which ensures that the database remains in a consistent state.
12. Explain the difference between two-tier and three-tier application architectures. Which is better suited for web applications? Why?
- Two-tier architecture, where the application resides at the client machine, and invokes database system functionality at the server machine through query language statements.
- Three-tier architecture, where the client machine acts as merely a front end and does not contain any direct database calls.
- Web applications are better used in three-tier approach in order to prevent distributing database manipulation between clients. This approach supports security and performance. 

13. List two features developed in the 2000s and that help database systems handle data-analytics workloads.
- Column-stores.
- Map-reduce.
14. Explain why NoSQL systems emerged in the 2000s, and briefly contrast their features with traditional database systems.
- Due to the variety of new data-intensive applications and the need for rapid development.
15. Describe at least three tables that might be used to store information in a social networking system such as Facebook.
- Users
- Posts
- Replies
