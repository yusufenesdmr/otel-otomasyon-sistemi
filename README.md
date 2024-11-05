# Otel Konaklama Sistemi Projesi

Bir otel için otomasyon sistemi geliştirerek, rezervasyon, oda, müşteri ve ödeme yönetimini daha verimli hale getirmek.

## Proje Özeti

Otel Otomasyon Sistemi, aşağıdaki kullanıcı türlerini ve işlevleri destekler:
- **Müşteriler**: Otel odalarını görüntüleyebilir, rezervasyon yapabilir, yorum bırakabilir, puan verebilir, konaklama geçmişlerini kaydedebilir ve otel hizmetlerini (restoran, spa vb.) kullanabilir.
- **Otel Yöneticileri**: Oda bilgileri, fiyatlandırmalar, müşteri bilgileri, rezervasyonlar, otel etkinlikleri ve hizmetler hakkında bilgi ekleyebilir ve düzenleyebilir.
- **Oda Yönetimi**: Otel odalarının durumu, rezervasyonları ve oda tipleri gibi çeşitli faktörleri içerir. 
- **Fatura**:otel hizmetlerinden yararlanan müşteriler için faturalama işlemlerini düzenler, takip eder ve yönetir.
  
Bu veri tabanı modeli; otel, odalar, müşteriler, rezervasyonlar, hizmetler, personel, faturalama, geri bildirimler ve kampanyalar gibi birçok varlığı kapsar.

## DataBase Structure

### Entitys (Tables) and Attributes

#### 1. Customer
- **Cus_id** (PK): Müşterinin kimlik numarası.
- **Name**: Müşterinin adı.
- **Phone**: Müşterinin telefon numarası.
- **Email**: Müşterinin mail adresi.

#### 2. Today Price
- **Price** (PK): Oda ücreti.
- **Available Room**: Boş oda.
- **Date**: Odanın ücretinin tarihi.

#### 3. Room
- **Number** (PK): Oda numarası.
- **Room_Type**: Sanatçının adı.
- 
#### 4. Hotel
- **Hotel_id** (PK): Otelin kimlik numarası.
- **Location**: Otelin adresi.
- **Name**: Otelin ismi.

#### 5. Bill 
- **Bill_id** (PK): Fatura kimlik numarası.
- **Date**: Faturanın oluşturulma tarihi.
- **Amount**: Faturanin bedel miktarı.
- **BName**: Faturayı ödeyen kişinin adı.
- 
#### 6. Reservation
- **Reservation_id**: Faturayı ödeyen kişinin adı
- **Date**: Rezervasyon tarihi.
  
### E Relations

1. **Customer - Today Price**: Her müşteri birden fazla günlük ücret ödeyebilir. (**M:N**).
2. **Customer - Bill**: Her müşterinin bir tane faturası mevcuttur. (**1:N**).
3. **Customer - Room**: Her müşteri birden fazla oda kiralayabilir. (**N:1**).
4. **Room - Hotel**: Bir otelin birden fazla odası vardır. (**N:1**).
