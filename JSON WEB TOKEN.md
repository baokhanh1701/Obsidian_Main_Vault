An open standard (RFC 7519)
-   **Compact**: Because of its size, it can be sent through an URL, POST parameter, or inside an HTTP header. Additionally, due to its size its transmission is fast.
-   **Self-contained**: The payload contains all the required information about the user, to avoid querying the database more than once.
Way for securely transmitting information bwt parties using JSON object.
- Digitally signed.
- JWTs can be signed using a secret (with HMAC algorithm) or a public/private key pair (RSA).

# Keywords
- Single Sign On
- public/private key pair
- Base64Url
- **Bearer** Schema
## JWT structure

`xxxxx.yyyyy.zzzzz`

### Header
	- typically consists of:
		- type of token (JWT)
		- hasing algorithm (HMAC SHA256, RSA)
	- **Base64Url**
```
{
  'alg': 'HS256',
  'typ': 'JWT'
}
```

### Payload
```
{ "sub": "1234567890", "name": "John Doe", "admin": true }
```

- contains the *claims*
- Claims are statements about an entity (user) and additional metadata.
	**- Reserved (registered) claims:**
	- predefined claims
	- not mandatory but recommended
		- `iss (issuer)`
		- `exp (expiration time)`
		- `sub (subject)`
		- `aud (audience)`
	**- Public claims:**
		These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the [IANA JSON Web Token Registry](https://www.iana.org/assignments/jwt/jwt.xhtml) or be defined as a URI that contains a collision resistant namespace.
	**- Private claims:**
		These are the custom claims created to share information between parties that agree on using them and are neither _registered_ or _public_ claims.

*> Do note that for signed tokens this information, though protected against tampering, is readable by anyone. Do not put secret information in the payload or header elements of a JWT unless it is encrypted.*

### Signature
To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

```
HMACSHA256( 
base64UrlEncode(header) + "." + 
base64UrlEncode(payload), 
secret)
``` 

## How do JWTs work?

![[Pasted image 20230227001644.png]]![[Pasted image 20230227002343.png]]
1.  The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows. For example, a typical [OpenID Connect](http://openid.net/connect/) compliant web application will go through the `/oauth/authorize` endpoint using the [authorization code flow](http://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth).
2.  When the authorization is granted, the authorization server returns an access token to the application.
3.  The application uses the access token to access a protected resource (like an API).

## But why should we use JWTs?

compared with: 
	 **Simple Web Tokens (SWT)**
	 **Security Assertion Markup Language Tokens (SAML)**
--

- JSON less verbose than XML
	- encoded size smaller --> JWT more compact than SAML --> easier to passed in HTML/HTTP environments
- Security-wise since:
> *SWT can only be symmetrically signed by a shared secret using the HMAC algorithm.*
`However, JWT and SAML tokens can use a public/private key pair in the form of a X.509 certificate for signing. Signing XML with XML Digital Signature without introducing obscure security holes is very difficult when compared to the simplicity of signing JSON.`

- More common:
	- JSON parsers map directly to objects.
	- XML doesn't have a natural document-to-object mapping.
	- easier to work with JWT than SAML assertions.

JWT is used at Internet scale.
	 ease of client-side processing of JWT on multiple platforms.
![[Pasted image 20230227003814.png]] 