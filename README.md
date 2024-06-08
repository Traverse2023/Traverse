# Traverse Root

This repo serves to hold the latest stable release of Traverse for local deployment using docker to containerize all services and databases.

All AWS resources are run locally using dockerized instance of aws localstack. This includes KMS, DynamoDB, SQS, etc...

Our graph database is also run using a standard dockerhub community image of Neo4j.

You will need to have Docker installed as well as Neo4j Desktop to view database entries. _MAKE SURE YOU HAVE AN UPDATED VERSION OF DOCKER TO HAVE UP TO DATE FUNCTIONALITIES!_


## To setup all dockerized services and databases for local deployment:

1. Clone repo recursively to init root of project and submodules at their specified "stable" commits:

`git clone --recursive ${this/repo/url}`

2. Run docker compose to build images and run containers.

`docker compose up --build`

You may also add the -d/--detach flag to run the container in the background and not attached to the terminal instance.
Additionally, you may also wish to run the services with auto reload enabled by making use of docker's _watch_ feature with the below command. This will by default run the containers detached.
          
`docker compose watch`

## To update all submodule repositories to the most up to date commits

1. Execute the below command to pull main for all submodules

`git submodule foreach git pull origin main && git submodule foreach git checkout main`

## Run individual services

To run individual services, you will add the service name as its specified in the compose.yaml file to the end of the compose up command like this:

`docker compose up --build ${service-name}`


## Viewing and interacting with database entries

### DynamoDB

  Download aws localstack desktop or go to https://app.localstack.cloud/inst/default/resources/ for browser version.

### Neo4j

  Download Neo4j desktop. Create a remote database connection with the following parameters. Then connect to the neo4j container.

  Connect URL: `neo4j://localhost:7687`
  
  User: `neo4j`

  Password: `password`





