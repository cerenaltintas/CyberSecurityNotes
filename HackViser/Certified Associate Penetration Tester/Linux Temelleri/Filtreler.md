Filtreler, düz metni (bir dosyada saklanan ya da başka bir program tarafından üretilen) standart girdi olarak alan, anlamlı bir biçime dönüştüren ve daha sonra standart çıktı olarak döndüren programlardır. Linux çok sayıda filtreye sahiptir.

### Filtreleme ve Pipe (|) Mantığı Nedir?

Linux'ta bir komutun çıktısı, başka bir komutun girdisi olabilir. Bunu sağlayan mekanizmaya Boru Hattı (Pipeline) denir ve | işareti ile gösterilir.

**Nasıl Çalışır?** 
Bir fabrikadaki üretim bandı gibi düşünün.
1. **Hammadde:** Bir dosyadan okunan metin.
2. Makine 1 (Komut 1): Metni okur ve işler (Örn: cat).
3. **Bant (Pipe |): İşlenmiş veriyi bir sonraki makineye taşır.
4. Makine 2 (Komut 2): Gelen veriyi süzer (Örn: grep).
5. **Ürün:** Ekrana gelen filtrelenmiş sonuç.

Bu sayede, tek başına basit olan komutlar birleşerek çok karmaşık işleri yapabilir hale gelir.

### 1. Yönlendirme (Redirection)

Linux'ta her programın 3 kapısı vardır:

1. **Giriş (STDIN - 0):** Klavye.
2. **Çıkış (STDOUT - 1):** Ekran.
3. **Hata (STDERR - 2):** Hata mesajları (Ekran).

Bu kapıları dosyalara yönlendirebiliriz.

| Operatör | Açıklama                                            | Örnek Komut ve Çıktısı                                   |
| -------- | --------------------------------------------------- | -------------------------------------------------------- |
| >        | Çıktıyı dosyaya yaz (Eskisini siler).               | ls > liste.txt<br>(Ekrana bir şey basmaz, dosyaya yazar) |
| >>       | Çıktıyı dosyanın **sonuna ekler**.                  | echo "Son satır" >> not.txt                              |
| 2>       | Sadece hataları dosyaya kaydeder.                   | ls /olmayan_dizin 2> hata.txt                            |
| <        | Dosyayı komuta girdi olarak verir.                  | wc -l < liste.txt                                        |
| \|       | Birinci komutun çıktısını ikinciye gönderir (Pipe). | cat dosya \| grep "aranan"                               |

**Örnek Senaryo: Hataları Gizleyerek Arama Yapmak**
find komutu erişemediği dizinler için "Permission denied" hatası basar. Bunları /dev/null (kara delik) dosyasına atarak temiz bir çıktı alalım.

```auto
user@hackerbox:~$ find / -name "gizli_dosya" 2> /dev/null
/home/admin/gizli_dosya
```
(Ekranda hata mesajları görünmez, sadece bulunan sonuç görünür).

### 2. Metin İşleme Araçları

Örnek olarak isimler.txt dosyamız olsun:

```auto
user@hackerbox:~$ cat isimler.txt
Ali Veli
Ayşe Yılmaz
Mehmet Öz
Ali Veli
```

**Cat**
Cat komutunun temel amacı bir veya birden fazla metin dosyasının içeriğini terminalde göstermektir. Bu komutu kullanarak dosya içeriklerini hızlı bir şekilde görüntüleyebilmekteyiz.
```auto
root@hackerbox:~$ cat /etc/ssh/sshd_config
# Port 22
# AddressFamily any
# ListenAddress 0.0.0.0
# ListenAddress ::
PermitRootLogin no
PasswordAuthentication yes
PermitEmptyPasswords no
ChallengeResponseAuthentication no
UsePAM yes
```
Yukarıdaki örnekte, SSH servisinin /etc/ssh/sshd_config yolundaki ayar dosyasının içeriği cat komutu ile ekrana yazdırılmıştır.

**Head