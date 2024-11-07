java c
CSCI235 – Database Systems
2024 S4
Implementation Task 2
Due on 7 November 2024
Scope
The Implementation of Task 2 is related to the contents of topic on Indexing.
This Implementation is due by Thursday, 7 November 2024, 9:00 pm Singapore time. This task is worth 3% of the total assessment for the subject.
Only electronic submission through Moodle at: https://moodle.uowplatform.edu.au/   is accepted. All email submission will be deleted and mark 0 (“zero”) will be awarded.
For all the  implemented tasks,  your  report  or output  must  include  a  listing  of all PL/pgPGSQL statements processed.
The submission procedure is explained at the end of this specification.
Specification
Step 1If you have not done it yet, download the TPCHR sample database and load the sample TPCHR using user account tpchr. This will make the user account tpchr the owner of the TPCHR database.
Step 2In this step we shall use the relational tables included in a sample TPCHR benchmark database owned by the user tpchr. The conceptual schema of the sample database is included in the file tpchr.pdf.
Instructions for Creating and Executing a psql Script. to Capture Queries and Output
Step 1: Create Your Script. File
1. Write your SQL commands :
o  Use any text editor (e.g., Notepad, VS Code) to create a script. file containing the SQL commands you want to execute.
2. Save the script:
o  Save the file with a .sql extension (e.g., my_script.sql).
Step 2: Execute the Script in psql and Capture Output
1. Open the psql command prompt:
o  Launch the psql command-line interface for PostgreSQL.
2.  Run the script. and capture both queries and output:
o  To execute your script. file and capture both the SQL queries and their output, use the following command:
psql -U tpchr -e -f my_script.sql > output_file.txt
o  Explanation :
-U: login as user tpchr
-e: Enables query echo, displaying each SQL command before execution.
-f: Specifies the script. file to execute.
> : Redirects both queries and output to a specified output file (e.g., output_file.txt).
This will create output_file.txt containing both the SQL queries and their results.
Task 1 (1.8 marks)The objective of this task is to find the smallest number of indexes that improve performance of a given collection of SELECT statements. We do not expect the best possible improvement in performance for each SELECT statement, however, processing of each SELECT statement must benefit from the existence of at least one of the indexes. An important objective is to minimize the total number of indexes created.
Using the relational table LINEITEM of the sample database TPCHR, for each one of the queries listed below:
i.     Find all the discount (l_discount) of all the items that are shipped (l_shipdate) most recently. Hint. Most recently mean the latest shipment date.
ii.     Find the total number of items shipped by air (l_shipmode) in 1998 (l_shipdate).
iii.     Find the order number (l_orderkey) and item number (l_linenumber) that have the highest discount (l_discount).
iv.     Find the total number of item per line status (l_linestatus). List the line status and the total items per line status.v.     Find the order key (l_orderkey), line item number (l_linenumber), line status  (l_linestatus), shipment date (l_shipdate) and shipment mode (l_shipmode) of  all orders with the order number (l_orderkey) 1795718, 1799046, and 1794626.
a) Construct a PGSQL statement that produces the required output specified in the statement.               (0.5 mark)b) Find the smallest number of indexes that improve performance of a given collection of SELECT statements of a relational table LINEITEM. The smallest number of indexing means a database system will compute the five queries constructed in (a) using one or more indexes that you have created. Hint, you may create an index that can be used to compute more than one queries. Use the explain analyse statement to justify your solutions.                                                            (1.3 mark)
Delivera代 写CSCI235 – Database Systems 2024 S4 Implementation Task 2SQL
代做程序编程语言bles
A file solution1.pdf with CREATE INDEX statements that improve the performance of the queries listed (i, ii, iii, iv, and v above) and the execution plan generated.Please remember that you must consider each one of the queries as an individual case! Please remember that all relational tables are large enough to make full table scans more time consuming that accessing the tables through an index! It means that any solution in which an index is not used for query processing is incorrect.
Task 2 (1.2 marks)The objective of this task is to implement queries statements that processing of each SELECT statement will traverse the index according to specified manners listed in the task.
The implementation task is to use the database tables found in the TPCHR workbench.
Consider the following index is created for the ORDERS relational table:
ordersIdx(o_custkey, o_clerk, o_orderdate)For each of the select statements specified below, find the best possible queries that when the queries are executed, the queries will traverse the index ordersIdx in a manner described in the specification (i) to (vi) .
Note: You need to write a 、create index’statement to create the index describe above before implementing your solutions.i.     Write a SELECT statement such that when it is executed, the query must traverse the index ordersIdx vertically, and the execution MUST access the relational table ORDERS.                      (0.2 mark)ii.     Write a SELECT statement such that when it is executed, the query must traverse the  index vertically, and  the  execution  MUST NOT access  the  relational  table ORDERS.                          (0.2 mark)iii.     Write a SELECT statement such that when it is executed, the query must traverse the index vertically and then horizontally at the leaf level of the index and the execution MUST access the relational table ORDERS.          (0.2 mark)iv.     Write a SELECT statement such that when it is executed, the query must traverse the  index vertically and then horizontally at  the  leaf  level  of the  index  and execution MUST NOT access the relational table ORDERS.                     (0.2 mark)v.     Write a SELECT statement such that when it is executed, the query must traverse the index horizontally at the leaf level of the index and the execution MUST access to the relational table ORDERS.                                    (0.2 mark)vi.     Write a SELECT statement such that when it is executed, the query must traverse the index horizontally at the leaf level of the index and the execution MUST NOT access to the relational table ORDERS.                                                      (0.2 mark)
DeliverablesSubmit a file solution.lst with a report from processing of pgSQL script. solution.sql. The report MUST have no errors the report MUST list all pgSQL statements processed. The report MUST include ONLY the ‘Create index’ statement, ‘SELECT’ statements, ‘ Explain analyze’ statement that implement the specifications of the implementation task.
Submissions
This assignment is due by 9:00 pm (21:00 hours) Thursday, 7 November 2024, 9:00 pm Singapore time.
Zip the files solution.sql and solution.pdf and submit the zipped file through Moodle in the following way:
1)  Access Moodle at http://moodle.uowplatform.edu.au/
2)  To login use a Login link located in the right upper corner the Web page or in the middle of the bottom of the Web page
3)   When  successfully  logged  in,  select  a  site  CSCI235  (SP424)  Database Systems
4)   Scroll down to a section Submissions of Implementation Tasks
5)   Click at Submit your Implementation Task 1 here link.
6)   Click at a button Add Submission
7)   Move the solution.pgSQL and solution.lst (or the zipped file) into an area provided in Moodle. You can drag and drop files here to add them. You can also use a link Add…
8)   Click at a button Save changes,
9)   Click at check box to confirm authorship of a submission,
10) When you  are  satisfied,  remember  to  click  at  a  button  Submit assignment.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
