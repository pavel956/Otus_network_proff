# DHCP
## DHCPv6

Схема лабараторного стенда в EVE-NG

![](схема6.png)

Таблица адресации.
![](adres.png)


- делаем стартовые настройки на всех узлах
- настраиваем IPv6 на R1 и маршрут по умолчанию в сторону R2

<pre><code>
interface GigabitEthernet0/0
  ipv6 address FE80::1 link-local
  ipv6 address 2001:DB8:ACAD:2::1/64
!
interface GigabitEthernet0/1
  ipv6 address FE80::1 link-local
 ipv6 address 2001:DB8:ACAD:1::1/64
ipv6 route ::/0 2001:DB8:ACAD:2::2
</code></pre>
- аналогично настраиваем R2 и маршрут в сторону R1

### SLAAC
- Включаем на R1 и R2 присоединение ко всей группе
многоадресной рассылки IPv6 и начало отправки
сообщений RA, содержащих сведения о
конфигурации адресов, хостам с помощью SLAAC.
<pre><code>
ipv6 unicast-routing
</code></pre>
