![](https://p19.f3.n0.cdn.getcloudapp.com/items/NQuvEepO/68747470733a2f2f636c2e6c792f3038335a31723358323331462f646f776e6c6f61642f496d616765253230323031372d30352d32332532306174253230322e31362e3035253230414d2e706e67.png?v=c6b67635a93a2309b8e90953c1466713)

# Welcome to TUGBOAT

> Built on top of the [Official](https://docs.docker.com/docker-hub/official_images/) Docker Images for [Php](https://hub.docker.com/_/php) and [MySQL](https://hub.docker.com/_/mysql), these preconfigured containers will jumpstart your php website or application development. If the environment requires further configurations dont sweat it, TUGBOAT can be extended to provided access to additional packages and configurations to the environment using [build scripts](https://github.com/bryanlittlefield/TUGBOAT/wiki/Running-Scripts-in-the-Web-Container-on-Build).  

- - - -

##  Quick Start:
- Install [Docker](https://docs.docker.com/engine/installation/)
- Run Command: 
  ```
  git clone https://github.com/bryanlittlefield/TUGBOAT && cd TUGBOAT && docker-compose up -d && cd var/www/html
  ```
- Visit `127.0.0.1` or your Remote IP/FQDN `xxx.xx.xx.xxx`
- The web root is mounted locally in `/var/www/html/`
- Happy Coding!:beers:


- - - -

##  Supported Versions:

- **PHP**:
  - 8.3
  - 8.2 (`stable`)
  - 8.1
- **MySQL**:
  - 8.1
  - 8.0 (`stable`)
  - 5.7
 
###  Beta RC
  - 8.3

###  No Longer Maintained:

- **PHP**:
  - 8.0
  - 7.4
  - 7.3
  - 7.2
  - 7.1
  - 7.0
  - 5.6
- **MySQL**:
  - 5.6
  - 5.5
- - - -

## See our [Wiki](https://github.com/bryanlittlefield/TUGBOAT/wiki) for more information.
