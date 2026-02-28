Exploit modülü, zafiyetleri test etmek ve sistemlerdeki zafiyetleri istismar etmek için gerekli kodları içeren modüllerdir. Exploit modülleri, zafiyet içeren bir hedefe gereksinim duyar.

Exploit modüllerini kullanmak için zafiyetli

Supervisor 3.3.2

servisi çalışan bir sistemi hedefimiz olarak kullanalım.

MSFConsole'da aşağıdaki gibi arama yapalım.

```auto
search type:exploit supervisor
```

Çıkan sonuçlar arasındaki

exploit/linux/http/supervisor_xmlrpc_exec

modülünü

use

komutuyla kullanalım.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image17-afdaa44a7.webp)

Bir exploit modülünü seçtikten sonra otomatik olarak bir

payload

yapılandırılır. Otomatik olarak yapılandırılan bu payloadı daha sonra değiştirebiliriz.

Exploit modülleri genellikle aşağıdaki seçeneklerin yapılandırılmasını gerektirir.

- **RHOST:** Uzak hedefin IP adresi.
- **LHOST:** Dinleme makinesinin IP adresi. Genellikle kendi bilgisayarımızın IP adresiyle yapılandırırız.
- **PAYLOAD:** Bir exploit başarılı bir şekilde çalıştırıldıktan sonra çalıştırılacak kod. Örneğin sistemde bir kullanıcı oluşturmak, meterpreter oturumu açmak ya da shell almak olabilir.

options

komutunu kullanarak payload yapılandırmaları dahil gerekli tüm ayarları görüntüleyebiliriz.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image18-059d6c37e.webp)

Exploit Ayarları

- **RHOSTS:** Hedef makinenin IP adresini belirtmemiz gerekiyor.
- **RPORT:** Hedef makinenin port numarası, çalışan zafiyetli servis için otomatik olarak yapılandırılmış. Bu değeri değiştirmemize gerek yok.
- **TARGETURI:** Hedef makinede çalışan servisin end-point yolu otomatik olarak yapılandırılmış. Bu değeri değiştirmemize gerek yok.

Payload Ayarları

Exploiti seçtiğimizde otomatik olarak

linux/x64/meterpreter/reverse_tcp

payloadı yapılandırılmıştı. Bu payload 64 bit linux sistemde meterpreter session ı açmak için tcp protokolü üzerinden reverse shell yöntemini kullanıyor.

- **LHOSTS:** Dinleme makinesinin IP adresini belirtmemiz gerekiyor.
- **LPORT:** Dinleme makinesinin port numarası belirtilir. Otomatik olarak 4444 değeri ile yapılandırılmış. Bu değeri değiştirmemize gerek yok.

Exploit Hedefi

Exploit hedeflerine baktığımızda Supervisor servisinin

3.0a1-3.3.2

versiyonlarında bu exploitin çalıştığını görüyoruz.

Gerekli Ayarların Yapılandırılması

Hedef makine adresini ve dinleme adresini ayarlayalım.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image19-ea0fdb1f3.webp)

Exploit Etme

Gerekli ayarları yaptıktan sonra

check

komutu ile exploiti çalıştırmadan çalışacak mı bunu kontrol edebiliriz. Bu

check

komutunu her exploit desteklememektedir ancak şu an seçmiş olduğumuz exploit

check

komutunu destekliyor.

check

komutunu çalıştırdığımızda hedefin istismar edilebilir olduğu sonucunu gördük. Ardından

exploit

ya da

run

komutunu kullanarak exploiti çalıştırabiliriz.

exploit

komutunu çalıştırdık ve

meterpreter

oturumu almayı başardık.

![](https://storage.hackviser.com/file/hackviser-prod/trainings/sections/images/12f1e503-f9cf-4ef8-9453-59b4b1f03445/image20-b19c2a570.webp)