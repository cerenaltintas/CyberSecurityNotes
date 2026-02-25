### İzin Nedir ve Neden Önemlidir?

Linux, çok kullanıcılı bir sistem olduğu için her dosyanın kime ait olduğu ve kimin o dosyayla ne yapabileceği sıkı kurallara bağlanmıştır. Bu kurallara **Dosya İzinleri** denir.

**Neden İzinler Var?**

- **Gizlilik:** Kişisel dosyalarınızı (örneğin e-postalarınızı) başka kullanıcıların okumasını engellemek için.
- **Bütünlük:** Önemli sistem dosyalarının yetkisiz kişilerce değiştirilmesini veya silinmesini önlemek için.
- **Güvenlik:** Kötü amaçlı bir yazılımın (virüs vb.) sistem genelinde çalışmasını ve yayılmasını engellemek için.

Eğer izinler olmasaydı, herhangi bir kullanıcı sistemdeki kritik bir dosyayı silebilir ve sistemi çökertebilirdi.

### 1. İzinleri Okuma

Linux dosya sisteminde her dosya ve dizinin, sistemdeki kullanıcılar tarafından nasıl erişilebileceğini belirleyen izinleri vardır. Bu izinler, dosyanın güvenliğini ve bütünlüğünü sağlamak için kritiktir. İzin yapısını anlamak için ls -l komutunun çıktısını detaylıca incelememiz gerekir.

```auto
root@hackerbox:~$ ls -l
-rwxr--r-- 2 john development 4096 Jul  29 12:34 notes.txt
```

ls -l çıktısı örneği: -rwxr--r-- Bu ifade, aslında bir dizi karakterden oluşur ve her karakterin özel bir anlamı vardır.
 -l parametresi ile elde ettiğimiz çıktıdaki sütunların açıklamaları aşağıdaki gibidir:

|Sütun içeriği|Açıklama|
|---|---|
|d|Dosya türü. Eğer dizin ise <br><br>d<br><br>, dosya ise <br><br>-<br><br> karakteri ile gösterilir.|
|rwxr--r--|Dosya izinleri|
|2|Dosyaya/dizine verilen sabit bağlantı (hard link) sayısı|
|john|Dosya/dizinin sahibi olan kullanıcı|
|development|Dosya/dizinin sahibi olan grup|
|4096|Dosyanın boyutu veya dizin bilgilerini saklamak için kullanılan blok sayısı|
|Jul 29 12:34|Dosya/dizinin oluşturulma veya son düzenlenme tarihi|
|notex.txt|Dosya/dizinin ismi|
 r , w , x ve - Karakterleri İzinler temel olarak üç farklı yetki türü ve bir de yetkisizlik durumu ile ifade edilir:

- ** r (Read)**: Dosyanın içeriğini **okuma** iznini ifade eder. Eğer bu izin bir dizin (dizin) için verilmişse, o dizinin içindeki dosyaları listeleme ( ls ) yetkisi verir.
- ** w (Write)**: Dosyanın içeriğine **yazma** veya dosyayı düzenleyebilme iznini ifade eder. Bir dosya üzerinde değişiklik yapmak, içeriğini silmek veya üzerine yazmak için bu izne ihtiyaç vardır. Dizinler için ise, o dizinin içine yeni dosya oluşturma veya silme yetkisi verir.
- ** x (Execute)**: Dosyayı **çalıştırabilme** iznini ifade eder. Bu izin, genellikle scriptler (komut dosyaları) veya derlenmiş programlar için verilir. Eğer bir dosya çalıştırılabilir bir programsa ancak x izni yoksa, sistem bu dosyanın çalışmasına izin vermez. Dizinler için ise, o dizinin içine erişim ( cd ile girme) yetkisi verir.
- ** - (Tire)**: Eğer r , w veya x karakterlerinden herhangi biri yerine - yazılmışsa, o pozisyondaki izin **verilmemiş** demektir.

Kullanıcı, Grup ve Diğer (User, Group, Others) Linux izin sistemi, yetkileri üç farklı kitleye böler. ls -l çıktısındaki 10 karakterlik izin dizisinin ilk karakteri dosya tipini belirtirken, geri kalan 9 karakter üçerli gruplar halinde bu kitleleri temsil eder:

```auto
---         ---     ---
rwx         rwx     rwx
kullanıcı   grup    diğer
```

1. **Kullanıcı (User - u):**
    
    - İzin dizisinin ilk üçlü grubudur (2, 3 ve 4. karakterler).
    - Dosyanın veya dizinin **sahibi** olan kullanıcının yetkilerini ifade eder.
    - Genellikle dosyayı oluşturan kişi sahibidir.
2. **Grup (Group - g):**
    
    - İzin dizisinin ikinci üçlü grubudur (5, 6 ve 7. karakterler).
    - Dosyanın atandığı **gruba** dahil olan tüm kullanıcıların yetkilerini ifade eder.
    - Bu özellik, bir proje üzerinde çalışan birden fazla kullanıcının aynı dosyalara erişebilmesi için kullanılır.
3. **Diğer (Others - o):**
    
    - İzin dizisinin son üçlü grubudur (8, 9 ve 10. karakterler).
    - Sistemde bulunan, dosyanın sahibi olmayan ve dosyanın grubuna dahil olmayan **diğer tüm** kullanıcıların yetkilerini ifade eder.
    - Genellikle "dünya" (world) olarak da adlandırılır.

İzinleri Okuyalım

Öncelikle yukarıdaki örnekte verilen izinleri ( -rwxr-xr-- ) parçalayarak analiz edelim: 
1. ** - **: En baştaki karakter dosya tipini gösterir. - olduğu için bunun bir **dosya** olduğunu anlıyoruz ( d olsaydı dizin olurdu).
2. ** rwx (Sahip):** Dosya sahibi dosyayı okuyabilir ( r ), yazabilir ( w ) ve çalıştırabilir ( x ). Tam yetkiye sahiptir.
3. ** r-x (Grup):** Gruba dahil kullanıcılar dosyayı okuyabilir ( r ) ve çalıştırabilir ( x ), ancak dosyaya yazamazlar ( - ).
4. ** r-- (Diğerleri):** Diğer herkes dosyayı sadece okuyabilir ( r ). Yazamaz ve çalıştıramazlar.

**Örnek Çıktı Analizi:**

```auto
user@hackerbox:~$ ls -l script.sh
-rwxr-xr-- 1 mehmet yazilim 450 Aug 01 14:00 script.sh
```

- **Sahip (mehmet):** Okur, yazar, çalıştırır ( rwx ).
- **Grup (yazilim):** Okur, çalıştırır ( r-x ).
- **Diğerleri:** Sadece okur ( r-- ).

### 2. İzin Değerleri (Oktal)

İzinler sayılarla ifade edilir:

- **r (Read) = 4**
- **w (Write) = 2**
- **x (Execute) = 1**

|İzin|Sayısal Karşılık|Anlamı|
|---|---|---|
|**rwx**|7 (4+2+1)|Tam yetki.|
|**rw-**|6 (4+2)|Okur/Yazar.|
|**r-x**|5 (4+1)|Okur/Çalıştırır.|
|**r--**|4|Sadece Okur.|

İzinlerin Sayısal Karşılıkları Tablosu

|İzin Grubu|İzinler|Oktal Değer|Anlamı|
|---|---|---|---|
|**Sahip**|rwx|7|Oku, Yaz, Çalıştır|
|**Grup**|r-x|5|Oku, Çalıştır (Yazamaz)|
|**Diğer**|r--|4|Sadece Oku|
|**TOPLAM**|rwxr-xr--|**754**|Dosyanın tam izni|

### 3. İzinleri Değiştirme ( chmod )

**Örnek Senaryo: Bir scripti çalıştırılabilir yapma**
 script.sh için çalıştırma izni ekleme (755):

```auto
user@hackerbox:~$ ls -l script.sh
-rw-r--r-- 1 user user 0 Aug 01 12:00 script.sh
user@hackerbox:~$ chmod 755 script.sh
user@hackerbox:~$ ls -l script.sh
-rwxr-xr-x 1 user user 0 Aug 01 12:00 script.sh
```

**Herkese tam yetki (777) — güvensizdir:**

```auto
user@hackerbox:~$ chmod 777 dosya.txt
user@hackerbox:~$ ls -l dosya.txt
-rwxrwxrwx 1 user user 0 Aug 01 12:00 dosya.txt
```

**Sadece sahip okur/yazar (600):**

```auto
user@hackerbox:~$ chmod 600 ozel.txt
user@hackerbox:~$ ls -l ozel.txt
-rw------- 1 user user 0 Aug 01 12:00 ozel.txt
```
 notes.txt dosyasında diğer kullanıcılara ( o ) yazma izni ekleyelim:

```auto
root@hackerbox:~$ chmod o+w notes.txt
root@hackerbox:~$ ls -l notes.txt
-rw-rw-rw- 1 john development 4096 Jul 29 12:34 notes.txt
```

Tek seferde tüm gruplara tüm izinleri vermek isterseniz:

```auto
root@hackerbox:~$ chmod ugo+rwx notes.txt
root@hackerbox:~$ ls -l notes.txt
-rwxrwxrwx 1 john development 4096 Jul 29 12:34 notes.txt
```

### 4. Özel İzinler (SUID, SGID, Sticky)

Bu izinler güvenlik ve işbirliği için kritiktir.

|Ad|Sayısal|Nerede|Ne Yapar?|Örnek|
|---|---|---|---|---|
|**SUID**|4000|Dosya|Çalıştıran kişi, dosya sahibinin yetkisiyle çalıştırır.|passwd|
|**SGID**|2000|Dizin|İçinde oluşturulan dosyalar dizinin grubunu alır.|Ortak projeler.|
|**Sticky**|1000|Dizin|Sadece dosya sahibi dosyasını silebilir.|/tmp|

**Örnek: SUID Ayarlama**

```auto
user@hackerbox:~$ chmod 4755 dosya
user@hackerbox:~$ ls -l dosya
-rwsr-xr-x 1 root root 0 Aug 01 12:00 dosya
```

( x yerine s geldi. Dosya artık root yetkisiyle çalışacak).

**Örnek: Sticky Bit Ayarlama (/tmp dizini)**

```auto
user@hackerbox:~$ chmod 1777 /tmp
user@hackerbox:~$ ls -ld /tmp
drwxrwxrwt 10 root root 4096 Aug 01 12:00 /tmp
```
 ( t harfi Sticky Bit'i gösterir).

### 5. Umask Hesaplama

Varsayılan izinleri belirler. Standart değer 022 'dir. 
- **Dosya:** 666 - 022 = **644** ( rw-r--r-- )
- **Dizin:** 777 - 022 = **755** ( rwxr-xr-x )

Kendi umask değerinizi görmek için:

```auto
user@hackerbox:~$ umask
0022
```

### 6. Dosya Öznitelikleri ( chattr ve lsattr )

İzinlerden daha güçlü koruma sağlar. Bir dosyayı **değiştirilemez (immutable)** yapmak için kullanılır.

- chattr +i dosya : Dosyayı kilitler. Root bile silemez.
- lsattr dosya : Öznitelikleri gösterir.

```auto
user@hackerbox:~$ sudo chattr +i kritik_dosya.conf
user@hackerbox:~$ rm kritik_dosya.conf
rm: cannot remove 'kritik_dosya.conf': Operation not permitted
```

(Kilidi açmak için sudo chattr -i kullanılır).