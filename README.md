## Auth

### 3 types of auth flows:
1. Stateful Sessions (Cookies)
2. Stateless JWT
3. Stateful JWT


### 1. Stateful Sessions (Cookies)
- session stored on server side (db, cache)
- session doesn't have meaningful data
- 4KB max size
- simple key-value string (`key=value`)
- CORS problem

Set by:
- server (`Set-Cookie` header)
- client (`document.cookie`)

Should have expiration

Flags:
- `HttpOnly` (cannot read by JS)
- `Secure` (can be sent over HTTPS only)
- `SameSite` (can be sent from the same domain, no CORS)


### JWT
- aren't stored on server side, only `client`
- reduce db lookups (token payload)
- 2 tokens: `access` (~30 min) / `refresh` (~1 month)
- `access`: [header] [payload] [signature]
- sent by `Authorization` header by client
- stored in `localStorage` (per domain)
- XSS problem
- 5MB max size

### 2. Stateless JWT
- token sent in `Authorization` cookie

### 3. Stateful JWT
- token sent in cookie with `HttpOnly` flag

### Stateless vs Stateful
- Stateful: You can revoke the authentication session on the IdP anytime.
- Stateless: The session expiration time is set when the authentication token is released. You cannot revoke the session on the IdP.


#### Resources
- https://www.youtube.com/watch?v=2PPSXonhIck&t=533s&ab_channel=CodeRealm
- https://web.dev/samesite-cookies-explained/

