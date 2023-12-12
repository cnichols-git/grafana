# grafana
**Some notes on getting Grafana set up and working**  

I mostly use RHEL  
- wget https://dl.grafana.com/oss/release/grafana-7.5.4-1.x86_64.rpm  
- sudo yum install grafana-7.5.4-1.x86_64.rpm  

**Turn it on**   
- systemctl daemon-reload  
- systemctl enable grafana-server
- systemctl start grafana-server  

**Other host cannot access this server because it is on port 3000**  
- sudo firewall-cmd --add-port=3000/tcp --permanent
- sudo firewall-cmd --reload  

Now in a browser http://serverIP:3000  
default log in admin/admin  

**Let's do this in a container using docker compose, docker and connecting it to Prometheus as it's database**

<code>---
volumes:
  grafana-data:
    driver: local
services:
  grafana:
    image: grafana/grafana-oss:latest
    container_name: grafana
    ports:
      - "3000:3000"
    volumes:
      - grafana-data:/grafana-data/data
    restart: unless-stopped</code>
https://developer.couchbase.com/tutorial-node-exporter-setup
