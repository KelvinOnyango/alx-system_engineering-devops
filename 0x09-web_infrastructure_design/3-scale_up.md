# Scaled Up Infrastructure Design

![Scaled Infrastructure Diagram](https://raw.githubusercontent.com/YOUR-USERNAME/alx-system_engineering-devops/main/0x09-web_infrastructure_design/3-scale_up.png)

## Architectural Changes

1. **New Server Additions**:
   - Dedicated **Web Tier** (2+ Nginx servers)
   - Dedicated **App Tier** (2+ application servers)
   - Dedicated **Database Tier** (Primary + Replica)

2. **HAProxy Cluster**:
   - Primary/Secondary setup with Keepalived (VRRP)
   - Automatic failover if primary LB fails

3. **Component Separation**:
   ```plaintext
   Web Tier: Handles HTTP/HTTPS only
   App Tier: Business logic execution
   DB Tier: Data persistence
### Justification for Scaling

#### **Component vs. Scaling Benefit**

| Component             | Scaling Benefit                          |
|-----------------------|-------------------------------------------|
| Load Balancer Cluster | Eliminates LB SPOF                        |
| Separate Web Tier     | Optimized static asset delivery           |
| Dedicated App Tier    | Better CPU utilization for computations   |
| Isolated DB Tier      | Dedicated I/O resources for queries       |

---

### Key Characteristics

#### **Horizontal Scaling**
- Add more web/app servers as needed
- Read replicas for database scaling

#### **Failover Mechanisms**
- Keepalived for LB redundancy
- Orchestrator for MySQL failover

#### **Network Optimization**
```plaintext
User → LB → Web → App → DB
Each hop can scale independently
```
---

### Comparison to Previous Design

| Metric                  | Task 2 Design | Scaled Up Design |
|-------------------------|---------------|------------------|
| Availability            | 99.9%         | 99.99%           |
| Max QPS                 | ~10K          | ~100K            |
| Failure Domains         | 3             | 6+               |
| Maintenance Complexity  | Medium        | High             |

