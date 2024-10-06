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
- The string “ijtest” is the name of the database; its files will be in a folder named “ijtest”, located in the directory from which the ij program was launched. For example, if you ran the program from Eclipse, the database folder will be in the project directory. The string “create = true” tells Derby to create a new database; if it is omitted (as in the second connection command), then Derby expects to find an existing database.

Database Engines
- Separating the UI from the database engine is good system design, as it simplifies the development of the application. For plug and play type advantages.
- We use JDBC to talk to a Database , it is a protocol , analogous to HTTP protocol, there are "JDBC requests".
- Database Engine is the backend of the Database Application. 
- Typically runs on a server . Multiple clients can connect to the server , there is scheduler to align these client requests.
- Using the IP address “0.0.0.0” tells the server to accept requests from anywhere. if this is used in the command sent while starting derby server , `start -h localhost` , use `start -h 0.0.0.0` . How will u expose ur laptop which is the server in this case to accept connections from the internet.
  
The SimpleDB Database System
- SimpleDB written by author , similar to derby , and simple , setup instructions see the book.
- The only way to shut down the server is to kill its process from the console window.
  
The SimpleDB Version of SQL
- SimpleDB supports SQL to a small extent , not all the complex stuff is included. 

### Exercises 

1.1 Suppose that an organization needs to manage a relatively small number of shared records (say, 100 or so).  
(a) Would it make sense to use a commercial database system to manage these records?  
     Ans - Yeah , managing it by storing in files would be tough , if multiple people want to access and edit, it will be tough . However , Using simple Microsoft Excel online would do the job.  
(b) What features of a database system would not be required?  
     Ans - P S A L-not required U  
(c) Would it be reasonable to use a spreadsheet to store these records? What are  
the potential problems?  
     Ans - back in the day , no , because multi user , accurate , persistence, were not satisfied , but today Execel in online so , its cool to use for this  


1.2. Suppose you want to store a large amount of personal data in a database. What features of a database system wouldn’t you need?  
     Ans - P ,S-not req ,  A - not req, L - not req , U  
1.3. Consider some data that you typically manage without a database system (such as a shopping list, address book, checking account info, etc.).  
    (a) How large would the data have to get before you would break down and store it in a database system?  
    Ans - just store it in DB   
    (b) What changes to how you use the data would make it worthwhile to use a database system?  
     Ans - doing a lot of CRUD actions and access by multiple people  


1.4 If you know how to use a version control system (such as Git or Subversion), compare its features to those of a database system.  
(a) Does a version control system have a concept of a record?  
All the data is store in the folder `.git` , it should have record to store commits branches etc.  
(b) How does check-in/checkout correspond to database concurrency control?  
we should not allow to users to push the same branch name to remote atleast one should get error . so concurrently 2 users shld not modify or create same data .   
(c) How does a user perform a commit? How does a user undo uncommitted  
changes?  
we make the changes and then `add` the changes to staging , then commit the staged changes. By running the command , `git commit` , the commit has a id associated with it . using this id a file is created in `.git` and data is stored in it.   
To revert `git revert` command is used , the data in .git is used to diff the current file and delete the changes , a new commit id with new changes is stored in .git and the old file with the old commit would be deleted / or maybe not if the same commit is in other branch.  
For more info - 
https://jvns.ca/blog/2023/09/14/in-a-git-repository--where-do-your-files-live-/#:~:text=git%20stores%20files%20in%20.&text=Every%20previous%20version%20of%20every,git%2Fobjects%20contains%202700%20files.  

https://stackoverflow.com/questions/58479776/does-creating-a-git-branch-copy-all-of-the-source-code#:~:text=Creating%20a%20branch%20in%20Git%20copies%20nothing.  

(d) Many version control systems save updates in difference files, which are
small files that describe how to transform the previous version of the file into the new one. If a user needs to see the current version of the file, the system starts with the original file and applies all of the difference files to it. How well does this implementation strategy satisfy the needs of a database system?  
P - since it is stored in files it is persisted  
S - multiple users can use it until they commit push changes concurrent don't happen.   
A - if u delete `.git` in local and remote there is no way to revert unless u have copy anywhere else. But power cuts and so won't be an issue.  
L - Things get slow with very Large Repos , thats why Meta created their own VCS Sapling , they were using Mercurial before which is again not git as it was better than git  
U - the commands are very useful to manipulate the data easily.   
