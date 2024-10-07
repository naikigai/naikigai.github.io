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



