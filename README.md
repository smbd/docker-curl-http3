# curl-http3

An http3 aware curl by various libraries

## Usage
XXX: quiche quictls gnutls openssl wolfssl

`docker run -it --rm smbd/curl-http3-XXX curl -V`
```
curl 8.8.0-DEV (x86_64-pc-linux-gnu) libcurl/8.8.0-DEV BoringSSL zlib/1.2.13 nghttp2/1.52.0 quiche/0.21.0
Release-Date: [unreleased]
Protocols: dict file ftp ftps gopher gophers http https imap imaps ipfs ipns mqtt pop3 pop3s rtsp smb smbs smtp smtps telnet tftp
Features: alt-svc AsynchDNS HSTS HTTP2 HTTP3 HTTPS-proxy IPv6 Largefile libz NTLM SSL threadsafe UnixSockets
```

`docker run -it --rm smbd/curl-http3-XXX curl --http3-only -ILv https://127.0.0.1/`
```
*   Trying 127.0.0.1:443...
* Server certificate:
*  subject: CN=41d5abdd724f
*  start date: Jun 10 11:34:01 2024 GMT
*  expire date: Jun  8 11:34:01 2034 GMT
*  issuer: CN=41d5abdd724f
*  SSL certificate verify result: self signed certificate (18), continuing anyway.
* Connected to 127.0.0.1 (127.0.0.1) port 443
* using HTTP/3
* [HTTP/3] [0] OPENED stream for https://127.0.0.1:443/
* [HTTP/3] [0] [:method: HEAD]
* [HTTP/3] [0] [:scheme: https]
* [HTTP/3] [0] [:authority: 127.0.0.1:443]
* [HTTP/3] [0] [:path: /]
* [HTTP/3] [0] [user-agent: curl/8.8.0-DEV]
* [HTTP/3] [0] [accept: */*]
> HEAD / HTTP/3
> Host: 127.0.0.1:443
> User-Agent: curl/8.8.0-DEV
> Accept: */*
> 
* Request completely sent off
< HTTP/3 200 
HTTP/3 200 
< server: nginx/1.27.0
server: nginx/1.27.0
< date: Tue, 11 Jun 2024 14:00:21 GMT
date: Tue, 11 Jun 2024 14:00:21 GMT
< content-type: text/html
content-type: text/html
< content-length: 615
content-length: 615
< last-modified: Tue, 28 May 2024 13:22:30 GMT
last-modified: Tue, 28 May 2024 13:22:30 GMT
< etag: "6655da96-267"
etag: "6655da96-267"
< alt-svc: h3=":443"; ma=86400
alt-svc: h3=":443"; ma=86400
< accept-ranges: bytes
accept-ranges: bytes
< 

```

### httpstat support

`docker run -it --rm smbd/curl-http3-XXX httpstat.sh -ILv https://blog.cloudflare.com --http3`

`docker run -it --rm smbd/curl-http3-XXX httpstat.sh -ILv https://yurets.pro --http3`

![](httpstat.png?raw=true "HTTPSTAT H3")


## Build

```
docker build  -t curl-http3-XXX:latest -f Dockerfile.XXX .

```
