# Docker_project
### What is Docker?
Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and deploy it as one package.
To install container we required 
```bash
 . docker pull mysql:5.7
 . docker pull wordpress
 . docker pull wordpress:5.1.1-php7.3-apache
 . docker pull mysql:5.7
 ```
### What is mysql? 
MySQL is a relational database management system based on SQL – Structured Query Language. The application is used for a wide range of purposes, including data warehousing, e-commerce, and logging applications. The most common use for mySQL however, is for the purpose of a web database.
To install mysql in redhat  use 
```bash
 . yum install mysql
```
### Redhat
I am using redhat for integration of docker containerization technique with mysql server.
 
 ```bash
 . docker volume create mysql_storage
 . docker volume create wp_storage
  ```
 ### To run container
```bash
 . docker run -dit -e --name dbos -e MYSQL_ROOT_PASSWORD=rootpass  MYSQL_USER=gagan_gupta -e MYSQL_PASSWORD=redhat -e MYSQL_DATABASE=dbmy -v mysql_storage:/var/lib/mysql mysql:5.7
```

after this command your your mysql is ready just check IP address by
```bash
 . docker inspect 5a | grep IP
 ``` 
 Now rn mysql using cmd
 ```bash
  . mysql -h (your_IP_address) -u gagan_gupta -predhat
 ```  
 Now you can run your mysql databases here
 
 ### wordpress Setup
 ```bash
 . docker run -dit -e Wordpress_DB_HOST= dbos -e WORDPRESS_DB_USER=gagan_gupta -e WORDPRESS_DB_PASSWORD=redhat -e WORDPRESS_DB_NAME=dbmy -p 1231:80 --link dbos --name wpos -v wp_storage:/var/www/html  wordpress:5.1.1-php7.3-apache
 now your worpress is ready or mysql is ready
  ```
 you can integrate both and see using (docker log wpos )
