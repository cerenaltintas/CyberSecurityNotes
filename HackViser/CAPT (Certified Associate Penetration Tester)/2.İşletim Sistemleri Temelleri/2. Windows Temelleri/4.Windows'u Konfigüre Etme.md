Bir kullanıcı kişiselleştirmek, problem çözmek, optimize etmek vb. gibi birçok nedenden dolayı sistem ayarlarını değiştirmek isteyebilir. Bu bölümde bunları nasıl yapacağımızı inceleyeceğiz.

## Ayarlar ve Denetim Masası

Windows'ta, Ayarlar ve Denetim Masası çeşitli sistem yapılandırmalarını ayarlamak için kullanılan iki arayüzdür, ancak farklılıkları vardır:

Ayarlar:

- Güncel olarak kullanılan araçtır
- Alt menülerle kullanım kolaylığı sağlar
- Hızlı erişim sağlar
- Yeni özellikler ve işlevler gelmeye devam eder

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/cont1-d2558efe9.webp)

Denetim Masası:

- Windows'u yapılandırmanın eski yolunu temsil eder
- Çeşitli uygulamalara sahip klasik bir klasör yapısı kullanır
- Daha ayrıntılı bir denetim düzeyi sunar
- Gelişmiş seçeneklere erişmesi gerekebilecek deneyimli kullanıcılara hitap eder
- Aşamalı olarak kaldırmakta ve yerini ayarlar almakta (Windows 11'de denetim masasındaki bazı öğeler direkt olarak ayarlardaki eşdeğer menüyü açar.)

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/cont2-34c8ae92d.webp)

## Sistem Yapılandırma (MSConfig)

Windows işletim sisteminde kullanılan bir sistem yapılandırma aracıdır. Bu araç, sistem başlangıcı ve sistem yapılandırmasıyla ilgili ayarları yapılandırmak ve yönetmek için kullanılır. Genellikle bir sistem yöneticisi veya gelişmiş kullanıcılar tarafından kullanılır.

Programı çalıştırdığınızda, aşağıdaki sekmelerle bir pencere açılır:

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/msconfig1-ac77416a5.webp)

Genel

Genel sekmesinde, Windows'un önyükleme sırasında hangi cihazların ve hizmetlerin yüklenmesi gerektiğini seçebiliriz. Seçenekler:

- Normal
- Tanımlayıcı
- Seçmeli

Önyükleme

Önyükleme sekmesinde, Safeboot gibi önyükleme seçeneklerini tanımlayabiliriz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/msconfig2-bb7eb4105.webp)

Hizmetler

Hizmetler sekmesinden tüm hizmetleri görüntüleyebiliriz. Hizmetleri etkinleştirebilir ya da devre dışı bırakabiliriz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/msconfig3-ac4046625.webp)

Başlangıç

Microsoft, başlangıç öğelerini etkinleştirmek/devre dışı bırakmak için Görev Yöneticisi kullanılmasını önermektedir. Başlangıç sekmesinde aşağıdaki mesaj yer alır.

"Başlangıç öğelerini yönetmek için görev yöneticisinin başlangıç bölümünü kullanın"

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/msconfig4-ba9e6b2f1.webp)

Araçlar

Msconfig'in Araçlar sekmesi, işletim sistemini daha detaylı yapılandırmanıza yardımcı olacak çeşitli yardımcı programları listeler. Her bir programın işlevini anlamak için kısa açıklamalar da mevcuttur.

Seçili komut bölümü her araç için değişecektir.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/msconfig5-af78d8c6c.webp)

## Kayıt Düzenleyici (Regedit)

Kayıt Defteri, Windows'un yapılandırma verilerini ve sistem ayarlarını içeren bir veritabanıdır. Bu veritabanı, Windows'un nasıl çalıştığını ve birçok sistem ve uygulama ayarını barındırır.

Kayıt defterini görüntülemek/düzenlemek için çeşitli yöntemler bulunmaktadır. Bunlardan biri Kayıt Düzenleyici'yi kullanmaktır.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/regedit-3ec13f9f8.webp)

Kayıt Düzenleyici, kullanıcıların Kayıt Defteri'ni düzenlemelerine ve ayarlamalarına olanak tanır. Bilgisayarın davranışını değiştirmek veya sistem ayarlarını özelleştirmek için kullanışlıdır.

Ancak, Kayıt Defteri'nde yanlış değişiklikler yapmak, sistemin istikrarını veya doğru çalışmasını olumsuz yönde etkileyebilir, bu nedenle bu tür değişiklikleri yaparken dikkatli olunmalıdır.

## Yerel Grup İlkesi

Yalnızca tek bir bilgisayarı yönetmek için kullanılan bir Windows aracıdır. Bu araç, bilgisayarınızın güvenlik ayarlarını, kullanıcı haklarını ve diğer konfigürasyon seçeneklerini yönetmenize olanak tanır.

GPO (Grup İlkesi Objesi) Bir ağ ortamındaki birden fazla bilgisayarı yönetmek için merkezi olarak bir domain controller üzerinden yönetilir.

Ama yerel grup ilkesi tek bir bilgisayarı yönetmek için kullanılır. Merkezi olarak yönetilemez.