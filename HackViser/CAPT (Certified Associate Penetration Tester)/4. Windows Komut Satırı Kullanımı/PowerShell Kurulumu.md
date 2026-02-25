Tamamlayıcılık açısından tüm makinelere PowerShell (PS) kurulumu anlatılacaktır.

Eğer güncel bir Windows makine kullanıyorsanız, kuruluma ihtiyacınız yok ve bu bölümü atlayabilirsiniz.

Yine de öğrenecek bir şeyler olabilir, bu bölümü de takip etmeniz önerilir.

### Windows

PowerShell'i Windows'a yüklemenin birden çok yolu olmasına karşın Microsoft'un önerdiği yol winget ile kurulumdur.

WinGet

Microsoft'un Windows 10 ve sonraki sürümleri için bir paket yöneticisidir. Windows kullanıcılarının yazılım kurulumunu, güncellemesini ve yönetimini kolaylaştırmak için geliştirilmiştir. Winget, Windows'un geliştirici araçlarının bir parçası olarak sunulan açık kaynaklı bir projedir.

Winget, kullanıcıların komut satırı aracılığıyla veya grafik arayüzü üzerinden yazılımları kolayca aramasını, yüklemesini ve güncellemesini sağlar

Komut satırı aracı winget , Windows 11 ve Windows 10'un modern sürümleri varsayılan olarak Uygulama Yükleyicisi olarak paketlenmiştir.

PowerShell'in en son sürümünü arama:

```auto
C:\>winget search Microsoft.PowerShell
Name               Id                           Version Source
---------------------------------------------------------------
PowerShell         Microsoft.PowerShell         7.4.1.0 winget
PowerShell Preview Microsoft.PowerShell.Preview 7.5.0.2 winget
```

Id ile kurulum

```auto
C:\>winget install --id Microsoft.Powershell --source winget
Found PowerShell [Microsoft.PowerShell] Version 7.4.1.0
This application is licensed to you by its owner.
Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
Downloading https://github.com/PowerShell/PowerShell/releases/download/v7.4.1/PowerShell-7.4.1-win-x64.msi
  ██████████████████████████████   103 MB /  103 MB
Successfully verified installer hash
Starting package install...
Successfully installed
```

### Linux (Ubuntu)

Snapstore kullanarak PS'nin paketlenmiş sürümünü Ubuntu'ya yükleyebiliriz.

```auto
sudo snap install powershell --classic
```

### macOS

Homebrew kullanarak yüklemek en popüler yollardandır.

```auto
brew install powershell/tap/powershell
```