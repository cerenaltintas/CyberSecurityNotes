dir
 Belirtilen dizindeki dosyaları ve klasörleri listeler.

```auto
C:\Users\user>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user

03/18/2024  07:14 PM    <DIR>          .
03/18/2024  07:14 PM    <DIR>          ..
03/15/2024  11:30 PM    <DIR>          3D Objects
03/15/2024  11:30 PM    <DIR>          Contacts
03/18/2024  09:34 AM    <DIR>          Desktop
03/15/2024  11:30 PM    <DIR>          Documents
03/16/2024  09:55 AM    <DIR>          Downloads
03/15/2024  11:30 PM    <DIR>          Favorites
03/15/2024  11:30 PM    <DIR>          Links
03/15/2024  11:30 PM    <DIR>          Music
03/15/2024  11:30 PM    <DIR>          Pictures
03/15/2024  11:30 PM    <DIR>          Saved Games
03/15/2024  11:31 PM    <DIR>          Searches
03/15/2024  11:30 PM    <DIR>          Videos
               0 File(s)              0 bytes
              14 Dir(s)  20,309,082,112 bytes free

```

cd
 Mevcut dizini değiştirir. Tek nokta bulunulan klasörü çift nokta ise bir üst klasörü gösterir

```auto
C:\Users\user>cd Documents

C:\Users\user\Documents>
```

mkdir
 Yeni bir klasör oluşturur.

```auto
C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/15/2024  11:30 PM    <DIR>          .
03/15/2024  11:30 PM    <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  20,308,930,560 bytes free

C:\Users\user\Documents>mkdir newdir

C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:32 PM    <DIR>          .
03/18/2024  10:32 PM    <DIR>          ..
03/18/2024  10:32 PM    <DIR>          newdir
               0 File(s)              0 bytes
               3 Dir(s)  20,308,930,560 bytes free
```

rmdir
 Boş bir klasörü siler. 
```auto
C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:32 PM    <DIR>          .
03/18/2024  10:32 PM    <DIR>          ..
03/18/2024  10:32 PM    <DIR>          newdir
               0 File(s)              0 bytes
               3 Dir(s)  20,308,930,560 bytes free

C:\Users\user\Documents>rmdir newdir

C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:32 PM    <DIR>          .
03/18/2024  10:32 PM    <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  20,308,860,928 bytes free
```

copy
 Bir dosyayı kopyalar.

```auto
C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:35 PM    <DIR>          .
03/18/2024  10:35 PM    <DIR>          ..
03/18/2024  10:35 PM                 0 test.txt
               1 File(s)              0 bytes
               2 Dir(s)  20,308,324,352 bytes free

C:\Users\user\Documents>copy test.txt test1.txt
        1 file(s) copied.

C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:36 PM    <DIR>          .
03/18/2024  10:36 PM    <DIR>          ..
03/18/2024  10:35 PM                 0 test.txt
03/18/2024  10:35 PM                 0 test1.txt
               2 File(s)              0 bytes
               2 Dir(s)  20,308,324,352 bytes free
```

move
 Bir dosyayı veya klasörü taşır.

```auto
C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:36 PM    <DIR>          .
03/18/2024  10:36 PM    <DIR>          ..
03/18/2024  10:35 PM                 0 test.txt
03/18/2024  10:35 PM                 0 test1.txt
               2 File(s)              0 bytes
               2 Dir(s)  20,308,324,352 bytes free

C:\Users\user\Documents>move test.txt ..\Desktop
        1 file(s) moved.

C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:38 PM    <DIR>          .
03/18/2024  10:38 PM    <DIR>          ..
03/18/2024  10:35 PM                 0 test1.txt
               1 File(s)              0 bytes
               2 Dir(s)  20,308,176,896 bytes free
```

del
 Bir dosyayı siler. 
```auto
C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:38 PM    <DIR>          .
03/18/2024  10:38 PM    <DIR>          ..
03/18/2024  10:35 PM                 0 test1.txt
               1 File(s)              0 bytes
               2 Dir(s)  20,308,045,824 bytes free

C:\Users\user\Documents>del test1.txt

C:\Users\user\Documents>dir
 Volume in drive C has no label.
 Volume Serial Number is AE5B-68D3

 Directory of C:\Users\user\Documents

03/18/2024  10:39 PM    <DIR>          .
03/18/2024  10:39 PM    <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  20,308,045,824 bytes free
```

---

CMD ile basit birkaç komutu deneyimlediğimize göre PowerShell'e sıfırdan giriş yapabiliriz.