https://medium.com/@mamependasadio1/what-happens-when-you-type-https-www-google-com-in-your-browser-and-press-enter-32cf029e3967
What Happens When You Type https://www.google.com in Your Browser and Press Enter?

Have you ever wondered what happens behind the scenes when you type https://www.google.com in your browser and press Enter? This simple action triggers a complex chain of events involving networking, security, server architecture, and data. In this article, we’ll explore the journey of a single web request from your device to Google’s servers and back.

1. DNS Request — Finding the IP Address
The first step is translating the human-readable domain name www.google.com into an IP address that your computer can understand.

Browser cache: Checks if it has the IP stored.
OS cache: If not, your system asks the operating system.
DNS Resolver: If still not found, a request is sent to your configured DNS server (often provided by your ISP or a public DNS like 8.8.8.8).
Root → TLD → Authoritative DNS: The DNS request travels through multiple DNS servers until it finds the one authoritative for google.com.
Finally, the resolver returns the IP address (e.g., 142.250.191.36), and your browser can now reach the server.

2. TCP/IP — Establishing a Connection
Your browser now knows the IP address. Next, it opens a TCP connection using the TCP/IP protocol suite:

3-way handshake: SYN → SYN-ACK → ACK
This establishes a reliable connection over port 443 (used for HTTPS).
3. HTTPS and SSL/TLS — Securing the Connection
Since you’re using https://, the browser must secure the connection using SSL/TLS.

SSL Handshake:
The server provides a digital certificate issued by a trusted Certificate Authority (CA).
The browser verifies this certificate.
A shared encryption key is agreed upon to encrypt the communication.
All future traffic is encrypted, protecting it from eavesdropping or tampering.
4. Firewall — Protecting the Network
Before the request reaches Google’s servers, it passes through firewalls.

Firewall filters incoming requests to block malicious traffic.
Only safe traffic on allowed ports (like 443 for HTTPS) is forwarded.
5. Load Balancer — Distributing the Load
Google handles millions of requests per second. A load balancer ensures your request goes to the least loaded and geographically closest server.

It helps ensure high availability and scalability.
It can also terminate SSL to offload encryption tasks from backend servers.
6. Web Server — Receiving the Request
Your request arrives at one of Google’s web servers (e.g., Nginx or Apache), which:

Accepts the HTTP request.
Parses the URL and headers.
Passes it to the application server for dynamic content.
7. Application Server — Handling Logic
The application server (e.g., running Python, Java, Node.js) processes the logic:

Determines what you’re asking for.
Retrieves information from databases or services.
Generates a response (like HTML, JSON, etc.).
8. Database — Fetching Data
If the page requires user-specific or dynamic content, the application server will query a database:

Google uses advanced distributed databases like Bigtable or Spanner.
The database responds with the needed data (e.g., search results).
9. The Response — Getting Back to You
The application server sends the generated page to the web server, which:

Responds to your browser with a status code (e.g., 200 OK).
Sends the HTML, CSS, JS, and image files.
The browser then renders the page for you to see.

Summary Diagram
![What_happen_when_diagram](Images/infrastructure.png)

Conclusion
Typing a URL into a browser triggers a series of impressive technologies working together in milliseconds — from DNS lookups, firewalls, encryption, load balancing, and server responses. Understanding this journey deepens your appreciation of how the web functions and makes you a better engineer, capable of working across the stack.

Sources
What is a database
What’s the difference between a web server and an app server?
DNS record types
Single point of failure
How to avoid downtime when deploying new code
High availability cluster (active-active/active-passive)
What is HTTPS
What is a firewall
