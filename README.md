Clone the repo and run following commands

## Master
$ mv Dockerfile(master).txt Dockerfile

$ docker build -t wazuh-master .

$ docker run -d -p 55000:55000 -p 1514:1514/udp -p 1515:1515 -p 514:514/udp --name wazuh-server wazuh-master 


## agent
copy Dockerfile(agent) and ossec.conf files to agent machine and run following command 

Change the master IP in ossec.conf (line 9)

Note: make sure master is up and running and password in authd.pass is same in both Dockerfile

$ docker build -t wazuh-agent .

$ docker run -d -p 55000:55000 -p 1514:1514/udp -p 1515:1515 -p 514:514/udp -v /path-to-ossec.conf/ossec.conf:/var/ossec/etc/ossec.conf --name wazuh-server wazuh-master 

# https://foxutech.com
