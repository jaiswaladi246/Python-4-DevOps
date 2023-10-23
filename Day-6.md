# Day-6 | Basic Networking Concepts


### 1. **What is Networking?**

Networking involves the practice of connecting multiple computing devices together for the purpose of sharing resources, information, and services. It enables communication between devices like computers, servers, smartphones, and more.

### 2. **IP Address and Subnetting**

- **IP Address**: An IP (Internet Protocol) address is a unique identifier assigned to each device on a network. It can be either IPv4 (e.g., 192.168.1.1) or IPv6 (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334).

- **Subnetting**: Subnetting involves dividing an IP network into multiple sub-networks to improve performance and security. It helps in efficiently utilizing IP addresses.Subnetting is the process of dividing an IP network into sub-networks to improve performance and security. It involves creating smaller, more manageable network segments. Let's go through an example of subnetting an IPv4 address.

**Example:**

Suppose we have the IP address `192.168.0.0` with a subnet mask of `255.255.255.0` (or `/24` in CIDR notation).

1. **Understanding the Subnet Mask:**
   - The subnet mask `255.255.255.0` means that the first 24 bits are fixed for network identification, and the remaining 8 bits are available for host addresses.
   - This provides us with 2^8 (256) possible host addresses within this subnet.

2. **Dividing the Subnet:**
   - Let's say we want to divide this subnet into four smaller subnets.

3. **Determining the New Subnet Mask:**
   - Since we're dividing the subnet into 4 equal parts, we need to borrow 2 bits from the host part for the network part. This gives us a new subnet mask of `255.255.255.192` (or `/26` in CIDR notation).

4. **Calculating Subnet Ranges:**
   - With the new subnet mask, each subnet will have 64 addresses (2^6).
   - We'll have 4 subnets: `192.168.0.0/26`, `192.168.0.64/26`, `192.168.0.128/26`, and `192.168.0.192/26`.

   - **Subnet 1 (192.168.0.0/26):**
     - Network Address: `192.168.0.0`
     - Usable Host Range: `192.168.0.1 - 192.168.0.62`
     - Broadcast Address: `192.168.0.63`

   - **Subnet 2 (192.168.0.64/26):**
     - Network Address: `192.168.0.64`
     - Usable Host Range: `192.168.0.65 - 192.168.0.126`
     - Broadcast Address: `192.168.0.127`

   - **Subnet 3 (192.168.0.128/26):**
     - Network Address: `192.168.0.128`
     - Usable Host Range: `192.168.0.129 - 192.168.0.190`
     - Broadcast Address: `192.168.0.191`

   - **Subnet 4 (192.168.0.192/26):**
     - Network Address: `192.168.0.192`
     - Usable Host Range: `192.168.0.193 - 192.168.0.254`
     - Broadcast Address: `192.168.0.255`

   - **Note:** The first address in each subnet is reserved for the network address, and the last address is reserved for the broadcast address.

This is a basic example of subnetting. In practice, subnetting becomes more complex when dealing with different subnet masks, VLSM (Variable Length Subnet Masking), and routing between subnets. Understanding subnetting is essential for network administrators and engineers.

### 3. **MAC Address**

- A MAC (Media Access Control) address is a hardware address assigned to a network interface card. It's unique to each device and is used for communication within a local network.

### 4. **Protocols**

- **TCP/IP**: Transmission Control Protocol/Internet Protocol is the suite of communication protocols used for connecting hosts on the internet. It includes protocols like TCP (Transmission Control Protocol) and IP (Internet Protocol).

- **HTTP/HTTPS**: HyperText Transfer Protocol (HTTP) and Secure HTTP (HTTPS) are protocols used for transferring data over the internet. HTTPS is secured using SSL/TLS encryption.

- **FTP/SFTP**: File Transfer Protocol (FTP) and Secure File Transfer Protocol (SFTP) are used for transferring files over a network.

- **SMTP/POP3/IMAP**: Simple Mail Transfer Protocol (SMTP) is used for sending emails, while POP3 (Post Office Protocol version 3) and IMAP (Internet Message Access Protocol) are used for receiving emails.

### 5. **Ports**

- Ports are virtual endpoints used for communication between different processes on a network. They allow a single device to host multiple services.

- **Well-known Ports**: Ports ranging from 0 to 1023 are reserved for well-known services like HTTP (80), HTTPS (443), FTP (21), etc.

### 6. **Firewalls and Routers**

- **Firewall**: A firewall is a security device that filters incoming and outgoing network traffic based on a defined set of security rules. It helps protect a network from unauthorized access.

- **Router**: A router is a networking device that forwards data packets between computer networks. It acts as a central hub for data traffic in a network.

### 7. **DNS (Domain Name System)**

- DNS translates human-readable domain names (e.g., www.example.com) into IP addresses that are used by network devices to locate each other on the internet.

### 8. **OSI Model**

- The OSI (Open Systems Interconnection) model is a conceptual framework used to understand network interactions. It's divided into seven layers, each responsible for different functions in the communication process.

   1. Physical Layer
   2. Data Link Layer
   3. Network Layer
   4. Transport Layer
   5. Session Layer
   6. Presentation Layer
   7. Application Layer

These are some fundamental networking concepts and protocols that form the basis of understanding how data is transmitted and received over networks. It's essential for anyone working with networked systems or services.

## Python Networking Libraries

### Socket Library

The socket library provides low-level networking capabilities. It allows you to create sockets for communication between processes. Here's a basic example of a Python server-client communication using the `socket` library. The server will listen for incoming connections, and the client will connect to the server and send a message.

**Server Script:**

```python
import socket

# Create a socket object
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the host and port
host = '127.0.0.1'  # localhost
port = 12345

# Bind the socket to the address
server_socket.bind((host, port))

# Start listening for incoming connections
server_socket.listen(5)

print(f'Server listening on {host}:{port}...')

# Accept a connection and get the client socket
client_socket, client_address = server_socket.accept()
print(f'Connection established with {client_address}')

# Receive data from the client
data = client_socket.recv(1024).decode('utf-8')
print(f'Received: {data}')

# Echo the received data back to the client
client_socket.send(data.encode('utf-8'))

# Close the sockets
client_socket.close()
server_socket.close()
```

**Client Script:**

```python
import socket

# Create a socket object
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the host and port to connect to
host = '127.0.0.1'  # localhost
port = 12345

# Connect to the server
client_socket.connect((host, port))

# Send a message to the server
message = "Hello, server!"
client_socket.send(message.encode('utf-8'))

# Receive data from the server
data = client_socket.recv(1024).decode('utf-8')
print(f'Received from server: {data}')

# Close the socket
client_socket.close()
```

**How to run:**

1. Save the server script in a file, e.g., `server.py`.
2. Save the client script in another file, e.g., `client.py`.
3. Open two terminal windows.
4. In the first terminal, run `python server.py` to start the server.
5. In the second terminal, run `python client.py` to start the client.

You should see output indicating that the client sends a message, the server receives it, and then echoes it back to the client.

### Requests Library

The `requests` library in Python is a widely-used library for making HTTP requests. It simplifies the process of sending HTTP requests and handling responses. Below is an example that demonstrates how to use the `requests` library to make a simple HTTP GET request:

```python
import requests

# Make a GET request to a URL
response = requests.get('https://jsonplaceholder.typicode.com/posts/1')

# Check if the request was successful (status code 200)
if response.status_code == 200:
    # Print the response content (JSON in this case)
    print(response.json())
else:
    # Print an error message if the request was not successful
    print(f'Error: {response.status_code}')
```

In this example:

1. We import the `requests` module.
2. We use `requests.get()` to send a GET request to the specified URL (`https://jsonplaceholder.typicode.com/posts/1`).
3. We check if the response status code is `200`, which indicates a successful request.
4. If the request was successful, we print the response content, assuming it's in JSON format. If not, we print an error message along with the status code.

Keep in mind that you'll need an active internet connection to run this code since it makes a request to an external URL.

To run this code, you need to have the `requests` library installed. You can install it using `pip`:

```bash
pip install requests
```

The `requests` library is incredibly versatile and can be used for a wide range of HTTP operations, including making POST, PUT, DELETE requests, handling authentication, sessions, and much more.

### Netmiko Library

Netmiko is a multi-vendor library that simplifies SSH connections to network devices and provides an easy-to-use interface for sending commands and receiving responses. It supports a wide range of network devices, including routers and switches from various vendors.

Here's an example of how to use the Netmiko library to connect to a network device and execute a command:

```python
from netmiko import ConnectHandler

# Define the device information
device = {
    'device_type': 'cisco_ios',
    'ip': '192.168.0.1',
    'username': 'your_username',
    'password': 'your_password',
    'secret': 'enable_password',  # Enable password if required
}

# Connect to the device
connection = ConnectHandler(**device)

# Enter enable mode if required
connection.enable()

# Send a command and get the output
command = 'show interfaces'
output = connection.send_command(command)

# Print the output
print(output)

# Disconnect from the device
connection.disconnect()
```

Explanation:

1. Import the `ConnectHandler` class from `netmiko`.
2. Define the device information, including the device type (e.g., `cisco_ios`), IP address, username, password, and enable password (if required).
3. Use `ConnectHandler(**device)` to establish an SSH connection to the device.
4. If required, use `connection.enable()` to enter enable mode.
5. Use `connection.send_command(command)` to send a command to the device and receive the output.
6. Print the output.
7. Use `connection.disconnect()` to close the SSH connection.

Before running this code, make sure you have the Netmiko library installed. You can install it using `pip`:

```bash
pip install netmiko
```

Note that you'll need to replace `'your_username'`, `'your_password'`, and `'enable_password'` with your actual login credentials. Also, ensure that you have SSH access enabled on the network device you're trying to connect to.

Keep in mind that Netmiko supports various device types, so you may need to adjust the `device_type` parameter depending on the type of network device you're connecting to (e.g., `cisco_ios`, `cisco_xr`, `juniper_junos`, etc.).

### Scapy Library 

`Scapy` is a powerful packet manipulation tool in Python that allows you to create, send, and analyze network packets. It is widely used for network testing, analysis, and penetration testing. Below are some examples demonstrating the basic usage of `Scapy`:

### Example 1: Sending ICMP (Ping) Packet

```python
from scapy.all import *

# Create an ICMP packet
packet = IP(dst="www.google.com") / ICMP()

# Send the packet and receive a response
response = sr1(packet, timeout=2, verbose=False)

# Check if a response was received
if response:
    print(f"Received response from {response.src}")
else:
    print("No response received")
```

### Example 2: Sending TCP Packet

```python
from scapy.all import *

# Create a TCP packet
packet = IP(dst="www.example.com") / TCP(dport=80, flags="S")

# Send the packet and receive a response
response = sr1(packet, timeout=2, verbose=False)

# Check if a response was received
if response:
    print(f"Received response from {response.src}")
else:
    print("No response received")
```

### Example 3: Sniffing Packets

```python
from scapy.all import *

# Define a packet sniffing function
def packet_sniffer(packet):
    print(packet.summary())

# Start sniffing packets on the network
sniff(filter="icmp", prn=packet_sniffer, count=5)
```

### Example 4: Crafting a Custom Packet

```python
from scapy.all import *

# Create a custom packet
packet = Ether(src="00:11:22:33:44:55", dst="66:77:88:99:00:11") / \
         IP(src="192.168.1.100", dst="192.168.1.1") / \
         TCP(sport=1234, dport=80)

# Send the packet
sendp(packet, iface="eth0")
```

### Example 5: Creating and Sending ARP Request

```python
from scapy.all import *

# Create an ARP request packet
packet = Ether(dst="ff:ff:ff:ff:ff:ff") / ARP(pdst="192.168.1.1")

# Send the ARP request
response = srp1(packet, timeout=2, verbose=False)

# Check if a response was received
if response:
    print(f"Received response from {response.psrc}")
else:
    print("No response received")
```

Before running these examples, ensure that you have `Scapy` installed. You can install it using `pip`:

```bash
pip install scapy
```

Please note that some of these examples involve sending packets, which might not be appropriate or allowed in all environments. Always use caution and ensure you have appropriate permissions and legal rights to perform any network-related activities.

### Twisted Library 

The Twisted library is an event-driven networking framework for Python. It provides support for various protocols, including TCP, UDP, SSH, and more. Below are examples of using Twisted for a simple TCP server and client:

### Example 1: Twisted TCP Server

```python
from twisted.internet import protocol, reactor

class EchoProtocol(protocol.Protocol):
    def dataReceived(self, data):
        self.transport.write(data)

class EchoFactory(protocol.Factory):
    def buildProtocol(self, addr):
        return EchoProtocol()

reactor.listenTCP(12345, EchoFactory())
reactor.run()
```

In this example, we create a simple Echo server. It listens on port 12345 and echoes back any data it receives.

### Example 2: Twisted TCP Client

```python
from twisted.internet import reactor, protocol

class EchoClient(protocol.Protocol):
    def connectionMade(self):
        self.transport.write(b'Hello, server!')

    def dataReceived(self, data):
        print(f'Received from server: {data.decode()}')
        self.transport.loseConnection()

class EchoClientFactory(protocol.ClientFactory):
    def buildProtocol(self, addr):
        return EchoClient()

    def clientConnectionFailed(self, connector, reason):
        print(f'Connection failed: {reason.getErrorMessage()}')
        reactor.stop()

    def clientConnectionLost(self, connector, reason):
        print(f'Connection lost: {reason.getErrorMessage()}')
        reactor.stop()

connector = reactor.connectTCP('127.0.0.1', 12345, EchoClientFactory())
reactor.run()
```

In this example, we create a client that connects to a TCP server running on `127.0.0.1:12345`. It sends a message to the server and waits for a response.

Before running these examples, ensure that you have Twisted installed. You can install it using `pip`:

```bash
pip install twisted
```

These examples showcase a simple echo server and client. Twisted is capable of handling much more complex networking tasks, including protocols like HTTP, SMTP, IMAP, and more. It's a versatile library for building networked applications in Python.
