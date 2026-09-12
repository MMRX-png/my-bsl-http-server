# my-bsl-http-server

A low-level HTTP web server built from scratch in the **Bonezegei Scripting Language (BSL)**, using the BSL Socket Library. The server binds directly to a TCP socket, parses raw incoming HTTP requests, and manually constructs HTTP responses — no frameworks involved.

This project was built for **Lab 1: Building an HTTP Server using Socket**.

## 1. Project Description

`my-bsl-http-server` is a minimal HTTP server that demonstrates how the HTTP protocol works at the socket level. It listens on **port 8080** and handles three cases:

| Route | Method | Response |
|---|---|---|
| `/` | GET | `200 OK` — HTML welcome/landing page |
| `/about` | GET | `200 OK` — HTML page about the project |
| Any other path | GET | `404 Not Found` — custom HTML error page |

Rather than relying on a built-in HTTP module, the server reads the raw request text off the socket, inspects the request line for the path being requested, and writes back a hand-built HTTP response (status line + headers + HTML body).

## 2. Installation & Setup Guide

### Prerequisites
- [Visual Studio Code](https://code.visualstudio.com/)
- The **Bonezegei Scripting Language Formatter** extension (search "Bonezegei" in the VS Code Extensions tab)
- The BSL interpreter, installed via the instructions embedded in the extension

### Step 1 — Install the BSL interpreter

Follow the install path for your OS, as described in the Bonezegei extension:

- **Windows / Linux:** Follow the native installation instructions provided in the extension guide.
- **macOS / Android:** Use **GitHub Codespaces** and follow the Linux installation process, since there is no native macOS build.

### Step 2 — Install the Socket library

From your terminal, in the project root:

```bash
bzg install socket
```

This downloads the socket library into `lib/socket.bzg`, which `src/http.bzg` includes.

### Step 3 — Clone this repository

```bash
git clone https://github.com/<your-username>/my-bsl-http-server.git
cd my-bsl-http-server
```

### Step 4 — Run the server

```bash
bzg run src/http.bzg
```

You should see:

```
Socket Ready
Server running on http://localhost:8080/
```

## 3. Usage Instructions

With the server running, open a browser and visit:

- **Home page:** [http://localhost:8080/](http://localhost:8080/) → 200 OK welcome page
- **About page:** [http://localhost:8080/about](http://localhost:8080/about) → 200 OK about page
- **Any unmapped route**, e.g. [http://localhost:8080/anything](http://localhost:8080/anything), [http://localhost:8080/home](http://localhost:8080/home) → 404 Not Found page

Every request is also logged to the terminal running the server, so you can watch raw HTTP requests come in as you browse.

## 4. Project Structure

```
my-bsl-http-server/
├── .gitattributes          # Forces GitHub to highlight *.bzg as JavaScript
├── LICENSE                 # MIT License
├── README.md
├── src/
│   └── http.bzg            # Main server source code
└── documentation/
    ├── home.png             # Screenshot of / route
    ├── about.png            # Screenshot of /about route
    ├── 404.png              # Screenshot of an unmapped route
    └── terminal.png         # Screenshot of terminal (username & dir visible)
```

## 5. Screenshots

### `/` — Home Route
![Home route](documentation/home.png)

### `/about` — About Route
![About route](documentation/about.png)

### 404 — Unmapped Route
![404 route](documentation/404.png)

### Terminal Output
![Terminal running the server](documentation/terminal.png)

## 6. License

This project is licensed under the [MIT License](LICENSE).
