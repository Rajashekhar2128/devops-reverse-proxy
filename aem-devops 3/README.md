
## First Assignment: Setting up a Reverse Proxy

### Problem Statement

Setup a Reverse Proxy on port 8080 that interfaces two different remote APIs.

- http://localhost:8080/emojis -> https://api.github.com/emojis
- http://localhost:8080/transit -> https://transit.land/api/v1


#### Evaluation
1. Use Apache Web Server 2.4
2. Submit documentation so we can set your solution locally and verify that it works correctly.
3. We will run these two command line scripts to verify that it works:
  - `curl -v http://localhost:8080/emojis` which will return exactly the same response as https://api.github.com/emojis.
  - `curl -v http://localhost:8080/transit` which will return exactly the same response as https://transit.land/api/v1
  - `curl -v http://localhost:8080/transit/changesets` which will return exactly the same response as https://transit.land/api/v1/changesets

### Supporting Materials

Feel free to follow these instructions to setup a basic Apache Web Server instance running locally. You will need
Docker Compose to get the base version up and running.

1. Get your development environment set up. Open up a terminal, `cd` into the Directory
containing the `docker-compose.yml` file and type:
  ```
  $ docker-compose build --no-cache web && docker-compose up web
  ```
2. Verify it works correctly:
  ```
$ curl -v http://localhost:8080
* Rebuilt URL to: http://localhost:8080/
*   Trying ::1...
* Connected to localhost (::1) port 8080 (#0)
> GET / HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.43.0
> Accept: */*
>
< HTTP/1.1 200 OK
< Date: Tue, 17 Apr 2018 18:22:51 GMT
< Server: Apache/2.4.33 (Unix)
< Last-Modified: Tue, 17 Apr 2018 18:15:46 GMT
< ETag: "fc-56a0f53c49880"
< Accept-Ranges: bytes
< Content-Length: 252
< Content-Type: text/html
<
<html>
  <head><title> Software Engineer, AEM — Growth Engineering Team</title></head>
  <body>
    <h1>Hi, you have successfully set up your coding challenge!</h1>
    <pre>
      curl -v http://localhost:8080
    </pre>
  </body>
</html>
  ```

3. Now you are ready to set up a Reverse proxy.
