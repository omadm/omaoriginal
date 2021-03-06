<strong> Appendix K. LwM2M Schema </strong>

This appendix provides the content of the LightweightM2M schema.

The schema was created to support the LwM2M Editor Tool.
The following elements and attributes are used by the LwM2M Editor Tool but are not part of the LwM2M protocol:

-   Description1, it is used to insert the definition of the Object

-   Description2, it is used to insert any extra information at the end of the table that contains the Resources

-   ObjectType, used to identify if the file contains an Object and Resources or only Resources

```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
     
   <xs:element name="LWM2M">
          
      <xs:complexType>
               
         <xs:sequence>
                    
            <xs:element minOccurs="1" maxOccurs="unbounded" name="Object">
                         
               <xs:complexType>
                              
                  <xs:sequence>
                                   
                     <xs:element name="Name" type="xs:string" />
                                   
                     <xs:element name="Description1" type="xs:string" />
                                   
                     <xs:element name="ObjectID" type="xs:unsignedShort" />
                                   
                     <xs:element name="ObjectURN" type="xs:string" />
                                   
                     <xs:element name="LWM2MVersion" type="xs:string" minOccurs="0" />
                                   
                     <xs:element name="ObjectVersion" type="xs:string" minOccurs="0" />
                                   
                     <xs:element name="MultipleInstances">
                                        
                        <xs:simpleType>
                                             
                           <xs:restriction base="xs:string">
                                                  
                              <xs:enumeration value="Multiple" />
                                                  
                              <xs:enumeration value="Single" />
                                                
                           </xs:restriction>
                                           
                        </xs:simpleType>
                                      
                     </xs:element>
                                   
                     <xs:element name="Mandatory">
                                        
                        <xs:simpleType>
                                             
                           <xs:restriction base="xs:string">
                                                  
                              <xs:enumeration value="Mandatory" />
                                                  
                              <xs:enumeration value="Optional" />
                                                
                           </xs:restriction>
                                           
                        </xs:simpleType>
                                      
                     </xs:element>
                                   
                     <xs:element name="Resources">
                                        
                        <xs:complexType>
                                             
                           <xs:sequence>
                                                  
                              <xs:element maxOccurs="unbounded" name="Item">
                                                       
                                 <xs:complexType>
                                                            
                                    <xs:sequence>
                                                                 
                                       <xs:element name="Name" type="xs:string" />
                                                                 
                                       <xs:element name="Operations">
                                                                      
                                          <xs:simpleType>
                                                                           
                                             <xs:restriction base="xs:string">
                                                                                
                                                <xs:enumeration value="R" />
                                                                                
                                                <xs:enumeration value="W" />
                                                                                
                                                <xs:enumeration value="RW" />
                                                                                
                                                <xs:enumeration value="E" />
                                                                                
                                                <xs:enumeration value="" />
                                                                              
                                             </xs:restriction>
                                                                        
                                          </xs:simpleType>
                                                                    
                                       </xs:element>
                                                                 
                                       <xs:element name="MultipleInstances">
                                                                      
                                          <xs:simpleType>
                                                                           
                                             <xs:restriction base="xs:string">
                                                                                
                                                <xs:enumeration value="Multiple" />
                                                                                
                                                <xs:enumeration value="Single" />
                                                                              
                                             </xs:restriction>
                                                                         
                                          </xs:simpleType>
                                                                    
                                       </xs:element>
                                                                 
                                       <xs:element name="Mandatory">
                                                                      
                                          <xs:simpleType>
                                                                           
                                             <xs:restriction base="xs:string">
                                                                                
                                                <xs:enumeration value="Mandatory" />
                                                                                
                                                <xs:enumeration value="Optional" />
                                                                              
                                             </xs:restriction>
                                                                         
                                          </xs:simpleType>
                                                                    
                                       </xs:element>
                                                                 
                                       <xs:element name="Type">
                                                                      
                                          <xs:simpleType>
                                                                           
                                             <xs:restriction base="xs:string">
                                                                                
                                                <xs:enumeration value="String" />
                                                                                
                                                <xs:enumeration value="Integer" />
                                                                                
                                                <xs:enumeration value="Float" />
                                                                                
                                                <xs:enumeration value="Boolean" />
                                                                                
                                                <xs:enumeration value="Opaque" />
                                                                                
                                                <xs:enumeration value="Time" />
                                                                                
                                                <xs:enumeration value="Objlnk" />
                                                                                
                                                <xs:enumeration value="" />
                                                                              
                                             </xs:restriction>
                                                                         
                                          </xs:simpleType>
                                                                    
                                       </xs:element>
                                                                 
                                       <xs:element name="RangeEnumeration" type="xs:string" />
                                                                 
                                       <xs:element name="Units" type="xs:string" />
                                                                 
                                       <xs:element name="Description" type="xs:string" />
                                                               
                                    </xs:sequence>
                                                            
                                    <xs:attribute name="ID" type="xs:unsignedShort" use="required" />
                                                          
                                 </xs:complexType>
                                                     
                              </xs:element>
                                                
                           </xs:sequence>
                                           
                        </xs:complexType>
                                      
                     </xs:element>
                                   
                     <xs:element name="Description2" type="xs:string" />
                                 
                  </xs:sequence>
                              
                  <xs:attribute name="ObjectType" type="xs:string" use="required" />
                            
               </xs:complexType>
                       
            </xs:element>
                  
         </xs:sequence>
             
      </xs:complexType>
        
   </xs:element>
</xs:schema>
```

