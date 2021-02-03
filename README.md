# Zabbix.org 原始文档

Zabbix.org改版后，让官方改的面目全非，首页上很多有用的信息都丢了，为此我从archive找回了，供需要的人。

Zabbix is an open source monitoring software - Zabbix on Wikipedia. This is Zabbix community platform.

## Templates	

[Searcher](https://monitoringartist.github.io/zabbix-searcher "zabbix-searcher")

[ommunity repos (templates/tools)](https://github.com/monitoringartist/zabbix-community-repos)

[Zabbix Share portal](https://share.zabbix.com)

[Zabbix official_templates](https://www.zabbix.com/cn/integrations?cat=official_templates)

### Tools

[Pootle for translating Zabbix](http://web.archive.org/web/20200920071019/https://www.zabbix.org/pootle/)

[Free test Zabbix instance](https://github.com/monitoringartist/dockbix-xxl#free-test-dockbix-instance)

Zabbix demo installation()

Official SVN repo over WebSVN()

[Zabbix CLI tools](Zabbix_CLI_Tools.md)

[Zabbix API libraries](libraries.md)

[Zapix API web tool](https://github.com/monitoringartist/zapix)

### Community

[Getting help](https://www.zabbix.com/cn/community)

[IRC #zabbix](https://webchat.freenode.net/?channels=#zabbix)

[Forum](https://www.zabbix.com/forum/)

[Community repos (templates/tools)](https://github.com/zabbix/zabbix-community-repos)

[link group](https://www.linkedin.com/company/2476879/) 

User mailing list

[zabbix announce](https://lists.sourceforge.net/lists/listinfo/zabbix-announce)
[zabbix users](https://lists.sourceforge.net/lists/listinfo/zabbix-users)


## How to

### Installation

[REQUIREMENTS](https://www.zabbix.com/documentation/current/manual/installation/requirements)

[Install on CentOS/RHEL](https://www.zabbix.com/documentation/current/manual/installation/install_from_packages/rhel_centos)

[Install on Debian/Ubuntu/Raspbian](https://www.zabbix.com/documentation/current/manual/installation/install_from_packages/debian_ubuntu)

[Install on openSUSE/SLES](https://www.zabbix.com/documentation/current/manual/installation/install_from_packages/suse)

[Zabbix on Raspberry Pi (OS Raspbian)](http://web.archive.org/web/20200806125157/https://zabbix.org/wiki/Zabbix_on_the_Raspberry_Pi_(OS_Raspbian))

[Install on From SOURCES](https://www.zabbix.com/documentation/current/manual/installation/install)

[Windows Agent Installation From MSI](https://www.zabbix.com/documentation/current/manual/installation/install_from_packages/win_msi)

[MAC OS  Agent Installation PKG](https://www.zabbix.com/documentation/current/manual/installation/install_from_packages/mac_pkg)

[Rebuild existing Zabbix RPM packages on RHEL, CentOS, ...](rebuild_rpms.md)

[Rebuild existing Zabbix DEB packages on Debian, Ubuntu, ...](http://web.archive.org/web/20200806125157/https://zabbix.org/wiki/Docs/howto/rebuild_debs)

[Zabbix on DB2](http://web.archive.org/web/20181103214227/http://www.zabbix.org/wiki/DB2_Installation_Cookbook)

[Install Zabbix with IBM DB2](http://web.archive.org/web/20181108122932/http://www.zabbix.org/wiki/Docs/howto/Install_Zabbix_with_IBM_DB2)

[Install on FreeNAS](http://web.archive.org/web/20181015193258/http://zabbix.org/wiki/Install_on_FreeNAS)

[Install on Synology](http://web.archive.org/web/20200814111945/https://www.zabbix.org/wiki/InstallOnSynology)

[Statically link the Zabbix agent](Zabbix_Agent_static_linking.md)

## HA

[High availability setup](http://web.archive.org/web/20181028005316/http://zabbix.org/wiki/Docs/howto/high_availability)

[High availability setup CentOS 6.x](http://web.archive.org/web/20200806125157/https://zabbix.org/wiki/Docs/howto/high_availability_on_Centos_6.x)

[HA for faster Frontend with Nginx and Google Pagespeed Module](http://web.archive.org/web/20180711070304/http://www.zabbix.org/wiki/Docs/howto/high_availability_Zabbix_Frontend)

[HA Using Puppet & puppet forge modules](http://web.archive.org/web/20200814112849/https://www.zabbix.org/wiki/Docs/howto/high_availability_Puppet_corosync_pacemaker)

## Database

### [Schema](https://assets.zabbix.com/files/org/Zabbix_db_schema-2.4.3-MySQL.pdf)

### MySQL

[MySQL partitioning (2.x.x)](http://web.archive.org/web/20201111205659/https://zabbix.org/wiki/Docs/howto/mysql_partition)

[Docs/howto/MySQL Table Partitioning (variant)](http://web.archive.org/web/20200806125157/https://zabbix.org/wiki/Docs/howto/MySQL_Table_Partitioning_(variant))

[MySQL partitioning with external management script](mysql_partitioning.md)

[Script for (configuration) backup](http://web.archive.org/web/20200814113732/https://www.zabbix.org/wiki/Docs/howto/database_backup_script)

[Zabbix: Partitioning MySQL / MariaDB database Tables in 5 min](https://bestmonitoringtools.com/zabbix-partitioning-tables-on-mysql-database/)

### PostgreSQL

Higher performant partitioning in PostgreSQL

PostgreSQL table partitioning by range

Zabbix2 PostgreSQL table partitioning

Zabbix2 PostgreSQL table autopartitioning

Script for (configuration) backup

### Misc

Keeping trunk database up to date

Upgrade Zabbix 1.8 to 2.0 and Migrate MySQL to PostgreSQL

Example duration of update from 1.8 to 2.0

Microsoft SQL Server monitoring with LLD

Implementing LDAP with SSL inside CentOS

## Integration

HP BSM connector

## SNMP

SNMP Traps in zabbix with SNMPv3

Start with SNMP traps in Zabbix

SNMP Builder

Configure Snmptraps on CentOS / RHEL 6.x with selinux

## JMX

Improved JMX Discovery

Configure JMX

## Windows

Agent deployment for Windows

How to set the FQDN as agent hostname on Windows

## Various

Add web monitoring by script

SSL Certificate external checks with Zabbix

Escaping timeouts with atd

Apache monitoring script

Configuring shared memory

Dockerized Zabbix

Wireshark dissector for Zabbix protocol

## Information

Official Zabbix Manuals

Introduction - Triggers and Actions and Hosts

Events

Monthly Bugsquash Days

Zabbix Summit 2019
Zabbix Summit 2018
Zabbix conference 2017
Zabbix conference 2016
Zabbix conference 2015
Zabbix conference 2014
Zabbix conference 2013
Zabbix conference 2012
Zabbix conference 2011

## Guidelines

Zabbix template guidelines

Bug reporting guidelines

Zabbix development guidelines

Zabbix coding guidelines

Zabbix syntax and naming guidelines

Zabbix documentation guidelines

## Development

General design

Zabbix protocols

Database schema documentation

Zabbix roadmap

Specifications

Translating Zabbix

Generating DB schema and data

Zabbix user interface usability

Developer documentation

SVN tags with revisions

Zabbix releases

Export changelog

Upstream Issues

Troubleshooting

Bulk SNMP requests device blacklist

Userparameters with PHP

Database Schemas

## Hacking

Action simulator project

Concept for acknowledging events via SMS

Maps and Charts with D3

Send comments to Logstash

Easier ad-hoc maintenance brain storming

Patches on Github

Get help and be part of the community

Need some help with Zabbix? Want to meet other Zabbix users? Read about the available options.

Get Zabbix

Official download page

Getting source and compiling from git

Get nightly builds and source from version control system (git)

Compile from a git checkout

Commercial tools

Zabbix Plugin for Confluence

Zabbix.org
Community code
Tasks
Zabbix
Community Training Program
Wiki


