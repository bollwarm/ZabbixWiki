## This HowTO describes how to compile the Zabbix agent with statically linked dependencies

Prerequisites

    Centos-7-x86_64 installation

zabbix source code from http://www.zabbix.com/download.php

Install dependencies

     yum -y install gcc make glibc-static libstdc++-static

Extract zabbix source

    tar xvf zabbix-2.4.6-tar.gz
    cd zabbix-2.4.6 

Compile the agent

    ./configure --enable-agent --enable-static && make 

Strip the binary to remove debugging symbols
 
    strip -s  ./src/zabbix_agent/zabbix_agentd

Now you have a statically linked Zabbix agent binary
