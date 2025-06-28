NGINX Reverse Proxy with Go & Python Microservices

This is a simple Docker-based setup with an NGINX reverse proxy routing traffic to two backend services — one written in Go and the other in Python (Flask)              
Step 1: Create the Project Folder Structure

Step 2: Add the Backend Applications

     In the Go folder (service_1), placed a small web server app that listens on a port and responds to /ping and /hello.

     In the Python folder (service_2), do the same using a lightweight web framework like Flask.

     These services simulate two different microservices.

Step 3: Write Dockerfiles for Each Service

     Each service needs its own Dockerfile so it can run in a container.

      Dockerfile contains

      Base image  (Go , Python)

     Copy in the code

     Set the working directory

     Expose the right port

     Set the startup command

Step 4: Configure NGINX as a Reverse Proxy

     Create an NGINX config file inside the nginx folder.

     It should: Listen on port 8080

Step 5: Containerize NGINX

    Create a Dockerfile for NGINX so it runs inside its own container.

Step 6: Define Everything in docker-compose.yml

    This file tells Docker how to build and run all three services together:

    Go service

    Python service

    NGINX reverse proxy
   
    defined build paths, container names, exposed ports, and dependencies here.

Step 7: Build and Run with One Command

     Use docker-compose up --build to:

    
Step 8: Test the Routing

     You can open your browser or use curl to test:

     /service1/ping and /service1/hello should hit the Go service.

    /service2/ping and /service2/hello should hit the Python service.


Step 9: Health Checks and Logs

     Each service has a /ping route used as a health check.

     Docker Compose checks these before letting NGINX start.

    view logs to confirm routing is working correctly using docker-compose logs nginx.


