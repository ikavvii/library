Managing how objects (resources) are created and handled is crucial in full-stack enterprise applications because it directly impacts scalability, performance, and memory management.

These three concepts—**Object per Client**, **Object per Request**, and **Object Pooling**—are essentially strategies for managing the _lifecycle_ of objects in a server environment.

---

## 1. Object per Client

In this model, the server creates a specific object instance dedicated to a single client. This object remains alive and attached to that client for the duration of their session or connection.

### The Concept

Think of this like a **Personal Shopper**. When you enter a store, a specific employee is assigned to you. They walk with you, hold your items, and remember your preferences until you leave the store. No one else can use that employee while they are helping you.

- **Stateful:** The object "remembers" data between calls from the same client.
    
- **Lifecycle:** Starts when the client connects/logs in and ends when they disconnect/log out (or time out).
    

### Where it's used

- **Stateful Session Beans (EJB):** In older Java EE architecture.
    
- **Shopping Carts:** A cart object often stays alive in the server's memory (session) for a specific user.
    
- **Desktop/Client-Server Apps:** Where a dedicated connection (TCP) is kept open.
    

### Pros & Cons

|**Pros**|**Cons**|
|---|---|
|**Convenience:** Easy to maintain state (e.g., keeping track of steps in a wizard).|**Scalability Issues:** If you have 10,000 clients, you need 10,000 objects in memory.|
|**Performance (per user):** No need to fetch user data from the DB for every single click.|**Resource Hog:** Memory usage stays high even if the client is idle (thinking about what to click next).|

---

## 2. Object per Request

This is the most common model in modern RESTful APIs and web applications. The server creates an object when a request comes in, uses it to process that specific request, and then immediately destroys it (or marks it for garbage collection) once the response is sent.

### The Concept

Think of this like a **Fast Food Cashier**. You walk up, place an order, they process it, hand you the receipt, and say "Next!". If you come back 5 seconds later to order fries, the cashier treats it as a brand new interaction. They don't "remember" your previous interaction personally; the computer system might, but the interaction itself is transactional.

- **Stateless:** The object does not retain data between different requests from the same client.
    
- **Lifecycle:** Created at the start of an HTTP request; destroyed at the end of the HTTP response.
    

### Where it's used

- **Spring Controllers / MVC:** By default, controllers and services are often stateless singletons handling requests, or new objects are spun up per request.
    
- **REST APIs:** Every call (GET, POST) is independent.
    
- **Serverless Functions (AWS Lambda):** The environment spins up, runs code, and shuts down.
    

### Pros & Cons

|**Pros**|**Cons**|
|---|---|
|**High Scalability:** The server only uses memory while actively processing a request. Idle clients consume zero server resources.|**State Management Complexity:** You must store state externally (Database, Redis, Cookies) because the object won't remember it.|
|**Simplicity:** No need to worry about one user's data accidentally leaking into another user's session.|**Overhead:** Creating and destroying objects thousands of times per second can cause "Garbage Collection" pressure (though modern JVMs handle this well).|

---

## 3. Object Pooling

Object pooling is a performance optimization technique. Instead of creating and destroying heavy objects repeatedly (which is expensive), you keep a "pool" of ready-to-use objects. When a request comes in, it "borrows" an object. When it's done, it "returns" it to the pool rather than destroying it.

### The Concept

Think of this like a **Taxi Rank**. The taxis are already built, fueled, and waiting. You (the request) get in a taxi, go to your destination, and get out. The taxi doesn't get destroyed; it drives back to the rank to pick up the next passenger.

- **Reusable:** Objects are recycled.
    
- **Lifecycle:** The pool starts at server startup. Individual objects live for a long time within the pool.
    

### Where it's used

- **Database Connections:** Creating a connection to a database is very slow (handshakes, authentication). We use Connection Pools (like HikariCP) so we don't have to connect/disconnect for every query.
    
- **Thread Pools:** Reusing worker threads to handle tasks.
    
- **Heavy Resources:** Anything that takes a long time to initialize (e.g., complex graphics parsers).
    

### Pros & Cons

|**Pros**|**Cons**|
|---|---|
|**Performance:** drastically reduces initialization time for heavy resources (like DB connections).|**Complexity:** You must manage the pool (what happens if the pool is empty? Do requests wait or fail?).|
|**Resource Control:** Prevents the server from crashing by limiting the maximum number of active objects (e.g., "Max 50 DB connections").|**"Stale" Objects:** If an object in the pool gets corrupted or the connection drops, the next user might get a broken object.|

---

## Comparison Summary

|**Feature**|**Object per Client**|**Object per Request**|**Object Pooling**|
|---|---|---|---|
|**Analogy**|Personal Shopper|Fast Food Cashier|Taxi Rank|
|**Duration**|Entire User Session|Single HTTP Request|Indefinite (Reused)|
|**State**|Stateful (Remembers you)|Stateless (Forgets you)|Cleaned before reuse|
|**Best For**|Shopping carts, Wizards, complex workflows|REST APIs, High traffic web apps|Database connections, Threads|

### Which one should you use?

- **Use Object per Request** for 90% of your business logic (Services, Controllers). It scales best.
    
- **Use Object Pooling** strictly for _expensive_ infrastructure resources (Database connections, sockets).
    
- **Use Object per Client** rarely, perhaps only for specific caching needs or very complex user sessions (though usually, we store this data in a database/Redis instead of a live object).
    

---

### Knowledge Check

If you were building a banking app where millions of users check their balance, but only a few thousand make transfers at any one time:

1. How would you handle the HTTP requests? (**Answer:** Object per Request)
    
2. How would you handle the connections to the SQL database? (**Answer:** Object Pooling)
    

Would you like to see a simple Java/Spring code snippet demonstrating the difference between a "Singleton/Per Request" bean and a "Session" bean?