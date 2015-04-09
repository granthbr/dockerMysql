# dockerMysql


Mounting the database file volume from other containers

Another way to persist the database data is to store database files in another container. To do so, first create a container that holds database files:

docker run -d -v /var/lib/mysql --name sql_data granthbr/datacontainer
 
This will create a new ssh-enabled container and use its folder /var/lib/mysql to store MySQL database files. You can specify any name of the container by using --name option, which will be used in next step.

After this you can start your MySQL image using volumes in the container created above (put the name of container in --volumes-from)

docker run -d --volumes-from sql_data -p 3306:3306 granthbr/dockerMysql 
