# Day 4 – TLS & Nginx Load Balancing

This practical covers TLS inspection, HTTPS configuration using a self-signed certificate, and load balancing using Nginx with Docker containers.

---

## Task 1: Inspect TLS Certificate

Used `curl` and `openssl` to inspect the TLS certificate of a public HTTPS website.

**Commands:**


curl -vI https://example.com

echo | openssl s_client -connect example.com:443 | openssl x509 -noout -subject -issuer -dates


**Observation:**
TLS handshake details, certificate issuer, subject, and validity period were displayed.

---

## Task 2: Self-Signed HTTPS Setup

Generated a self-signed SSL certificate and configured Nginx to enable HTTPS for a local domain (`myapp.local`).

**Command:**


sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048
-keyout /etc/ssl/private/myapp.key
-out /etc/ssl/certs/myapp.crt
-subj "/CN=myapp.local"


**Observation:**
The browser shows a security warning because the certificate is self-signed.

---

## Task 3: Nginx Load Balancing with Docker

Two Docker containers were used as backend servers, and Nginx distributed traffic between them.

**Nginx Config:**


upstream backend_servers {
server 127.0.0.1:8081;
server 127.0.0.1:8082;
}

server {
listen 80;

location / {
    proxy_pass http://backend_servers;
}

}


**Verification:**


for i in {1..6}; do curl -s http://localhost
 | grep Hostname; done


**Result:**
Requests were distributed between the two containers, confirming load balancing.

---

## Tools Used
- Vagrant (Ubuntu VM)
- Docker
- Nginx
- OpenSSL
- Curl
