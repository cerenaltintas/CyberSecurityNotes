### Sistem Hakkında Bilgi Edinme

Get-ComputerInfo

İşletim sistemi detayları, donanım bilgileri vb. hakkında bilgi verir.

```auto
PS C:\Users\Administrator> Get-ComputerInfo

WindowsBuildLabEx                                       : 17763.1.amd64fre.rs5_release.180914-1434
WindowsCurrentVersion                                   : 6.3
WindowsEditionId                                        : ServerStandard
WindowsInstallationType                                 : Server
WindowsInstallDateFromRegistry                          : 3/20/2024 4:48:20 AM
WindowsProductId                                        : 00429-00000-00001-AA815
WindowsProductName                                      : Windows Server 2019 Standard
WindowsRegisteredOrganization                           :
WindowsRegisteredOwner                                  : Windows User
WindowsSystemRoot                                       : C:\Windows
WindowsVersion                                          : 1809
BiosCharacteristics                                     :
BiosBIOSVersion                                         : {BOCHS  - 1}
BiosBuildNumber                                         :
BiosCaption                                             : Default System BIOS
BiosCodeSet                                             :
BiosCurrentLanguage                                     :
BiosDescription                                         : Default System BIOS
...
```

win32_OperatingSystem Sınıfı

Eğer hedef sistemi replike etmek ve denemeler yapmak istiyorsak idealdir.

```auto
PS C:\Users\Administrator> Get-WmiObject -Class win32_OperatingSystem

SystemDirectory : C:\Windows\system32
Organization    :
BuildNumber     : 17763
RegisteredUser  : Windows User
SerialNumber    : 00429-00000-00001-AA815
Version         : 10.0.17763
```

Yüklü yamaları görme

Get-Hotfix komutu, Windows Update veya kullanıcılar tarafından elle yüklenen tüm güncelleştirmeleri (hotfix'leri) görüntülemek için kullanılır.

```auto
PS C:\Users\Administrator> Get-Hotfix

Source        Description      HotFixID      InstalledBy          InstalledOn
------        -----------      --------      -----------          -----------
SRV2019       Update           KB4464455                          10/29/2018 12:00:00 AM
...
```

Defender

Defender'ın servisleri hakkında bilgi edinebiliriz.

```auto
PS C:\Users\Administrator> Get-Service | where DisplayName -like '*Defender*'

Status   Name               DisplayName
------   ----               -----------
Running  mpssvc             Windows Defender Firewall
Stopped  Sense              Windows Defender Advanced Threat Pr...
Running  WdNisSvc           Windows Defender Antivirus Network ...
Running  WinDefend          Windows Defender Antivirus Service
```

### Dosyalar Hakkında Bilgi Edinme

Bir metni dosyalarda bulma

Herhangi bir metni tüm dosyalarda bulmak için aşağıdaki komutu kullanabiliriz.

```auto
Get-ChildItem -Recurse *.* | Select-String -Pattern "SEARCH_STR"
```

Dosya yetkileri

Erişim Kontrol Listesi (ACL)'ni görüntülemek için kullanacağımız bir komut var. ACL, bir dosya veya klasöre erişim izni olan kullanıcı veya grupların ve sahip oldukları izinlerin (Okuma, Yazma, Silme vb.) bir listesidir.

```auto
Get-Acl file.txt
```

Dosya Hashleri

Herhangi bir dosyanın hashini alıp aratma, karşılaştırma vs. yapmak için kullanabiliriz

```auto
Get-FileHash file.txt
```