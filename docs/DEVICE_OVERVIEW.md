# Milesight UG65 – Cihaz Yapısına Genel Bakış

Bu doküman, Milesight UG65 (OpenWrt/LEDE tabanlı LoRaWAN gateway) cihazının dosya/klasör yapısı ve güvenlikle ilgili **genel** bilgileri özetler. Şifre, hash veya root erişim yöntemi içermez.

---

## Sistem özeti

| Özellik | Değer |
|--------|--------|
| İşletim Sistemi | Milesight LoRaWAN Gateway (LEDE 17.01-SNAPSHOT) |
| Çekirdek | Linux 4.14.x, aarch64 (ARMv8) |
| /var | /tmp ile symlink (RAM) |

---

## Önemli dizinler

- **/etc/config** – UCI: firewall, dropbear, dhcp, nginx, system, uhttpd, wireless, loraserver, mosquitto vb.
- **/etc/nginx** – Web proxy yapılandırması
- **/etc/init.d** – Servis scriptleri (70+)
- **/etc/dhcp3** – ISC dhcpd yapılandırması
- **/www** – Web arayüzü (HTML, JS, cgi-bin)
- **/overlay** – Kalıcı değişiklikler
- **/lora-server** – LoRa veritabanı ve ilgili veriler
- **/etc/loraserver**, **lora-app-server**, **lora-gateway-bridge**, **lora-pkt-fwd** – LoRa yığını
- **/etc/basicstation**, **chirpstack-gateway-bridge** – LoRa gateway konfigürasyonları

---

## Ağ ve servisler (özet)

- SSH (22), DNS (53), DHCP (67/68), HTTP (80), HTTPS (443), NTP (123), L2TP (1701) vb. portlar kullanılır.
- Servisler: nginx, uhttpd, dnsmasq, hostapd, dhcpd, postgresql, redis, mosquitto, loraserver, quagga vb.

---

## Güvenlik önerileri (genel)

- **Dosya izinleri:** Hassas dosyaların (ör. parola ve anahtar dosyaları) sadece gerekli kullanıcılar tarafından okunup yazılacak şekilde kısıtlanması önerilir.
- **SSH:** Mümkünse root parola ile girişi kısıtlayıp SSH anahtarı kullanın; güçlü parolalar kullanın.
- **Güncellemeler:** Üretici güncellemelerini takip edin; cihazı mümkünse yönetim ağında ve firewall ile koruyun.

Bu doküman yalnızca bilgi amaçlıdır; root veya admin erişim yöntemi verilmez. Tüm uygulama riski kullanıcıya aittir.
