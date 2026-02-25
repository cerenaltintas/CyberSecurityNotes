Linux işletim sistemlerinin günlük kullanımında ve sistem yönetiminde, yazılım paketlerinin yönetimi kritik bir öneme sahiptir. Linux dağıtımları, yazılım kurulumu, güncellemesi ve kaldırılması gibi işlemleri kolaylaştırmak için çeşitli paket yöneticileri sunar. Bu paket yöneticileri, yazılımları paket formatında, bağımlılıkları ile birlikte yönetmenize olanak tanır.

Her Linux dağıtımı, belirli paket yönetim sistemlerini ve paket formatlarını kullanır. Bu bölümde, Debian tabanlı Linux dağıtımlarında yaygın olarak kullanılan paket yönetim araçlarını ve bu araçların temel kullanımlarını ele alacağız.

### Paket (Package) ve Depo (Repository) Nedir?

Windows'ta bir program kurmak için internetten .exe dosyası indirip "İleri > İleri" dersiniz. Linux'ta ise işler daha güvenli ve düzenlidir.

-   **Paket (Package):** Bir programın çalışması için gereken tüm dosyaların (kodlar, kütüphaneler, resimler) sıkıştırılmış tek bir dosya halidir (Örn: .deb veya .rpm ).
-   **Depo (Repository):** Binlerce paketin saklandığı, güvenli ve resmi internet sunucularıdır. App Store veya Google Play Store gibi düşünebilirsiniz.
-   **Paket Yöneticisi (Package Manager):** Sizin yerinize depoya bağlanan, paketi indiren, kuran ve güncelleyen araçtır (Örn: apt ).

Bu sistem sayesinde virüs bulaşma riski çok düşüktür çünkü yazılımlar resmi kaynaklardan indirilir.

### Paket Yöneticilerinin Temel Özellikleri

Linux paket yöneticileri, yazılım paketlerinin yönetimi için çeşitli özellikler sunar:

-   **Paket İndirme:** Yazılım paketlerini ve bağımlılıklarını internet üzerinden otomatik olarak indirme.
-   **Bağımlılık Çözümleme:** Bir paketin gerektirdiği bağımlılıkları belirleme ve bunları otomatik olarak kurma.
-   **Paket Kurulumu ve Kaldırılması:** Yazılım paketlerini sisteme kurma ve gerektiğinde kaldırma.
-   **Güncellemeler ve Yükseltmeler:** Yüklü paketlerin yeni sürümlerini kontrol etme ve güncelleme.
-   **Yapılandırma Dosyaları ve Dizinleri:** Yazılım paketlerinin yapılandırma dosyaları ve dizinleriyle ilgili standartlar sunma.

### Paket Yöneticisi Karşılaştırması

Linux dünyasında farklı paket sistemleri vardır:

| Sistem | Format | Yönetici | Dağıtımlar | Örnek Komut |
| --- | --- | --- | --- | --- |
| **APT** | .deb | apt , dpkg | Debian, Ubuntu, Kali | apt install git |
| **RPM** | .rpm | dnf , yum | Fedora, RHEL, CentOS | dnf install git |
| **Pacman** | .pkg.tar.zst | pacman | Arch, Manjaro | pacman -S git |
| **Snap/Flatpak** | Kapsayıcı | snap , flatpak | Hepsi | snap install spotify |

### APT (Advanced Package Tool) Kullanımı

APT (Advanced Package Tool), Debian ve türevleri gibi Linux dağıtımlarında yazılım paketlerini yönetmek için kullanılan güçlü bir araçtır. Bu araç, kullanıcıların yeni yazılımları kolayca kurmalarına, mevcut yazılımları güncellemelerine, gereksiz olanları kaldırmalarına ve tüm bu işlemleri yaparken yazılımlar arasındaki bağımlılıkları otomatik olarak çözümlemelerine olanak tanır. Basit komut satırı komutlarıyla, kullanıcılar sistemlerini güncel ve güvenli tutabilir, aynı zamanda ihtiyaç duydukları yazılımlara hızlıca erişebilirler. APT'nin sunduğu kolaylık ve verimlilik, onu Linux kullanıcıları arasında popüler bir seçenek haline getirmiştir. Ubuntu/Debian sistemlerde apt kullanılır. 

1\. Güncelleme

Önce paket listesini internetten güncellemelisiniz.

```auto
user@hackerbox:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu bionic-security InRelease
Reading package lists... Done
All packages are up to date.
```

2\. Arama ve Bilgi Alma

Yüklemek istediğiniz paketin tam adını bilmiyorsanız arama yapabilirsiniz.

names-only parametresi sadece paket isimlerinde arama yaparken, normal arama açıklamaları da arar. 
**Paket İsmi ve Açıklamalarında Arama:**

```auto
user@hackerbox:~$ sudo apt search htop
aha - ANSI color to HTML converter
htop - interactive processes viewer
libauthen-oath-perl - Perl module for OATH One Time Passwords
```

**Sadece Paket İsimlerinde Arama:**

```auto
user@hackerbox:~$ sudo apt search --names-only htop
htop - interactive processes viewer
```

**Regex (Düzenli İfade) ile Arama:** İsmi tam olarak "htop" ile başlayanları bulmak için:

```auto
user@hackerbox:~$ sudo apt search ^htop
htop - interactive processes viewer
```

Daha detaylı bilgi (sürüm, boyut vb.) için apt-cache veya apt show kullanılır.

```auto
user@hackerbox:~$ apt show htop
Package: htop
Version: 2.2.0-2build1
...
```

```auto
user@hackerbox:~$ apt-cache policy htop
htop:
  Installed: 2.2.0-2build1
  Candidate: 2.2.0-2build1
```

3\. Yükleme

```auto
user@hackerbox:~$ sudo apt install htop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 80.0 kB of archives.
After this operation, 201 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic/universe amd64 htop amd64 2.1.0-3 [80.0 kB]
Fetched 80.0 kB in 1s (110 kB/s)
Selecting previously unselected package htop.
(Reading database ... 32507 files and directories currently installed.)
Preparing to unpack .../htop_2.1.0-3_amd64.deb ...
Unpacking htop (2.1.0-3) ...
Subject: htop 2.1.0-3 amd64
Setting up htop (2.1.0-3) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
```

Eğer sisteminizdeki bütün paketleri güncellemek isterseniz, **upgrade** komutunu kullanabilirsiniz.

```auto
user@hackerbox:~$ sudo apt upgrade
```

Bu yöntem, ekstra paket yüklemeyecek, veya artık kullanılmayan paket/kütüphaneleri kaldırmayacaktır. Eğer bunu önemsemiyorsanız, **dist-upgrade** komutunu kullanabilirsiniz.

```auto
user@hackerbox:~$ sudo apt dist-upgrade
```

4\. Kaldırma

-  ** remove **: Programı kaldırır, ayarları saklar.
-   ** purge **: Her şeyi (ayarlar dahil) siler.

```auto
user@hackerbox:~$ sudo apt remove htop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  htop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 201 kB disk space will be freed.
(Reading database ... 32558 files and directories currently installed.)
Removing htop (2.1.0-3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
```

Tamamen temizlemek için:

```auto
user@hackerbox:~$ sudo apt purge htop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  htop*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 201 kB disk space will be freed.
(Reading database ... 32558 files and directories currently installed.)
Removing htop (2.1.0-3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Purging configuration files for htop (2.1.0-3) ...
```

5\. Temizlik

Gereksiz bağımlılıkları (artık kullanılmayan kütüphaneleri) siler.

```auto
sudo apt autoremove
```

### DPKG (Debian Package)

İnternetten indirdiğiniz bir .deb dosyasını (örneğin Discord, Google Chrome) kurmak için kullanılır. apt bunu yapamaz.

**Örnek Senaryo: Discord Kurulumu**

```auto
user@hackerbox:~$ sudo dpkg -i discord.deb
(Reading database ... 100%
Unpacking discord ...
dpkg: dependency problems prevent configuration of discord:
 discord depends on libgconf...
```

**Hata Alırsanız:**

dpkg bağımlılıkları çözemez. Kurulum yarıda kalırsa düzeltmek için:

```auto
user@hackerbox:~$ sudo apt install -f
```

(Bu komut eksik parçaları internetten indirip kurulumu tamamlar).

### Modern Paketler (Snap)

Bağımlılık derdi olmadan çalışan yeni nesil paketlerdir.

```auto
user@hackerbox:~$ sudo snap install spotify
spotify 1.1.84 from Spotify installed
```

