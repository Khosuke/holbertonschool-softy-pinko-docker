# Project : Docker

### Task 0. Create Your First Docker Image
Create a Dockerfile that:

- Is based on the latest ubuntu
- Update APT using apt-get update
- Upgrade currently installed software through APT using apt-get upgrade -y
- Once built, you can run the Docker image in a container and it will echo “Hello, World!” on the terminal.

Directory: task0

### Task 1. Back-end
Set up Dockerfile to run Flask app with virtual environment

- Created a Dockerfile that installs Python 3, Flask, and sets up a virtual environment
- Ensured Flask listens on 0.0.0.0:5252 for external connections
- Exposed port 5252 for container communication with the host
- Copied application files into the container and configured the virtual environment
- Fixed Docker container issues with Flask installation inside the virtual environment

Directory: task1

### Task 2. Front-end
We have created a very simple API server with one route that returns “Hello, World!” and now we want to create a web page to view content from our API server in the context of a more full front-end.

- Inside the task2/front-end, clone this repository -> https://github.com/atlas-school/softy-pinko-front-end

With the softy-pinko-front-end directory and files in place, we need to create a new Dockerfile in our task2/front-end directory.
In order to host and distribute our front-end content we will use a static web server named Nginx; there are many others that can be used, but this one is rather simple to get started with and conveniently has a Docker image that we can use which is pre-installed.

- In the new task2/front-end/Dockerfile, instead of using the latest ubuntu version, use the latest version of nginx.
- The softy-pinko-front-end files must be copied to /var/www/html/softy-pinko-front-end on the Docker image.
- Create an Nginx config file named softy-pinko-front-end.conf inside of the task2/front-end directory. This file must be copied to the Docker image to /etc/nginx/conf.d/default.conf and must include all of the configuration settings required to get your site to show up when visiting the URL.

Directory: task2

### Task 3. Connecting the Front-end and Back-end
This task will have you connect your front-end to the back-end allowing you to have dynamic data on your front-end. This means that communication will occur between your two Docker images (each of which will be running in their own Docker container). To facilitate this, be sure to have multiple terminal instances open so you can have one Docker container running on each.

Directory: task3

### Task 4. Making it Simpler with Docker Compose
With a docker-compose.yml file, we can specify the different components of our entire application, set up some basic configurations, and allow Docker to handle spinning up the entire application all at once, no matter how many containers there are.

Directory: task4

### Task 5. Proxy Server
Making a proxy server to be listening to port 80. Set up a location section for / and use proxy_pass to route any request coming in on that route to http://front-end:9000. Next, set up a location section for /api and use proxy_pass to route any request coming in on that route to http://back-end:5252.

Directory: task5


### Task 6. Scale Horizontally
The goal here is to launch your Docker containers such that you have 2 (or more) API servers. Nginx will act as a load-balance between them so that every request goes to the next API server using the Round-Robin load-balancing algorithm.

Directory: task6
file: 2-api-servers.txt
