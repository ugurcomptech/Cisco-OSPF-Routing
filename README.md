# Cisco OSPF (Open Shortest Path First) Routing


Önceki belgelerimizde, yalnızca iki yönlendirici (router) olduğunda statik yönlendirme kullanmıştık. Ancak büyük ve karmaşık ağlar için statik yönlendirme zorlu bir yönetim gerektirebilir. İşte bu nedenle OSPF, RIP, EIGRP gibi dinamik yönlendirme protokolleri büyük ağlarda önemli bir rol oynar. Dinamik yönlendirme protokolleri, bir ağdaki birden fazla yönlendirici arasında otomatik olarak en iyi yolun belirlenmesine yardımcı olur. Bu protokoller, ağ topolojisinin değişmesi durumunda otomatik olarak güncellenir, bu da büyük ve büyüme potansiyeli olan ağlar için çok önemlidir.

Şimdi yapılandırmaları  yapmaya başlayalım:

- **Ankara Network:**
  - **Ip Adres:** 192.168.10.10
  - **Ağ Maskesi:** 255.255.255.0
  - **Ağ Geçidi:** 192.168.10.1

- **İstanbul Network:**
  - **Ip Adres:** 192.168.10.10
  - **Ağ Maskesi:** 255.255.255.0
  - **Ağ Geçidi:** 192.168.10.1


- **İzmir Network:**
  - **Ip Adres:** 192.168.10.10
  - **Ağ Maskesi:** 255.255.255.0
  - **Ağ Geçidi:** 192.168.10.1



Şimdi Routerları yapılandıralım:

```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gigabitEthernet 0/0
Router(config-if)#ip address 10.1.1.1 255.0.0.0
Router(config-if)#
```











![image](https://github.com/ugurcomptech/Cisco-OSPF-Routing/assets/133202238/b850e1d8-8aad-4922-b224-3748e663dfaa)
