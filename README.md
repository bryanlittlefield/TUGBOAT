![](https://cl.ly/083Z1r3X231F/download/Image%202017-05-23%20at%202.16.05%20AM.png)

# Welcome to TUGBOAT

> Built on top of the official Docker repositories for php and MySQL, these preconfigured containers should have everything you need to start your next php website or application. If the project requires further configuration dont sweat it, TUGBOAT can be extended to provided access to additional packages and configurations to the environment.  

- - - -

##  Quick Start:
- Install [Docker](https://docs.docker.com/engine/installation/)
- Clone [**TUGBOAT**](https://github.com/bryanlittlefield/TUGBOAT) into an empty directory using : `git clone https://github.com/bryanlittlefield/TUGBOAT .`
- Using a terminal, navigate to the directory you cloned TUGBOAT into and run `docker-compose up`
- Visit `127.0.0.1` | The web root is located locally in `/var/www/html` of your TUGBOAT directory by default. This will sync into your virtual environment
- Happy Coding!:beers:
> More advanced access and configurations below.

- - - -

## Changing MySQL and PHP Versions for your Environment
Within the `docker-compose.yml` file you can update which version of the image to pull by specifying version in replace of latest (see below)

```
web:
    image: bryanjlittlefield/tugboat-php:5.6
    volumes:
        - ./var/log/apache2:/var/log/apache2
        # Example of a Host Mounted Volume
        - ./var/www/html:/var/www/html
```        

```
db:
    image: bryanjlittlefield/tugboat-mysql:5.6
    volumes:
        - ./var/lib/mysql:/var/lib/mysql
```

> Currently TUGBOAT supports MySQL 5.5, 5.6, 5.7 and PHP Versions 5.6, 7.0, 7.1

- - - -

## SSH Logins
- **root**: `docker exec -i -t [container-name] bash`
- **dev**: `docker exec -i -t  -u dev [container-name] bash`

- - - -

## Login to Web Container Using SFTP Client
If using default settings the login for SFTP is the following:

> - **host:** `127.0.0.1`
> - **port:** `2222`
> - **user:** `root`
> - **passsword:** `root`

> - **host:** `127.0.0.1`
> - **port:** `2222`
> - **user:** `dev`
> - **passsword:** `dev`

> **!NOTE!** If you are having any issues logging in first confirm your hostkey by directly running ssh from a terminal `ssh -p2222 dev@127.0.0.1`. If that still doesnt not work log directly into the container and stap and stop ssh `service ssh restart`

- - - -

## Login to DB Using Sequel Pro
If using default settings the login to SequelPro is the following:

- **host:** `127.0.0.1`
- **user:** `admin`
- **passsword:** `admin`

- - - -

## Access to Mailhog
Access the GUI for checking the emails that are being caught by Mailhog:

- **URL:** `127.0.0.1:1025`

- - - -


## Magento Database Connection Example:

```
<connection>
   <host><![CDATA[my_container_name_1]]></host> -OR-  <host><![CDATA[mysql]]></host>
   <username><![CDATA[admin]]></username>
   <password><![CDATA[admin]]></password>
   <dbname><![CDATA[dev]]></dbname>
   <active>1</active>
</connection>
```
> **!MAGENTO NOTE!** It is HIGHLY recomended that if you are running Magento that you DO NOT mount your Magento root volume  due to Magento's large codebase. Instead run them inside of the web container. To remove the mounted /var/www/html volume go to the `docker-compose.yml` file and delete the line under volumes that looks like: `./var/www/html:/var/www/html`

> *See Github Issue: https://github.com/magento/magento2/issues/7859 - Hopefully this gets fixed soon!*

- - - -

## Wordpress Database Connection Example:

```
// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', 'dev' );

/** MySQL database username */
define( 'DB_USER', 'admin' );

/** MySQL database password */
define( 'DB_PASSWORD', 'admin' );

/** MySQL hostname */
define( 'DB_HOST', 'my_container_name_1' ); -OR- define( 'DB_HOST', 'mysql' );
```


## Useful Commands

- List Running Services: `docker exec -i -t [web-container-name] chkconfig`
- Check Groups: `docker exec -i -t [web-container-name] groups`
- List Installed PHP Extensions : `docker exec -i -t [web-container-name] php –me`

- - - -

## Using Docker (ADVANCED):


### DOCKER IMAGES
- - - -

**List Images**
```
docker images
```

**Remove Image**
```
docker rmi [image_name]
```

**Remove ALL Images**

```
docker rmi $(docker images -q)
```

**View Orphaned Images (un-tagged)**

```
docker images --filter dangling=true
```

**Remove Orphaned Images (un-tagged)**

```
docker rmi -f $(docker images --filter dangling=true -q)
```

- - - -
##  Built in Server Configurations include:

### Default Environment Setup:

* **Server Packages**
```
Debian 8.0 (jessie)
PHP 7
Ruby 2.1.x
redis
Vim
wget
cURL
pwgen
Zip
HTOP
Cron
Git
GD and Imagick
Composer
Beanstalkd
Node
NPM
Mcrypt
```
**and more! Just run: `apt list --installed` in the container to get the full list**

* **PHP Extensions**
```
Core
ctype
curl
date
dom
ereg
fileinfo
filter
ftp
gd
hash
iconv
json
libxml
mbstring
mcrypt
mysqli
mysqlnd
openssl
pcre
PDO
pdo_mysql
pdo_pgsql
pdo_sqlite
pgsql
Phar
posix
readline
redis
Reflection
session
SimpleXML
soap
SPL
sqlite3
standard
tokenizer
xml
xmlreader
xmlwriter
zip
zlib
```
- - - -


### DOCKER CONTAINERS
- - - -
> *Docker containers wrap up a piece of software in a complete filesystem that contains everything it needs to run: code, runtime, system tools, system libraries TLDR; anything you can install on a server*

**Run Container(s)**

```
docker run [container]
-d = run in background
-v = set volume sync ~/your/drive/path:/var/www/html
-p 80:80 open ports
```

**Remove/Delete Local Containers**

```
docker rm [container_id]
```

**Remove/Delete ALL Containers**

```
docker rm $(docker ps -a -q)
```

**Delete all stopped containers**
```
docker rm $( docker ps -q -f status=exited)
```

**Stop Local Container**
```
docker stop [container_id]
```

**Stop ALL Local Containers**
```
docker stop $(docker ps -a -q)
```

**Create a Volume to Store your Data**

```
docker volume create --name mysqldb
```

**List Containers (Running or Stopped)**

```
docker ps -a
```

**SSH into Docker Container (Web Server)**

```
docker exec -i -t [container-name] bash
```


### DOCKER VOLUMES
- - - -

**List Virtual Volumes**

```
docker volume ls
```

**Create a Virtual Volume**

```
docker volume create --name mysqldb
```

**Get Info on a Virtual Volumes**

```
docker volume inspect [volume-name]
```

**List Orphaned Volumes**
```
docker volume ls -qf dangling=true
```

**Remove Orphaned Volumes**

```
docker volume rm $(docker volume ls -qf dangling=true)
```



### DOCKER COMPOSE
> *Compose is a tool for defining and running multi-container Docker applications.*  
- - - -

**Run docker-compose.yml files**

```
docker-compose up -d
```

**Shut down Environment**

```
docker-compose down
```

**Rebuild images before starting containers**

```
docker-compose up --build
```

**Example Compose File (docker-compose.yml)**
```
wordpress:
	# build: .
	image: wordpress
	links:
		- db:mysql
	ports:
		- 80:80
	volumes:
		- ~/Sites/docker/public:/var/www/html
db:
	image: mysql
	ports:
		- 3306:3306
	environment:
		MYSQL_ROOT_PASSWORD: password
		MYSQL_DATABASE: wordpress
	volumes:
		- mysqldb:/var/lib/mysql
```



### Good Reads
- - - -

#### Docker Cheat Sheet
[https://github.com/wsargent/docker-cheat-sheet#images](https://github.com/wsargent/docker-cheat-sheet#images)

#### Docker Tools
[https://github.com/veggiemonk/awesome-docker](https://github.com/veggiemonk/awesome-docker)

#### Vagrant vs Docker
[https://deliciousbrains.com/vagrant-docker-wordpress-development/](https://deliciousbrains.com/vagrant-docker-wordpress-development/)

#### Docker In A Nut Shell
[https://prakhar.me/docker-curriculum/](https://prakhar.me/docker-curriculum/)

[https://blog.codeship.com/docker-machine-compose-and-swarm-how-they-work-together/](https://blog.codeship.com/docker-machine-compose-and-swarm-how-they-work-together/)

[http://takacsmark.com/getting-started-with-docker-in-your-project-step-by-step-tutorial/](http://takacsmark.com/getting-started-with-docker-in-your-project-step-by-step-tutorial/)

[https://severalnines.com/blog/mysql-docker-containers-understanding-basics](https://severalnines.com/blog/mysql-docker-containers-understanding-basics)

[https://www.digitalocean.com/community/tutorials/naming-docker-containers-3-tips-for-beginners](https://www.digitalocean.com/community/tutorials/naming-docker-containers-3-tips-for-beginners)

[https://www.digitalocean.com/community/tutorials/how-to-dockerise-and-deploy-multiple-wordpress-applications-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-dockerise-and-deploy-multiple-wordpress-applications-on-ubuntu)

### Docker Configurations
[https://blog.codeship.com/ensuring-containers-are-always-running-with-dockers-restart-policy/](https://blog.codeship.com/ensuring-containers-are-always-running-with-dockers-restart-policy/)

[https://blog.codeship.com/continuous-integration-and-delivery-with-docker/](https://blog.codeship.com/continuous-integration-and-delivery-with-docker/)
