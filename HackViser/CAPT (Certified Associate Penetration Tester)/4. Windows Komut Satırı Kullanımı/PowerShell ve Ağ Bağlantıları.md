PowerShell, ağ ayarlarını yönetmek için güçlü bir araçtır. Birçok cmdlet'i kullanarak ağ kartlarını listeleyebilir, bağlantı durumlarını kontrol edebilir, IP adreslerini yapılandırabilir ve daha fazlasını yapabilirsiniz. Biz sadece temel kısımları inceleyeceğiz.

## Ağ Hakkında Bilgi Edinme

Get-NetIPAddress komutu, bir bilgisayarın ağ arabirimlerine atanmış IP adreslerini ve diğer IP yapılandırma bilgilerini almanıza olanak tanır.

```auto
Get-NetIPAddress
```

Diğer kullanabileceğimiz komutlar ise CMD'den kalma ve halen kullanılan araçlardır.

IPConfig

"Internet Protocol Configuration"ın kısaltmasıdır ve ağ bağlantılarıyla ilgili IP yapılandırma bilgilerini görüntülemek için kullanılır. Bilgisayarın mevcut ağ bağlantılarına atanan IP adreslerini, alt ağ maskelerini, varsayılan ağ geçitlerini ve diğer ağ yapılandırma bilgilerini listeler.

```auto
PS C:\> ipconfig

Windows IP Configuration


Ethernet adapter Ethernet Instance 0:

   Connection-specific DNS Suffix  . :
   Site-local IPv6 Address . . . . . : fec0::e9d4:ba34:6516:c0c1%1
   Link-local IPv6 Address . . . . . : fe80::e9d4:ba34:6516:c0c1%6
   IPv4 Address. . . . . . . . . . . : 10.0.2.15
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::2%6
                                       10.0.2.2
```

Netstat

Bilgisayarınızın bağlantı noktalarını görüntülemek için kullanılan bir araçtır.

```auto
PS C:\> netstat

Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    10.0.2.15:62553        SRV2019:domain         TIME_WAIT
  TCP    [::1]:389              SRV2019:49531          ESTABLISHED
  TCP    [::1]:389              SRV2019:49551          ESTABLISHED
  TCP    [::1]:389              SRV2019:49558          ESTABLISHED
  TCP    [::1]:389              SRV2019:49677          ESTABLISHED
  TCP    [::1]:389              SRV2019:49678          ESTABLISHED
  TCP    [::1]:389              SRV2019:49683          ESTABLISHED
  TCP    [::1]:49531            SRV2019:ldap           ESTABLISHED
  TCP    [::1]:49551            SRV2019:ldap           ESTABLISHED
  ...
```

Nslookup

Bir alan adının DNS (Domain Name System) sunucularında çözülmesini sağlayan bir araçtır. Bir alan adına karşılık gelen IP adresini bulmak için nslookup kullanılır.

```auto
PS C:\> nslookup example.com
Server:  localhost
Address:  ::1

Non-authoritative answer:
Name:    example.com
Addresses:  2606:2800:220:1:248:1893:25c8:1946
          93.184.216.34
```

ARP

Açılımı Address Resolution Protocol olmakla birlikte, bir ağdaki IP adreslerini, fiziksel MAC adreslerine eşlemek için kullanılan bir protokoldür. ARP komutu, ARP önbelleğini yönetir ve bu önbellekteki girişleri listeler.

```auto
PS C:\> arp -a

Interface: 10.0.2.15 --- 0x6
  Internet Address      Physical Address      Type
  10.0.2.2              52-55-0a-00-02-02     dynamic
  10.0.2.3              52-55-0a-00-02-03     dynamic
  10.0.2.255            ff-ff-ff-ff-ff-ff     static
  224.0.0.22            01-00-5e-00-00-16     static
  224.0.0.251           01-00-5e-00-00-fb     static
  224.0.0.252           01-00-5e-00-00-fc     static
  239.255.255.250       01-00-5e-7f-ff-fa     static
  255.255.255.255       ff-ff-ff-ff-ff-ff     static
```

## Bağlantıyı Test Etme

Test-NetConnection komutu, bir ağ bağlantısının durumunu bir bilgisayara ping atarak test etmek için kullanılır.

```auto
Test-NetConnection
```

## Dosya İndirme

Invoke-WebRequest

, web sayfaları ve web hizmetleriyle etkileşim kurmak için kullanılan bir cmdlet'tir. HTTP/HTTPS istekleri göndermenize ve bu web kaynaklarından veri almanızı veya işlemler yapmanızı sağlar.

Dosya indirmek için komutu aşağıdaki gibi kullanabiliriz.

```auto
Invoke-WebRequest -Uri "https://upload.wikimedia.org/wikipedia/commons/a/af/PowerShell_Core_6.0_icon.png" -OutFile "powershell.png"
```

Burada Uri kısmı web adresini OutFile ise kaydedilecek dosya ismini ifade eder.