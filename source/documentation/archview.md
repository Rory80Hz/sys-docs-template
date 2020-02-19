# Architectural View

We use the [C4 approach](http://www.codingthearchitecture.com/2014/08/24/c4_model_poster.html) to illustrating the overall system architecture.

## System Context

High level overview of the context within which the system operates, indicate users and external dependencies.

![Hype X Context Diagram](/images/hype-x-context.png)

## System Containers

These are the distinct services / processes that make up the system. This could be many microservices, or a monolithic application, any data stores, caches, queues etc.

![Traces Context Diagram](/images/hype-x-containers.png)

### Containers and Responsibilities

For each container indicate what it is, what it does, and what it relies on, optionally include a link to source code. Similar to CRC Cards.

#### Example: Hype Service

This service does these things

* CRUD Operations for Hypes

* Publish Hype Created Event

It communicates with

* A queue

* A Database

[Source Code](http://example.org)

[System Documentation](http://example.org)

## System Sequence Diagrams

Outline key journeys and behaviours in the system. [Web Sequence Diagrams](https://www.websequencediagrams.com/) is a useful resource.

### Example : User Creates a new Hype
Components and Data Flows involved in creation of new hype.

![Hype X - New Hype Sequence Diagram](/images/hype-x-new-hype.png)