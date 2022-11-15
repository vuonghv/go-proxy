# Some proxies written in Go

## Reverse Proxy Basic

This reverse proxy server using NewSingleHostReveseProxy

1. Run HTTP server at port 8080
    ```bash
    go run http-server.go
    ```

    Usage:
    ```
    -addr string
        listen host:port (default "127.0.0.1:8080")
    ```

2. Run reverse proxy at port 9090
    ```bash
    go run reverse-proxy-basic.go
    ```

    Usage:
    ```
    -from string
        proxy's listening address (default "127.0.0.1:9090")
    -to string
        the address this proxy will forward to (default "127.0.0.1:8080")
    ```

3. Testing
    ```bash
    curl http://localhost:9090/abc/xyz
    Hello /abc/xyz [127.0.0.1:55561]
    ```

## Reverse Proxy With Load Balance

This reverse proxy support load balance between 2 backends in Round-Robin algo.

1. Run two HTTP server at port 8080/8081
    ```bash
    go run http-server.go -addr 127.0.0.1:8080
    go run http-server.go -addr 127.0.0.1:8081
    ```

2. Run reverse proxy at port 9090
    ```bash
    go run reverse-proxy-loadbalance.go
    ```

    Usage:
    ```
    -from string
        proxy's listening address (default "127.0.0.1:9090")
    -to1 string
        the first address this proxy will forward to (default "127.0.0.1:8080")
    -to2 string
        the second address this proxy will forward to (default "127.0.0.1:8081")
    ```

3. Testing
    ```bash
    curl http://localhost:9090/abc/b1
    Hello /abc/b1 [127.0.0.1:55561]

    curl http://localhost:9090/abc/b2
    Hello /abc/b2 [127.0.0.1:55561]
    ```

## Forward Proxy

TODO

## Happy Coding!
