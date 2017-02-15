Sample outbound-ssh server using pyez
-------------------------------------

This code is a sample outbound-ssh server for managing Juniper's SRX devices.
It works by passing accepted socket into the pyez Device class and eventually into the the ncclient ssh.py (wrapper for paramiko).


requirements
============
- valjeanchan/ncclient 
- valjeanchan/py-junos-eznc

instruction
===========

1. modify the username and the password on the script
2. paste the following JUNOS config into the srx box
~~~
set system services outbound-ssh client server1 device-id client1
set system services outbound-ssh client server1 keep-alive retry 10
set system services outbound-ssh client server1 keep-alive timeout 3
set system services outbound-ssh client server1 reconnect-strategy in-order
set system services outbound-ssh client server1 services netconf
set system services outbound-ssh client server1 <server1_ip> port 2200
set system services outbound-ssh client server1 <server1_ip> retry 10
set system services outbound-ssh client server1 <server1_ip> timeout 3
~~~
3. run the script 'python outbound-ssh-pyez.py'
4. logs will be output both on-screen and into file debug.log
