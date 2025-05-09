#### Here's how to compose and run multiple containers: 

To compose the containers, copy and paste the following command in your terminal:
``docker-compose build``

output: 
```
[+] Building 1.3s (13/13) FINISHED                                                                                              
 => [internal] load build definition from Dockerfile                                                                             0.0s
 => => transferring dockerfile: 32B                                                                                              0.0s
 => [internal] load .dockerignore                                                                                                0.0s
 => => transferring context: 2B                                                                                                  0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                 1.2s
 => [1/8] FROM docker.io/library/ubuntu:latest@sha256:ac58ff7fe25edc58bdf0067ca99df00014dbd032e2246d30a722fa348fd799a5           0.0s
 => [internal] load build context                                                                                                0.0s
 => => transferring context: 28B                                                                                                 0.0s
 => CACHED [2/8] RUN apt-get update                                                                                              0.0s
 => CACHED [3/8] RUN apt-get upgrade -y                                                                                          0.0s
 => CACHED [4/8] RUN apt-get install -y python3 python3-pip                                                                      0.0s
 => CACHED [5/8] RUN pip3 install flask                                                                                          0.0s
 => CACHED [6/8] RUN pip3 install flask-cors                                                                                     0.0s
 => CACHED [7/8] WORKDIR /app                                                                                                    0.0s
 => CACHED [8/8] COPY ./api.py /app/api.py                                                                                       0.0s
 => exporting to image                                                                                                           0.0s
 => => exporting layers                                                                                                          0.0s
 => => writing image sha256:26379ebe4741c491978aa03c623ebbd768c964fefba64055e3013460fe7c5a1d                                     0.0s
 => => naming to docker.io/library/softy-pinko-back-end:task4                                                                    0.0s
[+] Building 1.0s (8/8) FINISHED                                                                                                
 => [internal] load build definition from Dockerfile                                                                             0.0s
 => => transferring dockerfile: 32B                                                                                              0.0s
 => [internal] load .dockerignore                                                                                                0.0s
 => => transferring context: 2B                                                                                                  0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                                  0.8s
 => [internal] load build context                                                                                                0.1s
 => => transferring context: 3.46kB                                                                                              0.0s
 => [1/3] FROM docker.io/library/nginx:latest@sha256:af296b188c7b7df99ba960ca614439c99cb7cf252ed7bbc23e90cfda59092305            0.0s
 => CACHED [2/3] COPY ./softy-pinko-front-end /var/www/html/softy-pinko-front-end                                                0.0s
 => CACHED [3/3] COPY ./softy-pinko-front-end.conf  /etc/nginx/conf.d/default.conf                                               0.0s
 => exporting to image                                                                                                           0.1s
 => => exporting layers                                                                                                          0.0s
 => => writing image sha256:479f9d992a6eae6a56dff4b0cf7f9754446fa195ef273afba5705f460fee8da4                                     0.0s
 => => naming to docker.io/library/softy-pinko-front-end:task4                                                                   0.0s
```

And to run the composed build, copy and paste this one:
``docker-compose up``

output:

```
[+] Running 0/2
 ⠿ front-end Warning                                                                                                                                    2.1s
 ⠿ back-end Warning                                                                                                                                     2.1s
[+] Building 1.6s (20/20) FINISHED                                                                        
 => [softy-pinko-front-end:task4 internal] load build definition from Dockerfile                                                                        0.0s
 => => transferring dockerfile: 188B                                                                                                                    0.0s
 => [softy-pinko-back-end:task4 internal] load build definition from Dockerfile                                                                         0.0s
 => => transferring dockerfile: 262B                                                                                                                    0.0s
 => [softy-pinko-front-end:task4 internal] load .dockerignore                                                                                           0.0s
 => => transferring context: 2B                                                                                                                         0.0s
 => [softy-pinko-back-end:task4 internal] load .dockerignore                                                                                            0.0s
 => => transferring context: 2B                                                                                                                         0.0s
 => [softy-pinko-front-end:task4 internal] load metadata for docker.io/library/nginx:latest                                                             1.4s
 => [softy-pinko-back-end:task4 internal] load metadata for docker.io/library/ubuntu:latest                                                             1.4s
 => [softy-pinko-back-end:task4 internal] load build context                                                                                            0.0s
 => => transferring context: 250B                                                                                                                       0.0s
 => [softy-pinko-back-end:task4 1/8] FROM docker.io/library/ubuntu:latest@sha256:ac58ff7fe25edc58bdf0067ca99df00014dbd032e2246d30a722fa348fd799a5       0.0s
 => [softy-pinko-front-end:task4 internal] load build context                                                                                           0.1s
 => => transferring context: 2.68MB                                                                                                                     0.0s
 => [softy-pinko-front-end:task4 1/3] FROM docker.io/library/nginx:latest@sha256:af296b188c7b7df99ba960ca614439c99cb7cf252ed7bbc23e90cfda59092305       0.0s
 => CACHED [softy-pinko-back-end:task4 2/8] RUN apt-get update                                                                                          0.0s
 => CACHED [softy-pinko-back-end:task4 3/8] RUN apt-get upgrade -y                                                                                      0.0s
 => CACHED [softy-pinko-back-end:task4 4/8] RUN apt-get install -y python3 python3-pip                                                                  0.0s
 => CACHED [softy-pinko-back-end:task4 5/8] RUN pip3 install flask                                                                                      0.0s
 => CACHED [softy-pinko-back-end:task4 6/8] RUN pip3 install flask-cors                                                                                 0.0s
 => CACHED [softy-pinko-back-end:task4 7/8] WORKDIR /app                                                                                                0.0s
 => CACHED [softy-pinko-back-end:task4 8/8] COPY ./api.py /app/api.py                                                                                   0.0s
 => [softy-pinko-front-end:task4] exporting to image                                                                                                    0.0s
 => => exporting layers                                                                                                                                 0.0s
 => => writing image sha256:26379ebe4741c491978aa03c623ebbd768c964fefba64055e3013460fe7c5a1d                                                            0.0s
 => => naming to docker.io/library/softy-pinko-back-end:task4                                                                                           0.0s
 => => writing image sha256:479f9d992a6eae6a56dff4b0cf7f9754446fa195ef273afba5705f460fee8da4                                                            0.0s
 => => naming to docker.io/library/softy-pinko-front-end:task4                                                                                          0.0s
 => CACHED [softy-pinko-front-end:task4 2/3] COPY ./softy-pinko-front-end /var/www/html/softy-pinko-front-end                                           0.0s
 => CACHED [softy-pinko-front-end:task4 3/3] COPY ./softy-pinko-front-end.conf  /etc/nginx/conf.d/default.conf                                          0.0s
[+] Running 3/3
 ⠿ Network task4_default        Created                                                                                                                 0.0s
 ⠿ Container task4-back-end-1   Created                                                                                                                 0.1s
 ⠿ Container task4-front-end-1  Created                                                                                                                 0.1s
Attaching to task4-back-end-1, task4-front-end-1
task4-back-end-1   |  * Serving Flask app 'api'
task4-back-end-1   |  * Debug mode: off
task4-back-end-1   | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
task4-back-end-1   |  * Running on all addresses (0.0.0.0)
task4-back-end-1   |  * Running on http://127.0.0.1:5252
task4-back-end-1   |  * Running on http://172.18.0.2:5252
task4-back-end-1   | Press CTRL+C to quit
task4-front-end-1  | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
task4-front-end-1  | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
task4-front-end-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
task4-front-end-1  | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
task4-front-end-1  | 10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
task4-front-end-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
task4-front-end-1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
task4-front-end-1  | /docker-entrypoint.sh: Configuration complete; ready for start up
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: using the "epoll" event method
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: nginx/1.25.0
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: OS: Linux 5.15.49-linuxkit
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker processes
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 28
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 29
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 30
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 31
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 32
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 33
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 34
task4-front-end-1  | 2023/06/12 19:27:43 [notice] 1#1: start worker process 35
```
