
<strong> Appendix I. Media types </strong>

### I.1	Media-Type application/vnd.oma.lwm2m+tlv Registration

This section contains the IANA registration for media-type application/vnd.oma.lwm2m+tlv (see <http://www.iana.org/assignments/media-types/media-types.xhtml>).

Type name: application

Subtype name: vnd.oma.lwm2m+tlv

Required parameters: none

Optional parameters: none

Encoding considerations: binary

Security considerations:

> OMA LwM2M data is passive, meaning it does not contain executable or active content which may represent a security threat. The OMA LwM2M TLV format does not contain fields which are confidential. The usage of the LwM2M TLV format may be vulnerable to attacks modifying or spoofing the content of this format. The OMA LwM2M protocol uses source authentication and integrity protection.
>
> This media type inherits the security issues associated with the TLV format.

Interoperability considerations:

> This content type carries OMA LwM2M data model serialization within the scope of the OMA LwM2M enabler. The OMA LwM2M enabler specification includes static conformance requirements for this content.

Published specification:

> OMA LwM2M 1.0 Technical Specification – especially section 6.4.3. Available from <http://www.openmobilealliance.org>

Applications, which use this media type:

> OMA LwM2M

Fragment identifier considerations: none

Additional information:

-   Deprecated alias names for this type: none

-   Magic number(s): none

-   File extension(s): none

-   Macintosh File Type Code(s): none

Intended usage: Limited use. Only for usage with OMA LwM2M, which meet the semantics given in the mentioned specification.

Restriction on usage: no

Person & email address to contact for further information:

> John Mudge
>
> <helpdesk@omaorg.org>

Author/Change controller:

> Open Mobile Naming Authority (OMNA)
>
> <OMA-OMNA@mail.openmobilealliance.org>

Provisional registration (standards tree only): N/A

### I.2	Media-Type application/vnd.oma.lwm2m+json Registration

This section contains the IANA registration for media-type application/vnd.oma.lwm2m+json (see <http://www.iana.org/assignments/media-types/media-types.xhtml>).

Type name: application

Subtype name: vnd.oma.lwm2m+json

Required parameters: none

Optional parameters: none

Encoding considerations: Encoding considerations are identical to those specified for the "application/json" media type.

See RFC7159.

Security considerations:

> OMA LwM2M data is passive, meaning it does not contain executable or active content which may represent a security threat. The OMA LwM2M JSON format does not contain fields which are confidential. The usage of the LwM2M JSON format may be vulnerable to attacks modifying or spoofing the content of this format. The OMA LwM2M protocol uses source authentication and integrity protection.

Interoperability considerations:

> This content type carries OMA LwM2M data model serialization within the scope of the OMA LwM2M enabler. The OMA LwM2M enabler specification includes static conformance requirements for this content.

Published specification:

> OMA LwM2M 1.0 Technical Specification – especially section 6.4.4. Available from <http://www.openmobilealliance.org>

Applications which use this media type:

> OMA LwM2M

Fragment identifier considerations: none

Additional information:

-   Deprecated alias names for this type: none

-   Magic number(s): none

-   File extension(s): none

-   Macintosh File Type Code(s): none

Intended usage: Limited use. Only for usage with OMA LwM2M, which meet the semantics given in the mentioned specification.

Restriction on usage: no

Person & email address to contact for further information:

> John Mudge
>
> <helpdesk@omaorg.org>

Author/Change controller:

> Open Mobile Naming Authority (OMNA)
>
> <OMA-OMNA@mail.openmobilealliance.org>

Provisional registration (standards tree only): N/A
