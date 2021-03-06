# Web Development

## HTTP Requests and Responses

1. What type of architecture does the HTTP request and response process occur in? 
 - The HTTP protocol is a request/response protocol based on the client/server based architecture where web browsers, robots and search engines, etc. act like HTTP clients, and the Web server acts as a server.

2. What are the different parts of an HTTP request? 
 - A **request line** contains the request method, the name of the requested resource, and the version of HTTP in use.
   - The request line can also contain query parameters, which the client can use to send data to the server.
 - **Headers** contain additional details about the requested resource. They are used to implement many actions with security implications, such as authentication and remembering user resources.
 - **Whitespace** is a blank line indicating the end of the request.

3. Which part of an HTTP request is optional? 
 - Request Body

4. What are the three parts of an HTTP response?
 - A **status line** contains the response status code and translation, such as `OK` or `Conflict`.

 - **Headers** contain additional information about the response, similar to response headers.

   - *Whitespace* (a blank line) separates the header from the response body that follows.  
 - A **response body** contains the resource requested by the client, all of the web code and styling that your browser uses to format the page.

5. Which number class of status codes represents errors?
 - 400 is client side / 500 is server side

6. What are the two most common request methods that a security professional will encounter?
 - `GET` and `POST` requests

7. Which type of HTTP request method is used for sending data?
 - `POST`

8. Which part of an HTTP request contains the data being sent to the server?
 - The request body

9. In which part of an HTTP response does the browser receive the web code to generate and style a web page?
 - The response body

## Using curl

10. What are the advantages of using `curl` over the browser?
 - It's not always possible to examine HTTP requests and responses through a browser:
    - Sometimes the tools you can use to send and receive HTTP requests are limited.
        - For example, when working through a container that has no user interface, you'll need a command-line tool to send and receive HTTP requests.
 - Cybersecurity professionals need to be able to quickly test HTTP requests in a way that can be automated, but also allows them to make adjustments as they work

11. Which `curl` option is used to change the request method?
 - `--request` / `-X`

12. Which `curl` option is used to set request headers?  
 - ` --head` / `-H`

13. Which `curl` option is used to view the response header?
 - `-I`

14. Which request method might an attacker use to figure out which HTTP requests an HTTP server will accept?
 - `OPTIONS`

## Sessions and Cookies

Recall that HTTP servers need to be able to recognize clients from one another. They do this through sessions and cookies.
 - 

Answer the following questions about sessions and cookies:

15. Which response header sends a cookie to the client?   - `Set-Cookie: cart=Bob`

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```

16. Which request header will continue the client's session?   - `Set-Cookie: cart=Bob`

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```

## Example HTTP Requests and Responses

Look through the following example HTTP request and response and answer the following questions:

**HTTP Request**

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What is the request method? 
 - `POST`

18. Which header expresses the client's preference for an encrypted response?
 - `Upgrade-Insecure-Requests: 1`

19. Does the request have a user session associated with it?
 - No

20. What kind of data is being sent from this request body?
 - `Content-Type: application/x-www-form-urlencoded`

**HTTP Response**

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

```

21. What is the response status code?
 - `200 OK`

22. What web server is handling this HTTP response?
 - `Server: Apache`

23. Does this response have a user session associated to it?
 - `Set-Cookie: SessionID=5`


24. What kind of content is likely to be in the [page content] response body?
 - `Content-Type: text/html` / Probable Webpage

25. If your class covered security headers, what security request headers have been included?
 - `Strict-Transport-Security: max-age=31536000; includeSubDomains`

## Monoliths and Microservices

Answer the following questions about monoliths and microservices:

26. What are the individual components of microservices called?
 - A **front-end server**, responsible for displaying webpages and styling them in a readable format. This server is also responsible for receiving and responding to HTTP requests.
 - A **back-end server**, for executing business logic and writing or reading corresponding data to and from a database. The back-end server knows how to interact with the database depending on the specific request received.
 - A **database**, used to store information about employees, such as their employee IDs and names. Critical and sensitive information is found in databases.

27. What is a service that writes to a database and communicates to other services?
 - API

28. What type of underlying technology allows for microservices to become scalable and have redundancy?
 - Containers

#### Deploying and Testing a Container Set

Multi-Container deployment:

29. What tool can be used to deploy multiple containers at once?
 - Playbook

30. What kind of file format is required for us to deploy a container set?
 - .YML

## Databases

31. Which type of SQL query would we use to see all of the information within a table called `customers`?
 - `SELECT * FROM customers`

32. Which type of SQL query would we use to enter new data into a table? (You don't need a full query, just the first part of the statement.)
 - `INSERT INTO`

33. Why would we never run `DELETE FROM <table-name>;` by itself?
 - It would delete the entire table.

---

### Bonus Challenge

![dog](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/14.%20Web%20Development/giphy.gif)
