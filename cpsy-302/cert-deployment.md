## Advanced Servers

## Certificate Deployment

---

### Certificate Deployment Workflow

![pki-cert-deploy-workflow](./cert-deployment.assets/pki-cert-deploy-workflow.svg)

---

###  Certificate Templates

- A certificate template is a set of certificate rules
- It defines the certificate’s purpose
- It defines key and cryptographic requirements
- It defines who may request the certificate
- It tells the client how to create a valid request

- Microsoft describes templates as rules applied to certificate requests and instructions used by clients when creating requests.

---

### Certificate Template Example

![cert-template-computer](./cert-deployment.assets/cert-template-computer.webp)

---

### Enterprise CA and Templates

- Certificate templates are stored in Active Directory
- Templates can be shared across Enterprise CAs in the forest
- Only an **Enterprise CA** can issue template-based certificates
- A Standalone CA does not use AD-integrated templates

---

### Why Duplicate a Template

- Built-in templates provide starting points
- A duplicated template can be customized
- The original template remains unchanged
- The new template can have one clear purpose
- Permissions can be limited to the intended computers

- **Note:** Choose the existing template that most closely matches the required certificate, then customize the copy.

---

### Duplicated Template

![duplicated-template](./cert-deployment.assets/duplicated-template.webp)

---

### What a Template Controls

- A template can define:

  - Certificate subject and identity information

  - Certificate validity and renewal settings

  - Key type, size, and permitted operations

  - Enhanced Key Usage

  - Enrollment and auto-enrollment permissions

  - Whether special features such as key archival are required

---

### Template Compatibility

- Template compatibility controls available features
- It also identifies supported CA and client versions
- Newer template versions provide additional options
- Auto-enrollment requires a template that supports it
- Select compatibility based on actual environment requirements

- **Note:** Do not select newer compatibility settings unless the participating systems support them.

---

### Publishing a Template

- Creating a template does not automatically make it usable
- The template is stored in Active Directory
- An Issuing CA must be authorized to issue it
- Publishing connects the template to that CA
- Different CAs may publish different templates

- **Example:** A template may exist in the forest but remain unavailable until an Enterprise Issuing CA publishes it.

---

### Template Permissions

- Template permissions control access:

  - **Read:** Discover and examine the template

  - **Enroll:** Request a certificate from the template

  - **Autoenroll:** Receive the certificate automatically

  - Permissions are normally assigned to AD groups

  - Only the intended users or computers should receive access

- Certificate templates allow administrators to control which users and computers can read templates and enrol for certificates.

---

### Template Permissions

![tmpl-perm](./cert-deployment.assets/tmpl-perm.webp)

---

### Requirements for Auto-Enrollment

- Permission to read the template

- Permission to enrol using the template

- Permission to auto-enroll

- Membership in the correct AD security group

- Access to a CA that publishes the template

- An applicable computer GPO that enables certificate auto-enrollment

---

### Certificate Enrollment

- Enrollment is the process of requesting a certificate
- The client creates or accesses a key pair
- The client creates a certificate request
- The CA evaluates the request against the template
- An approved certificate is issued and installed

- **Note:** The certificate contains the public key. The private key normally remains on the requesting computer.

---

### Manual vs. Automatic Enrollment

- **Manual enrollment**

  - A user or administrator starts the request

  - Useful for special or controlled certificates

- **Auto-enrollment**

  - Windows starts the request automatically

  - Useful for larger numbers of domain users or computers

  - Supports consistent certificate deployment

---

### Auto-Enrollment

- Auto-enrollment uses Active Directory certificate policy
- Eligible domain members discover available templates
- The client checks template permissions
- The client requests a matching certificate
- The issued certificate is installed automatically

- Auto-enrollment can also help renew certificates and respond to template updates.

---

### Group Policy's Role

- Group Policy tells Windows:

  - Whether auto-enrollment is enabled

  - Whether computer or user policy applies

  - Whether expired certificates should be renewed

  - Whether pending requests should be updated

  - Whether certificate-template changes should be applied

- Group Policy activates the client-side auto-enrollment behaviour; it does not replace template permissions.

- GPO enables; template permissions authorize.

---

### Certificate Purpose and EKU

- EKU means **Enhanced Key Usage**
- EKU identifies the certificate’s permitted purposes
- **Server Authentication** identifies a server to clients
- **Client Authentication** identifies a client to a server
- Applications can reject certificates with an unsuitable EKU
- **Note:** A certificate can be valid but unsuitable for the intended service

---

### The Issued Certificate

- After successful enrollment:

  - The certificate appears in a certificate store

  - A computer certificate normally uses the Local Computer context

  - Its private key is associated with that computer

  - Services can locate certificates available to the computer

  - Not every installed certificate is suitable for every service

---

### IIS Certificate Readiness

- Before binding a certificate to IIS, verify:
  - **DNS SAN:** Matches the hostname clients will use
  - **Enhanced Key Usage:** Includes Server Authentication
  - **Validity:** Is within its validity period
  - **Certificate chain:** Leads to a root CA trusted by clients
  - **Private key:** Is present and accessible to the server
- **Note:** Installing a certificate does not automatically assign it to an IIS website

---

### Inspect Before Use

![inspect-cert-before-use](./cert-deployment.assets/inspect-cert-before-use.webp)

---

### HTTPS Binding

- An HTTPS binding connects a website to a certificate
- The binding tells IIS which certificate to present
- The server uses the matching private key during TLS
- The client receives the server certificate and supporting chain
- The binding does not make an incorrect certificate valid

- **Note:** Installing a certificate and assigning it to a website are separate concepts.

---

### IIS HTTPS Binding

![iis-https-binding](./cert-deployment.assets/iis-https-binding.webp)

---

### Renewal and IIS Rebinding

- Auto-enrollment can renew a certificate before it expires

- Renewal issues a new certificate

- IIS must use the renewed certificate in its HTTPS binding

- Enable **Automatic Rebind of Renewed Certificate**, or update the binding manually

- Verify that the website presents the renewed certificate

---

### HTTPS Using TLS

- The client connects to the IIS server
- The server presents its certificate
- The client validates the server’s identity
- TLS negotiates protected communication
- Application data is then encrypted and integrity-protected

- Windows uses **Schannel** to provide TLS authentication and encryption for client-server communication.

---

### Client Validation

- Checks performed by the connecting client:

  - Does the certificate identify the requested server?

  - Is the certificate currently valid?

  - Does it include Server Authentication?

  - Does the chain reach a trusted Root CA?

  - Has a certificate in the chain been revoked?

- Windows certificate validation includes chain, time, revocation, usage, and server-identity checks.

---

### Browser Certificate Viewer

![client-cert-viewer](./cert-deployment.assets/client-cert-viewer.webp)

---

### Name Matching

- The client connects using a DNS name
- The certificate must represent that identity
- A certificate for a different server should be rejected
- Subject Alternative Name is used for DNS identities
- Using the correct URL is part of successful validation

- **Example:** A certificate for `web01.example.com` should not be accepted for `web02.example.com`.

---

### Revocation in Deployment

- The Issuing CA publishes revocation information
- Clients use the certificate’s CDP information
- A current CRL must be available
- A revoked certificate should fail validation
- An expired or unreachable CRL may interrupt certificate use

---

### HTTPS Troubleshooting

<table>
  <thead>
    <tr>
      <th>Symptom</th>
      <th>Evidence to Inspect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>No certificate appears after auto-enrollment</td>
      <td>Applied computer GPO, template publication, Read/Enroll/Autoenroll permissions, and auto-enrollment event logs</td>
    </tr>
    <tr>
      <td>Certificate is unavailable for the IIS binding</td>
      <td>Local Computer certificate store, matching private key, and Server Authentication EKU</td>
    </tr>
    <tr>
      <td>Browser reports a name mismatch</td>
      <td>Hostname in the URL compared with DNS names in the certificate’s SAN</td>
    </tr>
  </tbody>
</table>

---

### HTTPS Troubleshooting

<table>
  <thead>
    <tr>
      <th>Symptom</th>
      <th>Evidence to Inspect</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Browser reports an untrusted certificate</td>
      <td>Client’s trusted root store and availability of intermediate CA certificates</td>
    </tr>
    <tr>
      <td>Website still presents an expired certificate after renewal</td>
      <td>Certificate thumbprint in the active IIS binding and automatic rebinding configuration</td>
    </tr>
    <tr>
      <td>Client reports a revocation-check failure</td>
      <td>Exact error, certificate CDP URLs, CRL validity, and client access to revocation information</td>
    </tr>
  </tbody>
</table>

---

### Modern Terminology and Practice

- Say **HTTPS using TLS**, not "**SSL**"
- IIS may still use "**SSL**" in some interface labels
- Do not use SHA-1 for new certificate designs
- Avoid RSA keys smaller than 2048 bits
- Avoid unnecessary all-purpose certificates
- Use purpose-specific templates and current cryptography

- Windows can reject certificates using outdated algorithms such as MD5 and SHA-1, while current Windows documentation treats TLS as the modern protocol family.

---

### Key Takeaways

- Enterprise CAs issue certificates using AD-integrated certificate templates.
- Administrators should duplicate built-in templates to customize deployment settings while leaving original templates intact.
- An Enterprise CA must publish the template before it can issue certificates using it.
- Successful computer auto-enrollment requires granting Read, Enroll, and Autoenroll permissions to appropriate AD security groups.

---

### Key Takeaways

- The client submits a certificate request containing its public key and required request information. The private key normally remains on the client.
- Auto-enrollment requires both client Group Policy and template security permissions to permit the request.
- HTTPS bindings fail if the server cannot access the certificate's matching private key.
- Clients evaluate revocation according to application policy. Unavailable revocation information can cause validation failures.

---

### Resources

- [Server Certificate Deployment Overview](https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/server-certificate-deployment-overview)
- [Microsoft PKI Planning and Deploying Certificate Services](https://www.petenetlive.com/KB/Article/0001309)
- [Manage certificate templates](https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/manage-certificate-templates)
- [Key Archival Security Considerations](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-wcce/95f13be7-e0e9-4e58-9762-228bb086e7f7)

---

### AI Disclaimer

- Concepts were sketched by hand on an iPad using an Apple Pencil, with ChatGPT Images 2.5 used for final rendering.
- Every AI-generated illustration is manually reviewed and verified.