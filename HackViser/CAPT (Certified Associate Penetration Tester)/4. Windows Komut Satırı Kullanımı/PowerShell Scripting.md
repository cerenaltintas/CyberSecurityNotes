## Powershell ISE

İlk başta bahsetmiş olsak da hatırlatmak amaçlı tekrarlayalım.

Windows PowerShell ISE, açılımı Windows PowerShell Integrated Scripting Environment (Tümleşik Betik Ortamı) olan bir uygulamadır. PowerShell için geliştirilmiş bir grafiksel kullanıcı arayüzü (GUI) sağlar. Bu arayüz sayesinde PowerShell'da komut yazmak, çalıştırmak, test etmek ve hatalarını gidermek tek bir pencere üzerinden mümkün olur.

## PowerShell ile Betik (script) Yazma

PowerShell scriptleri, bir dizi komutu ve fonksiyonu bir araya getiren metin dosyalarıdır ve genellikle .ps1 uzantısıyla biterler.

Şuana kadar gördüğümüz konuları ve daha fazlasını otomatize etmek için kullanılırlar. Örneğin:

- Sistem yönetimi: Kullanıcı hesapları oluşturma, diskleri biçimlendirme, dosyaları kopyalama ve silme gibi işlemleri otomatikleştirmek.
- Ağ yönetimi: Ağ bağlantı ayarlarını yapılandırma, IP adreslerini yönetme, uzak sunuculara erişme gibi işlemleri otomatikleştirmek.
- Veri işleme: Verileri analiz etme, raporlar oluşturma, veritabanlarıyla etkileşim kurma gibi işlemleri otomatikleştirmek.
- Yazılım geliştirme: Uygulama dağıtımı, test otomasyonu, hata ayıklama gibi işlemleri otomatikleştirmek.

### Kontrol Yapıları

Değişkenler
 Değişkenler, scriptlerinizde veri saklamak ve işlemek için kullanılır.

```auto
# Bir değişken tanımlama
$name = "John Doe"

# Değişkene değer atama
$age = 30

# Değişkenin değerini alma
$name

# Birden fazla değişkeni tek satırda tanımlama
$firstName, $lastName = "John", "Doe"
```

Koşullar
 Koşullar, belirli bir işlemin ne zaman gerçekleştirileceğini belirlemenizi sağlar.

If-Else Yapısı

```auto
if ($age -gt 18) {
  Write-Host "Adult"
} else {
  Write-Host "Kid"
}
```

Switch-Case Yapısı

```auto
$dayOfWeek = Get-Date -Format dddd  # Get the current day of the week in full string format (e.g., "Monday", "Tuesday", etc.)

switch ($dayOfWeek) {
    "Monday" { Write-Host "Today is Monday. Time to start the week!" }
    "Tuesday" { Write-Host "Tuesday! Still a long way to go!" }
    "Wednesday" { Write-Host "It's Wednesday. Halfway through!" }
    "Thursday" { Write-Host "Thursday! Almost there!" }
    "Friday" { Write-Host "Friday! Time to celebrate the weekend!" }
    "Saturday" { Write-Host "Saturday! Enjoy the weekend!" }
    "Sunday" { Write-Host "Sunday! Last day before Monday!" }
    Default { Write-Host "Invalid day of the week." }
}
```

Döngüler
 Döngüler, bir kod bloğunu belirli bir sayıda veya koşul karşılanana kadar tekrarlamanızı sağlar.

For Döngüsü

```auto
for ($i = 1; $i -le 10; $i++) {
  Write-Host $i
}
```

While Döngüsü

```auto
$i = 1
while ($i -le 10) {
  Write-Host $i
  $i++
}
```

Do-While Döngüsü

```auto
$i = 1
do {
  Write-Host $i
  $i++
} while ($i -le 10)
```

Foreach Döngüsü

```auto
$names = "John", "Jane", "Doe"
foreach ($name in $names) {
  Write-Host $name
}
```

### Yazıp Kaydetmek

PowerShell ISE programını açıp komutları yazıp kaydedebiliriz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/568ab27d-60b5-4873-9d26-6b2b6bd8827e/ise-8ef88b016.webp)

## PowerShell Gallery

PowerShell Gallery, PowerShell kodlarını paylaşmak ve edinmek için merkezi bir havuzdur. Hem Microsoft hem de topluluk tarafından oluşturulan kodları içerir. PowerShellGet modülü aracılığıyla script'leri doğrudan PowerShell'den yükleyebilirsiniz ama kodların doğruluğu ve güvenliği konusunda dikkatli olmak gerekir, çünkü topluluk tarafından oluşturulan içerikler de bulunabilir.

### Arama

Örneğin sysinternals modülünü aramak istersek Find-Module kullanabiliriz.

```auto
PS C:\Users\Administrator> Find-Module -Name "sysinternals"

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      SysInternals                        PSGallery            PowerShell cmdlets for SysInternal tools
```

Eğer ilk kez aratıyorsanız NuGet kurulumu yapmak isteyecektir. Enterlayıp indirin.

### Yükleme

```auto
Install-Module -name SysInternals
```