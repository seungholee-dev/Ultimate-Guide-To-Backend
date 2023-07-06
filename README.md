# Ultimate-Guide-To-Interview

## MUST KNOW CS Backgrounds FOR IT INTERVIEWS


## Contributors 
<a href="https://github.com/seungholee-dev/Ultimate-Guide-To-Backend/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=seungholee-dev/Ultimate-Guide-To-Backend" />
</a>

### How to Contribute
- You can fork this repo and send Pull Request for any changes or anything new.

## Contents
1. [Network](#network)
2. [Database](#database)
3. [OS](#os)
4. [Algorithm](#algorithm)
5. [Security](#security)
6. [Architecture](#architecture)
7. [Design Patterns](#designparretns)
8. [Java](#java)
9. [Python](#python)
10. [Javascript](#javascript)

<br>

## 1. Network

<details>
<summary>What happens when you type <code>google.com</code> on browser?</summary>
  
1. **Browser Cache Check**: The browser first checks its cache for a DNS record to find the corresponding IP address of google.com. If found, it moves to step 8, otherwise it proceeds to the next step.
2. **Operating System Cache Check**: If the IP address is not found in the browser cache, the browser makes a system call to the operating system to fetch the IP address. The OS checks its cache, and if not found, it queries the local DNS resolver configured in your network settings.
3. **Local DNS Resolver Check**: If the local DNS resolver has the IP in its cache, it returns it, otherwise, it performs a recursive query to find the IP.
4. **Root Nameserver Query**: The local DNS resolver queries a root nameserver (.). The root nameserver responds with a delegation, which points to the .com TLD (Top-Level Domain) nameserver.
5. **TLD Nameserver Query**: The local DNS resolver then asks the .com TLD nameserver for the address of the google.com nameserver. The TLD nameserver responds with the IP address of Google's nameserver.
6. **Google's Nameserver Query**: The local DNS resolver then asks Google's nameserver for the IP address of google.com. Google's nameserver returns the IP address of google.com to the local DNS resolver, which then sends it back to the browser.
7. **Browser Cache Update**: The browser caches the IP address for google.com so it can skip the DNS process for subsequent requests.
8. **HTTP Request**: The browser initiates a TCP connection with the server at the IP address it got from the DNS process. The browser sends an HTTP GET request to the server, asking for the web page associated with google.com.
9. **Server Response**: The server processes the request, generates an HTTP response and sends it back to the browser. The response contains the HTML content of the web page.
10. **Page Rendering**: The browser receives the response and begins rendering the HTML content into a web page. During this process, the browser may find references to other resources (like images, CSS, JavaScript files) needed for the page. For each of these, the browser makes additional HTTP requests.
11. **Finish Loading**: Once all the referenced resources are loaded and the page is fully rendered, the browser signals that the page is loaded.
</details>


<details>
<summary> TCP vs UDP </summary>
Both are Happening in Transport Layer in OSI 7 Model

1. **Connection vs Connectionless**: TCP is a connection-oriented protocol, which means it establishes a connection before data transmission takes place. It involves a three-way handshake between the sender and receiver to open the connection, and another three-way handshake to close it. UDP is a connectionless protocol, which means it does not establish a connection before transmitting data, it just sends the data directly.
2. **Reliability**: TCP is a reliable protocol. It ensures that all data packets reach the destination in the correct order. It does this by assigning a sequential number to each packet, checking these numbers at the receiving end, and asking for retransmission if a packet is missing or arrives out of order. UDP does not provide such guarantees. It sends the packets and doesn't check or care whether they arrive or not.
3. **Flow Control**: TCP has flow control, which adjusts the data transmission rate according to the network conditions, such as congestion or traffic load. UDP does not have flow control and just sends packets without adjusting to network conditions.
4. **Error Checking**: Both TCP and UDP use checksums to ensure that the data is not corrupted during transmission. However, only TCP provides error recovery by retransmitting lost or corrupted packets.
5. **Speed**: Because UDP lacks the features mentioned above, it is generally faster and requires fewer resources than TCP. It is often used for real-time applications like streaming video or audio where it's not critical that all data arrives and in order.
6. **Data Ordering**: TCP ensures data is sent and received in the order it was transmitted, while UDP does not maintain ordering.
7. **Use cases**: TCP is typically used in applications where reliability is important, such as web browsing (HTTP/HTTPS), email (SMTP), file transfer (FTP), and secure shell (SSH). UDP is used where speed or efficiency is more important than reliability, such as in streaming audio or video (like YouTube or VoIP calls), online multiplayer games, or DNS lookups.
</details>


<details>
<summary>TCP 3 Way Handshake, 4 Way Handshake</summary>
In TCP (Transmission Control Protocol), a three-way handshake and a four-way handshake are used to establish and terminate a connection, respectively.

Here's a quick overview of each:

**Three-Way Handshake (Connection Establishment):**

The three-way handshake is used to establish a connection between a client and a server. This process synchronizes both the sender and receiver before data transmission starts.

1. **SYN(Client → Server)**: The client sends a SYN (synchronize) packet to the server to initiate a connection. This packet includes an initial sequence number from the client.
2. **SYN-ACK(Server → Client)**: The server acknowledges the client's SYN packet by sending back a SYN-ACK (synchronize-acknowledge) packet. The acknowledgment number will be the client's sequence number plus one. The server also sends its own SYN message with its initial sequence number.
3. **ACK(Client → Server)**: Finally, the client acknowledges the server's SYN-ACK packet by sending an ACK (acknowledge) packet. The acknowledgment number will be the server's sequence number plus one. This completes the three-way handshake.

**Four-Way Handshake (Connection Termination):**

The four-way handshake is used to terminate a connection between a client and a server. The process ensures that both parties have finished transmitting all the data.

1. **FIN(Client → Server)**: The client sends a FIN (finish) packet to the server to indicate that it has finished sending data.
2. **ACK(Server → Client)**: The server acknowledges the client's FIN packet by sending back an ACK (acknowledge) packet.
3. **FIN(Server → Client)**: Then, **when the server has finished sending all its data**, it sends its own FIN packet to the client. 
4. **ACK(Client → Server)**: Finally, the client acknowledges the server's FIN packet by sending an ACK packet. The connection is now fully terminated.

Note: While it's common to think of the client initiating the close process, keep in mind that either the client or the server can initiate the closing of a connection.
</details>

<details>
<summary> HTTP vs HTTPS </summary>
  
**HTTP (HyperText Transfer Protocol)** is the foundation of any data exchange on the Web. It's a protocol used for transmitting hypertext over the Internet. HTTP is not secure, so the information can be intercepted by third parties to gather data being passed between the two systems.

**HTTPS (HyperText Transfer Protocol Secure)** is the secure version of HTTP. It's used for secure communication over a computer network, and is widely used on the Internet. In HTTPS, the communication protocol is encrypted using Transport Layer Security (TLS) or, formerly, Secure Sockets Layer (SSL).

Here's a summary of some key differences:

1. **Security**: HTTP is unsecured, meaning that data is not encrypted and can be intercepted by attackers. In contrast, HTTPS is secure and uses encryption algorithms to hide the data in transit and prevent it from being read by attackers.
2. **Port**: By default, HTTP uses port 80 for communication, while HTTPS uses port 443.
3. **URL Scheme**: HTTP URLs start with **`http://`** and HTTPS URLs start with **`https://`**.
4. **Certificates**: HTTPS requires a SSL/TLS certificate to establish a secure connection. HTTP does not require any certificates.
5. **Performance**: HTTPS is slightly slower than HTTP due to the time it takes to set up the secure connection and the added overhead of encryption/decryption. However, the difference is often negligible and is usually outweighed by the benefits of security.
6. **SEO Ranking**: Search engines, like Google, tend to rank HTTPS websites higher than HTTP ones.

Given the growing concerns about user privacy and data protection, using HTTPS is increasingly becoming the standard for most websites, especially for those dealing with sensitive data, like e-commerce websites and online banking.
</details>

<details>
<summary>HTTPS</summary>
HTTPS (Hypertext Transfer Protocol Secure) works similarly to HTTP in that it follows a request-response protocol for communication between a client and server. However, it includes a layer of security via SSL/TLS protocols that encrypts the data in transit. Here's a simplified view of how HTTPS works:

1. **Client Hello**: The client (e.g., a web browser) starts by initiating a handshake process. It sends a "Client Hello" message to the server with its SSL/TLS version, the cipher suites it has available, and a random string of bytes known as the "client random."
2. **Server Hello**: The server responds with a "Server Hello" message. This message will contain the SSL/TLS version, the chosen cipher suite from those offered by the client, a "server random" string of bytes, and the server's digital certificate. The certificate includes the server's public key and is signed by a trusted Certificate Authority (CA). If the server requires a client certificate for mutual authentication, it will request it in this phase.
3. **Certificate Validation**: The client verifies the server's certificate with the CA to make sure it's valid and trustworthy. If the certificate is invalid or not trusted, the client will show a warning or terminate the connection. If it's valid, the client proceeds to generate a pre-master secret.
4. **Pre-Master Secret**: The client encrypts the pre-master secret with the server's public key (obtained from the server's digital certificate) and sends it back to the server.
5. **Shared Secret Generation**: Both the server and the client generate the master secret and session keys based on the pre-master secret. They are used for encryption and decryption of information during the secure session.
6. **Client Ready**: The client sends a message to the server, encrypted with the session key, to indicate it's ready to start the encrypted session. The server will decrypt the message using the session key, and if successful, it sends back an acknowledgment also encrypted with the session key.
7. **Secure Communication**: Now that the handshake process is complete, all subsequent data transferred between the server and client will be encrypted with the agreed session key. This includes the HTTP requests and responses.
8. **Connection Closure**: At the end of the session, the client or the server can initiate a closure of the session, and new keys will be required for future sessions.

So, the main difference between HTTP and HTTPS is this handshake process, which securely encrypts the data in transit. It ensures that even if the data is intercepted, it cannot be read without the unique session keys.
</details>

<details>
<summary> TLS, SSL </summary>
SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are cryptographic protocols designed to provide secure communication over a network. They are most commonly used to secure web traffic, but they can also secure other types of traffic.

SSL was developed by Netscape in the mid-1990s. TLS was introduced as a new version of SSL (SSL 3.1) by the Internet Engineering Task Force (IETF) in 1999, and has been updated several times since. The latest version as of my knowledge cutoff in September 2021 is TLS 1.3, which was published in August 2018.

Although TLS is the newer and more secure protocol, people often still use the term "SSL" in conversation and marketing, usually meaning the secure transport protocol in general, regardless of the actual version used.

Here's a brief overview of what these protocols do:

1. **Encryption**: SSL/TLS protocols encrypt the data being transmitted, which protects it from being read by anyone who might intercept the communication. This is crucial for sensitive data like passwords, credit card numbers, or any personally identifiable information.
2. **Authentication**: SSL/TLS uses certificates to authenticate the server in a connection (and optionally the client), ensuring that clients are communicating with the intended server, not a malicious one pretending to be legitimate.
3. **Integrity**: SSL/TLS provides a mechanism to check whether the data has been tampered with during transmission. This ensures the integrity of the data, meaning that it arrives the same way it was sent without any alterations.

The process of establishing a secure SSL/TLS connection involves a "handshake," which includes negotiating of security parameters, exchanging and verifying of certificates, and generating shared secret keys for encryption. Once the handshake is successfully completed, the communication between the client and server will be secure
</details>

<details>
<summary>GET vs POST </summary>
GET and POST are two different HTTP (Hypertext Transfer Protocol) methods (also known as verbs) that a client can use to request data from a server. The main differences between them are in how they carry the parameters and how they affect browser behavior.

**GET Method**

- The GET method is used to retrieve information from the server using a given URI (Uniform Resource Identifier).
- Parameters/data sent to the server is appended in the URL, usually as key-value pairs separated by ampersands. For example, **`http://example.com/page?param1=value1&param2=value2`**.
- Because data is sent in the URL, it's visible in the browser address bar, and can be bookmarked and logged in browser history. This makes it inappropriate for sending sensitive data, such as passwords.
- GET requests can be cached by the browser.
- There's a length restriction on the URL (which varies by browser), so the amount of data that can be sent using a GET request is limited.
- GET requests should only be used to request data, not to change the state of the server. They should be idempotent, meaning making the same request multiple times produces the same result.

**POST Method**

- The POST method is used to send data to the server to create/update a resource.
- The data sent to the server is stored in the body of the HTTP request, so it's not visible in the browser address bar, and can't be bookmarked or logged in browser history.
- POST requests can send much more data than GET requests, and there's no restriction on the data type.
- POST requests are not cached by the browser by default.
- POST requests may change the state of the server, and they are not required to be idempotent.

In general, if you're retrieving data or performing an action that doesn't alter the server's state, you would use a GET request. If you're sending data to the server to create or update a resource, you would use a POST request. However, there are other HTTP methods such as PUT, DELETE, PATCH, etc., that are used for more specific purposes in a RESTful API design.
</details>

<details>
<summary> PUT vs POST  </summary>
- POST is used to create a new resource, while PUT is used to update an existing one or create a new one at a specific location.
- POST does not have to be idempotent (meaning that making the same request multiple times may have different results), while PUT should be idempotent (making the same request multiple times has the same effect as making it once).
- With POST, the server decides the URI of the new resource, while with PUT, the client decides the URI.
</details>

<details>
<summary> What is RESTful </summary>
RESTful, or Representational State Transfer (REST), is an architectural style used in web services development. It is a set of constraints that provides a way of mapping HTTP verbs (GET, POST, PUT, DELETE, etc.) and CRUD actions (Create, Read, Update, Delete) that are performed on resources identified by URIs.

RESTful web services allow requesting systems to access and manipulate textual representations of web resources using a uniform and predefined set of stateless operations.

Key principles of REST include:

1. **Statelessness**: Each HTTP request happens in complete isolation. When the client makes an HTTP request, it includes all information necessary for the server to fulfill that request. The server will not store anything about the latest HTTP request the client made. It treats each request as if it was brand-new.
2. **Client-Server**: The client handles the user interface and user experience, and the server provides the data and makes it accessible to the client through a RESTful API. This separation of concerns supports the independent evolution of the client-side logic and server-side logic.
3. **Cacheability**: Because a stateless API can increase request overhead by handling large loads of incoming and outbound calls, a REST API should be designed to encourage the storage of cacheable data.
4. **Uniform Interface**: The method of communication between the client and the server must be uniform, meaning that the same protocol, such as HTTP, is used to interact with the resources in the REST architecture.
5. **Layered System**: A client cannot ordinarily tell whether it is connected directly to the end server or an intermediary along the way. Intermediary servers can improve system scalability by enabling load balancing and by providing shared caches.

RESTful services use HTTP methods to implement the concept of CRUD operations:

- GET is used to retrieve a resource;
- POST is used to create a new resource;
- PUT is used to update an existing resource;
- DELETE is used to delete a resource.

Each resource is identified by a specific URI (Uniform Resource Identifier), and that's why we say that RESTful services are "resource-based".

</details>

<details>
<summary> What is CORS </summary>

CORS stands for Cross-Origin Resource Sharing. It's a mechanism that allows many resources (e.g., fonts, JavaScript, etc.) on a web page to be requested from another domain outside the domain from which the first resource was served.

An example of where CORS is necessary: if a web application served from **`domain1.com`** tries to make a request for a resource on **`domain2.com`**, then the browser's same-origin policy would block the request, because it's trying to access a resource from a different domain. The same-origin policy is a security feature implemented in web browsers to prevent requests to different origins (domains, protocols, or ports) for security reasons.

CORS provides a secure way to allow one domain (the origin domain) to call APIs in a different domain. CORS works by adding specific HTTP headers that tell the browser that it's okay to allow a web application from one site to access the resources of a different site.

It is up to the server to specify the domains allowed to access its resources. The server can specify which methods (GET, POST, etc.) are allowed from which origin and can also specify other settings. If the server does not send the appropriate CORS headers back, the browser will block the request for security reasons.

It's important to note that CORS is a negotiated process. That means the web application asks the server if it's okay to perform certain actions, and then the server responds with the appropriate CORS headers to tell the application if it's allowed or not. This negotiation happens behind the scenes without any need for the user to be aware of it.

</details>


<details>
<summary> What is OSI 7 Layers and why we need it? </summary>
<br>

The OSI Model (Open Systems Interconnection Model) is a conceptual framework that standardizes the functions of a communication system or a network into seven distinct categories, known as layers. It was developed by the International Organization for Standardization (ISO) to understand and describe how different network protocols interact and work together to provide network services.

The seven layers of the OSI model are:

1. **Physical Layer**: The physical layer is all about the nitty-gritty details of physically transmitting data over networks. This can include specifics such as electrical voltages, signal timing, physical connectors, types of cables (like Cat 5e or optical), wireless radio frequencies, and more. Its job is to move individual bits of data from one node to another. It also defines how digital data is converted to electric signals or wireless signals and vice versa.
2. **Data Link Layer**: This layer is concerned with getting data across a specific link or channel, so it's here that we see the implementation of protocols like Ethernet for local area networks (LANs). The data link layer provides reliable transit of data across a physical network link by handling error detection and correction, and it also defines the protocol for device's MAC addresses which are used to identify machines on a network.
3. **Network Layer**: This layer is responsible for routing of packets across networks, and it's where IP (Internet Protocol) operates. The network layer manages the mapping between IP addresses and MAC addresses. It's responsible for packet forwarding, including routing through different nodes in the network. It also handles fragmentation and error detection.
4. **Transport Layer**: This layer is where end-to-end communication management takes place. It's responsible for delivery of the entire message from source to destination. The transport layer can handle issues like data integrity, error checking, and recovery. It also manages segmentation of data and reassembles segments into streams of data at the destination. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are common transport layer protocols.
5. **Session Layer**: The session layer establishes, maintains, and breaks the bidirectional sessions between end-user application processes. It sets up sessions between applications, manages data exchange, and provides dialog control between devices. This includes initiating opening and closing of connections and managing the interactions between computers (duplex, half-duplex, or full-duplex).
6. **Presentation Layer**: This layer serves as the data translator for the network. It's used for translating between network and application data formats. It formats or transforms data to be sent across a network in a way that the application on the receiving end can understand. This layer is also involved in data encryption and decryption, compression, and decompression.
7. **Application Layer**: This is the layer closest to the end-user. It's where the actual application-specific communication functions occur, like file transfers, email, and web browsing. The application layer is what enables software programs to send and receive information over the network. Protocols in this layer would include HTTP, SMTP, FTP, DNS, and more.

The reason we need the OSI model is that it provides a standard for different systems and devices (even those from different manufacturers) to be able to communicate with each other. It provides a common language and framework, so that different types of software and hardware can interoperate effectively.

The model also allows for modular engineering, where different layers can be developed and updated independently. It promotes understanding and helps describe how network protocols work together to provide network services.

</details>

<details>
<summary> What is TCP/IP 4 Layers </summary>

The TCP/IP model (also known as the Internet Protocol Suite) is a more streamlined model compared to the OSI model. It describes the basic protocols that make the internet work. The model gets its name from two of its most important protocols: Transmission Control Protocol (TCP) and Internet Protocol (IP).

The TCP/IP model has four layers:

1. **Network Interface Layer**: This is similar to both the physical and the data link layers in the OSI model. It describes the physical methods and protocols for transmitting and receiving data on a network. This layer can involve protocols and technologies like Ethernet, Wi-Fi, or DSL.
2. **Internet Layer**: Corresponds to the network layer of the OSI model. It's responsible for addressing, packaging, and routing functions. The most significant protocol at this layer is the Internet Protocol (IP). It defines IP addresses, which enable the network to route packets of data to the right destination.
3. **Transport Layer**: Similar to its counterpart in the OSI model, the transport layer is responsible for ensuring data gets from its source to its destination in the correct sequence and without errors. It's here that you'll find TCP (which provides reliable, ordered delivery of data) and UDP (which provides lower overhead, but less reliable delivery).
4. **Application Layer**: This combines the functions of the session layer, presentation layer, and application layer in the OSI model. It represents the level at which applications access network services. This layer includes high-level protocols like HTTP, FTP, SMTP, and more.

The TCP/IP model is focused more on the practical aspects of building and implementing a network, while the OSI model is more conceptually exhaustive. Today, the TCP/IP model is more commonly used in practice but the OSI model is still taught widely for its thoroughness and conceptual understanding of network protocols.

</details>

## 2. Database

<details>
<summary> What is ACID? </summary>

  ACID is an acronym used in the context of databases, which stands for Atomicity, Consistency, Isolation, and Durability. These are a set of properties that guarantee reliable processing of database transactions.

  **Atomicity**: This property ensures that a transaction (a series of operations) is treated as a single unit, which either all succeed or all fail. There's no intermediate state where some operations succeed and others fail. If a failure occurs at some point, then the transaction will be rolled back so that it appears as though no changes have been made at all.

**Consistency**: This property ensures that a transaction brings the database from one valid state to another. The database has certain integrity constraints, and the consistency property ensures that any transaction will bring the database from one state that adheres to the constraints to another state that also adheres to the constraints.

**Isolation**: This property ensures that concurrent execution of transactions leaves the database in the same state that would have been obtained if the transactions were executed sequentially. That means, each transaction is executed in isolation from other transactions.

**Durability**: This property ensures that once a transaction has been committed, it will remain committed even in the case of a system failure (such as a power outage or crash). This is usually achieved by storing the transaction data in non-volatile memory.

These properties are crucial for systems where the reliability of transactions is important, such as in banking systems where it is critical that transactions (like money transfers) aren't partially completed or lost.
</details>

<details>
<summary> Why use index in DB? </summary>

  Indexing is a data structure technique used in a database to improve the speed of data retrieval operations. Essentially, an index in a database is similar to an index at the end of a book.

When you search for data in a database without an index, the system has to go through every row in the database table until it finds the results—a process known as a full table scan. This can be very slow if your database contains millions or billions of rows.

To speed this up, you can create an index on a column or a set of columns. The database management system then maintains this index and keeps it sorted. When you need to find data, it can then use the index to find the data quickly, without having to scan the whole table. It does this by using algorithms like binary search or B-trees, which are much faster than a full table scan for large datasets.

However, indexes also have some drawbacks. They take up disk space (since the index data needs to be stored), and they slow down write operations (like INSERT and UPDATE), because the database needs to update the index every time the data is changed. So it's a trade-off—you use indexes to speed up read operations at the cost of slower write operations and more disk space.

Indexes can be of different types like B-tree, Bitmap, Hash, etc., and the type of index to use depends on the specific use case and the database system.

As a database administrator or developer, part of your job is deciding which columns to index and what type of index to use, in order to strike the right balance between read speed, write speed, and disk space.
</details>

<details>
<summary> What is Transaction? </summary>

  A transaction in a database is a single logical unit of work that consists of one or more related tasks. It is used to ensure data integrity and consistency. Transactions group a set of tasks into a single execution unit. Each transaction is treated as a single, indivisible logical unit of work, in which all commands must succeed in order for the transaction to be considered successful.

A typical example of a transaction is a bank transfer from one account to another. The transaction consists of several individual operations:

Checking if the source account has enough funds.
Deducting the money from the source account.
Adding the money to the destination account.
If any of these operations fail, the whole transaction should be rolled back - i.e., the database should revert to the state before the transaction started.

The basic stages of a transaction include:

Begin Transaction: When a transaction begins.
Execution: Where the changes are made during the transaction.
Validation/Commit or Rollback: If the transaction is successful, it is committed, making all changes permanent. If it encounters any error, it is rolled back, reversing all changes made during the transaction.
Transactions in databases obey the ACID properties: Atomicity, Consistency, Isolation, and Durability, as I explained in the previous response.
</details>

<details>
<summary>Transaction Isolation Levels</summary>
  Transaction Isolation Levels are a part of ACID properties (Atomicity, Consistency, Isolation, and Durability) and control the degree to which one transaction must be isolated from other transactions. They essentially control how and when the changes made by one transaction are visible to others.

Isolation levels are important because they help manage concurrency control, and can help to prevent common database issues like dirty reads, nonrepeatable reads, and phantom reads.

There are typically four transaction isolation levels, as defined in the SQL standard:

Read Uncommitted: In this level, a transaction may read data that has been modified by another transaction but not yet committed - often referred to as a "dirty read". This level has the highest level of concurrency but also the highest level of risk, as changes that aren't even final yet can be read.

Read Committed: This level guarantees that any data read was committed at the moment it was read. Thus, it prevents dirty reads. However, it does not prevent nonrepeatable reads or phantom reads, because the same data can be read multiple times within the same transaction, and there is no guarantee that the data will be the same for each read if other transactions are modifying the data.

Repeatable Read: This level guarantees that any data read cannot change; if a row is read multiple times, it will always display the same data. However, it does not prevent phantom reads, which occur when a new row that matches the original search criteria is added by another transaction.

Serializable: This is the highest isolation level. It guarantees that transactions occur in a completely isolated fashion; i.e., as if they were executed serially, one after the other. This isolation level prevents dirty reads, nonrepeatable reads, and phantom reads.

Remember, higher isolation levels provide more data consistency but reduce the level of concurrent access and can affect the system's performance due to increased locking on the data. Therefore, choosing the right transaction isolation level depends on the specific needs of your system regarding consistency and performance.
</details>

<details>
<summary>What is Normalization</summary>
  Normalization is a database design technique used to minimize data redundancy and avoid data anomalies, like insert, update, or delete anomalies. The process involves dividing larger tables into smaller, less redundant tables and defining relationships between them using foreign keys. The main goal of normalization is to add, delete, and modify data without causing data inconsistencies.

There are several stages of normalization, each called a "normal form." Here are the most commonly used:

1. **First Normal Form (1NF)**: Each table cell should contain a single value, and each record needs to be unique.
2. **Second Normal Form (2NF)**: It includes the rules of 1NF and additionally, it mandates that all non-key attributes should be fully functionally dependent on the primary key. In simpler words, if a column is not about the key, remove it.
3. **Third Normal Form (3NF)**: It includes rules of 1NF and 2NF, and also requires that all non-key attributes must only depend on the primary key. So, there should be no transitive dependency for non-prime attributes.
4. **Boyce-Codd Normal Form (BCNF)**: This is a stricter version of 3NF. Every determinant must be a candidate key.
5. **Fourth Normal Form (4NF)**: It proposes that no database table instance should contain two or more, independent and multivalued data describing the relevant entity.

While normalization can reduce redundancy and inconsistencies, it's not always the best strategy for every situation. Sometimes, denormalization (adding intentional redundancy to data) can improve read performance. As with many areas of database design, the correct approach depends on the specific use case.
</details>

<details>
<summary>What is Join?</summary
In relational databases, a join operation combines rows from two or more tables based on a related column between them. This allows you to query data from multiple tables as if the data were in one table. Here are the basic types of joins:

1. **INNER JOIN**: The INNER JOIN keyword selects records that have matching values in both tables. This is the most common type of join. If there are records in the first table that do not have matches in the second table, those records are not included in the result set, and vice versa.
2. **LEFT JOIN (or LEFT OUTER JOIN)**: The LEFT JOIN keyword returns all records from the left table (table1), and the matched records from the right table (table2). The result is NULL from the right side, if there is no match.
3. **RIGHT JOIN (or RIGHT OUTER JOIN)**: The RIGHT JOIN keyword returns all records from the right table (table2), and the matched records from the left table (table1). The result is NULL from the left side, when there is no match.
4. **FULL JOIN (or FULL OUTER JOIN)**: The FULL JOIN keyword returns all records when there is a match in either left (table1) or right (table2) table records. Essentially, it's a combination of a RIGHT JOIN and a LEFT JOIN. If there's no match, the result is NULL on either side.
5. **CROSS JOIN**: The CROSS JOIN creates a result set that is the number of rows in the first table multiplied by the number of rows in the second table if no WHERE clause is used along with CROSS JOIN. This type of join returns what's known as the Cartesian Product of the two tables.
6. **SELF JOIN**: A self join is a regular join, but the table is joined with itself.

Each of these joins allows for complex queries across multiple tables, enabling more intricate data relationships and insights. Different types of joins are used based on the specific data requirements of the query.
</details>

<details>
<summary>RDBMS vs NoSQL</summary>
  RDBMS and NoSQL are two different types of database management systems that are used for storing and managing data, each with its own strengths and weaknesses.

RDBMS (Relational Database Management Systems)

Structure: RDBMSs use structured data. They store data in tables, and these tables are linked to each other using foreign keys, hence the term "relational". Examples include MySQL, PostgreSQL, Oracle Database, and Microsoft SQL Server.

Schema: They have a predefined schema that the data must adhere to. Before you can store data, you have to define tables, specify their data fields and types.

ACID Properties: RDBMSs strictly follow ACID properties (Atomicity, Consistency, Isolation, Durability), which is a key aspect for transactional systems.

Scaling: RDBMSs are typically scaled vertically by adding more power (CPU, RAM, SSD) to an existing machine.

Best Use Cases: They are best used when dealing with structured data, data integrity is a must, or complex transactions are involved.

NoSQL (Non-Relational Databases or Not Only SQL)

Structure: NoSQL databases are designed to store unstructured or semi-structured data. They come in several types including document databases, key-value stores, wide-column stores, and graph databases. Examples include MongoDB (Document database), Redis (Key-Value), Cassandra (Wide-Column), and Neo4j (Graph database).

Schema: NoSQL databases are usually schema-less. This means that you can store different types of data in the same database, and even in the same collection or table.

BASE Properties: NoSQL databases follow BASE properties (Basically Available, Soft state, Eventual consistency), which allows for flexibility and scalability.

Scaling: NoSQL databases can be scaled horizontally by adding more servers to the existing pool.

Best Use Cases: They are best used when dealing with large amounts of data that doesn't fit well into tables, rapid development (due to the flexibility of schema-less design), or when the data is geographically distributed.

In essence, whether to use an RDBMS or NoSQL depends on the specific needs of your application, including the data structure, consistency requirements, scalability needs, and the type and volume of data you're dealing with.
</details>

<details>
<summary>Sharding vs Partitioning</summary>
  Partitioning is a database technique where a table is split into smaller pieces called partitions. Each partition is a part of the same database, usually on the same server, and is based on certain criteria like a range of values or a specific hash function.

Sharding is a method used to distribute data across multiple databases, potentially across multiple servers or data centers. Each shard holds a subset of the data and functions as a separate database. This is typically used for very large datasets and high traffic loads to improve performance and scalability.
</details>

<details>
<summary>CAP Theorem</summary>
CAP theorem is a fundamental principle in distributed database systems that states it's impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees:

Consistency: Every read from the database gets the latest (or a specified) data or an error. In other words, all nodes in a system see the same data at the same time.

Availability: Every request receives a non-error response, without guarantee that it contains the most recent write. In other words, the system is always operational and the data is available for access whenever needed.

Partition Tolerance: The system continues to operate despite arbitrary partitioning due to network failures. In other words, the system can sustain any amount of network failures without a system-wide failure.
</details>

