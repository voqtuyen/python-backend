## What is a connection?
A connection is a physical communication channel between the application and the SQL Server: the TCP socket, the named pipe, the shared memory region


## What does the Session do?
The Session establishes all conversations with the database and represents a “holding zone” for all the objects which you’ve loaded or associated with it during its lifespan. 
It provides the interface where SELECT and other queries are made that will return and modify ORM-mapped objects


## What is a transaction?
- ACID properties in database transactions
- A transaction is a series of database operations performed as a group of logical units in a DBMS.Database applications usually access the database through transactions rather than individual operations
![cfda5a9d6e091c7a9142178ebf51963c](https://user-images.githubusercontent.com/28733480/121657121-539dff00-caca-11eb-8382-ae3f362739ac.JPEG)


## References
1. https://stackoverflow.com/questions/39199173/difference-between-session-and-connection-in-sql-server
2. https://docs.sqlalchemy.org/en/14/orm/session_basics.html
