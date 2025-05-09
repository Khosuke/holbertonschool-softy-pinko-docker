#### Here's how to compose and run multiple containers: 

To compose the containers, copy and paste the following command in your terminal:
``docker-compose build``

output: 
```
[+] Building 1.5s (13/13) FINISHED                                                                                              
 => [internal] load build definition from Dockerfile                                                                       0.0s
 => => transferring dockerfile: 262B                                                                                       0.0s
 => [internal] load .dockerignore                                                                                          0.0s
 => => transferring context: 2B                                                                                            0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                           1.4s
 => [1/8] FROM docker.io/library/ubuntu:latest@sha256:ac58ff7fe25edc58bdf0067ca99df00014dbd032e2246d30a722fa348fd799a5     0.0s
 => [internal] load build context                                                                                          0.0s
 => => transferring context: 259B                                                                                          0.0s
 => CACHED [2/8] RUN apt-get update                                                                                        0.0s
 => CACHED [3/8] RUN apt-get upgrade -y                                                                                    0.0s
 => CACHED [4/8] RUN apt-get install -y python3 python3-pip                                                                0.0s
 => CACHED [5/8] RUN pip3 install flask                                                                                    0.0s
 => CACHED [6/8] RUN pip3 install flask-cors                                                                               0.0s
 => CACHED [7/8] WORKDIR /app                                                                                              0.0s
 => CACHED [8/8] COPY ./api.py /app/api.py                                                                                 0.0s
 => exporting to image                                                                                                     0.0s
 => => exporting layers                                                                                                    0.0s
 => => writing image sha256:839f2b832b76117f25a85adc73133026d69ab9008eb6c01459922b47cd61a2b1                               0.0s
 => => naming to docker.io/library/softy-pinko-back-end:task5                                                              0.0s
[+] Building 1.1s (8/8) FINISHED                                                                                                
 => [internal] load build definition from Dockerfile                                                                       0.0s
 => => transferring dockerfile: 188B                                                                                       0.0s
 => [internal] load .dockerignore                                                                                          0.0s
 => => transferring context: 2B                                                                                            0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                            0.9s
 => [1/3] FROM docker.io/library/nginx:latest@sha256:593dac25b7733ffb7afe1a72649a43e574778bf025ad60514ef40f6b5d606247      0.0s
 => [internal] load build context                                                                                          0.0s
 => => transferring context: 2.68MB                                                                                        0.0s
 => CACHED [2/3] COPY ./softy-pinko-front-end /var/www/html/softy-pinko-front-end                                          0.0s
 => CACHED [3/3] COPY ./softy-pinko-front-end.conf  /etc/nginx/conf.d/default.conf                                         0.0s
 => exporting to image                                                                                                     0.0s
 => => exporting layers                                                                                                    0.0s
 => => writing image sha256:7c073606697aa4578af1ddad5f2210e611f5aa0762175006d0992b637c1de081                               0.0s
 => => naming to docker.io/library/softy-pinko-front-end:task5                                                             0.0s
[+] Building 0.4s (7/7) FINISHED                                                                                                
 => [internal] load build definition from Dockerfile                                                                       0.0s
 => => transferring dockerfile: 31B                                                                                        0.0s
 => [internal] load .dockerignore                                                                                          0.0s
 => => transferring context: 2B                                                                                            0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                            0.3s
 => [internal] load build context                                                                                          0.0s
 => => transferring context: 32B                                                                                           0.0s
 => [1/2] FROM docker.io/library/nginx:latest@sha256:593dac25b7733ffb7afe1a72649a43e574778bf025ad60514ef40f6b5d606247      0.0s
 => CACHED [2/2] COPY ./proxy.conf /etc/nginx/conf.d/default.conf                                                          0.0s
 => exporting to image                                                                                                     0.0s
 => => exporting layers                                                                                                    0.0s
 => => writing image sha256:bc5dd1e5f2e15577273ef909c555c32b7dfd892c5c6f07f1d50a8519a4c99f32                               0.0s
 => => naming to docker.io/library/softy-pinko-proxy:task5                                                                 0.0s
```

And to run the composed build, copy and paste this one:
``docker-compose up``

output:

```
[+] Running 3/0
 ⠿ Container task5-back-end-1   Created                                                                                    0.0s
 ⠿ Container task5-front-end-1  Created                                                                                    0.0s
 ⠿ Container task5-proxy-1      Created                                                                                    0.0s
Attaching to task5-back-end-1, task5-front-end-1, task5-proxy-1
task5-back-end-1   |  * Serving Flask app 'api'
task5-back-end-1   |  * Debug mode: off
task5-back-end-1   | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
task5-back-end-1   |  * Running on all addresses (0.0.0.0)
task5-back-end-1   |  * Running on http://127.0.0.1:5252
task5-back-end-1   |  * Running on http://172.19.0.2:5252
task5-back-end-1   | Press CTRL+C to quit
task5-front-end-1  | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
task5-front-end-1  | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
task5-front-end-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
task5-front-end-1  | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
task5-front-end-1  | 10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
task5-front-end-1  | /docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
task5-front-end-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
task5-front-end-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
task5-front-end-1  | /docker-entrypoint.sh: Configuration complete; ready for start up
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: using the "epoll" event method
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: nginx/1.25.1
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: OS: Linux 5.15.49-linuxkit
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker processes
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 28
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 29
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 30
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 31
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 32
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 33
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 34
task5-front-end-1  | 2023/06/15 19:28:38 [notice] 1#1: start worker process 35
task5-proxy-1      | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
task5-proxy-1      | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
task5-proxy-1      | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
task5-proxy-1      | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
task5-proxy-1      | 10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
task5-proxy-1      | /docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
task5-proxy-1      | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
task5-proxy-1      | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
task5-proxy-1      | /docker-entrypoint.sh: Configuration complete; ready for start up
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: using the "epoll" event method
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: nginx/1.25.1
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: OS: Linux 5.15.49-linuxkit
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker processes
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 28
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 29
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 30
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 31
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 32
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 33
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 34
task5-proxy-1      | 2023/06/15 19:28:39 [notice] 1#1: start worker process 35
task5-back-end-1   | 172.19.0.4 - - [15/Jun/2023 19:28:48] "GET /api/hello HTTP/1.0" 200 -
task5-front-end-1  | 2023/06/15 19:28:49 [error] 30#30: *27 open() "/var/www/html/softy-pinko-front-end/favicon.ico" failed (2: No such file or directory), client: 172.19.0.4, server: softy-pinko-front-end, request: "GET /favicon.ico HTTP/1.0", host: "front-end:9000", referrer: "http://localhost/"
```
