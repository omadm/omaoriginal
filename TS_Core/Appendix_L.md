<strong> Appendix L. Example of Trigger Message from Server (Informative) </strong>

Example WAP Push over SMS containing the trigger information:


|Binary value|Meaning|Description|
|:-:|:--|:-:|
|06|User-Data-Header (UDHL) Length = 6 bytes|WDP layer (start WDP headers).|
|05|UDH IE identifier: Port numbers||
|04|UDH port number IE length||
|0B|Destination port (high)|Port number 2948|
|84|Destination port (low)||
|C0|Originating port (high)|Port number chosen by sender|
|02|Originating port (low)|WDP layer (end WDP headers)|
|01|Transaction ID / Push ID|WSP layer (start WSP headers)|
|06|PDU type (push)||
|03|Headerslength (content type+headers)||
|C4|Content type code|MIME-Type|
|AF|X-WAP-Application-ID||
|9A|Id for urn: x-wap-application:lwm2m.dm| WSP layer (end WSP headers)|
|{14-bytes}|112-bit clear value| Clear CoAP Text|

|CoAP raw bytes|Description|
|:-:|:--|
|44 02 b6 0b 21 61 fb 63 b1 31 01 30 01 38|PDU length:14 <br> CoAP Version: 1 <br> Message Type: Confirmable <br> Token length: 4 <br> Code: 0.02 POST <br> Message ID: 34488 <br> Token length: 4 <br> Value: 0x301e65ca <br><br> OPTION (0/3) <br> Option number (delta): 11(11)<br> Name: URI_PATH <br> Value length: 1 <br> Value: "1" <br><br> OPTION (1/3)<br> Option number (delta): 11(0) <br> Name: URI_PATH <br> Value length: 1 <br> Value: "0"<br><br> OPTION (2/3)<br> Option number (delta): 11(0)<br> Name: URI_PATH<br> Value length: 1<br> Value: "8"<br>No payload.|
