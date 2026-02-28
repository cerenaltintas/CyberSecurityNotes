MSFConsole, Metasploit Framework'e erişim ve bu çerçevede çalışma imkanı sunan bir komut satırı arayüzüdür. Metasploit Framework'ü kullanırken genellikle MSFconsole tercih edilir. Bu arayüz, hedef tarama, güvenlik açıklarını kullanma ve veri toplama gibi işlemleri gerçekleştirmenize olanak tanır.

### MSFConsole'u Başlatma

Linux'ta MSFConsole'u başlatmak için terminalde

msfconsole

komutunu çalıştıralım.

```auto
root💀hackerbox:~# msfconsole
```

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image1-28a9c227d.webp)

MSFConsole her başlatıldığında yukarıdaki görselde de görüldüğü üzere farklı bannerlar gelir. MSFConsole'u bu şekilde bannersiz başlatmak için aşağıdaki komutu kullanabiliriz.

```auto
root💀hackerbox:~# msfconsole -q
```

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image2-72453a3f3.webp)

### MSFConsole'da Yardım Alma Komutları

- Geçerli mod için uygun komutların bir listesini görmek için
    
    help
    
    komutunu kullanabiliriz. Herhangi bir modül seçili değilken, ana moddayken,
    
    help
    
    komutu genel olarak kullanılabilir komutlar için yardımı menüsünü gösterir. Modül modundayken ise, o modüle ait komutlar ve seçenekler için yardım menüsü gösterilir.
    
- Bir modül hakkında detaylı bilgi almak için
    
    info <module_name>
    
    yazın.
    

### Temel Komutlar

search

MSFConsole'da bir arama yapmak için

search

komutunu kullanırız.

search [<options>] [<keywords>:<value>]

```auto
-h, --help                      Yardım menüsü
-I, --ignore                    Tek eşleşme arama ile aynı ada sahipse komutu yoksay
-o, --output <filename>         Çıktıyı csv formatında bir dosyaya gönderme
-S, --filter <filter>           Arama sonuçlarını filtrelemek için kullanılan regex şeması
-s, --sort-ascending <column>   Arama sonuçlarını belirtilen sütuna göre artan sırada sıralar
```

**Örnek** ![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image3-0cbf123e6.webp)

use

Bir modülü seçmek için kullanılır. Yaptığımız bir arama sonucundaki listeden bir modülü numarasını kullanarak seçebiliriz ya da bir modülün tam yolunu belirtiriz.

use <module-number>

ya da

use <module-path>

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image4-3440277b1.webp)

info

Bir modül hakkında detaylı bilgi almak için kullanılır.

Bir modül seçiliyken

info

komutu çalıştırabiliriz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image5-1bbbe06e0.webp)

options

Seçili olan bir modülün yapılandırmalarını görüntülemek için kullanılır.

Seçilen exploiti çalıştırmak için **Required** sütununda **yes** yazan alanların doldurulması gerekir. Diğer seçenekler opsiyoneldir.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image6-33754cd9a.webp)

show

show

komutu ile encoderlar, nops, exploitler, payloadlar, auxiliary modüller, post modüller, pluginler ve seçenekler(options) görüntülenebilir.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image7-c9092f6ae.webp)

set ve get

set

komutu ile bir seçeneğin değerini değiştirmek için kullanılır.

get

komutu bir seçeneğin değerini görüntülemek için kullanılır.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image8-13a017d8c.webp)

unset

Bir seçeneğin değerini temizlemek için kullanılır.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image9-cd46e0f57.webp)

advanced

O anda etkin olan modül için gelişmiş seçenekleri gösterir.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image11-14c016b8e.webp)

history

Komut geçmişini gösterir.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image10-808b30285.webp)

sessions

Aktif olan oturumları listeler.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image12-878fd800a.webp)

back

Seçili modülden çıkmak için kullanılır.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image13-dde5729cf.webp)