# Otel Konaklama Sistemi Projesi

Bir otel için otomasyon sistemi geliştirerek, rezervasyon, oda, müşteri ve ödeme yönetimini daha verimli hale getirmek.

### Proje Ekibindeki Kişiler
- Yusuf Enes Demir (225260001)
- Mert Arslan (225260051)
- Yusuf Talha Yıldırım (225260085)

## Proje Özeti

Gereksinimler ve Varlık İsimleri ile Primary Key'ler
## 1. Müşteri Yönetimi
 **Varlık:** Customer
 **Primary Key**: Customer_id
**Gereksinimler:**
Müşterilerin adı, telefon numarası ve e-posta adresi gibi iletişim bilgileri saklanmalıdır.
Müşteri, sisteme rezervasyon yapabilmek ve fatura oluşturabilmek için eklenmelidir.
Müşteriler, otel hakkında değerlendirme yapabilir ve yorum bırakabilir.
## 2. Oda Yönetimi
**Varlık:** Room
 **Primary Key:** Room_id
**Gereksinimler:**
 Her oda için benzersiz bir kimlik numarası (Room_id) tanımlanmalıdır.
 Odaların tipi (örneğin, tek kişilik, çift kişilik, süit) ve fiyat bilgisi tutulmalıdır.
Odaların doluluk durumu ve müsaitlik bilgisi sürekli güncel olmalıdır.
Her oda bir otele ait olmalıdır.
# 3. Otel Yönetimi
**Varlık:** Hotel
**Primary Key:** Hotel_id
**Gereksinimler:**
Otelin adı, adresi ve puanlaması saklanmalıdır.
Otel yöneticileri, oda bilgilerini, fiyatlandırmaları, müşteri bilgilerini ve hizmet detaylarını ekleyip düzenleyebilmelidir.
Her otel, birden fazla oda ve hizmet sunabilir.
Otel hakkında yapılan değerlendirme ve puanlamalar kaydedilmelidir.
# 4. Rezervasyon Yönetimi
**Varlık:** Reservation
**Primary Key:** Reservation_id
**Gereksinimler:**
Rezervasyonlar, müşteriler ve odalarla ilişkilendirilmelidir.
Rezervasyonlar için başlangıç ve bitiş tarihi bilgisi tutulmalıdır.
Rezervasyonlar üzerinden ödeme işlemleri takip edilmelidir.
Odaların doluluk durumu, yapılan rezervasyonlara göre otomatik güncellenmelidir.
# 5. Fatura Yönetimi
**Varlık:** Bill
**Primary Key:** Bill_id
**Gereksinimler:**
Her müşteri için fatura bilgisi oluşturulmalıdır.
Faturalar, rezervasyonla ve müşteriyle ilişkilendirilmelidir.
Fatura miktarı, otel odası ve diğer hizmetlere göre hesaplanmalıdır.
Fatura tarihi ve toplam tutar bilgisi saklanmalıdır.
# 6. Değerlendirme ve Yorumlar
**Varlık:** Review
**Primary Key:** Review_id
**Gereksinimler:**
Müşteriler, otel hakkında değerlendirme (puanlama) yapabilmelidir.
Değerlendirmeler müşteriler ve otellerle ilişkilendirilmelidir.
Her değerlendirme için bir tarih ve müşteri yorumu saklanmalıdır.
# 7. Personel Yönetimi
**Varlık:** Staff
**Primary Key:** Staff_id
**Gereksinimler:**
Her otelin personel bilgileri saklanmalıdır.
Personellerin adı, unvanı ve hangi otelde çalıştığı bilgisi bulunmalıdır.
Yalnızca otel yöneticileri personel bilgilerini düzenleyebilir.
# 8. Hizmet Yönetimi
**Varlık**: Service
**Primary Key**: Service_id
**Gereksinimler:**
Her otel sunduğu hizmetlerin listesini tutmalıdır (örneğin, kahvaltı, spa, Wi-Fi).
Hizmetler, otellerle ilişkilendirilmelidir.
Hizmetlerin türü ve fiyat bilgisi saklanmalıdır.
# 9. Ödeme Yönetimi
**Varlık:** Payment
**Primary Key:** Payment_id
**Gereksinimler:**
Her rezervasyonla ilişkili ödeme bilgileri tutulmalıdır.
Ödeme işlemleri, fatura ile ilişkilendirilmelidir.
Ödeme türü (nakit, kart) ve ödeme tarihi bilgisi saklanmalıdır.
## E-R Diyagramı Varlıkları ve İlişkiler
**Customer:**
**Customer_id (Primary Key)**
**Name**
**Phone**
**Email**
## Room:
**Room_id (Primary Key)**
**Hotel_id (Foreign Key)**
**Room_Type**
**Price**
**Available**
## Hotel:
**Hotel_id (Primary Key)**
**Hotel_Name**
**Location**
**Score**
## Bill:
**Bill_id (Primary Key)**
**Customer_id (Foreign Key)**
**Date**
**Amount**
## Reservation:
**Reservation_id (Primary Key)**
**Customer_id (Foreign Key)**
**Room_id (Foreign Key)**
**Start_Date**
**End_Date**
## Review:
**Review_id (Primary Key)**
**Customer_id (Foreign Key)**
**Hotel_id (Foreign Key)**
**Rating**
**Comments**
**Comment_Date**
## İlişkiler
**Customer (Müşteri) ile Reservation (Rezervasyon):**

Her müşteri birden fazla rezervasyon yapabilir (1:N).
Her rezervasyon bir müşteri ile ilişkilidir (N:1).
Customer (Müşteri) ile Bill (Fatura):

Her müşteri birden fazla fatura alabilir (1:N).
Her fatura yalnızca bir müşteri ile ilişkilidir (N:1).

**Customer (Müşteri) ile Review (Değerlendirme):**

Her müşteri birden fazla değerlendirme yapabilir (1:N).
Her değerlendirme yalnızca bir müşteri ile ilişkilidir (N:1).

**Hotel (Otel) ile Room (Oda):**

Bir otelde birden fazla oda bulunabilir (1:N).
Her oda yalnızca bir otel ile ilişkilidir (N:1).

**Hotel (Otel) ile Review (Değerlendirme):**

Bir otel birden fazla değerlendirme alabilir (1:N).
Her değerlendirme yalnızca bir otele aittir (N:1).

**Hotel (Otel) ile Staff (Personel):**

Her otel birden fazla personel çalıştırabilir (1:N).
Her personel yalnızca bir otel ile ilişkilidir (N:1).
Hotel (Otel) ile Service (Hizmet):

Her otel birden fazla hizmet sunabilir (1:N).
Her hizmet yalnızca bir otel ile ilişkilidir (N:1).

**Room (Oda) ile Reservation (Rezervasyon):**

Her oda birden fazla rezervasyonla ilişkilendirilebilir (1:N).
Her rezervasyon yalnızca bir oda ile ilişkilidir (N:1).

**Reservation (Rezervasyon) ile Payment (Ödeme):**

Her rezervasyon birden fazla ödeme alabilir (1:N).
Her ödeme yalnızca bir rezervasyon ile ilişkilidir (N:1).

**Room (Oda) ile Room_Features (Oda Özellikleri):**

Her oda birden fazla özellikle ilişkilendirilebilir (1:N).
Her özellik yalnızca bir oda ile ilişkilidir (N:1). 

## ER DİYAGRAMI

![image](https://github.com/user-attachments/assets/3e9cef7b-9c3b-41ff-955f-ae5f740d5944)





