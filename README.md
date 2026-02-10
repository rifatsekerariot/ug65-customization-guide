# Milesight UG65 – Topluluk Özelleştirme Rehberi

Bu depo, **Milesight UG65** LoRaWAN gateway cihazında Ethernet portunu LAN olarak kullanma ve temel yapılandırma adımlarını içeren **resmi olmayan, topluluk rehberidir**. Milesight ile bağlantılı veya onaylı değildir.

---

## Bu rehber ne işe yarar?

- **Ethernet portunu LAN yapma:** Cihazın Ethernet portuna takılan cihazların (laptop, PC vb.) DHCP ile IP alıp WiFi veya SIM üzerinden internete çıkabilmesi.
- **Cihaz yapısına genel bakış:** Dosya/klasör yapısı ve güvenlikle ilgili genel bilgiler (şifre veya root erişim yöntemi **verilmez**).
- **Script’ler:** Bridge ve DHCP’yi kalıcı yapan örnek script’ler; kendi cihazınızda **root erişiminiz varsa** uygulayabilirsiniz.

**Root erişimi:** Bu rehberde root şifresine nasıl ulaşılacağı anlatılmaz. Cihazda zaten root yetkiniz varsa adımları uygulayabilirsiniz; yoksa bu rehberi yalnızca bilgi amaçlı kullanın.

---

## İçerik

| Dosya / Klasör | Açıklama |
|----------------|----------|
| [DISCLAIMER.md](DISCLAIMER.md) | Sorumluluk reddi ve uyarılar |
| [scripts/](scripts/) | Ethernet LAN bridge ve DHCP için örnek script’ler |
| [docs/](docs/) | Cihaz yapısı, Ethernet LAN kurulumu, güvenlik önerileri |

---

## Hızlı başlangıç (Ethernet’i LAN yapma)

1. Cihaza **root** ile SSH erişiminiz olduğundan emin olun (bu rehber root erişim yöntemi vermez).
2. [docs/ETHERNET_LAN.md](docs/ETHERNET_LAN.md) ve [scripts/](scripts/) içindeki adımları okuyun.
3. `scripts/eth_lan_bridge` dosyasını cihaza kopyalayıp init servisi olarak etkinleştirin; DHCP için `scripts/` içindeki rc.local örnek satırlarını uygulayın.

Tüm risk ve sorumluluk uygulayana aittir; garanti dışı kalabileceğiniz konular için [DISCLAIMER.md](DISCLAIMER.md) dosyasını okuyun.

---

## Lisans ve katkı

Bu içerik eğitim ve kendi cihazınızda kullanım amaçlı paylaşılmaktadır. Katkılarınızı pull request ile gönderebilirsiniz; şifre veya güvenlik açığı detayı eklemeyin.
