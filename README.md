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



Şimdi Routerların iç ve dış networkünü yapılandıralım:

## Ankara Router
```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gigabitEthernet 0/0
Router(config-if)#ip address 192.168.10.1 255.255.255.0
Router(config-if)#exit
Router(config)interface serial 0/1/0
Router(config-if)#ip address 10.1.1.1 255.0.0.0
```

## İstanbul Router 

```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gigabitEthernet 0/0
Router(config-if)#ip address 192.168.20.1 255.255.255.0
Router(config-if)#exit
Router(config)interface serial 0/1/0
Router(config-if)#ip address 10.1.1.2 255.0.0.0
Router(config-if)#exit
Router(config)interface serial 0/1/1
Router(config-if)#ip address 30.1.1.1 255.0.0.0
```

## İzmir Router
```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface gigabitEthernet 0/0
Router(config-if)#ip address 192.168.30.1 255.255.255.0
Router(config-if)#exit
Router(config)interface serial 0/1/1
Router(config-if)#ip address 30.1.1.2 255.0.0.0
```

![image](https://github.com/ugurcomptech/Cisco-OSPF-Routing/assets/133202238/873b6ff4-c54d-42cd-a622-8cedc31d28bb)


Şimdi OSPF yapılandırmalarını yapalım:


#OSPF

## Ankara Router
```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#router ospf  100
Router(config-router)#network 192.168.10.0 0.0.0.255 area 0 // iç networkü tanıtıyoruz
Router(config-router)#network 10.1.1.1 0.255.255.255 area 0 // İstanbulla iletşimde olan dış networkü tanıtıyoruz
Router(config-router)#
```

## İstanbul Router
```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#router ospf  100
Router(config-router)#network 192.168.20.0 0.0.0.255 area 0 // iç networkü tanıtıyoruz
Router(config-router)#network 10.1.1.2 0.255.255.255 area 0 // İstanbulla iletişimde olan dış networkü tanıtıyoruz
Router(config-router)#network 30.1.1.1 0.255.255.255 area 0 // İzmirle iletişimde olan dış networkü tanıtıyoruz
Router(config-router)#
```

## izmir Router
```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#router ospf  100
Router(config-router)#network 192.168.30.0 0.0.0.255 area 0 // iç networkü tanıtıyoruz
Router(config-router)#network 30.1.1.2 0.255.255.255 area 0 // İstanbulla iletşimde olan dış networkü tanıtıyoruz
Router(config-router)#
```


