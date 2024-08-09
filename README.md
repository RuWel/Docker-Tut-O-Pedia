# Configuration

There are _2 compose files_. One in which the frontend and backend are built from their Docker files. The other where the images are pulled from DockerHub.

# Setup

We use **4 dockers**

- postgresql
- liquibase
- ruwel123/tutbackend:1.0
- ruwel123/tutreactts:1.0

## postgresql

- a postgresql docker database
- name: tutpostgresql

## liquibase

- liquibase docker to initialise the database.
- name: tutliquibase
- depends on: tutpostgresql

## tutbackend

- springboot/REST backend application
- name: tutbackend
- depends on: tutpostgresql
- toegang: via 'http://localhost:8080/api/heartbeat'

## tutreactts

- React Typescript frontend application
- name: tutfrontend
- depends on: tutbackend
- toegang: via 'http://localhost:3000/'
