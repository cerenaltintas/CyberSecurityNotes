Her ne kadar şuana kadar arayüz ile etkileşime giriyor olsak da arayüz Windows'u kullanmanın tek yolu değildir.

Sadece klavye kullanarak da etkileşime girebiliriz.

### Komut İstemi (cmd)

Komut İstemi, Windows'ta bulunan bir komut işlemcisidir. Metin tabanlı bir arayüz aracılığıyla bilgisayarlarını yönetmelerini sağlar.

Kullanıcıların dosya yönetimi, sistem yapılandırması, ağ ayarları, program yürütme ve diğer sistem görevlerini gerçekleştirmelerine imkan tanır. Komutlar çalıştırılırken parametreler alabilir.

Örneğin çalışan işlemlerin listesini öğrenmek için

```auto
tasklist
```

Oturum açan kullanıcının adını öğrenmek için

```auto
whoami
```

Ekranı temizlemek için

```auto
cls
```

yazabiliriz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/e1be5281-62bc-43a6-afbe-08f19de70f1b/cmd-9538349eb.webp)

### PowerShell

PowerShell, Microsoft tarafından geliştirilen ve Windows işletim sistemi için bir komut satırı arayüzü ve betikleme dilidir.

Gelişmiş bir komut satırı arayüzü ve betikleme ortamı sağlar. Klasik Komut İstemi'nden (CMD) daha gelişmiş özelliklere sahiptir ve birçok farklı görevi otomatikleştirmek için kullanılabilir.

PowerShell, .NET Framework'ü temel alan bir komut işlemcisidir. Bu, kullanıcıların .NET Framework kütüphanelerine erişebilecekleri ve PowerShell betikleriyle .NET nesnelerini manipüle edebilecekleri anlamına gelir. Bu da PowerShell'i bir bakıma nesneye yönelik yapar.

PowerShell, cmdlet'ler olarak adlandırılan küçük, tek amaçlı komutlar kullanır. Bu cmdlet'ler, çeşitli sistem yönetimi görevlerini gerçekleştirmek için kullanılır. Ayrıca, kullanıcılar PowerShell'de kendi betiklerini oluşturabilir ve PowerShell komut dosyaları (*.ps1 uzantılı dosyalar) aracılığıyla karmaşık işlemleri otomatikleştirebilir.

Microsoft, komut istemi yerine PowerShell kullanılmasını önermektedir ve komut istemiyle geriye dönük olarak uyumlu çalışmaktadır.

Şimdi ise PowerShell ile yazabileceğimiz hata tespit ederken kullanılabilecek komutları inceleyelim.

---

Bilgisayarın ağ adresi ayarlarını öğrenmek için

```auto
ipconfig
```

Komut ile birlikte kullanabileceğimiz ayarları görmek için

```auto
ipconfig -?
```

yazabiliriz.