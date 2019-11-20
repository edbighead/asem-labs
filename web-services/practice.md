## NGINX

### Configuration files

[NGINX](https://www.nginx.com/) is a lightweight, high-performance **web server** designed for high-traffic use cases.

All NGINX configuration files are located in the `/etc/nginx/` directory. The primary configuration file is `/etc/nginx/nginx.conf`.

Configuration options in NGINX are called **directives**. Directives are organized into groups known as **blocks** or **contexts**. The two terms are synonymous.

Lines preceded by a `#` character are comments and not interpreted by NGINX. Lines containing directives must end with a `;` or NGINX will fail to load the configuration and report an error.

Below is a condensed copy of the `/etc/nginx/nginx.conf` file that is included with installations from the NGINX repositories. The file starts with 4 **directives**: `user, worker_processes, error_log, and pid`. These are outside any specific **block** or **context**, so they’re said to exist in the `main` **context**. The `events` and `http` blocks are areas for additional **directives**, and they also exist in the `main` **context**.

```
user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;

events {
       . . .
}

http {
       . . .
}
```

See the [NGINX docs](https://nginx.org/en/docs/ngx_core_module.html) for explanations of these directives and others available in the main context.

### Serving Static Content

An important web server task is serving out files (such as images or static HTML pages). You will implement an example where, depending on the request, files will be served from different local directories: `/opt/data/website` (which may contain HTML files) and `/mnt/assets` (containing images). Also, you will add a default [error_page](http://nginx.org/en/docs/http/ngx_http_core_module.html#error_page). This will require editing of the configuration file and setting up of a [server](http://nginx.org/en/docs/http/ngx_http_core_module.html#server) block inside the [http](http://nginx.org/en/docs/http/ngx_http_core_module.html#http) block with two [location](http://nginx.org/en/docs/http/ngx_http_core_module.html#location) blocks.


* **http block** - Provides the configuration file context in which the HTTP server directives are specified.
  ```
  http {
    server { 
    }
  }
  ```

* **server block** - Sets configuration for a virtual server. There is no clear separation between IP-based (based on the IP address) and name-based (based on the “Host” request header field) virtual servers. Instead, the `listen` directives describe all addresses and ports that should accept connections for the server, and the `server_name` directive lists all server names.

  ```

  server {
      listen       80;
      server_name  localhost;
  }
 
  ```

* **location** - Sets configuration depending on a request URI. A location can either be defined by a prefix string, or by a regular expression. Regular expressions are specified with the preceding "\~*" modifier (for case-insensitive matching), or the "\~" modifier (for case-sensitive matching).
  ```
  server {
    ...
    location / {
        root /data/www;
    }
  }
  ```
#### Command refference
starting container `docker-compose -f easy.yaml up`

getting inside container `docker exec -it nginx_easy bash`

changing comfiguration `vim /etc/nginx/conf.d/website.conf`

working with vim `¯\_(ツ)_/¯`

## Using nginx as HTTP load balancer
Load balancing across multiple application instances is a commonly used technique for **optimizing resource utilization**, **maximizing throughput**, **reducing latency**, and **ensuring fault-tolerant configurations**.

It is possible to use nginx as a very efficient HTTP load balancer to distribute traffic to several application servers and to improve performance, scalability and reliability of web applications with nginx.

### Load balancing methods
The following load balancing mechanisms (or methods) are supported in nginx:

* round-robin — requests to the application servers are distributed in a round-robin fashion,
* least-connected — next request is assigned to the server with the least number of active connections,
* ip-hash — a hash-function is used to determine what server should be selected for the next request (based on the client’s IP address).

The simplest configuration for load balancing with nginx may look like the following:
```
upstream myapp1 {
    server srv1.example.com;
    server srv2.example.com;
    server srv3.example.com;
}

server {
    listen 80;

    location / {
        proxy_pass http://myapp1;
    }
}
```

### Least connected load balancing
Another load balancing discipline is least-connected. Least-connected allows controlling the load on application instances more fairly in a situation when some of the requests take longer to complete.

With the least-connected load balancing, nginx will try not to overload a busy application server with excessive requests, distributing the new requests to a less busy server instead.

Least-connected load balancing in nginx is activated when the least_conn directive is used as part of the server group configuration:
```
  upstream myapp1 {
      least_conn;
      server srv1.example.com;
      server srv2.example.com;
      server srv3.example.com;
  }
```

### Session persistence
Please note that with round-robin or least-connected load balancing, each subsequent client’s request can be potentially distributed to a different server. There is no guarantee that the same client will be always directed to the same server.

If there is the need to tie a client to a particular application server — in other words, make the client’s session “sticky” or “persistent” in terms of always trying to select a particular server — the ip-hash load balancing mechanism can be used.

With ip-hash, the client’s IP address is used as a hashing key to determine what server in a server group should be selected for the client’s requests. This method ensures that the requests from the same client will always be directed to the same server except when this server is unavailable.

To configure ip-hash load balancing, just add the ip_hash directive to the server (upstream) group configuration:

```
upstream myapp1 {
    ip_hash;
    server srv1.example.com;
    server srv2.example.com;
    server srv3.example.com;
}
```

### Weighted load balancing
It is also possible to influence nginx load balancing algorithms even further by using server weights.

In the examples above, the server weights are not configured which means that all specified servers are treated as equally qualified for a particular load balancing method.

With the round-robin in particular it also means a more or less equal distribution of requests across the servers — provided there are enough requests, and when the requests are processed in a uniform manner and completed fast enough.

When the weight parameter is specified for a server, the weight is accounted as part of the load balancing decision.

```
upstream myapp1 {
    server srv1.example.com weight=3;
    server srv2.example.com;
    server srv3.example.com;
}
```

### Task
* Spin up 4 nginx instances with `docker-compose -f medium.yaml up`. 
* 1 load balancer instance `load_balancer` and 3 worker nodes `nginx_1`, `nginx_2` and `nginx_3` will be created
* Overwrite the default nginx page in `nginx_x` containers with the following text `Hello from instance X` where X is the number of instance
* Configure `load_balancer` as a **weighted round-robin** load balancer. *Hint: docker containers can comunicate through container name*

### *Task
* All 3 worker nodes are displaying `load_balancer`'s IP as `$remote_addr` in log files. How can you change it? *Hint: using headers*