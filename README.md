# grafana
**Some notes on getting Grafana set up and working**  

I mostly use REHL  
- wget https://dl.grafana.com/oss/release/grafana-7.5.4-1.x86_64.rpm  
- sudo yum install grafana-7.5.4-1.x86_64.rpm  

**Turn it on**   
- systemctl daemon-reload  
- systemctl enable grafana-server
- systemctl start grafana-server  

**Other host cannot access this server because it is on port 3000**  
- sudo firewall-cmd --add-port=3000/tcp --permanent
- sudo firewall-cmd --reload
