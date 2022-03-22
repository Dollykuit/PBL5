# Project 5

## Implementing a client server architecture using mysql database management system (DBMS)

### This to demonstrate a basic client-server using Mysql Relational Database Management system (RDBMS)

**Step 1**

Created and configured two Linux based virtual servers (EC2 instances in AWS) and were named as below 

- Server A name - MySQL Server
- Server B name - MySQL Client

**Step 2**

Installed the mysql server using the below code:

    sudo apt install mysql_server
    
  
<img width="960" alt="Screenshot 2022-03-22 223953" src="https://user-images.githubusercontent.com/98477745/159588112-307795d3-4247-415b-8798-a58c24cde646.png">

  Ran the below command to verify MySQL was up and running
   
    sudo systemctl status mysql
    
  <img width="831" alt="Screenshot 2022-03-22 224353" src="https://user-images.githubusercontent.com/98477745/159589001-872bc703-f8e4-4c14-a7b5-3a99e71ffd53.png">
  
  Used the below to confirm mysql has been installed on the Server 
  
     sudo mysql
     
  <img width="955" alt="Screenshot 2022-03-22 225126" src="https://user-images.githubusercontent.com/98477745/159589250-4debf783-84ad-41ba-a543-1a0ff4a93661.png">
  
Installed MySQL client software on MySQL linux client server using:

    sudo yum install mysql
    
  <img width="960" alt="Screenshot 2022-03-22 225720" src="https://user-images.githubusercontent.com/98477745/159589896-78318c93-5046-4cc3-bffa-d79086830b15.png">

Created an inbound rule TCP port 3306 in the MySQL server EC2 instance to allow only the private IP address of the MySQL client to connect

<img width="960" alt="Screenshot 2022-03-22 231224" src="https://user-images.githubusercontent.com/98477745/159591384-94a4725e-f475-4d9d-8b4f-5b85fc6773b9.png">

On MySQL server EC2 instace, we created a Database user and granted full privileges for the Database User.

    CREATE USER 'client'@'%' IDENTIFIED BY 'password';
    GRANT ALL PRIVILEGES ON *.* TO 'client'@'%' WITH GRANT OPTION;
    

<img width="960" alt="Screenshot 2022-03-22 232454" src="https://user-images.githubusercontent.com/98477745/159592520-b116cb83-c157-4d2b-913b-409b8a607789.png">

Then configured MySQL server to allow connections from remote hosts with the below:

    sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
    
 Changed the binding address in the configuration file from ext '127.0.0.1' to '0.0.0.0' ext

<img width="960" alt="Screenshot 2022-03-22 232942" src="https://user-images.githubusercontent.com/98477745/159592920-06d8e47d-793a-4305-983a-a0268fdfaaec.png">


Connected to MySQL server from Mysql client EC2 instance using the below:

    mysql -h 172.31.92.165 -u client -p


<img width="960" alt="Screenshot 2022-03-22 233705" src="https://user-images.githubusercontent.com/98477745/159593588-6cd305b9-74ed-447b-b522-657773f7d933.png">

Ran the below command to show databases;

    SHOW DATABASES;
  
  <img width="960" alt="Screenshot 2022-03-22 234006" src="https://user-images.githubusercontent.com/98477745/159593892-9c6aebe7-a9db-4f48-9481-11a02a2ed2a4.png">
  
  **COMPLETED**
 
 
    
    
 




