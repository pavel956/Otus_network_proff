# **IPSec over DmVPN**

Цель:
Настроить GRE поверх IPSec между офисами Москва и С.-Петербург
Настроить DMVPN поверх IPSec между офисами Москва и Чокурдах, Лабытнанги

+ Настроите GRE поверх IPSec между офисами Москва и С.-Петербург.
* Настроите DMVPN поверх IPSec между Москва и Чокурдах, Лабытнанги.

________________________________________________________

1.




 ```
crypto isakmp policy 10
 encr 3des
 hash sha256
 authentication pre-share
 group 2
crypto isakmp key BUBLIL address 172.16.5.22
!
!
crypto ipsec transform-set TO_R18 esp-3des esp-sha256-hmac
 mode transport
!
crypto ipsec profile PROFILE
 set transform-set TO_R18

interface Tunnel0
 ip address 192.168.170.1 255.255.255.0
 ip mtu 1400
 ip tcp adjust-mss 1360
 keepalive 10 5
 tunnel source 172.16.5.5
 tunnel mode ipsec ipv4
 tunnel destination 172.16.5.22
 tunnel protection ipsec profile PROFILE
 ```

 ``` 
crypto ikev2 proposal PHASE1
 encryption aes-cbc-128
 integrity sha256
 group 2
!
crypto ikev2 policy 10
 proposal PHASE1
!
!
crypto ikev2 profile PROFILE1
 match identity remote address 172.16.5.22 255.255.255.252
 authentication remote pre-share key PASSWORD
 authentication local pre-share key PASSWORD
!
!
!
crypto ipsec transform-set IPSEC_TS esp-aes esp-md5-hmac
 mode tunnel
!
crypto ipsec profile TO_R18
 set transform-set IPSEC_TS
 set ikev2-profile PROFILE1
 ```
<img src="image.png" alt="image" width="60%" height="auto">
<img src="image-1.png" alt="image" width="60%" height="auto">
<img src="image-2.png" alt="image" width="60%" height="auto">
<img src="image-3.png" alt="image" width="60%" height="auto">
<img src="image-4.png" alt="image" width="60%" height="auto">
<img src="image-5.png" alt="image" width="60%" height="auto">
<img src="image-6.png" alt="image" width="60%" height="auto">




2.



[конфигурация узлов](conf/)

[1](1/)