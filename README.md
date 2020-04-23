# docker_metabase_db
Docker, metabase and db setup

This is a project to install and set up docker with 2 active containers 1 for the database and 1 for the metabase software to visualise the data. 



## Getting Started

## Prerequisites
Ubuntu Installation 
Docker Installation


Internet Connection

## Installing
1. Download the jbl folder. 
The file contains 1 subfolder named services, the docker-compose.yml, the MySQL_Read_Stats.sql file(contains the sql data). 
The services folder contains 2 subfolders, metabase and mysql. metabase has a single docker file and mysql has a docker file and a create.sql file that contains the commmand to create the database.

2.Install Docker using the following guide https://docs.docker.com/engine/install/ubuntu/

3.Install Docker-Compose using the following guide https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04

change the version in this command to latest: $ sudo curl -L https://github.com/docker/compose/releases/download/1.25.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

4. Open terminal and move to the directory that the docker-compose.yml exists (inside jbl folder).

5. Run the following command: $ docker-compose up -d --build

6. Check with the $ docker ps command if you have 2 containers 1 fore mysqldb and 1 for metabase

7. Check if following command $ docker exec -ti c21f81644be9 mysql -uroot -proot -e "show databases;" using your container id returns you the read_stats_xt database

8.Run the following command: docker exec -i 26eb33938727 mysql --user root -P 3306 --password=root read_stats_xt < MySQL_Read_Stats.sql 
using your container id and your username and password.

9. You can log in in the container using the following command $ docker exec -ti container_id bash
when logged in you can run the following mysql command $ mysql -uroot -p using mysql commands you can check if your tables exist and are full of data. 

10.Login into localhost:3000 so you can configure metabase use your conainer name that mysql runs as localhost

