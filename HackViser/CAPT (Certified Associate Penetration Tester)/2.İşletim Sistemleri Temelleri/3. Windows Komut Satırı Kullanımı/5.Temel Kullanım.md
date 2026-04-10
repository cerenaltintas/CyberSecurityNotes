Öncelikle gündelik kullanımda çok işe yarayacak sık kullanacağımız komutları göreceğiz.

## Dosya ve Dizin

Dosya ve dizinlerle uğraşırken bilinmelidir ki tek nokta (.) bulunulan dizini, çift nokta (..) ise bir üst dizini ifade eder.

Get-ChildItem (ls)

Belirtilen dizinin içeriğini listeleyen bir cmdlet.

```auto
PS C:\Users\user> Get-ChildItem


    Directory: C:\Users\user


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-r---         3/15/2024  11:30 PM                3D Objects
d-r---         3/15/2024  11:30 PM                Contacts
d-r---          4/1/2009  12:10 PM                Desktop
d-r---         3/18/2024  10:39 PM                Documents
d-r---         3/16/2024   9:55 AM                Downloads
d-r---         3/15/2024  11:30 PM                Favorites
d-r---         3/15/2024  11:30 PM                Links
d-r---         3/15/2024  11:30 PM                Music
d-r---         3/15/2024  11:30 PM                Pictures
d-r---         3/15/2024  11:30 PM                Saved Games
d-r---         3/15/2024  11:31 PM                Searches
d-r---         3/15/2024  11:30 PM                Videos
```

Set-Location (cd)
Çalışma dizinini değiştiren bir cmdlettir.

İlk örneklerimizde görmüştük.

```auto
PS C:\Users\user> Set-Location .\Documents\
PS C:\Users\user\Documents>
```

New-Item
Bu cmdlet yeni bir dosya veya dizin oluşturur.

Bir parametre vermezsek varsayılan olarak boş bir dosya oluşturur.

```auto
PS C:\Users\user\Documents> new-item file.txt


    Directory: C:\Users\user\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          4/1/2009  10:15 PM              0 file.txt
```

Bir klasör oluşturmak için -ItemType Directory parametresini verebiliriz

```auto
PS C:\Users\user\Documents> New-Item -ItemType Directory logs


    Directory: C:\Users\user\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----          4/1/2009  10:24 PM                logs
```

Daha fazla örneğe ve yapılacak gelişmiş kullanıma yardım sayfasından ulaşabilirsiniz.

```auto
get-help New-Item -examples
```

Remove-Item (rm)
 Bu komut dosyaları veya dizinleri siler.

```auto
PS C:\Users\user\Documents> Remove-Item .\logs\
```

Copy-Item (cp)
 Dosya veya dizinleri kopyalamak için kullandığımız bir komuttur.

```auto
PS C:\Users\user\Documents> New-Item file.txt


    Directory: C:\Users\user\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          4/1/2009  10:26 PM              0 file.txt


PS C:\Users\user\Documents> copy-item file.txt file1.txt
PS C:\Users\user\Documents> ls


    Directory: C:\Users\user\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          4/1/2009  10:26 PM              0 file.txt
-a----          4/1/2009  10:26 PM              0 file1.txt
```

Move-Item (mv)
 Dosyaları veya dizinleri taşır veya yeniden adlandırır. Eğer dosya ismi vermeyip dizin ismi verirsek sadece taşıma yapar.

```auto
PS C:\Users\user\Documents> Move-Item .\file1.txt ..\Desktop\
```

Eğer yeni bir isim verirsek taşır ve yeniden adlandırır.

```auto
PS C:\Users\user\Documents> move-item ..\Desktop\file1.txt .\file01.txt
PS C:\Users\user\Documents> ls


    Directory: C:\Users\user\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          4/1/2009  10:26 PM              0 file.txt
-a----          4/1/2009  10:26 PM              0 file01.txt
```

Get-Content (cat)
 Dosyaların içeriğini görüntülemek için kullanılır.

```auto
PS C:\Users\user\Documents> get-content .\file.txt
```

## Sistem İşlemleri

Get-Process
 Sistemdeki işlemlerin listesini görüntüler.

Genellikle fitreleme seçenekleriyle kullanılır.

Parametre olmadan çağırılırsa tüm işlemleri gösterir.

```auto
PS C:\Users\user> Get-Process

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    327      19     9500      27948       0.06   5036   1 ApplicationFrameHost
    170      10     1868       8272              2796   0 blnsvr
    272      14     7124      24228       0.31   5136   1 conhost
    516      21     1772       5092               472   0 csrss
    328      17     1776       5192               560   1 csrss
    397      16     3848      19652       0.14   5532   1 ctfmon
    359      17     3332      12372              2192   0 dasHost
    226      17     4196      12140       0.00   6960   1 dllhost
    916      35    44548      78560               476   1 dwm
   1662      63    25876      93940       1.31   5432   1 explorer
     32       5     1444       3652               856   1 fontdrvhost
     32       5     1304       3212               864   0 fontdrvhost
      0       0       60          8                 0   0 Idle
   1208      25     6788      18816               716   0 lsass
      0       0       72        500              1840   0 Memory Compression
    210      14     2200       1832              1372   0 MicrosoftEdgeUpdate
    798      22    11248      25608              6232   0 MoUsoCoreWorker
   1280      44    51628     116456       1.50    904   1 msedge
    149       9     2024       7348       0.02   7048   1 msedge
    307      17    11436      27120       0.03   7200   1 msedge
    349      30    10988      32772       0.27   7208   1 msedge
    169      12     6716      17164       0.05   7216   1 msedge
    193      15    17768      25800       0.08   7580   1 msedge
    401      22    76128     115708       2.77   8136   1 msedge
    773      95   265236     203064              2960   0 MsMpEng
    178      40     3828       8652              4656   0 NisSrv
    678      33   120356     135084       1.09   6824   1 powershell

...
```

```auto
Get-Process -name win*

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    162      11     1460       6948               552   0 wininit
    274      12     2592      12076               624   1 winlogon
```

Stop-Process:
 Bir işlemi sonlandırır. Isim veya işlem id'si ile çağırılabilir.

```auto
PS C:\Users\user> get-process -name explorer*

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
   2202      85    38472     120904       1.88   5432   1 explorer


PS C:\Users\user> stop-process -Id 5432
```

Get-Service
 Sistemdeki hizmetlerin listesini görüntülemek için kullanılır.

```auto
PS C:\Users\user> Get-Service

Status   Name               DisplayName
------   ----               -----------
Stopped  AarSvc_40ce5       Agent Activation Runtime_40ce5
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
Stopped  AppMgmt            Application Management
Stopped  AppReadiness       App Readiness
Stopped  AppVClient         Microsoft App-V Client
Running  AppXSvc            AppX Deployment Service (AppXSVC)
Stopped  AssignedAccessM... AssignedAccessManager Service
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
Stopped  autotimesvc        Cellular Time
Stopped  AxInstSV           ActiveX Installer (AxInstSV)
Running  BalloonService     BalloonService
Stopped  BcastDVRUserSer... GameDVR and Broadcast User Service_...
Stopped  BDESVC             BitLocker Drive Encryption Service
Running  BFE                Base Filtering Engine
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  BluetoothUserSe... Bluetooth User Support Service_40ce5
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Stopped  BTAGService        Bluetooth Audio Gateway Service
...
```

Start-Service
 Bir hizmeti başlatır.

```auto
PS C:\Users\user> Start-Service -Name Appinfo
```

Stop-Service
 Bir hizmeti durdurur.

```auto
PS C:\Users\user> Stop-Service -Name Appinfo
```

## Nesne Seçimi ve Filtreleme

Yukarıda incelediğimiz cmdlet’ler, çok uzun çıktılar üreten, çıktısı farklı şekillerde kullanılmak istenen ya da yalnızca tek bir sütununa erişilmek istenen komutlar içerebilir. Bunları nasıl yöneteceğimizi öğreneceğiz.

PowerShell'de pipe işlemi, komut çıktılarınızı bir sonraki komuta aktararak güçlü bir şekilde görev zincirlemenizi sağlar. Boru sembolü "|" ile gösterilir.

Pipe işlemi, tek bir komut satırında birden fazla komut çalıştırmanıza olanak tanır. Önceki komutun çıktısı, sonraki komutun girdisi hâline gelir. Bu, karmaşık görevleri daha küçük ve daha yönetilebilir adımlara ayırmanıza, ayrıca çıktıları ihtiyaçlarınıza göre işlemenize olanak tanır.

Örneğin, çalışan işlemlerin bir listesini alıp yalnızca adlarını ve kimlik numaralarını görmek isteyebilirsiniz:

```auto
Get-Process | Select-Object ProcessName, Id
```

Select-Object (select)

Bu cmdlet sayesinde bir koleksiyondaki nesnelerin belirli özelliklerini seçerek yalnızca ihtiyaç duyduğunuz bilgileri görüntüleyebilirsiniz.

Yukarıdaki örnekte işimize yaramayacak olan diğer kısımları almadan sadece işlemin ismini ve idsini aldık.

Where-Object (where)

Nesneleri belirli kriterlere göre filtrelemenizi sağlar. Bu sayede yalnızca ihtiyacınız olan nesneleri işleme alırsınız.

Örneğin tüm servisleri listeleyip sadece çalışan servislerin çıktısını almak için

```auto
Get-Service | Where-Object Status -eq "Running"
```

Burada -eq operatörü eşitlik anlamına gelir.

Sık kullanılan operatörler aşağıdaki gibidir.

- -eq: Eşittir
- -ne: Eşit değil
- -gt: Büyüktür
- -ge: Büyük veya eşittir
- -lt: Küçüktür
- -le: Küçük veya eşittir

Diğer tüm operatörleri Where-Object komutunun yardım sayfasında bulabilirsiniz.

Select-String
 Select-String komutu, metin dosyaları veya dizelerdeki metin satırlarını aramak ve seçmek için kullanılan bir PowerShell cmdlet'idir. Belirli bir desenle eşleşen satırları veya desenle eşleşmeyen satırları seçebilirsiniz.

- Metin Dosyalarını Arama: Bir metin dosyasında belirli bir kelimeyi, ifadeyi veya regex desenini aramak için kullanılabilir.
- Dize İşleme: Bir dizedeki belirli bir metni seçmek veya değiştirmek için kullanılabilir.
- Filtreleme: Belirli kriterlere uyan metin satırlarını seçmek için kullanılabilir.

Bir metin dosyasında belirli bir kelimeyi arama

```auto
PS C:\Users\user\Documents> Select-String -Pattern "today" .\file.txt

file.txt:1:The purpose of today's training is to defeat yesterday's understanding. - Miyamoto Musashi
```