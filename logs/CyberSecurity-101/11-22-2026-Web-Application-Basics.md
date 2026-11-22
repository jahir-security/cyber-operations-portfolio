# Web Application Basics - [11-22-2026]

## What This Covers

This lab covers the fundamental components of web applications and how communication takes place between a client and a web server through HTTP. It begins with understanding front-end and back-end components, including HTML, CSS, JavaScript, databases, web servers, infrastructure, and Web Application Firewalls (WAF). I explored the anatomy of URLs and learned how their individual components help browsers locate specific web resources. The lab further covers HTTP request and response messages, request methods, URL paths, protocol versions, headers, request bodies, response status codes, and security headers. From a cybersecurity perspective, I examined how HTTP headers influence web application security, including Content-Security-Policy (CSP), Strict-Transport-Security (HSTS), X-Content-Type-Options, and Referrer-Policy. Finally, I used the provided static-site HTTP request emulator to perform GET, POST, and DELETE requests against API endpoints and complete practical tasks involving user information.

## Key Concepts

* Understanding the basic architecture of web applications and how they operate through a web browser.
* Understanding the difference between front-end and back-end components.
* Understanding the role of HTML, CSS, and JavaScript in front-end development.
* Understanding the role of databases, web servers, application servers, storage, and networking infrastructure in back-end operations.
* Understanding how a Web Application Firewall (WAF) filters potentially malicious incoming requests.
* Understanding Uniform Resource Locators (URLs) and their individual components.
* Identifying the scheme, user information, host/domain, port, path, query string, and fragment within a URL.
* Understanding the difference between HTTP and HTTPS and the importance of encrypted communication.
* Understanding typosquatting and how misleading domain names can be used in phishing attacks.
* Understanding the HTTP request-response cycle between a client and a web server.
* Identifying the main components of HTTP messages, including the start line, headers, empty line, and body.
* Understanding HTTP request methods such as GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS, TRACE, and CONNECT.
* Understanding how URL paths identify specific resources or API endpoints on a web server.
* Understanding HTTP protocol versions, including HTTP/0.9, HTTP/1.0, HTTP/1.1, HTTP/2, and HTTP/3.
* Analysing common HTTP request headers such as Host, User-Agent, Referer, Cookie, and Content-Type.
* Understanding HTTP request body formats, including URL Encoded, Form Data, JSON, and XML.
* Understanding HTTP response status lines and their three components: HTTP version, status code, and reason phrase.
* Understanding the five HTTP response code categories: Informational (100-199), Successful (200-299), Redirection (300-399), Client Errors (400-499), and Server Errors (500-599).
* Recognising common HTTP status codes such as 100, 200, 301, 404, and 500.
* Analysing response headers such as Date, Content-Type, Server, Set-Cookie, Cache-Control, and Location.
* Understanding the Secure and HttpOnly cookie flags and their importance in protecting session cookies.
* Understanding security headers and how they help mitigate common web application attacks.
* Understanding Content-Security-Policy (CSP) directives, including default-src, script-src, and style-src.
* Understanding Strict-Transport-Security (HSTS) and its max-age, includeSubDomains, and preload directives.
* Understanding X-Content-Type-Options and the nosniff directive to prevent MIME type sniffing.
* Understanding Referrer-Policy directives such as no-referrer, same-origin, strict-origin, and strict-origin-when-cross-origin.
* Using the provided HTTP request emulator to interact with API endpoints and perform GET, POST, and DELETE operations.
* Understanding how HTTP requests can retrieve, modify, and delete information from a web application.

## Commands/Tools Used

```http
# HTTP Request Emulator:

# GET Request - Retrieve User Information:
GET /api/users


# POST Request - Update Bob's Country:
POST /api/user/2

Content-Type: application/json

{
    "country": "US"
}


# DELETE Request - Delete User:
DELETE /api/user/1
```

```http
# Common HTTP Request Methods:

GET
POST
PUT
DELETE
PATCH
HEAD
OPTIONS
TRACE
CONNECT
```

```http
# Common HTTP Request Headers:

Host: tryhackme.com

User-Agent: Mozilla/5.0

Referer: https://www.google.com/

Cookie: user_type=student; room=introtowebapplication; room_status=in_progress

Content-Type: application/json
```

```http
# Common HTTP Response Headers:

Date: Fri, 23 Aug 2024 10:43:21 GMT

Content-Type: text/html; charset=utf-8

Server: nginx

Set-Cookie: sessionId=38af1337es7a

Cache-Control: max-age=600

Location: /index.html
```

```http
# Cookie Security Flags:

Set-Cookie: sessionId=example; Secure; HttpOnly
```

```http
# Content Security Policy (CSP):

Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'


# Strict Transport Security (HSTS):

Strict-Transport-Security: max-age=63072000; includeSubDomains; preload


# Prevent MIME Type Sniffing:

X-Content-Type-Options: nosniff


# Referrer Policy:

Referrer-Policy: no-referrer
Referrer-Policy: same-origin
Referrer-Policy: strict-origin
Referrer-Policy: strict-origin-when-cross-origin
```

```bash
# Security Header Analysis Tool:
securityheaders.io

# Practical HTTP Request Testing:
Provided Static-Site HTTP Request Emulator
```

## What I learned

I learned how web applications are structured and how different components work together to deliver content through a web browser. I started by understanding front-end technologies such as HTML, CSS, and JavaScript, along with back-end components such as databases, web servers, infrastructure, and WAFs. I then learned how to break down URLs into their individual components and understand how browsers use them to locate web resources. I explored the structure of HTTP requests and responses, including request lines, headers, methods, URL paths, protocol versions, request bodies, and response status codes. I also learned how to interpret HTTP headers and understand the security implications of exposed server information, insecure cookies, and insufficient security policies. I studied important security headers such as CSP, HSTS, X-Content-Type-Options, and Referrer-Policy. Finally, I used the provided HTTP request emulator to retrieve user information through a GET request, update Bob's country from UK to US through a POST request, and delete a user through a DELETE request. These exercises helped me understand how web applications communicate through HTTP and how different request methods can be used to interact with backend API resources.
