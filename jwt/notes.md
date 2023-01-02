A json web token or jwt ("jot") is a representation of a series of claims, with a signature to verify its authenticity

{
	"alg": "HS256",
	"typ": "JWT"
}

{
	"sub": "1234567890",
	"name": "John Doe",
	"admin": true
}

claims are definitions or assertions made about a certain party or object, some of the claims are apart of the JWT spec and others are user defined.

Standard claims:
- sub (subject)

Key aspects of JWTs
- possibility of signing them using JSON Web Signatures (JWS)
- and/or encrypting them using JSON Web Encryption (JWE)

JWT Purpose:
- main purpose is to transfer claims between two parties


JWT Uses:
- authentication
- authorization
- federated identity
- client-side sessions ("stateless" sessions)
- client-side secrets

## Practical Applications

### client-side/stateless sessions: client-side data
1. key aspect is the use of signing and possibly encryption to authenticate and protect the session contents
2. client-side data is subject to tampering, so must be handled with care by backend.
3. JWTs can provide different types of signatures and encryption
4. signatures are useful to validate the data against tampering
5. encryption is useful to protect the data from being read by third parties
6. a common claim that can be usually be ready by third parties is teh sub claim. subject usually identifies one of the parties to the other (ie. user IDs or emails). it is not a requirement that this claim be unique
7. therefore, additional claims may be required to uniquely identify a user
8. a claim that could be "open" is one representing a user's shopping cart, a third party (client-side script) might be able to get these items if they are stored in an unencrypted JWT
9. the server can trust signed data be unmodified if the signature check passes


Signed JWTs consist of:
- header
- payload
- signature

Signature Stripping
1. common way of attacking a signed JWT is to remove the signature
2. since the 3 parts of a signed JWT are encoded separately it's possible to remove the signature and change the header to claim the JWT is unsigned


** be careful with certain JWT validation libraries ** 
- can result in unsigned tokens being taken as valid tokens (may allow an attacker to modify the payload at his or her discretion)
- make sure the validation application does not consider unsigned JWTs valid

### Cross-Site Request Forgery (CSRF)
1. attacks attempts to perform requests against sites where the user is logged in by tricking the user's browser into sending a request from a different site
2. to accomplish this, a specially crafed site (or item) must contain the URL to the target (ie. <img> tag embedded in a malicious page with src pointing to the attack's target)
<img src="http://target.site.com/add-user?user=name&grant=admin">
3. the img tag above will send a request to target.site.com when the page that contains it is loaded. If the user had logged in before to target.site.com and the site used a cookie to keep the session active, the cookie would be sent as well.
4. JWTs, like any other client-side data, can be stored as cookies
5. short-lived JWTs can help
6. common csrf mitigation techniques include adding special headers to requests only when they are performed from the right origin, per session cookies, and per request tokens
7. CSRF attacks aren't possible if JWTs (and session data) are not stored as cookies, cross-site scripting attacks are still possible though

### Cross-Site Scripting (XSS)
1. attacks attempt to inject javascript in trusted sites
2. injected javascript can then steal tokens from cookies and localstorage
3. common XSS attacks are usually caused by improper validation of data passed to the backend (like sql injection attacks) - data sanitization
4. mitigation techniques rely on proper validation of all data passed to the backend; any data received from clients must always be sanitized
5. if cookies are used, cookies can be protected from being accessed by javascript by setting the HttpOnly flag;
6. The HttpOnly flag won't protect the cookie from CSRF attacks

### Federated Identity
1. systems allow different parties to share authentication and authorization services with other parties (a user's identity is centralized)
2. federated identity management solutions: (most common)
 - SAML
 - OpenID Connect
3. some companies use JWT
4. the use of JWTs for centralized authentication and authorization varies but the essential flow of the authorization process is:
  - server <--> user (bi-directional): use attempts to access a resource controlled by server
	- user <--> authorization server (bi-directional): 
	- user <--> identity provider (bi-directional)
	- user <--> authorization server (bi-directional)
	- user <--> server (bi-directional)
	- server -> resource