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
