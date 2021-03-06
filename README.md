# GIS Docker Project

## Project's aim:

Carry out a resilient cloud GIS using Docker.

## Objective:

Design, develop and document a system which has two main roles:  
- Disseminating geographical data in a resilient way.  
- Integrating new geographical data when the system is in its operating state.

## Instructions:

https://docs.google.com/document/d/1N-eZ4-nIZwrFRbM7Vmv_Ndnjm1wsFEICqVnhz0bBO8U/edit

## Our solution:

* We carried out a geographical system that runs on a `Docker` based cluster of Raspberry Pi machines. It allows users to visualise, in a web page, all possible layers.  
* We used the Docker native clustering `Docker Swarm` which turns a pool of Docker hosts into a single, virtual Docker host.  
* The system uses `Geoserver` to disseminate data, which we duplicated to make it tolerant to machine breakdown. Then, we should synchronise the servers, that is why we anticipated a shell script to run so as to synchronise them.  
* In order to store geographical data to be integrated, we used `PostgreSQL` as a database management system with the geographic extension `PostGIS`.  
* PostgreSQL is also duplicated, and we used `Pgpool-II` as a middleware that works between PostgreSQL servers and PostgreSQL database clients using Replication and Load-Balancing mode.  
* We also implemented an `HAProxy` to ensure load balancing between the Geoservers, and `Keepalived` to provide high-availability to our system.

### All in Docker Containers!

All the tools used are in Docker containers: Geoserver, PostgreSQL/PostGIS, Pgpool-II, HAProxy and Keepalived.  
We used `Docker Compose` which is a tool for defining and running multi-container Docker applications.

### Architecture

To make our application, we proposed an architecture that we are going to explain using the following diagrams:

#### 1. Physical Architecture:

![Physical Architecture](https://github.com/AAiache/GIS-Docker-Project/blob/master/Architecture_Diagrams/Physical.png?raw=tru "Physical Architecture")

#### 2. Logical Architecture:

![Logical Architecture](https://github.com/AAiache/GIS-Docker-Project/blob/master/Architecture_Diagrams/Logical.png?raw=tru "Logical Architecture")

Pink rectangles stand for Docker containers.

#### 3. Administrative Architecture:

![Administrative Architecture](https://github.com/AAiache/GIS-Docker-Project/blob/master/Architecture_Diagrams/Administrative.png?raw=tru "Administrative Architecture")

## [Try it!](data/user_manual.md)

