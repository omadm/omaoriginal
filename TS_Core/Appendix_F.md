
<strong> Appendix F. Example LwM2M Client (Informative) </strong>

This appendix defines an example LwM2M Client for a simple imaginary device with a Cellular interface including instantiated Objects and their values, which is used throughout this specification in examples. The example client has the Endpoint Name “example-client”. The example device has two Server Objects (it is configured to register with two different LwM2M Servers), five accompanying Access Control Object Instances for those servers, a Device Object, a Connectivity Monitoring Object for a Cellular interface and a Firmware Update Object with no instance. The first Server controls the access control rights for both servers.

The Short Server ID 101 & 102, are respectively associated to the Server 1 and Server 2;


| Object                         | Object ID  | Object Instance ID |
|:--|:--|:--|
| **LwM2M Security Object\[0\]**     | 0              | 0                      |
| **LwM2M Security Object\[1\]**     | 0              | 1                      |
| **LwM2M Security Object\[2\]**     | 0              | 2                      |
| **LwM2M Server Object \[1\]**      | 1              | 0                      |
| **LwM2M Server Object \[2\]**      | 1              | 1                      |
| **Access Control Object \[0\]**    | 2              | 0                      |
| **Access Control Object \[1\]**    | 2              | 1                      |
| **Access Control Object \[2\]**    | 2              | 2                      |
| **Access Control Object \[3\]**    | 2              | 3                      |
| **Access Control Object \[4\]**    | 2              | 4                      |
| **Device Object**                  | 3              | 0                      |
| **Connectivity Monitoring Object** | 4              | 0                      |
| **Firmware Update Object**         | 5              | -                      |

```
Table 29: Object Instances of the example
```


| Resource Name |Resource ID|Resource Instance ID|Value|Notes|
|:--|:-:|:-:|:-:|:--|
| **LwM2M Server URI**| 0 |  |coaps://bootstrap.example.com | Example LwM2M Bootstrap-Server |
| **Bootstrap-Server**| 1 |  | true |   |
| **Security Mode**  | 2 |  | 0 | PSK mode |
| **Public Key or Identity** | 3 |  | b313cc22-f969-42ec-ad42 | Example of a PSK Identity string |
| **Server Public Key**      | 4 |  |   | Unused in PSK mode   |
| **Secret Key** | 5 |    | e129791359950cbb1c8c3c582913b551 | 128-bit random sequence in hex encoding for use as a PSK. |
| **Client Hold Off Time**   | 11  |    | 3600 |      |

```
Table 30: LwM2M Security Object [0]
```

| Resource Name |Resource ID|Resource Instance ID|Value|Notes|
|:--|:-:|:-:|:-:|:--|
| **LwM2M Server URI**       | 0               |                          | coaps://server1.example.com      | Example LwM2M Server 1                                    |
| **Bootstrap-Server**       | 1               |                          | false                            |                                                           |
| **Security Mode**          | 2               |                          | 0                                | PSK mode                                                  |
| **Public Key or Identity** | 3               |                          | b313cc22-f969-42ec-ad42          | Example of a PSK Identity string                          |
| **Server Public Key**      | 4               |                          |                                  | Unused in PSK mode                                        |
| **Secret Key**             | 5               |                          | 1ca2028d7197c778e9aef5ef69082bea | 128-bit random sequence in hex encoding for use as a PSK. |
| **Short Server ID**        | 10              |                          | 101                              |                                                           |

```
Table 31: LwM2M Security Object [1]
```

| Resource Name |Resource ID|Resource Instance ID|Value|Notes|
|:--|:-:|:-:|:-:|:--|
| **LwM2M Server URI**|0 |   | coaps://server2.example.com | Example LwM2M Server 2 |
|**Bootstrap-Server**| 1 | | false |
| **Security Mode** | 2 |   | 1 | RPK mode |
| **Public Key or Identity** | 3 |  | 3059301306072a8648ce3d020106082a8648ce3d03010703420004a09dcb1bc739e7f19afa9adcb1944968bfba73efcec29b50486eb44d1b29c193449970a3736830cb2bd5d7ec05d2bd1fc07b6df5e48b54ce77a6a7229c3a91c2  |  The raw public key of the LwM2M Client in ASN.1 DER format. The textual representation of the key can be found below labelled as \*.|
| **Server Public Key**| 4  |  | 3059301306072a8648ce3d020106082a8648ce3d0301070342000482c773f378d30c2783a48eb811b96cf6a90694a8564f1e7f6d366152f11698950f6f7c40cda585334f837750a102f5bf25508ceb9e55dfc0f12a455199a4c960 | The raw public key of the LwM2M Server in ASN.1 DER format. The textual representation of the key can be found below labelled as \** . |
|**Secret Key** | 5 |  | 307702010104209f352da16495748e146fcb5370b8e96d292ced5567a8fae55a22bb67d91651b8a00a06082a8648ce3d030107a14403420004a09dcb1bc739e7f19afa9adcb1944968bfba73efcec29b50486eb44d1b29c193449970a3736830cb2bd5d7ec05d2bd1fc07b6df5e48b54ce77a6a7229c3a91c2 | The private key of the client in PKCS#8 format. The textual representation of the key can be found below labelled as \*** . |
 |**Short Server ID** | 10 |  | 102  |  |
 
```
Table 32: LwM2M Security Object [2]
```

```
*: The client public key in text representation:

   0  89: SEQUENCE {
  2  19:   SEQUENCE {
  4   7:     OBJECT IDENTIFIER ecPublicKey (1 2 840 10045 2 1)
 13   8:     OBJECT IDENTIFIER prime256v1 (1 2 840 10045 3 1 7)
       :     }
 23  66:   BIT STRING
       :     04 A0 9D CB 1B C7 39 E7 F1 9A FA 9A DC B1 94 49
       :     68 BF BA 73 EF CE C2 9B 50 48 6E B4 4D 1B 29 C1
       :     93 44 99 70 A3 73 68 30 CB 2B D5 D7 EC 05 D2 BD
       :     1F C0 7B 6D F5 E4 8B 54 CE 77 A6 A7 22 9C 3A 91
       :     C2
       :   }
```

```
**: The server public key in text representation:

 0  89: SEQUENCE {
  2  19:   SEQUENCE {
  4   7:     OBJECT IDENTIFIER ecPublicKey (1 2 840 10045 2 1)
 13   8:     OBJECT IDENTIFIER prime256v1 (1 2 840 10045 3 1 7)
       :     }

 23  66:   BIT STRING
       :     04 82 C7 73 F3 78 D3 0C 27 83 A4 8E B8 11 B9 6C
       :     F6 A9 06 94 A8 56 4F 1E 7F 6D 36 61 52 F1 16 98
       :     95 0F 6F 7C 40 CD A5 85 33 4F 83 77 50 A1 02 F5
       :     BF 25 50 8C EB 9E 55 DF C0 F1 2A 45 51 99 A4 C9
       :     60
       :   }
```

```
***: The client private key in text representation:

 0 119: SEQUENCE {
  2   1:   INTEGER 1
  5  32:   OCTET STRING
       :     9F 35 2D A1 64 95 74 8E 14 6F CB 53 70 B8 E9 6D
       :     29 2C ED 55 67 A8 FA E5 5A 22 BB 67 D9 16 51 B8
 39  10:   [0] {
 41   8:     OBJECT IDENTIFIER prime256v1 (1 2 840 10045 3 1 7)
       :     }
 51  68:   [1] {
 53  66:     BIT STRING
       :       04 A0 9D CB 1B C7 39 E7 F1 9A FA 9A DC B1 94 49
       :       68 BF BA 73 EF CE C2 9B 50 48 6E B4 4D 1B 29 C1
       :       93 44 99 70 A3 73 68 30 CB 2B D5 D7 EC 05 D2 BD
       :       1F C0 7B 6D F5 E4 8B 54 CE 77 A6 A7 22 9C 3A 91
       :       C2
       :     }
       :   }
```

| Resource Name |Resource ID|Resource Instance ID|Value|Notes|
|:--|:-:|:-:|:-:|:--|
| **Short Server ID** | 0  | | 101 | Example LwM2M Server 1 |
| **Lifetime**        | 1  | | 86400 | |
| **Default Minimum Period** | 2 | | 300 | |
| **Default Maximum Period** | 3 | | 6000 | |
| **DisableTimeout**  | 5  | | 86400  | |
| **Notification Storing When Disabled or Offline** | 6 | | True | |
| **Binding Preference**  | 7 | | U | UDP binding preference |

```
Table 33: LwM2M Server Object [0]
```

|                                                   |                 |                          |           |                                     |
|---------------------------------------------------|-----------------|--------------------------|-----------|-------------------------------------|
| **Resource Name**                                 | **Resource ID** | **Resource Instance ID** | **Value** | **Notes**                           |
| **Short Server ID**                               | 0               |                          | 102       | Example LwM2M Server 2              |
| **Lifetime**                                      | 1               |                          | 86400     |                                     |
| **Default Minimum Period**                        | 2               |                          | 60        |                                     |
| **Default Maximum Period**                        | 3               |                          | 6000      |                                     |
| **DisableTimeout**                                | 5               |                          | 86400     |                                     |
| **Notification Storing When Disabled or Offline** | 6               |                          | False     |                                     |
| **Binding Preference**                            | 7               |                          | UQ        | UDP with Queuing binding preference |

```
Table 34: LwM2M Server Object [1]
```

|                          |                 |                          |                    |                                                                                                                                            |
|--------------------------|-----------------|--------------------------|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| **Resource Name**        | **Resource ID** | **Resource Instance ID** | **Value**          | **Notes**                                                                                                                                  |
| **Object ID**            | 0               |                          | 1                  | LwM2M Server Object 0 (Server 1)                                                                                                           |
| **Object Instance ID**   | 1               |                          | 0                  |                                                                                                                                            |
| **ACL**                  | 2               | 101                      | 0b0000000000001111 | For this Object Instance (1:0), Server 1 has access rights (R, W, E, D). Note that the Resource Instance ID indicates the Short Server ID. |
| **Access Control Owner** | 3               |                          | 101                | Server 1 controls this Object Instance’s access rights.                                                                                    |

```
Table 35: Access Control Object [0] (for the LwM2M Server Object Instance 0)
```

|                          |                 |                          |                    |                                                                                                                                            |
|--------------------------|-----------------|--------------------------|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| **Resource Name**        | **Resource ID** | **Resource Instance ID** | **Value**          | **Notes**                                                                                                                                  |
| **Object ID**            | 0               |                          | 1                  | LwM2M Server Object 1 (Server 2)                                                                                                                                  |
| **Object Instance ID**   | 1               |                          | 1                  |                                                                                                                                            |
| **ACL**                  | 2               | 102                      | 0b0000000000001111 | For this Object Instance (1:1), Server 2 has access rights (R, W, E, D). Note that the Resource Instance ID indicates the Short Server ID. |
| **Access Control Owner** | 3               |                          | 102                | Server 2 controls this Object Instance’s access rights.                                                                                    |

```
Table 36: Access Control Object [1] (for the LwM2M Server Object Instance 1)
```

|                          |                 |                          |                    |                                                                                                                                            |
|--------------------------|-----------------|--------------------------|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| **Resource Name**        | **Resource ID** | **Resource Instance ID** | **Value**          | **Notes**                                                                                                                                  |
| **Object ID**            | 0               |                          | 3                  | Device Object                                                                                                                              |
| **Object Instance ID**   | 1               |                          | 0                  |                                                                                                                                            |
| **ACL**                  | 2               | 101                      | 0b0000000000001111 | For this Object Instance (3:0), Server 1 has access rights (R, W, E, D). Note that the Resource Instance ID indicates the Short Server ID. |
| **ACL**                  | 2               | 102                      | 0b0000000000000001 | For this Object Instance (3:0), Server 2 has read-only access rights. Note that the Resource Instance ID indicates the Short Server ID.    |
| **Access Control Owner** | 3               |                          | 101                | Server 1 controls this Object Instance’s access rights.                                                                                    |

```
Table 37: Access Control Object [2] (for the Device Object Instance)
```

|                          |                 |                          |                    |                                                                                                                                                                          |
|--------------------------|-----------------|--------------------------|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Resource Name**        | **Resource ID** | **Resource Instance ID** | **Value**          | **Notes**                                                                                                                                                                |
| **Object ID**            | 0               |                          | 4                  | Connectivity Monitoring Object                                                                                                                                           |
| **Object Instance ID**   | 1               |                          | 0                  |                                                                                                                                                                          |
| **ACL**                  | 2               | 101                      | 0b0000000000000001 | For this Object Instance (4:0), Server 1 has read-only access rights. Note that the Resource Instance ID indicates the Short Server ID.                                  |
| **ACL**                  | 2               | 0                        | 0b0000000000000001 | For this Object Instance (4:0), The other Servers except Server 1 have read-only access rights. Note that this Resource Instance ID indicates the default access rights. |
| **Access Control Owner** | 3               |                          | 101                | Server 1 controls this Object Instance’s access rights.                                                                                                                  |

```
Table 38: Access Control Object [3] (for the Connectivity Monitoring Object Instance)
```

|                          |                 |                          |                    |                                                             |
|--------------------------|-----------------|--------------------------|--------------------|-------------------------------------------------------------|
| **Resource Name**        | **Resource ID** | **Resource Instance ID** | **Value**          | **Notes**                                                   |
| **Object ID**            | 0               |                          | 5                  | Firmware Update Object                                      |
| **Object Instance ID**   | 1               |                          | 65535              | Irrelevant                                                  |
| **ACL**                  | 2               | 101                      | 0b0000000000010000 | Server 1 can create Firmware Update Object Instance         |
| **Access Control Owner** | 3               |                          | 65535              | This Object Instance must be managed by Bootstrap Interface |

```
Table 39: Access Control Object [4] (for the Firmware Update Object)
```

|                             |                 |                          |                        |                                          |
|-----------------------------|-----------------|--------------------------|------------------------|------------------------------------------|
| **Resource Name**           | **Resource ID** | **Resource Instance ID** | **Value**              | **Notes**                                |
| Manufacturer                | 0               |                          | Open Mobile Alliance   |                                          |
| Model Number                | 1               |                          | Lightweight M2M Client |                                          |
| Serial Number               | 2               |                          | 345000123              |                                          |
| Firmware version            | 3               |                          | 1.0                    |                                          |
| Available Power Sources     | 6               | 0                        | 1                      | Internal Battery                         |
| Available Power Sources     | 6               | 1                        | 5                      | USB                                      |
| Power Source Voltage        | 7               | 0                        | 3800                   | 3.8V battery                             |
| Power Source Voltage        | 7               | 1                        | 5000                   | USB VBUS                                 |
| Power Source Current        | 8               | 0                        | 125                    | 125mA                                    |
| Power Source Current        | 8               | 1                        | 900                    | USB 900mA                                |
| Battery level               | 9               |                          | 100                    |                                          |
| Memory free                 | 10              |                          | 15                     | 15 kB of free memory                     |
| Error code                  | 11              | 0                        | 0                      | No errors                                |
| Current Time                | 13              |                          | 1367491215             | May 2<sup>nd</sup>, 2013 at 11:42 AM GMT |
| UTC Offset                  | 14              |                          | +02:00                 | UTC+2 (CET)                              |
| Supported Binding and Modes | 16              |                          | U                      | UDP binding                              |

```
Table 40: Device Object Instance
```

|                          |                 |                          |               |                 |
|--------------------------|-----------------|--------------------------|---------------|-----------------|
| **Resource Name**        | **Resource ID** | **Resource Instance ID** | **Value**     | **Notes**       |
| Network Bearer           | 0               |                          | 0             | GSM Bearer      |
| Available Network Bearer | 1               |                          | 0             | GSM Bearer      |
| Radio signal strength    | 2               |                          | 92            | RSSI in dBm     |
| Link Quality             | 3               |                          | 2             | RxQual Downlink |
| IP Addresses             | 4               | 0                        | 192.168.0.100 |                 |
| Router IP Addresses      | 5               | 0                        | 192.168.1.1   |                 |
| Link Utilization         | 6               |                          | 5             | %               |
| APN                      | 7               | 0                        | internet      |                 |

```
Table 41: Connectivity Monitoring Object Instance
```
