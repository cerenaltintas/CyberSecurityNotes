PowerShell, Windows ve Active Directory'deki kullanıcı ve grupları yönetmek için güçlü bir araçtır. Bu, kullanıcı hesapları oluşturma ve silme, parolaları sıfırlama, grup üyeliğini yönetme ve daha fazlasını yapmanızı sağlar.

### Active Directory'ye Genel Bakış

Active Directory, Microsoft tarafından geliştirilmiş ve Windows Server işletim sisteminin bir bileşeni olan bir dizin hizmetidir. Ağınızdaki tüm domain'e katılmış cihazlar, kullanıcılar, yazıcılar, uygulamalar ve diğer kaynaklar hakkında merkezi bir veritabanı sağlar.

Kullanıcı hesaplarını tek bir merkezi konumdan oluşturmayı, yönetmeyi ve silmeyi sağlar. Ayrıca, kullanıcıların şifrelerini sıfırlamak ve parola politikalarını uygulamak gibi işlemleri gerçekleştirebilir ve kullanıcı profillerini ile erişim izinlerini yönetebilirsiniz.

Grup politikaları, aynı ayarları birden fazla kullanıcı veya cihaza kolayca uygulamanızı sağlar. Bu politikalar aracılığıyla yazılım dağıtımı, masaüstü ayarları ve güvenlik ayarları gibi çeşitli alanlarda tutarlılığı sağlayabilir ve kullanıcı ve bilgisayar davranışlarını kontrol edebilirsiniz.

Active Directory, küçük ağlardan büyük kurumsal ağlara kadar geniş bir yelpazede ölçeklenebilir. Binlerce kullanıcı ve cihaza kadar destek sunar ve ihtiyaçlarınıza göre altyapınızı genişletebilirsiniz.

RSAT

RSAT, açılımı Remote Server Administration Tools (Uzak Sunucu Yönetim Araçları) olan bir Microsoft teknolojisidir. Bu araçlar, Windows işletim sistemine sahip bir bilgisayardan uzaktaki Windows Server'ları yönetmenizi sağlar.

RSAT, sunuculara özgü çeşitli yönetim araçları içerir. Bu araçların bazıları grafiksel arayüzlü (GUI) araçlar iken bazıları da PowerShell cmdlet'leri olarak sunulur.

PowerShell, RSAT'ın bir parçası olarak yüklenen modüller aracılığıyla sunucu yönetimi için kapsamlı bir komut seti sağlar. Bu modüller, sunucu rollerine ve özelliklerine özgü cmdlet'ler içerir.

Get-ADUser Enumerating Users & Groups

Kurulumu

1. Başlat menüsünü açın.
2. Ayarlar'a gidin.
3. Uygulamalar'ı seçin.
4. Uygulamalar ve özellikler'e tıklayın.
5. Sağ panelde "İsteğe bağlı özellikler" seçeneğini bulun.
6. "Özellik ekle" butonuna tıklayın.
7. Açılan pencerede "Uzak Sunucu Yönetim Araçları"nı arayın.
8. Aramanızdan çıkan sonucu seçin.
9. "Kur" butonuna tıklayın.

### Kullanıcı ve Grup Yönetimi

Kullanıcıları ve grupları neden listeleyip, tespit edebilmeliyiz?

Kullanıcıları, grupları ve onların izinlerini listeleyerek ağdaki ve Active Directory/Windows makinelerdeki olası güvenlik açıklıklarını belirleyebilirsiniz. Örneğin, fazla yetkiye sahip kullanıcı hesapları veya istenmeyen üyelere sahip grupları bulabilirsiniz.

Buradaki komutların yükseltilmiş yetkiler istediğini unutmayın. Eğer kendi bilgisayarınızda bu komutları deniyor ve hata alırsanız PowerShell'i yönetici olarak açın.

Yerel Kullanıcılar

Get-LocalUser

Kullanıcıyı getirir. Eğer parametre verilmezse tüm kullanıcıları listeler.

```auto
PS C:\Windows\system32> Get-LocalUser

Name               Enabled Description
----               ------- -----------
Administrator      False   Built-in account for administering the computer/domain
DefaultAccount     False   A user account managed by the system.
Guest              False   Built-in account for guest access to the computer/domain
user               True
WDAGUtilityAccount False   A user account managed and used by the system for Windows Defender Application Guard scenarios.
```

New-LocalUser

Bilgisayarda yeni bir yerel kullanıcı hesabı oluşturur.

```auto
PS C:\Windows\system32> New-LocalUser -Name "j.doe" -Password (ConvertTo-SecureString -String 'password123' -AsPlainText -Force)

Name  Enabled Description
----  ------- -----------
j.doe True
```

Set-LocalUser

Mevcut bir yerel kullanıcı hesabının özelliklerini değiştirir.

```auto
Set-LocalUser -Name "j.doe" -Description "This is a test user."
```

Disable-LocalUser

Bir yerel kullanıcı hesabını devre dışı bırakır.

```auto
Disable-LocalUser -Name "j.doe"
```

Enable-LocalUser

Devre dışı bırakılmış bir yerel kullanıcı hesabını yeniden etkinleştirir.

```auto
Enable-LocalUser -Name "j.doe"
```

Remove-LocalUser

Bilgisayardan bir yerel kullanıcı hesabını siler.

```auto
Remove-LocalUser -Name "j.doe"
```

Yerel Gruplar

Get-LocalGroup:

Bilgisayardaki tüm yerel grupları listeler.

```auto
Get-LocalGroup
```

New-LocalGroup:

Bilgisayarda yeni bir yerel grup oluşturur.

```auto
New-LocalGroup -Name "Students"
```

Set-LocalGroup:

Mevcut bir yerel grubun özelliklerini değiştirir.

```auto
Set-LocalGroup -Name "Students" -Description "Improvise. Adapt. Overcome."
```

Add-LocalGroupMember:

Bir kullanıcıyı veya başka bir grubu belirli bir yerel gruba ekler.

```auto
Add-LocalGroupMember -Group "Students" -Member "j.doe"
```

Remove-LocalGroupMember:

Bir kullanıcıyı veya başka bir grubu belirli bir yerel gruptan kaldırır.

```auto
Remove-LocalGroupMember -Group "Students" -Member "j.doe"
```

Remove-LocalGroup:

Bilgisayardan bir yerel grubu siler.

```auto
Remove-LocalGroup -Name "Students"
```

Active Directory Kullanıcıları

Get-ADUser

Active Directory'den bir veya daha fazla kullanıcı hesabını sorgulayıp bilgilerini görüntüler.

Belirli bir kullanıcı adına göre arama

```auto
Get-ADUser "j.doe"
```

Tüm kullanıcıları listeleme

```auto
Get-ADUser -Filter *
```

New-ADUser

Active Directory'de yeni bir kullanıcı hesabı oluşturur.

```auto
New-ADUser -Name "j.doe" -SamAccountName j.doe -AccountPassword (ConvertTo-SecureString "sifre123!" -AsPlainText -Force)
```

Set-ADUser

Active Directory'de mevcut bir kullanıcı hesabının özelliklerini değiştirir.

Kullanıcının soyadını değiştirme

```auto
Set-ADUser -Identity "j.doe" -Surname "doe"
```

Remove-ADUser

Active Directory'den bir kullanıcı hesabını siler.

```auto
Remove-ADUser "j.doe"
```

Active Directory Grupları

Get-ADGroup:

Active Directory'den bir veya daha fazla güvenlik grubunu sorgulayıp bilgilerini görüntüler.

Belirli bir grup adına göre arama:

```auto
Get-ADGroup "Students"
```

Tüm güvenlik gruplarını listeleme:

```auto
Get-ADGroup -Filter *
```

New-ADGroup:

Active Directory'de yeni bir güvenlik grubu oluşturur.

Bu örnekte "Universal" grup kapsamı kullanılmıştır. Diğer kapsamlar ihtiyaca göre seçilebilir.

```auto
New-ADGroup -Name "Students" -GroupScope Universal
```

Set-ADGroup:

Active Directory'de mevcut bir güvenlik grubunun özelliklerini değiştirir.

Grubun açıklamasını değiştirme:

```auto
Set-ADGroup -Identity "Students" -Description "Learn as if you were to live forever"
```

Get-ADGroupMember:

Active Directory'deki belirli bir güvenlik grubunun üyelerini görüntüler.

"Students" grubunun üyelerini listeleme:

```auto
Get-ADGroupMember -Identity "Students"
```

Add-ADGroupMember

Bir kullanıcıyı bir güvenlik grubuna ekler.

```auto
Add-ADGroupMember -Identity "Students" -Members j.doe
```

Remove-ADGroupMember:

Bir kullanıcıyı veya başka bir grubu belirli bir güvenlik grubundan kaldırır.

```auto
Remove-ADGroupMember -Identity "Students" -Member "j.doe"
```

Remove-ADGroup:

Active Directory'den bir güvenlik grubunu siler.

```auto
Remove-ADGroup "Students"
```