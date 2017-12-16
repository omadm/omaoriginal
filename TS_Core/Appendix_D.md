<strong> Appendix D. LwM2M Object Template and Guidelines (Normative) </strong>

This Appendix provides the template to be used for the specification of LwM2M Objects. Furthermore, guidelines for the creation of LwM2M Objects are provided.

The XML versions of LwM2M Objects MUST comply with the XML schema which can be found here: <http://openmobilealliance.org/tech/profiles/LWM2M.xsd>

### D.1	Object Template

**Appendix D.x LwM2M Object: *&lt;LwM2M object name&gt;***

**Description**

**Object definition:**

|             |                         |                 |                    |                                                     |
|-------------|-------------------------|-----------------|--------------------|-----------------------------------------------------|
| **Name**    | **Object ID **          | **Instances**   | **Mandatory**      | **Object URN**                                      |
| Object Name | 16-bit Unsigned Integer | Multiple/Single | Mandatory/Optional | urn:oma:lwm2m:{oma,ext,x}:{Object ID}\[:{version}\] |

-   **Name:** specifies the Object name.

-   **Object ID:** specifies the Object ID.

-   **Instances:** indicates whether this Object supports multiple Object Instances or not. If this field is “Multiple” then the number of Object Instance can be from 0 to many. If this field is “Single” then the number of Object Instance can be from 0 to 1. If the Object field “Mandatory” is “Mandatory” and the Object field “Instances” is “Single” then, the number of Object Instance MUST be 1.

-   **Mandatory:** if this field is “Mandatory”, then the LwM2M Client MUST support this Object. If this field is “Optional”, then the LwM2M Client SHOULD support this Object.

-   **Object URN:** specifies the Object URN. The format of the Object URN is “urn:oma:lwm2m:{oma,ext,x}:{Object ID}\[:{version}\]” and {} part means that those values are variable and filled with real value. For example, Object URN of LwM2M Server Object is “urn:oma:lwm2m:oma:1”. The “version” field, follows the rules specified in Section 6.2 related to Object Versioning Policy.

**Resource definition:**

<table>
<tbody>
<tr class="odd">
<td><strong>ID</strong></td>
<td><strong>Name</strong></td>
<td><strong>Operations</strong></td>
<td><strong>Instances</strong></td>
<td><strong>Mandatory</strong></td>
<td><strong>Type</strong></td>
<td><strong>Range or Enumeration</strong></td>
<td><strong>Units</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr class="even">
<td>0</td>
<td>Resource Name</td>
<td>R (Read),<br />
W (Write),<br />
E (Execute)</td>
<td>Multiple/Single</td>
<td>Mandatory/Optional</td>
<td><p>String,</p>
<p>Integer,</p>
<p>Float,</p>
<p>Boolean,</p>
<p>Opaque,</p>
<p>Time,</p>
<p>Objlnk none</p></td>
<td>If any</td>
<td>If any</td>
<td>Description</td>
</tr>
</tbody>
</table>

-   **ID:** specifies the Resource ID which is unique within Object.

-   **Name:** specifies the Resource name.

-   **Operations:** indicates which operations the Resource supports in the “Device Management & Service Enablement” Interface. This field can be set to a combination of R (Read, Observe, Discover, Write-Attributes), and W (Write), or can be set to E (Execute); Executable Operation is exclusive regarding the two others (R, W). This field may also have an empty value, which means that this field is not allowed to be accessed via “Device Management & Service Enablement” Interface but allowed to be accessed via “Bootstrap” Interface.

-   **Instances:** indicates whether this Resource supports multiple Resource Instances or not. If this field is “Multiple” then the number of Resource Instance can be from 0 to many. If this field is “Single” then the number of Resource Instance can be from 0 to 1. If the Resource field “Mandatory” is “Mandatory” and the field “Instances” of the Resource is “Single” then, the number of Resource Instance MUST be 1. Resource which supports “Execute” operation MUST have “Single” as value of the “Instances” field.

-   **Mandatory:** if this field is “Mandatory”, then any Instance of the Object that Resource belongs to, MUST instantiate such a Resource (refer Section 6.1, Resource Model). If this field is “Optional”, then this Resource MAY be omitted from some - or even all - Instances of the Object that Resource belongs to.

-   **Type:** Data Type indicates the type of Resource value. Data Types used in this enabler are described in Appendix C Data Types. Resource which supports “Execute” operation MUST have no associated Data Type (none) encoded as an empty value in Object DDF file.

-   **Range or Enumeration:** this field limits the value of Resource.

-   **Units:** specifies the unit of the Resource value.

-   **Description:** specifies the Resource description.

<span id="_Ref368310666" class="anchor"><span id="_Ref368312910" class="anchor"><span id="_Ref368314129" class="anchor"><span id="_Ref368314148" class="anchor"><span id="_Toc370916126" class="anchor"><span id="_Toc370922948" class="anchor"></span></span></span></span></span></span>In addition to the object and resource definition tables, an object containing Executable Resource(s) is specified in third Table, gathering the definition of the arguments of all the Executable Resources of that Object.

This table provides the properties of arguments

<strong> Executable Resource Arguments Definition </strong>

<table>
  <tr>
    <td><strong> ID </strong></td> <td><strong> Resource Name </strong></td> <td><strong> Order </strong></td> <td><strong> Name</strong></td> <td><strong> Typ</strong></td> <td><strong> Range or Enum </strong></td> <td><strong> Unit </strong></td> <td><strong> Description</strong></td>
  </tr>
  <tr>
    <td> </td><td> </td> <td>  [0:9] </td> <td> String </td> <td> Data Types </td> <td> If any </td> <td> If any </td> <td>  </td>
  </tr>  
</table>

Example of an Executable Resource Arguments Definition Table for an Object having 3 Executable Resource

<strong> Executable Resource Arguments Definition </strong>

<table>
  <tr>
    <td><strong> ID </strong></td> <td><strong> Resource Name </strong></td> <td><strong> Order </strong></td> <td><strong> Name</strong></td> <td><strong> Typ</strong></td> <td><strong> Range or Enum </strong></td> <td><strong> Unit </strong></td> <td><strong> Description</strong></td>
  </tr>
  <tr>
    <td> 5 </td><td> Delete </td> <td>  0 </td> <td> - </td> <td> none </td> <td> - </td> <td> - </td> <td> 1 argument <br> EXECUTE /X/0/5 0 </td>
  </tr>  
  <tr>
    <td> 7 </td><td rowspan="2"> Update </td> 
    <td>  0 </td> <td> Remove </td> <td> none </td> <td> - </td> <td>  </td> <td rowspan="2"> 2 arguments <br> ex EXECUTE /X/0/7 0,1='2' </td> <tr> <td>  1 </td> <td> Keep </td> <td> Integer </td> <td> [0-2] </td> <td>  </td> </tr>
  
  </tr>  
  
  <tr>
    <td> 10 </td><td> Create </td> <td colspan="5">   </td> <td>  </td>
  </tr>  
  
</table>



### D.2	Open Mobile Naming Authority (OMNA) Guidelines

This appendix defines guidelines for OMNA regarding registries and protocol ID ranges to be maintained.


#### D.2.1 Object Registry

LwM2M Objects must be registered with the OMNA Lightweight Object registry. The rules for Object registry are documented at: <http://www.openmobilealliance.org/wp/OMNA/LwM2M/LwM2MRegistry.html>

The URN format for an Object is automatically built from the class of Object, the Object ID and potentially the Object Version (see Section 6.2 Object Versioning) as follows:

urn:oma:lwm2m:{oma,ext,x}:{Object ID}\[:{version}\].

#### D.2.2 Resource Registry

LwM2M Objects are specified as being composed of Resources, each identified by a Resource ID. Resources can either be specific to each Object with meaning only when used in that Object, or Reusable Resources can be registered, assigned an ID from the OMNA range and re-used in any Object.

The rules for registering Resource are documented at: <http://www.openmobilealliance.org/wp/OMNA/LwM2M/LwM2MRegistry.html>
