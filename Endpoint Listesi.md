
#### **DİL SEÇİM EKRANI**

**Dilleri getir:**

**GET  `/api/v1/languages`**

Response: Başarılı

```php
{
  "success": true,
  "data": [
    {
      "id": 1,
      "code": "tr",
      "name": "Türkçe",
      "iconUrl": "https://cdn.app.com/flags/tr.png"
    },
    {
      "id": 2,
      "code": "en",
      "name": "English",
      "iconUrl": "https://cdn.app.com/flags/en.png"
    }
  ]
}
```

Response: Hatalı

```php
{
  "success": false,
  "message": "Diller getirilemedi."
}
```

**Dil seçimi**

**Not:**  Uygulama ilk açılışındaki dil seçimi yerel olarak tutulur. Bu veri, daha sonrasında Kayıt endpoint'ine parametre olarak eklenir. 
Eğer kullanıcı kayıt olduktan sonra profil ayarlarından dilini değiştirmek isterse, o zaman endpoint olarak şu şekilde yazılabilir.

**PUT** **`/api/v1/users/me/language`**

```php
{
  "code": "tr"
}
```

**Response: Başarılı** 

```php
{
  "success": true,
  "data": {
    "language": {
      "code": "tr",
      "name": "Türkçe"
    }
  }
}
```

**Response: Hatalı**

```php
{
  "success": false,
  "message": "Dil güncellenemedi."
}
```

---
### ***LOGIN EKRANI**

**Giriş yap**

**POST `/api/v1/auth/login`**

```php
{
  "identifier": "string", 
  "password": "string"
}
```

**Response: Başarılı** 

```php
{
  "success": true,
  "data": {
    "accessToken": "string",
    "refreshToken": "string",
    "tokenType": "Bearer",
    "expiresIn": 3600,
    "user": {
      "id": 1,
      "fullName": "Ahmet Yılmaz",
      "email": "ahmet@email.com",
      "phone": "+905xxxxxxxxx",
      "userType": "FARMER",
      "languageCode": "tr"
    }
  }
}
```

Response: Hatalı

```php
{
  "success": false,
  "errors": [
    {
      "field": "identifier",
      "message": "Bu alan zorunludur."
    },
    {
      "field": "password",
      "message": "Şifre zorunludur."
    }
  ]
}
```

Response: Hatalı (Wrong Credentials)

```php
{
  "success": false,
  "message": "Email/telefon veya şifre hatalı."
}
```

Response: Hatalı (Rate Limit)

```php
{
  "success": false,
  "message": "Çok fazla deneme yaptınız. Lütfen daha sonra tekrar deneyin."
}
```

---
#### **TOKEN İŞLEMLERİ**

Token Yenileme 

POST `/api/v1/auth/refresh-token`

```php
{
  "refreshToken": "string"
}
```

**Response: Başarılı**

```php
{
  "success": true,
  "data": {
    "accessToken": "string",
    "refreshToken": "string",
    "tokenType": "Bearer",
    "expiresIn": 3600
  }
}
```

**Response: Hatalı**

```php
{
  "success": false,
  "message": "Geçersiz veya süresi dolmuş refresh token."
}
```

Token Doğrulama

GET **`/api/v1/users/me`**

**Response: Başarılı**

```php
{
  "success": true,
  "data": {
    "id": 1,
    "fullName": "Ahmet Yılmaz",
    "email": "ahmet@email.com",
    "phone": "+905xxxxxxxxx",
    "userType": "FARMER",
    "languageCode": "tr"
  }
}
```

**Response: Hatalı**

```php
{
  "success": false,
  "message": "Yetkisiz erişim."
}
```

---
#### **KAYIT OL  EKRANI**

**Register**

**POST `/api/v1/auth/register`**

```php
{
  "fullName": "...",
  "email": "...",
  "password": "...",
  "phone": "...",
  "userType": "FARMER",
  "languageCode": "tr",
  
  "location": {
	  "countryId": 1,
	  "cityId": 34,
	  "districtId": 123,
	  "latitude": 40.876545,
	  "longitude": 31.098268
},
  
  "interests": [1,2,3]
  "isTermsAccepted": true
}
```

**Response: Başarılı**

```php
{
  "success": true,
  "data": {
    "accessToken": "string",
    "refreshToken": "string",
    "tokenType": "Bearer",
    "expiresIn": 3600,
    "user": {
      "id": 1,
      "fullName": "Ahmet Yılmaz",
      "email": "ahmet@email.com",
      "phone": "+905xxxxxxxxx",
      "userType": "FARMER",
      "languageCode": "tr"
    }
  }
}
```

Response: Hatalı 1

```php
{
  "success": false,
  "errors": [
    {
      "field": "email",
      "message": "Geçersiz email formatı"
    },
    {
      "field": "password",
      "message": "Şifre en az 8 karakter olmalı"
    },
    {
      "field": "isTermsAccepted",
      "message": "Devam etmek için şartları ve gizlilik politikasını kabul etmelisiniz."
    },
    {
      "field": "location.latitude",
      "message": "Lütfen harita üzerinden bir konum seçiniz."
    }
  ]
}
```

**Response: Hatalı 2**

```php
{
  "success": false,
  "message": "Bu e-posta veya telefon zaten kullanımda."
}
```

---
#### **KONUM SEÇİMİ**

**Ülkeler:**

GET **`/api/v1/locations/countries`**

```php
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "Türkiye",
      "code": "TR"
    }
  ]
}
```

**Response: Başarılı**

```php
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "Türkiye",
      "code": "TR"
    },
    {
      "id": 2,
      "name": "United States",
      "code": "US"
    }
  ]
}
```

**Response: Hatalı**

```php
{
  "success": false,
  "message": "Ülkeler getirilemedi."
}
```

**Şehirler:**

GET **`/api/v1/locations/countries/{countryId}/cities`**

```php
{
  "success": true,
  "data": [
    {
      "id": 34,
      "name": "İstanbul"
    }
  ]
}
```

**Response: Başarılı** 

```php
{
  "success": true,
  "data": [
    {
      "id": 34,
      "name": "İstanbul"
    },
    {
      "id": 61,
      "name": "Trabzon"
    }
  ]
}
```

**Response: Hatalı**

```php
{
  "success": false,
  "message": "Şehirler getirilemedi."
}
```

İlçeler:

GET **`/api/v1/locations/cities/{cityId}/districts`**

```php
{
  "success": true,
  "data": [
    {
      "id": 6101,
      "name": "Ortahisar"
    }
  ]
}
```

**Response: Başarılı**

```php
{
  "success": true,
  "data": [
    {
      "id": 6101,
      "name": "Ortahisar"
    },
    {
      "id": 6102,
      "name": "Akçaabat"
    }
  ]
}
```

**Response: Hatalı**

```php
{
  "success": false,
  "message": "İlçeler getirilemedi."
}
```

---
#### **ŞİFREMİ UNUTTUM**

**Şifre sıfırlama isteği**

**POST `/api/v1/auth/forgot-password`**

```php
{
  "identifier": "string"
}
```

Response: Güvenlik için her zaman aynı dönülür

```php
{
  "success": true,
  "message": "Eğer bu e-posta/telefon sistemde kayıtlıysa, şifre sıfırlama linki gönderilmiştir."
}
```

**Kod doğrulama**

POST **`/api/v1/auth/verify-reset`**

```php
{
  "identifier": "string", // Kodun gönderildiği kanal
  "code": "string" // Kullanıcının girdiği kod
}
```

Response: Başarılı

```php
{
  "success": true,
  "data": {
    "resetToken": "string"
  }
}
```

Response: Hatalı

```php
{
  "success": false,
  "message": "Kod geçersiz veya süresi dolmuş."
}
```

**Yeni şifre belirleme**

POST **`/api/v1/auth/reset-password`**

```php
{
  "resetToken": "string",
  "newPassword": "string"
}
```

Response: Başarılı

```php
{
  "success": true,
  "message": "Şifre başarıyla güncellendi."
}
```

Response: Hatalı

```php
{
  "success": false,
  "message": "Token geçersiz veya süresi dolmuş."
}
```