Başlat menüsünden PowerShell yazıp açtıktan sonra önümüze aşağıdaki gibi bir pencere gelmeli.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/3b84b576-04fe-4de1-a5e5-11eef5f480d9/ps-247489f91.webp)

Windows PowerShell açmamız gereken uygulama.

Windows PowerShell ISE, açılımı Windows PowerShell Integrated Scripting Environment (Tümleşik Betik Ortamı) olan bir uygulamadır. PowerShell için geliştirilmiş bir grafiksel kullanıcı arayüzü (GUI) sağlar. Bu arayüz sayesinde PowerShell'da komut yazmak, çalıştırmak, test etmek ve hatalarını gidermek tek bir pencere üzerinden mümkün olur.

## İlk Komutunuz

Açtıktan sonra ilk yazacağımız satır PS'nin versiyonunu öğrenmek için olacak.

```auto
PS C:\Users\user> $PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.19041.1237
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1237
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## Yardım Alma

PowerShell'de binlerce komut var ve hepsini ezberlemek çok iyi bir hafızaya sahip değilseniz imkansız gibi.

Aslına bakarsanız komutları ezberlemeye gerek de yok. Yardım sayfaları bunun için var.

PowerShell'de komutlar, "cmdlet" olarak adlandırılır. Cmdlet'ler, "Fiil-İsim" şeklinde adlandırılır.

Örneğin, işlemleri görüntülemek için Get-Process cmdlet'i kullanılırken, hizmetler hakkında bilgi için Get-Service cmdlet'i kullanılır.

PowerShell komutu terimi, cmdlet, işlev veya diğer ad olup olmadığına bakılmaksızın, PowerShell'deki herhangi bir komut türü için genellikle kullanılan genel bir terimdir.

---

### Get-Help Komutu

- Get-Help komutu bir komut hakkında bilgi almak için kullanılır. Get-Help komutunun nasıl çalıştığını öğrenmek için

```auto
Get-Help Get-Help
```

yazabiliriz. 

Eğer uzun geliyorsa herhangi bir komutun sonuna -? atarak da yardım sayfasına erişebilirsiniz.

### Get-Command

Peki ya yardım istediğimiz komutun ismini unutursak? Orada da imdada Get-Command yetişiyor.

Get-Command , PowerShell'da yüklü olan tüm komutları, cmdlet'leri, işlevleri, filtreleri, betikleri ve hatta uygulama komutlarını listelemek için kullanılan bir komuttur.

Bu komutun kullanımını görmek için tekrar get-help yapabiliriz.

```auto
Get-Help -Name Get-Command -Detailed
```

Bu iki komut aslında PS öğrenmek için ihtiyacınız olan şeylerin %80'ini kapsıyor.

### Update-Help

Eğer yardım sayfaları eksik veya güncel değil ise Update-Help komutu kullarak güncelleştirebiliriz.

Bu komut yükseltilmiş yetkiler istemekte.

## Alias (Kısaltma/lar)

Aliaslar, PowerShell'de cmdlet'ler, işlevler ve betikler için kısaltmalar oluşturmaya yarayan özel adlardır. Komutları daha kısa ve yazması daha kolay hale getirerek komut satırında daha hızlı çalışmanıza yardımcı olurlar.

Eğer daha önceden Linux veya CMD komutlarını biliyorsanız çok işinize yarayacaktır.

Örneğin Set-Location cmdlet'i için cd alias'ı kullanılabilir.

Daha hızlı bir PowerShell kullanımı için aliasların bilinmesi önerilmektedir.

Tüm aliasları görüntülemek için

```auto
alias
```

Bir komut için olan aliası görüntülemek için alias dan sonra komut yazılabilir.

```auto
PS C:\Users\user> alias cd

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           cd -> Set-Location
```

## Tab Tamamlaması

PowerShell tab tamamlama, bir komut veya parametrenin adını yazarken Tab tuşuna basarak otomatik olarak tamamlama özelliğidir. Bu özellik, komutları ve parametreleri daha hızlı ve kolay bir şekilde yazmanıza yardımcı olur.

Tab tamamlamayı kullanmak için:

- Komut veya parametrenin adını yazmaya başlayın.
- Tab tuşuna basın.

PowerShell, yazdığınız metne en uygun eşleşmeyi otomatik olarak tamamlayacaktır. Birden fazla eşleşme varsa, Tab tuşuna tekrar basıldığında mevcut seçenekler arasında geçiş yapar.

Gene PowerShell'i hızlı ve efektif kullanmak için sık sık kullanacağımız bir özellik.

Örneğin, ev klasöründe ( C:\Users\<KULLANICI ADI> )

```auto
Set-Location do<TAB>
```

Yaparsak, arguman ilk önce .\Documents\ olacak tekrar tab tuşuna basarsak .\Downloads\ olacaktır.