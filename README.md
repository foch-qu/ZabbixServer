# Zabbix Server

#### - Zabbix-Server IP: 192.168.0.236 
###### - Username: Admin
###### - Passwd:   zabbix
### How to Run Server 

Run  `/home/cidana/startZabbixServer.sh` to start zabbix server

Run  `/home/cidana/restartZabbixServer.sh` to RESTART ZABBIX SERVER

### Add Scripts in target machine(zabbix agent not zabbix server)
###### - First
* `vim /etc/zabbix/zabbix_agentd.conf` 
* `UnsafeUserParameters=1`
* `User=root`
  
###### - Secend
Add `docker_discovery.py` & `docker_monitor.py` & `docker_discovery.conf` in `/etc/zabbix/zabbix_agentd.d`

###### - Third
Install python modules  
`pip install simplejson`  
`pip install docker`

###### - Fourth
Restart zabbix agent  
`systemctl restart zabbix-agent`

###### - Fifth
On zabbix server test target machine's docker status
* `docker exec -it zabbix-server-mysql bash`
* `zabbix_get -s 192.168.0.75 -k "docker_status[jenkins mem_percent]"`  
    return: `42.0`

### e.g
* https://hacpai.com/article/1586573801031#1-3-%E5%AF%BC%E5%85%A5docker%E7%9B%91%E6%8E%A7%E6%A8%A1%E6%9D%BF