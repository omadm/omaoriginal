
<strong> Appendix B. Static Conformance Requirements (Normative) </strong>

The notation used in this appendix is specified in \[SCRRULES\].

### B.1 SCR for LWM2M Client

#### B.1.1 Bootstrap Interface

|                    |                                                                                                   |                             |                       |
|--------------------|---------------------------------------------------------------------------------------------------|-----------------------------|-----------------------|
| **Item**           | **Function**                                                                                      | **Reference**               | **Requirement**       |
| LwM2M-BOOT-001-C-M | Support of at least one Bootstrap Mode                                                            | Section 5.1                 |                       |
| LwM2M-BOOT-002-C-O | Support of Factory Bootstrap Mode                                                                 | Section 5.2.3.1             |                       |
| LwM2M-BOOT-003-C-O | Support of Bootstrap from Smartcard                                                               | Section 5.2.3.2, Appendix F | LwM2M-BOOT-012C-O     |
| LwM2M-BOOT-004-C-O | Support of Client Initiated Bootstrap                                                             | Section 5.2.3.3             |                       |
| LwM2M-BOOT-005-C-O | Support of Server Initiated Bootstrap                                                             | Section 5.2.3.4             |                       |
| LwM2M-BOOT-006-C-M | Support of LwM2M Server Bootstrap Information                                                     | Section 5.2.2               |                       |
| LwM2M-BOOT-007-C-O | Support of LwM2M Bootstrap-Server Bootstrap Information                                           | Section 5.2.2               |                       |
| LwM2M-BOOT-008-C-M | Support of accepting Bootstrap Information transferred                                            | Section 5.2.2               |                       |
| LwM2M-BOOT-009-C-M | Support of Bootstrap Sequence                                                                     | Section 5.2.4               |                       |
| LwM2M-BOOT-010-C-M | Support of Bootstrap Security                                                                     | Section 5.2.5               |                       |
| LwM2M-BOOT-011-C-O | Support of Bootstrap from Smartcard with Secure Channel                                           | Section 5.2.3.2, Appendix F | LwM2M-BOOT-012C-O AND LwM2M-SEC-007-C-O      |
| LwM2M-BOOT-012-C-O | Retrieve & Process bootstrap data from Smartcard                                                  | Section 5.2.3.2             |                       |
| LwM2M-BOOT-013-C-O | Check for Bootstrap Data change in Smartcard                                                      | Section 5.2.3.2             |                       |
| LwM2M-BOOT-014-C-O | Support of the BOOSTRAP-REQUEST operation                                                         | Section 5.2.7.1             | LwM2M-BOOT-004-C-O    |
| LwM2M-BOOT-015-C-O | Support of the BOOTSTRAP-FINISH, BOOTSTRAP DISCOVER, BOOTSTRAP WRITE, BOOTSTRAP DELETE operations | Section 5.2.7.2 Section 5.2.7.3 Section 5.2.7.4 Section 5.2.7.5              | LwM2M-BOOT-004-C-O OR LwM2M-BOOT-005-C-O     |
| LwM2M-BOOT-016-C-O | Check and report Bootstrap Configuration Inconsistency                                            | Section 5.2.6               | LwM2M-BOOT-004-C-O OR LwM2M-BOOT-005-C-O     |

#### B.1.2 Client Registration

|                   |                                                                                |                        |                        |
|-------------------|--------------------------------------------------------------------------------|------------------------|------------------------|
| **Item**          | **Function**                                                                   | **Reference**          | **Requirement**        |
| LwM2M-CR-001-C-M  | Support of “Register” operation                                                | Section 5.3.1          |                        |
| LwM2M-CR-002-C-M  | Support of Endpoint Client Name parameter                                      | Section 5.3.1          |                        |
| LwM2M-CR-003-C-M  | Support of Lifetime parameter                                                  | Section 5.3.1          |                        |
| LwM2M-CR-004-C-M  | Support of LwM2M Version parameter                                             | Section 5.3.1          |                        |
| LwM2M-CR-005-C-M  | Support of Binding Mode parameter                                              | Section 5.3.1, 5.3.1.1 |                        |
| LwM2M-CR-006-C-O  | Support of SMS Number parameter                                                | Section 5.3.1          |                        |
| LwM2M-CR-007-C-M  | Support of Object and Object Instances parameter                               | Section 5.3.1          |                        |
| LwM2M-CR-008-C-M  | Support of “Update” operation                                                  | Section 5.3.2          |                        |
| LwM2M-CR-009-C-O  | Support of “De-register” operation                                             | Section 5.3.3          |                        |
| LwM2M-CR-010-C-O  | Support of Updating Bootstrap Information from Smartcard at Register/Update    | Section 5.3.2          | (LwM2M-CR-001-C-M OR LwM2M-CR-008-C-M ) AND LwM2M-BOOT-013-C-O AND (LwM2M-BOOT-003-C-O OR LwM2M-BOOT-011-C-O)     |
| LwM2M-CR-0011-C-M | No Security Object (ID:0) and Security Object Instances in the parameters list | Section 5.3.1          |                        |
| LwM2M-CR-0012-C-M | Support of Object Versioning in the Object and Object Instances parameter list | Section 5.3.1          |                        |

#### B.1.3 Device Management and Service Enablement Interface

|                    |                                         |               |                 |
|--------------------|-----------------------------------------|---------------|-----------------|
| **Item**           | **Function**                            | **Reference** | **Requirement** |
| LwM2M-DMSE-001-C-M | Support of “Read” operation             | Section 5.4.1 |                 |
| LwM2M-DMSE-002-C-M | Support of “Discover” operation         | Section 5.4.2 |                 |
| LwM2M-DMSE-003-C-M | Support of “Write” operation            | Section 5.4.3 |                 |
| LwM2M-DMSE-004-C-M | Support of “Write-Attributes” operation | Section 5.4.4 |                 |
| LwM2M-DMSE-005-C-O | Support of Minimum Period parameter     | Section 5.4.4 |                 |
| LwM2M-DMSE-006-C-O | Support of Maximum Period parameter     | Section 5.4.4 |                 |
| LwM2M-DMSE-007-C-O | Support of Greater Than parameter       | Section 5.4.4 |                 |
| LwM2M-DMSE-008-C-O | Support of Less Than parameter          | Section 5.4.4 |                 |
| LwM2M-DMSE-009-C-O | Support of Step parameter               | Section 5.4.4 |                 |
| LwM2M-DMSE-010-C-O | Support of Cancel parameter             | Section 5.4.4 |                 |
| LwM2M-DMSE-011-C-M | Support of “Execute” operation          | Section 5.4.5 |                 |
| LwM2M-DMSE-012-C-M | Support of “Create” operation           | Section 5.4.6 |                 |
| LwM2M-DMSE-013-C-M | Support of “Delete” operation           | Section 5.4.7 |                 |

#### B.1.4 Information Reporting

|                  |                                           |               |                 |
|------------------|-------------------------------------------|---------------|-----------------|
| **Item**         | **Function**                              | **Reference** | **Requirement** |
| LwM2M-IR-001-C-M | Support of “Observe” operation            | Section 5.5.1 |                 |
| LwM2M-IR-002-C-M | Support of “Notify” operation             | Section 5.5.2 |                 |
| LwM2M-IR-003-C-M | Support of “Cancel Observation” operation | Section 5.5.3 |                 |

#### B.1.5 Data Format

|                  |                              |                              |                 |
|------------------|------------------------------|------------------------------|-----------------|
| **Item**         | **Function**                 | **Reference**                | **Requirement** |
| LwM2M-DF-001-C-O | Support of Plain Text format | Section 6.4, 6.4.1           |                 |
| LwM2M-DF-002-C-O | Support of Opaque format     | Section 6.4, 6.4.2           |                 |
| LwM2M-DF-003-C-M | Support of TLV format        | Section 6.4, 6.4.3           |                 |
| LwM2M-DF-004-C-O | Support of JSON format       | Section 6.4, 6.4.4           |                 |

#### B.1.6 Security
<table>
  <tr>
    <td><strong> Item </strong></td><td><strong> Function </strong></td><td><strong> Reference </strong></td><td><strong> Requirement </strong></td>
  </tr>   
 <tr>
    <td> LwM2M-SEC-001-C-M </td><td> Support of at least one key mode </td><td> Section 7.1 </td><td> LwM2M-SEC-002-C-O<br> OR <br> LwM2M-SEC-003-C-O <br> OR <br> LwM2M-SEC-004-C-O <br> OR <br> LwM2M-SEC-004-C-O </td>
 </tr> 
 <tr>
  <td> LwM2M-SEC-002-C-O</td><td> Support of Pre-Shared Keys mode </td><td> Section 7.1.7 </td><td> </td> 
 </tr>
 <tr>
  <td> LwM2M-SEC-003-C-O </td><td> Support of Raw Public Key Certificates mode </td><td> Section 7.1.8 </td><td> </td>
 </tr>
 <tr>
  <td> LwM2M-SEC-004-C-O </td><td> Support of X.509 Certificates mode </td><td> Section 7.1.9 </td><td> </td>
 </tr>
 <tr>
  <td> LwM2M-SEC-005-C-O </td><td> Support of No Sec mode  </td><td> Section 7.1.10 </td><td> </td>
 </tr>
 <tr>
  <td> LwM2M-SEC-006-C-O </td><td> Support of UDP Channel Security </td><td> Section 7.1 </td><td> </td>
 </tr> 
  <td> LwM2M-SEC-007-C-O </td><td> Support of Smartcard Secure Channel </td><td> Section 7.1, Appendix G </td><td> LwM2M-SEC-009-C-O </td>
  </tr>
  <tr>
   <td> LwM2M-SEC-008-C-O </td><td> Support of Access Control Mechanism </td><td> Section 7.3 </td><td> </td>
  </tr>
  <tr> 
   <td> LwM2M-SEC-009-C-O </td><td> Smartcard Secure Channel using <br> [GLOBALPLATFORM] <br> [GP SCP03] </td><td>  </td>
  </tr>
 </table> 

#### B.1.7 Mechanism

|                                                                  |                        |               |                 |
|------------------------------------------------------------------|------------------------|---------------|-----------------|
| **Item**                                                         | **Function**           | **Reference** | **Requirement** |
| LwM2M-MEC-001-C-O                                                | Support of Queue Mode  | Section 8.3   |                 |
| <span id="_Toc365994807" class="anchor"></span>LwM2M-MEC-002-C-M | Support of UDP Binding | Section 8.6.1 |                 |
| LwM2M-MEC-003-C-O                                                | Support of SMS Binding | Section 8.6.2 |                 |

#### B.1.8 Objects

|                   |                                           |               |                 |
|-------------------|-------------------------------------------|---------------|-----------------|
| **Item**          | **Function**                              | **Reference** | **Requirement** |
| LwM2M-OBJ-001-C-M | Support of LwM2M Security Object          | Appendix E.1  |                 |
| LwM2M-OBJ-002-C-M | Support of LwM2M Server Object            | Appendix E.2  |                 |
| LwM2M-OBJ-003-C-O | Support of Access Control Object          | Appendix E.3  |                 |
| LwM2M-OBJ-004-C-M | Support of Device Object                  | Appendix E.4  |                 |
| LwM2M-OBJ-005-C-O | Support of Connectivity Monitoring Object | Appendix E.5  |                 |
| LwM2M-OBJ-006-C-O | Support of Firmware Update Object         | Appendix E.6  |                 |
| LwM2M-OBJ-007-C-O | Support of Location Object                | Appendix E.7  |                 |
| LwM2M-OBJ-008-C-O | Support of Connectivity Statistics Object | Appendix E.8  |                 |

### B.2	SCR for LwM2M Server

#### B.2.1 Bootstrap Interface

|                    |                                       |                 |                 |
|--------------------|---------------------------------------|-----------------|-----------------|
| **Item**           | **Function**                          | **Reference**   | **Requirement** |
| LwM2M-BOOT-005-S-M | Support of Server Initiated Bootstrap | Section 5.2.3.4 |                 |
| LwM2M-BOOT-010-S-M | Support of Bootstrap Security         | Section 5.2.5   |                 |

#### B.2.2 Client Registration

|                  |                                                  |                        |                 |
|------------------|--------------------------------------------------|------------------------|-----------------|
| **Item**         | **Function**                                     | **Reference**          | **Requirement** |
| LwM2M-CR-001-S-M | Support of “Register” operation                  | Section 5.3.1          |                 |
| LwM2M-CR-002-S-M | Support of Endpoint Client Name parameter        | Section 5.3.1          |                 |
| LwM2M-CR-003-S-M | Support of Lifetime parameter                    | Section 5.3.1          |                 |
| LwM2M-CR-004-S-M | Support of LwM2M Version parameter               | Section 5.3.1          |                 |
| LwM2M-CR-005-S-M | Support of Binding Mode parameter                | Section 5.3.1, 5.3.1.1 |                 |
| LwM2M-CR-006-S-M | Support of SMS Number parameter                  | Section 5.3.1          |                 |
| LwM2M-CR-007-S-M | Support of Object and Object Instances parameter | Section 5.3.1          |                 |
| LwM2M-CR-008-S-M | Support of “Update” operation                    | Section 5.3.2          |                 |
| LwM2M-CR-009-S-M | Support of “De-register” operation               | Section 5.3.3          |                 |

#### B.2.3	Device Management and Service Enablement Interface

|                    |                                         |               |                 |
|--------------------|-----------------------------------------|---------------|-----------------|
| **Item**           | **Function**                            | **Reference** | **Requirement** |
| LwM2M-DMSE-001-S-M | Support of “Read” operation             | Section 5.4.1 |                 |
| LwM2M-DMSE-002-S-M | Support of “Discover” operation         | Section 5.4.2 |                 |
| LwM2M-DMSE-003-S-M | Support of “Write” operation            | Section 5.4.3 |                 |
| LwM2M-DMSE-004-S-M | Support of “Write-Attributes” operation | Section 5.4.4 |                 |
| LwM2M-DMSE-005-S-M | Support of Minimum Period parameter     | Section 5.4.4 |                 |
| LwM2M-DMSE-006-S-M | Support of Maximum Period parameter     | Section 5.4.4 |                 |
| LwM2M-DMSE-007-S-M | Support of Greater Than parameter       | Section 5.4.4 |                 |
| LwM2M-DMSE-008-S-M | Support of Less Than parameter          | Section 5.4.4 |                 |
| LwM2M-DMSE-009-S-M | Support of Step parameter               | Section 5.4.4 |                 |
| LwM2M-DMSE-010-S-M | Support of “Execute” operation          | Section 5.4.5 |                 |
| LwM2M-DMSE-011-S-M | Support of “Create” operation           | Section 5.4.6 |                 |
| LwM2M-DMSE-012-S-M | Support of “Delete” operation           | Section 5.4.7 |                 |

#### B.2.4	Information Reporting

|                  |                                           |               |                 |
|------------------|-------------------------------------------|---------------|-----------------|
| **Item**         | **Function**                              | **Reference** | **Requirement** |
| LwM2M-IR-001-S-M | Support of “Observe” operation            | Section 5.5.1 |                 |
| LwM2M-IR-002-S-M | Support of “Notify” operation             | Section 5.5.2 |                 |
| LwM2M-IR-003-S-M | Support of “Cancel Observation” operation | Section 5.5.3 |                 |

#### B.2.5	Data Format

|                  |                              |                    |                 |
|------------------|------------------------------|--------------------|-----------------|
| **Item**         | **Function**                 | **Reference**      | **Requirement** |
| LwM2M-DF-001-S-M | Support of Plain Text format | Section 6.4, 6.4.1 |                 |
| LwM2M-DF-002-S-M | Support of Opaque format     | Section 6.4, 6.4.2 |                 |
| LwM2M-DF-003-S-M | Support of TLV format        | Section 6.4, 6.4.3 |                 |
| LwM2M-DF-004-S-M | Support of JSON format       | Section 6.4, 6.4.4 |                 |

#### B.2.6	Security

|                   |                                             |                |                 |
|-------------------|---------------------------------------------|----------------|-----------------|
| **Item**          | **Function**                                | **Reference**  | **Requirement** |
| LwM2M-SEC-002-S-M | Support of Pre-Shared Keys mode             | Section 7.1.7  |                 |
| LwM2M-SEC-003-S-M | Support of Raw Public Key Certificates mode | Section 7.1.8  |                 |
| LwM2M-SEC-004-S-M | Support of X.509 Certificates mode          | Section 7.1.9  |                 |
| LwM2M-SEC-005-S-M | Support of No Sec mode                      | Section 7.1.10 |                 |
| LwM2M-SEC-006-S-M | Support of UDP Channel Security             | Section 7.1    |                 |

#### B.2.7 Mechanism

|                   |                        |               |                 |
|-------------------|------------------------|---------------|-----------------|
| **Item**          | **Function**           | **Reference** | **Requirement** |
| LwM2M-MEC-001-S-M | Support of Queue Mode  | Section 8.3   |                 |
| LwM2M-MEC-002-S-M | Support of UDP Binding | Section 8.6.1 |                 |
| LwM2M-MEC-003-S-O | Support of SMS Binding | Section 8.6.2 |                 |

#### B.2.8	Objects

|                   |                                           |               |                 |
|-------------------|-------------------------------------------|---------------|-----------------|
| **Item**          | **Function**                              | **Reference** | **Requirement** |
| LwM2M-OBJ-001-S-M | Support of LwM2M Security Object          | Appendix E.1  |                 |
| LwM2M-OBJ-002-S-M | Support of LwM2M Server Object            | Appendix E.2  |                 |
| LwM2M-OBJ-003-S-O | Support of Access Control Object          | Appendix E.3  |                 |
| LwM2M-OBJ-004-S-M | Support of Device Object                  | Appendix E.4  |                 |
| LwM2M-OBJ-005-S-O | Support of Connectivity Monitoring Object | Appendix E.5  |                 |
| LwM2M-OBJ-006-S-O | Support of Firmware Update Object         | Appendix E.6  |                 |
| LwM2M-OBJ-007-S-O | Support of Location Object                | Appendix E.7  |                 |
| LwM2M-OBJ-008-S-O | Support of Connectivity Statistics Object | Appendix E.8  |                 |
