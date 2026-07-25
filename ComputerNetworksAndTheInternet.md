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

