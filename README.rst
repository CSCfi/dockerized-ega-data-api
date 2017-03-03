What is this
=======================================
This is a bundle of Docker containers for EGA Access API. Microservices for the Access API are submodules in this project and Docker containers can be build using Maven and the whole bundle can be run using either Docker Compose or Openshift. 

Usage
=====
Build, run and test the API using Maven, Docker-compose and Openshift::

    git clone --recursive https://github.com/CSC-IT-Center-for-Science/dockerized-ega-data-api.git
    cd dockerized-ega-data-api
    mvn clean install

    # Docker-compose
    docker-compose up

    # Openshift 
    oc new-app -f docker-compose.yml

    # Use the API
    curl http://localhost:8051/datasets/
    curl http://localhost:8051/files/
-----

Known issues
=====
- Status database doens't work at the moment. It needs separate own container in order to communicate with Dataedge and RES microservices. This now bypassed using in-memory database.
- You might see a stacktrace at start up if Eureka container is not ready. Issue is purely cosmetic because microservices will retry connection every 30 second (and succeed when Eureka is ready).  
  
