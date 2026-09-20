## Advanced Servers

## Samba File Services with AD

---

### Network File Services

- A **network file service** allows users to access files stored on another computer.
- Files are stored centrally instead of only on individual workstations.
- Centralized file services make it easier to manage:
  - Access permissions
  - Shared data
  - Backups
  - Security
- Windows environments commonly use **SMB** for network file services.

---

### Server Message Block

- **SMB — Server Message Block**
- SMB is a network protocol used to access shared resources.
- Common SMB resources include:
  - Files
  - Folders
  - Printers
- SMB is the primary file-sharing protocol used in modern Windows environments.
- Modern SMB normally communicates over **TCP port 445**.

---

### SMB Client and Server

- SMB uses a **client-server model**.
- **SMB Client:** Requests access to a shared resource.
- **SMB Server:** Hosts and manages the shared resource.
- A Windows workstation commonly acts as the SMB client.
- Windows Server or Linux with Samba can act as the SMB server.

![smb-client-server](./samba-ad.assets/smb-client-server.png)

---

### SMB Shares

- An SMB server publishes resources called **shares**.
- A share usually represents a directory on the server.
- The share has a network name that clients use to access it.
- The share name does not need to match the server's local directory name.
- Multiple shares can exist on the same SMB server.

---

### UNC Paths

- Windows commonly accesses SMB resources using a **UNC path**.
- **UNC — Universal Naming Convention**
- Basic format: `\\server\share`

- The first component `\\server` identifies the server.
- The second component `\share` identifies the share.

---

### SMB Dialects

- An SMB **dialect** is a version of the SMB protocol.
- The client and server negotiate a compatible dialect when establishing a connection.
- Modern systems normally use **SMB 2.x or SMB 3.x**.
- **SMB 3.1.1** provides modern security and protocol capabilities.
- SMB 1 is obsolete and should normally remain disabled.

---

### SMB 3

- SMB 3 introduced major improvements for enterprise environments.
- Features include:
  - Improved performance
  - Improved availability
  - SMB encryption
  - Improved signing
  - Better resiliency
- SMB continues to evolve as an enterprise file-service protocol.

---

### SMB Signing

- **SMB signing** protects SMB messages from unauthorized modification.
- The sender cryptographically signs SMB messages.
- The receiver verifies the signature.
- Signing helps protect against **man-in-the-middle tampering**.
- Signing protects message integrity but does not replace encryption.

---

### SMB Encryption

- SMB encryption protects SMB data while it travels across the network.
- Encryption provides **confidentiality** for SMB traffic.
- SMB signing primarily protects **integrity**.
- Modern SMB versions can support both.
- Security requirements determine whether these features are supported or required.

---

### Samba

- [**Samba**](https://www.samba.org/) is an open-source implementation of the SMB protocol.
- Samba allows Linux and Unix systems to communicate with Windows SMB clients.
- Samba can provide:
  - File sharing
  - Printer sharing
  - Active Directory integration
  - Domain membership
- A Linux server running Samba can operate as an enterprise SMB file server.

---

### Samba Server Components

- Samba contains several services and supporting components.
- Important components include:
  - **smbd**
  - **winbindd**
  - Kerberos integration
  - NSS integration
  - Active Directory domain membership
- Each component performs a different part of the file-service process.

---

### `smbd`

- **smbd** is the Samba SMB file-server daemon.
- It accepts SMB connections from clients.
- It provides access to configured shares.
- It evaluates Samba share configuration.
- It performs file operations against the Linux filesystem.
- Share definitions are normally stored in **`smb.conf`**.

---

### Active Directory Member Server

- A server can join an existing **Active Directory domain**.
- The server becomes a **domain member**.
- A member server uses AD identities but does not become a Domain Controller.
- Active Directory continues to provide:
  - Users
  - Groups
  - Authentication
  - Kerberos services
- The member server provides its own application or resource services.

---

### Samba as a Domain Member

- Samba can operate as an Active Directory member server.
- Domain membership allows Samba to recognize AD users and groups.
- Domain identities can then be used to control SMB resources.
- Windows users can access Linux-hosted shares using their domain identities.
- This creates a bridge between **Windows identity services** and the **Linux filesystem**.

---

### Domain Membership

- Joining a computer to Active Directory creates a **computer account**.
- The computer becomes an identity in the domain.
- A trust relationship is established between the computer and Active Directory.
- The computer receives credentials used for ongoing domain communication.
- Domain membership is therefore more than simply knowing the domain name.

---

### The Machine Account

- A domain member has its own **machine account**.
- The machine account represents the computer in Active Directory.
- It has credentials separate from normal user accounts.
- These credentials allow the server to prove that it is a trusted domain member.
- Administrators do not provide their passwords for every future domain operation.

---

### Machine Trust

- The machine account establishes a **trust relationship** with the domain.
- Samba uses this relationship for ongoing communication with Active Directory.
- Machine credentials are maintained automatically.
- If the trust relationship becomes invalid, domain operations can fail.
- A successful user password does not repair a broken machine trust.

---

### Kerberos and Samba

- Active Directory uses **Kerberos** as its primary authentication protocol.
- A domain user normally receives a **Ticket-Granting Ticket (TGT)** after authentication.
- The TGT can later be used to request tickets for network services.
- SMB is one of those network services.
- This allows SMB to participate in enterprise **Single Sign-On**.

---

### Kerberos-to-SMB

- Suppose a domain user accesses:<br> `\\fileserver.example.com\Team`

- The client needs to authenticate to the SMB service on that server.
- Kerberos identifies the requested service using a **Service Principal Name (SPN)**.
- SMB commonly uses the **cifs** service class.
- The client can request a Kerberos service ticket for the file service.

---

### The `cifs` Service

- A Kerberos SMB service can be represented as:<br>`cifs/fileserver.example.com`

- **cifs** identifies the SMB file service.
- The hostname identifies the server providing the service.
- The KDC issues a service ticket for that specific service.
- The client presents the ticket when connecting to the SMB server.

---

### Kerberos Single Sign-On

- The user has already authenticated to the domain.
- The client can use the existing TGT to request an SMB service ticket.
- The user does not need to repeatedly enter their password.
- Samba receives proof of the authenticated domain identity.
- This is an example of **Kerberos Single Sign-On**.

---

### Authentication vs. Authorization

- **Authentication:** Who are you?
- **Authorization:** What are you allowed to do?
- Kerberos can authenticate the domain user.
- Authentication alone does not grant access to a file.
- Samba and the Linux filesystem still determine what the authenticated user may do.

---

### Active Directory and Linux Identities

- Active Directory and Linux represent identities differently.
- Active Directory primarily uses **Security Identifiers (SIDs)**.
- Linux filesystems use:
  - User IDs (**UIDs**)
  - Group IDs (**GIDs**)
- A Linux SMB server needs a way to connect these identity models.

---

### Security Identifiers

- A **SID — Security Identifier** uniquely identifies a Windows security principal.
- Security principals include:
  - Users
  - Groups
  - Computers
- Windows permissions are fundamentally associated with SIDs.
- Linux filesystems do not normally use Windows SIDs directly.

---

### Linux UID and GID

- Linux identifies users using a numeric **UID**.
- Linux identifies groups using a numeric **GID**.
- Files and directories store ownership using these numeric identities.
- Linux therefore needs a usable UID/GID representation of an AD identity.
- This is where **Winbind** becomes important.

---

### `Winbind`

- **Winbind** integrates Samba with Windows domain identities.
- It allows Linux to resolve Active Directory users and groups.
- Winbind can map:
  - AD user SID → Linux UID
  - AD group SID → Linux GID
- This allows domain identities to participate in Linux filesystem permissions.
- **winbindd** is the Winbind daemon.

---

### Name Service Switch

- **NSS — Name Service Switch**
- NSS determines where Linux looks for users and groups.
- Traditional Linux identities may come from:
  - `/etc/passwd`
  - `/etc/group`
- NSS can also query external identity sources.
- Winbind can become one of those identity sources.

---

### NSS with Winbind

- **libnss-winbind** connects Linux NSS to Winbind.
- Domain users can then appear to Linux applications like normal Linux users.
- Domain groups can appear like normal Linux groups.
- Commands and applications can resolve domain identities into UIDs and GIDs.
- This allows Linux filesystem permissions to reference AD identities.

---

### Identity Resolution

- Authentication and identity resolution are related but different.
- A user may successfully authenticate to Active Directory.
- Linux must still determine:
  - Who the user is locally
  - Their UID
  - Their GIDs
  - Their group memberships
- Authorization depends on this resolved identity information.

---

### `SSSD`

- **SSSD — System Security Services Daemon**
- SSSD can integrate Linux systems with identity providers such as Active Directory.
- It commonly provides:
  - User lookup
  - Group lookup
  - Authentication
  - Identity caching
  - Access control integration
- SSSD is commonly used for Linux login integration.

---

### `Winbind` vs. `SSSD`

- Both Winbind and SSSD can integrate Linux with Active Directory.
- **SSSD** is commonly used for general Linux identity and login integration.
- **Winbind** is tightly integrated with Samba.
- Samba member file servers commonly use Winbind for domain identity mapping.
- The appropriate identity stack depends on the server's role.

---

### `realmd`

- **realmd** helps Linux discover and join identity domains.
- It can discover Active Directory using DNS.
- realmd coordinates other tools rather than replacing them.
- Different domain-join configurations can use different identity stacks.
- The selected stack should match the intended server role.

---

### Active Directory Discovery

- A Linux server must locate Active Directory services before joining the domain.
- Active Directory publishes services through **DNS SRV records**.
- Important services include:
  - LDAP
  - Kerberos
  - Domain Controllers
- Correct DNS configuration is therefore fundamental to AD integration.

---

### DNS and Active Directory

- Active Directory is heavily dependent on DNS.
- DNS allows clients and servers to locate domain services.
- A normal hostname lookup is not enough.
- AD clients also need service discovery information.
- Incorrect DNS configuration can appear as authentication or domain-join failures.

---

### DNS `SRV` Records

- **SRV records** identify servers providing particular network services.
- Active Directory publishes records for services such as: LDAP, Kerberos
- An SRV record can contain: Service, Protocol, Priority, Weight, Port, Target
- Clients use these records to locate appropriate domain services.

---

### Why Time Matters

- Kerberos uses timestamps as part of authentication.
- Domain members and Domain Controllers need synchronized clocks.
- Excessive clock skew can cause Kerberos authentication to fail.
- A correct password cannot compensate for incorrect system time.
- DNS and time should therefore be checked before troubleshooting higher layers.

---

### From AD Identity to File Access

- Active Directory authenticates the user.
- Winbind resolves the domain identity.
- Linux receives usable UID and GID information.
- Samba evaluates SMB authorization.
- The Linux filesystem evaluates filesystem authorization.
- Successful file access requires the entire chain to work.

---

### Role-Based Access Control

- **RBAC — Role-Based Access Control**
- Permissions are assigned according to organizational roles rather than individual users.
- Users receive access by becoming members of appropriate groups.
- Group-based authorization is easier to manage than large numbers of direct user permissions.
- Active Directory security groups provide the foundation for this model.

---

### AGDLP

- **AGDLP** is a common Active Directory group-nesting model.
- AGDLP stands for:<br>**Accounts → Global Groups → Domain Local Groups → Permissions**

- Each layer has a different purpose.
- The model separates organizational roles from resource permissions.

---

### AGDLP

![agdlp](./samba-ad.assets/agdlp.webp)

Credit: [All about AGDLP group scope for active directory](https://www.infosecinstitute.com/resources/general-security/agdlp-group-scope-active-directory-account-global-domain-local-permissions/)

---

### Why AGDLP?

- Users change jobs.
- Employees join and leave departments.
- Resources change.
- Permissions change.
- AGDLP separates these changes into manageable layers.
- Administrators can change role membership without redesigning resource permissions.

---

### Separation of Concerns

- **Global groups:** Who performs this organizational role?
- **Domain Local groups:** What permission does this resource provide?
- **Resource ACL:** What operations does that permission allow?
- Each layer has one clear responsibility.
- This makes access-control designs easier to understand and troubleshoot.

---

### Samba Authorization

- Samba provides an authorization layer at the SMB protocol level.
- Share configuration can determine:
  - Who may connect
  - Who receives read access
  - Who receives write access
  - Whether guest access is permitted
- Samba authorization happens before or alongside filesystem access checks.

---

### Samba Share Configuration

- Samba shares are normally defined in **smb.conf**.
- A share definition can specify:
  - Share name
  - Filesystem path
  - Authorized users or groups
  - Read/write behavior
  - File creation behavior
- Group-based rules are preferable to large lists of individual users.

---

### `valid users`

- Samba's **valid users** setting can restrict who may access a share.
- Users outside the permitted identities are rejected.
- AD groups can be used in these authorization rules.
- Permission groups are more scalable than individual user entries.
- This creates an SMB-level access boundary.

---

### Read-Only by Default

- A share can be configured as **read-only by default**.
- Specific authorized groups can then receive write access.
- This follows the principle of granting only the access that is required.
- Read-only users can consume information without modifying it.
- Modify users receive additional capabilities.

---

#### `write list`

- Samba can define a **write list**.
- Members of the listed groups can receive write access.
- Other authorized users can remain read-only.
- This allows multiple permission levels within the same share.
- Group membership determines the user's effective Samba access.

---

### Samba Is Not the Filesystem

- Samba controls access through the SMB service.
- The actual files still exist on a Linux filesystem.
- Linux independently evaluates filesystem permissions.
- Samba cannot simply ignore a Linux filesystem denial.
- This creates **two authorization layers**.

---

### Two Authorization Layers

- **Layer 1: Samba authorization**
  - Controls SMB access.
- **Layer 2: Linux filesystem authorization**
  - Controls access to files and directories.
- Both layers must permit the requested operation.
- A failure in either layer can produce **Access Denied**.

---

### POSIX ACLs

- **ACL — Access Control List**
- POSIX ACLs extend traditional Linux permissions.
- ACLs allow additional users and groups to receive permissions.
- Multiple AD groups can therefore receive different permissions on the same directory.
- ACLs are useful for enterprise shared folders.

---

### Access ACLs

- An **access ACL** controls permissions on an existing file or directory.
- It can contain entries for:
  - Owner
  - Named users
  - Owning group
  - Named groups
  - Mask
  - Others
- These entries determine current access to the object.

---

### Default ACLs

- A directory can also contain a **default ACL**.
- Default ACLs provide an inheritance template for new objects.
- New files and subdirectories receive ACL information based on the parent directory.
- Default ACLs do not retroactively modify existing files.
- They help maintain consistent permissions over time.

---

### Why Inheritance Matters

- Shared folders continuously receive new files and directories.
- Permissions must remain consistent as users create content.
- Without appropriate inheritance:
  - New files may receive unexpected groups.
  - Read-only users may lose access.
  - Modify users may be unable to collaborate.
- File-server design must consider both current and future objects.

---

### The ACL Mask

- POSIX ACLs contain a **mask**.
- The mask limits the maximum effective permissions available to:
  - Named users
  - Named groups
  - The owning group
- An ACL entry may appear to grant `rwx`.
- A restrictive mask can reduce those effective permissions.

---

### `setgid` on Shared Directories

- Linux directories can use the **setgid** bit.
- New files and subdirectories inherit the directory's group ownership.
- This is useful for collaborative shared directories.
- Without setgid, new objects may use the creator's primary group.
- Consistent group ownership helps maintain predictable access.

---

### `setgid` and Default ACLs

- **setgid** helps control inherited group ownership.
- **Default ACLs** help control inherited permissions.
- They solve different but related problems.
- Enterprise shared directories often use both.
- Correct inheritance prevents permissions from gradually becoming inconsistent.

---

### File Creation Permissions

- Samba can influence permissions assigned to newly created files and directories.
- Linux filesystem rules still apply.
- File creation settings should support the intended access model.
- Shared files should not accidentally become world-accessible.
- New objects should preserve the required group collaboration model.

---

### Windows SMB Connection

- A Windows client connects to a Samba share using SMB.
- The client identifies the target server and share.
- Authentication establishes the user's identity.
- Samba determines whether the user may access the share.
- Linux determines whether the resulting identity may access the requested file.

---

### Windows Single Sign-On

- A domain user normally authenticates when signing in to Windows.
- The existing domain identity can then be used for network services.
- Kerberos can provide service tickets without repeatedly requesting the password.
- This creates a transparent user experience.
- **SSO simplifies authentication; it does not bypass authorization.**

---

### Windows Security Tokens

- Windows creates an **access token** for a user session.
- The token contains information about the authenticated identity.
- It also contains security group memberships.
- Applications use this security context when accessing resources.
- Group membership therefore directly affects authorization decisions.

---

### Group Membership Changes

- Group membership can change while a user is already signed in.
- Existing security contexts may still contain older membership information.
- A new sign-in may be required before the new membership is reflected.
- Identity systems may also cache group information.
- Stale identity information can make correct permissions appear broken.

---

### SMB Sessions

- Windows maintains SMB sessions with remote servers.
- An existing session may continue using previously supplied credentials.
- Connecting again does not always create a completely new authentication context.
- Credential caching can therefore affect access testing.
- Always distinguish the intended user from the identity actually connected.

---

### SMB Connection Negotiation

- When an SMB connection begins, client and server negotiate capabilities.
- This includes the SMB dialect.
- Security capabilities may also be negotiated.
- The resulting session represents the authenticated user.
- File operations then occur within that SMB session.

---

### Dependency Chain

- Troubleshoot file access as an **end-to-end dependency chain**:
  - DNS and time
  - Kerberos and Active Directory
  - Machine trust
  - Winbind identity resolution
  - Group membership
  - Samba authorization
  - Linux ACLs
  - SMB client session
- **Find the failed layer before changing the configuration.**

---

### Key Takeaways

- **SMB** provides network file sharing in Windows environments.
- **Samba** allows Linux systems to provide SMB services.
- Samba can operate as an **Active Directory member server**.
- **smbd** provides the SMB file service.
- **Winbind** connects AD identities to the Linux identity model.
- **NSS** makes those identities available to Linux applications.

---

### Key Takeaways

- Active Directory uses **Kerberos** for domain authentication.
- SMB commonly uses the Kerberos **cifs** service class.
- A Samba domain member has its own **computer account and machine trust**.
- Kerberos establishes identity.
- Samba and Linux determine authorization.
- **Authentication does not automatically grant resource access.**

---

### Key Takeaways

- **AGDLP** separates accounts, organizational roles, resource permission groups, and permissions.
- Global groups commonly represent roles.
- Domain Local groups commonly represent resource permissions.
- Permissions should be assigned to groups rather than individual users.
- Nested group membership determines effective access.

---

### Key Takeaways

- Samba and Linux provide **two independent authorization layers**.
- Both layers must permit an operation.
- POSIX ACLs extend traditional Linux permissions.
- Default ACLs support permission inheritance.
- The ACL mask can limit effective permissions.
- `setgid` helps maintain consistent group ownership.

---

### Resources

- [Server Message Block Protocol](https://asmed.com/comptia-net-server-message-block-protocol-smb/)
- https://www.samba.org/
- [winbindd](https://www.samba.org/samba/docs/current/man-html/winbindd.8.html)
- [All about AGDLP group scope for active directory](https://www.infosecinstitute.com/resources/general-security/agdlp-group-scope-active-directory-account-global-domain-local-permissions/)