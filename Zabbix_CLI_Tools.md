# Zabbix CLI Tools

## Tools

### zabbixctl

Zabbixctl](https://github.com/kovetskiy/zabbixctl)  is tool that provides effective way for operating in Zabbix server using command line interface.

Features:

Searching, sorting and showing triggers statuses;
Acknowledge specified triggers;
Listing hosts latest data;
Search and operate on users groups.

### Zabbix Tool

[zabbix_tool](https://github.com/BrianGallew/zabbix_tool) is a Github repository containing three useful, maybe even essential, Zabbix CLI tools.

Both CLI tools support --help and --debug, while the Python module uses the standard logging module and supports both extensive logging as well as a "no send" mode.

zabbix_tool: this is the eponymous tool for manipulating your Zabbix installation. It's far from complete, yet I use it on a daily basis to get useful work done. While somewhat useful as-is, the real power can only be realized by using it to codify changes you want to make in Zabbix. Best of all, given what's already there you can usually accomplish this by adding one or two more functions (usually less than 10 lines each).

screen_creator (essential!): Allows you to create and re-size screens, adding items to your screens by hostgroup or hostname, with filtering. While you can create some useful screens in a single go, you generally get the best bang for the buck from a multiple execution method (see below for an example).

python_zabbix_assistant.py: Python module that can be used to send data to Zabbix trapper items.

### ZabCon

[Zabcon](https://github.com/red-tux/zabcon) is a tool written in Ruby which makes use of the Zabbix API wrapper also written in Ruby. The goal of Zabcon is to make it easier to maintain your Zabbix installation.

### Zabbix-Gnomes

The Zabbix Gnomes are a collection of simple and reusable python scripts that are meant as an interface from the Unix shell to the Zabbix API. They will allow you to manipulate and use Zabbix information in normal *nix shell scripts without bothering with API calls.

### Zabbix (agent) framework

This tool is used to maintain external zabbix checks in one place. There are lot of places where it is possible to download many external checks. But there is problem with installation, update and centralised management. This tool should do all of this in easy steps. In future it can be starting point to install and configure zabbix agent on systems with one step. Primary goal is not to make all plugins available here but to be able to use any plugin and decentralized development. If you are maintainer of some external check, it is enough to create zaf file in your repo and use zaf installer everywhere. Next to this, this tool can even communicate with Zabbix API with NO dependencies to high level languages. Shell, sed and awk only.

### Zabbix Cli

[Zabbix-cli](https://github.com/usit-gd/zabbix-cli) is a tool for managing some Zabbix administration task via the zabbix-API. Manual here: https://github.com/usit-gd/zabbix-cli/blob/master/docs/manual.rst

## Examples

### zabbix_tool

Get help (warning: very, very long)

    zabbix_tool --help 

Re-assign all of the hosts currently using proxy HKG01 to proxy HKG02.

    zabbix_tool assign_proxy_hosts HKG02 $(zabbix_tool get_hosts_assigned_to_proxy --filter=name HKG01)

List the hint count for all of your Cassandra nodes

    zabbix_tool --filter=lastvalue get_item "Cassandra_status-Hints" hg-type-cassandra

### screen_creator

Create a screen of Cassandra graphs - 3 columns of graphs for 8 servers.

```
for host in cass-{1..8}.example.com
 do
  ./screen_creator --hsize=3 --vsize=8 --add_all_group=hg-type-cassandra "Memory Usage"
  ./screen_creator --hsize=3 --vsize=8 --add_all_group=hg-type-cassandra "Disk /cassandra"
  ./screen_creator --hsize=3 --vsize=8 --add_all_group=hg-type-cassandra "Hints"
 done
```
### Zabbix (agent) framework

Simple installation of zaf on any system:

    curl -k https://raw.githubusercontent.com/limosek/zaf/1.2/install.sh | sh

Install plugin which will find and discover biggest directories on system

    zaf install fsx
 
Get all host ids in system via API

    zaf api get-host-ids
 
Export all hosts to backup directory in xml format, one xml per host

   zaf api export-hosts ./backup
