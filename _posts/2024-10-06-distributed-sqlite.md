## Distributed SQLite

Turns out there are many many types of databases in this universe.  
People created many for each and every use case.  
Git for VCS ,  
Vector database like qdrant for AI ML stuff,   
SQLite , on application , single file disk database which is faster because the DB is not on a different server.  

Etc . 

A friend proposed we make SQLite on top of GFS (google file system) , 
Like what ?
How will u make a single file thing on one application distributed . On top of that where is GFS API , we can find only google drive API . 

On some googling we come across , LiteFS , it is a distributed SQLite built by Fly.io

Somehow SQLite can handle 1 million Terabytes/1 billion Gigabytes easily. Which means a lot of data , says here https://www.epicweb.dev/why-you-should-probably-be-using-sqlite  

Isn't it limited by the system in which the embedded database is. 
Where did they even get this metric from.  

> SQLite being a file on disk does make connecting from external clients effectively impossible. But with Fly.io at least, it’s easy to run prisma studio on the production server and proxy that for local access. If you need to connect to it from another app, then you’re out of luck and have to set up HTTP endpoints on the host app for any data you need (for now).

-- https://www.epicweb.dev/why-you-should-probably-be-using-sqlite  

www.epicweb.dev is epic , mostly stuff is written in  simple language.  

Anyways , 
What are Distributed Systems ? Why do we need them ?  
In a system where there are more than one computers operating it is called distributed system .  
Horizontal scaling is Distributed system strategy.  
The complexities of distributed system is mainly due to DB how do u put data consistent across all the computers. How will one computer know that it is working on fresh data and not stale data , to solve this use locks to lock stuff right, cool where will u store the locks , a company I used to work previously used to store locks on redis , Redis it self is distributed , how the fuck .  





 





