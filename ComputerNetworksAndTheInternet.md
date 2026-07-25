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

# 1.1.2 A Services Description

Yukarıdaki tartışmamız Internet'i oluşturan birçok parçayı tanımladı. Ama Internet'i tamamen farklı bir açıdan da tanımlayabiliriz — yani **applications'a hizmet veren bir altyapı** olarak.

Geleneksel uygulamaların yanı sıra (e-mail ve Web gibi), Internet applications arasında şunlar da var: mobile smartphone ve tablet applications, Internet messaging, real-time road-traffic information ile mapping, music streaming, movie ve television streaming, online social media, video conferencing, multi-person games ve location-based recommendation systems. Bu uygulamalara **distributed applications** denir, çünkü birbiriyle data exchange eden multiple end systems içerirler.

Burası kritik aslında canlar, **Internet applications end systems'te çalışır** — network core'daki packet switches'te çalışmazlar. Packet switches end systems arası data exchange'i kolaylaştırır, ama data'nın kaynağı veya hedefi olan application ile ilgilenmezler. Bu, sınavlarda sık sorulan bir ayrımdır: "Application katmanı nerede çalışır?" Cevap: **End system'lerde (host'larda)**, router'larda değil!

## Hizmet Veren Altyapı

Peki "applications'a hizmet veren bir altyapı" tam olarak ne demek? Diyelim ki insanlığa büyük fayda sağlayacak veya seni zengin ve ünlü yapacak harika bir distributed Internet application fikrin var. Bu fikri gerçek bir Internet application'ına nasıl dönüştürürsün?

Application'lar end systems'te çalıştığı için, end systems'te çalışan programlar yazman gerekir. Örneğin programlarını **Java**, **C** veya **Python**'da yazabilirsin. Ama distributed bir Internet application geliştirdiğin için, farklı end systems'te çalışan programların birbirine **data göndermesi** gerekir.

İşte burada merkezi bir konuya geliyoruz — bu da Internet'i bir **application platformu** olarak tanımlamanın alternatif yoluna yol açıyor. Bir end system'de çalışan bir program, Internet'e başka bir end system'deki başka bir programa data teslim etmesi için **nasıl talimat verir?**

## Socket Interface — Internet'in "Posta Servisi Interface"i

Internet'e bağlı end systems, bir programın başka bir end system'deki spesifik hedef programına data göndermesi için nasıl istekte bulunduğunu belirleyen bir **socket interface** sağlar. 
Bu Internet socket interface, gönderen programın uyması gereken bir **kurallar setidir** ki Internet data'yı hedef programına teslim edebilsin. 

Şimdilik kitapta aşırı sık kullanılan basit bir analojisine bakalım: Alice, Bob'a posta servisiyle mektup göndermek istiyor. Alice, elbette mektubu (data) yazıp pencereden dışarı atamaz. Bunun yerine posta servisi şunları gerektirir:

1. Mektubu zarfın içine koy
2. Bob'un tam adını, adresini ve zip code'unu zarfın ortasına yaz
3. Zarfı mühürle
4. Pulu zarfın sağ üst köşesine yapıştır
5. Zarfı resmi posta servisi posta kutusuna at

Böylece posta servisinin kendi **"postal service interface"i** var — yani Alice'in uyması gereken kurallar seti ki mektup Bob'a ulaşsın. 
Benzer şekilde Internet'in de bir **socket interface'i** var; data gönderen programın, Internet'e data'yı alıcı programa teslim etmesi için uyması gereken kurallar.

## Internet'in Birden Fazla Hizmeti

Posta servisi elbette müşterilerine birden fazla hizmet sunar: hızlı teslimat, teslim alma onayı, genel kullanım ve daha birçok hizmet. Benzer şekilde Internet de uygulamalarına **multiple services** sunar. 
Bir Internet application geliştirdiğinde, uygulaman için Internet'in hizmetlerinden **birini seçmen** gerekir. 

## İki Tanımı Birleştirmek

Şu ana kadar Internet'in iki tanımını verdi bize network ustaları: biri hardware ve software bileşenleri açısından, diğeri distributed applications'a hizmet veren bir altyapı olarak. 
Ama belki hâlâ kafa karışıktır: Packet switching nedir? TCP/IP nedir? Router nedir? Internet'te ne tür communication links var? Distributed application nedir? Bir termostat falan Internet'e nasıl bağlanır?

Yazarların notu şöyle bize: Eğer şu an bunların hepsi kafanı karıştırıyorsa **endişelenme** — bu kitabın amacı hem Internet'in nuts-and-bolts'ını hem de nasıl ve neden çalıştığını yöneten prensipleri tanıtmaktır. 

"Socket interface" kavramı şimdilik soyut gelebilir, ama ileride göreceğiz ki bu aslında **API (Application Programming Interface)** demek. Yani uygulamanın işletim sistemine "şu IP'ye, şu porta, şu data'yı gönder" demesinin standart yolu. Production'da bir uygulama bağlantı sorunu yaşıyorsa, ilk bakacağın yer socket seviyesidir: `netstat`, `ss`, `lsof` komutlarıyla hangi socket'lerin hangi durumda (LISTEN, ESTABLISHED, TIME_WAIT) olduğunu kontrol edersin. Mülakatlarda "socket ne demek?" diye sorarlarsa, "application ile transport layer arasındaki arayüz" diyeceksin. TCP socket = IP + Port kombinasyonudur. Unutmamak lazım gerçekten önemli.

