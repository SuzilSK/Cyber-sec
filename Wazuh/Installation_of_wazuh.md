-----Installation of WAZUH-----

I had installed manually each comonent in of wazuh at Ubuntu 22.some_version

sudo apt upgrade   

to install all the components of wazuh
wazuh-dashboard   
wazuh-manager   
wazuh-indexer   
filebeat   

command to install all the above component

sudo curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a    

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
o/p
suzil@suzil-LENOVO-V14:~$ sudo curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

04/04/2024 20:44:11 INFO: Starting Wazuh installation assistant. Wazuh version: 4.7.3
04/04/2024 20:44:11 INFO: Verbose logging redirected to /var/log/wazuh-install.log
04/04/2024 20:44:20 INFO: Wazuh web interface port will be 443.
04/04/2024 20:44:43 INFO: Wazuh repository added.
04/04/2024 20:44:43 INFO: --- Configuration files ---
04/04/2024 20:44:43 INFO: Generating configuration files.
04/04/2024 20:44:45 INFO: Created wazuh-install-files.tar. It contains the Wazuh cluster key, certificates, and passwords necessary for installation.
04/04/2024 20:44:45 INFO: --- Wazuh indexer ---
04/04/2024 20:44:45 INFO: Starting Wazuh indexer installation.
04/04/2024 20:45:26 INFO: Wazuh indexer installation finished.
04/04/2024 20:45:26 INFO: Wazuh indexer post-install configuration finished.
04/04/2024 20:45:26 INFO: Starting service wazuh-indexer.
04/04/2024 20:45:39 INFO: wazuh-indexer service started.
04/04/2024 20:45:39 INFO: Initializing Wazuh indexer cluster security settings.
04/04/2024 20:45:50 INFO: Wazuh indexer cluster initialized.
04/04/2024 20:45:50 INFO: --- Wazuh server ---
04/04/2024 20:45:50 INFO: Starting the Wazuh manager installation.
04/04/2024 20:46:18 INFO: Wazuh manager installation finished.
04/04/2024 20:46:18 INFO: Starting service wazuh-manager.
04/04/2024 20:46:35 INFO: wazuh-manager service started.
04/04/2024 20:46:35 INFO: Starting Filebeat installation.
04/04/2024 20:47:12 INFO: Filebeat installation finished.
04/04/2024 20:47:21 INFO: Filebeat post-install configuration finished.
04/04/2024 20:47:21 INFO: Starting service filebeat.
04/04/2024 20:47:22 INFO: filebeat service started.
04/04/2024 20:47:22 INFO: --- Wazuh dashboard ---
04/04/2024 20:47:22 INFO: Starting Wazuh dashboard installation.
04/04/2024 20:49:41 INFO: Wazuh dashboard installation finished.
04/04/2024 20:49:41 INFO: Wazuh dashboard post-install configuration finished.
04/04/2024 20:49:41 INFO: Starting service wazuh-dashboard.
04/04/2024 20:49:42 INFO: wazuh-dashboard service started.
04/04/2024 20:50:03 INFO: Initializing Wazuh dashboard web application.
04/04/2024 20:50:04 INFO: Wazuh dashboard web application initialized.
04/04/2024 20:50:04 INFO: --- Summary ---
04/04/2024 20:50:04 INFO: You can access the web interface https://<wazuh-dashboard-ip>:443
    User: admin
    Password: your_password_will_be_there
04/04/2024 20:50:04 INFO: Installation finished.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

after installing write the command 

sudo systemctl enable wazuh-manager
sudo systemctl enable wazuh-dashboard
sudo systemctl enable wazuh-indexer
sudo systemctl enable filebeat

sudo systemctl start wazuh-manager
sudo systemctl start wazuh-dashboard
sudo systemctl start wazuh-indexer
sudo systemctl start filebeat
--------------------------------------------------------------------------------------------------------------------------------------
sudo systemctl status wazuh-manager
o/p
suzil@suzil-LENOVO-V14:~$ sudo systemctl status wazuh-manager
● wazuh-manager.service - Wazuh manager
     Loaded: loaded (/lib/systemd/system/wazuh-manager.service; enabled; vendor>
     Active: active (running) since Sun 2024-04-14 16:31:09 IST; 58min ago
    Process: 1228 ExecStart=/usr/bin/env /var/ossec/bin/wazuh-control start (co>
      Tasks: 139 (limit: 9180)
     Memory: 1.5G
        CPU: 10min 49.153s
     CGroup: /system.slice/wazuh-manager.service
             ├─1729 /var/ossec/framework/python/bin/python3 /var/ossec/api/scri>
             ├─1741 /var/ossec/framework/python/bin/python3 /var/ossec/api/scri>
             ├─1744 /var/ossec/framework/python/bin/python3 /var/ossec/api/scri>
             ├─1754 /var/ossec/framework/python/bin/python3 /var/ossec/api/scri>
             ├─1858 /var/ossec/bin/wazuh-authd
             ├─1903 /var/ossec/bin/wazuh-db
             ├─1980 /var/ossec/bin/wazuh-execd
             ├─2242 /var/ossec/bin/wazuh-analysisd
             ├─2397 /var/ossec/bin/wazuh-syscheckd
             ├─2523 /var/ossec/bin/wazuh-remoted
             ├─2608 /var/ossec/bin/wazuh-logcollector
             ├─2699 /var/ossec/bin/wazuh-monitord
             └─2728 /var/ossec/bin/wazuh-modulesd

Apr 14 16:31:01 suzil-LENOVO-V14 env[1228]: Started wazuh-execd...
---------------------------------------------------------------------------------------------------------------------------------------

sudo systemctl status wazuh-dashboard

o/p
suzil@suzil-LENOVO-V14:~$ sudo systemctl status wazuh-dashboard
● wazuh-dashboard.service - wazuh-dashboard
     Loaded: loaded (/etc/systemd/system/wazuh-dashboard.service; enabled; vend>
     Active: active (running) since Sun 2024-04-14 16:30:46 IST; 58min ago
   Main PID: 681 (node)
      Tasks: 11 (limit: 9180)
     Memory: 163.1M
        CPU: 9.610s
     CGroup: /system.slice/wazuh-dashboard.service
             └─681 /usr/share/wazuh-dashboard/node/bin/node --no-warnings --max>

Apr 14 16:31:07 suzil-LENOVO-V14 opensearch-dashboards[681]: {"type":"log","@ti>
Apr 14 16:31:09 suzil-LENOVO-V14 opensearch-dashboards[681]: {"type":"log","@ti>
Apr 14 16:31:12 suzil-LENOVO-V14 opensearch-dashboards[681]: {"type":"log","@ti>
Apr 14 16:31:14 suzil-LENOVO-V14 opensearch-dashboards[681]: {"type":"log","@ti>
Apr 14 16:31:18 suzil-LENOVO-V14 opensearch-dashboards[681]: {"type":"log","@ti>
Apr 14 16:31:18 suzil-LENOVO-V14 opensearch-dashboards[681]: {"type":"log","@ti>
Apr 14 16:31:18 suzil-LENOVO-V14 opensearch-dashboards[681]: {"type":"log","@ti>
---------------------------------------------------------------------------------------------------------------------------------------

sudo systemctl status wazuh-indexer

o/p
suzil@suzil-LENOVO-V14:~$ sudo systemctl status wazuh-indexer
● wazuh-indexer.service - Wazuh-indexer
     Loaded: loaded (/lib/systemd/system/wazuh-indexer.service; enabled; vendor>
     Active: active (running) since Sun 2024-04-14 16:31:15 IST; 57min ago
       Docs: https://documentation.wazuh.com
   Main PID: 1225 (java)
      Tasks: 91 (limit: 9180)
     Memory: 2.7G
        CPU: 1min 32.019s
     CGroup: /system.slice/wazuh-indexer.service
             └─1225 /usr/share/wazuh-indexer/jdk/bin/java -Xshare:auto -Dopense>
----------------------------------------------------------------------------------------------------------------------------------------

sudo systemctl status filebeat

o/p
suzil@suzil-LENOVO-V14:~$ sudo systemctl status filebeat
● filebeat.service - Filebeat sends log files to Logstash or directly to Elasti>
     Loaded: loaded (/lib/systemd/system/filebeat.service; enabled; vendor pres>
     Active: active (running) since Sun 2024-04-14 16:30:52 IST; 58min ago
       Docs: https://www.elastic.co/products/beats/filebeat
   Main PID: 1221 (filebeat)
      Tasks: 10 (limit: 9180)
     Memory: 24.6M
        CPU: 709ms
     CGroup: /system.slice/filebeat.service
             └─1221 /usr/share/filebeat/bin/filebeat --environment systemd -c />

Apr 14 16:30:52 suzil-LENOVO-V14 systemd[1]: Started Filebeat sends log files t>
---------------------------------------------------------------------------------------------------------------------------------------

then open the directory and view the wazuh.yml file and check for hosts:

sudo cat /usr/share/wazuh-dashboard/data/wazuh/config/wazuh.yml

o/p
hosts:
  - default:
      url: https://localhost
      port: 55000
      username: wazuh-wui
      password: "N.LtNTpyDpI1yXMVpR1H7SH6jfDg**rC"
      run_as: false
where we can access the wazhu_dashboad

the above given url, port no is used to host the wazuh
---------------------------------------------------------------------------------------------------------------------------------------

open any browser and type the above url or the host ip address with the port no given above for example https://localhost:55000 or 192.168.0.12:55000

wazuh dash boad will be open:

