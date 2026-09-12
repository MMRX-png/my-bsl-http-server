my-bsl-http-server is a lightweight HTTP web server built entirely from scratch in the Bonezegei Scripting Language (BSL), using only the low-level BSL Socket Library — no web frameworks, no HTTP libraries. The project was created to demonstrate a foundational understanding of how the HTTP protocol actually works underneath the frameworks developers use every day: opening a TCP socket, binding it to a port, listening for and accepting client connections, reading a raw incoming HTTP request as text, and manually constructing a valid HTTP response (status line, headers, and HTML body) before sending it back over the wire.

The server binds to port 8080 and implements simple path-based routing:

/ — serves a landing/welcome page with a 200 OK response

/about — serves an about page describing the project with a 200 OK response

Any other path — serves a custom 404 Not Found page

Each incoming request is logged to the terminal in real time, making it easy to observe the raw request/response cycle as it happens. This project serves as a hands-on introduction to socket programming, HTTP fundamentals, and basic server-side routing logic.
