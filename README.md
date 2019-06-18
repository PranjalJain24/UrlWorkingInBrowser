# What happens when you type a URL in browser
This is a basic understanding on what happens when you type in a URL in browser and how the information is transferred to our computers through internet. A lot of stuff happens under the hood in the network to get an HTTP request from the browser to the server and then an HTTP response from the server back to the browser.

## Step by step process:-

### 1. Enter URL in address bar
When you press any key, the browser receives the event and tries to auto-complete. Depending on your browser's algorithm which is based on search history, bookmarks, cookies, and popular searches from the internet and if you are in private/incognito mode or not various suggestions will be presented to you in the dropbox below the URL bar. Suggestions keep on coming with every key pressed.

### 2. Parse URL and see if it is a URL or a search term?
The browser now has the information about protocol and resource contained in the URL (Uniform Resource Locator).
When no protocol or valid domain name is given the browser proceeds to feed the text given in the address box to the browser's default web search engine.

### 3. DNS lookup
We type the URL http://www.example.com in the web browser and press enter. This will instruct our browser to create an HTTP request to send to www.example.com. 
Our computer will now try to connect to www.example.com in TCP port 80 (the default HTTP port). First, it needs to create a TCP SYN segment to initiate the TCP connection which includes a random source port, destination port (80) and a flag (SYN).
This TCP segment is then encapsulated in an IP packet that contains the source IP (192.168.0.10) and the destination IP. For the destination IP, our computer goes to its DNS cache and looks for an entry containing www.example.com. 
In order to find the DNS record, the browser checks four caches: Browser, OS , router andISP. If it is present in cache and is fresh, goes to step where browser decodes response. 

### 4. DNS server initiates a DNS query to find the IP address of the server
Since it's cache is empty,we need to wait until we can get the IP address of www.example.com. For this DNS service is used to translate human-readable names into IP addresses. Our computer creates a DNS request that includes the type of request and the domain name to resolve.
This DNS request is then encapsulated in a UDP datagram whose header contains a random source port and the destination port. This datagram is then placed inside an IP packet whose header has the source IP address and the destination IP address.
We now want to send this IP packet but our computer doesn’t know where to send it. The computer looks at its route table to see which route matches the destination IP address.

### 5. TCP connection for data transfer:
After receiving the correct IP address it will build a connection with the server that matches IP address to transfer information for which internet protocols are used like TCP.
To transfer data TCP connection should be established by TCP/IP three-way handshake process:
* Client machine sends a SYN packet to the server over the internet asking if it is open for new connections.
* If the server has open ports that can accept and initiate new connections, it’ll respond with an ACKnowledgment of the SYN packet using a SYN/ACK packet.
* The client will receive the SYN/ACK packet from the server and will acknowledge it by sending an ACK packet.

### 6. The browser sends an HTTP request to the web server.
Now you need to transfer data. The browser will send a GET request asking for maps.google.com web page. If you’re entering credentials or submitting a form this could be a POST request. 

### 7. The server handles the request.
Request from the browser is sent to request handler by web server to read and generate a response. The request handler is a program that reads the request, its’ headers, and cookies to check what is being requested and also update the information on the server if needed. Then it will assemble a response in a particular format (JSON, XML, HTML).

The server breaks down the request to the following parameters:
* HTTP Request Method (either GET, HEAD, POST, PUT, DELETE, CONNECT, OPTIONS, or TRACE). In the case of a URL entered directly into the address bar, this will be GET.
* Domain, in this case - example.com.
* Requested path/page, in this case - / (as no specific path/page was requested, / is the default path).

### 8. The server sends out an HTTP response
The server response contains the web page you requested as well as the status code, compression type (Content-Encoding), how to cache the page (Cache-Control), any cookies to set, privacy information, etc.

### 9. The browser displays the HTML content 
It will render the bare bone HTML skeleton. Then it will check the HTML tags and sends out GET requests for additional elements on the web page, such as images, CSS stylesheets, JavaScript files etc. These static files are cached by the browser so it doesn’t have to fetch them again the next time you visit the page. At the end, you’ll see the page appearing on your browser.
