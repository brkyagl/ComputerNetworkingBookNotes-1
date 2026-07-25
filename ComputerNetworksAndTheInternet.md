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
