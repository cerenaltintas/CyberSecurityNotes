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

**Canlı Log Takibi (tail -f):**
Bir log dosyasını sürekli izlemek (örneğin bir sunucuya gelen istekleri anlık görmek) için -f (follow) parametresi kullanılır.

```auto
user@hackerbox:~$ tail -f /var/log/syslog
Aug 1 10:00:01 server CRON[123]: (root) CMD (command)
Aug 1 10:05:01 server sshd[456]: Accepted password for user...
```

(Yeni log düştükçe ekran akar. Çıkmak için CTRL+C).

**Sort**
sort komutu, verilen dosyanın içeriğini alfabetik sıralar.

```auto
root@hackerbox:~$ cat names.txt
Bob
Charlie
Alice

root@hackerbox:~$ sort names.txt
Alice
Bob
Charlie
```
Yukarıdaki örnekte, "names.txt" içerisinde yer alan isimleri "alfabetik" olarak ekrana yazdırdık.

**Uniq**
uniq komutu, ardışık olarak tekrar eden satırları filtreleyerek dosya içerisindeki benzersiz satırları gösterir.

Genellikle sort komutu ile birlikte kullanılır çünkü tek başına kullanıldığında sadece ardışık olarak tekrar eden satırları tespit eder.

```auto
root@hackerbox:~$ cat names.txt
Alice
Charlie
Alice
Bob

root@hackerbox:~$ sort names.txt | uniq
Alice
Bob
Charlie
```
-c: Tekrar sayısını gösterir (Count).

**Örnek: Kimden kaç tane var sayalım**
```auto
user@hackerbox:~$ sort isimler.txt | uniq -c
      2 Ali Veli
      1 Ayşe Yılmaz
      1 Mehmet Öz
```

**Grep**
grep komutu, dosyalar içindeki belirli metin dizelerini aramak, satırları filtrelemek ve eşleşen sonuçları göstermek için kullanılır.

grep çok güçlü bir araçtır ve log dosyaları, konfigürasyon dosyaları veya herhangi bir metin dosyası üzerinde aramalar yapmak için sıkça kullanılır.

```auto
root@hackerbox:~$ grep '192.168.1.1' /var/log/apache2/access.log
192.168.1.1 - - [15/Mar/2024:10:00:00 +0000] "GET /index.html HTTP/1.1" 200 612 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
192.168.1.1 - - [15/Mar/2024:10:00:02 +0000] "POST /login.php HTTP/1.1" 200 452 "http://example.com/login" "Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N)"
192.168.1.1 - - [15/Mar/2024:10:00:03 +0000] "GET /wp-admin HTTP/1.1" 403 497 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_6)"
```

Bu komut, Apache 2 web sunucusuna ait erişim loglarının içerisinde yalnızca IP adresi 192.168.1.1 olan kayıtları ekrana yazdıracaktır.

**İleri Düzey grep Parametreleri:**

- -i: Büyük/küçük harf duyarsız.
- -v: Eşleşmeyenleri göster (hariç tut).
- -r: Dizin içinde özyineli (recursive) arama.

**Wc**
wc (word count) komutu, dosyaların ne kadar büyük olduğunu veya ne kadar veri içerdiğini hızlıca anlamanızı sağlar.
```auto
root@hackerbox:~$ wc /etc/passwd
46   67 2544 /etc/passwd
```

Yukarıdaki örnekte wc komutu, Linux işletim sistemlerindeki kayıtlı kullanıcıların listesini içeren /etc/passwd dosyasının sırasıyla satır, kelime ve toplam karakter sayısını getirmiştir.

|Sütun değeri|Açıklama|
|---|---|
|46|Satır sayısı|
|67|Kelime sayısı|
|2544|Karakter sayısı|
|/etc/passwd|Dosya yolu|
**Cut**
Satırları böler ve istediğiniz sütunu alır. /etc/passwd dosyası buna en iyi örnektir.

```auto
user@hackerbox:~$ cut -d ":" -f 1 /etc/passwd | head -n 3
root
daemon
bin
```
(-d: Ayırıcı karakter [:], -f: Sütun numarası [1]).

**Awk**
awk komutu metin ve veri işleme görevleri için tasarlanmıştır ve özellikle sütun bazlı verilerle çalışırken oldukça etkilidir. Dosyaları satır satır okuyup, her satırı alanlara (sütunlara) ayırır ve belirtilen koşullara göre işlem yapar. awk, karmaşık metin işlemleri için çok sayıda fonksiyon ve kontrol yapıları sunar.

```auto
root@hackerbox:~$ cat names.txt
John Doe
Emily Clark
Alex Turner

root@hackerbox:~$ awk '{print $1}' names.txt
John
Emily
Alex
```
Bu örnekte, names.txt adlı bir dosya içerisinde üç isim-soyisim çifti bulunmaktadır: John Doe, Emily Clark ve Alex Turner. awk '{print $1}' names.txt komutu, awk programını kullanarak bu dosyanın içeriğini işler. awk, metin dosyalarını satır satır okuyarak her satırı boşluk veya tab karakterlerine göre alanlara ayırır. Bu örnekte {print $1} ifadesi, her satırın ilk alanını (yani ismi) yazdırması talimatını verir.

**Gelişmiş Örnek: Süreç Listesi**
ps aux çıktısından sadece Kullanıcı Adı ($1) ve Komut ($11) sütunlarını alalım.

```auto
user@hackerbox:~$ ps aux | awk '{print $1, $11}' | head -n 3
USER COMMAND
root /sbin/init
root [kthreadd]
```

**Sed**
sed (stream editor) komutu metinleri işlemek, değiştirmek, eklemek, silmek veya dosyalar arasında yer değiştirmek gibi çeşitli metin düzenlemeleri yapabilen bir araçtır.

sed komutu, genellikle metinleri filtrelemek ve dönüştürmek için kullanılır.

```auto
root@hackerbox:~$ cat names.txt
Alice
Charlie
Bob

root@hackerbox:~$ sed 's/Alice/George/' names.txt
George
Charlie
Bob
```
Yukarıdaki örnekte, names.txt içerisinde bulunan Alice ismi, sed komutu yardımıyla George olarak değiştirilmiştir. Ancak, sed komutunun dosyada değişiklik yapmayıp, yalnızca ekrana yeni yapılan değişikliği yazdırmıştır. Dosyayı kalıcı değiştirmek için -i parametresi kullanılır.

**Tee**
Çıktıyı hem ekrana basar hem dosyaya yazar.

```auto
user@hackerbox:~$ echo "Log Kaydı" | tee log.txt
Log Kaydı
```

**Diff**
İki dosya arasındaki farkları gösterir.
```auto
user@hackerbox:~$ diff dosya1.txt dosya2.txt
< Eski satır
> Yeni satır
```

**Tr**
Karakter değişimi yapar.
**Örnek: Küçük harfleri büyük yapalım**

```auto
user@hackerbox:~$ echo "merhaba" | tr "a-z" "A-Z"
MERHABA
```