# How Browsers Work: A Visual Guide

## Overview
This guide explains the journey from typing a URL to seeing a webpage, using visual diagrams to illustrate each step.

---

## 1. URL Processing Flow

```mermaid
graph TD
    A[User Input in Address Bar] --> B{Input Type?}
    B -->|Random Text| C[Transform to Search URL]
    B -->|Domain Name| D[Normalize to Full URL]
    B -->|Full URL| E[Use as-is]
    C --> F[https://google.com/search?q=pizza]
    D --> G[https://example.com]
    E --> G
    G --> H[Ready for HTTP Request]
```

---

## 2. Complete Browser Request Pipeline

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant DNS
    participant Server
    
    User->>Browser: Enter URL
    Browser->>Browser: Parse URL
    Browser->>Browser: Create HTTP Request
    Browser->>DNS: Resolve domain to IP
    DNS-->>Browser: Return IP Address
    Browser->>Server: TCP Handshake (SYN)
    Server-->>Browser: TCP Response (SYN-ACK)
    Browser->>Server: TCP Confirm (ACK)
    Note over Browser,Server: TCP Connection Established
    Browser->>Server: Send HTTP Request
    Server-->>Browser: Send HTTP Response
    Browser->>Browser: Parse HTML & Build DOM
    Browser->>Browser: Apply CSS & Layout
    Browser->>Browser: Paint & Composite
    Browser->>User: Display Webpage
```

---

## 3. URL to HTTP Request Transformation

```mermaid
graph LR
    A[URL: https://example.com] --> B[Parse Components]
    B --> C[Protocol: HTTPS]
    B --> D[Host: example.com]
    B --> E[Path: /]
    C --> F[HTTP Request Headers]
    D --> F
    E --> F
    F --> G[Host: example.com<br/>Accept: text/html<br/>User-Agent: ...]
```

---

## 4. DNS Resolution Process

```mermaid
graph TD
    A[Domain: example.com] --> B[DNS Query]
    B --> C{DNS Server}
    C --> D[Lookup Domain]
    D --> E[IP Address: 93.184.216.34]
    E --> F[Return to Browser]
    F --> G[Browser can connect to server]
```

---

## 5. TCP Three-Way Handshake

```mermaid
sequenceDiagram
    participant Client as Browser<br/>seq=0, ack=0
    participant Server as Server<br/>seq=0, ack=0
    
    Note over Client,Server: Step 1: SYN
    Client->>Server: SYN (seq=1000)
    Note over Server: State: SYN-RECEIVED
    
    Note over Client,Server: Step 2: SYN-ACK
    Server->>Client: SYN-ACK (seq=5000, ack=1001)
    Note over Client: State: ESTABLISHED
    
    Note over Client,Server: Step 3: ACK
    Client->>Server: ACK (ack=5001)
    Note over Server: State: ESTABLISHED
    
    Note over Client,Server: Connection Ready for Data Transfer
```


---

## 6. HTML Parsing to DOM Tree

```mermaid
graph TD
    A[HTML Bytes] --> B[Tokenization]
    B --> C{Token Type}
    C -->|Start Tag| D[Create Element Node]
    C -->|Text| E[Create Text Node]
    C -->|End Tag| F[Close Element]
    D --> G[Build DOM Tree]
    E --> G
    F --> G
    G --> H[DOM Ready]
```

---

## 7. DOM Tree Structure Example

```mermaid
graph TD
    A[Document] --> B[html]
    B --> C[head]
    B --> D[body]
    C --> E[title: Example Domain]
    D --> F[main]
    F --> G[h1: Example Domain]
    F --> H[p: An example paragraph]
    F --> I[p]
    I --> J[a: An example link]
```

---

