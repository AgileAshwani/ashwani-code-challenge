### Sample exercise on Docker compose

**objective**

1. Using docker-compose file, run following docker containers:
    - any database engine
    - any service discovery tool
    - your application
2. The Application shall discover the database configuration on startup using the service discovery tool (Consul, ETCd, Zookeeper, .. )
3. The Application shall connect to a database, read a greeting string and print it.
4. The Application shall serve HTTP and be available on host's 127.0.0.1:8080

**Constraints**

You should not use Docker's service discovery abilities, such as

environment variables and 'links'
docker swarm
docker compose's service name
We need 3rd component between the app and db.
Use a service discovery tool for this, like Consul, etcd, Zookeeper or other.

**Expected result**

I can clone the repo, run 'docker-compose up', type '127.0.0.1:8080' in a browser and see 'Hello, world'.

We expect from you a link to github repo with docker-compose.yml and Dockerfiles you might need.

### Solution

* docker-compose.yml file used to deploy complete application stack, consists of:  
       - dockerized-consulserver  
       - dockerized-registrator  
       - dockerized-mysql-greetingsdb  
       - dockerized-web-greetingsapp  

* Consul discovery service detects the mysql database i.e. `greetingsdb` which is being used for our web app i.e. `greetingsapp`

* `greetingsapp` is a simple web application reads `Hello World` string from `greetingsdb` (SQL query to `greetings_tbl`)

**How to setup**

##### System Pre-Requisite :

1. Install `docker`
2. Install `docker-compose`
3. Install `git`

##### Setting Up :

1. Clone this repo `git clone https://github.com/akgitdevops/ashwani-code-challenge.git`
2. Execute `docker-compose up -d`
3. Browse the application `http://127.0.0.1:8080`







