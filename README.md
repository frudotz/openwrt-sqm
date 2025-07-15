# OpenWRT için Smart Queue Management Rehberi! 
Bu rehberimizde OpenWRT cihazınıza SQM kurulumu yaparak **bufferbloat** sorununun çözmenizi sağlayacağız.  
*Rehberimizde [OpenWRT dökümanını](https://openwrt.org/docs/guide-user/network/traffic-shaping/sqm) referans aldık. Rehberimizi kaynak göstererek paylaşmanızı rica ederiz.* 🙏  


<details>
  <summary>📋 İçindekiler</summary>
  <ol>
    <li><a href="#-sqm-ne-i%CC%87%C5%9Fe-yarar">⚡ SQM Ne İşe Yarar?</a></li>
    <li><a href="#-sqm-paket-kurulumu">🚀 SQM Paket Kurulumu</a></li>
    <li><a href="#-pratik-ayar-önerileri">🧩 Pratik Ayar Önerileri</a></li>
    <li><a href="#-performans-testi">📊 Performans Testi</a></li>
    <li><a href="#-sık-sorulan-sorular">🔧 Sık Sorulan Sorular</a></li>
    <li><a href="#-katkıda-bulun--bağış">🤝 Katkıda Bulun / Bağış</a></li>
    <li><a href="#️-kaynaklar">🗃️ Kaynaklar</a></li>
  </ol>
</details>


## ⚡ SQM Ne İşe Yarar?

- SQM, ağ trafiğini akıllıca yöneterek bufferbloat’ı azaltır.
- Birden çok cihaz aktifken bile daha düşük ve stabil ping sağlar.  
- Bant genişliğini adil paylaşarak hem hızdan hem tepkisellikten ödün vermemeni sağlar.  

> 🔧 SQM bir sihir değil hattını fiber yapmaz, ama hattının potansiyelini sonuna kadar kullandırır.


## 🚀 SQM Paket Kurulumu

Herhangi bir uçbirim üzerinden cihaza SSH ile bağlanarak aşağıdaki komutları girin.  

```
opkg update
opkg install luci-app-sqm
```

> 📝 Bu işlemi arayüzden `System > Software` altından da yapabilirsiniz.

### ✅ Bu kadar!  
LuCI web arayüzünde şu menü gelir:  
**Network → SQM/QoS**


## 🧩 Pratik Ayar Önerileri

- Download/upload değerini hızının %85-90’ı kadar gir. (Kbps cinsinden, 100 Mbps → 102400 Kbps)
- Queue discipline olarak `cake` → modern & en dengeli.
- Script olarak `piece_of_cake.qos` → ilk kurulum için hızlı ve temiz çözüm.


## 📊 Performans Testi

Kurulum sonrası bufferbloat testi için:
- [Waveform Bufferbloat Test](https://www.waveform.com/tools/bufferbloat)
- [DSLReports Speedtest (varsa)](http://www.dslreports.com/speedtest)

İdeal:
- İndirme & yükleme sırasında bile ping artışı minimal
- Bufferbloat sonucu: **A veya A+**


## 🔧 Sık Sorulan Sorular

**S:** Download’u tam ISS hızına yazsam?  
**C:** Upload sırasında ping zıplayabilir. %85-90 cıvarı idealdir.

**S:** `fq_codel` mi `cake` mi?  
**C:** Cake genellikle daha iyi. Modern donanımda CPU’yu da yormaz.

**S:** LuCI yok, CLI’dan?  
**C:** `sqm-scripts` paketini kur → `/etc/config/sqm` dosyasını elle düzenle.

## 🤝 Katkıda Bulun / Bağış
Yanlış gördüğünüz veya eklemek istediğiniz bir şey varsa:  
PR/Issue açarak ya da DM’den yazazarak iletebilirsiniz.  
Kod kadar fikir de katkıdır. 🙏  

### [🍻 Bir bira ısmarla](https://coff.ee/frudotz)
Rehberimizi faydalı bulduysanız, destek olabilirsiniz.


# 🗃️ Kaynaklar
  - [OpenWRT Wiki](https://openwrt.org/docs/guide-user/network/traffic-shaping/sqm)
  - [Bufferbloat.net](https://www.bufferbloat.net)
  - `tc`, `iptables` ve `cake` parametreleriyle ileri seviye tuning
   
-----------
🎀 Rehberimizi okuduğunuz için teşekkür ederiz!  
⭐ İçeriği faydalı bulduysanız desteklemek için **Star** verebilirsiniz.  

