JWTs and Angular
----------------
1. the application server can be completely stateless; the authentication server can issue the token, send it back and then immediately discard it
2. JWTs are a JSON payload containing a particular claim
3. dwe don't have to keep JWTs in memory between requests to confirm that the claim is valid because they carry a Message Authentication Code or MAC
4. JWTs are made up of a signature, payload, and header


### Payload
1. the payload is just a plain javascript object
2. the payload could be anything such as info about a bank transfer; there are no restrictions on the content of the payload, but any information in the token is readable to anyone who intercepts the token.
{
	"name": "John Doe",
	"email": "john@johndoe.com",
	"admin": true
}

the content of the payload is validated by the receiver by inpecting the signature

### Header
1. JSON object holding metadata information about the token itself
valid header:
{
	"alg": "RS256",
	"type": "JWT"
}

### Signature
1. is a message authentication code (MAC)
2. the signature can only be produced by someone in possession of the payload (plus header) and a given secret
3. the presence of the signature makes a JWT self-validating


### How signature works with Auth??
1. user submits username and password to the auth server (application server or a separate server - typical)
2. the server validates teh username and password combo and creates a JWT token with payload containing the user technical identifier and an expiration timestamp
3. the auth server takes the secret key, uses it to sign the header plus payload, then sends it back to the user browser
4. the browser takes the signed JWT and sends it with each HTTP request to our application server
5. the signed JWT acts as a temporary user credential, that replaces the username and password combo
6. the application server checks the JWT signature, confirms the payload was signed by someone with the secret key
7. the payload identifies a particular user via a technical identifier
8. only the auth server has the private key, the auth server only gives out tokens to users that submit the correct password
9. the server proceeds with processing the HTTP request assuming it belongs to that user
10. the only way for an attacker to impersonate a user would be to steal the username/password or steal teh secret signing key from the auth server
11. the signature is a very important part of the JWT
12. with JWTs the server that issued the JWT and the auth server can be separate servers

### Base64 
1. when sending JWTs across the network we encode in base64 to ensure we don't run into character encoding issues
2. encoding issues happen because different computers across the world are handling strings in different character encodings ie. UTF-8, ISO 8859-1, etc.
3. in order to not have to deal with these issues we choose a subset of characters taht all common encodings handle the same way, base64 encoding

### Base64 vs Base64Url
1. what we see in JWT is actually Base64Url instead of Base64
2. Base64Url is similar to Base64 but there are a couple of characters different so that we can easily sned a JWT as part of a url parameter
3. header and payload are two javascript objects, converted to jSON and encoded in base64url and separated by a dot

### Standard JWT payload properties
1. iss - the issuing entity; authentication server
2. iat - the timestamp of creation of the JWT (seconds since epoch)
3. sub - contains the technical identifier of the user
4. exp - the token expiration timestamp

### Signature types
1. HS256
2. RS256

### HS256
1. HS256 - digital signature based on a cryptographic hashing function

### Hashing function (SHA-256)
1. special function with some unique properties
2. lots of practical use cases like digital signatures
3. http://www.xorbin.com/tools/sha256-hash-calculator (output tool)
4. irreversibility (property 1)
5. reproducible (property 2)
6. no collisions (property 3)
7. unpredictability (property 4)

### Irreversibility
- if we take our header and payload and run it through the function, you can't get the data back by looking at the output
- hashing is not encryption, encryption is reversible

### Reproducible
- if we hash the same input header and payload multiple times, we will always get back the same exact result
- given a pair of inputs and a has output, we can always validate if a given output (signature) is corect

### No Collisions
- if we submit multiple values to a hashing function, we always get back a unique result per input value
- there are no situations when two different inputs will give the same output

### Unpredictability
- given a known output, it's not possbile to guess the input using a successive incremental approximation method
- it won't work because in a hashing function, if we change even a single character in the input, on average 50% of the output bits will change, so even minimal differences in the input create a completely different output

### Use hashing function to produce a signature?
- we take the header, payload, add a secret password, then hash everything together
- the result is a SHA-256 HMAC or hash-based message authentication code, one example of a function that does that is the HMAC-SHA256 function, used in HS256 signatures
- the result of that function can only be reproduced by someone in possession of the JWT header, the payload, and the password; the hased result proves that the payload was created and then signed by someone with the password

Sources:
- https://blog.angular-university.io/angular-jwt/