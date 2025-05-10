### Introduction to Sockets

- **What is a Socket?**

  - A socket is an endpoint of communication between two processes.

  - They are used for network communication (e.g., client-server model).

  - Sockets can be used across different platforms and are essential for internet-based applications.

---

### **Types of Sockets**

- Constants represent the address (and protocol) families:
  - `AF_INET`: IPv4 address family
  - `AF_INET6`: IPv6 address family
  - `AF_UNIX`: Used to communicate between processes on the same machine
- Constants represent the socket types:
  - `SOCK_STREAM`: TCP (streaming) sockets
  - `SOCK_DGRAM`: UDP sockets

---

### Client vs Server Sockets

- **Client Socket**

  - Used by the application to initiate a connection.

  - Example: Your browser connecting to a web server.

- **Server Socket**

  - Listens for incoming connections.

  - Acts as a switchboard operator, creating new client sockets for each connection.

---

#### Workflow Between Server and Client

![socket-client-server](./unit-07-slides.assets/socket-client-server.webp)

---

#### Creating a Socket - Client

- When you use your browser to visit http://www.sait.ca, it did something like this:

```
# create an INET, STREAMing socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# now connect to the web server on HTTP port 80
s.connect(("www.sait.ca", 80))
```

- When the `connect` completes, the socket **`s`** can be used to send in a request for the text of the page. The same socket will read the reply, and then be **destroyed**. **Client** sockets are normally **only used for one exchange** (or a small set of sequential exchanges).

---

#### Creating a Socket - Server

- First, the web server creates a "server socket":

```python
# create an INET, STREAMing socket
serversocket = socket.socket(
    socket.AF_INET,
    socket.SOCK_STREAM
)

# bind the socket to a public host, and a well-known port
serversocket.bind((socket.gethostname(), 80))

# become a server socket
serversocket.listen(5)
```

---

### Creating a Socket - Server

- `bind()`: Binds the socket to a specific IP and port.

```python
serversocket.bind((socket.gethostname(), 80))
```

- `listen(5)`: Enables the socket to accept incoming connections. The maximum number of queued connections is 5.

```python
serversocket.listen(5)
```

---

### Server Accepting Connections

```python
while True:
    # accept connections from outside
    clientsocket, address = serversocket.accept()
    # Handle the client
```

- `accept()` blocks until a client connects.
- Returns a new socket object (`clientsocket`) and the client’s address.

---

### Server Accepting Connections

- This is *all* a “server” socket does. It doesn’t send any data. It doesn’t receive any data. It just produces “client” sockets.
- As soon as `clientsocket` is created, The server go back to listening for more connections.
- The two “clients” are free to chat it up - they are using some dynamically allocated port which will be recycled when the conversation ends.

---

### Using a Socket -  `send` and `recv`

```python
# Note: These methods work with raw bytes, not strings.
# send() sends bytes to the connected socket.
s.send(b"Hello, world!")

# recv() receives up to the specified number of bytes.
# When a recv returns 0 bytes, it means the other side
# has closed (or is closing) the connection. You will 
# not receive any more data on this connection.
data = s.recv(1024)

# Use encode()/decode() for text.
s.send(f"Hello, world!".encode())
s.recv(1024).decode()
```

---

### File-like Interface for Sockets

- **Advantages:**

  - Allows using `read()` and `write()` like file objects.

  - But remember to call `flush()` when writing to ensure data is sent immediately.

```python
import socket

s = socket.socket(...)
s.setblocking(False)
s.makefile("r")  # Read mode
s.makefile("w")  # Write mode
```

---

### Blocking vs Non-blocking Sockets

- **Blocking Sockets**

  - Default behavior.

  - `recv()` and `send()` will wait until data is available or sent.

- **Non-blocking Sockets**

  - Set using `s.setblocking(False)`.

  - `recv()` and `send()` may return immediately without data.

---

#### Handling Message Boundaries

- **Problem:**

  - `recv()` may return partial messages.

  - No built-in end-of-message signal.

- **Solutions:**

  - Fixed-length messages

  - Delimited messages (e.g., `\n`)

  - Length-prefixed messages

---

### Fixed-Length Message Example

```python
# A simple way to handle sending messages over sockets.
# Ensures all data is sent, even if it takes multiple calls.

def mysend(sock, msg):
    totalsent = 0
    while totalsent < len(msg):
        sent = sock.send(msg[totalsent:])
        if sent == 0:
            raise RuntimeError("Socket connection broken")
        totalsent += sent
```

---

### Closing Sockets Properly

```python
# If your socket just disappears without doing a close,
# the socket at the other end may hang indefinitely,
# thinking you’re just being slow.
s.close()
```

- **Best Practice:**

  - Always close sockets after use.

  - Python automatically closes sockets when they go out of scope, but this is not reliable.
  - Failure to close can lead to resource leaks and hanging connections.

---

### Activity

- A simple client and server implementation. The server will echo whatever it receives back to the client. [Echo Client and Server](https://realpython.com/python-sockets/#echo-client-and-server)
- File transfer is the process of copying or moving a file from one computer to another over a network or Internet connection. [How to Transfer Files in the Network using Sockets in Python](https://thepythoncode.com/article/send-receive-files-using-sockets-python)

---

### Key Takeaways

- Sockets enable communication between processes.
- Use `socket.socket()` to create a socket.
- Client sockets connect, server sockets listen and accept.
- Use `send()`/`recv()` or file-like interfaces for data transfer.
- Handle blocking vs non-blocking sockets carefully.
- Always close sockets properly.

---

### Sources:

- https://docs.python.org/3/howto/sockets.html
- https://realpython.com/python-sockets/
- https://thepythoncode.com/article/send-receive-files-using-sockets-python
- https://www.datacamp.com/tutorial/a-complete-guide-to-socket-programming-in-python
- https://docs.python.org/3/library/socket.html