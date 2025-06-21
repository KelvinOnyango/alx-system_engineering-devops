# Simple Web Infrastructure Design

![Simple Web Stack Diagram](https://i.imgur.com/0-simple_web_stack_diagram.png)  
*(Replace with your actual image link after uploading)*

## Infrastructure Components

1. **Server**  
   - A single physical/virtual machine hosting all components
   - IP Address: 8.8.8.8

2. **Domain Name (foobar.com)**  
   - Translates human-readable `www.foobar.com` to server IP (8.8.8.8) via DNS

3. **DNS Record**  
   - `www.foobar.com` uses a **CNAME record** pointing to `foobar.com`
   - `foobar.com` uses an **A record** pointing to 8.8.8.8

4. **Web Server (Nginx)**  
   - Handles HTTP/HTTPS requests
   - Serves static files (HTML, CSS, images)
   - Proxies dynamic requests to application server

5. **Application Server**  
   - Executes backend code (Python/Django, Node.js, etc.)
   - Processes business logic
   - Communicates with database

6. **Database (MySQL)**  
   - Stores and manages application data
   - Handles user accounts, content, etc.

7. **Communication Flow**  
