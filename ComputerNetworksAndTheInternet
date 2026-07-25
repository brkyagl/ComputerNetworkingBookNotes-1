# 1.1 Nedir Bu Internet?

Bu kitapta public Internet'i computer networks ve onların protocols'ünü tartışmak için ana araç olarak kullanılıyor. Peki Internet nedir? Bu soruya iki şekilde cevap veriyor bu abilerimiz:

1. **Nuts-and-bolts description:** Internet'in temel hardware ve software bileşenlerini anlatarak. Civata falan anlamına geliyor Türkçe olarak ıvır zıvır ama işin temel donanımı işte.
2. **Networking infrastructure:** Distributed uygulamalara hizmet veren bir altyapı olarak tanımlayarak. Internet = Altyapı.

## 1.1.1 A Nuts-and-Bolts Description

Internet dediğin şey aslında dünya genelinde **milyarlarca computing device'ı** birbirine bağlayan bir computer network. 
Çok uzun zaman önce değil, bu computing device'lar çoğunlukla geleneksel desktop bilgisayarlar, Linux workstation'lar ve Web sayfaları ile e-posta mesajları gibi bilgileri depolayan ve ileten **server**'lardı.

Ama giderek artan şekilde kullanıcılar Internet'e **akıllı telefon** ve **tablet**'lerle bağlanıyor. 
Bugün dünya nüfusunun yaklaşık **üçte ikisi** aktif mobil Internet kullanıcısı [Statista Users - https://www.statista.com/statistics/239114/global-mobile-internet-penetration/]. 
Üstelik geleneksel olmayan Internet "nesneleri" de bağlanıyor: TV'ler, oyun konsolları, termostatlar, ev güvenlik sistemleri, ev aletleri, saatler, gözlükler, arabalar, trafik kontrol sistemleri ve daha fazlası.

Hatta "computer network" terimi biraz eskimiş gibi duruyor, çünkü Internet'e bağlanan bu kadar çok geleneksel olmayan device var. 
Internet jargonunda, bütün bu cihazlara **hosts** veya **end systems** denir. Bazı tahminlere göre, 2026 yılında Internet'e bağlı yaklaşık **22 milyar** cihaz vardı ve bu sayı 2030 yılına kadar **31.2 milyara** ulaşacak [Statista Connections - https://www.statista.com/statistics/1183457/iot-connected-devices-worldwide/].

End system'ler, **communication links** ve **packet switches**'lerden oluşan bir ağ ile birbirine bağlıdır. Bir sonraki başlıklarda göreceğiz ki communication links'in birçok tipi var 
ve bunlar farklı fiziksel medyalardan oluşuyor: **coaxial cable**, **copper wire**, **optical fiber** ve **radio spectrum**. Farklı link'ler farklı hızlarda data iletebilir; bir link'in **transmission rate**'i **bits/second** cinsinden ölçülür.

Bir end system'in başka bir end system'e data göndermesi gerektiğinde, gönderen end system data'yı **segment**'lere böler ve her segment'e **header bytes** ekler. 
Ortaya çıkan bilgi paketlerine computer networks jargonunda **packets** denir. Bu packets daha sonra network üzerinden hedef end system'e gönderilir ve orada **reassembled** yani tekrar, yeniden monte edilerek, orijinal data haline getirilir.

Bir **packet switch**, gelen communication link'lerinden birine ulaşan bir packet'i alır ve giden communication link'lerinden birine **forward** eder. 
Packet switches birçok şekil ve türde gelir, ama günümüz Internet'indeki en belirgin iki tip **routers** ve **link-layer switches**'dir. Her iki switch tipi de packet'leri nihai hedeflerine doğru forward eder. 
**Link-layer switches** tipik olarak access networks'te kullanılırken, **routers** tipik olarak network core'da kullanılır. 
Bir packet'in gönderen end system'den alıcı end system'e kadar geçtiği communication links ve packet switches dizisine network üzerinden bir **route** veya **path** denir.

Packet-switched networks (packet taşıyan ağlar) birçok açıdan, otobanlar, yollar ve kavşaklar üzerinde araç taşıyan transportation networks'e benzer. 
Örneğin, binlerce kilometre uzaktaki bir depoya büyük miktarda kargo taşıması gereken bir fabrikayı düşün. 
Fabrikada cargo **segment**'lere ayrılır ve bir kamyon filosuna yüklenir. Her kamyon daha sonra otobanlar, yollar ve kavşaklardan oluşan network üzerinden bağımsız olarak hedef depoya seyahat eder. 
Hedef depoda cargo boşaltılır ve aynı sevkiyattan gelen diğer cargo ile birleştirilir. Böylece birçok açıdan: **packets** kamyonlara, **communication links** otoban ve yollara, **packet switches** kavşaklara, ve **end systems** binalara benzer. 
Tıpkı bir kamyonun transportation network üzerinden bir path izlemesi gibi, bir packet de computer network üzerinden bir path izler.

End system'ler Internet'e **Internet Service Providers (ISPs)** aracılığıyla erişir. Bunlar arasında residential ISP'ler (yerel kablo veya telefon şirketleri gibi), 
corporate ISP'ler, university ISP'ler, havalimanları, oteller, kafeler ve diğer public alanlarda WiFi erişimi sağlayan ISP'ler, ve akıllı telefonlarımıza ve diğer cihazlarımıza mobil erişim sağlayan cellular data ISP'ler bulunur. 
Her ISP kendi başına packet switches ve communication links'lerden oluşan bir network'tür.

ISP'ler end system'lere çeşitli network access tipleri sunar: residential broadband access (cable modem veya DSL gibi), high-speed local area network access ve mobile wireless access. 
ISP'ler aynı zamanda content providers'a(içerik sağlayıcıları işte mesela Netflix) da Internet access sağlar; server'ları doğrudan Internet'e bağlar. 
Internet, end system'leri birbirine bağlamakla ilgilidir, bu yüzden end system'lere erişim sağlayan ISP'ler de birbirine bağlı olmalıdır. 
Bu lower-tier ISP'ler, ulusal ve uluslararası upper-tier ISP'ler üzerinden birbirine bağlıdır ve bu upper-tier ISP'ler birbirine doğrudan bağlıdır. 
Bir upper-tier ISP, high-speed fiber-optic link'lerle birbirine bağlı **high-speed routers**'lerden oluşur. 
Her ISP network'ü — upper-tier veya lower-tier — bağımsız olarak yönetilir, **IP protocol**'ünü çalıştırır ve belirli isimlendirme ve adres kuralları'na uyar. ISP'leri ve onların birbirine bağlanmasını daha sonra yakından inceleyeceğiz.

End system'ler, packet switches ve Internet'in diğer parçaları, Internet içinde bilgi gönderimini ve alımını kontrol eden **protocols**'ü çalıştırır. 
**Transmission Control Protocol (TCP)** ve **Internet Protocol (IP)**, Internet'teki en önemli iki protokoldür. IP protocol, router'lar ve end system'ler arasında gönderilen ve alınan packet'lerin formatını belirler. 
Internet'in ana protocols'ü kolektif olarak **TCP/IP** olarak bilinir. Bu protokollere detaylı bakmaya başlayacağız. Ama bu sadece bir başlangıç — bu bu kitapta adamlar büyük bir kısmı networking protocols ile ilgili yazmış zaten.

Protocol'lerin Internet için önemi göz önüne alındığında, herkesin her bir protocol'ün ne yaptığı konusunda anlaşması önemlidir, böylece insanlar birbiriyle çalışabilen sistemler ve ürünler oluşturabilir. 
İşte tam burada **standards** devreye girer. Internet standards, **Internet Engineering Task Force (IETF)** tarafından geliştirilir. IETF standards documents'a **requests for comments (RFCs)** denir. 
RFC'ler, isimlerinin de ima ettiği gibi, genel görüş talepleri olarak başladı; Internet'in öncüsünün karşılaştığı network ve protocol tasarım problemlerini çözmek için. 
RFC'ler oldukça teknik ve detaylıdır. TCP, IP, HTTP (Web için) ve SMTP (e-mail için) gibi protokolleri tanımlarlar. Şu anda **9000'den fazla RFC** bulunmaktadır.

Diğer kuruluşlar da network component'leri için standartlar belirler; en dikkat çekici olanı network links için olanlar. 
Örneğin **IEEE 802 LAN Standards Committee**, **Ethernet** ve wireless **WiFi** standartlarını belirler.

- **Transmission rate bits/second ile ölçülür**, bytes/second değil. Sınavlarda ve mülakatlarda bu ayrım tuzak soru olarak gelir. 1 byte = 8 bit.
- **Link-layer switches vs Routers:** Link-layer switches access network'te (evindeki, ofisteki switch gibi), routers ise network core'da (ISP backbone kısmı gibi). Router L3 (IP), switch L2 (MAC) çalışır.
- **RFC'ler "tavsiye" gibi görünse de aslında Internet'in anayasasıdır.** Bir protokolün RFC numarasını bilmek, o protokolün davranışını anlamak için kritiktir. Örneğin IP = RFC 791, TCP = RFC 793.
- **IEEE 802.3 = Ethernet, IEEE 802.11 = WiFi.** Bunları karıştırma, sınavlarda direkt sorarlar.

## Internet Haritası 

```
                    ┌─────────────────────────────────────┐
                    │      National or Global ISP         │
                    │    (◯)────(◯)────(◯)                │
                    │      │      │      │                │
                    └──────┼──────┼──────┼────────────────┘
                           │      │      │
            ┌──────────────┘      │      └──────────────┐
            │                     │                     │
       ┌────┴────┐          ┌────┴────┐          ┌─────┴──────┐
       │ Mobile  │          │  Local  │          │ Datacenter │
       │ Network │          │  or     │          │  Network   │
       │  📱🚗🚦 │          │Regional │          │  [🖥️🖥️]   │
       │   ⬆️    │          │  ISP    │          │     │      │
       │  (◯)────┼──────────┤  (◯)    ├──────────┤  (◯)       │
       └─────────┘          │  │ │    │          └────────────┘
                            │  │ │    │
       ┌──────────────┐     │  │ │    │     ┌─────────────────┐
       │   Home       │     │  │ │    │     │  Content        │
       │   Network    │     │  │ │    │     │  Provider       │
       │ [💻📱🌡️🧊]   │     │  │ │    │     │    Network      │
       │    (◯)───────┼─────┘  │ │    └─────┤   (◯)           │
       └──────────────┘        │ │          └─────────────────┘
                               │ │
                               │ │
       ┌──────────────────────── │
       │    Enterprise Network    │
       │  [💻💻💻📱📱🖥️]          │
       │     (◯)──(◯)──(◯)        │
       └──────────────────────────┘

       Örnek:
       ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐
       │  💻     │  │  🖥️     │  │  📱     │  │  (◯)    │
       │  Host   │  │ Server  │  │ Mobile  │  │ Router  │
       │(end sys)│  │         │  │Computer │  │         │
       └─────────┘  └─────────┘  └─────────┘  └─────────┘
       
       ┌─────────┐  
       │  ⬆️     │  
       │ Link-   │  
       │ layer   │  
       │ Switch  │  
       └─────────┘  
       
 
```
