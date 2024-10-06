## Chapter 1 - Database Systems

What we discuss ?
- Issues that are solved by database
- Derby and SimpleDB database systems

5 Fundamemtal Requirememts of Database , PSALU :
- Databases must be persistent. Otherwise, the records would disappear as soon as the computer is turned off.
- Databases can be shared. Many databases, such as our university database, are intended to be shared by multiple concurrent users.
- Databases must be kept accurate. If users cannot trust the contents of a database, it becomes useless and worthless.
- Databases can be very large. The database of Fig. 1.1 contains only 29 records, which is ridiculously small. It is not unusual for a database to contain millions (or even billions) of records.
- Databases must be usable. If users are not able to easily get at the data they want, their productivity will suffer, and they will clamor for a different product.

What does it mean to have the above conditions met :
- Record Storage : For persistence we can store in files , but CRUD actions would get complex
- Multi-User Access : Data should be locked before writes, so that we don't end up having wrong data.
- Dealing with Catastrophe : You need the database system to recover gracefully from the crash, undoing the updates of all programs that were running when the crash occurred. The mechanism for doing so is interesting and nontrivial, and is examined in Chap. 5
- Memory Management : In this analogy, your kitchen corre- sponds to RAM, the neighborhood store corresponds to a flash drive, and the mail order company corresponds to a disk. Suppose that it takes 5 seconds to get the cookie from your kitchen. Getting the cookie from the analogous store would require 5000 seconds, which is over an hour. This means going to the store, waiting in a very long line, buying the cookie, and returning. And getting the cookie from the analogous mail order company would require 500,000 seconds, which is over 5 days. That means ordering the cookie online and having it shipped using standard delivery. From this point of view, flash and disk memory look terribly slow.
- Usability : Have a query language so that people can easily query.

The Derby Database System :
- The string “ijtest” is the name of the database; its files will be in a folder named “ijtest”, located in the directory from which the ij program was launched. For example, if you ran the program from Eclipse, the database folder will be in the project directory. The string “create 1⁄4 true” tells Derby to create a new database; if it is omitted (as in the second connection command), then Derby expects to find an existing database.

Database Engines
- Separating the UI from the database engine is good system design, as it simplifies the development of the application. For plug and play type advantages.
- We use JDBC to talk to a Database , it is a protocol , analogous to HTTP protocol, there are "JDBC requests".
- Database Engine is the backend of the Database Application. 
- Typically runs on a server . Multiple clients can connect to the server , there is scheduler to align these client requests.
