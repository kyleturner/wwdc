Networking Best Practices
==========

* **Latency**: RTT for communication from phone to server and back, number of time packets have to spend in queues and in links

Hiding latency from the user is a great way to enhance the user experience.

* Perform networking asynchronously
* Responsive user interface, use placeholders and fill in with data once it arrives
* Use one connection with concurrent requests, such as *HTTP Pipelining*
* Request early!  No need to wait if you know you'll need it
* Cache that shit!


HTTP APIs
-----

```NSURLConnection```

* Asynchronous event-based API
* Perisistent connections, pipelining, authentication, caching, cookies, SOCKS and HTTP proxy are automatic!
* Maintain pool of connections, dynamically assign request to connection, response may come from cache

**Lifecycle**

* Create NSURLRequest
* Send request
* Wait for response
* Wait for data
* Finish or error

**HTTP Pipelining**

```[NSMutableURLRequest setHTTPShouldUsePipelining:]```

