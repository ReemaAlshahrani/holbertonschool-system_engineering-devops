# Simple Web Stack

## Diagram
```mermaid
graph TD
    User([User / Browser])
    DNS[DNS Server]
    
    subgraph Server["Single Server (IP: 8.8.8.8)"]
        Nginx[Web Server: Nginx]
        AppServer[Application Server]
        Code[Application Files / Codebase]
        DB[(Database: MySQL)]
    end

    User -->|1. Request www.foobar.com| DNS
    DNS -->|2. Resolves IP: 8.8.8.8| User
    User -->|3. HTTP Request| Nginx
    Nginx -->|4. Forward Dynamic Requests| AppServer
    AppServer -->|5. Access Codebase| Code
    AppServer -->|6. Query Data| DB
    DB -->|7. Return Data| AppServer
    AppServer -->|8. Response| Nginx
    Nginx -->|9. HTTP Response| User
