### 1. 

#### a) What is encapsulation, and how does it happen at each layer of the 5-layer TCP/IP model?

**Encapsulation** is the process of wrapping data with protocol information at each layer of the network model. In the 5-layer TCP/IP model, data moves through each layer, and each layer adds its own header (and sometimes trailer) information.

- **Application Layer**: Provides data (for example, an HTTP message).
- **Transport Layer**: Encapsulates the application data with a transport header (like TCP/UDP header), forming a segment (TCP) or datagram (UDP).
- **Network Layer**: Adds an IP header, creating a packet.
- **Data Link Layer**: Wraps the packet in a frame by adding a MAC header and trailer.
- **Physical Layer**: Converts frames into electrical/optical signals and transmits them over the medium.

---

#### b) i) State the purpose of Cookies in web applications. Mention the different types of Cookies.

**Purpose of Cookies:**  
Cookies store user data (session information, preferences, authentication tokens) on the client-side to maintain state across multiple requests.

**Types of Cookies:**
- **Session Cookies**: Temporary, deleted after the browser is closed.
- **Persistent Cookies**: Stored on the device for a set duration, used for remembering login info, preferences.
- **Secure Cookies**: Only transmitted over HTTPS.
- **HttpOnly Cookies**: Not accessible via JavaScript, helps mitigate XSS attacks.
- **SameSite Cookies**: Control whether cookies are sent with cross-site requests.

---

#### b) ii) Elaborate on the key components of a web browser engine and the process of rendering a web page.

**Key Components of Web Browser Engine:**
- **Rendering Engine** (e.g., Blink, WebKit): Parses HTML, CSS and renders content.
- **JavaScript Engine** (e.g., V8, SpiderMonkey): Executes JS code.
- **Networking Layer**: Handles HTTP(S) requests/responses.
- **UI Backend**: Draws widgets, windows, scroll bars.
- **Data Storage**: Stores cache, cookies, local storage.

**Process of Rendering a Web Page:**
1. **HTML Parsing**: Constructs a DOM tree from HTML.
2. **CSS Parsing**: Builds a CSSOM tree from CSS.
3. **Render Tree Construction**: Combines DOM and CSSOM to form the render tree.
4. **Layout**: Calculates the position and size of elements.
5. **Painting**: Draws pixels onto the screen.

---

#### c) With an example code describe the purpose of Idempotent HTTP methods GET, PUT and DELETE. Also explain the purpose of HTTP cache and its types.

**Idempotent HTTP Methods:**
- **GET**: Retrieve data; multiple identical requests produce the same result and do not change server state.

    ```http
    GET /api/user/123
    ```

- **PUT**: Update or create a resource; sending the same request multiple times has the same effect as once.

    ```http
    PUT /api/user/123
    Body: { "name": "Alice" }
    ```
- **DELETE**: Remove a resource; repeating the request produces the same outcome (the resource remains deleted).

    ```http
    DELETE /api/user/123
    ```
**Purpose of HTTP Cache:**
HTTP cache improves performance by storing responses and reusing them for subsequent requests, reducing load times and server strain.

**Types of HTTP Cache:**
- **Browser Cache**: Stores resources on the client-side, reuses for the same site.
- **Proxy Cache**: Stores responses at intermediate proxy servers for multiple users.
- **Gateway Cache (Reverse Proxy)**: Used by CDNs, caches responses closer to end-users.

---