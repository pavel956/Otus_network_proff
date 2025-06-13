
# **BGP**
________________________________________________________
Настроить BGP между автономными системами
Организовать доступность между офисами Москва и С.-Петербург

1. Настроите eBGP между офисом Москва и двумя провайдерами - Киторн и Ламас.
2. Настроите eBGP между провайдерами Киторн и Ламас.
3. Настроите eBGP между Ламас и Триада.
4. Настроите eBGP между офисом С.-Петербург и провайдером Триада.
5. Организуете IP доступность между пограничным роутерами офисами Москва и С.-Петербург.
6. План работы и изменения зафиксированы в документации.


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="shem.png" alt="image" width="60%" height="auto">
 
1. начальные настройки BGP на примере R14 В сторону Киторн
<pre><code>
router bgp 1001
  neighbor 172.16.5.2 remote-as 101
</code></pre>

Настраиваем  BGP на R22
<pre><code>router bgp 101
 neighbor 172.16.5.1 remote-as 1001
 neighbor 172.16.5.9 remote-as 301
 neighbor 172.16.5.17 remote-as 520</code></pre>

проверяем таблицу BGP после настройки на всех маршрутизаторах
<img src="R14_ip_bgp_1.png" alt="image" width="60%" height="auto">

<img src="R18_sh_ip_sum.png" alt="image" width="60%" height="auto">