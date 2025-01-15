# Medium article and flowchart

## Behind the Scenes of Web Infrastructure

### Exploring How Each Layer Powers Your Online Experience / A Step-by-Step Breakdown

> What happens when we type https://www.google.com and press enter ?

[Flowchart of web infrastructure](https://github.com/Bomays/holbertonschool-network/blob/12e2f9f1b0fc743e06a0dd18bcacb67f3a9ea66b/what_happens_when_your_type_google_com_in_your_browser_and_press_enter/Image/Web%20infrastructure%20process.png)


    DNS Request
    The Domain Name System (DNS) is the“phonebook of the Internet.”

    Paul Vixie, a prominent internet engineer and one of the key contributors to the development of the Domain Name System compared DNS with the “internet phone book” in various discussions and writings, because, like a phone book helps you look up a person’s phone number based on their name, DNS helps you look up the IP address of a website based on its domain name.

Here’s a more detailed look at the process:

    Your browser first checks its own cache to see if it has recently looked up the IP address for www.google.com.
    If not found in the browser cache, it checks the operating system’s DNS cache ( Operating System Cache).
    The next stop is the Router’s Cache.
    If still not found, your computer queries your ISP’s DNS server

    IP address is a unique numerical label assigned to each device connected to a network, allowing it to communicate with other devices over the internet or local network.

    Cache is a temporary storage area where data is stored for quick access. It holds copies of frequently accessed or recently used data so that it can be retrieved faster the next time it’s needed

    ISP is the company that provides you access to the internet.

    The Server is a computer or system that provides resources, services, or data to other devices (clients) over a network as web servers, file servers, and database servers.

    If your ISP’s DNS server doesn’t have the IP address for the website you’re trying to visit, it starts a recursive search to find it
    Once found, the IP address is cached at various levels for future quick access.

    Recursive search detailed:

    > It asks first the main “root” servers that know where to find information about different website types (like .com .org .net .fr)
    > Then the .com top-level domain (TLD) nameservers: It asks the servers that manage .com websites (since you’re trying to visit a .com website)
    > Finally, Google’s authoritative nameservers: It reaches the specific server for the website you’re looking for (like Google’s server) to get the exact address (IP) needed to visit the website.

2. TCP/IP

Transmission Control Protocol/Internet Protocol (TCP/IP) is the fundamental suite of protocols that the Internet is built on. It allows for both reliable data transfer (TCP) and proper routing (IP) over it.

    Three-Way Handshake is a TCP process used to establish a reliable connection between two devices (like the computer and Google’s server). It ensures that both are ready to exchange data. TCP ensures reliable communication by making sure that data packets are delivered correctly, in the right order, and without errors.

    Three-Way Handshake detailed process:

    > The computer sends a request, called a SYN packet, to Google’s server, asking to start a connection.
    > Google’s server responds, agreeing to the connection with a SYN-ACK packet.
    > Your computer confirms the connection by sending an ACK packet back.

    IP Routing: IP handles how data is sent across the internet by breaking it into smaller packets. Each packet has source and destination IP addresses, so routers can forward them to the right destination.
    IP focuses on finding the best path for the data to travel, but it doesn’t guarantee that packets will arrive in order or that they won’t be lost during the process.

    IP Routing detailed process:

    > Data is split into smaller pieces called packets (as we saw above with TCP).
    > Each packet has the address of where it’s coming from (computer, tablet or whatever you prefer!) and where it’s going (Google’s server).
    > Routers (devices that direct data on the internet) use these addresses to send the packets to the right destination.

    Error Checking and Ordering: The system makes sure all packets are received and in the correct order.
    If any packets are lost or delayed, they are sent again to ensure everything arrives correctly.

3. Firewalls
Firewalls act as a barrier between trusted internal networks and untrusted external networks.

    Firewalls detailed process:

    > Firewalls look at each piece of data (packet) and decides whether to allow or block it based on predefined rules. It is called Packet Filtering

    > Then arrives a Stateful Inspection where they track the ongoing connections between devices, ensuring that the data follows the correct path and state.

    > After, the Application Layer Filtering happens filtering data based on specific applications or services (like web browsing or email).

    > Finally the work of Next-Generation Firewalls (NGFW) which are advanced firewalls that do more than just block data, they can inspect the data deeply and protect against attacks.

4. HTTPS/SSL
HTTPS (HTTP Secure) uses SSL/TLS protocols to provide encrypted communication.

    HTTP (HyperText Transfer Protocol) is a protocol used for transferring data, like web pages, between a web server and a browser. It defines how requests and responses are made on the web.

    SSL/TLS Handshake (Secure Connection Setup) is the process where a browser and server establish a secure connection. They exchange information, verify the server’s identity with a certificate, agree on encryption methods, and create a shared key to encrypt all communication.

    SSL/TLS Handshake detailed process:

    > Client Hello: The browser sends information about the secure connection methods it supports.
    > Server Hello: The server picks the best secure connection method to use.
    > Certificate Exchange: The server sends its security certificate to prove its identity.
    > Key Exchange: Both browser and server agree on a secret key to use for encryption.

    Certificate Validation:

The browser checks if the server’s certificate is trusted and not expired.
It also makes sure the certificate’s digital signature is valid, confirming the server’s identity.

    What is an SSL certificate:

    A certificate is a digital document used to prove the identity of a website and establish trust. It contains the website’s public key, domain name, and information about the certificate authority that issued it.

    Encryption:

After everything is verified, all communication between your browser and the server is encrypted using the agreed secret key to keep it secure.

5. Load Balancer
Load balancers distribute network traffic across multiple servers.

What they use:

    Various algorithms/methods used to distribute traffic as:

    Round Robin method that distributes requests evenly across servers in a sequential order.

    Least Connections are a method that directs traffic to the server with the fewest active connections.

    IP Hash method that routes traffic based on the client’s IP address, ensuring consistent connection to the same server.

    Load balancers regularly check if servers are responsive, it is a process called Health Check
    Session Persistence process ensures a user’s session stays on the same server.
    SSL Termination is a process that handle SSL decryption to offload this task from web servers, it does not always occurs especially when an end-to-end encryption is required as for healthcare and finance industries. In this case load balancer performs SSL passthrough, forwarding encrypted traffic directly to the servers.

6. Web Server
Web servers handle HTTP requests and serve web content.

    During the Request Parsing the server parses the HTTP request headers It reads and understands the details of the incoming HTTP request.
    Then URL Mapping, as it tells, maps the URL to the correct resource. It figures out which resource (like a web page or file) matches the requested URL.
    In one hand if the request is for something simple as Static Content, like a file (HTML, CSS, JavaScript, or images), the server sends it directly.
    On another hand for Dynamic Content if the request needs processing (like for a database query), the server passes it to an application server to generate the response.
    Finally, during the Response Headers the server adds important details (like content type or status) to the response before sending it back to the client.

    A Query is a request for information or data, often sent to a database or server to retrieve specific results.

7. Application Server
Application servers run the core business logic of web applications.

    What is the Core Business Logic:

    It refers to the essential rules and processes that define how a web application operates and handles its tasks.

    This includes executing the application’s code, performing calculations, processing data, and making decisions based on business requirements.Essentially, it’s the part of the application that makes it function according to the business goals.

    First the application server looks at the request from the web server to understand what is being asked, it is the Request Processing
    Then it runs and executes the application code (written in languages like for example C, JavaScript, Python, PHP) for the Business Logic process.
    When done, it goes on Data Processing to performs any calculations or manipulations needed on the data.
    It makes External Service Calls reaching out to other services (inside or outside the system) for additional data or actions.
    Finally it is time to the Response Generation! After processing everything, it prepares the results to send back to the web server.

8. Database
Databases store and manage the application’s data.

    It Receives and interprets SQL or NoSQL queries during the Query Processing
    Efficiently fetches requested data from storage for the Data Retrieval process, using Indexing to speed up data retrieval.

    It Ensures data integrity during concurrent operations with the Transaction Management and implements various Caching mechanisms to improve performance.

CONCLUSION

I hope this breakdown provides a clearer understanding of the complex processes involved in loading a web page, a process that we all rely on daily.

However, this process doesn’t always go smoothly. Sometimes, it fails, and we’re left frustrated, whether it’s not being able to watch a video we have been eagerly waiting for, or struggling to buy an important car part online when our car won’t start (this happened to me just a few days ago).

When things go wrong, it’s often due to a Single Point of Failure (SPOF). Perhaps the infrastructure wasn’t designed to be as resilient as it should be. In fact, robust design and fault-tolerant architectures (those that minimize SPOFs) are crucial for providing the best possible user experience.
Focus on SPOFs

    Single Points of Failure (SPOFs) are critical parts of a system that, if they fail, can cause the entire system to fail. In web infrastructure, SPOFs can severely impact both system reliability and availability

To illustrate this concept, i have created a repository containing flowcharts made with Mermaid and accompanying documentation. These visual tools highlight key web infrastructure concepts, including how simple and vulnerable setups evolve into more complex and resilient systems. This progression is vital for modern web applications.

For further exploration, including brief topics like SPOFs, database replication, and component separation, you can check out my repository from a Holberton School course where I actually study full-stack development fundamentals