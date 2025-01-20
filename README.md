# -MULTITHREADED-CHAT-APPLICATION
COMPANY: COTECH IT SOLUTION
NAME:POONAM SURYAWANSHI
INTERN ID:CTO8GBY
DOMAIN:JAVA PROGRAMMING
DURATION:4 WEEKS
MENTOR:NEELA SANTOSH

Task Description: Building a Multithreaded Client-Server Chat Application in Java
In this task, you are required to develop a multithreaded client-server chat application using Java Sockets. The primary objective of the project is to allow multiple users to communicate with each other in real-time through a central server, with each user running a client application. The server will handle the connections from multiple clients, managing communication and message distribution between them.

The key concept behind this project is the use of multithreading, which is essential for handling multiple client connections concurrently. Each client that connects to the server will be assigned a separate thread to handle its communication. This ensures that multiple users can interact with each other simultaneously, without blocking each other’s actions.

1. Multithreaded Server Design
The server’s primary responsibility is to accept incoming client connections, manage multiple clients at the same time, and facilitate message exchange between them. To achieve this, a multithreaded server design is required. When a client connects to the server, the server needs to spawn a new thread for that client. Each thread handles the communication with the specific client by reading messages from that client and forwarding them to the other clients connected to the server.

In Java, this is typically achieved using the Socket class for establishing the connection and ServerSocket for listening to incoming client connections. Once a client is connected, the server creates a new instance of a thread or a runnable object to handle communication for that particular client.

2. Socket Programming
Socket programming forms the backbone of this chat application. Sockets are endpoints for communication between two machines or processes over a network. In this case, we use TCP sockets (via Socket class) because they guarantee reliable and ordered data transmission, making them suitable for real-time chat applications. The server listens for client requests using ServerSocket, while each client creates a socket connection to the server using the Socket class.

Sockets allow bidirectional communication, which means both the server and the clients can send and receive data simultaneously. For this chat application, clients will send messages to the server, and the server will broadcast these messages to all other connected clients.

3. Multithreading for Concurrent Communication
Handling multiple clients simultaneously is one of the biggest challenges in networked applications. In the case of this chat application, we want to ensure that each client can independently send and receive messages without interfering with other clients. This is where multithreading comes into play. By creating a new thread for each client, the server can handle multiple clients concurrently.

When a client connects to the server, the server spawns a new thread that handles all communication for that client. This thread listens for messages from the client and forwards them to the other connected clients. Since each client has its own thread, all clients can communicate in parallel without blocking each other’s actions.

The threads are managed in such a way that each client can send a message without waiting for others to finish. The server uses a thread pool (or a similar mechanism) to efficiently manage resources, ensuring that each client’s message is handled properly without overloading the system.

4. Client-Side Design
The client in the chat application is responsible for connecting to the server, sending messages, and receiving messages from the server. Each client runs in its own separate process and interacts with the server through sockets. The client will have two main components:

Message Sender: The user types messages into a text interface, which are sent to the server.
Message Receiver: The client listens for incoming messages from the server and displays them on the screen.
For simplicity, the client is implemented to run in a console window, where the user can type messages, and the messages are displayed in real-time as they are sent by other clients. To ensure that the user can send messages and receive messages simultaneously, we will use multithreading on the client-side as well. One thread listens for incoming messages, while another handles the user input.

5. Broadcasting Messages
When a client sends a message, the server needs to forward it to all other connected clients. This can be achieved by maintaining a list or set of all active clients. When a message is received from any client, the server iterates over this list and sends the message to every other client. This process ensures that all clients receive the message and that the chat feels real-time.

6. Message Formatting and Display
The message sent by each client is usually in plain text format, but it can be formatted in a way that is easy to read and identify which client sent the message. For example, the server can prepend the username or IP address of the sender to the message, making it clear who the message is coming from.

Each client will display these messages in a structured format, either in the terminal or a GUI window. The client will be designed to show incoming messages in real-time, so the user can see when someone else sends a message while they are typing.

7. Error Handling and Connection Management
In any network application, proper error handling is crucial to ensure a smooth experience for users. This includes handling scenarios such as:

Client Disconnecting: The server should handle the case where a client disconnects unexpectedly and remove the client’s handler from the list.
Message Format Errors: If a message from a client is improperly formatted or corrupted, the server should be able to gracefully handle it without crashing.
Network Failures: The server should deal with potential network interruptions or connection timeouts and provide appropriate error messages to clients.
Additionally, connection management includes limiting the number of concurrent clients and managing the resources efficiently so that the server does not become overwhelmed.

8. Implementation Challenges
The task of building a multithreaded chat application presents several challenges:

Concurrency: Ensuring that each client’s communication is handled concurrently without blocking other clients is a fundamental challenge. This can be overcome by using threads and synchronization techniques.
Synchronization: If multiple threads are accessing shared resources (e.g., a list of clients), synchronization must be used to avoid race conditions or inconsistent state.
Scalability: The system should be able to handle a large number of clients simultaneously. This requires efficient memory management and thread management.
Network Latency: In real-time communication applications like a chat system, minimizing network latency is essential to provide a smooth experience for the users. Techniques such as compression, batch processing, and asynchronous communication can help reduce delays.
9. Extending the Application
Once the basic functionality is implemented, the application can be extended with additional features:

User Authentication: Clients could log in with usernames and passwords to identify themselves in the chat.
Private Messaging: Allow clients to send private messages to specific users instead of broadcasting them to everyone.
Graphical User Interface (GUI): A GUI can be implemented to provide a more user-friendly experience, such as a chat window with input fields and message boxes.
File Sharing: Add the ability for clients to send files, images, or other attachments.
Conclusion:
This multithreaded client-server chat application provides an essential introduction to network programming and concurrent programming. By using Java sockets and multithreading, the application ensures that multiple clients can communicate in real-time without blocking each other. This task is not only a valuable exercise in understanding the fundamental concepts of client-server architecture but also in working with multithreading, networking, and real-time communication. With further enhancements, this chat application can become more sophisticated and feature-rich, providing a scalable platform for real-time messaging.

OUTPUT:
Server Terminal:
Server started on port 12345
New client connected: /127.0.0.1
New client connected: /127.0.0.1
Received: Hello from Client 1
Received: Hi, Client 1! This is Client 2

Client1 Terminal:
Connected to server
Hello from Client 1  [Sent by Client 1]
Hi, Client 1! This is Client 2  [Broadcast message from Client 2]

Client2 Terminal:
Connected to server
Hi, Client 1! This is Client 2  [Sent by Client 2]
Hello from Client 1  [Broadcast message from Client 1]








