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

**Head**
head komutu, belirtilen bir dosyanın en başından belirli sayıda satırı görüntülemek için kullanılır. Varsayılan olarak, head komutu dosyanın ilk 10 satırını gösterir, ancak bu sayı -n parametresi ile değiştirilebilir.
Bu komut, dosya içeriğinin tamamını değil, sadece başlangıç kısmını hızlıca gözden geçirmek istediğinizde kullanışlıdır.

```auto
root@hackerbox:~$ head -n 3 /var/log/apache2/access.log
192.168.1.1 - - [15/Mar/2024:10:00:00 +0000] "GET /index.html HTTP/1.1" 200 612 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
192.168.1.2 - - [15/Mar/2024:10:00:02 +0000] "POST /login.php HTTP/1.1" 200 452 "http://example.com/login" "Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N)"
192.168.1.3 - - [15/Mar/2024:10:00:03 +0000] "GET /wp-admin HTTP/1.1" 403 497 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_6)"
```

Yukarıdaki örnekte, Apache2 Web Server servisine ait /var/log/apache2/access.log yolundaki erişim kayıtlarını barındıran dosyanın içeriğinin ilk 3 satırı ekrana yazdırılmıştır.

**Tail**
tail komutu, belirtilen bir dosyanın sonundan itibaren belirli sayıda satırı görüntülemek için kullanılır. Varsayılan olarak, tail komutu dosyanın son 10 satırını gösterir, ancak bu sayı -n parametresi ile değiştirilebilir.
Bu komut, özellikle log dosyaları gibi sürekli büyüyen dosyaların en son eklenen içeriğini gözlemlemek için son derece yararlıdır.

```auto
root@hackerbox:~$ tail -n 3 /var/log/auth.log
Mar 15 12:00:00 servername sshd[23456]: Failed password for invalid user admin from 192.168.1.1 port 54321 ssh2
Mar 15 12:01:00 servername sshd[23457]: Accepted password for user1 from 192.168.1.2 port 65432 ssh2
Mar 15 12:02:00 servername sshd[23458]: Failed password for user2 from 192.168.1.3 port 76543 ssh2
```
Yukarıdaki örnekte,  auth.log dosyasının son üç satırı ekrana yazdırılmıştır. auth.log dosyası, Linux sisteminde kullanıcı kimlik doğrulama işlemleri ile ilgili olayların kaydedildiği bir log dosyasıdır.