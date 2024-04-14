-----Installation of WAZUH-----
----------------------------------------------------------------------------------------------------------------------

I had installed manually each comonent in of wazuh at Ubuntu 22.some_version   

sudo apt upgrade      

to install all the components of wazuh    

wazuh-dashboard      
wazuh-manager   
wazuh-indexer   
filebeat   

command to install all the above component    

sudo curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a        

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++   
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
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

after installing write the command   

sudo systemctl enable wazuh-manager   
sudo systemctl enable wazuh-dashboard   
sudo systemctl enable wazuh-indexer   
sudo systemctl enable filebeat   

sudo systemctl start wazuh-manager   
sudo systemctl start wazuh-dashboard   
sudo systemctl start wazuh-indexer   
sudo systemctl start filebeat   

----------------------------------------------------------------------------------------------------------------------   
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

----------------------------------------------------------------------------------------------------------------------  

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

----------------------------------------------------------------------------------------------------------------------  

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
             
----------------------------------------------------------------------------------------------------------------------  
 
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

----------------------------------------------------------------------------------------------------------------------   

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

----------------------------------------------------------------------------------------------------------------------  

open any browser and type the above url or the host ip address with the port no given above for example https://localhost:55000 or 192.168.0.12:55000   

wazuh dash boad will be open:   
![Screenshot from 2024-04-14 18-02-11](https://github.com/SuzilSK/Cyber-sec/assets/129137449/3bfb5134-7fbf-4670-884e-98f643a00b93)

type the password

![Screenshot from 2024-04-14 18-03-27](https://github.com/SuzilSK/Cyber-sec/assets/129137449/c015cc89-990b-48c6-aae5-de223557e183)

![Screenshot from 2024-04-14 18-03-36](https://github.com/SuzilSK/Cyber-sec/assets/129137449/82d3f9cd-fe79-45d1-a9a0-bf95240ade7b)

initially no agent will be there to analyse since we have configured one wazuh agent in any endpoint device then we can see the connected agent to the wazuh-server dashboard for now one host was connected to the wazuh sever where wazuh agent is installed

![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/93c11735-8466-4a1f-9466-578e0dd65d7d)

----------------------------------------------------------------------------------------------------------------------

----------wazuh-agent-installation-process-----------
----------------------------------------------------------------------------------------------------------------------

type the command with root priviledge sudo su or sudo -i   
command:1
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import && chmod 644 /usr/share/keyrings/wazuh.gpg     

command:2
The necassary installation packages were added to the sources.list file by typing the following command:     
echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list     

sudo apt upgrade    

The WAZUH Agent is deployed in the machine by typing the command     
WAZUH_MANAGER="192.168.1.13" apt-get install wazuh-agent    
Here, 192.168.1.13 is the IP address of the WAZUH Indexer, that was obtained in the previous step.

provide the wazuh server ip address in the WAZUH_MANAGER="0.0.0.0"     

sudo systemctl enable wazuh-agent    

sudo systemctl start wazuh-agent    

sudo systemctl status wazuh-agent     
o/p   
![Screenshot from 2024-04-14 18-25-04](https://github.com/SuzilSK/Cyber-sec/assets/129137449/e44f3639-ba0b-4825-8f62-7bcd1ad38717)      

Note we can also provide the ip address of the wazuh-server in the wazuh-agent installed configuration file which is in the directory  /var/ossec/etc/ossec.conf find    

<ossec_config>
  <client>
    <server>
      <address>10.11.132.128</address>
      <port>1514</port>
      <protocol>tcp</protocol>
    </server>
    <config-profile>ubuntu, ubuntu20, ubuntu20.04</config-profile>
    <notify_time>10</notify_time>
    <time-reconnect>60</time-reconnect>
    <auto_restart>yes</auto_restart>
    <crypto_method>aes</crypto_method>
  </client>
    
    
change the <address>10.11.132.128</address> to the wazuh-servers ip address    

----------------------------------------------------------------------------------------------------------------------
Note:   
  if in case snort or any ids or any other third party .sevice is running in your system and the sevice is detected by the wazuh it will incorporate them to .confg file make sure you comment all the third party .services to run wazuh agent on the system   

    <!--<localfile>   
      <log_format>snort</log_format>   
      <location>/var/log/snort/alert</location>   
    </localfile>-->   
  

  all the installation part of wazuh-server and wazuh-agent is done now lets look the working and analysis of wazuh in realtime
  
----------------------------------------------------------------------------------------------------------------------

-------------vulnerability-assessment-and-log-analysis-in-wazuh------------
----------------------------------------------------------------------------------------------------------------------
before analysis in wazuh server make sure all the settings for analysis and log monitoring is enabled in wazuh-server config file which is in the directory /var/ossec/etc/shared/default/agent.conf use root user sudo -i    

cd /var/ossec/etc/shared/default   
nano agent.conf    

in the server initially the will be not set for vulnerability scanning
![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/838b9e45-090f-4068-8c27-a379e4902035)

We need to edit with the below code       

<agent_config>

  <!-- Shared agent configuration here -->
  <wodle name="syscollector">
   <disabled>no</disabled>
   <interval>1h</interval>
   <os>yes</os>
   <packages>yes</packages>
   <hotfixes>yes</hotfixes>
</wodle>

</agent_config>
  

below image after editing with the above code   
![image](https://github.com/SuzilSK/Cyber-sec/assets/129137449/39b86e40-eabd-43db-8146-89b7271895ea)

We need to edit the /var/ossec/etc/ossec.conf to yes as shown in the below screenshot. refer the link https://documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/configuring-scans.html   

  <vulnerability-detector>   
    <enabled>yes</enabled>   
    <interval>5m</interval>   
    <min_full_scan_interval>6h</min_full_scan_interval>   
    <run_on_start>yes</run_on_start>   

    <!-- Ubuntu OS vulnerabilities -->   
    <provider name="canonical">   
      <enabled>yes</enabled>   
      <os>trusty</os>   
      <os>xenial</os>   
      <os>bionic</os>   
      <os>focal</os>   
      <os>jammy</os>   
      <update_interval>1h</update_interval>   
    </provider>   

    <!-- Debian OS vulnerabilities -->   
    <provider name="debian">   
      <enabled>yes</enabled>   
      <os>buster</os>  
      <os>bullseye</os>  
      <os>bookworm</os>  
      <update_interval>1h</update_interval>  
    </provider>  

    <!-- RedHat OS vulnerabilities -->    
    <provider name="redhat">   
      <enabled>yes</enabled>   
      <os>5</os>   
      <os>6</os>   
      <os>7</os>   
      <os>8</os>      
      <update_interval>1h</update_interval>   
    </provider>   

    <!-- Amazon Linux OS vulnerabilities -->   
    <provider name="alas">   
      <enabled>yes</enabled>  
      <os>amazon-linux</os>   
      <os>amazon-linux-2</os>   
      <os>amazon-linux-2022</os>   
      <os>amazon-linux-2023</os>   
      <update_interval>1h</update_interval>   
    </provider>   

    <!-- SUSE OS vulnerabilities -->   
    <provider name="suse">   
      <enabled>yes</enabled>   
      <os>11-server</os>   
      <os>11-desktop</os>   
      <os>12-server</os>   
      <os>12-desktop</os>   
      <os>15-server</os>   
      <os>15-desktop</os>   
      <update_interval>1h</update_interval>   
    </provider>   

    <!-- Arch OS vulnerabilities -->   
    <provider name="arch">   
      <enabled>yes</enabled>   
      <update_interval>1h</update_interval>   
    </provider>   

    <!-- Alma Linux OS vulnerabilities -->   
    <provider name="almalinux">   
      <enabled>yes</enabled>   
      <os>8</os>   
      <os>9</os>   
      <update_interval>1h</update_interval>   
    </provider>   

    <!-- Windows OS vulnerabilities -->   
    <provider name="msu">   
      <enabled>yes</enabled>   
      <update_interval>1h</update_interval>   
    </provider>   

    <!-- Aggregate vulnerabilities -->   
    <provider name="nvd">   
      <enabled>yes</enabled>   
      <update_interval>1h</update_interval>   
    </provider>   

  </vulnerability-detector>    

also edit according to the need of the your requirement in the wazuh .config file
after editing the file save it and restart wazuh-manager    

sudo systemctl restart wazuh-manager       

----------------------------------------------------------------------------------------------------------------------

after all the changes done open wazuh dashboad for analysis    

navigate to vulnerability under threat detection section

![Screenshot from 2024-04-14 17-30-36](https://github.com/SuzilSK/Cyber-sec/assets/129137449/23c882f2-8501-42eb-877e-251bcaf7fac8)

click critical vulnerability   

![Screenshot from 2024-04-14 18-41-00](https://github.com/SuzilSK/Cyber-sec/assets/129137449/297492b0-307c-4905-8a5d-7ba319daf5d6)

![Screenshot from 2024-04-14 18-41-28](https://github.com/SuzilSK/Cyber-sec/assets/129137449/2e7a828c-ef6f-4d54-b234-7cc074fdc78c)
  
![Screenshot from 2024-04-14 18-42-03](https://github.com/SuzilSK/Cyber-sec/assets/129137449/95ca6b29-449b-41ac-9260-cfaa347668c4)

Now navigate to security events   

![Screenshot from 2024-04-14 18-42-20](https://github.com/SuzilSK/Cyber-sec/assets/129137449/4e5523ba-d4f4-457f-8df2-1c64ed83e50c)

![Screenshot from 2024-04-14 18-42-25](https://github.com/SuzilSK/Cyber-sec/assets/129137449/7a3a6bea-8ab8-4f71-aa04-51cb3b907963)

navigate to mitire attack   

![Screenshot from 2024-04-14 18-42-56](https://github.com/SuzilSK/Cyber-sec/assets/129137449/948eb5f2-7eb8-442c-a1a4-3de349766fd9)



