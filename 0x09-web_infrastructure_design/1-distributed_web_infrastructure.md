# Distributed Web Infrastructure Design

![Distributed Infrastructure Diagram](https://raw.githubusercontent.com/KelvinOnyango/alx-system_engineering-devops/main/0x09-web_infrastructure_design/1-distributed_web_infrastructure.png)

## Added Components

1. **Additional Server**
   - **Purpose**: Provides redundancy and handles increased traffic
   - **Implementation**: Second web server (Nginx) identical to first

2. **Load Balancer (HAProxy)**
   - **Purpose**: Distributes traffic evenly across web servers
   - **Algorithm**: Round Robin (cycles through servers sequentially)
   - **Setup**: Active-Active (both servers handle traffic simultaneously)

3. **Database Primary-Replica**
   - **Primary**: Handles all write operations (INSERT/UPDATE/DELETE)
   - **Replica**: Handles read operations (SELECT), syncs with primary

## Key Explanations

### Load Balancer Configuration
- **Distribution Algorithm**: Round Robin
  ```plaintext
  Request 1 → Web Server 1
  Request 2 → Web Server 2
  Request 3 → Web Server 1
  Active-Active vs Active-Passive:

- Active-Active: All servers handle traffic (used here)
- Active-Passive: Backup servers only activate during failures
  
 ### Database Cluster
 Application → Primary (Writes)
             ↓ Replicates
Application → Replica (Reads)

### Current Infrastructure Issues

#### **Remaining SPOFs (Single Points of Failure):**
- Single load balancer (no HAProxy backup)
- Single application server
- Primary database failure stops writes

#### **Security Issues:**
- No firewall rules shown
- Traffic not encrypted (no HTTPS)
- No authentication between servers

#### **Monitoring Gaps:**
- No alert system for failures
- No traffic metrics collection
- No health checks beyond HAProxy
