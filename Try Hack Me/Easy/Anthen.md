```
┌──(xnv㉿kali)-[~]
└─$ nmap -A 10.10.127.200

80/tcp   open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
| http-robots.txt: 4 disallowed entries 
|_/bin/ /config/ /umbraco/ /umbraco_client/
|_http-title: Anthem.com - Welcome to our blog
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: WIN-LU09299160F
|   NetBIOS_Domain_Name: WIN-LU09299160F
|   NetBIOS_Computer_Name: WIN-LU09299160F
|   DNS_Domain_Name: WIN-LU09299160F
|   DNS_Computer_Name: WIN-LU09299160F
|   Product_Version: 10.0.17763
|_  System_Time: 2021-05-29T03:45:51+00:00
| ssl-cert: Subject: commonName=WIN-LU09299160F
| Not valid before: 2021-01-02T15:57:43
|_Not valid after:  2021-07-04T15:57:43
|_ssl-date: 2021-05-29T03:46:08+00:00; +1s from scanner time.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

```
┌──(xnv㉿kali)-[~]
└─$ wfuzz -c -w /usr/share/dirb/wordlists/common.txt --hc 404,403 -u http://10.10.127.200/FUZZ

search                  [Status: 200, Size: 3418, Words: 520, Lines: 93]
blog                    [Status: 200, Size: 5394, Words: 1311, Lines: 127]
sitemap                 [Status: 200, Size: 1041, Words: 94, Lines: 30]
rss                     [Status: 200, Size: 1851, Words: 240, Lines: 30]
archive                 [Status: 301, Size: 123, Words: 6, Lines: 4]
categories              [Status: 200, Size: 3491, Words: 561, Lines: 104]
authors                 [Status: 200, Size: 4070, Words: 769, Lines: 112]
tags                    [Status: 200, Size: 3544, Words: 579, Lines: 105]
install                 [Status: 302, Size: 126, Words: 6, Lines: 4]
robots.txt              [Status: 200, Size: 192, Words: 17, Lines: 11]
1073                    [Status: 200, Size: 5349, Words: 1311, Lines: 127]
1074                    [Status: 301, Size: 123, Words: 6, Lines: 4]
1078                    [Status: 200, Size: 6200, Words: 1232, Lines: 149]
```

```
┌──(xnv㉿kali)-[~]
└─$ wfuzz -c -w /usr/share/dirb/wordlists/common.txt --hc 404,403 -u http://10.10.127.200/umbraco/FUZZ
====================================================================
ID           Response   Lines    Word       Chars       Payload
=====================================================================
000000001:   200        95 L     189 W      4078 Ch     "http://10.10.127.200/umbraco/"
000000259:   301        1 L      10 W       160 Ch      "actions"
000000447:   200        0 L      1 W        3276 Ch     "application"
000000499:   301        1 L      10 W       159 Ch      "assets"
000000994:   301        1 L      10 W       159 Ch      "config"
000001041:   301        1 L      10 W       161 Ch      "controls"
000001087:   301        1 L      10 W       159 Ch      "create"
000001156:   301        1 L      10 W       162 Ch      "dashboard"
000001207:   200        95 L     189 W      4078 Ch     "default"
000001247:   301        1 L      10 W       162 Ch      "developer"
000001263:   301        1 L      10 W       160 Ch      "dialogs"
000002058:   301        1 L      10 W       160 Ch      "install"
000002179:   301        1 L      10 W       155 Ch      "js"
000002274:   301        1 L      10 W       156 Ch      "lib"
000002455:   301        1 L      10 W       164 Ch      "masterpages"
000002489:   301        1 L      10 W       160 Ch      "Members"
000002488:   301        1 L      10 W       160 Ch      "members"
000003003:   301        1 L      10 W       160 Ch      "plugins"
000003092:   302        3 L      8 W        125 Ch      "preview"
000003526:   301        1 L      10 W       159 Ch      "Search"
000003525:   301        1 L      10 W       159 Ch      "search"
000003609:   301        1 L      10 W       161 Ch      "settings"
000004309:   301        1 L      10 W       158 Ch      "views"
000004415:   301        1 L      10 W       164 Ch      "webservices"
```

```
http://10.10.127.200/robots.txt

*************
```

```
http://10.10.206.67/umbraco/#/login

**@anthem.com / *************
```

```
http://10.10.85.150/archive/we-are-hiring/ 
TAG 1
THM{*************}
```

```
view-source:http://10.10.85.150/
TAG 2
THM{*************}
```

```
http://10.10.85.150/authors
TAG3
THM{*********}
```

```
view-source:http://10.10.102.212/archive/a-cheers-to-our-it-department/
TAG4
***{************}
```

```
http://10.10.241.70/umbraco/#/
**@anthem.com / ******************
```

```
┌──(luf3㉿kali)-[~]
└─$ rdesktop 10.10.245.117  
sg / ******************
```

```
User.txt  que está no desktop
THM{*********}
```

```
Pasta backup está ocupa na pasta C:/

Colocando o usuario nas permissões do arquivo oculto 
```

```
Senha oculta no arquivo
*************
```

```
Loga com o usuario 
administrator / *************
```

```
Arquivo de root no desktop


