## Server Fundamentals 

## Client/Server Model

---

### Operating System

By way of review - A fully functioning computer system consists of four components:

- **Hardware**
- **Operating System**
- **Applications**
- **Users**

---

### System Components

![system-components](./ClientServer.assets/system-components.webp)

---

### What is an operating system?

- The program that, after being initially loaded into the computer by a bootstrap program, manages all the other programs in a computer.
- Software that manages hardware on the computer, supports applications, provides an interface for the user, and manages **I/O**.

---

### What does an operating system do?

An operating system (OS) provides the following tasks for the programs and applications that run on the computer:

- Decides which programs should execute.
- Decides what order multiple programs should run in.
- Decides how much time each program should be allowed.
- Decides how much memory each application can use.
- Moves input and output from attached hardware devices, such as keyboards, hard disks, and printers.
- Makes sure that different programs and users running at the same time do not interfere with each other.

---

### What is a File System:

- An operating system’s method of organizing, managing, and accessing its files through logical structures and routines.
- **Be careful not to confuse file systems with directories:**
  - A **file system** interacts with the operating system.
  - A **directory** organizes files so that a user can find them on a hard disk or storage volume.
- **Examples:**
  - FAT/FAT32/NTFS/ReFS/CDFS/UDFS
  - **Linux:** Ext4, XFS, ZFS, etc.
  - Disk Management and CLI

---

### Operating Systems

- **Plain Operating systems** contain **NO** networking component – these need to be added in as an installed application.
  - Examples: DOS, Win 3.1 (not 3.11).
- **Network Operating system** includes software to communicate with other computers via a network.
  - Provides security for, and access to, shared data and shared devices.
  - Interfaces between clients and servers.
  - Provides the services necessary to communicate over a network.

---

### Simple Peer-To-Peer Network

![peer-to-peer-network](./ClientServer.assets/peer-to-peer-network.webp)

---

### Client-Server Based Network

![client-server-network](./ClientServer.assets/client-server-network.webp)

---

### Client/Server

- **Client**
  - **It is a piece of software that uses services.**
  - Typically, a client is an application that runs on a personal computer and relies on a server to perform some operations.

- **Server**
  - **It is a piece of software that provides services.**
  - A server is a computer or device on a network that manages network resources.

---

### Client/Server Attributes

- Processing is divided between client and server.
- Client and server can reside on the same or different machines.
- There may be one centralized server or several distributed servers.
- Client requests resources.
- Server supplies resources.
- Modular.
- Message based.

---

### Service/Server Implementation

- Varies according to O/S.
- Is a **TSR** (Terminate Stay Resident) program – runs in memory in the background “listening” for requests bound for a service.
- **What is a TCP/IP port – and what is its purpose?**
- **In Windows:**
  - Installed through the control panel / using add remove programs / add Windows components.
  - Installed as a “role” or a “feature” in Windows server.
  - Installed through an application.

---

### Services in Windows

- Every server will implement as a service – but **NOT** every service is a server.
- Once installed, a service is either started or stopped.
- Three startup types: **disabled**, **manual**, **automatic**.
- Every service has dependencies, recovery actions, and logon instructions.

![windows-services](./ClientServer.assets/windows-services.webp)

---

### Services in Linux

- Similar to Windows, services (and services which operate as a server) are started either manually or at boot.
- Run in the background.
- Used to depend on the “run level” in “init” based systems – like safe mode in Windows – the difference between run levels was what services started.
- Now depends on “**systemd**” system - which uses “targets” and uses `systemctl`.
- Are known as “**daemons**”, but are the same thing.

---

### Essential Network Services: DHCP Server
**(Dynamic Host Configuration Protocol)**

- **TCP/IP** is the protocol of choice.
- Every client machine must be configured with an IP address.
- This can either be done manually or automatically through **DHCP**.
- To do this manually is tedious and error-prone.
- The client broadcasts a request for IP configuration, the DHCP server responds with IP automatically.

---

### Name Resolution Servers

- To access resources on a network, clients usually use the name of the computer they are trying to access.
- For example: `www.google.com` OR `\\prn161\H410`.
- Clients don’t know and can’t remember the IP address (they also **CAN’T** know the IP in a DHCP environment).
- Need to “resolve” the name to an IP address.

---

### Essential Network Services: Name Resolution Servers

- Name resolution allows you to resolve a name to an IP address – there are two main types:
  - **Domain Name Servers (DNS)** do **Host Name resolution**.
  - **Windows Internet Name Service (WINS)** do **Netbios name resolution** (not common anymore – used to be good for internal networks).
- Clients query either the WINS or DNS servers for the IP of the target system name that they are trying to locate.
- In DHCP environments, having a centralized, dynamic server to manage name resolution is essential.

---

### Login Server:

- Login server (**Domain Controller**) holds user and computer credentials.

![login-server-diagram](./ClientServer.assets/login-server-diagram.webp)

---

### Login Servers

- Credential management is critical in running a network.
- In Microsoft parlance, a server that operates as a login server is described as a “**domain controller**”.
- A domain controller holds a copy of the **Active Directory** database – which includes every user, computer, and resource administered on the network (You log into AD at SAIT).
- This allows the administrator to manage every user and computer from a single server – allows “**single sign on**” – credentials can be used across all resources.

---

### File Servers:

- **1.** Client computer asks for a file from the file server over a network.
- **2.** File server locates the file and sends a copy to the client computer.
- **3.** The **FULL** set of data is sent to the PCs. Also allows for backup.

![file-server-diagram](./ClientServer.assets/file-server-diagram.webp)

---

### A Database Server example:

- **1.** The user runs client software to create a query. The client connects to the Database server and sends the request.
- **2.** The server analyzes the query, computes the results, and processing is carried out on the **database server**.
- **3.** The server sends back the **result** of the processed data (not the whole file).

![database-server-diagram](./ClientServer.assets/database-server-diagram.webp)

---

### File Server vs Database Server

![file-vs-database-diagram](./ClientServer.assets/file-vs-database-diagram.webp)

---

### Web/Virtualization Servers

- Most of us are familiar with Web servers… But this is a client/server interaction – what is the client?
- **Virtualization server** is a system with an OS designed to host many other virtual computers inside it – many advantages to this:
  - Segmentation of services.
  - Ease of Management and deployment – less power/space.
  - Cloud based services.
  - **VDI** (Virtual Desktop Infrastructure).

---

### “LAMP” Servers

- Often Servers are **Hybrids** – offering more than one service at a time.
- It is good practice to separate out different services – in case a server is compromised, is taken offline, or needs to be rebooted - you don’t want to impact the other services being hosted.
- **LAMP** is a common Linux based server providing Web with a database – i.e., Drupal.
- **LAMP** stands for **L**inux, **A**pache, **M**ySQL, **P**HP.

---

### Summary

- Plus a bunch of other different types of servers – firewalls, NAS, Transaction, radius, VPN, etc.
- Often dedicated machines, but not necessarily.
- In our case, we’re running services which are “servers” on platforms like Linux and Windows “servers” – likely on large computers… called “servers”.