# Donut Trader 0.3.1 — Fabric 1.21.11

**[Yeni JAR'ı indir](donut-trader-1.21.11-alt-0.3.1.jar?raw=true)** · [Kaynak kodu](donut-trader-source-0.3.1.zip?raw=true)

Minecraft Java **1.21.11**, Java **21**, Fabric Loader **0.19.5+** ve 1.21.11 Fabric API gerekir. Eski Donut Trader JAR'ını kaldırıp yeni JAR'ı `mods` klasörüne koyun. Aynı anda iki sürüm kurmayın.

## Kullanım

- **Sol Alt**, **`/dt`** veya **`/dt ui`**: paneli açar. Özet, Fırsatlar, Filtreler, Geçmiş sekmeleri vardır.
- **`/dt auto`** veya panelde **AUTO aç**: otomatik arama, uygun alış ve yeniden ilan akışını başlatır.
- **`/dt stop`**: durdurur. **`/dt status`**: hangi aşamada olduğu, kaç ilan taradığı ve neden almıyor. **`/dt market`**: veri kaynakları.

Panel açıkken yeni işlem yapılmaz; kapanınca arama yeniden açılır. Ekonomik işlemin ortasında panel açılmaz. Filtre değişikliği AUTO'yu durdurur. Oyun açıldığında AUTO kendiliğinden başlamaz.

## Geliştirmeler

**0.3.1:** menüyü açma/kapatma tuşu Sol Alt oldu. Eski kaydedilmiş Sağ Shift ayarını taşımamak için menü tuşunun kimliği yenilendi. `/dt` ve `/dt ui` korunur.

Gonuts'un MIT lisanslı **RobustStats** istatistik kodu dahil edildi: uç satışları ayıklama, log-MAD ve çeyreklik fiyat dağılımı. Kontrol paneli, eşya kara listesi, kalıcı işlem günlüğü ve neden beklediğini gösteren durum eklendi. Güncel Gonuts 26.2/Java25 hedeflidir; bu JAR, mevcut 1.21.11 istemcisinin geliştirilmiş sürümüdür, upstream'in bütün GUI/Swarm/Discord/proxy özelliklerinin portu değildir.

**API anahtarı zorunlu değildir.** Dış fiyat referansı eksik/eskimiş/engelli olduğunda en az beş aynı eşya/adette canlı akran ilanı kullanılır. Bu, tamamlanmış satış veya gerçek talep kanıtı değildir; panel bunu belirtir. Fiyat dağılımı %30'dan genişse işlem yapılmaz. Uygun ve taze web referansı hedefi yalnızca aşağı sınırlar. Son web kontrolü HTTP403 verdi; yeni sürüm bu durumda canlı ekran karşılaştırmasına devam edebilir.

İsteğe bağlı DONUT+ API anahtarı panelde panodan eklenebilir. Anahtar yalnızca yerel dosyada tutulur ve resmi api.donutsmp.net adresine Bearer olarak gönderilir; sohbet/loglarda gösterilmez. Resmi tamamlanmış işlem sayfaları arka planda 30 saniye aralıkla okunur. Yeterli kanıt için son üç günde en az beş kabul edilen satış, üç satıcı ve son altı saatte bir satış gerekir. Tekrarlanan sayfalar, özel eşyalar ve uç değerler ayıklanır; oynaklık %30'u aşan eşya bekletilir. Son başarılı okuma 90 saniyeden eskiyse bu referans kullanılmaz. Örneklenen satış/saat tüm pazarın likiditesi olarak gösterilmez. Anahtar yokken sahte satış veya demo fiyatı üretilmez.

## Bütçe ve kayıtlar

Toplam kümülatif alış bütçesi **10m**, asgari **tahmini net marj %15**, hesaplanan satış ücreti **en az %10 varsayımıdır**. Gerçek sunucu ücreti ve gerçekleşmiş kâr kanıtlanmış değildir. Kısa fiyat etiketlerinin üst sınırı alış tıklamasından önce bütçeye kalıcı ayrılır. Doğrudan teslimde kesin hesap kesintisi ayrıca ölçülmez; bütçe görünen teklifin ayrılan üst sınırını izler.

Gerçek envanter paketi, tam eşya/adet ve yeni Your Items ilanı kontrol edilir. Envanterden kaybolması tek başına satış başarısı değildir. Belirsiz ekonomik işlem otomatik tekrar edilmez. `config/donut-trader-ledger.json` bütçe dosyası korunmalı; silmek bütçeyi sıfırlar. Yeni `donut-trader-history.json` sadece işlem geçmişidir. Grafik **ilanların tahmini net kârını** gösterir; ilan açılması, eşyanın satıldığı veya kâr elde edildiği anlamına gelmez.

## Doğrulama ve kaynaklar

Java21/Fabric1.21.11 derlemesi ve **80 test** geçti. Para aralıkları, bütçe, yerel diyalog/teslim kanıtı, API şeması ve tekrarlanan kayıtlar, satıcı yoğunluğu, oynaklık, kaynak yokluğunda canlı akran tahmini ve kalıcı günlük kontrol edildi. **Gerçek hesapla DonutSMP alış/satışı ve yeni panelin oyunda görüntülenmesi bu ortamda denenmedi.** Kâr garantisi yoktur.

Kaynak arşivi üretim kodunu ve 71 sentetik testi içerir; kullanıcı tarafından sağlanan canlı ekran kaydı ve ona bağlı dokuz test yerelde tutulmuştur. Kaynak arşivinde Java21 ile `gradlew.bat build` veya `./gradlew build` kullanılabilir.

[Gonuts, pinned source](https://github.com/cody-raves/Gonuts/tree/1f7712fce7e7f01288e099790c1409dbf2e57b1c) · [Resmi API sözleşmesi](https://api.donutsmp.net/doc.json) · [Web referansı](https://donutsmpterminal.com/snapshots/latest.json). Gonuts copyright2026cody-raves ve MIT lisansı JAR içindeki `GONUTS-NOTICE.txt` / `licenses/Gonuts-MIT.txt` dosyalarındadır.

`SHA256SUMS` tüm JAR ve kaynak arşivi dosyalarının indirme kontrolünü içerir. Önceki sürümler yalnızca tarihsel dosyalardır.
