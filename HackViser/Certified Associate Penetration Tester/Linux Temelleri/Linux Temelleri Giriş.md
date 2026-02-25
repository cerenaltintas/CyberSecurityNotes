%% Error: Cannot create a waypoint in a note that's not the folder note. For more information, check the instructions [here](https://github.com/IdreesInc/Waypoint) %%
LIST FROM "Linux Temelleri"

**Linux ve Windows Karşılaştırması**

Linux'u anlamak için en yaygın kullanılan işletim sistemi olan Windows ile farklarına bakmak faydalıdır.

|Özellik|Linux|Windows|
|---|---|---|
|**Kaynak Kodu**|Açık Kaynak (Open Source). Herkes kodu görebilir ve değiştirebilir.|Kapalı Kaynak (Closed Source). Kod gizlidir ve Microsoft'a aittir.|
|**Lisans**|Genellikle Ücretsiz (GPL).|Ücretli lisans gerektirir.|
|**Dosya Sistemi**|Tek kök dizin (<br><br>/<br><br>) ve hiyerarşik yapı. Sürücü harfi yoktur.|Sürücü harfleri (<br><br>C:\<br><br>, <br><br>D:\<br><br>) kullanılır.|
|**Kullanıcı Arayüzü**|İsteğe bağlıdır. Birden çok masaüstü ortamı (GNOME, KDE) seçilebilir.|Yerleşik ve standart bir arayüzü vardır.|
|**Güvenlik**|İzin tabanlı yapısı ve açık kaynak olması nedeniyle virüslere karşı daha dirençlidir.|Hedef kitlesi büyük olduğu için kötü amaçlı yazılımların ana hedefidir.|
|**Donanım Desteği**|Çekirdek (Kernel) içinde yerleşik sürücülerle gelir. Çoğu donanımı otomatik tanır.|Sürücülerin ayrıca yüklenmesi gerekebilir.|

### Linux Felsefesi

Linux, işbirliği ve özgürlük ruhunu temsil eder. Gelişimi, aşağıdaki ilkeleri kanıtlar:

- **Özgürlük:** Linux, kullanıcılara yazılımlarını kontrol etme, değiştirme ve yeniden dağıtma özgürlüğü verir. Bu, inovasyon ve güvenlik ortamını teşvik eder.
- **İşbirliği:** Dünya genelinde binlerce geliştirici Linux'a katkıda bulunur, böylece keskin, güvenli ve kullanıcı ihtiyaçlarına duyarlı kalır.
- **Şeffaflık:** Linux'un açık kaynak doğası, mülkiyetli sistemlerle karşılaştırılamayacak bir şeffaflık seviyesi sağlar.
- **Her Şey Bir Dosyadır (Everything is a File):** Unix felsefesinin en belirgin özelliğidir. Linux'ta dokümanlar, dizinler, sabit diskler, modemler, klavyeler, yazıcılar ve hatta işlemler (processes) ve ağ bağlantıları birer dosya olarak temsil edilir. Bu, sistem yönetimini ve programlamayı tutarlı hale getirir.
- **Küçük ve Özelleşmiş Araçlar:** "Bir şeyi yap ve onu iyi yap." Linux komutları genellikle tek bir görevi mükemmel şekilde yapmak üzere tasarlanmıştır. Karmaşık işlemler, bu küçük araçların birbirine bağlanmasıyla (piping) gerçekleştirilir.

### Linux Nasıl Çalışır?

Linux, Windows veya macOS gibi bir işletim sistemidir ancak nasıl çalıştığı ve ücretsiz, açık kaynak doğası açısından farklıdır. Kalbinde Linux çekirdeği bulunur, bu da sistemin temel parçasıdır. Çekirdek (kernel), bilgisayarın donanımını, CPU, bellek ve çevre birimleri gibi yönetmekten sorumludur ve tüm yazılım uygulamalarının fiziksel donanımla etkileşimde bulunmasını sağlar.

Çekirdek, yazılım uygulamaları ile bilgisayarın donanımı arasında bir köprü görevi görerek çalışır. Bir yazılım uygulaması, bir dosyayı kaydetmek veya ekranda bir şey göstermek gibi donanımla ilgili bir şey yapmak istediğinde, bir istek çekirdeğe gönderir. Çekirdek, bu isteği donanımın anlayacağı talimatlara çevirir.

Linux, çoklu görev ve çok kullanıcılı bir ortamı destekler. Bu, birden fazla kullanıcının aynı anda sistemi kullanabilmesi ve her birinin aynı anda birden fazla programı çalıştırabilmesi anlamına gelir. Bu, birçok kişinin farklı görevler için aynı sisteme erişmesi gereken sunucu ortamlarında özellikle yararlıdır.


### Linux Dosya Sistemi Hiyerarşisi (FHS)
Linux, Windows'taki

C:\,D:\ gibi sürücü harfleri yerine, /(root) dizininden başlayan tek bir ağaç yapısı kullanır. Bu yapı **Filesystem Hierarchy Standard (FHS)** ile standartlaştırılmıştır.

| Dizin                 | Açıklama                                                | İçerik Örneği                                     |
| --------------------- | ------------------------------------------------------- | ------------------------------------------------- |
| /(Root)               | Dosya sisteminin başlangıç noktasıdır.                  | Tüm sistem.                                       |
| /bin                  | Temel kullanıcı komutlarını barındırır. (Binary)        | ls, cp, cat, bash                                 |
| /boot                 | Sistemin açılması için gereken dosyaları içerir.        | vmlinuz(Kernel), initrd, GRUB                     |
| /dev                  | Donanım aygıt dosyalarını içerir. (Devices)             | /dev/sda(Disk), <br><br>/dev/tty(Terminal)        |
| /etc                  | Sistemin yapılandırma dosyalarının bulunduğu merkezdir. | /etc/passwd<br><br>, <br><br>/etc/ssh/sshd_config |
| /home                 | Kullanıcıların kişisel dosyalarının saklandığı yerdir.  | /home/mehmet, <br>/home/ali                       |
| /lib                  | Programların ihtiyaç duyduğu kütüphane dosyaları.       | libc.so, Kernel modülleri                         |
| /mnt<br> & <br>/media | Geçici bağlanan diskler ve USB bellekler.               | /media/usb-disk                                   |
| /opt                  | Elle kurulan 3. parti uygulamalar.                      | Google Chrome, TeamViewer vb.                     |
| /proc                 | Sanal dosya sistemi. Sistem bilgisini tutar.            | /proc/cpuinfo, <br>/proc/meminfo                  |
| /root                 | Sistem yöneticisinin (root) ev dizinidir.               | Root'un özel dosyaları.                           |
| /sbin                 | Sadece yöneticinin kullandığı kritik komutlar.          | iptables, fdisk, reboot                           |
| /tmp                  | Geçici dosyalar içindir.                                | Uygulama önbellekleri.                            |
| /usr                  | İkincil hiyerarşi. Kullanıcı araçları buradadır.        | /usr/bin/python, <br>/usr/share                   |
| /var                  | Boyutu sürekli değişen dosyalar.                        | Loglar (/var/log), Web sitesi (/var/www)          |

### Linux Mimarisi

Linux işletim sistemi, bilgisayarın kaynaklarını yönetmek ve kullanıcı etkileşimini kolaylaştırmak için katmanlı bir yapıdan oluşur.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/linux-layers-a4d3a0334.webp)

1. **Donanım Katmanı (Hardware)**: CPU, RAM, Disk, Ağ Kartı gibi fiziksel bileşenlerdir.
    
2. **Çekirdek Katmanı (Kernel)**: İşletim sisteminin beynidir.
    
    - **Kernel Space (Çekirdek Alanı):** Sadece çekirdeğin erişebildiği, donanımla doğrudan konuşan güvenli bellek alanıdır. Sürücüler burada çalışır.
    - **User Space (Kullanıcı Alanı):** Kullanıcı uygulamalarının çalıştığı kısıtlı alandır. Donanıma erişmek için çekirdekten izin isterler (System Call).
3. **Sistem Kütüphaneleri (System Libraries)**: Çekirdeğin karmaşık fonksiyonlarını uygulamaların anlayacağı basit komutlara çeviren çevirmenlerdir (örn: glibc).
    
4. **Kabuk Katmanı (Shell)**: Kullanıcıdan komut alan ve bunu çekirdeğe ileten arayüzdür (Bash, Zsh).
    
5. **Uygulama Katmanı (Applications)**: Tarayıcılar, metin editörleri, veritabanı sunucuları gibi kullanıcının çalıştığı programlardır.
    

### Linux Açılış Süreci (Boot Process)

Bir Linux sisteminde güç düğmesine basıldığında sırasıyla şunlar olur:

1. **BIOS/UEFI:** Donanım testi (POST) yapar ve önyüklenebilir disk arar.
2. **MBR/GPT:** Diskin ilk sektöründeki önyükleme kaydını okur.
3. **Bootloader (GRUB):** İşletim sistemi seçme ekranını gösterir ve seçilen Linux çekirdeğini (Kernel) RAM'e yükler.
4. **Kernel:** Donanımları tanır, sürücüleri yükler ve kök dosya sistemini (/) bağlar.
5. **Init System (Systemd/SysVinit):** İlk işlem olarak (PID 1) çalışır. Arka plan servislerini, ağı ve giriş ekranını başlatır.