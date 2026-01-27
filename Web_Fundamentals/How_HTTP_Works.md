# The HyperText Transfer Protocol (HTTP)

## A Visual Guide to How HTTP Works

---

## 1. Anatomy of a URL

```mermaid
graph TD
    A[Complete URL] --> B[Protocol]
    A --> C[Host]
    A --> D[Port]
    A --> E[Resource Path]
    A --> F[Query String]
    
    B --> B1["http:// or https://"]
    C --> C1["example.com or api.example.com"]
    D --> D1[":80 or :443 (optional)"]
    E --> E1["/path/to/resource"]
    F --> F1["?param=value&key=data"]
```

### URL Example Breakdown

```mermaid
graph LR
    A["https://api.example.com:443/users?q=dave&max=50"] --> B[Protocol: https]
    A --> C[Host: api.example.com]
    A --> D[Port: 443]
    A --> E[Path: /users]
    A --> F[Query: q=dave&max=50]
```

---

## 2. Protocol Types

```mermaid
graph TD
    A{Protocol Type} --> B[HTTP]
    A --> C[HTTPS]
    
    B --> B1[Plain Text]
    B --> B2[Port 80 default]
    B --> B3[❌ Not Secure]
    B --> B4[Readable by attackers]
    
    C --> C1[Encrypted with TLS]
    C --> C2[Port 443 default]
    C --> C3[✅ Secure]
    C --> C4[Protected from eavesdropping]
    
```

---

## 3. DNS Resolution Process

```mermaid
sequenceDiagram
    participant Client
    participant HostsFile as Local Hosts File
    participant DNS as DNS Server
    participant Server
    
    Client->>HostsFile: Check localhost
    HostsFile-->>Client: 127.0.0.1 (loopback)
    
    Client->>DNS: nslookup ischool.uw.edu
    DNS-->>Client: IP: 128.208.201.29
    
    Client->>Server: Connect to 128.208.201.29
    Note over Client,Server: Connection Established
```

---


## 4. HTTP Request Structure

```mermaid
graph TD
    A[HTTP Request] --> B[Request Line]
    A --> C[Headers]
    A --> D[Blank Line]
    A --> E[Body - Optional]
    
    B --> B1["GET /path HTTP/1.1"]
    C --> C1["Host: example.com"]
    C --> C2["Authorization: Bearer token"]
    C --> C3["Content-Type: application/json"]

```

---


---

## 5. Complete HTTP Request/Response Cycle

```mermaid
sequenceDiagram
    participant Client
    participant DNS
    participant Server
    
    Note over Client: User enters URL
    Client->>DNS: Resolve hostname
    DNS-->>Client: Return IP address
    
    Note over Client,Server: TCP Connection
    Client->>Server: HTTP Request
    Note over Client,Server: Request Line: GET /users HTTP/1.1
    Note over Client,Server: Headers: Host, Authorization, etc.
    
    Note over Server: Process Request
    Server-->>Client: HTTP Response
    Note over Client,Server: Status Line: HTTP/1.1 200 OK
    Note over Client,Server: Headers: Content-Type, etc.
    Note over Client,Server: Body: Resource data
    
    Note over Client: Parse & Display
```



