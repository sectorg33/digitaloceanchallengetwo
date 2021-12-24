# digitaloceanchallengetwo
Showcasing My Way Of Deploying A Wordpress Using MySQL Managed Database

first and foremost install docker with these two easy commands.
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ DRY_RUN=1 sh ./get-docker.sh

test the installation with:
docker run hello-world

then install a wordpress image with:- 
docker pull wordpress

first list the images with:- 
docker ps -a (and note the container ID)
then start the container if it's stopped with:- 
docker start "containerid"
then log into the docker with:- 
docker exec -it containerid bash

then first make an update:-
apt update

then connect to your created mysql managed database on digital ocean with:- 
mysql -u user -p -h host_uri -P port

Create a Wordpress User Account with:-
CREATE USER 'wordpressuser'@localhost IDENTIFIED WITH mysql_native_password BY 'your_database_password';

Grant permisions to the newly created user on the wordpress database with:-
GRANT ALL ON wordpress.* TO 'wordpressuser'@localhost; 

Then Type:-
exit

Then edit your wp-config file and replace these values with your own credentials

/** The name of the database for WordPress */
define( 'DB_NAME', 'your_database_name' );

/** MySQL database username */
define( 'DB_USER', 'your_database_username' );

/** MySQL database password */
define( 'DB_PASSWORD', 'your_database_password' );

/** MySQL hostname */
define( 'DB_HOST', 'your_database_host:25060' );

/** Database charset to use in creating database tables. */
define( 'DB_CHARSET', 'utf8' );

/** The database collate type. Don't change this if in doubt. */
define( 'DB_COLLATE', '' );

define('FS_METHOD', 'direct');

save and close

Then head over to your browser to start the installation.
