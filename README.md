# Description

Supervisor daemon and apps monitoring through Zabbix.

Template "Template App Supervisor" finds all supervisor apps, creates new items and triggers.

# Dependencies

perl, sudo, zabbix-agent, zabbix-sender.

libswitch-perl library.

Installation
============

In ten easy steps.

1. copy `supervisor_check.pl` to `/etc/zabbix/`
2. copy `zabbix_agentd.d/supervisor.conf` to `/etc/zabbix/zabbix_agentd.d/`
3. copy `sudoers.d/zabbix` (or its content) to `/etc/sudoers.d/`
4. `chown root:root /etc/sudoers.d/zabbix ; chmod 440 /etc/sudoers.d/zabbix`
5. `chmod 755 /etc/zabbix/supervisor_check.pl`
6. edit `supervisor_check.pl` and set yours `$ZabbixServer` and `$HostName` for zabbix_sender.
7. restart zabbix-agent daemon.
8. import `zbx_templates/Template App Supervisor check.xml` into your templates.
9. apply template "Template App Supervisor" host.
10. copy `cron.d/zabbix_supervisor_check` to `/etc/cron.d/` and reload crond.

Installation Ubuntu
-------------------

Should be able to copy and paste for easy installation.

```sh
sudo apt-get install libswitch-perl
git clone git@github.com:Lelik13a/Zabbix-Supervisor-Check.git
# or
# git clone https://github.com/Lelik13a/Zabbix-Supervisor-Check.git
cd Zabbix-Supervisor-Check
# vim /etc/zabbix/supervisor_check.pl # set yours $ZabbixServer and $HostName for zabbix_sender.
sudo cp supervisor_check.pl /etc/zabbix/
sudo cp zabbix_agentd.d/supervisor.conf /etc/zabbix/zabbix_agentd.conf.d/
sudo service zabbix-agent restart
sudo cp sudoers.d/zabbix /etc/sudoers.d/
sudo chown root:root /etc/sudoers.d/zabbix
sudo chmod 440 /etc/sudoers.d/zabbix
sudo chmod 755 /etc/zabbix/supervisor_check.pl
sudo cp cron.d/zabbix_supervisor_check /etc/cron.d/
sudo service cron reload
```

License
=======

...*???*...
