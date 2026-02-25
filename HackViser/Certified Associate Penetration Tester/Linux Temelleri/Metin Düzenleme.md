Linux, metin dosyalarını oluşturma, düzenleme ve görüntüleme işlemleri için bir dizi güçlü araç sunar. Bu bölümde, komut satırından erişilebilen en popüler metin düzenleyicileri ve araçlarından birini ele alacağız:

nano

ve ileri düzey kullanıcıların vazgeçilmezi

vim

.

### Nano Metin Editörü

Nano, Linux tabanlı sistemlerde en çok kullanılan editörlerden biridir. Basit ve etkili bir metin editörüdür, aynı zamanda linux dağıtımları ile önyüklü olarak gelmektedir. Kullanmadan önce nano editörü hakkında herhangi bir ön bilgiye sahip olmamız gerekmez. Nano'da dosya üzerinde işlem yapmak için komut kullanılmaz, tüm temel işlemler editörün alt kısmında görüntülenir. Bunları

CTRL

tuşu ile tetikleyebiliriz, örneğin dosyayı kaydetmek için

CTRL+O

tuşlarına, editörden çıkmak için

CTRL+X

tuşlarına basmak yeterlidir.

Bir dosyayı nano editör ile düzenlemek için aşağıdaki komutu çalıştırın:

```auto
root@hackerbox:~$ nano note.txt
```

Yukarıdaki komut

note.txt

dosyasını

nano

editör ile açacaktır. Dosyayı düzenlemek için imleci hareket ettirip, istediğiniz metni girebilirsiniz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/nano-example-de92e5f97.webp)

Ekran görüntüsünün en altında, kısa açıklamaları olan iki satır görüyoruz.

düzeltme

(

^

) işareti, klavyemizde bulunan

CTRL

tuşumuzu temsil etmektedir.

**Kısayollar:**

- **CTRL + O:** Kaydet (Write Out).
- **CTRL + X:** Çıkış (Exit).
- **CTRL + W:** Arama (Where Is).
- **CTRL + K:** Satırı Kes.
- **CTRL + U:** Yapıştır.

Örneğin,

[CTRL + W]

tuşlarına bastığımızda, düzenleyicinin altında

Search:

satırı belirir, buraya aradığımız kelime veya kelimeleri girebiliriz. Şimdi

demo

kelimesini arayıp

[ENTER]

tuşuna bastığımızda, imleç eşleşen ilk kelimeye gider.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/nano-search-example-281805453.webp)

Bu şekilde metin içerisinde arama sağlayabiliriz.

note.txt

dosyası içerisinde yaptığımız değişiklikleri kaydetmek için,

CTRL + O

kısayolunu kullanıyoruz. Daha sonra

CTRL + X

kısayolunu kullanarak metin editöründen çıkış yapıyoruz.

Metin editöründen çıktıktan sonra, yazdığımız metnin gerçekten kaydedildiğini doğrulamak için

cat

komutu ile dosya içeriğini yazdırabiliriz.

cat

komutu, dosyaların içeriğini terminale yazdırmak için kullanılır.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/68a4d2f6-4913-4850-b2cd-ec08a7918b4c/nano-cat-example-34b63c38e.webp)

### Vim (Vi IMproved)

vim

(veya klasik

vi

), Linux dünyasının en güçlü editörüdür. Öğrenme eğrisi diktir ancak bir kez öğrenildiğinde klavyeden elinizi kaldırmadan şimşek hızında düzenleme yapmanızı sağlar. Fare kullanmadan her şeyi klavyeyle yaparsınız.

Vim ile dosya açmak:

```auto
vim script.sh
```

Vim Modları

Vim açıldığında **Normal Mod**da başlar. Bu modda yazı yazamazsınız, sadece komut verirsiniz.

1. **Normal Mod (Varsayılan):** Gezinme, kopyalama, silme işlemleri yapılır. 
    
    ESC
    
     tuşu her zaman sizi bu moda döndürür.
2. **Insert Modu (Ekleme):** Yazı yazma modudur. Normal moddayken 
    
    i
    
     tuşuna basarak geçilir. Sol altta 
    
    -- INSERT --
    
     yazar.
3. **Visual Mod (Seçim):** Metin seçmek (blok seçimi) için kullanılır. Normal moddayken 
    
    v
    
     tuşuna basarak geçilir.

Temel Vim Komutları ve Senaryoları (Normal Modda)

**Senaryo 1: Yazı yazmak**

1. Vim ile dosya açın: 
    
    vim test.txt
    
2. i
    
     tuşuna basarak Insert moduna geçin. (Sol altta 
    
    -- INSERT --
    
     yazar).
3. "Merhaba Dünya" yazın.
4. ESC
    
     tuşuna basarak Normal moda dönün.

**Senaryo 2: Bir satırı silmek**

1. Silmek istediğiniz satırın üzerine yön tuşlarıyla veya 
    
    h,j,k,l
    
     ile gelin.
2. dd
    
     tuşlayın. Satır silinecektir.

**Senaryo 3: Dosyayı Kaydedip Çıkmak**

1. Normal modda olduğunuzdan emin olun (
    
    ESC
    
    ).
2. :wq
    
     yazın (write and quit) ve 
    
    Enter
    
    a basın.

**Kısayol Tablosu:**

|Tuş|Eylem|
|---|---|
|i|Yazma moduna geç (Insert).|
|ESC|Normal moda dön.|
|:w|Kaydet (Write).|
|:q|Çık (Quit).|
|:wq|Kaydet ve Çık.|
|:q!|Kaydetmeden zorla çık.|
|dd|Satırı sil (Kes).|
|yy|Satırı kopyala.|
|p|Yapıştır.|
|u|Geri al (Undo).|
|/kelime|"kelime"yi ara. (<br><br>n<br><br> ile sonraki).|

### Diğer Editörler

- **
    
    view
    
    **: Vim'i sadece okuma modunda açar. Dosyayı yanlışlıkla değiştirme riskini önler.
    
    ```auto
    view onemli_dosya.txt
    ```
    
- **Grafiksel Editörler**: Eğer masaüstü ortamınız (GNOME, KDE vb.) varsa, 
    
    gedit
    
    , 
    
    kate
    
    , 
    
    VS Code
    
     (
    
    code .
    
    ) gibi grafiksel editörleri de kullanabilirsiniz.