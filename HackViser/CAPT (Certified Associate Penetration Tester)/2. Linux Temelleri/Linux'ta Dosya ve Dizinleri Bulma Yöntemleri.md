Linux'ta dosya ve dizin arama işlemleri, kullanıcıların dosya sistemleri üzerinde etkili bir şekilde gezinmelerini sağlar. Bu bölümde, find, locate ve which komutları kullanılarak dosya ve dizinleri nasıl bulabileceğinizden bahsedeceğiz. Bu komutlar, farklı senaryolar ve ihtiyaçlar için uygun çözümler sunar.

### find Komutu ile Arama

find komutu, belirli kriterlere göre dosya ve dizinleri aramak için kullanılır. Derinlemesine arama yapabilme yeteneği ile, büyük ve karmaşık dosya sistemlerinde etkili sonuçlar üretir.

**Genel Kullanım:**

find [NEREDE] [KRİTER] [EYLEM]

Temel Aramalar

| Kriter                   | Örnek Komut               | Açıklama                                |
| ------------------------ | ------------------------- | --------------------------------------- |
| **İsim**                 | find / -name "notlar.txt" | Tam ismi "notlar.txt" olanı bulur.      |
| **İsim (Harf Duyarsız)** | find . -iname "ReSiM.Jpg" | Büyük/küçük harfe takılmadan bulur.     |
| **Tür**                  | find /home -type d        | Sadece dizinleri (d) bulur. (f: dosya). |
| **Boyut**                | find / -size +100M        | 100 Megabyte'tan büyük dosyaları bulur. |
| **Kullanıcı**            | find /var -user www-data  | Sahibi www-data olan dosyaları bulur.   |

**Örnek Senaryo: İsimle Arama (-name)**

```auto
user@hackerbox:~$ find . -name "*.txt"
./Belgeler/notlar.txt
./Masaüstü/yapilacaklar.txt
./İndirilenler/liste.txt
./.cache/gecici.txt
```

_Bulunduğumuz dizin ve altındaki tüm dizinlerde sonu .txt ile biten dosyaları listeledik._

**Örnek Senaryo: Türe Göre Arama (-type)** 

Sadece ssh ismindeki dizinleri bulmak için:

```auto
user@hackerbox:~$ find /etc -type d -name "ssh"
/etc/ssh
```

_Eğer -type d demeseydik, ssh ismindeki dosyaları veya linkleri de bulabilirdi._

**Örnek Senaryo: Boyuta Göre Arama (-size)** 1GB'dan büyük dosyaları bulmak için:

```auto
user@hackerbox:~$ find / -size +1G
/var/log/syslog.1
/home/user/film.mkv
/var/lib/mysql/ibdata1
```

_Disk dolduğunda yer açmak için en çok kullanılan yöntemdir._

Mantıksal Operatörler (AND, OR, NOT)

- **VE (-a):** 
    Varsayılandır. Hem txt olsun HEM 1MB'dan büyük olsun.
    
    ```auto
    user@hackerbox:~$ find . -name "*.txt" -size +1M
    ./buyuk_notlar.txt
    ```
    
- **VEYA (-o):** 
  Jpg VEYA png olsun.
    
    ```auto
    user@hackerbox:~$ find . -name "*.jpg" -o -name "*.png"
    ./resim.jpg
    ./logo.png
    ./screenshot.png
    ```
    
- **DEĞİL (-not):** 
  Sahibi root OLMAYANLAR.
    
    ```auto
    user@hackerbox:~$ find . -not -user root
    ./home/user/dosya.txt
    ./tmp/test.tmp
    ```
    

Bulunan Dosyaya Komut Uygulama (-exec ve xargs)

En güçlü özelliktir. Bulduğu her dosya için bir komut çalıştırır.

**Örnek:**

.tmp uzantılı tüm dosyaları bul ve sil.

```auto
user@hackerbox:~$ find . -name "*.tmp" -exec rm {} \;
```

- {}: Bulunan dosya isminin yerini tutar.
- \; : Komutun bittiğini belirtir.

**xargs Kullanımı:** Çok fazla dosya bulunduğunda

xargs daha performanslıdır.

```auto
user@hackerbox:~$ find . -name "*.log" | xargs rm
```

### locate Komutu ile Arama
 locate komutu, sistemdeki dosyaları bulmak için kullanılır.

locate, updatedb adlı bir veritabanını kullanır. Bu veritabanı, sisteminizdeki dosyaların bir dizinini içerir ve locate komutu bu veritabanında hızlı bir şekilde arama yapar.

- **Temel Kullanım**:

```auto
user@hackerbox:~$ locate notlar.txt
/home/user/Belgeler/notlar.txt
/home/user/Yedek/notlar.txt
```

locate komutunun hızlı sonuçlar vermesi, dosya sistemindeki değişikliklerin updatedb tarafından periyodik olarak güncellenmesine bağlıdır. Bu yüzden, çok yeni dosyaları bulamayabilir. Veritabanını manuel güncellemek için sudo updatedb komutu çalıştırılabilir.

### which Komutu ile Komut Dosyalarını Bulma

which komutu, belirli bir komutun yolu hakkında bilgi edinmek için kullanılır. Bu, özellikle birden fazla sürümü yüklü olan programların hangisinin kullanıldığını anlamak için faydalıdır.

- **Temel Kullanım**:

```auto
user@hackerbox:~$ which python
/usr/bin/python
```

Bu komut, python komutunun hangi yolda olduğunu gösterir. Bu, genellikle sistemdeki varsayılan python sürümünün konumunu öğrenmek için kullanılır.

### 4. grep ile Dosya İÇİNDE Arama

Dosya ismini değil, dosyanın **içindeki yazıyı** arar.

**Örnek Senaryo:**

server.log dosyasında "Error" geçen satırları bulalım.

```auto
user@hackerbox:~$ grep "Error" server.log
[2023-10-01 10:00] Error: Connection timeout
[2023-10-01 10:05] Error: Database unreachable
[2023-10-01 10:10] Error: Service stopped
```

**Regex (Düzenli İfade) Tablosu ve Örnekler:**

|Sembol|Anlamı|Örnek Komut|Eşleşen|
|---|---|---|---|
|^|Satır başı|grep "^Hata" log.txt|"Hata oluştu" (Evet), "Bir Hata" (Hayır)|
|$|Satır sonu|grep "tamam$" log.txt|"İşlem tamam" (Evet), "tamamlandı" (Hayır)|
|.|Herhangi bir karakter|grep "k.t" kelimeler.txt|kat, küt, kıt|
|*|Öncekinin tekrarı|grep "ab*" kod.txt|a, ab, abb, abbb|

**Pratik Örnek: Regex ile Arama** Satır başı "User" ile başlayan satırları bul:

```auto
user@hackerbox:~$ grep "^User" config.txt
User: admin
User: guest
```

**Örnek: Tüm Dizinde Arama (-r)**

/var/log içindeki tüm dosyalarda "Error" kelimesini ara (büyük/küçük harf duyarsız).

```auto
user@hackerbox:~$ grep -r -i "error" /var/log/
/var/log/syslog:Oct 1 12:00:00 Error: Disk full
/var/log/auth.log:Oct 1 12:05:00 Failed password
/var/log/kern.log:Oct 1 12:10:00 I/O Error
```

### Özet

Linux'ta dosya ve dizin arama işlemleri, find, locate ve which komutları ile kolayca gerçekleştirilebilir. 
find komutu, derinlemesine ve kriter bazlı aramalar için idealdir. locate komutu, hızlı sonuçlar elde etmek istediğinizde kullanışlıdır ancak en güncel sonuçları sağlamayabilir.
which komutu ise, özellikle komutların sistemdeki yerlerini bulmak için kullanılır. Bu araçlar, Linux kullanıcılarının dosya sistemleri üzerinde etkin bir şekilde gezinmelerini ve ihtiyaç duydukları dosyaları ve programları bulmalarını sağlar.