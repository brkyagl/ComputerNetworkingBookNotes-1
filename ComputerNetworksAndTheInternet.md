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

# 1.1.3 Nedir Ya Bu Protocol?

Artık Internet'in ne olduğu hakkında biraz fikrimiz var, şimdi computer networking'teki diğer önemli buzzword'ü ele alalım: **protocol**. Protocol nedir? Protocol ne yapar?

## Kitaptaki İnsan Analojisi

Computer network protocol kavramını anlamanın en kolay yolu, önce bazı **insan diyaloglarını** düşünmek olabilir, çünkü biz insanlar da sürekli protocol'ler icra ediyoruz.

Birine saat sorarken ne yaptığınızı düşünün. İnsan protocol (veya en azından iyi davranışlar) diyor ki, önce bir selamlaşma yapmalısın — ilk **"Merhaba"** gibi, başka biriyle iletişimi başlatmak için. **"Merhaba"**'ya tipik yanıt ise karşılıklı bir **"Merhaba"** mesajıdır. Örtük olarak, samimi bir **"Merhaba"** yanıtı, saat sorabileceğinizin işaretidir. İlk **"Merhaba"**'ya farklı bir yanıt (örneğin **"Rahatsız etme beni!"** veya **"Abe ben suri no turkish,"** veya bazı yazılamayacak yanıtlar) ise iletişime isteksizlik veya yetersizlik belirtebilir. Bu durumda human protocol, o kişiden saat sormamak olurdu. Bazen bir soruya hiç yanıt alınmaz, bu durumda tipik olarak o kişiden saat sormaktan vazgeçilir. İnsan protocol'ümüzde, **gönderdiğimiz spesifik mesajlar** ve **alıcı yanıt mesajlarına veya diğer olaylara karşı aldığımız spesifik aksiyonlar** (örneğin belirli bir süre içinde yanıt gelmemesi) vardır. Açıkça, iletilen ve alınan mesajlar, bu mesajlar gönderildiğinde ve alındığında veya diğer olaylar gerçekleştiğinde alınan aksiyonlar, bir insan protocol'de merkezi rol oynar. Eğer insanlar farklı protocol'ler çalıştırırsa (örneğin biri nazik ama diğeri değilse, veya biri zaman kavramını anlıyor ama diğeri anlamıyorsa), protocol'ler birbiriyle çalışmaz ve hiçbir faydalı iş yapılamaz. Networking'te de aynı şey geçerlidir — bir görevi tamamlamak için aynı protocol'ü çalıştıran iki (veya daha fazla) iletişim kuran varlık gerekir.

İkinci bir insan analojisi düşünelim. Diyelim ki bir college class'tasınız (örneğin bir computer networking class'ı). Öğretmen protocol'ler hakkında gevezelik ediyor ve siz kafanız karışmış durumdasınız. Öğretmen durup soruyor: **"Sorusu olan var mı?"** (uyumayan tüm öğrencilere iletilen ve alınan bir mesaj). Siz elinizi kaldırıyorsunuz (öğretmene örtük bir mesaj iletiyorsunuz). Öğretmeniniz size gülümseyerek **"Evet . . ."** diyerek sizi onaylıyor (soru sormanızı teşvik eden iletilen bir mesaj), ve siz sonra sorunuzu soruyorsunuz (yani öğretmeninize mesajınızı iletiyorsunuz). Öğretmeniniz sorunuzu duyuyor (soru mesajınızı alıyor) ve cevaplıyor (size bir yanıt iletiyor). Bir kez daha görüyoruz ki, mesajların iletimi ve alımı, ve bu mesajlar gönderildiğinde ve alındığında alınan reaksiyonlar seti, bu question-and-answer protocol'ünün kalbinde yer alır.


## İnsan Protocol'ü ve Computer Network Protocol'ü

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   Sol Taraf: İnsan                        Sağ Taraf: Computer Network       │
│                                                                             │
│                                                                             │
│   👩 Alice                               💻 Client Computer                 │
│      │                                      │                               │
│      │  "Merhaba"                           │  TCP connection request       │
│      │ ───────────────────────────────►     │ ─────────────────────────►    │
│      │                                      │         🖥️ Web Server         │
│      │  "Merhaba"                           │                               │
│      │ ◄───────────────────────────────     │    TCP connection reply       │
│      │                                      │ ◄─────────────────────────    │
│      │                                      │                               │
│      │  "Saat kaç?"                         │  GET http://www.test-         │
│      │ ───────────────────────────────►     │  test.com/network/            │
│      │                                      │ ─────────────────────────►    │
│      │                                      │                               │
│      │  "10:00"                             │  <file>                       │
│      │ ◄───────────────────────────────     │ ◄─────────────────────────    │
│      │                                      │                               │
│   Time ▼                                  Time ▼                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Network Protocols

Bir **network protocol**, bir insan protocol'üne benzer, tek farkı mesaj exchange eden ve aksiyon alan varlıkların bir cihazın hardware veya software component'leri olmasıdır (örneğin computer, akıllı telefon, tablet, router veya diğer network-capable device). Internet'te iki veya daha fazla iletişim kuran remote varlığı içeren tüm aktivite, bir protocol tarafından yönetilir. Örneğin, fiziksel olarak bağlı iki computer'daki **hardware-implemented protocols**, iki network interface card arasındaki **"tel"** üzerindeki bit akışını kontrol eder; end systems'teki **congestion-control protocols**, sender ve receiver arasındaki packet'lerin iletim hızını kontrol eder; router'lardaki protocol'ler bir packet'in kaynaktan hedefe olan path'ini belirler. Protocol'ler Internet'in her yerinde çalışır, ve dolayısıyla bu okuduğumuz kitaptaki konuların büyük bir kısmı computer network protocols hakkındadır.

Muhtemelen aşina olduğunuz bir computer network protocol örneği olarak, bir Web server'a request yaptığınızda ne olduğunu düşünün; yani bir Web sayfasının URL'sini Web browser'ınıza yazdığınızda.
İlk olarak, computer'ınız Web server'a bir **connection request message** gönderir ve bir yanıt bekler. Web server sonunda connection request mesajınızı alır ve bir **connection reply message** döndürür. Artık Web dokümanını request etmenin OK olduğunu bilen computer'ınız, o Web server'dan fetch etmek istediği Web sayfasının adını bir **GET message** içinde gönderir. Son olarak, Web server Web sayfasını (**file**) computer'ınıza döndürür.

Yukarıdaki insan ve networking örnekleri göz önüne alındığında, mesajların exchange'i ve bu mesajlar gönderildiğinde ve alındığında alınan aksiyonlar, bir protocol'ün temel tanımlayıcı elementleridir:

> **Bir *protokol*, iki veya daha fazla iletişim kuran varlık arasında exchange edilen mesajların biçimini ve sırasını, ayrıca bir mesajın veya başka bir olayın iletilmesi ve/veya alınması sırasında gerçekleştirilen eylemleri tanımlar.**

Internet ve genel olarak computer networks, protocol'leri yoğun şekilde kullanır. Farklı iletişim görevlerini tamamlamak için farklı protocol'ler kullanılır.

Sınavda falan "Protocol nedir?" diye sorarlarsa, tam olarak bu cümleyi akla getir: *“Bir protokol, mesajların biçimini ve sırasını ile iletim/alınma sırasında gerçekleştirilen işlemleri tanımlar.”* Ayrıca şuna dikkat et: şema sağ taraf aslında **TCP Three-Way Handshake**'in basitleştirilmiş halidir. Client SYN gönderir, Server SYN-ACK döner, Client ACK gönderir — ama burada kitapta sadece "connection request" ve "connection reply" diyor. 

Şimdilik bil ki: Protocol = format + order + actions. Bu üçlüyü unutma.

---

# 1.2 The Network Edge

Önceki konularda, Internet ve networking protocol'lerinin high-level önbakışını sunduk. Şimdi Internet'in component'lerine biraz daha derinlemesine dalacağız. 
Bu konuda network'ün **edge**'inden başlayacağız ve en tanıdık olduğumuz component'lere bakacağız — yani günlük hayatta kullandığımız computer'lar, akıllı telefon'lar ve diğer cihazlar. 
Bir sonraki konuda da network edge'den network core'a geçeceğiz ve computer networks'teki switching ve routing'i inceleyeceğiz.

Önceki konudan hatırlayın: computer networking jargonunda, Internet'e bağlı computer'lar ve diğer cihazlar sıklıkla **end systems** olarak adlandırılır. 
Bunlara **end systems** denir çünkü Internet'in **edge**'inde yer alırlar. Internet'in end systems'leri arasında desktop computer'lar (örneğin desktop PC'ler, Mac'ler ve Linux box'lar), server'lar (örneğin Web ve e-mail server'ları) ve mobile devices (örneğin laptop'lar, akıllı telefon'lar ve tablet'ler) bulunur.

## End-System Etkileşimleri

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌──────────────┐                                                          │
│   │ Mobile       │     ┌─────────────────────────────────────               │
│   │ Network      │     │      National or Global ISP        │               │
│   │  📱 🚗 🚦    │     │    (◯)────(◯)────(◯)               │               │ 
│   │     ⬆️       │     │      │      │      │               │               │
│   │   (◯)────────┼─────┼──────┼──────┼──────┼───────────────┤               │
│   └──────────────┘     │      │      │      │               │               │
│                        │      │      │      │               │               │
│   ┌──────────────┐     │  ┌───┴───┐  │      │  ┌────────────┴────┐          │
│   │ Home         │     │  │ Local │  │      │  │ Datacenter      │          │
│   │ Network      │     │  │ or    │  │      │  │ Network         │          │
│   │ [💻📱🌡️🧊]   │     │  │Regional│ │      │  │  [🖥️🖥️]         │          │
│   │    (◯)───────┼─────┘  │ ISP   │  │      │  │     │           │           │
│   └──────────────┘        │ (◯)   │  │      │  │  (◯)            │           │
│                           └───┬───┘  │      │  └─────────────────┘           │
│                               │      │      │                                │
│   ┌──────────────────┐        │      │      │      ┌────────────────────┐    │
│   │ Enterprise       │        │      │      │      │ Content Provider   │    │
│   │ Network          │        │      │      │      │ Network            │    │
│   │ [💻💻💻📱📱🖥️]   │       │      │      │      │  (◯)                │   │
│   │    (◯)──(◯)──(◯)│         │      │      │      └────────────────────┘    │
│   └──────────────────┘        │      │      │                                │
│                               │      │      │                                │
│                               └──────┴──────┘                                │
│                                                                              │
│   ═══════════════════════════════════════════════════════════════════════    │
│                                                                              │
│   End-System: Bir laptop (Mobile Network) ile bir server                     │
│   (Content Provider Network / Datacenter) arasındaki iletişim yolu.          │
│   Paket edge'den (end system) core'a (ISP'ler) doğru ilerler.                │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

Ayrıca, giderek artan sayıda geleneksel olmayan "nesneler" de end systems olarak Internet'e bağlanıyor...

End systems aynı zamanda **hosts** olarak da adlandırılır, çünkü **host** (yani çalıştırır) application program'ları: Web browser programı, Web server programı, e-mail client programı veya e-mail server programı gibi **hosts** ve **end systems** terimlerini birbirinin yerine kullanacağız; yani **host = end system**. Host'lar bazen daha da iki kategoriye ayrılır: **clients** ve **servers**. Informal olarak, client'lar tipik olarak desktop'lar, laptop'lar, akıllı telefon'lar ve benzeri cihazlarken, server'lar Web sayfalarını depolayan ve dağıtan, video stream eden, e-mail relay eden ve daha fazlasını yapan daha güçlü makinelerdir. Bugün, search results, e-mail, Web sayfaları, videolar ve mobile app content aldığımız çoğu server, büyük **data centers**'ta bulunur. Örneğin, Google'ın küresel altyapısı 2024 sonları itibarıyla 33 veri merkezine sahipken, 2026 yılı itibarıyla 4 kıtada toplam 35 Data Center ve 40 Cloud bölgesine ulaşmıştır.

## Data Centers and Cloud Computing

Google, Microsoft, Amazon ve Alibaba gibi Internet şirketleri, her birinde on binlerce ila yüz binlerce host barındıran devasa data center'lar inşa etmiştir. Bu data center'lar sadece şemalarda gösterildiği gibi Internet'e bağlı değil, aynı zamanda data center'ın host'larını birbirine bağlayan karmaşık computer networks'leri de dahili olarak içerirler. Data center'lar, günlük hayatta kullandığımız Internet applications'ların arkasındaki motorlardır.

Genel olarak konuşursak, data center'lar üç amaca hizmet eder; bunları somutluk için Amazon bağlamında açıklayalım:

1. **Amazon e-commerce pages**'ini kullanıcılara sunarlar; örneğin ürünleri açıklayan sayfalar ve satın alma bilgileri.
2. Amazon-spesifik data processing tasks için **büyük ölçekli paralel hesaplama altyapısı** olarak hizmet ederler.
3. Diğer şirketlere **cloud computing** sağlarlar.

Bugün, computing'teki önemli bir trend, şirketlerin IT ihtiyaçlarının hepsini Amazon gibi bir cloud provider kullanarak karşılamasıdır. 
Örneğin, Airbnb ve diğer birçok Internet-based şirket kendi data center'larını sahip olmaz ve yönetmez, bunun yerine tüm Web-based servislerini Amazon cloud'unda, yani **Amazon Web Services (AWS)**'de çalıştırır.

Bir data center'daki işçi arılar host'lardır. İçerik sunarlar (örneğin Web sayfaları ve videolar), e-mail ve dokümanları depolarlar, ve toplu olarak büyük ölçekli distributed hesaplamalar gerçekleştirirler. 
Data center'lardaki host'lara **blades** denir ve pizza kutularına benzerler; genellikle CPU, memory ve disk storage içeren commodity host'lardır. 
Host'lar **raf**'lara istiflenir ve her raf tipik olarak 20 ila 40 blade içerir. Raflar daha sonra gelişmiş ve gelişen data center network designs kullanılarak birbirine bağlanır.

Bu arada şunların üstünde duralım: **Host = End System**. Kitap bunu birbiri yerine kullanıyor, Ee biz de öyle kullanacağız. Ayrıca **Client vs Server** ayrımı informal — yani katı bir kural değil. Bir laptop client olabilir ama üzerinde bir Web server çalıştırırsan server da olur. Production'da "edge computing" konsepti var, artık client'lar da işlem yapıyor. Data center konusunda ise referans önemli: Google'ın 35 data center'ı ve milyonlarca server'ı var. Bu, "ölçek" kavramını anlamak için kritik. Cloud computing (AWS, Azure, GCP) demek, senin fiziksel server'ın yok ama bu devasa data center'lardaki virtual machine'leri kullanıyorsun demek. Sınavda "cloud nedir?" diye sorarlarsa, "başkasının data center'ındaki kaynakları kiralamak" diyeceğiz. Ayrıca **blade** terimini unutma: data center'daki ince, pizza kutusu şeklindeki server'lara denir. Raf başı 20-40 blade, bu da hesaplama gücünün ne kadar yoğun olduğunu gösterir.

# 1.2.1 Access Networks

Network'ün "edge"indeki applications ve end systems'leri ele aldıktan sonra, şimdi **access network**'ü düşünelim — yani bir end system'i fiziksel olarak ilk router'a (aynı zamanda **"edge router"** olarak da bilinir) bağlayan network, bu router da end system'den başka herhangi bir uzak end system'e giden path üzerindedir.

## Home Access: DSL, Cable, FTTH, Fixed Wireless, and LEO Satellites

2023 itibarıyla, Avrupa ve ABD'deki hanelerin %80'inden fazlası Internet access'e sahip [OECD 2024], ancak dünya genelinde ve farklı demografik gruplar arasında bir dijital uçurum mevcut [globaldigitalinclusion 2025]. 
Bu yaygın home access network kullanımı göz önüne alındığında, access networks önbakışına evlerin Internet'e nasıl bağlandığını inceleyerek başlayalım.

Bugün, en yaygın üç geniş bantlı ev kullanımı access tipi **digital subscriber line (DSL)**, **cable** ve **fiber to the home (FTTH)**'dir.

---

## Access Networks

```
┌─────────────────────────────────────────────────────────────────────────────┐
│   ┌──────────────┐                                                          │
│   │ Mobile       │     ┌─────────────────────────────────────┐              │
│   │ Network      │     │      National or Global ISP         │              │
│   │  📱 🚗 🚦    │     │    (◯)────(◯)────(◯)                │              │
│   │     ⬆️       │     │      │      │      │                │              │
│   │   (◯)════════╪═════╪══════╪══════╪══════╪═══════════════╪═══╗            │
│   └──────────────┘     │      │      │      │               │   ║            │
│                        │      │      │      │               │   ║            │
│   ┌──────────────┐     │  ┌───┴───┐  │      │  ┌────────────┴───┴──┐         │
│   │ Home         │     │  │ Local │  │      │  │ Datacenter        │         │
│   │ Network      │     │  │ or    │  │      │  │ Network           │         │
│   │ [💻📱🌡️🧊]   │     │  │Regional│ │      │  │  [🖥️🖥️]          │         │
│   │    (◯)═══════╪═════╝  │ ISP   │  │      │  │     │            │         │
│   └──────────────┘        │ (◯)   │  │      │  │  (◯)             │         │
│                           └───┬───┘  │      │  └─────────────────┘          │
│                               │      │      │                               │
│   ┌──────────────────┐        │      │      │      ┌────────────────────┐   │
│   │ Enterprise       │        │      │      │      │ Content Provider   │   │
│   │ Network          │        │      │      │      │ Network            │   │
│   │ [💻💻💻📱📱🖥️]   │        │      │      │     │  (◯)               │    │
│   │    (◯)══(◯)══(◯)│         │      │      │     └────────────────────┘    │
│   └──────────────────┘        │      │      │                               │
│                               └──────┴──────┘                               │
│                                                                             │
│   ═══════ : Thick shaded lines = Access Networks                            │
│   (Home, Enterprise, Mobile Wireless edge connections)                      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

> Mobile Network, Home Network ve Enterprise Network'ten Local/Regional ISP'ye giden kalın gölgeli çizgiler access networks'ü temsil ediyor.

## DSL Internet Access

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│    [Home phone]                                                             │
│         │                                                                   │
│         │                                                                   │
│         ├────────────┐                                                      │
│         │            │                                                      │
│    [Splitter]◄───────┘                                                      │
│         │                                                                   │
│         │                                                                   │
│    [DSL modem]                                                              │
│         │                                                                   │
│         │          Existing phone line (bakır tel)                          │
│         └────────────────────────────────────────────────────────┐          │
│                                                                  │          │
│                                                                  ▼          │
│                                                               [DSLAM]       │
│                                                                 │           │
│                                                                 │           │
│                                                                 ▼           │
│    [Home PC]◄──────────────────────────────────────────────────┘            │
│                                                                             │
│    Central Office (CO) ─────► [Telephone network] ─────► [Internet]         │
│                                   (◯)────(◯)────(◯)                         │
│                                                                             │
│    DSLAM = Digital Subscriber Line Access Multiplexer                       │
│    CO    = Telco'nun local central office'ı                                 │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

Bir ikamet yeri tipik olarak DSL Internet access'i, aynı yerel telefon şirketinden (telco) alır ki bu şirket wired local phone access'i de sağlar. 
Böylece, DSL kullanıldığında, müşterinin telco'su aynı zamanda onun ISP'sidir. Şemada gösterildiği gibi her müşterinin DSL modem'i mevcut telephone line'ı kullanarak telco'nun local central office'inde (CO) bulunan bir **digital subscriber line access multiplexer (DSLAM)** ile data exchange eder. Evin DSL modem'i digital data'yı alır ve bunu CO'ya telephone wires üzerinden iletim için **high-frequency tones**'a çevirir; birçok evden gelen analog signals DSLAM'da tekrar digital formata çevrilir.

ikamet yeri telephone line hem data hem de geleneksel telephone signals'i aynı anda taşır, bunlar farklı frekanslarda encode edilmiştir:

- **High-speed downstream channel**, 50 kHz ila 1 MHz bandında
- **Medium-speed upstream channel**, 4 kHz ila 50 kHz bandında
- **Sıradan iki yönlü telefon kanalı**, 0 ila 4 kHz bandında

Bu yaklaşım, tek DSL link'inin sanki üç ayrı link varmış gibi görünmesini sağlar, böylece bir telephone call ve bir Internet connection aynı anda DSL link'ini paylaşabilir.  
Müşteri tarafında, bir **splitter** eve gelen data ve telephone signals'i ayırır ve data signal'ini DSL modem'e yönlendirir. 
Telco tarafında, CO'da DSLAM data ve phone signals'i ayırır ve data signal'ini Internet'e gönderir. Yüzlerce veya binlerce hane tek bir DSLAM'e bağlanır.

En son DSL standardı [ITU DSL 2019], kısa mesafelerde **1 Gbps'e kadar downstream** ve **500 Mbps'e kadar upstream** transmission rate sağlar. Downstream ve upstream rate'leri farklı olduğu için, access **asymmetric** (asimetrik) olarak adlandırılır. Gerçek downstream ve upstream transmission rate'leri, yukarıda belirtilen rate'lerden daha düşük olabilir, çünkü DSL sağlayıcılar farklı rate'leri farklı fiyatlarda sunduğundan ikamet yerinin rate'i bilerek sınırlayabilir. 
Maksimum rate aynı zamanda ev ile CO arasındaki mesafe, twisted-pair line'ın kalınlığı ve elektriksel parazit derecesi tarafından da sınırlanır. 
Mühendisler DSL'i ev ile CO arasındaki kısa mesafeler için özel olarak tasarlamıştır; genel olarak, eğer ikamet yerin CO'nun **5 ila 10 mil** içinde değilse, residence alternatif bir Internet access formuna başvurmak zorundadır.

> DSL'in asimetrik olması çok önemli. Downstream (indirme) > Upstream (yükleme). Neden? Çünkü ev kullanıcısı genelde video izler, Web sayfası indirir — yani daha çok data alır. [ITU DSL 2019] standardını unutma, bu ITU-T G.fast ve benzeri standartları kapsar. Ayrıca "5-10 mil" kuralı: DSL elektrik sinyali taşıdığı için mesafe arttıkça zayıflar. Production'da bir kullanıcı "Internet yavaş" diyorsa, DSL ise ilk kontrol: CO'ya olan mesafe ve hat kalitesi. Splitter'ın olmaması telefon çalmalarında Internet'in kopmasına neden olur.

## Hybrid Fiber-Coaxial Access Network

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│        Hundreds of homes          Hundreds of homes                         │
│         🏠    🏠    🏠            🏠    🏠    🏠                            │
│          │     │     │             │     │     │                            │
│          └─────┼─────┘             └─────┼─────┘                            │
│                │                         │                                  │
│           [Coaxial cable]           [Coaxial cable]                         │
│                │                         │                                  │
│                │    ┌─────────────┐      │                                  │
│                └────┤ Fiber node  ├─────┘                                   │
│                     │  (Kavşak)   │                                         │
│                     └──────┬──────┘                                         │
│                            │                                                │
│                         [Fiber cable]                                       │
│                            │                                                │
│                            ▼                                                │
│                     ┌─────────────┐                                         │
│                     │    CMTS     │                                         │
│                     │(Cable Modem  │                                        │
│                     │ Termination │                                         │
│                     │   System)   │                                         │
│                     └──────┬──────┘                                         │
│                            │                                                │
│                            ▼                                                │
│    [Internet] ◄───────── [Cable head end]                                   │
│       (◯)                                                                   │
│                                                                             │
│    HFC = Hybrid Fiber Coaxial                                               │
│    CMTS = Cable Modem Termination System (DSL'deki DSLAM'in karşılığı)      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

DSL, telco'nun mevcut local telephone altyapısını kullanırken, **cable Internet access** cable television şirketinin mevcut cable television altyapısını kullanır. Bir ikamet yeri, cable television'ı sağlayan aynı şirketten cable Internet access alır. Şemada gösterildiği gibi fiber optik kablo, head end'i yani başlık ucunu mahalle düzeyindeki kavşaklara bağlar, buradan geleneksel coaxial cable tek tek evlere ve dairelere ulaşır. 
Her komşu kavşak tipik olarak **500 ila 5.000 hane**'yi destekler. Hem fiber hem de coaxial cable bu sistemde kullanıldığı için, bu sıklıkla **hybrid fiber coax (HFC)** olarak adlandırılır.

Cable Internet access özel modem'ler gerektirir; bunlara **cable modem**'ler denir. DSL modem'inde olduğu gibi, cable modem tipik olarak harici bir cihazdır ve home PC'ye bir **Ethernet port** üzerinden bağlanır.
Cable head end'de, **cable modem termination system (CMTS)** DSL network'ün DSLAM'ine benzer bir fonksiyon görür — birçok downstream home'dan cable modem'ler tarafından gönderilen analog signal'i tekrar digital formata çevirir. 
Cable modem'ler HFC network'ünü iki channel'a ayırır: bir downstream ve bir upstream channel. DSL'de olduğu gibi, access tipik olarak **asymmetric**'tir; downstream channel genellikle upstream channel'dan daha yüksek transmission rate'e sahiptir. **DOCSIS 2.0** ve **3.0** standartları sırasıyla **40 Mbps ve 1.2 Gbps** downstream bitrate'leri ve **30 Mbps ve 100 Mbps** upstream rate'leri tanımlar. DSL network'lerinde olduğu gibi, maksimum gerçekleştirilebilir rate, daha düşük kısıtlı data rate'ler veya medya bozuklukları nedeniyle gerçekleşmeyebilir.

Cable Internet access'in önemli bir karakteristiği, bunun bir **shared broadcast medium** olmasıdır. 
Özellikle, head end tarafından gönderilen her packet downstream'ta her eve giden her link üzerinden travel eder; ve bir home tarafından gönderilen her packet upstream channel'da head end'e gider. 
Bu nedenle, eğer birkaç kullanıcı aynı anda downstream channel'da bir video dosyası indiriyorsa, her kullanıcının aldığı gerçek rate, toplam cable downstream rate'inden önemli ölçüde daha düşük olacaktır. 
Diğer yandan, eğer sadece birkaç aktif user varsa ve hepsi Web surfing yapıyorsa, o zaman her kullanıcı tam cable downstream rate'inde Web sayfaları alabilir, çünkü kullanıcılar nadiren tam olarak aynı anda bir Web sayfasına request ederler. 
Upstream channel da shared olduğu için, transmissions'ı koordine etmek ve collisions'dan kaçınmak için bir **distributed multiple access protocol** gereklidir. 

> İşte DSL vs Cable'in en kritik farkı burada: DSL **paylaşımsız** bir hat kullanır — senin hattın sana aittir, komşunun indirmesi seni etkilemez. Ama Cable **shared broadcast medium**'dur — tüm mahalle aynı coaxial cable'i paylaşır. Akşam prime time'da herkes Netflix açarsa, senin hızın düşer. Bu yüzden "contention ratio" (paylaşım oranı) çok önemli. Production'da bir kullanıcı "akşamları Internet yavaşlıyor" diyorsa ve Cable kullanıyorsa, sebep muhtemelen bu. DOCSIS 3.1 ve sonrasıyla bu biraz iyileşti ama fiziksel limit var. Ayrıca CMTS = DSLAM'in karşılığı, bunu unutma. Upstream shared olduğu için CSMA/CD veya benzeri distributed multiple access protocol kullanılır.

## FTTH (Fiber to the Home)

DSL ve cable network'ler şu anda ABD'deki ikametlerin geniş bant access'in çoğunluğunu temsil etse de, daha yüksek hızlar sağlayan yükselen bir teknoloji **fiber to the home (FTTH)**'dir [Fiber Broadband 2025 - https://fiberbroadband.org/2025/12/16/fiber-broadband-association-reports-historic-fiber-deployment-highs/]. İsmi de ima ettiği gibi, FTTH konsepti basittir — CO'dan doğrudan eve bir **optical fiber path** sağlar. FTTH potansiyel olarak **gigabits per second** aralığında Internet access rate'leri sağlayabilir.

CO'dan evlere optical distribution için birkaç rekabetçi teknoloji vardır. En basit optical distribution network, her ev için CO'dan bir fiber çıkaran **direct fiber**'dir. 
Daha yaygın olarak, CO'dan çıkan her fiber aslında birçok ev tarafından paylaşılır; fiber, evlere nispeten yaklaşana kadar müşteriye özel ayrı fiber bağlantılarına bölünmez. 
Bu splitting'i gerçekleştiren iki rekabetçi optical-distribution network mimarisi vardır: **active optical networks (AONs)** ve **passive optical networks (PONs)**. AON temelde switched Ethernet'tir, ki bu ileride tartışılacaktır.

Burada, Verizon'un FiOS servisinde kullanılan **PON**'u kısaca tartışalım. Aşağıdaki şema PON distribution mimarisini kullanarak FTTH'yi gösteriyor. 
Her evin bir **optical network terminator (ONT)**'si vardır, bu özel optical fiber ile bir komşu splitter'a bağlıdır. Splitter, birkaç evi (tipik olarak **100'den az**) tek bir shared optical fiber üzerinde birleştirir, bu fiber telco'nun CO'sundaki bir **optical line terminator (OLT)**'a bağlanır. OLT, optik ve elektrik sinyalleri arasında dönüştürme yaparak bir telekom router aracılığıyla İnternet’e bağlanır. 
Evde, kullanıcılar bir home router'ı (tipik olarak wireless router) ONT'ye bağlar ve bu home router üzerinden Internet'e erişir. 
PON mimarisinde, OLT'den splitter'a gönderilen tüm packet'ler splitter'da **çoğaltılır** (bir cable head end'e benzer şekilde).

## FTTH Internet Access

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│    [Home 1]        [Home 2]        [Home 3]                                 │
│       🏠             🏠             🏠                                      │
│       │              │              │                                       │
│    [ONT]          [ONT]          [ONT]                                      │
│       │              │              │                                       │
│       └──────────────┼──────────────┘                                       │
│                      │                                                      │
│              [Optical splitter]                                             │
│                      │                                                      │
│                      │                                                      │
│                   [Optical fibers]                                          │
│                      │                                                      │
│                      ▼                                                      │
│                   [OLT]                                                     │
│              (Optical Line                                                  │
│               Terminator)                                                   │
│                      │                                                      │
│                      │                                                      │
│                      ▼                                                      │
│    [Central office]──┴──► [Internet]                                        │
│       🏢                    (◯)                                             │
│                                                                             │
│    ONT = Optical Network Terminator (ev tarafı)                             │
│    OLT = Optical Line Terminator (CO tarafı)                                │
│    Splitter = Passive optical splitting (güç gerektirmez!)                  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Fixed Wireless Internet (FWI)

**Fixed wireless Internet (FWI)** da popüler bir Internet access teknolojisi haline geldi. FWI sadece high-speed şekilde ikametine access sağlamakla kalmaz, aynı zamanda telco'nun CO'sundan eve kadar pahalı ve arıza eğilimli cabling kurulumunu da gerektirmez. **5G fixed wireless** ile, beam-forming teknolojisi kullanılarak, data provider'ın baz istasyonundan evdeki bir modem'e wireless olarak gönderilir. Bir WiFi wireless router modem'e bağlanır (muhtemelen birlikte paketlenmiş), tıpkı bir WiFi wireless router'ın cable veya DSL modem'e bağlanması gibi.

## LEO Satellites - Düşük Yörünge Uyduları

DSL, cable, FTTH ve FWI'ye ek olarak, **low-earth orbit (LEO) satellites** giderek artan şekilde geniş bant Internet access için kullanılıyor, özellikle kırsal ve uzak alanlarda. SpaceX'in **Starlink** gibi şirketler, büyük uydu takımyıldızları konuşlandırıyor; “jeostasyonel uydular”a (Jeostasyoner uydular, ekvator üzerinde yaklaşık 35.786 kilometre yükseklikte, Dünya ile aynı hızda dönen ve yer sabit kalan özel araçlardır. Bu uydular haberleşme, televizyon yayını ve meteoroloji alanlarında kullanılır) göre çok daha düşük sinyal yayılma gecikmeleri ile high-speed access sağlıyorlar.

> LEO vs jeostasyonel farkı önemli. Jeostasyonel uydu ~35.786 km yükseklikte, gidiş-dönüş propagation delay ~250-300ms. LEO uydu (Starlink gibi) ~550 km yükseklikte, delay ~20-40ms. Online oyun ve video conference için bu fark gece-gündüz. Ayrıca FTTH'de PON mimarisinin "passive" olması önemli: splitter güç gerektirmez, sadece ışığı böler. Bu, CO'dan eve kadar aktif cihaz olmadığı için daha az arıza demek. AON ise switched Ethernet, yani aktif cihazlar var. Production'da "fiber mi çekelim?" diye sorulursa, PON daha ucuz ve yaygın, AON daha esnek ama daha pahalı. 

## Ethernet and WiFi

Corporate ve university campus'lerde, ve giderek artan şekilde home settings'te, bir **local area network (LAN)** bir end system'i edge router'a bağlamak için kullanılır. 
Birçok LAN teknolojisi olmasına rağmen, **Ethernet** corporate, university ve home networks'te by far en yaygın access technology'dir. 
Ethernet kullanıcıları bir Ethernet switch'e bağlanmak için **twisted-pair copper wire** kullanır. Ethernet switch veya birbiriyle bağlı böyle switch'lerden oluşan bir network, daha sonra daha büyük Internet'e bağlanır. 
Ethernet access ile, kullanıcılar tipik olarak Ethernet switch'e **100 Mbps ila onlarca Gbps** access'e sahiptir; oysa server'lar **1 Gbps ila 10 Gbps** access'e sahip olabilir.

Ancak giderek artan şekilde, insanlar laptop'lardan, akıllı telefon'lardan, tablet'lerden ve diğer "nesnelerden" wireless olarak Internet'e erişiyor. 
Bir **wireless LAN** ortamında, wireless kullanıcılar packet'leri bir **access point**'e iletir/alır ki bu access point enterprise'un network'üne bağlıdır (büyük olasılıkla wired Ethernet kullanarak), bu da sırayla wired Internet'e bağlanır. 
Bir wireless LAN kullanıcısı tipik olarak access point'in birkaç on metre içinde olmalıdır. **IEEE 802.11** teknolojisine dayalı wireless LAN access, daha samimi adıyla **WiFi**, şimdi neredeyse her yerde — üniversiteler, business office'lar, kafeler, havalimanları, evler ve hatta uçaklarda. 802.11 bugün **100 Mbps'ten daha fazla** shared transmission rate sağlar.

Ethernet ve WiFi access network'leri ilk olarak enterprise (corporate, university) settings'te deploy edilmiş olsa da, bunlar aynı zamanda home network'lerin de yaygın component'leridir. 
Birçok home, broadband ikamet yeri access'i (yani cable modem veya DSL) bu ucuz wireless LAN teknolojileriyle birleştirerek güçlü home network'ler oluşturur.  
Bu home network, mutfaktan arka bahçe'ye ordan yatak odalarına dolaşan bir **taşınabilir laptop**, birden fazla Internet'e bağlı **ev aletleri**, aynı zamanda bir **wired PC**'den oluşur; bir **base station** (wireless access point) ki bu evdeki wireless PC ve diğer wireless cihazlarla iletişim kurar; ve wireless access point'i, diğer wired home cihazlarını Internet'e bağlayan bir **home router**'dan oluşur.

## Ethernet Internet Access

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│    [PC]              [PC]              [PC]              [Server]           │
│     💻                💻                💻                🖥️                │
│      │                │                │                  │                 │
│      │ 1 Gbps         │ 1 Gbps         │ 1 Gbps           │                 │
│      │                │                │                  │                 │
│      └────────────────┴────────────────┴──────────────────┘                 │
│                              │                                              │
│                        [Ethernet switch]                                    │
│                              │                                              │
│                              │                                              │
│                              ▼                                              │
│                        [Kurumsal router]                                    │
│                              │                                              │
│                              │                                              │
│                              ▼                                              │
│                "Kurumun İnternet Servis Sağlayıcısına"                      │
│                                                                             │
│    Users: 100 Mbps - tens of Gbps                                           │
│    Servers: 1 Gbps - 10 Gbps                                                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

## A Typical Home Network

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         ┌─────────┐                                         │
│                         │   🏠    │                                         │
│                         │  EV     │                                         │
│                         │         │                                         │
│    ┌──────────┐    ┌────┴───┐     │     ┌──────────┐                        │
│    │ Laptop   │◄──►│ Wireless│    │     │ Thermostat│                       │
│    │          │        AP    │    │     │    🌡️    │                        │
│    │   💻     │    │  ⬆️     │    │     │          │                        │
│    └──────────┘    └────┬───┘     │     └──────────┘                        │
│                         │         │                                         │
│    ┌──────────┐    ┌────┴───┐     │     ┌──────────┐                        │
│    │  Fridge  │◄──►│        │     │     │   PC     │                        │
│    │    🧊    │    │ Home   │◄────┼────►│ (wired)  │                        │
│    └──────────┘    │Router  │     │     │   💻     │                        │
│                    └───┬────┘     │     └──────────┘                        │
│                        │          │                                         │
│                        │          │                                         │
│                        └──────────┘                                         │
│                             │                                               │
│                             │                                               │
│                             ▼                                               │
│                      [Cable head end]                                       │
│                             │                                               │
│                             ▼                                               │
│                        [Internet]                                           │
│                           (◯)                                               │
│                                                                             │
│    Bu network, hane üyelerinin Internet'e broadband access sağlar;          │
│    bir üye mutfaktan arka bahçeye yatak odalarına dolaşabilir.              │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Wide-Area Wireless Access: 4G and 5G

iPhone'lar ve Android cihazlar gibi mobile devices, mesajlaşmak, online sosyal network'lerde fotoğraf ve video paylaşmak, mobile ödeme yapmak, film izlemek, müzik dinlemek, video conference yapmak ve hareket halindeyken çok daha fazlasını yapmak için kullanılıyor. Bu cihazlar, cep telefonu için kullanılan aynı wireless altyapı'yı kullanarak packet'leri mobil şebeke operatörü tarafından işletilen bir **baz istasyonu** aracılığıyla gönderir/alır. 
WiFi'dan farklı olarak, bir kullanıcının base station'ın sadece birkaç on metre değil, **birkaç kilometre** içinde olması yeterlidir.

Telecommunications şirketleri, **fourth-generation (4G)** wireless olarak adlandırılan şeylere muazzam yatırımlar yaptı; bu, gerçek dünya download hızlarında **60 Mbps'ye kadar** sağlar. 
Ancak daha yüksek hızlı wide-area access teknolojileri — **fifth-generation (5G)** wide-area wireless network'leri — şimdiden deploy ediliyor. 

> Burada kritik bir ayrım var: **LAN (Local Area Network)** vs **WAN (Wide Area Network)**. Ethernet ve WiFi LAN teknolojileridir — kısa mesafe, yüksek hız, düşük gecikme. 4G/5G ise WAN teknolojileridir — uzun mesafe (kilometrelerce), mobil altyapı, daha yüksek gecikme. Bir sınavda "Neden ofiste WiFi kullanıyoruz, 5G değil?" diye sorarlarsa, cevap: WiFi daha hızlı, daha düşük gecikme, daha az tıkanıklık, ama kısa menzil. 5G ise uzun menzil, ama base station'a bağımlısın ve shared spectrum. Ayrıca home network mimarisini unutma: Home Router = NAT + DHCP + Switch + Access Point (çoğu modern cihaz hepsi bir arada). Production'da bir evde network sorunu varsa, "modem mi router mi?" ayrımını yapmak gerekir — cable head end'e giden cihaz modem, ev içi dağıtımı yapan router. Birçok insan bunları karıştırır.

# 1.2.2 Physical Media

Önceki konularda, Internet'teki en önemli network access teknolojilerinden bazılarının önbakışını verdik. 
Bu teknolojileri açıklarken, kullanılan physical media'yı da belirttik. Örneğin, HFC'nin fiber cable ve coaxial cable kombinasyonunu kullandığını söyledik. 
DSL ve Ethernet'in copper wire kullandığını söyledik. Ve mobile access network'lerin radio spectrum kullandığını söyledik. Bu konuda ise, Internet'te yaygın olarak kullanılan bu ve diğer transmission media'nın kısa bir önbakışını sunuyoruz.

Bir physical medium'ın ne anlama geldiğini tanımlamak için, bir bit'in kısa hayatını düşünelim. Bir bit'in bir end system'den, bir dizi link ve router'dan geçerek başka bir end system'e seyahat ettiğini hayal edin. 
Bu zavallı bit birçok kez tekme atılır ve birçok kez iletilir. Kaynak end system ilk olarak bit'i iletir; kısa süre sonra serideki ilk router bit'i alır; ilk router daha sonra bit'i iletir; ve kısa süre sonra serideki ikinci router bit'i alır; ve böyle devam eder. Böylece bit'imiz, kaynaktan hedefe seyahat ederken bir dizi **transmitter-receiver pair**'inden geçer. 
Her transmitter-receiver pair'i için, bit, bir **physical medium** üzerinde elektromanyetik dalgalar veya optik darbeler yoluyla iletilir. 
Physical medium birçok şekil ve form alabilir ve yol boyunca her transmitter-receiver pair'i için aynı tip olmak zorunda değildir.

Physical media örnekleri arasında **twisted-pair copper wire**, **coaxial cable**, **multimode fiber-optic cable**, **karasal radio spectrum** ve **uydu radio spectrum** bulunur. 
Physical media iki kategoriye ayrılır: **guided media(kılavuzlu medya)** ve **unguided media(kılavuzsuz medya)**. Guided media'da, dalgalar katı bir medium boyunca yönlendirilir; örneğin bir fiber-optic cable, bir twisted-pair copper wire veya bir coaxial cable. Unguided media'da, dalgalar atmosferde ve dış uzayda yayılır; örneğin bir wireless LAN'da veya bir dijital uydu kanalında.

Ancak çeşitli media tiplerinin karakteristiklerine girmeden önce, maliyetleri hakkında birkaç söz söyleyelim. Physical link'in (copper wire, fiber-optic cable vb.) “gerçek maliyet”i, diğer networking maliyetlerine kıyasla genellikle nispeten düşüktür. Özellikle, physical link'in kurulumuyla ilişkili işgücü maliyeti, malzemenin maliyetinden katlarca daha yüksek olabilir. 
Bu nedenle, birçok builder binadaki her odaya twisted pair, optical fiber ve coaxial cable kurar. Başlangıçta sadece bir ortam kullanılsa bile, yakın gelecekte başka bir ortam kullanılabileceği ihtimali yüksektir, ve bu yüzden gelecekte ekstra kablo çekmek zorunda kalmamak için para tasarrufu yapılır.

## Twisted-Pair Copper Wire

En ucuz ve en yaygın kullanılan guided transmission medium **twisted-pair copper wire**'dır. Yüz yılı aşkın bir süredir telephone network'lerinde kullanılmıştır. 
Aslında, telefon ahizesinden yerel telefon santraline kadar uzanan kablolu bağlantıların %99’undan fazlasında twisted-pair copper kullanılır. 
Çoğumuz evlerimizde (veya ebeveynlerimizin veya neneler-dedeler) ve çalışma ortamlarında twisted pair görmüşüzdür. 
Twisted pair, her biri yaklaşık **1 mm kalınlığında** olan iki yalıtımlı copper wire'dan oluşur; bunlar düzenli bir spiral desen şeklinde dizilir. 
Wire'lar(teller) birbirine bükülür (twisted) çünkü bu, yakındaki benzer pair'lerden gelen elektriksel parazit'i azaltır. 
Tipik olarak, birkaç pair bir koruyucu kalkan içine sarılarak bir cable'de birleştirilir. Bir wire pair, tek bir communication link oluşturur.

**Unshielded twisted pair (UTP)**, bir building içindeki computer network'ler için yaygın olarak kullanılır; yani **LAN'lar** için. 
Bugün twisted pair kullanan LAN'lar için data rate'leri **10 Mbps ila 10 Gbps** aralığındadır. Elde edilebilen data rate'ler, wire'ın kalınlığına ve transmitter ile receiver arasındaki mesafeye bağlıdır.

Fiber-optic teknolojisi 1980'lerde ortaya çıktığında, birçok insan twisted pair'i nispeten düşük bit rate'leri nedeniyle küçümsedi. Bazı insanlar hatta fiber-optic teknolojisinin twisted pair'i tamamen egale edeceğini düşündü.
Ama twisted pair kolay kolay pes etmedi. Modern twisted-pair teknolojisi, örneğin **category 6a cable**, yüz metre mesafelere kadar **10 Gbps** data rate'leri elde edebilir. 
Sonuçta, twisted pair **high-speed LAN networking** için dominant çözüm olarak ortaya çıktı.

Daha önce tartıştığımız gibi, twisted pair aynı zamanda ikamet yerine Internet access için de yaygın olarak kullanılır. 
Dial-up modem teknolojisinin twisted pair üzerinde **56 kbps**'ye kadar hızlarda access sağladığı görülmüş. 
Ayrıca **DSL (digital subscriber line)** teknolojisinin, ikamet yerindeki kullanıcıların twisted pair üzerinden Internet'e **onlarca Mbps** hızında erişmesini sağladığını da görülüyor (kullanıcılar ISP'nin central office'ine yakın yaşadığında).

>  **"İşçilik maliyeti > Malzeme maliyeti"**. Builder'lar her odaya her türlü kabloyu çeker çünkü gelecekte değiştirmek çok pahalı. Production'da bir datacenter veya ofis tasarlarken, "şu an ne kullanıyoruz" demek yerine "5-10 yıl sonra ne kullanacağız" diye düşünmek gerekir. Ayrıca twisted pair'in hâlâ dominant olması şaşırtıcı gelebilir ama Cat6a ile 10 Gbps alıyorsun, bu LAN için çoğu senaryoda yeterli. Ama unutmayın: mesafe önemli! 100 metre üzeri zayıflama artar, o yüzden switch'ler arası mesafe kritik. UTP = Unshielded Twisted Pair, STP = Shielded Twisted Pair. UTP daha ucuz ama EMI(elektriksel parazit)'ya daha açık. STP daha pahalı ama daha az parazitli. Sınavda "UTP neden yaygın?" diye sorarlarsa, "ucuz, esnek, yeterince hızlı, kolay kurulum" denilir.

## Coaxial Cable

Twisted pair gibi, coaxial cable de iki copper iletkenden oluşur, ancak bu iki iletken **concentric** (merkezdeki çekirdek ve etrafındaki örgü) şekildedir, parallel değil. 
Bu yapı ve özel yalıtım ve koruma ile, coaxial cable **yüksek data transmission rate'leri** elde edebilir. 
Coaxial cable kablolu televizyon sistemlerinde oldukça yaygındır. Daha önce gördüğümüz gibi, cable televizyon sistemleri yakın zamanda cable modem'lerle birleştirilerek ikamet yeri kullanıcılara **yüzlerce Mbps** hızında Internet access sağlamıştır. Cable televizyon ve cable Internet access'te, transmitter digital signal'i spesifik bir frequency band'a kaydırır ve ortaya çıkan analog signal, transmitter'dan bir veya daha fazla receiver'a gönderilir. 
Coaxial cable bir **guided shared medium** olarak kullanılabilir. Spesifik olarak, birkaç end system doğrudan cable'a bağlanabilir; her bir end system, diğer end system'ler tarafından gönderilen her şeyi alır.

> Coaxial cable'in "shared medium" olması kritiktir, Tüm mahalle aynı coaxial cable'i paylaşır. Bu yüzden cable Internet'te "privacy" konusu vardı — eskiden komşunun paketlerini sniff etmek mümkündü. Bugün DOCSIS 3.1 ile encryption var ama yine de shared medium mantığı değişmez. Ayrıca concentric yapı: içteki çekirdek (merkez iletken), etrafında dielektrik yalıtım, ardından örgülü koruma, en dışta da plastic jacket. Bu yapı EMI'ya karşı twisted pair'den çok daha dayanıklı. 75 ohm empedans'lıdır(Kelime anlamı olarak buradaki empedans, yüksek frekanslı sinyallerin (video veya internet verisi) kablo içinde ilerlerken karşılaştığı "elektriksel dalga direnci" veya daha teknik adıyla karakteristik empedanstır.) (twisted pair 100 ohm). Sınavlarda "coaxial neden shielding'i daha iyi?" diye sorarlarsa, "tam kapsayan örgü shield sayesinde dış elektromanyetik alanlar iç iletkeni etkilemez" demek doğrudur.

## Fiber Optics

Bir **optical fiber**, ince, esnek bir medium'dur ki **ışık darbeleri** iletir; her darbe bir bit'i temsil eder. Tek bir optical fiber, **onlarca hatta yüzlerce gigabit per second**'a kadar muazzam bit rate'leri destekleyebilir. 
Electromagnetic parazit'e karşı **immune**'dirler (bağışık), **100 kilometreye kadar** çok düşük 'sinyal zayıflaması'na sahiptirler ve **sniff** edilmeleri (dinlenmeleri) çok zordur. Bu karakteristikler fiber optics'i **tercih edilen uzun mesafe guided transmission medium** yapmıştır; özellikle yurtdışı link'ler için. Birçok uzun-mesafeli telephone network, ABD'de ve dünyanın başka yerlerinde artık sadece fiber optics kullanır. Fiber optics aynı zamanda Internet'in **backbone**'unda da yaygındır. Ancak, optical devices'ların — transmitter'lar, receiver'lar ve switch'ler gibi — **yüksek maliyet'i**, bunların kısa-süreli transport için deployment'ını engellemiştir; örneğin bir LAN'da veya ikamet yeri access network'ünde eve girerken.

**Optical Carrier (OC)** standard link hızları **51.8 Mbps ila 39.8 Gbps** aralığındadır; bu spesifikasyonlar sıklıkla **OC-n** olarak adlandırılır, burada link speed **n × 51.48 Mbps**'ye eşittir. Bugün kullanımda olan standartlar arasında **OC-1, OC-3, OC-12, OC-24, OC-48, OC-96, OC-192, OC-768** bulunur.

> Fiber'in üç süper gücü: **1) EMI'ya bağışık** — elektromanyetik parazit yok, yanında elektrik hattı geçse bile etkilenmez. **2) Düşük zayıflama** — 100 km'de bile sinyal zayıflamadan gider, bu yüzden deniz altı kablolar fiber. **3) Hard to tap** — fiberi dinlemek için fiziksel olarak keseceksin, bu da detect edilebilir. Ama dezavantajı: **optical devices pahalı** SFP, SFP+, QSFP modüller, DWDM sistemler... Bunlar binlerce dolar. Bu yüzden LAN'da twisted pair hâlâ dominant. OC-n hesaplaması: OC-1 = 51.84 Mbps (STM-0), OC-3 = 155.52 Mbps (STM-1), OC-48 = 2.488 Gbps (STM-16), OC-192 = 9.953 Gbps (STM-64). SDH/SONET terminolojisidir bu. Production'da "10G fiber" dediğin zaman aslında OC-192/STM-64 konuşuyorsun. Ayrıca "backbone" dediğimiz yer, ISP'lerin omurgası — orada fiber hâkim, copper yok.

## Karasal Radio Channels

Radio channels, electromagnetic spectrum'da signal taşır. Fiziksel wire kurulumu gerektirmedikleri için, duvarlardan geçebildikleri için, mobile kullanıcılara connectivity sağlayabildikleri için ve potansiyel olarak signal'i uzun mesafeler taşıyabildikleri için çekici bir medium'dur. Bir radio channel'ın karakteristikleri, “yayılma ortamı”na ve signal'in taşınacağı mesafeye önemli ölçüde bağlıdır. Çevresel hususlar arasında **path loss** ve **shadow fading** (signal bir mesafe boyunca ve engelleyici objelerin etrafından seyahat ederken sinyal gücü'nü azaltan), **multipath fading** (sinyalin nesnelerden yansıması nedeniyle) ve **parazit** (diğer transmission'lar ve electromagnetic signals nedeniyle) bulunur.

Yer üstü radio channels genel olarak üç grupta sınıflandırılabilir:

- Çok kısa mesafede çalışanlar (örneğin bir veya iki metre; wireless headset'ler, keyboard'lar ve medical devices gibi personal devices)
- Local area'da çalışanlar, tipik olarak on metrelerden birkaç yüz metreye kadar
- Wide area'da çalışanlar, onlarca kilometreye kadar 

> Radio channel'ların üç düşmanı var, bunları unutma: **1) Path loss** — mesafe arttıkça sinyal zayıflar. **2) Shadow fading** — bina, ağaç, duvar araya girerse sinyal kesilir veya yansır. **3) Multipath fading** — sinyal direkt gelir, duvardan yansıyarak gelir, yerden yansıyarak gelir... Bu çok sayıda yol birbiriyle çakışmaktadır, sinyal gücü dalgalanır. Bu yüzden wireless'ta "sinyal kesintisi" olur. Production'da WiFi kapsam sorunu yaşıyorsan, bir WiFi analyzer ile RSSI (Received Signal Strength Indicator) ölçersin. -30 dBm mükemmel, -67 dBm kullanılabilir, -80 dBm ve altı çöp. Ayrıca 2.4 GHz vs 5 GHz ayrımı: 2.4 daha uzun mesafe, duvarları daha iyi geçer ama daha fazla parazit. 5 GHz daha hızlı ama daha kısa menzil.

## Uydu Radio Channels

Bir iletişim uydusu, **yer istasyonları** olarak bilinen iki veya daha fazla yerdeki mikrodalga vericisini/alıcısını birbirine bağlar. Uydu, bir frequency band'ında transmission'ları alır, signal'i bir **repeater** kullanarak regenerates eder ve signal'i başka bir frequency'de iletir. İletişimde kullanılan iki tip uydu vardır: **jeostasyonel uydular** ve **düşük yörüngeli (LEO) uydular**.

**Jeostasyonel uydular**, Dünya üzerinde aynı noktanın üzerinde kalıcı olarak kalır. Bu sabit konum, uydunun Dünya yüzeyinin **36.000 kilometre** yukarısındaki bir yörüngeye yerleştirilmesiyle sağlanır. Yer istasyonundan uyduya ve tekrar yer istasyonuna uzanan bu muazzam mesafe, **280 milisaniyelik** önemli bir sinyal yayılma gecikmesine yol açar. Yine de, yüzlerce Mbps hızında çalışabilen uydu links, DSL veya cable-based Internet access'in olmadığı alanlarda sıklıkla kullanılır. Jeostasyonel uydular aynı zamanda **global positioning system (GPS)**'in de merkezi component'idir; birçok location-based Internet application buna dayanır.

**LEO uydular**, Dünya'ya çok daha yakın yerleştirilir ve Dünya üzerindeki bir noktanın üzerinde kalıcı olarak kalmazlar. Dünya'nın etrafında dönerler (tıpkı Ay gibi) ve birbirleriyle ve yer istasyonlarıyla iletişim kurabilirler. Jeostasyonel uydulara kıyasla, çok daha düşük bir gidiş-dönüş yayılma gecikmeleri vardır; yaklaşık **10 milisaniye**. Bir alana sürekli veri akışı sağlamak için, bir dizi uydunun yörüngeye yerleştirilmesi gerekiyor. Şu anda birçok alçak irtifa iletişim sistemi geliştirilme aşamasındadır. LEO satellite teknolojisi, özellikle kara tabanlı iletişim altyapısı tarafından kolayca hizmet verilemeyen uzak alanlarda Internet access için giderek artan şekilde kullanılmaktadır.

> İşte Jeostasyonel vs LEO'nun kritik farkları: **Jeostasyonel: 36.000 km, ~280ms delay.** Bu online oyun ve video conference için ölümcül. Ama TV broadcast için uygun çünkü tek uydu tüm bir kıtayı görür. **LEO: ~550 km, ~10ms delay.** Starlink gibi. Ama iletişim için yüzlerce uydu gerekir (Starlink'in 6.500 ile 7.000 uydusu var). Jeostasyonel "repeater" mantığı: uplink frequency'den alır, downlink frequency'ye çevirir. Bu FDMA (Frequency Division Multiple Access) sayesinde birden fazla yer istasyonu aynı uyduyu kullanabilir. BU ARADA KİTAPTA GPS aslında Jeostasyonel gösteriliyor lakin şöyle bi şey okudum MEO (Medium Earth Orbit, ~20.000 km) ama kitap burada Jeostasyonel ile ilişkilendirmiş. Production'da "uydu Internet" dediğin zaman, kırsal alanlarda DSL/Cable yoksa tek çare. Ama geçikme yüksek, bu yüzden real-time app'lerde kullanım zor. LEO bu sorunu çözüyor ama maliyet yüksek, uydu sayısı çok fazla.

---

# 1.3 The Network Core

Internet'in edge'ini inceledikten sonra, şimdi network core'a daha derinlemesine dalalım — yani Internet'in end systems'lerini birbirine bağlayan packet switches ve links'in oluşturduğu **mesh** (ağ). Aşağıda ki şema, network core'u kalın, gölgeli çizgilerle vurguluyor.

## Şema — The Network Core

```
┌─────────────────────────────────────────────────────────────────────────────┐
│   ┌──────────────┐                                                          │
│   │ Mobile       │     ┌════════════════════════════════════╗               │
│   │ Network      │     ║      National or Global ISP        ║               │
│   │  📱 🚗 🚦    │     ║    (◯)════(◯)════(◯)               ║              │
│   │     ⬆️       │     ║      ║      ║      ║               ║              │
│   │   (◯)────────┼─────╫──────╫──────╫──────╫───────────────╫──────┐       │
│   └──────────────┘     ║      ║      ║      ║               ║      │       │
│                        ║      ║      ║      ║               ║      │       │
│   ┌──────────────┐     ║  ┌───╫───┐  ║      ║  ┌────────────╫───┐  │       │
│   │ Home         │     ║  │ Local│  ║       ║  │ Datacenter ║   │  │       │
│   │ Network      │     ║  │ or   │  ║       ║  │ Network    ║   │  │       │
│   │ [💻📱🌡️🧊]   │     ║  │Regional│║      ║  │  [🖥️🖥️]    ║   │  │       │
│   │    (◯)───────┼─────╝  │ ISP  │  ║      ║  │     │       ║  │  │       │
│   └──────────────┘        │ (◯)  │  ║      ║  │  (◯)        ║  │  │       │
│                           └───┬──┘  ║      ║  └────────────╨───┘  │       │
│                               │     ║      ║                      │       │
│   ┌──────────────────┐        │     ║      ║      ┌────────────────┴──┐   │
│   │ Enterprise       │        │     ║      ║      │ Content Provider ║    │
│   │ Network          │        │     ║      ║      │ Network          ║    │
│   │ [💻💻💻📱📱🖥️]   │       │      ║      ║      │  (◯)            ║    │
│   │    (◯)──(◯)──(◯)│         │     ║      ║      └─────────────────┘    │
│   └──────────────────┘        │     ║      ║                             │
│                               └─────╩══════╩─────────────────────────────┘
└─────────────────────────────────────────────────────────────────────────────┘
```

## 1.3.1 Packet Switching

Bir network application'da, end systems birbirleriyle **messages** exchange eder. Messages, uygulama tasarımcısının istediği her şeyi içerebilir. 
Messages bir control function gerçekleştirebilir (örneğin, el sıkışma örneğimizdeki **"Merhaba"** mesajları) veya data içerebilir; örneğin bir e-mail message, bir JPEG image veya bir MP3 ses dosyası. 
Bir source end system'den bir destination end system'e mesaj göndermek için, source uzun mesajı'ı **packets** olarak bilinen daha küçük data parçacık'larına böler.

Source ve destination arasında, her packet **communication links** ve **packet switches** (iki predominant tip: **routers** ve **link-layer switches**) üzerinden travel eder. 
Packets, her communication link üzerinde link'in **full transmission rate**'inde iletilir. Yani, eğer bir source end system veya packet switch, **L bits**'lik bir packet'i transmission rate'i **R bits/sec** olan bir link üzerinden gönderiyorsa, packet'i iletme süresi **L/R seconds**'dir.

> Mesela şöyle, Transmission delay = Packet Length / Transmission Rate. Örneğin 1500 byte'lık (12000 bit) bir packet'i 1 Gbps link üzerinden göndermek: 12000 / 10^9 = 12 mikrosaniye. Ama aynı packet'i 1 Mbps link üzerinden göndermek: 12000 / 10^6 = 12 milisaniye. Arada 1000x fark var. Sınavlarda "bir packet'in link üzerinde geçiş süresi nedir?" diye sorarlarsa, propagation delay ile karıştırma. **Transmission delay** = paketi "push etmek" için geçen süre (L/R). **Propagation delay** = bit'in fiziksel olarak hattan gitmesi için geçen süre (mesafe/ışık hızı). İkisi farklı. Production'da bir darboğaz analizi yaparken, link'in transmission rate'ini ve queue'ların durumunu kontrol edersin. Eğer router buffer'ı doluysa, packet queue'da bekler — bu da **queuing delay**'e neden olur. L/R sadece "paketi hatta koyma" süresidir, queue'da bekleme dahil değil.

## Store-and-Forward Transmission

Çoğu packet switch, link'lerin input'larında **store-and-forward transmission** kullanır. 
Store-and-forward transmission, packet switch'in outbound link üzerinde packet'in ilk bit'ini iletmeye başlamadan önce **tüm packet'i alması** gerektiği anlamına gelir. 
Store-and-forward transmission'ı daha detaylı incelemek için, tek bir router ile bağlı iki end system'den oluşan basit bir network düşünelim, 
Bir router tipik olarak birçok sayıda link'e sahiptir, çünkü görevi gelen bir packet'i outgoing bir link'e switch etmektir; bu basit örnekte, router'ın oldukça basit bir görevi vardır: bir packet'i bir (input) link'ten tek bağlı diğer link'e transfer etmek.

## Store-and-Forward Packet Switching

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│    [Source]                    [Router]                  [Destination]      │
│       💻                         (◯)                        💻              │
│        │                          │                          │              │
│        │    ═══════════════►      │                          │              │
│        │    R bps                 │                          │              │
│        │                          │                          │              │
│        │  ┌───┐                   │                          │              │
│        │  │ 3 │                   │  ┌─────────────────┐     │              │
│        │  │ 2 │ ───────────────►  │  │      │                │              |
│        │  │ 1 │  (packet bits     │  │    Burada 1 paket     │              |
│        │  └───┘   geliyolar)      │  │    Bit diğerlerini,   |              │ 
│        │                          │  │    Bekliyor...        │              |
│        │                          │  └─────────────────┘     │              │
│        │                          │                          │              │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

Bu örnekte, source'un destination'a göndermek için üç packet'i var; her biri **L bits**'ten oluşuyor. Üstteki şemada gösterilen zaman anında, source packet 1'in bir kısmını iletmiş ve packet 1'in ön kısmı router'a ulaşmış durumda. 
Router store-and-forward kullandığı için, bu an itibarıyla router aldığı bit'leri iletemez; bunun yerine önce packet'in bit'lerini buffer'lamalı (yani **"store"**). 
Sadece router **tüm packet'in bit'lerini** aldıktan sonra, outbound link üzerinde packet'i iletmeye (yani **"forward"**) başlayabilir.

Store-and-forward transmission'a biraz daha içgörü kazanmak için, source'un packet'i göndermeye başladığı andan destination'ın tüm packet'i aldığı ana kadar geçen süreyi hesaplayalım. 
Burada propagation delay'i ihmal edeceğiz — bit'lerin tel üzerinden ışık hızına yakın bir hızda travel etmesi için geçen süre —. 
Source zaman 0'da iletmeye başlar; zaman **L/R** saniyesinde, source tüm packet'i iletmiştir ve router tüm packet'i almış ve store etmiştir (propagation delay olmadığı için). 
Zaman **L/R**'de, router tüm packet'i yeni aldığı için, outbound link üzerinde destination'a doğru packet'i iletmeye başlayabilir; zaman **2L/R**'de, router tüm packet'i iletmiştir ve destination tüm packet'i almıştır. Böylece, toplam delay **2L/R**'dir.

Eğer switch bunun yerine bit'leri geldikleri gibi hemen forward etseydi (önce tüm packet'i almadan), toplam delay **L/R** olurdu çünkü bit'ler router'da bekletilmezdi. Ama daha sonra tartışacağımız gibi, router'lar forward etmeden önce tüm packet'i **receive, store ve process** etmek zorundadır.

Şimdi, source'un ilk packet'i göndermeye başladığı andan destination'ın üç packet'in hepsini aldığı ana kadar geçen süreyi hesaplayalım. Daha önce olduğu gibi, zaman **L/R**'de router ilk packet'i forward etmeye başlar. Aynı zamanda zaman **L/R**'de, source tüm ilk packet'i göndermeyi bitirdiği için ikinci packet'i göndermeye başlayacaktır. Böylece, zaman **2L/R**'de destination ilk packet'i almıştır ve router ikinci packet'i almıştır. Benzer şekilde, zaman **3L/R**'de destination ilk iki packet'i almıştır ve router üçüncü packet'i almıştır. Son olarak, zaman **4L/R**'de destination tüm üç packet'i almıştır!

Şimdi, source'dan destination'a **N** link'ten oluşan bir path üzerinden bir packet göndermenin genel durumunu düşünelim; her link'in rate'i **R**'dir (böylece source ve destination arasında **N-1** router vardır). Yukarıdaki aynı mantığı uygulayarak, end-to-end delay'in şu olduğunu görürüz:

```
┌────────────────────────────────────────┐
│                                        │
│         d_end-to-end = N × (L/R)       │
│                                        │
└────────────────────────────────────────┘
```

Şimdi, **P** packet'in **N** link serisi üzerinden gönderildiğinde delay'in ne olacağını belirlemek isteyebilirsiniz.

> Router, paketin **tamamını** almadan bir bit bile forward etmez. Neden? Çünkü router paketin header'ını okumak zorunda — nereye gideceğini anlamak için. Ayrıca error checking yapar (CRC). Bu yüzden "cut-through switching" (geldikçe forward etme) daha hızlı gibi görünse de, modern router'lar store-and-forward kullanır çünkü güvenilirlik ve routing kararı için gerekli. Formül **d_end-to-end = N × (L/R)** — N link varsa, her link'te L/R transmission delay var. Ama bu sadece **transmission delay**, propagation delay ve queuing delay dahil değil. Sınavlarda "3 router'lı bir path'te 1 MB'lık bir dosya 1 Gbps link'te ne kadar sürede gider?" diye sorarlarsa, önce packet'lere böl, sonra N × L/R hesapla. Ama unutma: bu formül tek bir packet için. P packet için hesap yaparken, pipelining devreye girer — router bir packet'i forward ederken source bir sonrakini gönderiyor. Bu yüzden P packet için toplam delay ≈ (N + P - 1) × (L/R). Production'da bir traceroute çıktısındaki her hop, bir store-and-forward noktasıdır. Her router'da packet buffer'lanır, process edilir, sonra forward edilir. Bu yüzden latency = propagation + transmission + queuing + processing. Store-and-forward sadece transmission kısmını etkiler.

## Queuing Delays and Packet Loss

Her packet switch'in birden fazla link'i vardır. Her bağlı link için, packet switch'in bir **output buffer** (aynı zamanda **output queue** olarak da adlandırılır) vardır. 
Bu buffer, router'ın o link'e göndermek üzere olduğu packet'leri saklar. Output buffer'lar packet switching'te kilit rol oynar. 
Eğer gelen bir packet bir link'e iletilmesi gerekiyorsa ama o link başka bir packet'in iletimiyle meşgulse, gelen packet output buffer'da beklemek zorundadır. 
Böylece, store-and-forward delay'lere ek olarak, packet'ler output buffer **queuing delay**'leri yaşarlar. 
Bu delay'ler değişkendir ve network'teki tıkanıklık seviyesine bağlıdır. Buffer alanı sınırlı olduğu için, gelen bir packet buffer'ın tamamen dolu olduğunu fark edebilir. Bu durumda **packet loss** oluşur — ya gelen packet ya da zaten queue'da bekleyen packet'lerden biri **dropped** olur.

## Packet Switching

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│    [Host A]            [Router]                    [Router]                 │
│       💻                  (◯)                        (◯)                    │
│        │                  │                          │                      │
│        │ 100 Mbps         │                          │                      │
│        │ Ethernet         │                          │                      │
│        │                  │                          │                      │
│        │    ┌───┐         │  ┌─────────────────┐     │                      │
│        │    │ ▓▓│────────►│  │ Queue of packets│     │                      │
│        │    │ ▓▓│         │  │ waiting for     │     │                      │
│        │    └───┘         │  │ output link     │     │                      │
│        │                  │  │  ▓▓ ▓▓ ▓▓ ▓▓    │     │                      │
│        │                  │  └─────────────────┘     │                      │
│        │                  │           │              │                      │
│    [Host B]               │           │ 15 Mbps      │                      │
│       💻──────────────────┘           │              │                      │
│                                       ▼              │                      │
│                                 [Host C] [Host D] [Host E]                  │
│                                   💻       💻       💻                      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

Şema basit bir packet-switched network'ü gösteriyor. Host A ve B'nin Host E'ye packet gönderdiğini varsayalım. Host A ve B önce packet'lerini **100 Mbps Ethernet** link'leri üzerinden ilk router'a gönderir. 
Router daha sonra bu packet'leri **15 Mbps** link'e yönlendirir. Eğer kısa bir zaman aralığında router'a gelen packet'lerin geliş rate'i (bits per second'a çevrildiğinde) **15 Mbps'yi aşıyorsa**, router'da **tıkanıklık** oluşur çünkü packet'ler link üzerine iletilmeden önce link'in output buffer'ında kuyruk oluşturur. Örneğin, eğer Host A ve B aynı anda arka arkaya beşer packet gönderirse, bu packet'lerin çoğu kuyruk'da bir süre bekleyecektir. Bu durum aslında birçok günlük duruma tamamen benzer — örneğin bir banka için sırada beklemek veya bir gişenin önünde beklemek. 

## Forwarding Tables and Routing Protocols

Daha önce, bir router'ın bağlı communication link'lerinden birine ulaşan bir packet'i aldığını ve bu packet'i bağlı link'lerinden bir diğerine forward ettiğini söylemiştik. 
Ama router bu packet'i hangi link'e forward etmesi gerektiğini nasıl belirler? Packet forwarding aslında farklı şekillerde yapılır.

Internet'te, her end system'in **IP address** olarak adlandırılan bir adresi vardır. Bir source end system destination'a packet göndermek istediğinde, source packet'in header'ına destination'ın IP adresini ekler. 
Posta adresleri gibi, bu adres de **hiyerarşik bir yapıya** sahiptir. Bir packet network'teki bir router'a ulaştığında, router packet'in destination adresinin bir kısmını inceler ve packet'i komşu bir router'a forward eder. 
Daha spesifik olarak, her router'ın destination adreslerini (veya destination adreslerinin kısımlarını) o router'ın outbound link'lerine eşleyen bir **forwarding table**'ı vardır. 
Bir packet router'a ulaştığında, router adresi inceler ve bu destination adresi kullanarak forwarding table'ını arar, uygun outbound link'i bulur. Router daha sonra packet'i bu outbound link'e yönlendirir.

End-to-end routing süreci, harita kullanmayan ama bunun yerine yol tarifi sormayı tercih eden bir araba sürücüsüne benzer.

Örneğin, Ahmet İstanbul’dan Antalya, Kaş’taki Atatürk Caddesi No: 42 adresine gidiyor olsun.

İstanbul (Source): Ahmet önce mahallesindeki benzin istasyonuna gider ve Kaş, Antalya’daki Atatürk Caddesi No: 42 adresine nasıl gideceğini sorar. Benzin istasyonu görevlisi adresin Antalya kısmını çıkarır ve Ahmet’e hemen istasyonun yanından geçen O-4 / O-7 otoyoluna girip güneye devam etmesini söyler. Ayrıca Ahmet’e Afyon’a vardığında başka birine sorması gerektiğini belirtir.

Afyon (Ara Router / Hop): Ahmet otoyolu takip ederek Afyonkarahisar’a kadar sürer; orada başka bir benzin istasyonu görevlisine yol tarifi sorar. Bu görevli adresin Kaş kısmını çıkarır ve Ahmet’e Burdur üzerinden devam etmesini, Burdur’da tekrar yol sorması gerektiğini söyler.

Burdur (Ara Router / Hop): Burdur’daki benzin istasyonu görevlisi de adresin Kaş kısmını analiz eder ve Ahmet’e Fethiye/Kaş yönüne giden D635 karayoluna bağlanması gerektiğini söyler. Ahmet Kaş ilçe sınırından içeri girer.

Kaş İlçe Merkezi (Yerel Router): Ahmet Kaş mevkisindeki başka bir benzin istasyonu görevlisine gider. Bu sefer görevli adresin Atatürk Caddesi kısmını çıkarır ve Ahmet’e merkeze inip Atatürk Caddesi’ne ulaşması için izlemesi gereken yerel caddeleri söyler.

Atatürk Caddesi (En Yakın Node/Hop): Ahmet Atatürk Caddesi’ne ulaştığında, kaldırımda yürüyen bir kuryeye hedefine nasıl ulaşacağını sorar. Kurye adresin No: 42 kısmını çıkarır ve binayı doğrudan gösterir.

Ahmet sonunda nihai destination’ına ulaşır.

Bu analojide, yol boyunca tarif veren benzin istasyonu görevlileri ve kurye birer router’a karşılık gelir. Her biri paketin (arabanın) üzerindeki adres bilgisini katman katman inceleyerek bir sonraki hop’a yönlendirir.

Bir router'ın packet'in destination adresini kullanarak forwarding table'ını index'lediğini ve uygun outbound link'i belirlediğini öğrendik. 
Ama bu ifade bir başka soruyu gündeme getiriyor: Forwarding table'lar nasıl oluşturulur? Her router'da elle mi configure edilirler, yoksa Internet daha otomatik bir prosedür mü kullanır? Ama şimdilik iştahımızı kabartmak için, Internet'in forwarding table'ları otomatik olarak ayarlamak için kullanılan bir dizi özel **routing protocol**'ü olduğunu not edelim. Örneğin bir routing protocol, her router'dan her destination'a **en kısa path'i** belirleyebilir ve en kısa path sonuçlarını router'lardaki forwarding table'ları configure etmek için kullanabilir.

> İşte burada iki kritik kavram: **Forwarding** ve **Routing**. Forwarding = local action. Router gelen pakete bakar, forwarding table'dan çıkış portunu bulur, gönderir. Milisaniyeler içinde gerçekleşir. Routing = global process. Tüm network'ün topolojisini bilerek en iyi path'i hesaplar. Dakikalar/saatler içinde gerçekleşir. "Forwarding table" data plane'de (hızlı, hardware), "Routing protocol" control plane'de (yavaş, software) çalışır. Bu ayrımı unutma, SDN (Software-Defined Networking) konseptinin temeli bu. Ayrıca queuing delay = tıkanıklık göstergesidir. Production'da `ping` ile RTT ölçüyorsun, birden bire artarsa router queue'ları doluyor demektir. `show interfaces` ile output drops ve queue depth kontrol edersin. Packet loss = TCP throughput düşer (congestion window küçülür), UDP ise paketi kaybeder. Sınavlarda "router neden packet drop eder?" diye sorarlarsa, "buffer overflow" diyebiliriz. RED (Random Early Detection) ve ECN gibi mekanizmalar bunu önlemek için var. Ayrıca Ahmet'in yolculuğundaki "hiyerarşik adres çıkarma" mantığı, IP adreslerinin CIDR (Classless Inter-Domain Routing) yapısına tamamen uyar: Router en spesifik match'e bakar. Bu, forwarding table lookup'ın temelidir.

# 1.3.2 Circuit Switching

Links ve switches'ten oluşan bir network üzerinden data taşımanın iki temel yaklaşımı vardır: **circuit switching** ve **packet switching**. Önceki konuda packet-switched network'leri ele aldık, şimdi dikkatimizi circuit-switched network'lere çeviriyoruz.

Circuit-switched network'lerde, end systems arasındaki communication session süresi boyunca path üzerinde ihtiyaç duyulan kaynaklar (buffer'lar, link transmission rate) **reserved** (ayrılmış) edilir. Packet-switched network'lerde ise bu kaynaklar **reserved değildir**; bir session'ın mesajları kaynakları ihtiyaç duyduklarında kullanır ve sonuç olarak bir communication link'e erişim için beklemek zorunda kalabilirler (yani **queue**). 
Basit bir analoji olarak, iki restoran düşünelim: biri rezervasyon gerektirir, diğeri ne rezervasyon ister ne de kabul eder. Rezervasyon gerektiren restoran için, evden çıkmadan önce arayıp rezervasyon yaptırma zahmetine katlanmamız gerekir. Ama restorana vardığımızda, prensip olarak hemen oturur ve siparişimizi veririz. Rezervasyon gerektirmeyen restoran için, masa rezerve etmekle uğraşmamıza gerek yoktur. Ama restorana vardığımızda, oturmadan önce bir masa için beklememiz gerekebilir.

Geleneksel telefon network'leri, circuit-switched network'lerin örnekleridir. Bir kişinin telefon network'ü üzerinden başka birine bilgi (ses veya faks) göndermek istediğinde neler olduğunu düşünelim. 
Gönderen bilgiyi göndermeden önce, network sender ve receiver arasında bir connection kurmalıdır. Bu, sender ve receiver arasındaki path üzerindeki switch'lerin o connection için connection state'ini sürdürdüğü **bona fide** (gerçek) bir connection'dır. Telephony jargonunda, bu connection'a bir **circuit** denir. Network circuit'ı kurduğunda, aynı zamanda connection süresi boyunca network link'lerinde sabit bir transmission rate'i de reserve eder (her link'in transmission capacity'sinin bir kısmını temsil eder). Belirli bir transmission rate bu sender-to-receiver connection için reserve edildiğinden, sender data'yı receiver'a **garantili sabit hızda** transfer edebilir.

Aşağıda bir circuit-switched network'ü gösteriyor. Bu network'te, dört circuit switch birbirine dört link ile bağlıdır. Bu link'lerin her biri dört circuit'e sahiptir, böylece her link dört eşzamanlı connection'ı destekleyebilir. Host'lar (örneğin PC'ler ve workstation'lar) her biri doğrudan switch'lerden birine bağlıdır. İki host iletişim kurmak istediğinde, network iki host arasında dedicated yani özel bir **end-to-end connection** kurar. Böylece, Host A'nın Host B ile iletişim kurması için, network önce iki link'in her birinde bir circuit reserve etmelidir. Bu örnekte, dedicated end-to-end connection ilk link'teki ikinci circuit'i ve ikinci link'teki dördüncü circuit'i kullanır.

##  Circuit-Switched Network

```
┌─────────────────────────────────────────────────────────────────────────────┐
│    [Host A]                                    [Host B]                     │
│       💻                                          💻                         │
│        │                                          │                         │
│        │                                          │                         │
│        └──────────┐                    ┌──────────┘                         │
│                   (◯)══════════════════(◯)                                  │
│                   [SW1]    Link 1      [SW2]                                 │
│                     │    4 circuits      │                                   │
│                     │                    │                                   │
│                     │   Circuit 2 used   │                                   │
│                     │   for A→B          │                                   │
│                     │                    │                                   │
│                    (◯)══════════════════(◯)                                  │
│                   [SW3]    Link 2      [SW4]                                 │
│                     │    4 circuits      │                                   │
│                     │                    │                                   │
│                     │   Circuit 4 used   │                                   │
│                     │   for A→B          │                                   │
│                     │                    │                                   │
│        ┌──────────┘                      └──────────┐                        │
│        │                                            │                        │
│    [Host C]                                    [Host D]                     │
│       💻                                          💻                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

Her link dört circuit'e sahip olduğu için, end-to-end connection tarafından kullanılan her link için connection, connection süresi boyunca link'in toplam transmission capacity'sinin **dörtte birini** alır. Böylece, örneğin, komşu switch'ler arasındaki her link 1 Mbps transmission rate'e sahipse, her end-to-end circuit-switch connection **250 kbps** dedicated transmission rate alır.

Buna karşılık, bir host'un packet-switched bir network üzerinden (Internet gibi) başka bir host'a packet göndermek istediğinde neler olduğunu düşünelim. Circuit switching'te olduğu gibi, packet bir dizi communication link üzerinden iletilir. Ama circuit switching'ten farklı olarak, packet **hiçbir link kaynağını reserve etmeden** network'e gönderilir. Eğer link'lerden biri, aynı anda başka packet'lerin de iletilmesi gerektiği için tıkanık ise, o zaman packet transmission link'in gönderici tarafındaki bir buffer'da beklemek zorunda kalacak ve bir delay yaşayacaktır. Internet packet'ları zamanında teslim etmek için elinden geleni yapar, ancak herhangi bir **garanti vermez**.

> İşte packet switching vs circuit switching'in kritik noktaları burası. **Circuit switching = garanti, ama israf.** Rezervasyon yaptın, masanın boş da kalsa o masa senin. Telefon konuşması sırasında sessiz kalırsan, o bandwidth çöpe gidiyor. **Packet switching = paylaşım, ama garanti yok.** Masaya oturan varsa beklersin, ama boş masaları kimseye ayırmıyoruz, herkes kullanabiliyor. Bu yüzden Internet packet switching kullanır — daha verimli. Ama VoIP veya video conference gibi real-time uygulamalarda QoS (Quality of Service) gerekebilir, işte o zaman circuit switching mantığına yaklaşan mekanizmalar (IntServ, DiffServ) devreye girer. 250 kbps hesabı: 1 Mbps / 4 circuit = 250 kbps. Bu **FDM (Frequency Division Multiplexing)** veya **TDM (Time Division Multiplexing)** ile yapılır. TDM'de her circuit farklı time slot'u kullanır, FDM'de farklı frequency band'ı. Geleneksel telefon hizmetleri TDM kullanır (64 kbps per circuit, E1/T1 hatlar). Sınavlarda "neden Internet packet switching kullanıyor?" diye sorarlarsa, "kaynak kullanımı daha verimli, ani trafik artışına uygun,  hataya dayanıklı" diyebiliriz. "Circuit switching nerede kullanılır?" → "Telephony, dedicated leased lines, real-time garanti gereken yerler."
