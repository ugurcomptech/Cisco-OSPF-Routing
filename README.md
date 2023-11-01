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
