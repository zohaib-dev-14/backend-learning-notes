# HTTP & Request Lifecycle (Backend Foundations)

---

## 1. What is HTTP?

HTTP (HyperText Transfer Protocol) is the communication protocol used between a client and a server.

Model:

Client → Request → Server
Server → Response → Client

HTTP is **stateless**, meaning each request is independent.

---

## 2. Structure of an HTTP Request

An HTTP request contains:

### 1. Method

* GET (Read data)
* POST (Create data)
* PUT (Replace data)
* PATCH (Partial update)
* DELETE (Remove data)

### 2. URL

Examples:

```
/notes
/notes/123
```

### 3. Headers

Extra metadata such as:

* Content-Type
* Authorization
* Cookies

### 4. Body (Optional)

Used mainly in POST / PUT / PATCH requests.

---

## 3. Structure of an HTTP Response

Server response contains:

* Status Code (200, 201, 400, 404, 500)
* Headers
* Body (JSON, text, etc.)

Example JSON response:

```json
{
  "message": "success"
}
```

---

## 4. Node.js Request Lifecycle (Deep Understanding)

### Step 1: Server Starts

```js
app.listen(3000)
```

Internally:

```js
http.createServer(app)
```

Port 3000 is opened and Node starts waiting for requests.

---

### Step 2: Client Sends Request

Example:

GET /notes

---

### Step 3: OS Detects Network Activity

The operating system detects activity on port 3000 and notifies Node.

Node emits a "request" event.

---

### Step 4: Node Calls Listener

Internally:

```js
server.on("request", app)
```

Node executes:

```js
app(req, res)
```

The Express app function becomes the request handler.

---

### Step 5: Express Pipeline Execution

Order of execution:

1. Global middleware
2. Route matching
3. Route handler execution
4. Response sent

---

### Step 6: Response Travels Back

Express → Node → OS → Client

After response is sent, server goes back to waiting state.

---

## 5. Middleware in Lifecycle

Middleware functions run before the final route handler.

Example:

```js
app.use(express.json())
```

Purpose:

* Parse JSON body
* Logging
* Authentication
* Validation

Execution order matters.

---

## 6. Complete Visual Flow

Client
↓
Internet
↓
OS (Port 3000)
↓
Node HTTP Server
↓
Express App (Listener)
↓
Middleware
↓
Route Handler
↓
Response
↓
Back to Waiting State

---

## Key Concepts Summary

* HTTP is stateless.
* Node.js is event-driven.
* Express app is a function used as a request listener.
* Middleware runs sequentially.
* Backend works as a request–response machine.

---

## Current Understanding Level

✔ HTTP structure
✔ Request & Response flow
✔ Node event-based handling
✔ Express middleware pipeline
✔ End-to-end lifecycle clarity

---

Next Topic Recommendation:
Authentication & Stateless Systems (JWT, Sessions, Cookies)
