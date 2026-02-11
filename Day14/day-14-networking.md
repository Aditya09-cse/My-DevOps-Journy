# Day 14 – Networking Fundamentals & Hands-on Checks

Today was all about understanding how networking actually works — not just theory, but real commands and real outputs.

Target used: google.com

---

## 🔹 Quick Concepts

### OSI vs TCP/IP (in simple words)

- OSI has 7 layers (Physical → Data Link → Transport → Netwrok → Session → Presentation → Application).
- TCP/IP has 4 layers (Link → Internet → Transport → Application).
- OSI is conceptual.
- TCP/IP is what actually runs the internet.

### Where things sit

- IP → Internet Layer
- TCP/UDP → Transport Layer
- HTTP/HTTPS → Application Layer
- DNS → Application Layer

Example:
`curl https://google.com`
= HTTP (Application)
over TCP (Transport)
over IP (Internet)

---

# 🔹 Hands-on Checks

## 1️⃣ Identity Check

Command:
hostname
hostname -I

Result:
Hostname: ip-172-31-22-214  
IP: 172.31.22.214

Observation:
The machine is running in a private subnet (172.31.x.x range).

---

## 2️⃣ Reachability Test

Command:
ping google.com

Result:
- 0% packet loss
- Avg latency ~7 ms

Observation:
Internet connectivity is healthy and stable.

---

## 3️⃣ Route Path

Command:
traceroute google.com

Result:
- Destination reached in 7 hops
- No timeouts
- Stable latency

Observation:
Routing path is clean. No abnormal delay between hops.

---

## 4️⃣ Listening Services

Command:
ss -tulpn

Observed:
- SSH → Port 22 (LISTEN)
- DNS Resolver → 127.0.0.53:53
- HTTP → Port 80

Observation:
SSH and HTTP services are actively listening.

---

## 5️⃣ DNS Resolution

Command:
dig google.com
nslookup google.com

Resolved IP:
142.251.x.x (Google IP)

Observation:
DNS resolution working correctly through local resolver (127.0.0.53).

---

## 6️⃣ HTTP Check

Command:
curl -I https://www.google.com

Result:
HTTP/2 200

Observation:
Application layer working correctly. Server responded successfully.

---

## 7️⃣ Connections Snapshot

Command:
netstat -an | head

Observed:
- LISTEN → 22 (SSH), 80 (HTTP)
- ESTABLISHED → Active SSH session
- TIME_WAIT → Closed HTTPS connection

Observation:
System has active inbound SSH and recent outbound HTTPS traffic.

---

# 🔹 Mini Task – Port Probe

Identified Port:
SSH → 22

Command:
nc -zv localhost 22

Result:
Connection succeeded.

Conclusion:
SSH service is reachable locally.

If it failed, next checks would be:
- systemctl status ssh
- ufw status
- ss -tulpn

---

# 🔹 Reflection

Fastest debugging combo:
- ping (network check)
- curl -I (application check)

If DNS fails:
Check Application layer → dig, resolv.conf, local resolver.

If HTTP 500 appears:
Likely server-side application issue → check logs and service status.

---

## 🚀 What I Learned

Networking troubleshooting is layered:

1. Check IP
2. Check reachability
3. Check DNS
4. Check ports
5. Check application response

Every command tells part of the story.
When combined, they give the full picture.

