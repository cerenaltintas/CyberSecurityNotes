## Sistem Dosyaları

Program Dosyaları:

- \Program Files: 64-bit Windows'ta 64-bit programlar için.
- \Program Files (x86): 64-bit Windows'ta 32-bit programlar için.
- \ProgramData: Kullanıcıdan bağımsız program verileri için.

Kullanıcı Verileri:

- \Users: Her kullanıcı için bir profil klasörü içerir.
- \Public: Kullanıcılar arasında paylaşılan dosyalar için.
- [kullanıcı_adı]\AppData: Kullanıcı başına uygulama verileri ve ayarları için.

Windows Sistemi:

- \Windows: Windows'un kendisini içerir.
- \System, \System32, \SysWOW64: Windows çekirdek bileşenlerini ve dinamik bağlantı kitaplıklarını (DLL'lerini) içerir.
- \WinSxS: Windows bileşen deposu (güncellemeler ve hizmet paketleri dahil).

Diğer:

- \PerfLogs: Windows performans kayıtları (varsayılan olarak boş).

## Dosya Sistemi

Windows ilk çıktığında, FAT (File Allocation Table) dosya sistemini kullanıyordu. FAT, basit ve uyumlu bir dosya sistemiydi, ancak büyük dosyaları (4 GB'tan büyük) desteklemiyordu ve gelişmiş güvenlik özellikleri sunmuyordu.

1993 yılında Windows NT 3.1 ile birlikte NTFS (New Technology File System) dosya sistemi tanıtıldı. NTFS, FAT'ın eksikliklerini gidermek için tasarlanmıştı. Büyük dosyaları destekler, dosya ve klasör izinleri gibi gelişmiş güvenlik özellikleri sunar ve disk alanını daha verimli kullanır. NTFS günümüzde Windows'un varsayılan dosya sistemidir.

2000'li yılların başında USB flash sürücüler gibi taşınabilir depolama aygıtları popüler hale geldi. FAT32 dosya sistemi, taşınabilir depolama aygıtları için ideal bir çözüm olarak ortaya çıktı. FAT32, FAT'tan daha gelişmiş bir dosya sistemidir ve 4 GB'tan büyük dosyaları destekler.

2006 yılında Windows Vista ile birlikte exFAT (Extended File Allocation Table) dosya sistemi tanıtıldı. exFAT, FAT32'nin yerini alması için tasarlanmıştır ve 4 GB'tan büyük dosyaları destekler. NTFS kadar gelişmiş olmasa da, daha basittir ve taşınabilir depolama aygıtları için daha uygundur.

### NTFS ve FAT

NTFS bir journaling (günlüklü) dosya sistemi olarak bilinir. Bir arıza durumunda, dosya sistemi bir günlük dosyasında saklanan bilgileri kullanarak diskteki klasörleri/dosyaları otomatik olarak onarabilir. Bu işlev FAT ile mümkün değildir.

NTFS, Windows'un depolama ihtiyaçlarının arttığı bir dönemde önemli bir gelişmeydi ve FAT'ın birçok sınırlamasını aştı:

Güvenlik: NTFS, dosya erişimini kontrol etmek için izinler sunarak daha sağlam bir güvenlik modeli sundu.

Ölçeklenebilirlik: NTFS, daha büyük dosya boyutlarını ve sürücü kapasitelerini destekleyerek daha modern depolama ihtiyaçlarına uyum sağladı.

Güvenilirlik: NTFS, veri bütünlüğünü ve kurtarmayı geliştirmek için günlük tutma özelliğini sundu.

Özellikler: NTFS, dosya sıkıştırma, şifreleme ve disk kotaları gibi ek işlevler sunarak depolama yönetimini ve güvenliğini geliştirdi.

Sonuç olarak NTFS, FAT'a kıyasla daha modern, güvenli ve ölçeklenebilir bir dosya sistemidir ve Windows'un temel bir bileşeni olmaya devam etmektedir.

### Erişim Kontrol Listesi (Access Control List)

ACL, Erişim Kontrol Listesi (Access Control List) anlamına gelir. Bu liste, bir bilgisayar sistemindeki bir kaynağa (dosya, klasör, yazıcı, ağ kaynağı vb.) kimlerin erişebileceğini ve hangi erişim izinlerine sahip olduklarını belirler.

ACL, sistem yöneticilerinin ve kullanıcıların hassas verileri korumasına ve yalnızca yetkili kişilerin belirli kaynaklara erişebilmesini sağlamasına olanak tanır.

NTFS disklerde, dosya ve klasörlerin erişim izni ayarlanabilir.

Ayarlanabilir izinler şunlardır:

- Tam denetim
- Değiştirme
- Okuma ve yürütme
- Klasör içeriğini listeleme
- Okuma
- Yazma

Erişim Kontrol Listesini görüntüleme/değiştirme

1. Dosya veya klasöre sağ tıklayın
2. Menüden Özellikler'i seçin.
3. Özellikler içinde, Güvenlik sekmesine tıklayın
4. Grup veya kullanıcı adları listesinde, izinlerini görüntülemek istediğiniz kullanıcıyı, bilgisayarı veya grubu seçin.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/acl-f2ab97d69.webp)

### Alternatif Veri Akışları (ADS)

NTFS dosya sistemleri dünyasında, Alternatif Veri Akışları (ADS) dosyaların içindeki gizli bölmeler gibi davranır. NTFS, dosyaların gördüğünüz normal verilerden daha fazlasına sahip olmasına izin verir.

Avantajlar:

ADS uygulamalar için meşru amaçlar sunar. Örneğin programlar:

- Görüntüler için küçük resim önizlemeleri veya belge özetleri gibi meta veriler.
- Dosya ile ilişkili kritik olmayan bilgiler.
- İndirilen dosyalar hakkında güvenlik bilgileri.
- Dosyanın nereden indirildiği vb.

gibi verileri kullanabilir.

Güvenlik Riskleri:

ADS geçerli kullanım alanlarına sahip olsa da, kötüye de kullanılabilirler.

Kötü amaçlı yazılımlar ADS'den yararlanarak bir dosyanın içine kötü amaçlı kod gizleyebilir ve bu da geleneksel yöntemlerle tespit edilmesini zorlaştırabilir.

### Gölge Kopya (Shadow Copy)

Gölge kopya, Windows'ta bulunan ve belirli bir zamanda bir dosyanın veya klasörün kopyasını oluşturmanıza ve saklamanıza olanak tanıyan bir özelliktir. Bu, dosyaları veya klasörleri yanlışlıkla silmeniz veya değiştirmeniz durumunda geri yüklemenize yardımcı olur.

Her ne kadar detaylı incelemeyecek olsak da bilinmelidir ki bu özellik fidye saldırılarından korunmanın bir yolu değildir.

Kötü amaçlı yazılım geliştiricileri, Windows'ta gölge kopya özelliğinin farkındadır ve bu dosyaları arayıp silmek için kod yazabilirler. Bu durum, çevrimdışı bir yedeklemenizin olmadığı takdirde bir fidye yazılımı saldırısından kurtulmayı imkansız hale getirebilir.

## Kullanıcı Yapısı

Windows, kullanıcıları farklı erişim haklarına sahip kategorilere ayıran bir kullanıcı yapısı kullanır. En yaygın iki kategori şunlardır:

Yöneticiler:

- Bilgisayarda tam kontrol sahibidirler.
- Sistem ayarlarını değiştirebilir, programları yükleyebilir ve kaldırabilir, diğer kullanıcı hesaplarını yönetebilir ve diğer birçok işlemi gerçekleştirebilirler.
- Yöneticiler, hassas sistem dosyalarını ve verileri değiştirme yeteneğine sahip olduklarından, bu rol yalnızca güvenilir kişilere atanmalıdır.

Standart Kullanıcılar:

- Bilgisayarı kullanmak için temel izinlere sahiptirler.
- Programları çalıştırabilir, dosyaları açabilir ve düzenleyebilir, internete erişebilirler.
- Sistem ayarlarını değiştiremez, programları yükleyemez veya kaldıramaz ve diğer kullanıcı hesaplarını yönetemezler.
- Standart kullanıcılar, bilgisayarın güvenliğini ve istikrarını korumaya yardımcı olmak için sınırlı izinlere sahiptir.

Diğer Kullanıcı Türleri:

- Konuk: Bilgisayarı geçici olarak kullanmak için sınırlı izinlere sahip olan kullanıcı türüdür.
- Belirtilmiş Erişim: Belirli programları veya dosyaları kullanmak için özel izinlere sahip olan kullanıcı türüdür.

### Kullanıcı Hesaplarını Yönetme:

Hesapları yönetmenin en hızlı yolu Yerel Kullanıcı ve Gruplar'dan düzenleme yapmaktır.

Başlat menüsüne PowerShell yazıp açın

Gelen ekrana

```auto
lusrmgr
```

komutu yazın.

Gelen pencereden, yerel kullanıcıları ve grupları yönetebilirsiniz.

Hesap türlerini değiştirebilir. Hesapları aktifleştirip/devre dışı bırakabilir ve çok daha fazlasını yapabilirsiniz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/lusrmgr-1c06f8138.webp)

### Kullanıcı Hesabı Denetimi (User Account Control)

UAC, Kullanıcı Hesabı Denetimi (User Account Control) olarak adlandırılır ve Microsoft Windows işletim sistemlerinde yerleşik bir güvenlik özelliğidir. UAC, bilgisayarınızda yönetici yetkisi gerektiren işlemleri gerçekleştirmeden önce size onay isteyerek çalışır. Bu, yetkisiz değişikliklerden veya zararlı yazılımların yüklenmesinden kaynaklanan hataları önlemeye yardımcı olur.

Bir program yönetici ayrıcalıkları gerektiren bir işlem gerçekleştirmeye çalıştığında (örneğin, bir program yüklemek, sistem ayarlarını değiştirmek), UAC penceresi ekranda görüntülenir. Bu pencerede onay vermeniz veya reddetmeniz gerekir.

Dereceleri (yüksekten alçağa):

- Her zaman uyar: En güvenli seçenektir. Sistem ayarlarında yaptığınız değişiklikler dahil her şey için uyarı alırsınız.
- Yalnızca programlar bilgisayarımda değişiklik yapmaya çalıştığında uyar (varsayılan): Programların yaptığı değişiklikler için uyarı alırsınız ancak kendi yaptığınız değişiklikler için uyarı almazsınız.
- Yalnızca programlar bilgisayarımda değişiklik yapmaya çalıştığında uyar (masaüstü kararmaz): Üç bildirim seçeneğinin en az güvenli olanıdır. Uyarı yukarıdakilerle aynıdır ancak UAC penceresi açıldığında masaüstü kullanılabilir kalır.
- Asla uyarı gösterme (UAC devre dışı): Önerilmez. Tüm UAC uyarılarını devre dışı bırakarak sisteminizi savunmasız hale getirir.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/uac-c84d4b76a.webp)

Avantajları

- Güvenlik: UAC, yetkisiz değişikliklerden kaynaklanan hataları ve zararlı yazılımların yüklenmesini önlemeye yardımcı olur.
- Kontrol: Yönetici ayrıcalıkları gerektiren işlemler üzerinde size daha fazla kontrol sağlar.
- Kullanıcı Dostu: UAC penceresi, ne olup bittiğini anlamanıza ve onay vermeden önce bir işlemi durdurmanıza olanak tanır.

Dezavantajları

- Rahatsızlık: UAC sık sık onay isteyebilir, bu da bazı kullanıcılar için rahatsız edici olabilir.
- Uyumsuzluk: Bazı programlar UAC ile uyumsuz olabilir ve düzgün çalışmayabilir.