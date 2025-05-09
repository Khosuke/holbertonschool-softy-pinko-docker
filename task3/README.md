#### Here's how to build and run the container: 

We'll need two terminal, one for the front-end and one for the back-end.

**First terminal building/running the backend:**

To build the back-end, copy and paste the following command in your terminal:
``docker build -f ./back-end/Dockerfile -t softy-pinko-back-end:task3 ./back-end``

output: 
```
[+] Building 1.2s (8/8) FINISHED
 => [internal] load build definition from Dockerfile                                                                                 0.0s
 => => transferring dockerfile: 37B                                                                                                  0.0s
 => [internal] load .dockerignore                                                                                                    0.0s
 => => transferring context: 2B                                                                                                      0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                     1.1s
 => [1/8] FROM docker.io/library/ubuntu:latest@sha256:ac58ff7fe25edc58bdf0067ca99df00014dbd032e2246d30a722fa348fd799a5               0.0s
 => [internal] load build context                                                                                                    0.0s
 => => transferring context: 28B                                                                                                     0.0s
 => CACHED [2/8] RUN apt-get update                                                                                                  0.0s
 => CACHED [3/8] RUN apt-get upgrade -y                                                                                              0.0s
 => CACHED [4/8] RUN apt-get install -y python3 python3-pip                                                                          0.0s
 => CACHED [5/8] RUN pip3 install flask                                                                                              0.0s
 => CACHED [6/8] RUN pip3 install flask-cors                                                                                         0.0s
 => CACHED [7/8] WORKDIR /app                                                                                                        0.0s
 => CACHED [8/8] COPY ./api.py /app/api.py                                                                                           0.0s
 => exporting to image                                                                                                               0.0s
 => => exporting layers                                                                                                              0.0s
 => => writing image sha256:72111d9280c3fb3d875aa956a9d5eb407adc55256e667ec3e30dcadd128fd073                                         0.0s
 => => naming to docker.io/library/softy-pinko-back-end:task3                                                                        0.0s
```

And to run the back-end copy and paste this one:
``docker run -p 5252:5252 -it --rm --name softy-pinko-back-end-task3 softy-pinko-back-end:task3``

output:

```
 * Serving Flask app 'api'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5252
 * Running on http://172.17.0.2:5252
Press CTRL+C to quit
```


**Second terminal building/running the front-end:**

To build the front-end, copy and paste the following command in your terminal:
``docker build -f ./front-end/Dockerfile -t softy-pinko-front-end:task3 ./front-end``

output:
```
[+] Building 1.2s (8/8) FINISHED
 => [internal] load build definition from Dockerfile                                                                                 0.0s
 => => transferring dockerfile: 37B                                                                                                  0.0s
 => [internal] load .dockerignore                                                                                                    0.0s
 => => transferring context: 2B                                                                                                      0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                                      1.0s
 => CACHED [1/3] FROM docker.io/library/nginx:latest@sha256:af296b188c7b7df99ba960ca614439c99cb7cf252ed7bbc23e90cfda59092305         0.0s
 => [internal] load build context                                                                                                    0.0s
 => => transferring context: 34.59kB                                                                                                 0.0s
 => [2/3] COPY ./softy-pinko-front-end /var/www/html/softy-pinko-front-end                                                           0.0s
 => [3/3] COPY ./softy-pinko-front-end.conf  /etc/nginx/conf.d/default.conf                                                          0.0s
 => exporting to image                                                                                                               0.0s
 => => exporting layers                                                                                                              0.0s
 => => writing image sha256:f981f38fb967b1a4d477ce370ed52e1fcd97e1dc4863baf1faf47e908bec4057                                         0.0s
 => => naming to docker.io/library/softy-pinko-front-end:task3                                                                       0.0s
```

And to run the front-end copy and paste this one:
``docker run -p 9000:9000 -it --rm --name softy-pinko-front-end-task3 softy-pinko-front-end:task3``

output:
```
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2023/06/12 19:10:39 [notice] 1#1: using the "epoll" event method
2023/06/12 19:10:39 [notice] 1#1: nginx/1.25.0
2023/06/12 19:10:39 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2023/06/12 19:10:39 [notice] 1#1: OS: Linux 5.15.49-linuxkit
2023/06/12 19:10:39 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2023/06/12 19:10:39 [notice] 1#1: start worker processes
2023/06/12 19:10:39 [notice] 1#1: start worker process 28
2023/06/12 19:10:39 [notice] 1#1: start worker process 29
2023/06/12 19:10:39 [notice] 1#1: start worker process 30
2023/06/12 19:10:39 [notice] 1#1: start worker process 31
2023/06/12 19:10:39 [notice] 1#1: start worker process 32
2023/06/12 19:10:39 [notice] 1#1: start worker process 33
2023/06/12 19:10:39 [notice] 1#1: start worker process 34
2023/06/12 19:10:39 [notice] 1#1: start worker process 35
```
