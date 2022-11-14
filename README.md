# Some proxies written in Go

## Reverse Proxy

1. Run HTTP server at port 8080
    ```
    go run http-server.go
    ```

2. Run reverse proxy at port 9090
    ```
    go run basic-reverse-proxy.go
    ```

3. Testing
    ```
    curl http://localhost:9090/abc/xyz
    Hello /abc/xyz [127.0.0.1:55561]
    ```

## Forward Proxy

TODO

## Happy Coding!
