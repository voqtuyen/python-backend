## What is a connection?
A connection is a physical communication channel between the application and the SQL Server: the TCP socket, the named pipe, the shared memory region


## What does the Session do?
The Session establishes all conversations with the database and represents a “holding zone” for all the objects which you’ve loaded or associated with it during its lifespan. 
It provides the interface where SELECT and other queries are made that will return and modify ORM-mapped objects


## What is a transaction?



## References
1. https://stackoverflow.com/questions/39199173/difference-between-session-and-connection-in-sql-server
2. https://docs.sqlalchemy.org/en/14/orm/session_basics.html
