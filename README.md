# 🚀 LiftOff 🚀
- - - -
![TUGBOAT](https://cl.ly/083Z1r3X231F)

### Welcome to LiftOff, the straight to code approach for php developers’ local environments.

> Built on top of the official Docker repositories for php and MySQL, these preconfigured containers should have everything you need for your next php website or application. If the project requires further configuration, LiftOff can be extended to provided access to additional packages and configurations to the environment.  

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

- **host:**
- **user:**
- **passsword:**

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
[https://scotch.io/tutorials/getting-started-with-docker](https://scotch.io/tutorials/getting-started-with-docker)

[https://www.digitalocean.com/community/tutorials/how-to-dockerise-and-deploy-multiple-wordpress-applications-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-dockerise-and-deploy-multiple-wordpress-applications-on-ubuntu)

[https://github.com/wsargent/docker-cheat-sheet#images](https://github.com/wsargent/docker-cheat-sheet#images)

[https://www.viget.com/articles/how-to-use-docker-on-os-x-the-missing-guide](https://www.viget.com/articles/how-to-use-docker-on-os-x-the-missing-guide)

[https://github.com/wsargent/docker-cheat-sheet#images](https://github.com/wsargent/docker-cheat-sheet#images)

[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-ubuntu-14-04)

[https://medium.com/dev-tricks/apache-and-php-on-docker-44faef716150#.b4wargdpa](https://medium.com/dev-tricks/apache-and-php-on-docker-44faef716150#.b4wargdpa)

[https://deliciousbrains.com/vagrant-docker-wordpress-development/](https://deliciousbrains.com/vagrant-docker-wordpress-development/)
