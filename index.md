# JSON

JSON &mdash; **J**ava**s**cript **O**bject **N**otation

```json
    { 
        "stringValue": "value",
        "numberValue": 123.45,
        "booleanValue": true,
        "nullValue": null,
        "arrayValue": [
            "item1",
            "item2"
        ]
    }
```

## Why JSON?

* Text-based - easy to parse, easy to read
* Ubiquitous - most modern APIs read and write JSON
* Easier than the alternatives - XML, CSV, binary protocols

# HTTP

HTTP &mdash; **H**yper**t**ext **T**ransfer **P**rotocol

```http
GET /id/account HTTP/1.1 (1)
Host: app.pluralsight.com (2)
```

1. Request line
    * Verb - GET, POST, DELETE, etc.
    * Resource - the path from the URL
    * HTTP version
2. Header - Some headers are spelled out in the HTTP spec, while others have been added after the fact.
    * `Host` header specifies to the web server what site is requested (servers can host multiple domains)

```http
HTTP/1.1 302 Found (1)
Date: Thu, 01 Jun 2017 16:59:09 GMT
Content-Type: text/html; charset=utf-8
Transfer-Encoding: chunked (2)
Connection: keep-alive (3)
Set-Cookie: __cfduid=dba4e49317db82df73b95153ef40307181496336349; expires=Fri, 01-Jun-18 16:59:09 GMT; path=/; domain=.pluralsight.com; HttpOnly
Cache-Control: private
Location: /id/?redirectTo=%2Fid%2Fadmin
PS-Build: 1.0.984.0 (4)
PS-Node: COM-1
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Server: cloudflare-nginx
CF-RAY: 3683b8c6fc2f6e3e-SJC

3bc9 (2)
<html><head>...

0


```

1. Response line
    * HTTP version
    * Status code &mdash; 302 is a temporary redirect
    * Status description
2. `Transfer-Encoding: chunked` indicates that the server is sending the body of the response in chunks. The `3bc9` before the body indicates that the first chunk is 0x3bc9 bytes long.
3. `Connection: keep-alive` instructs the client that the TCP connection with the server may remain open, instead of closing it and starting a new one for each request. This can speed up transmissions quite a bit.
4. `PS-Build` is a custom header on many of the Pluralsight apps that indicates the build number.

Lines in HTTP are separated by `\r\n`. The end of headers is indicated with a double line break (i.e. `\r\n\r\n`), as is the end of the body/chunk.

# REST 

REST - **Re**presentational **S**tate **T**ransfer