#  TP Réseau 

ipconfig /all
Interface Wifi
1.  Description. . . . . . . . . . . . . . : Realtek RTL8852AE WiFi 6 802.11ax PCIe Adapter
2.  Adresse physique . . . . . . . . . . . : F8-89-D2-E7-0B-5F
3. Adresse IPv4. . . . . . . . . . . . . .: 10.33.16.169


Interface ethernet 
1.  Description. . . . . . . . . . . . . . : Realtek Gaming GbE Family Controller
2.   Adresse physique . . . . . . . . . . . : 50-81-40-84-AB-FC

Gateway
1. Passerelle par défaut. . . . . . . . . : 10.33.19.254

Passerelle mac (arp -a)
1. ` 10.33.19.254          00-c0-e7-e0-04-4e     dynamique`

informations sur une carte IP
1. Adresse physique: ‎F8-89-D2-E7-0B-5F
2. Adresse IPv4: 10.33.16.169
3. Passerelle par défaut IPv4: 10.33.19.254![](https://i.imgur.com/Unj2dc7.png)

Modification ip 
1. ![](https://i.imgur.com/0Geeam6.png)

En changeant d'adresse ip, c'est comme si tu changeait d'identité, et le reseau ne te reconnait plus 

## TP Duo

![](https://i.imgur.com/b35qPNS.png)

ipconfig 
```
1.   Adresse IPv4. . . . . . . . . . . . . .: 10.10.10.16
2.   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
```

Deux machine qui se joignent :Ping 10.10.10.15
```
Envoi d’une requête 'Ping'  10.10.10.15 avec 32 octets de données :
Réponse de 10.10.10.15 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.15 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.15 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.15 : octets=32 temps=1 ms TTL=128

Statistiques Ping pour 10.10.10.15:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 1ms, Maximum = 1ms, Moyenne = 1ms
```

Déterminer l'adresse MAC de votre correspondant
```
Interface : 10.10.10.16 --- 0x8
  Adresse Internet      Adresse physique      Type
  10.10.10.15           50-eb-f6-e4-41-70     dynamique
```

Tester l'accès internet :(ping 1.1.1.1)
```
Envoi d’une requête 'Ping'  1.1.1.1 avec 32 octets de données :
Réponse de 1.1.1.1 : octets=32 temps=20 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=20 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=22 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=20 ms TTL=55

Statistiques Ping pour 1.1.1.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 20ms, Maximum = 22ms, Moyenne = 20ms
```

 Prouver que la connexion Internet passe bien par l'autre PC
```
tracert 192.168.137.1

Tracing route to LAPTOP-DS0S1GKI [192.168.137.1]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  LAPTOP-DS0S1GKI [192.168.137.1]

Trace complete.
```

sur le PC serveur
```
C:\Users\Joel\netcat-1.11>nc.exe -l -p 8888
hu
ho
```
sur le PC client
```
C:\Users\lukas\netcat-win32-1.11\netcat-1.11>nc.exe 192.168.137.1 8888
hu
ho
```

Visualiser la connexion en cours
netstat -a 
```
Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    0.0.0.0:135            LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:445            LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:902            LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:912            LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:5040           LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:5357           LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:7680           LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:49664          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:49665          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:49666          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:49667          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:49668          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:49669          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:55931          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:57621          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    0.0.0.0:61379          LAPTOP-DS0S1GKI:0      LISTENING
  TCP    10.33.16.169:139       LAPTOP-DS0S1GKI:0      LISTENING
  TCP    10.33.16.169:49451     24.105.29.76:https     ESTABLISHED
  TCP    10.33.16.169:49478     37.244.28.103:https    CLOSE_WAIT
  TCP    10.33.16.169:49485     51.104.167.255:https   TIME_WAIT
  TCP    10.33.16.169:49495     162.159.135.232:https  ESTABLISHED
  TCP    10.33.16.169:49508     a23-72-17-56:http      TIME_WAIT
  TCP    10.33.16.169:49509     a95-100-252-27:http    TIME_WAIT
  TCP    10.33.16.169:49530     a865a9e11bc2c0d65:https  ESTABLISHED
  TCP    10.33.16.169:49535     10.10.10.127:ms-do     SYN_SENT
  TCP    10.33.16.169:49542     10.33.19.8:ms-do       SYN_SENT
  TCP    10.33.16.169:49544     104.21.92.95:https     ESTABLISHED
  TCP    10.33.16.169:54338     ws-in-f188:5228        ESTABLISHED
  TCP    10.33.16.169:54344     20.90.152.133:https    ESTABLISHED
  TCP    10.33.16.169:57704     a865a9e11bc2c0d65:https  ESTABLISHED
  TCP    10.33.16.169:61377     37.244.54.10:1119      ESTABLISHED
  TCP    10.33.16.169:61380     124:4070               ESTABLISHED
  TCP    10.33.16.169:61383     47:https               ESTABLISHED
  TCP    10.33.16.169:61432     20.199.120.151:https   ESTABLISHED
  TCP    10.33.16.169:61462     40:https               ESTABLISHED
  TCP    10.33.16.169:65166     162.159.134.234:https  ESTABLISHED
  TCP    10.33.16.169:65354     ec2-3-218-125-188:https  ESTABLISHED
  TCP    10.33.16.169:65356     ec2-3-218-125-188:https  ESTABLISHED
  TCP    10.33.16.169:65461     172.65.251.78:https    ESTABLISHED
  TCP    10.33.16.169:65466     172.65.251.78:https    ESTABLISHED
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49488  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49489  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49490  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49491  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49492  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49493  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49494  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49496  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49497  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49499  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49500  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49502  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49503  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49504  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49505  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49506  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49507  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49510  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49511  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49512  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49513  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49514  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49516  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49517  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49518  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49519  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49520  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49521  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49523  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49524  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49525  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49527  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49528  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49529  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49531  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49532  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49533  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49534  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49536  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49539  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49540  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49541  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49543  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49545  CLOSING
  TCP    127.0.0.1:6463         LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:6463         LAPTOP-DS0S1GKI:57179  ESTABLISHED
  TCP    127.0.0.1:9010         LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:9010         LAPTOP-DS0S1GKI:61208  ESTABLISHED
  TCP    127.0.0.1:9010         LAPTOP-DS0S1GKI:61211  ESTABLISHED
  TCP    127.0.0.1:9080         LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:9100         LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:9100         LAPTOP-DS0S1GKI:61210  ESTABLISHED
  TCP    127.0.0.1:9180         LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:22885        LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:45654        LAPTOP-DS0S1GKI:0      LISTENING
  TCP    127.0.0.1:49506        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:49521        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:49533        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:49534        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:49541        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:49545        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:57179        LAPTOP-DS0S1GKI:6463   ESTABLISHED
  TCP    127.0.0.1:61208        LAPTOP-DS0S1GKI:9010   ESTABLISHED
  TCP    127.0.0.1:61210        LAPTOP-DS0S1GKI:9100   ESTABLISHED
  TCP    127.0.0.1:61211        LAPTOP-DS0S1GKI:9010   ESTABLISHED
  TCP    127.0.0.1:61399        LAPTOP-DS0S1GKI:61400  ESTABLISHED
  TCP    127.0.0.1:61400        LAPTOP-DS0S1GKI:61399  ESTABLISHED
  TCP    192.168.88.1:139       LAPTOP-DS0S1GKI:0      LISTENING
  TCP    192.168.137.1:139      LAPTOP-DS0S1GKI:0      LISTENING
  TCP    192.168.137.1:8888     Lukas:64873            ESTABLISHED
  TCP    192.168.137.1:54311    LAPTOP-DS0S1GKI:0      LISTENING
  TCP    192.168.174.1:139      LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:135               LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:445               LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:5357              LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:7680              LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:49664             LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:49665             LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:49666             LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:49667             LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:49668             LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:49669             LAPTOP-DS0S1GKI:0      LISTENING
  TCP    [::]:55931             LAPTOP-DS0S1GKI:0      LISTENING
  UDP    0.0.0.0:53             *:*
  UDP    0.0.0.0:500            *:*
  UDP    0.0.0.0:1900           *:*
  UDP    0.0.0.0:1900           *:*
  UDP    0.0.0.0:1900           *:*
  UDP    0.0.0.0:1900           *:*
  UDP    0.0.0.0:3702           *:*
  UDP    0.0.0.0:3702           *:*
  UDP    0.0.0.0:4500           *:*
  UDP    0.0.0.0:5050           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5353           *:*
  UDP    0.0.0.0:5355           *:*
  UDP    0.0.0.0:49763          *:*
  UDP    0.0.0.0:54122          *:*
  UDP    0.0.0.0:54544          *:*
  UDP    0.0.0.0:54546          *:*
  UDP    0.0.0.0:54700          *:*
  UDP    0.0.0.0:54701          *:*
  UDP    0.0.0.0:54702          *:*
  UDP    0.0.0.0:55492          *:*
  UDP    0.0.0.0:56149          *:*
  UDP    0.0.0.0:56230          *:*
  UDP    0.0.0.0:57621          *:*
  UDP    0.0.0.0:60444          *:*
  UDP    0.0.0.0:60857          *:*
  UDP    0.0.0.0:61456          *:*
  UDP    10.33.16.169:137       *:*
  UDP    10.33.16.169:138       *:*
  UDP    10.33.16.169:1900      *:*
  UDP    10.33.16.169:2177      *:*
  UDP    10.33.16.169:54542     *:*
  UDP    127.0.0.1:1900         *:*
  UDP    127.0.0.1:54543        *:*
  UDP    127.0.0.1:59687        *:*
  UDP    127.0.0.1:60445        *:*
  UDP    192.168.88.1:137       *:*
  UDP    192.168.88.1:138       *:*
  UDP    192.168.88.1:1900      *:*
  UDP    192.168.88.1:2177      *:*
  UDP    192.168.88.1:54540     *:*
  UDP    192.168.137.1:67       *:*
  UDP    192.168.137.1:68       *:*
  UDP    192.168.137.1:137      *:*
  UDP    192.168.137.1:138      *:*
  UDP    192.168.137.1:1900     *:*
  UDP    192.168.137.1:2177     *:*
  UDP    192.168.137.1:54539    *:*
  UDP    192.168.174.1:137      *:*
  UDP    192.168.174.1:138      *:*
  UDP    192.168.174.1:1900     *:*
  UDP    192.168.174.1:2177     *:*
  UDP    192.168.174.1:54541    *:*
  UDP    [::]:500               *:*
  UDP    [::]:547               *:*
  UDP    [::]:3702              *:*
  UDP    [::]:3702              *:*
  UDP    [::]:4500              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5353              *:*
  UDP    [::]:5355              *:*
  UDP    [::]:49764             *:*
  UDP    [::]:54545             *:*
  UDP    [::]:54547             *:*
  UDP    [::1]:1900             *:*
  UDP    [::1]:54538            *:*
  UDP    [fe80::3016:67b6:dbd3:1c70%8]:53  *:*
  UDP    [fe80::3016:67b6:dbd3:1c70%8]:1900  *:*
  UDP    [fe80::3016:67b6:dbd3:1c70%8]:2177  *:*
  UDP    [fe80::3016:67b6:dbd3:1c70%8]:54534  *:*
  UDP    [fe80::49d5:3161:f24d:bf1a%22]:1900  *:*
  UDP    [fe80::49d5:3161:f24d:bf1a%22]:2177  *:*
  UDP    [fe80::49d5:3161:f24d:bf1a%22]:54537  *:*
  UDP    [fe80::6494:e7fa:3f16:e6c4%17]:1900  *:*
  UDP    [fe80::6494:e7fa:3f16:e6c4%17]:2177  *:*
  UDP    [fe80::6494:e7fa:3f16:e6c4%17]:54536  *:*
  UDP    [fe80::e9ef:eeaa:a0d7:ac3d%21]:1900  *:*
  UDP    [fe80::e9ef:eeaa:a0d7:ac3d%21]:2177  *:*
  UDP    [fe80::e9ef:eeaa:a0d7:ac3d%21]:54535  *:*
```

 Pour aller un peu plus loin
```
Connexions actives

  Proto  Adresse locale         Adresse distante       État
  TCP    10.33.16.169:7680      10.33.19.112:62998     TIME_WAIT
  TCP    10.33.16.169:7680      10.33.19.112:63001     TIME_WAIT
  TCP    10.33.16.169:7680      10.33.19.112:63004     TIME_WAIT
  TCP    10.33.16.169:49590     25:https               CLOSE_WAIT
  TCP    10.33.16.169:49797     20.54.232.160:https    ESTABLISHED
  TCP    10.33.16.169:49802     ec2-3-218-125-188:https  ESTABLISHED
  TCP    10.33.16.169:49803     ec2-3-218-125-188:https  ESTABLISHED
  TCP    10.33.16.169:49861     52.155.161.106:https   ESTABLISHED
  TCP    10.33.16.169:49872     172.64.108.2:https     CLOSE_WAIT
  TCP    10.33.16.169:49882     a865a9e11bc2c0d65:https  ESTABLISHED
  TCP    10.33.16.169:54338     ws-in-f188:5228        ESTABLISHED
  TCP    10.33.16.169:54344     20.90.152.133:https    ESTABLISHED
  TCP    10.33.16.169:57704     a865a9e11bc2c0d65:https  ESTABLISHED
  TCP    10.33.16.169:61377     37.244.54.10:1119      ESTABLISHED
  TCP    10.33.16.169:61380     124:4070               ESTABLISHED
  TCP    10.33.16.169:61383     47:https               ESTABLISHED
  TCP    10.33.16.169:61432     20.199.120.151:https   ESTABLISHED
  TCP    10.33.16.169:61462     40:https               ESTABLISHED
  TCP    10.33.16.169:65166     162.159.134.234:https  ESTABLISHED
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49835  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49836  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49837  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49838  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49839  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49840  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49841  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49842  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49843  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49845  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49846  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49847  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49848  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49849  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49851  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49852  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49853  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49854  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49855  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49856  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49857  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49858  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49859  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49863  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49864  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49865  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49866  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49867  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49868  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49869  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49870  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49871  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49873  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49874  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49875  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49876  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49877  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49878  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49879  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49880  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49881  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49883  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49886  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49887  TIME_WAIT
  TCP    127.0.0.1:1120         LAPTOP-DS0S1GKI:49888  TIME_WAIT
  TCP    127.0.0.1:6463         LAPTOP-DS0S1GKI:57179  ESTABLISHED
  TCP    127.0.0.1:9010         LAPTOP-DS0S1GKI:61208  ESTABLISHED
  TCP    127.0.0.1:9010         LAPTOP-DS0S1GKI:61211  ESTABLISHED
  TCP    127.0.0.1:9100         LAPTOP-DS0S1GKI:61210  ESTABLISHED
  TCP    127.0.0.1:49836        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:49847        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:49854        LAPTOP-DS0S1GKI:1120   TIME_WAIT
  TCP    127.0.0.1:57179        LAPTOP-DS0S1GKI:6463   ESTABLISHED
  TCP    127.0.0.1:61208        LAPTOP-DS0S1GKI:9010   ESTABLISHED
  TCP    127.0.0.1:61210        LAPTOP-DS0S1GKI:9100   ESTABLISHED
  TCP    127.0.0.1:61211        LAPTOP-DS0S1GKI:9010   ESTABLISHED
  TCP    127.0.0.1:61399        LAPTOP-DS0S1GKI:61400  ESTABLISHED
  TCP    127.0.0.1:61400        LAPTOP-DS0S1GKI:61399  ESTABLISHED
```

Firewall
![](https://i.imgur.com/HoKsjVO.png)
