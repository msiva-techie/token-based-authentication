# Token-based-authentication
Token Based Authentication for MERN (MongoDB, Express, React, Node.js) Application

Prevent cross site scripting (XSS) and cross site request forgery (CSRF).
Secure the cookie with {secure:true,httpOnly:true}.
secure flag makes sure that the connection takes place only using https.

### Cross Site Scripting (XSS)
  Use cookies with httpOnly
    Client side javascript code cannot access httpOnly cookies
    
### Cross Site Request Forgery (CSRF)
  Use Double Submit Cookie to avoid CSRF attacks.
    Have token in a seperate cookie along with httpOnly cookie. Cross verify the token in httpCookie and the token in the second cookie to verify that the request is a valid.
    
### Double Submit Cookie
  1. The Access token (JWT) is stored in httpOnly cookie. JWT also contains an additional token (XSRF-token) which may be a random ID.
  2. We store this token (XSRF-token) in a seperate cookie which is not a httpOnly cookie making sure that client side javascript code to access it.
  3. After receiving both the cookies, the client will read the token (XSRF-token) from the second cookie and set this as the header to the subsequent requests.
  4. The server after receiving the httpCookie (contains JWT token) will cross verify the token (XSRF-token) in the request header.
  5. If the token (XSRF-token) in both request header and the JWT token are same, then the request is valid.

### Running the project
  1. Run mongodb
  2. Run authentication-server using "npm run start"
  3. Run authentication-client using "npm run start"
  4. Open localhost:3000
