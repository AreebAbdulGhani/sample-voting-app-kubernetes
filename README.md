# sample-voting-app-kubernetes
Started with Docker and then deployed it on Kubernetes and then created an AWS (EKS) cluster.

This is a sample voting application which provides an interface for a user to vote and another interface to show the results.

Goals:

1) Deploy these applications as containers on a Kubernetes cluster.
2) Then enable connectivity between the containers so that the applications can access each other and the databases.
3) Then enable external access for the external facing applications, which are the voting and the result app so that the users can access the web browse.

We cannot deploy container directly on Kubernetes.

The application consists of various components such as the voting app, which is a web application developed in python,to provide the user with an interface to choose between two options, a car and a dog. When you make a selection, the vote is stored in Redis, Redis serves as a database in memory. This vote is then processed by the worker, which is an application written in .NET, The worker application takes the new vote and updates the persistent database, which is a PostgreSQL in our case. The PostgreSQL simply has a table with the number of votes for each category, cats and dogs. Then finally the result of the vote is displayed in a web interface, which is another web application developed in NodeJS. This resulting application reads the count of votes from the PostgreSQL database and displays it to the user.

So that is the architecture and data flow of this simple voting application stack. This simple application is build with a combination of different services, different development tools and multiple development platforms such as Python, NodeJS, .NET, etc... This sample application will be used to showcase how easy it is to setup an entire application stack consisting of diverse components in Docker.

-------------xxxxxxxxxxxxxxxxxx----------------

This is based on the original https://github.com/dockersamples/example-voting-app repository from the docker-examples GitHub page and modified it to work on the Kubernetes cluster.
