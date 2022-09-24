# Access Control
Access control is a field which describes how restrict access to places or resources.
In computer security access control includes authentication and authorization.

In this chapter we are going use following terms:
* resource owner
  * An entity that wants to access his resource that is being protected by access control.
  * If the resource owner is a person it is being reffered as the user.
* protected resource
  * Information or a service that is being protected by a resource server
*  resource server
   *  A server hosting the protected resource.
* authorization server
  * A server that can authenticate and authorize a resource owner.
* client
  * An application making protected resource requests on behalf of the resource owner and with its authorization. 


# Authentication
**Authentication** is the act of proving an assertion, such as the identity of a computer system user. 

## Basic authentication
Basic authentication is a simple method to enable a HTTP client (e.g. web browser) to provide the user name and password as credential via HTTP. 

     +--------+                               +---------------+
     |        |--(A)- Authorization Request ->|   Resource    |
     |        |                               |     Owner     |
     |        |<-(B)-- Authorization Grant ---|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(C)-- Authorization Grant -->| Authorization |
     | Client |                               | & Resource    |
     |        |<-(D)-- Protected Resource ----| Server        |
     |        |                               +---------------+
     |        |
     +--------+ 

User name and password are written together with an colon (:) as a seperator and then encoded with the Base64 variant. At the HTTP Header with the key *Authorization* the encoded credentials are added with the string Basic as the value.

`Authorization: Basic <credentials Base64 encoded>`

The basic authentication mechanism does not provide confidentiality protection for the transmitted credentials. They are merely encoded with Base64 in transit and not encrypted or hashed in any way. Therefore, basic authentication is typically used in conjunction with HTTPS to provide confidentiality.

## OAuth2
In the traditional client-server authentication model, the client requests an access-restricted resource (protected resource) on the server by authenticating with the server using the resource owner's credentials.  In order to provide third-party applications access to restricted resources, the resource owner shares its credentials with
the third party.  This creates several problems and limitations:

* Third-party applications are required to store the resource owner's credentials for future use, typically a password in clear-text.

* Servers are required to support password authentication, despite the security weaknesses inherent in passwords.

* Third-party applications gain overly broad access to the resource owner's protected resources, leaving resource owners without any ability to restrict duration or access to a limited subset of resources.

* Resource owners cannot revoke access to an individual third party without revoking access to all third parties, and must do so by changing the third party's password.

* Compromise of any third-party application results in compromise of the end-user's password and all of the data protected by that password.

OAuth2 tackles these problems with access tokens. The client obtains an access token from an authorization server. The client then is able to use this token for the third party applications. 


     +--------+                               +---------------+
     |        |--(A)- Authorization Request ->|   Resource    |
     |        |                               |     Owner     |
     |        |<-(B)-- Authorization Grant ---|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(C)-- Authorization Grant -->| Authorization |
     | Client |                               |     Server    |
     |        |<-(D)----- Access Token -------|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(E)----- Access Token ------>|    Resource   |
     |        |                               |     Server    |
     |        |<-(F)--- Protected Resource ---|               |
     +--------+                               +---------------+



https://datatracker.ietf.org/doc/html/rfc6749
https://oauth.net/specs/
## OpenID
### Keycloak
## Other
There are also other methods such as SASL, SAML
# Authorization 
**Authorization** is the function of specifying access rights/privileges to resources, which is related to general information security and computer security, and to access control in particular. 

## Access Control Models
Access to accounts can be enforced through many types of controls.

* Attribute-based Access Control (ABAC)
An access control paradigm whereby access rights are granted to users through the use of policies which evaluate attributes (user attributes, resource attributes and environment conditions)
* Discretionary Access Control (DAC)
In DAC, the data owner determines who can access specific resources. For example, a system administrator may create a hierarchy of files to be accessed based on certain permissions.
* Graph-based Access Control (GBAC)
Compared to other approaches like RBAC or ABAC, the main difference is that in GBAC access rights are defined using an organizational query language instead of total enumeration.
* History-Based Access Control (HBAC)
Access is granted or declined based on the real-time evaluation of a history of activities of the inquiring party, e.g. behavior, time between requests, content of requests. For example, the access to a certain service or data source can be granted or declined on the personal behavior, e.g. the request interval exceeds one query per second.
* History-of-Presence Based Access Control (HPBAC)
Access control to resources is defined in terms of presence policies that need to be satisfied by presence records stored by the requestor. Policies are usually written in terms of frequency, spread and regularity. An example policy would be "The requestor has made k separate visitations, all within last week, and no two consecutive visitations are apart by more than T hours."
* Identity-Based Access Control (IBAC)
Using this network administrators can more effectively manage activity and access based on individual needs.
* Lattice-Based Access Control (LBAC)
A lattice is used to define the levels of security that an object may have and that a subject may have access to. The subject is only allowed to access an object if the security level of the subject is greater than or equal to that of the object.
Mandatory Access Control (MAC)
In MAC, users do not have much freedom to determine who has access to their files. For example, security clearance of users and classification of data (as confidential, secret or top secret) are used as security labels to define the level of trust.
* Organization-Based Access Control (OrBAC)
OrBAC model allows the policy designer to define a security policy independently of the implementation
* Role-Based Access Control (RBAC)
RBAC allows access based on the job title. RBAC largely eliminates discretion when providing access to objects. For example, a human resources specialist should not have permissions to create network accounts; this should be a role reserved for network administrators.
* Rule-Based Access Control (RAC)
RAC method, also referred to as Rule-Based Role-Based Access Control (RB-RBAC), is largely context based. Example of this would be allowing students to use labs only during a certain time of day; it is the combination of students' RBAC-based information system access control with the time-based lab access rules.
Responsibility Based Access Control
Information is accessed based on the responsibilities assigned to an actor or a business role.

Based upon the authentication the authorization server can retrieve the information it owns about the resource owner in order to authorize the resource owner. In case of OAuth2 or OpenID the 

A very common model is the RBAC in companies since the employess have multiple roles within a company and the roles. To manage these roles companies often use Active Directory from Microsoft to map the roles with groups in Activie Directory.
 
# Evolution in IAM
We can have also a look on **I**dentity **A**ccess **M**anagement (IAM) landscape with an perspective on data sourvarinity. As a resource owner I want to have more control over to whom I want to share my resources or my credentials.
## Central IAM
Not so long ago every resource server had to have their own IAM, meaning that the different for each system the resource owner was had to register 
## Federated IAM
Nowadays 
## Self Souvereign Identity
The federated provider from the prevoius model can become to knowledgeable about the resource owner with their possible monopol position.
New concepts currently evolve to make IAM more self souvereign.

**S**elf **S**ouvereign **I**denetity (SSI) is a field where the concepts try to decouple information about the user even further from the system that provide service.
We are going to have a look two concepts **V**erifiable **C**redential (VC) and **D**ecentralized **Id**enttifiers (DID).
VC is a concept where IAM is split into three roles Issuer, Holder and Verifier.
Issuer is a entity that is able to credit about a claim of a Person. For example a university is able to 

Systems that only want to grant their service or protocted resource when the user shares information about themself.
Then the system is able to verify that information and authenticate.
