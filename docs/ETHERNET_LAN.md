# Ethernet Portunu LAN Olarak Kullanma

Bu doküman, Milesight UG65’te Ethernet portunu WiFi ile aynı LAN’da kullanıp DHCP ve internet erişimi sağlama adımlarını özetler. **Root erişiminiz olmalıdır;** root erişim yöntemi bu depoda verilmez.

---

## Ne yapılır?

- **br-lan** adında bir bridge oluşturulur.
- **wlan0** (WiFi AP) ve **eth0** (Ethernet) bu bridge’e eklenir.
- Bridge’e **192.168.10.1/24** atanır.
- Mevcut DHCP sunucusu (dhcpd) **br-lan** üzerinde dinleyecek şekilde yeniden başlatılır.

Sonuç: Ethernet’e takılan cihazlar 192.168.10.x alır, ağ geçidi 192.168.10.1 olur ve cihazın SIM/WiFi çıkışı üzerinden internete çıkabilir.

---

## Ön koşullar

- Cihaza **root** ile SSH veya konsol erişimi. (Bu rehber root şifresi veya erişim yöntemi içermez.)
- Cihazda mevcut LAN/WiFi ağı 192.168.10.0/24 ve dhcpd kullanılıyor olmalı (varsayılan UG65 yapısı).

---

## Adımlar

1. **Bridge script’ini yükle**  
   `scripts/eth_lan_bridge` dosyasını cihaza `/etc/init.d/eth_lan_bridge` olarak kopyalayın, `chmod +x` yapın.

2. **Servisi etkinleştir**  
   `/etc/init.d/eth_lan_bridge enable`

3. **Başlat**  
   `/etc/init.d/eth_lan_bridge start`  
   (Ethernet’te kullandığınız IP değişebilir; erişim için WiFi veya yeni DHCP ile alacağınız 192.168.10.x kullanın.)

4. **Kalıcı DHCP için**  
   `scripts/rc_local_dhcpd_brlan.txt` içindeki satırları `/home/rc.local.custom` dosyasına ekleyin (açılışta dhcpd’nin br-lan’da dinlemesi için).

---

## Erişim

- Gateway adresi: **192.168.10.1**
- Ethernet veya WiFi’den bu adrese, kendi kullandığınız kullanıcı ve şifre ile SSH/HTTPS erişebilirsiniz. Bu depoda şifre paylaşılmaz.

---

## Rollback (bridge’i kaldırma)

Root ile:

```bash
/etc/init.d/eth_lan_bridge stop
/etc/init.d/eth_lan_bridge disable
ip addr add 192.168.1.8/24 dev eth0
ip link set eth0 up
```

Ardından dhcpd’yi gerekirse yeniden yapılandırıp başlatın. Tüm risk ve sorumluluk uygulayana aittir; [DISCLAIMER.md](../DISCLAIMER.md) geçerlidir.
