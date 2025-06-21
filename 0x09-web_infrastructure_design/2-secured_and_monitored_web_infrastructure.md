# Secured & Monitored Web Infrastructure

![Secure Infrastructure Diagram](https://raw.githubusercontent.com/KelvinOnyango/alx-system_engineering-devops/main/0x09-web_infrastructure_design/2-secured_web_infra.png)

## Added Security Components

1. **Three Firewalls**:
   - **LB Firewall**: Filters traffic to load balancer
   - **Web Server Firewalls**: Restrict access to web tier
   - **Purpose**: Prevent unauthorized access and DDoS attacks

2. **SSL Certificate**:
   - **Implementation**: LetsEncrypt on HAProxy
   - **HTTPS Purpose**: Encrypts traffic to prevent eavesdropping and MITM attacks

3. **Monitoring Clients**:
   - **Agents**: SumoLogic collectors on all servers
   - **Data Collection**: System metrics, access logs, performance stats

## Key Explanations

### Monitoring System
```plaintext
Data Flow:
Web Servers → Monitoring Agents → SumoLogic Cloud → Alerts/Dashboards
jn
```
### Monitoring QPS

- Configure agents to track HTTP requests/sec
- Create dashboard showing requests over time
- Set alerts when QPS exceeds thresholds

---

### Current Infrastructure Issues

#### **SSL Termination at Load Balancer**
- Traffic between LB and web servers is unencrypted
- Potential vulnerability in internal network

#### **Single Write MySQL**
- Primary failure stops all write operations
- Replica promotion requires manual intervention

#### **Identical Components**
- Resource contention (e.g., DB queries slowing web apps)
- Single failure domain (compromise one server → risk all services)
- Difficult to scale components independently
