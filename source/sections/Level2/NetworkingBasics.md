# Networking Basics

<!-- TOC -->

- [Networking Basics](#networking-basics)
    - [Networking Basics](#networking-basics-1)
    - [RFCs](#rfcs)
    - [IP, Internet Protocol](#ip-internet-protocol)
    - [IP Address](#ip-address)
    - [DNS Domain Name System](#dns-domain-name-system)
    - [TCP Protocol](#tcp-protocol)
    - [UDP Protocol](#udp-protocol)
    - [HTTP](#http)
        - [HTML Documents](#html-documents)
        - [HyperLinks](#hyperlinks)
        - [Requests](#requests)
        - [Communication](#communication)
        - [Other Resources](#other-resources)
    - [HTTPS](#https)
    - [HTTP/2](#http2)
        - [Multiplexing](#multiplexing)
        - [Headers Compression](#headers-compression)
        - [Server Push](#server-push)
        - [Binary Communication](#binary-communication)
    - [HTTP Request Example](#http-request-example)
        - [Analyzing the URL Request](#analyzing-the-url-request)
        - [DNS Lookup Phase](#dns-lookup-phase)
        - [TCP Request Handshaking](#tcp-request-handshaking)
        - [Sending the request](#sending-the-request)
        - [The response](#the-response)
        - [Parse the HTML](#parse-the-html)
    - [Websockets](#websockets)

<!-- /TOC -->

## Networking Basics

* Network is built as a series of layers that start from the very low level information exchange protocols called the Physical Layer
* Physical layer contains information for encoding and signaling of data
* The Data Link Layer includes protocols like Wi-fi and defines more protocols that provide data framing, addressing, error detection, etc.
* Higher level stacks upon each other to provide higher level functionality
* Web is built upon stack of protocols called TCP/IP
* IP sits on the Network level
* TCP and UDP sit at Transport level
* HTTP, HTTPS, Websockets are on the Application layer 


## RFCs

* The network protocols are defined by things called RFCs (Request for Comments)
* RFCs are community driven documents that undergo heavy revision before publication and define the official protocols to be standards for people that create software implementations

## IP, Internet Protocol

* IP is the foundation of the internet
* IP is defined to create a communication channel between two computers over the network
* The protocol defines datagrams which is a way to organize the data
* Datagrams have 2 parts:
    1. Header - Metadata about the payload, size, authentication, id number on fragment, source and destination IP address
    2. Payload - Information to transfer (the data)
* When data is transferred from one computer to another, the data is split into fragments where the receiver rebuilds the complete package using the numbering
* This is because the packets that are sent are connectionless, meaning they can take many different routes based on what nodes fail or which route is faster. Since the packets can come out of order, there needs to be a way to rebuild it in the correct order
    * Intermediate nodes can dynamically alter which next node to send the package to so not all of the packages can arrive at the same time
* If all the packets don't arrive then they are all thrown out and the packages need to be resent
* Each node in the network (computer) is defined with an IP Address

## IP Address

* In TCP/IP networks, the nodes are identified using IP Addresses
* IP addresses are 4 8-bit numbers separated by dots and correspond to a computer (node) id in a network
* Each number ranges from 0-255
    * Ex. 212.21.4.28
* Everytime the computer connects to a network, a local IP address is created for that computer
* This means that without some sort of method such as Port Forwarding, the IP address cannot be reached from outside the network

## DNS Domain Name System

* Domain Names map a public IP address to a certain String
    * Ex. google.com
    * Allows for changing the server IP address and company used to host the website without having to tell all the users what new IP address to go to
* There is a DNS (Domain Name System) that maps domain names to IP addresses
* The DNS is essentially a network of servers and home routers are already pre-configured to reach a specific DNS
* The DNS servers received requests sent by the computer and then properly route to their parent DNS 
* Overall, the system is like a tree where the root DNS is at the top and it knows the IP Addresses of the DNS servers below it which are in charge of the IP addresses for extensions such as .com, .gov, .org, etc.
* Then the DNS servers who are in charge of the extensions know the IP address mappings of the domains under it
* This process trickles down to get the specific IP address of the server that you are fetching the request from

## TCP Protocol

* TCP is the transmission control protocol
* TCP, unlike IP and UDP, is connection oriented; this means that before transmissions can happen, a connection must be established and the data is sent in little packets
* TCP has a process called a handshake when sending data
* TCP's main benefit is reliability, the protocol ensures that all of the data is correctly sent or it fails and the process has to restart
* Connections happen from process to process where processes are called ports
* Ports are associated with an IP address and correspond to certain processes on that IP address
    * Ex. localhost:8080, corresponds to the IP address associated with localhost, with process 8080
* Some processes like HTTP and HTTPS have their own default ports, which is why when typing in the URL, the port does not need to be specified

## UDP Protocol

* UDP is the user datagram protocol
* Unlike TCP, UDP is transfer based meaning it is connectionless
* This means that it is technically faster than TCP as there are less packets that need to be sent
* Hoewver, UDP is more unreliable than TCP because there is nothing built into the protocol that ensures that all the data has been sent or received correctly
    * Some higher level process that utilizes UDP would have to create this reliability
* UDP also uses ports and is the base for the next HTTP, HTTP/3

## HTTP

### HTML Documents

* HTTP was created as a protocol to not only transfer files but also HTML documents in a fail-proof way
* HTTP is not secured but a later version, HTTPS, is
* HTTP is a language for web browsers (clients) to be able communicate with web servers

### HyperLinks

* In web browsers, the documents can contain links that point to other documents
    * When creating the links, the first part, server IP and protocol is the same, however anything appended after the address is the relative document path
    * Ex. https://flaviocopes.com/courses
        1. https is the protocol
        2. flaviocopes.com is the domain name
        3. courses is the document relative path in the server

### Requests

* Requests require a method (verb), address, and relative pathing or URL
    * Ex. GET /axios/ flaviocopes.com
* All requests have headers - key : value pairs that are sent to communicate metadata and information to the server
    * Required header is Host (the domain name that is being requested)

### Communication

* The HTTP protocol is stateless, meaning each request is assumed to be independent of each other and any prior request is meaningless
    * This makes the server faster as it doesn't need to keep track of the state of the client
    * This made HTTP the standard as it was quicker and had less overhead than that of other protocols but was also fail-safe as requests are either completed in its entirety or not failed
* Communication happens in the following way:
    * ```
        GET /a-page HTTP/1.1
        Host: google.com
    * Here we see that the request method is "GET", the URL is specified, and the protocol
    * Below is the headers where we defined the "Host"
* Can test with **telnet**
    * Command line for testing connections with servers
    * Doesn't work with HTTPS protocols since it is unencrypted, but can encrypt with SSL

### Other Resources

* HTTP can give back any type of file not just HTML
    * CSS, JS, IMG, SVG, etc.
* Usually, an HTTP request is made to get the document HTML which contain links to other resources such as CSS and JS files
    * These links are used in additional HTTP requests to get the necessary files

## HTTPS

* Typically in an HTTP request, two trips are made
    * One from the client to server requesting the resources
    * One from the server to client giving back the requested resources
* With more content and links inside the HTML document, additional HTTP requests have to be made over the Client/Server connection
* In all of these connections, someone can listen in and also receive the packets of data if the connection is not encrypted
* HTTPS was made just for that purpose, to encrypt the entire connection from client to server
* In HTTPS everything is encrypted from the query parameters to the headers except for the domain name and the port
* This may require additional computation to encrypt the request and also decrypting the request but HTTP/2 is faster due to:
    * Header compression
    * Resource Multiplexing
    * Server push - push more than one resource, HTML, CSS, and JS in one response

## HTTP/2

* HTTP/2 is the latest, standardized version of the HTTP protocol
* It is completely backwards compatible and aimed to reduce the inefficiencies of HTTP/1.1
* It has the following new features:
    * Request and response multiplexing
    * Header Compression
    * Server Push
    * Binary Communication

### Multiplexing

* Before only one request could be served per TCP connection
* Now HTTP/2 allows for request/response multiplexing over a single TCP connection, allowing the server to serve multiple requests over a single connection
* Made these obsolete:
    * Image sprites (packing multiple images into one to make one request)
    * Domain sharding (hack to prevent browser limit of simultaneous connections to same domain)

### Headers Compression

* HTTP/2 compresses the header information which makes it much lighter and require less data

### Server Push

* Allows the server to push multiple responses for a single request
* If the server gives back an HTML document as a response, most likely, there are CSS and JS files that are being requested as well, so it will send those as well
* Server can decide to send resources that may be needed in future requests and have the client cache it

### Binary Communication

* HTTP/2 uses binary communication which is easier to parse, more compact, and less error prone

## HTTP Request Example

<span style="color:orange">**Should Make Blog Post / Visualization diagram**</span>

### Analyzing the URL Request

* When something is typed into the URL address bar, if not all the information is provided, it is automatically filled out
    * Ex. flaviocopes.com, browser will by default prepend http://www to it, making it http://www.flaviocopes.com

### DNS Lookup Phase

* There is a whole process to get the host server IP address
    1. Checks the local DNS cache to find the domain
    2. If not found, the browser uses the gethostname POSIX system call to get the host information
    3. The system call first checks /etc/hosts to see if the system provides the information locally (makes it a localhost)
    4. If not there (which is most cases) it makes a request to the DNS server provided by the ISP using the UDP protocol
    5. The ISP DNS server can have the domain in its cache, but if it doesn't it goes to the **root DNS server** which resolves the "www" part of the URL
    6. The root DNS server knows the IP address for the DNS servers that resolve every type of extension (.com, .gov, .edu, etc) called **top level DNS servers**
    7. After matching the extension to the right top level DNS server, the request is forwarded to that top level DNS server
    8. The DNS resolver then caches the root DNS server so it doesn't have to look it up again
    9. The top level DNS server then has a list of registered domain names and their IP addresses
    10. When buying a domain name, the domain registrar sends the top level DNS server the server name and IP address, the hosting provider provides a bunch of DNS servers to host the website
    11. These DNS servers have the associated domain name to the IP address and thus the corresponding IP address is found and returned

### TCP Request Handshaking

* Now that the server IP address is found, the browser can initiate a TCP connection to the IP address
    * This connection requires a bit of sending data back and forth before being able to send data

### Sending the request

* Requests are plain text documents written in a certain precise way:
* The request has 3 parts:
    1. The request line 
        * Sets (on a single line)
            * HTTP method
            * Resource locationo
            * Protocol Version
        * Ex. ``` GET / HTTP/1.1 ```
    2. The request header
        * Sets key : value pairs that contain information about the request, terminated by a blank line
        * 2 mandatory fields:   
            1. Host - Domain name to target
            2. Connection - Whether to keep connection open or closed after
        * Ex. 
```
Host: flaviocopes.com 
Connection: close
```
    3. The request body
        * Contains data in the form of JSON
        * Ex. 
``` 
{
    data: {
        some_text
    }
}
```

### The response

* Server processes the HTTP request and sends back a response
* Starts with status code and a message
    * Ex. ``` 200 OK ```
* The response also includes the request headers and the response body

### Parse the HTML

* The browser, which now has the requested HTML will parse it and repeat the same process (for HTTP/1.1) for CSS files, images, JS, etc.

## Websockets

* Websockets are an alternative to the HTTP protocol
* Unlike HTTP, websockets are a long-lived connection meaning once the connection is open and a message is sent, it usually stays open
* Some differences between HTTP and Websockets
    * Server can send data to client without the client requesting it
    * Client and server can talk to each other simultaneously
    * Low latency communication since little data overhead is needed to send a request
* Websockets are better for long-lived and real-time connection
* HTTP is better for occasional data exchange and interactions initiated by the client
* HTTP is simpler to implement and Websockets require a bit more sophistication
* Secured protocol for Websockets is wss://, ws:// is the unsafe version
