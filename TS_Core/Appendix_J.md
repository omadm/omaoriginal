
<strong> Appendix J. LwM2M Schema and Object Definition File (Informative) </strong>

For supporting the LwM2M Enabler version and the Object Version in the Definition file (.xml) of a LwM2M Object, the LwM2M schema (URL: ="<http://openmobilealliance.org/tech/profiles/LWM2M.xsd>") contains 2 optional elements: LwM2MVersion and ObjectVersion (see Appendix K).

The Object definition file (.xml), which describes the resources of a particular Object may contain these two elements:

1.  the “LwM2MVersion” element indicates the minimum version of the LwM2M Enabler supporting that Object,

2.  the “ObjectVersion” element indicates the version of the Object as defined in Section 6.2 “Object Versioning” in this document.

In addition:

-   when the minimum LwM2M version supporting the Object is the Initial Version of the LwM2M Enabler (1.0), this information may be omitted.

-   when the Object version is the Initial Version of that Object (1.0), the Object Version information may be omitted.

-   when the Object definition is part of any LwM2M Enabler, the Object Version information may be omitted.

For example: an Object ID:44 in Version 2.4 for which the minimum LwM2M version supporting this Object Version is 1.1, will have an URN defined as “*urn:oma:lwm2m:oma:44:2.4”* used to name the associate Object definition (.xml) file on the OMNA portal:

```
<?xml version="1.0" encoding="UTF-8"?> 
<LWM2M xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="http://openmobilealliance.org/tech/profiles/LWM2M.xsd" > 
                <Object ObjectType="MODefinition"> 
                                <Name>MyDevice</Name> 
                                <Description1>< ![CDATA[This LWM2M Object is my device]]></Description1> 
                                <ObjectID>44</ObjectID> 
                                <LWM2MVersion>1.1</LWM2MVersion> 
                                <ObjectVersion>2.4</ObjectVersion> 
                                <ObjectURN>urn:oma:lwm2m:oma:44:2.4</ObjectURN> 
                                <MultipleInstances>Single</MultipleInstances> 
                                <Mandatory>Mandatory</Mandatory> 
                                <Resources>   
                                        . 
                                       . 
                               </Resources> 
                               </Description2> 
                               </Resources> 
               </Object> 
</LWM2M> 
```
  

