![](https://cl.ly/083Z1r3X231F/download/Image%202017-05-23%20at%202.16.05%20AM.png)

### Welcome to TUGBOAT

> Built on top of the official Docker repositories for php and MySQL, these preconfigured containers should have everything you need for your next php website or application. If the project requires further configuration, TUGBOAT can be extended to provided access to additional packages and configurations to the environment.  

- - - -
###  Built in Server Configurations include:

### Environment Setup:

* **Server Packages**
```
Debian 8.0 (jessie)
PHP 7
Ruby 2.1.x
memcached
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

* **Node**
```
Grunt
Bower
Gulp
Browsersync
```


- - - -

## SSH Logins
**root**: `docker exec -i -t [container-name] bash`
**dev**: `docker exec -i -t  -u dev [container-name] bash`

_
## Login to DB Using Sequel Pro
If using default settings the login to SequelPro is the following:

- **host:** `127.0.0.1`
- **user:** `admin`
- **passsword:** `admin`

- - - -

## Mailcatcher
Run: `mailcatcher --http-ip=0.0.0.0`  to turn on mailcatcher (on by default)
Then visit: http://127.0.0.1:1080

- - - -

## Useful Commands

List Running Services: `chkconfig`
Check Groups: `groups`
List Installed PHP Extensions : `php –me`

- - - -

## Using Docker (ADVANCED):


### DOCKER IMAGES
- - - -

**List Cached Images**
```
docker images
```

**Remove Cached Image**
```
docker rmi [image_name]
```

**Remove ALL Cached Images**

```
docker rmi $(docker images -q)
```

**View Orphaned Images (un-tagged)**

```
docker images --filter dangling=true
```

**Remove Orphaned Images (un-tagged)**

```
docker rmi --f $(docker images --filter dangling=true -q)
```

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
docker exec -i -t [container-name] bash`
```

**Delete all containers**

```
docker rm $(docker ps -a -q)
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

####Docker Cheat Sheet
[https://github.com/wsargent/docker-cheat-sheet#images](https://github.com/wsargent/docker-cheat-sheet#images)

####Docker Tools
[https://github.com/veggiemonk/awesome-docker](https://github.com/veggiemonk/awesome-docker)

####Vagrant vs Docker
[https://deliciousbrains.com/vagrant-docker-wordpress-development/](https://deliciousbrains.com/vagrant-docker-wordpress-development/)


####Docker In A Nut Shell
[https://prakhar.me/docker-curriculum/](https://prakhar.me/docker-curriculum/)

[http://takacsmark.com/getting-started-with-docker-in-your-project-step-by-step-tutorial/](http://takacsmark.com/getting-started-with-docker-in-your-project-step-by-step-tutorial/)

[https://severalnines.com/blog/mysql-docker-containers-understanding-basics](https://severalnines.com/blog/mysql-docker-containers-understanding-basics)

[https://www.digitalocean.com/community/tutorials/naming-docker-containers-3-tips-for-beginners](https://www.digitalocean.com/community/tutorials/naming-docker-containers-3-tips-for-beginners)

[https://www.digitalocean.com/community/tutorials/how-to-dockerise-and-deploy-multiple-wordpress-applications-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-dockerise-and-deploy-multiple-wordpress-applications-on-ubuntu)

