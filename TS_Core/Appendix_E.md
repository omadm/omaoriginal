<strong> Appendix E. LwM2M Objects defined by OMA (Normative) </strong> 

This Appendix provides LwM2M Objects defined by OMA. Other organizations and companies may define additional LwM2M according to the guidelines and template provided in Appendix D.

The following LwM2M Objects have been defined by OMA as part of LwM2M 1.0:

| **Object**              | **Object ID** |
|-------------------------|---------------|
| LwM2M Security          | 0             |
| LwM2M Server            | 1             |
| Access Control          | 2             |
| Device                  | 3             |
| Connectivity Monitoring | 4             |
| Firmware                | 5             |
| Location                | 6             |
| Connectivity Statistics | 7             |

```
Table 28: LwM2M Objects defined by OMA LwM2M 1.0
```

The LwM2M Server MUST support LwM2M Security, LwM2M Server, and Device Object and SHOULD support Access Control, Device, Connectivity, Firmware Update, Location, and Connectivity Statistics Object.

### E.1	LwM2M Object: LwM2M Security

<strong>Description</strong>

This LwM2M Object provides the keying material of a LwM2M Client appropriate to access a specified LwM2M Server. One Object Instance SHOULD address a LwM2M Bootstrap-Server.<br />
These LwM2M Object Resources MUST only be changed by a LwM2M Bootstrap-Server or Bootstrap from Smartcard and MUST NOT be accessible by any other LwM2M Server.

<strong>Object definition</strong>

<table>
<thead>
<tr class="header">
<th><strong>Name</strong></th>
<th><strong>Object ID</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Object URN</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>LwM2M Security</td>
<td>0</td>
<td>Multiple</td>
<td>Mandatory</td>
<td>urn:oma:lwm2m:oma:0:1.1</td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="even">
<td><strong>Resource definitions</strong></td>
<td></td>
</tr>
<tr class="odd">
<td><table>
<thead>
<tr class="header">
<th><strong>ID</strong></th>
<th><strong>Name</strong></th>
<th><strong>Operations</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Type</strong></th>
<th><strong>Range or Enumeration</strong></th>
<th><strong>Units</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0</td>
<td>LwM2M Server URI</td>
<td></td>
<td>Single</td>
<td>Mandatory</td>
<td>String</td>
<td>0-255 bytes</td>
<td></td>
<td>Uniquely identifies the LwM2M Server or LwM2M Bootstrap-Server. The format of the CoAP URI is defined in Section 6 of RFC 7252.</td>
</tr>
<tr class="even">
<td>1</td>
<td>Bootstrap-Server</td>
<td></td>
<td>Single</td>
<td>Mandatory</td>
<td>Boolean</td>
<td></td>
<td></td>
<td>Determines if the current instance concerns a LwM2M Bootstrap-Server (true) or a standard LwM2M Server (false)</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Security Mode</td>
<td></td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td>0-4</td>
<td></td>
<td>Determines which UDP payload security mode is used<br />
0: Pre-Shared Key mode<br />
1: Raw Public Key mode<br />
2: Certificate mode<br />
3: NoSec mode<br />
4: Certificate mode with EST</td>
</tr>
<tr class="even">
<td>3</td>
<td>Public Key or Identity</td>
<td></td>
<td>Single</td>
<td>Mandatory</td>
<td>Opaque</td>
<td></td>
<td></td>
<td>Stores the LwM2M Client’s Certificate or optional its certification path {including client certificate but not the trust anchor} (Certificate mode), public key (RPK mode) or PSK Identity (PSK mode). The format is defined in Section E.1.1.</td>
</tr>
<tr class="odd">
<td>4</td>
<td>Server Public Key</td>
<td></td>
<td>Single</td>
<td>Mandatory</td>
<td>Opaque</td>
<td></td>
<td></td>
<td>Stores the LwM2M Server’s, respectively LwM2M Bootstrap-Server’s, Certificate or a trust anchor certificate suitable for path validation (Certificate mode), public key (RPK mode). The format is defined in Section E.1.1.</td>
</tr>
<tr class="even">
<td>5</td>
<td>Secret Key</td>
<td></td>
<td>Single</td>
<td>Mandatory</td>
<td>Opaque</td>
<td></td>
<td></td>
<td>Stores the secret key or private key of the security mode. The format of the keying material is defined by the security mode in Section E.1.1. This Resource MUST only be changed by a bootstrap-server and MUST NOT be readable by any server.</td>
</tr>
<tr class="odd">
<td>6</td>
<td>SMS Security Mode</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td>0-255</td>
<td></td>
<td>Determines which SMS security mode is used (see section 7.2)<br />
0: Reserved for future use<br />
1: DTLS mode (Device terminated) PSK mode assumed<br />
2: Secure Packet Structure mode (Smartcard terminated)<br />
3: NoSec mode<br />
4: Reserved mode (DTLS mode with multiplexing Security Association support)<br />
5-203 : Reserved for future use<br />
204-255: Proprietary modes</td>
</tr>
<tr class="even">
<td>7</td>
<td>SMS Binding Key Parameters</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Opaque</td>
<td>6 bytes</td>
<td></td>
<td>Stores the KIc, KID, SPI and TAR. The format is defined in Section E.1.2.</td>
</tr>
<tr class="odd">
<td>8</td>
<td>SMS Binding Secret Key(s)</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Opaque</td>
<td>16-32-48 bytes</td>
<td></td>
<td><p>Stores the values of the key(s) for the SMS binding.</p>
<p>This resource MUST only be changed by a bootstrap-server and MUST NOT be readable by any server.</p></td>
</tr>
<tr class="even">
<td>9</td>
<td>LwM2M Server SMS Number</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td><p>MSISDN used by the LwM2M Client to send messages to the LwM2M Server via the SMS binding.</p>
<p>The LwM2M Client SHALL silently ignore any SMS originated from unknown MSISDN</p></td>
</tr>
<tr class="odd">
<td>10</td>
<td>Short Server ID</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td>1-65534</td>
<td></td>
<td>This identifier uniquely identifies each LwM2M Server configured for the LwM2M Client.<br />
This Resource MUST be set when the Bootstrap-Server Resource has false value.<br />
Specific ID:0 and ID:65535 values MUST NOT be used for identifying the LwM2M Server (Section 6.3).</td>
</tr>
<tr class="even">
<td>11</td>
<td>Client Hold Off Time</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>s</td>
<td><p>Relevant information for a Bootstrap-Server only.<br />
The number of seconds to wait before initiating a Client Initiated Bootstrap once the LwM2M Client has determined it should initiate this bootstrap mode.</p>
<p>In case client initiated bootstrap is supported by the LwM2M Client, this resource MUST be supported.</p></td>
</tr>
<tr class="odd">
<td>12</td>
<td>Bootstrap-Server Account Timeout</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>s</td>
<td><p>The LwM2M Client MUST purge the LwM2M Bootstrap-Server Account after the timeout value given by this resource. The lowest timeout value is 1.</p>
<p>If the value is set to 0, or if this resource is not instantiated, the Bootstrap-Server Account lifetime is infinite.</p></td>
</tr>
<tr class="even">
<td>13</td>
<td>Matching Type</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td>0-3</td>
<td></td>
<td>The Matching Type Resource specifies how the certificate or raw public key in in the Server Public Key is presented. Four values are currently defined: 

 - 0: Exact match. This is the default value and also corresponds to the functionality of LwM2M v1.0. Hence, if this resource is not present then the content of the Server Public Key Resource corresponds to this value. 
 - 1: SHA-256 hash [RFC6234]
 - 2: SHA-384 hash [RFC6234]
 - 3: SHA-512 hash [RFC6234]
</td>
</tr>
<tr class="odd">
<td>14</td>
<td>SNI</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>This resource holds the value of the Server Name Indication (SNI) value to be used during the TLS handshake. When this resource is present then the LwM2M Server URI acts as the address of the service while the SNI value is used for matching a presented certificate, or PSK identity. 
</td>
</tr>
<tr class="even">
<td>15</td>
<td>Certificate Usage</td>
<td></td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td>0-3</td>
<td></td>
<td>The Certificate Usage Resource specifies the semantic of the certificate or 
 raw public key stored in the Server Public Key Resource, which is used to match 
 the certificate presented in the TLS / DTLS handshake. When this resource is 
 absent the default value is value (3) -- domain issued certificate mode. 

The following four types are specified, as defined in RFC 6698: 

 - 0: Certificate usage 0 ("CA constraint")

      This mode is used to specify a CA certificate, or
      the public key of such a certificate, that MUST be found in any of
      the PKIX certification paths for the end entity certificate given
      by the server in TLS or DTLS.  This certificate usage is sometimes
      referred to as "CA constraint" because it limits which CA can be
      used to issue certificates for a given service on a host.  The
      presented certificate MUST pass PKIX certification path
      validation, and a CA certificate that matches the Server Public Key
      Resource content MUST
      be included as part of a valid certification path.  Because this
      certificate usage allows both trust anchors and CA certificates,
      the certificate might or might not have the basicConstraints
      extension present.

 - 1: Certificate usage 1 ("service certificate constraint")
 
      This mode is used to specify an end entity
      certificate, or the public key of such a certificate, that MUST be
      matched with the end entity certificate given by the server in
      TLS.  This certificate usage is sometimes referred to as "service
      certificate constraint" because it limits which end entity
      certificate can be used by a given service on a host.  The target
      certificate MUST pass PKIX certification path validation and MUST
      match the Server Public Key Resource content.

 - 2: Certificate usage 2 ("trust anchor assertion")
 
      This mode is used to specify a certificate, or the
      public key of such a certificate, that MUST be used as the trust
      anchor when validating the end entity certificate given by the
      server in TLS.  This certificate usage is sometimes referred to as
      "trust anchor assertion" and allows a domain name administrator to
      specify a new trust anchor -- for example, if the domain issues
      its own certificates under its own CA that is not expected to be
      in the end users' collection of trust anchors.  The target
      certificate MUST pass PKIX certification path validation, with any
      certificate matching the Server Public Key
      Resource content considered to be a trust
      anchor for this certification path validation.

 - 3: Certificate usage 3 ("domain-issued certificate")
 
      This mode is used to specify a certificate, or the
      public key of such a certificate, that MUST match the end entity
      certificate given by the server in TLS.  This certificate usage is
      sometimes referred to as "domain-issued certificate" because it
      allows for a domain name administrator to issue certificates for a
      domain without involving a third-party CA.  The target certificate
      MUST match the Server Public Key
      Resource content.  The difference between certificate
      usage 1 and certificate usage 3 is that certificate usage 1
      requires that the certificate pass PKIX validation, but PKIX
      validation is not tested for certificate usage 3.
</td>
</tr>
<tr class="odd">
<td>16</td>
<td>DTLS/TLS Ciphersuite</td>
<td></td>
<td>Multiple</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td></td>
<td>When this resource is present it instructs the DTLS/TLS client to propose the indicated ciphersuite(s) in the ClientHello of the handshake. A ciphersuite is indicated as a 32-bit integer value. The IANA TLS ciphersuite registry is maintained at  https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml. As an example, the TLS_PSK_WITH_AES_128_CCM_8 ciphersuite is represented with the following string "0xC0,0xA8". To form an integer value the two values are concatinated. In this example, the value is 0xc0a8 or 49320.
</td>
</tr>

</tbody>
</table>
  
<tbody>
<tr class="odd">
<td></td>
</tr>
</tbody>
</table></td>
</tr>
<tr class="even">
<td><ol style="list-style-type: upper-alpha">

#### E.1.1 UDP Channel Security: Security Key Resource Format

</ol>
<p>This section defines the format of the Secret Key and Public Key and Identity Resources of the LwM2M Server and LwM2M Bootstrap-Server Objects when using UDP Channel security. These Resources are used to configure the security mode and keying material that a Client uses with a particular Server. The Objects are configured on the Client using one of the Bootstrap mechanisms described in Section 5.1. The use of this keying material for each security mode is defined in Section 7.1.</p>
<ol style="list-style-type: upper-alpha">

##### E.1.1.1 Pre-Shared Key (PSK) Mode

</ol>
<p>The PSK is a binary shared secret key between the Client and Server of the appropriate length for the Cipher Suite used [RFC4279]. This key is composed of a sequence of binary bytes in the Secret Key Resource. The default PSK Cipher Suites defined in this specification use a 128-bit AES key. Since the security of the default PSK Cipher Suites rely on the length and the entropy of this shared secret it is RECOMMENDED to provision a 16 byte (128 bit) key or longer in the Secret Key Resource. Recommendations for generating random keys are provided in RFC 4086 [RFC4086].<br />
The corresponding PSK Identity for this PSK is stored in the Public Key or Identity Resource. The PSK Identity is simply stored as a UTF-8 String as per [RFC4279]. Clients and Servers MUST support arbitrary PSK Identities of up to 128 bytes and PSK keys of up to 64 bytes in length as required by [RFC4279].</p>
<ol style="list-style-type: upper-alpha">

##### E.1.1.2 Raw-Public Key (RPK) Mode

</ol>
<p>The raw-public key mode requires a public key and a private key of the appropriate type and length for the cipher suite used. These keys are carried as a sequence of binary bytes with the public key stored in the Public Key or Identity Resource, and the private key stored in the Secret Key Resource. The public key MUST be encoded using the SubjectPublicKeyInfo structure, as described in [RFC7250].</p>
<p>The private key is stored in the Secret Key Resource, encoded as OneAsymetricKey as defined in [RFC5958].</p>
<ol style="list-style-type: upper-alpha">

##### E.1.1.3 Certificate Mode

</ol>
<p>The Certificate mode requires an X.509v3 Certificate along with a matching private key. The private key is stored in the Secret Key Resource, encoded as OneAsymetricKey as defined in  [RFC5958]. The certificate in a DER encoded binary format is stored in the Public Key or Identity Resource.</p>
<ol style="list-style-type: upper-alpha">

### E.1.2 SMS Payload Security: Security Key Resource Format

</ol>
<p>This section defines the format of the Secret Key and Public Key and Identity resources of the LwM2M Server and LwM2M Bootstrap Objects when using SMS Payload security. These resources are used to configure keying material that a Client uses with a particular Server. The Objects are configured on the Client using one of the Bootstrap mechanisms described in Section 5.1. The use of this keying material is defined in Section 7.2.</p>
<p>The SMS key parameters are stored in the order KIc, KID, SPI, TAR (KIc is byte 0).</p>
<p>Ordering of bits within bytes SHALL follow ETSI TS 102 221, section 3.4 “Coding Conventions” (b8 MSB, b1 LSB).</p>
<ol style="list-style-type: upper-alpha">

#### E.1.3 Unbootstrapping

</ol>
<p>Unbootstrapping is the process of deleting a Security Object Instance. If a Security Object Instance is to be deleted, certain related resources and configurations need to be deleted or modified. Therefore, when the Delete operation is sent via the Bootstrap Interface, the Client MUST execute the following procedure.</p>
<ol style="list-style-type: decimal">
<li><blockquote>
<p>If there is an Object Instance that can be accessed only by a Server of the Server Object Instance (i.e., the Server is Access Control Owner and the LwM2M Server can access the Object Instance only in an Access Control Object Instance), the Object Instance and the corresponding Access Control Object Instance MUST be deleted</p>
</blockquote></li>
<li><blockquote>
<p>If an Object Instance can be accessed by multiple Servers including the Server which Security Object Instance is to be deleted, then:</p>
</blockquote>
<ul>
<li><blockquote>
<p>The ACL Resource Instance for the Server in the Access Control Object Instance for the Object Instance MUST be deleted</p>
</blockquote></li>
<li><blockquote>
<p>If the Server is the Access Control Owner of the Access Control Object Instance, then the Access Control Owner MUST be changed to another Server according to the rules below:<br />
The Client MUST choose the Server who has highest sum of each number assigned to an access right (Write: 1, Delete: 1) for the Access Control Owner. If two or more Servers have the same sum, the Client MUST choose one of them as the new Access Control Owner</p>
</blockquote></li>
</ul></li>
<li><blockquote>
<p>Observation operations from the Server MUST be deleted</p>
</blockquote></li>
<li><blockquote>
<p>Server Object Instance MUST be deleted</p>
</blockquote></li>
<li><blockquote>
<p>Client MAY send “De-register” operation to the Server</p>
</blockquote></li>
</ol>
<p>Note: To monitor the change of the Access Control Owner, the Server MAY observe Access Control Owner Resource.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><span id="_Ref368312933" class="anchor"><span id="_Ref368313249" class="anchor"></span></span></td>
<td></td>
</tr>
</tbody>
</table>

### E.2	LwM2M Object: LwM2M Server

<strong>Description</strong>

This LwM2M Objects provides the data related to a LwM2M Server. A Bootstrap-Server has no such an Object Instance associated to it.

<strong>Object definition</strong>

<table>
<thead>
<tr class="header">
<th><strong>Name</strong></th>
<th><strong>Object ID</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Object URN</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>LwM2M Server</td>
<td>1</td>
<td>Multiple</td>
<td>Mandatory</td>
<td>urn:oma:lwm2m:oma:1:1.1</td>
</tr>
</tbody>
</table>

<strong>Resource definitions</strong>

<table>
<thead>
<tr class="header">
<th><strong>ID</strong></th>
<th><strong>Name</strong></th>
<th><strong>Operations</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Type</strong></th>
<th><strong>Range or Enumeration</strong></th>
<th><strong>Units</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0</td>
<td>Short Server ID</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td>1-65534</td>
<td></td>
<td>Used as link to associate server Object Instance.</td>
</tr>
<tr class="even">
<td>1</td>
<td>Lifetime</td>
<td>RW</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td></td>
<td>s</td>
<td>Specify the lifetime of the registration in seconds (see Section 5.3 Registration)</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Default Minimum Period</td>
<td>RW</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>s</td>
<td>The default value the LwM2M Client should use for the Minimum Period of an Observation in the absence of this parameter being included in an Observation.<br />
If this Resource doesn’t exist, the default value is 0.</td>
</tr>
<tr class="even">
<td>3</td>
<td>Default Maximum Period</td>
<td>RW</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>s</td>
<td>The default value the LwM2M Client should use for the Maximum Period of an Observation in the absence of this parameter being included in an Observation.</td>
</tr>
<tr class="odd">
<td>4</td>
<td>Disable</td>
<td>E</td>
<td>Single</td>
<td>Optional</td>
<td></td>
<td></td>
<td></td>
<td>If this Resource is executed, this LwM2M Server Object is disabled for a certain period defined in the Disabled Timeout Resource. After receiving “Execute” operation, LwM2M Client MUST send response of the operation and perform de-registration process, and underlying network connection between the Client and Server MUST be disconnected to disable the LwM2M Server account.<br />
After the above process, the LwM2M Client MUST NOT send any message to the Server and ignore all the messages from the LwM2M Server for the period.</td>
</tr>
<tr class="even">
<td>5</td>
<td>Disable Timeout</td>
<td>RW</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>s</td>
<td>A period to disable the Server. After this period, the LwM2M Client MUST perform registration process to the Server. If this Resource is not set, a default timeout value is 86400 (1 day).</td>
</tr>
<tr class="odd">
<td>6</td>
<td>Notification Storing When Disabled or Offline</td>
<td>RW</td>
<td>Single</td>
<td>Mandatory</td>
<td>Boolean</td>
<td></td>
<td></td>
<td>If true, the LwM2M Client stores “Notify” operations to the LwM2M Server while the LwM2M Server account is disabled or the LwM2M Client is offline. After the LwM2M Server account is enabled or the LwM2M Client is online, the LwM2M Client reports the stored “Notify” operations to the Server.<br />
If false, the LwM2M Client discards all the “Notify” operations or temporarily disables the Observe function while the LwM2M Server is disabled or the LwM2M Client is offline.<br />
The default value is true.<br />
The maximum number of storing Notifications per Server is up to the implementation.</td>
</tr>
<tr class="even">
<td>7</td>
<td>Binding</td>
<td>RW</td>
<td>Single</td>
<td>Mandatory</td>
<td>String</td>
<td>The possible values of Resource are listed in 5.3.1.1</td>
<td></td>
<td>This Resource defines the transport binding configured for the LwM2M Client.<br />
If the LwM2M Client supports the binding specified in this Resource, the LwM2M Client MUST use that transport for the Current Binding Mode.</td>
</tr>
<tr class="odd">
<td>8</td>
<td>Registration Update Trigger</td>
<td>E</td>
<td>Single</td>
<td>Mandatory</td>
<td></td>
<td></td>
<td></td>
<td>If this Resource is executed the LwM2M Client MUST perform an “Update” operation with this LwM2M Server using the relevant transport for the current Binding Mode.</td>
</tr>
<tr class="even">
<td>9</td>
<td>Bootstrap-Request Trigger</td>
<td>E</td>
<td>Single</td>
<td>Optional</td>
<td></td>
<td></td>
<td></td>
<td>When this Resource is executed the LwM2M Client MUST initiate a "Client Initiated Bootstrap" procedure in using the LwM2M Bootstrap-Server Account.</td>
</tr>
</tbody>
</table>


### E.3	LwM2M Object: Access Control

<strong>Description</strong>

Access Control Object is used to check whether the LwM2M Server has access right for performing an operation.

<strong>Object definition</strong>

<table>
<thead>
<tr class="header">
<th><strong>Name</strong></th>
<th><strong>Object ID</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Object URN</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>LwM2M Access Control</td>
<td>2</td>
<td>Multiple</td>
<td>Optional</td>
<td>urn:oma:lwm2m:oma:2:1.1</td>
</tr>
</tbody>
</table>

<strong>Resource definitions</strong>

<table>
<thead>
<tr class="header">
<th><strong>ID</strong></th>
<th><strong>Name</strong></th>
<th><strong>Operations</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Type</strong></th>
<th><strong>Range or Enumeration</strong></th>
<th><strong>Units</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0</td>
<td>Object ID</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td>1-65535</td>
<td></td>
<td>Resources 0 and 1 point to the Object Instance for which the Instances of the ACL Resource of that Access Control Object Instance are applicable.</td>
</tr>
<tr class="even">
<td>1</td>
<td>Object Instance ID</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td>0-65535</td>
<td></td>
<td>See above</td>
</tr>
<tr class="odd">
<td>2</td>
<td>ACL</td>
<td>RW</td>
<td>Multiple</td>
<td>Optional</td>
<td>Integer</td>
<td>16-bit</td>
<td></td>
<td>The Resource Instance ID MUST be the Short Server ID of a certain LwM2M Server for which associated access rights are contained in the Resource Instance value.<br />
The Resource Instance ID 0 is a specific ID, determining the ACL Instance which contains the default access rights.<br />
Each bit set in the Resource Instance value, grants an access right to the LwM2M Server to the corresponding operation.<br />
The bit order is specified as below.<br />
1st LSB: R(Read, Observe, Write-Attributes)<br />
2nd LSB: W(Write)<br />
3rd LSB: E(Execute)<br />
4th LSB: D(Delete)<br />
5th LSB: C(Create)<br />
Other bits are reserved for future use.</td>
</tr>
<tr class="even">
<td>3</td>
<td>Access Control Owner</td>
<td>RW</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td>1-65535</td>
<td></td>
<td><p>Short Server ID of a certain LwM2M Server; only such an LwM2M Server can manage the Resources of this Object Instance.</p>
<p>The specific value MAX_ID=65535 means this Access Control Object Instance is created and modified during a Bootstrap phase only.</p></td>
</tr>
</tbody>
</table>


### E.4	LwM2M Object: Device

</span><strong>Description</strong>

This LwM2M Object provides a range of device related information which can be queried by the LwM2M Server, and a device reboot and factory reset function.

<strong>Object definition</strong>

<table>
<thead>
<tr class="header">
<th><strong>Name</strong></th>
<th><strong>Object ID</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Object URN</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Device</td>
<td>3</td>
<td>Single</td>
<td>Mandatory</td>
<td>urn:oma:lwm2m:oma:3</td>
</tr>
</tbody>
</table></td>
</tr>
<tr class="even">
<td><strong>Resource definitions</strong></td>
</tr>
<tr class="odd">
<td><table>
<thead>
<tr class="header">
<th><strong>ID</strong></th>
<th><strong>Name</strong></th>
<th><strong>Operations</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Type</strong></th>
<th><strong>Range or Enumeration</strong></th>
<th><strong>Units</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0</td>
<td>Manufacturer</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Human readable manufacturer name</td>
</tr>
<tr class="even">
<td>1</td>
<td>Model Number</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>A model identifier (manufacturer specified string)</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Serial Number</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Serial Number</td>
</tr>
<tr class="even">
<td>3</td>
<td>Firmware Version</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Current firmware version of the Device. The Firmware Management function could rely on this resource.</td>
</tr>
<tr class="odd">
<td>4</td>
<td>Reboot</td>
<td>E</td>
<td>Single</td>
<td>Mandatory</td>
<td></td>
<td></td>
<td></td>
<td>Reboot the LwM2M Device to restore the Device from unexpected firmware failure.</td>
</tr>
<tr class="even">
<td>5</td>
<td>Factory Reset</td>
<td>E</td>
<td>Single</td>
<td>Optional</td>
<td></td>
<td></td>
<td></td>
<td>Perform factory reset of the LwM2M Device to make the LwM2M Device to go through initial deployment sequence where provisioning and bootstrap sequence is performed. This requires client ensuring post factory reset to have minimal information to allow it to carry out one of the bootstrap methods specified in section 5.2.3.<br />
When this Resource is executed, “De-register” operation MAY be sent to the LwM2M Server(s) before factory reset of the LwM2M Device.</td>
</tr>
<tr class="odd">
<td>6</td>
<td>Available Power Sources</td>
<td>R</td>
<td>Multiple</td>
<td>Optional</td>
<td>Integer</td>
<td>0-7</td>
<td></td>
<td>0 – DC power<br />
1 – Internal Battery<br />
2 – External Battery<br />
4 – Power over Ethernet<br />
5 – USB<br />
6 – AC (Mains) power<br />
7 – Solar<br />
<br />
The same Resource Instance ID MUST be used to associate a given Power Source (Resource ID:6) with its Present Voltage (Resource ID:7) and its Present Current (Resource ID:8)</td>
</tr>
<tr class="even">
<td>7</td>
<td>Power Source Voltage</td>
<td>R</td>
<td>Multiple</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>mV</td>
<td>Present voltage for each Available Power Sources Resource Instance.</td>
</tr>
<tr class="odd">
<td>8</td>
<td>Power Source Current</td>
<td>R</td>
<td>Multiple</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>mA</td>
<td>Present current for each Available Power Source.</td>
</tr>
<tr class="even">
<td>9</td>
<td>Battery Level</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td>0-100</td>
<td>%</td>
<td>Contains the current battery level as a percentage (with a range from 0 to 100). This value is only valid for the Device Internal Battery if present (one Available Power Sources Resource Instance is 1).</td>
</tr>
<tr class="odd">
<td>10</td>
<td>Memory Free</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td>KB</td>
<td>Estimated current available amount of storage space which can store data and software in the LwM2M Device (expressed in kilobytes).</td>
</tr>
<tr class="even">
<td>11</td>
<td>Error Code</td>
<td>R</td>
<td>Multiple</td>
<td>Mandatory</td>
<td>Integer</td>
<td>0-8</td>
<td></td>
<td>0=No error<br />
1=Low battery power<br />
2=External power supply off<br />
3=GPS module failure<br />
4=Low received signal strength<br />
5=Out of memory<br />
6=SMS failure<br />
7=IP connectivity failure<br />
8=Peripheral malfunction<br />
<br />
When the single Device Object Instance is initiated, there is only one error code Resource Instance whose value is equal to 0 that means no error. When the first error happens, the LwM2M Client changes error code Resource Instance to any non-zero value to indicate the error type. When any other error happens, a new error code Resource Instance is created. When an error associated with a Resource Instance is no longer present, that Resource Instance is deleted. When the single existing error is no longer present, the LwM2M Client returns to the original no error state where Instance 0 has value 0.<br />
This error code Resource MAY be observed by the LwM2M Server. How to deal with LwM2M Client’s error report depends on the policy of the LwM2M Server.</td>
</tr>
<tr class="odd">
<td>12</td>
<td>Reset Error Code</td>
<td>E</td>
<td>Single</td>
<td>Optional</td>
<td></td>
<td></td>
<td></td>
<td>Delete all error code Resource Instances and create only one zero-value error code that implies no error, then re-evaluate all error conditions and update and create Resources Instances to capture all current error conditions.</td>
</tr>
<tr class="even">
<td>13</td>
<td>Current Time</td>
<td>RW</td>
<td>Single</td>
<td>Optional</td>
<td>Time</td>
<td></td>
<td></td>
<td>Current UNIX time of the LwM2M Client.<br />
The LwM2M Client should be responsible to increase this time value as every second elapses.<br />
The LwM2M Server is able to write this Resource to make the LwM2M Client synchronized with the LwM2M Server.</td>
</tr>
<tr class="odd">
<td>14</td>
<td>UTC Offset</td>
<td>RW</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Indicates the UTC offset currently in effect for this LwM2M Device. UTC+X [ISO 8601].</td>
</tr>
<tr class="even">
<td>15</td>
<td>Timezone</td>
<td>RW</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Indicates in which time zone the LwM2M Device is located, in IANA Timezone (TZ) database format.</td>
</tr>
<tr class="odd">
<td>16</td>
<td>Supported Binding and Modes</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>String</td>
<td></td>
<td></td>
<td>Indicates which bindings and modes are supported in the LwM2M Client. The possible values of Resource are combination of &quot;U&quot; or &quot;UQ&quot; and &quot;S&quot; or &quot;SQ&quot;.</td>
</tr>
<tr class="even">
<td>17</td>
<td>Device Type</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Type of the device (manufacturer specified string: e.g., smart meters / dev Class…)</td>
</tr>
<tr class="odd">
<td>18</td>
<td>Hardware Version</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Current hardware version of the device</td>
</tr>
<tr class="even">
<td>19</td>
<td>Software Version</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Current software version of the device (manufacturer specified string). On elaborated LwM2M device, SW could be split in 2 parts: a firmware one and a higher level software on top.<br />
Both pieces of Software are together managed by LwM2M Firmware Update Object (Object ID 5)</td>
</tr>
<tr class="odd">
<td>20</td>
<td>Battery Status</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td>0-6</td>
<td></td>
<td><p>This value is only valid for the Device Internal Battery if present (one Available Power Sources Resource Instance value is 1).</p>
<table>
<thead>
<tr class="header">
<th><p><strong>Battery</strong></p>
<p><strong>Status</strong></p></th>
<th><strong>Meaning</strong></th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0</td>
<td>Normal</td>
<td>The battery is operating normally and not on power.</td>
</tr>
<tr class="even">
<td>1</td>
<td>Charging</td>
<td>The battery is currently charging.</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Charge Complete</td>
<td>The battery is fully charged and still on power.</td>
</tr>
<tr class="even">
<td>3</td>
<td>Damaged</td>
<td>The battery has some problem.</td>
</tr>
<tr class="odd">
<td>4</td>
<td>Low Battery</td>
<td>The battery is low on charge.</td>
</tr>
<tr class="even">
<td>5</td>
<td>Not Installed</td>
<td>The battery is not installed.</td>
</tr>
<tr class="odd">
<td>6</td>
<td>Unknown</td>
<td>The battery information is not available.</td>
</tr>
</tbody>
</table></td>
</tr>
<tr class="even">
<td>21</td>
<td>Memory Total</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td></td>
<td>Total amount of storage space which can store data and software in the LwM2M Device (expressed in kilobytes).</td>
</tr>
<tr class="odd">
<td>22</td>
<td>ExtDevInfo</td>
<td>R</td>
<td>Multiple</td>
<td>Optional</td>
<td>Objlnk</td>
<td></td>
<td></td>
<td>Reference to external “Device” object instance containing information. For example, such an external device can be a Host Device, which is a device into which the Device containing the LwM2M client is embedded. This Resource may be used to retrieve information about the Host Device.</td>
</tr>
</tbody>
</table>
 
 

### E.5	LWM2M Object: Connectivity Monitoring

</span><strong>Description</strong>

This LwM2M Object enables monitoring of parameters related to network connectivity.<br />
In this general connectivity Object, the Resources are limited to the most general cases common to most network bearers. It is recommended to read the description, which refers to relevant standard development organizations (e.g., 3GPP, IEEE).<br />
The goal of the Connectivity Monitoring Object is to carry information reflecting the more up to date values of the current connection for monitoring purposes. Resources such as Link Quality, Radio Signal Strength, Cell ID are retrieved during connected mode at least for cellular networks.

<strong>Object definition</strong>

<table>
<thead>
<tr class="header">
<th><strong>Name</strong></th>
<th><strong>Object ID</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Object URN</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Connectivity Monitoring</td>
<td>4</td>
<td>Single</td>
<td>Optional</td>
<td>urn:oma:lwm2m:oma:4</td>
</tr>
</tbody>
</table></td>
<td></td>
</tr>
<tr class="even">
<td><strong>Resource definitions</strong></td>
<td></td>
</tr>
<tr class="odd">
<td><table>
<thead>
<tr class="header">
<th><strong>ID</strong></th>
<th><strong>Name</strong></th>
<th><strong>Operations</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Type</strong></th>
<th><strong>Range or Enumeration</strong></th>
<th><strong>Units</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0</td>
<td>Network Bearer</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td></td>
<td></td>
<td>Indicates the network bearer used for the current LwM2M communication session from the below network bearer list.<br />
0~20 are Cellular Bearers<br />
0: GSM cellular network<br />
1: TD-SCDMA cellular network<br />
2: WCDMA cellular network<br />
3: CDMA2000 cellular network<br />
4: WiMAX cellular network<br />
5: LTE-TDD cellular network<br />
6: LTE-FDD cellular network<br />
7: NB-IoT<br />
8~20: Reserved for other type cellular network<br />
21~40 are Wireless Bearers<br />
21: WLAN network<br />
22: Bluetooth network<br />
23: IEEE 802.15.4 network<br />
24~40: Reserved for other type local wireless network<br />
41~50 are Wireline Bearers<br />
41: Ethernet<br />
42: DSL<br />
43: PLC<br />
44~50: reserved for others type wireline networks.</td>
</tr>
<tr class="even">
<td>1</td>
<td>Available Network Bearer</td>
<td>R</td>
<td>Multiple</td>
<td>Mandatory</td>
<td>Integer</td>
<td></td>
<td></td>
<td>Indicates list of current available network bearer. Each Resource Instance has a value from the network bearer list.</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Radio Signal Strength</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td></td>
<td>dBm</td>
<td><p>This node contains the average value of the received signal strength indication used in the current network bearer (as indicated by Resource 0 of this Object).</p>
<p>For the following network bearers the signal strength parameters indicated below are represented by this resource:<br />
GSM: RSSI<br />
UMTS: RSCP<br />
LTE: RSRP<br />
NB-IoT: NRSRP</p>
<p>For the following network bearers the signal strength parameters indicated below are represented by this resource:<br />
GSM: RSSI<br />
UMTS: RSCP<br />
LTE: RSRP</p>
<p>For more details on Network Measurement Report, refer to the appropriate Cellular or Wireless Network standards. (e.g., for LTE Cellular Network refer to ETSI TS 36.133 specification).</p></td>
</tr>
<tr class="even">
<td>3</td>
<td>Link Quality</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td></td>
<td>This contains received link quality e.g.<br />
LQI for IEEE 802.15.4 (range 0..255), RxQual Downlink for GSM (range 0…7, refer to [3GPP 44.018] for more details on Network Measurement Report encoding),<br />
RSRQ for LTE, (refer to [3GPP 36.214]),<br />
NRSRQ for NB-IoT (refer to [3GPP 36.214]).</td>
</tr>
<tr class="odd">
<td>4</td>
<td>IP Addresses</td>
<td>R</td>
<td>Multiple</td>
<td>Mandatory</td>
<td>String</td>
<td></td>
<td></td>
<td>The IP addresses assigned to the connectivity interface. (e.g., IPv4, IPv6, etc.)</td>
</tr>
<tr class="even">
<td>5</td>
<td>Router IP Addresses</td>
<td>R</td>
<td>Multiple</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>The IP address of the next-hop IP router, on each of the interfaces specified in resource 4 (IP Addresses)<br />
Note: This IP Address doesn’t indicate the Server IP address.</td>
</tr>
<tr class="odd">
<td>6</td>
<td>Link Utilization</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td>0-100</td>
<td>%</td>
<td>The average utilization of the link to the next-hop IP router in %.</td>
</tr>
<tr class="even">
<td>7</td>
<td>APN</td>
<td>R</td>
<td>Multiple</td>
<td>Optional</td>
<td>String</td>
<td></td>
<td></td>
<td>Access Point Name in case Network Bearer Resource is a Cellular Network.</td>
</tr>
<tr class="odd">
<td>8</td>
<td>Cell ID</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td></td>
<td>Serving Cell ID in case Network Bearer Resource is a Cellular Network.<br />
As specified in TS [3GPP_TS_23.003] and in [3GPP_TS_24.008]. Range (0…65535) in GSM/EDGE<br />
UTRAN Cell ID has a length of 28 bits.<br />
Cell Identity in WCDMA/TD-SCDMA. Range: (0..268435455).<br />
LTE Cell ID has a length of 28 bits.<br />
Parameter definitions in [3GPP_TS_25.331].</td>
</tr>
<tr class="even">
<td>9</td>
<td>SMNC</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td></td>
<td>Serving Mobile Network Code. In case Network Bearer Resource has 0(cellular network). Range (0…999).<br />
As specified in TS [3GPP_TS_23.003].</td>
</tr>
<tr class="odd">
<td>10</td>
<td>SMCC</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td></td>
<td>Serving Mobile Country Code. In case Network Bearer Resource has 0 (cellular network). Range (0…999).<br />
As specified in TS [3GPP_TS_23.003].</td>
</tr>
</tbody>
</table>


### E.6	LwM2M Object: Firmware Update


<strong>Description</strong>

This LwM2M Object enables management of firmware which is to be updated. This Object includes installing firmware package, updating firmware, and performing actions after updating firmware. The firmware update MAY require to reboot the device; it will depend on a number of factors, such as the operating system architecture and the extent of the updated software.</p>
<p>The envisioned functionality with LwM2M version 1.0 is to allow a LwM2M Client to connect to any LwM2M version 1.0 compliant Server to obtain a firmware image using the object and resource structure defined in this section experiencing communication security protection using DTLS. There are, however, other design decisions that need to be taken into account to allow a manufacturer of a device to securely install firmware on a device. Examples for such design decisions are how to manage the firmware update repository at the server side (which may include user interface considerations), the techniques to provide additional application layer security protection of the firmware image, how many versions of firmware image to store on the device, and how to execute the firmware update process considering the hardware specific details of a given IoT hardware product. These aspects are considered to be outside the scope of the LwM2M version 1.0 specification.</p>
<p>A LwM2M Server may also instruct a LwM2M Client to fetch a firmware image from a dedicated server (instead of pushing firmware image to the LwM2M Client). The Package URI resource is contained in the Firmware object and can be used for this purpose.</p>
<p>A LwM2M Client MUST support block-wise transfer [CoAP_Blockwise] if it implements the Firmware Update object.</p>
<p>A LwM2M Server MUST support block-wise transfer. Other protocols, such as HTTP/HTTPs, MAY also be used for downloading firmware updates (via the Package URI resource). For constrained devices it is, however, RECOMMENDED to use CoAP for firmware downloads to avoid the need for additional protocol implementations.</p>
<p>Once a new firmware image is successfully installed in the Device, if the Resource “Firmware Version” ID:3 is available in the Instance of the Device Object (ID:3) the LwM2M Client MUST update such a Resource accordingly to the new firmware image version.</p>
<p>Note : PkgName (ID:6) and PkgVersion (ID:7) Resources contain optional information handled by the Firmware Update functionality for its own purpose and have no direct correlation with the “Firmware Version” ID:3 of Device Object ID:3.</p>

<strong>Object definition</strong>

<table>
<thead>
<tr class="header">
<th><strong>Name</strong></th>
<th><strong>Object ID</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Object URN</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Firmware Update</td>
<td>5</td>
<td>Single</td>
<td>Optional</td>
<td>urn:oma:lwm2m:oma:5</td>
</tr>
</tbody>
</table>


<strong>Resource definitions</strong>

<table>
<thead>
<tr class="header">
<th><strong>ID</strong></th>
<th><strong>Name</strong></th>
<th><strong>Operations</strong></th>
<th><strong>Instances</strong></th>
<th><strong>Mandatory</strong></th>
<th><strong>Type</strong></th>
<th><strong>Range or Enumeration</strong></th>
<th><strong>Units</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>0</td>
<td>Package</td>
<td>W</td>
<td>Single</td>
<td>Mandatory</td>
<td>Opaque</td>
<td></td>
<td></td>
<td>Firmware package</td>
</tr>
<tr class="even">
<td>1</td>
<td>Package URI</td>
<td>RW</td>
<td>Single</td>
<td>Mandatory</td>
<td>String</td>
<td>0-255 bytes</td>
<td></td>
<td>URI from where the device can download the firmware package by an alternative mechanism. As soon the device has received the Package URI it performs the download at the next practical opportunity.<br />
The URI format is defined in RFC 3986. For example, coaps://example.org/firmware is a syntactically valid URI. The URI scheme determines the protocol to be used. For CoAP this endpoint MAY be a LwM2M Server but does not necessarily need to be. A CoAP server implementing block-wise transfer is sufficient as a server hosting a firmware repository and the expectation is that this server merely serves as a separate file server making firmware images available to LwM2M Clients.</td>
</tr>
<tr class="odd">
<td>2</td>
<td>Update</td>
<td>E</td>
<td>Single</td>
<td>Mandatory</td>
<td>none</td>
<td></td>
<td></td>
<td>Updates firmware by using the firmware package stored in Package, or, by using the firmware downloaded from the Package URI.<br />
This Resource is only executable when the value of the State Resource is Downloaded.</td>
</tr>
<tr class="even">
<td>3</td>
<td>State</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td>0-3</td>
<td></td>
<td><p>Indicates current state with respect to this firmware update. This value is set by the LwM2M Client.<br />
0: Idle (before downloading or after successful updating)<br />
1: Downloading (The data sequence is on the way)<br />
2: Downloaded<br />
3: Updating<br />
If writing the firmware package to Package Resource is done, or, if the device has downloaded the firmware package from the Package URI the state changes to Downloaded.<br />
Writing an empty string to Package URI Resource or setting the Package Resource to NULL (‘\0’), resets the Firmware Update State Machine: the State Resource value is set to Idle and the Update Result Resource value is set to 0.</p>
<p>When in Downloaded state, and the executable Resource Update is triggered, the state changes to Updating.<br />
If the Update Resource failed, the state returns at Downloaded.<br />
If performing the Update Resource was successful, the state changes from Updating to Idle.</p>
<p>Firmware Update mechanisms are illustrated below in Figure 20 of the LwM2M version 1.0 specification.</p></td>
</tr>
<tr class="odd">
<td>5</td>
<td>Update Result</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td>0-9</td>
<td></td>
<td><p>Contains the result of downloading or updating the firmware<br />
0: Initial value. Once the updating process is initiated (Download /Update), this Resource MUST be reset to Initial value.<br />
1: Firmware updated successfully,<br />
2: Not enough flash memory for the new firmware package.<br />
3. Out of RAM during downloading process.<br />
4: Connection lost during downloading process.<br />
5: Integrity check failure for new downloaded package.<br />
6: Unsupported package type.<br />
7: Invalid URI</p>
<p>8: Firmware update failed<br />
9: Unsupported protocol. A LwM2M client indicates the failure to retrieve the firmware image using the URI provided in the Package URI resource by writing the value 9 to the /5/0/5 (Update Result resource) when the URI contained a URI scheme unsupported by the client. Consequently, the LwM2M Client is unable to retrieve the firmware image using the URI provided by the LwM2M Server in the Package URI when it refers to an unsupported protocol.</p></td>
</tr>
<tr class="even">
<td>6</td>
<td>PkgName</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td>0-255 bytes</td>
<td></td>
<td>Name of the Firmware Package</td>
</tr>
<tr class="odd">
<td>7</td>
<td>PkgVersion</td>
<td>R</td>
<td>Single</td>
<td>Optional</td>
<td>String</td>
<td>0-255 bytes</td>
<td></td>
<td>Version of the Firmware package</td>
</tr>
<tr class="even">
<td>8</td>
<td>Firmware Update Protocol Support</td>
<td>R</td>
<td>Multiple</td>
<td>Optional</td>
<td>Integer</td>
<td></td>
<td></td>
<td><p>This resource indicates what protocols the LwM2M Client implements to retrieve firmware images. The LwM2M server uses this information to decide what URI to include in the Package URI. A LwM2M Server MUST NOT include a URI in the Package URI object that uses a protocol that is unsupported by the LwM2M client.</p>
<p>For example, if a LwM2M client indicates that it supports CoAP and CoAPS then a LwM2M Server must not provide an HTTP URI in the Packet URI.</p>
<p>The following values are defined by this version of the specification:</p>
<p>0 – CoAP (as defined in RFC 7252) with the additional support for block-wise transfer. CoAP is the default setting.</p>
<p>1 – CoAPS (as defined in RFC 7252) with the additional support for block-wise transfer</p>
<p>2 – HTTP 1.1 (as defined in RFC 7230)</p>
<p>3 – HTTPS 1.1 (as defined in RFC 7230)</p>
<p>Additional values MAY be defined in the future. Any value not understood by the LwM2M Server MUST be ignored.</p></td>
</tr>
<tr class="odd">
<td>9</td>
<td>Firmware Update Delivery Method</td>
<td>R</td>
<td>Single</td>
<td>Mandatory</td>
<td>Integer</td>
<td></td>
<td></td>
<td><p>The LwM2M Client uses this resource to indicate its support for transferring firmware images to the client either via the Package Resource (=push) or via the Package URI Resource (=pull) mechanism.</p>
<p>0 – Pull only</p>
<p>1 – Push only</p>
<p>2 – Both. In this case the LwM2M Server MAY choose the preferred mechanism for conveying the firmware image to the LwM2M Client.</p></td>
</tr>
</tbody>
</table>


#### E.6.1	Firmware Update State Machine

<p>Figure 20 shows a possible implementation of the firmware update mechanism, described as a UML 2.0 state diagram. The state diagram consists of states, drawn as rounded rectangles, and transitions, drawn as arrows connecting the states. The syntax of the transition is trigger [guard] / behaviour. A trigger is an event that may cause a transition, guard is a condition and behaviour is an activity that executes while the transition takes place. The states additionally contain a compartment that includes assertions and variable assignments. For example, the assertion in the IDLE state indicates the value of the “Update Result” resource (abbreviated as “Res”) must be between 0 and 9. The State resource is set to zero (0) when the program is in this IDLE state.</p>
<p>Errors during the Firmware Update process MUST be reported only by the “Update Result” resource. For instance, when the LwM2M Server performs a Write operation on resource “Package URI”, the LwM2M Client returns a Success or Failure for the Write operation. Then if the URI is invalid, it changes its “Update Result” resource value to 7.</p>

![alt text](images/firmware_update_mechanisms.png "Figure 20: Firmware Update Mechanisms") 
```
Figure 20: Firmware Update Mechanisms
```

#### E.6.2	Examples

<p>The example depicted in Figure 30 illustrates a successful message exchange where a LwM2M Server pushes a firmware image to a LwM2M Client using the block-wise transfer. In this example the LwM2M Server indicates a block size of 128 bytes and the firmware image of 80 KiB (=81920 bytes) will be sent to the LwM2M Client in 640 messages with each 128 bytes payload. Since the LwM2M Server-provided block size matches the preferences of the LwM2M Client the exchange proceeds until the full firmware image is downloaded. In this example, no messages are lost during transmission.</p>

```
   LwM2M                                                  LwM2M 
   Server                                                 Client
   |                                                          |
   | CON [MID=1], POST, /5/0/0, 1:0/1/128       ------>       |
   |                                                          |
   | <------   ACK [MID=1], 2.31 Continue, 1:0/1/128          |
   |                                                          |
   | CON [MID=2], POST, /5/0/0, 1:1/1/128       ------>       |
   |                                                          |
   | <------   ACK [MID=2], 2.31 Continue, 1:1/1/128          |
   |                                                          |
   |               ... 637 exchanges ...                      |
   |                                                          |
   | CON [MID=640], POST, /5/0/0, 1:639/0/128   ------>       |
   |                                                          |  
   | <------   ACK [MID=640], 2.04 Changed, 1:639/0/128       |
   |                                                          |
```
```
Figure 30: Example of a LwM2M Server pushing a firmware image to a LwM2M client
```

<p>The second example shown in Figure 31 illustrates the case where the client was provided with a URI by the LwM2M Server (using the Package URI resource) and therefore fetches the firmware image from the indicated server. Note that only the retrieval of the firmware image from the LwM2M Server is shown in Figure 31 and not the initial configuration of the Package URI.</p>

```
   LwM2M                                                       LwM2M    
   Client                                                      Server      
   |                                                           |      
   | CON [MID=1], GET, /firmware                       ------> |      
   |                                                           |      
   | <------   ACK [MID=1], 2.05 Content, 2:0/1/128            |      
   |                                                           |      
   | CON [MID=2], GET, /firmware, 2:1/0/128            ------> |      
   |                                                           |      
   | <------   ACK [MID=2], 2.05 Content, 2:1/1/128            |      
   |                                                           |      
   |               ... 637 exchanges ...                       |      
   |                                                           |      
   | CON [MID=640], GET, /firmware, 2:639/0/128         ------>|     
   |                                                           |      
   | <------   ACK [MID=640], 2.05 Content, 2:639/0/128        |      
   |                                                           |   
```
```
Figure 31: Example of a client fetching a firmware image
```

#### E.6.3	Firmware Update Consideration

<p>If some Objects are not supported after firmware update, the LwM2M Client MUST delete all Object Instances of the Objects that are not supported.</p>

### E.7	LwM2M Object: Location

<strong> Description </strong>

The LwM2M Location Object provides the ability to express a point (in 2d, and in 3d), a circle (in 2d) and a sphere (in 3d). This location information is used to indicate where the LwM2M Client is located at the indicated point in time. A point is used when there is no known uncertainty and it forms part of a number of other geometries. A point may be specified using either world geodetic system (WGS) 84 (latitude, longitude) or WGS 84 (latitude, longitude, altitude). The circular area is used for coordinates in two-dimensional coordinate reference systems (CRSs) to describe uncertainty about a point. It is specified using a two-dimensional CRS (using latitude, longitude). The sphere is a volume that provides the same information as a circle in three dimensions. It is specified using a three-dimensional CRS (using latitude, longitude, and altitude). The use of the world geodetic system 1984 (WGS84) coordinate reference system and the usage of European petroleum survey group (EPSG) code 4326 for two-dimensional (2d) shape representations and EPSG 4979 for three-dimensional (3d) volume representations is mandated. For the circle and the sphere a confidence value of 95% is assumed \[RFC7459\]. Finally, the ability to convey information about moving objects is enabled by expression of speed and velocity. 

<strong> Object definition </strong> 

<table>
 <tr>
  <td><strong> Name </strong></td><td><strong> Object ID </strong></td><td><strong>  Instances </strong></td><td><strong>  Mandatory </strong></td><td><strong> Object URN </strong></td>
 </tr>
 <tr>
  <td> Location </td><td>  6 </td><td> Single </td><td> Optional </td><td> urn:oma:lwm2m:oma:6 </td>
 </tr>
 </table>
 
 <strong> Resource definitions </strong> 
 
 <table>
 <tr>
  <td><strong> ID </strong></td><td><strong> Name </strong></td><td><strong> Operations </strong></td><td><strong> Instances </strong></td><td><strong> Mandatory </strong></td><td><strong> Type </strong></td><td><strong> Range or Enumeration </strong></td><td><strong> Units </strong></td><td><strong> Description </strong></td>
 </tr>
 <tr>
  <td> 0 </td><td> Latitude  </td><td>  R </td><td> Single </td><td>  Mandatory </td><td>  Float  </td><td>  </td><td>  Deg              </td><td> The decimal notation of latitude, e.g., -43.5723 [World Geodetic System 1984]. </td>
 </tr>
 <tr> 
  <td> 1 </td><td> Longitude </td><td>  R  </td><td>  Single </td><td>  Mandatory </td><td>  Float </td><td> </td><td>  Deg  </td><td>  The decimal notation of longitude, e.g., 153.21760 [World Geodetic System 1984]. </td>
 </tr>
 <tr>
  <td> 2 </td><td>  Altitude  </td><td>  R </td><td>  Single </td><td>  Optional </td><td>  Float </td><td> </td><td> m                 </td><td>  The decimal notation of altitude in meters above sea level.</td>
 </tr>
 <tr>
  <td> 3 </td><td>  Radius </td><td>  R </td><td>  Single </td><td>  Optional </td><td>  Float </td><td> </td><td> m  </td><td>  The value in the Radius Resource indicates the size in meters of a circular area around a point geometry. </td>
 </tr>
 <tr>
  <td> 4 </td><td>  Velocity </td><td>  R </td><td>  Single </td><td> Optional </td><td>  Opaque </td><td>  </td><td>                   </td><td>  The velocity of the LwM2M Client is defined in \[3GPP-TS\_23.032\]. </td>
 </tr>
 <tr>
  <td> 5 </td><td>  Timestamp </td><td>  R </td><td>  Single </td><td>  Mandatory </td><td>  Time </td><td>  </td><td> </td><td> The timestamp of when the location measurement was performed. </td>
 </tr>
 <tr>
  <tr> 
   <td> 6 </td><td>  Speed </td><td>  R  </td><td>  Single </td><td>  Optional </td><td>  Float </td><td>   </td><td>  Meters per second </td><td>  Speed is the time rate of change in position of a LwM2M Client without regard for direction: the scalar component of velocity. </td>
 </tr>
 </table>  

### E.8	LwM2M Object: Connectivity Statistics

<strong> Description </strong>                                                                                                         

This LwM2M Objects enables client to collect statistical information and enables the LwM2M Server to retrieve these information, set the collection duration and reset the statistical parameters.                                                                                                                                                                                                                    <strong> Object definition </strong>
<table>
 <tr>
  <td><strong> Name </strong></td><td><strong> Object ID </strong></td><td><strong>  Instances </strong></td><td><strong>  Mandatory </strong></td><td><strong> Object URN </strong></td>
 </tr>
 <tr>
  <td> Connectivity Statistics </td><td> 7 </td><td> Single  </td><td> Optional </td><td> urn:oma:lwm2m:oma:7 </td>
  </tr>
 </table>
 
 <strong> Resource definitions </strong>
  
  
  <table>
 <tr>
  <td><strong> ID </strong></td><td><strong> Name </strong></td><td><strong> Operations </strong></td><td><strong> Instances </strong></td><td><strong> Mandatory </strong></td><td><strong> Type </strong></td><td><strong> Range or Enumeration </strong></td><td><strong> Units </strong></td><td><strong> Description </strong></td>
 </tr>
 <tr>
  <td> 0  </td><td> SMS Tx Counter </td><td> R  </td><td> Single </td><td> Optional </td><td> Integer </td><td>  </td><td>  </td><td> Indicate the total number of SMS successfully transmitted during the collection period. </td>
 </tr>
 <tr>
  <td>  1 </td><td> SMS Rx Counter </td><td> R </td><td> Single </td><td> Optional </td><td> Integer </td><td>                          </td><td>  </td><td> Indicate the total number of SMS successfully received during the collection period. </td>
 </tr>
 <tr>
  <td> 2 </td><td> Tx Data </td><td> R </td><td> Single </td><td> Optional </td><td> Integer </td><td> </td><td> Kilo-Bytes </td><td> Indicate the total amount of IP data transmitted during the collection period.</td>
 </tr>
 <tr>
  <td> 3  </td><td> Rx Data </td><td> R  </td><td> Single </td><td> Optional </td><td> Integer </td><td>  </td><td> Kilo-Bytes</td><td> Indicate the total amount of IP data received during the collection period.  </td>
 </tr>
 <tr>
  <td> 4 </td><td> Max Message Size </td><td> R </td><td> Single </td><td> Optional </td><td> Integer </td><td> </td><td> Byte </td><td> The maximum IP message size that is used during the collection period. </td>
 </tr>
  <tr>
  <td> 5 </td><td> Average Message Size </td><td> R  </td><td> Single </td><td> Optional </td><td> Integer </td><td>                      </td><td> Byte </td><td> The average IP message size that is used during the collection period.</td>
 </tr>
 <tr>
   <td> 6 </td><td> Start </td><td> E </td><td> Single </td><td> Mandatory </td><td>  </td><td>  </td><td>  </td><td> Reset resources 0-5 to 0 and start to collect information, If resource 8 (Collection Period) value is 0, the client will keep collecting information until resource 7 (Stop) is executed, otherwise the client will stop collecting information after specified period ended. </td>
 </tr>
 <tr>
  <td> 7 </td><td> Stop </td><td> E </td><td> Single </td><td> Mandatory </td><td> </td><td> </td><td> </td><td> Stop collecting information, but do not reset resources 0-5. </td>
 </tr>
 <tr>
  <td> 8  </td><td> Collection Period </td><td> RW </td><td> Single  </td><td> Optional </td><td> Integer </td><td>                       </td><td> Seconds </td><td> The default collection period in seconds. The value 0 indicates that the collection period is not set.</td>
  </tr>
 </table>
 
 Note: When reporting the Tx Data or Rx Data, the LwM2M Client reports the total KB transmitted/received over IP bearer(s), including all protocol header bytes up to and including the IP header. This does not include lower level retransmissions/optimizations (e.g. RAN, header compression) or SMS messages.                                                                                                     
