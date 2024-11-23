# Kafe Satış Analizi ve Tahminleme Projesi

## Projenin Amacı
Bu proje, kafe işletmelerine yönelik satış verilerinin analizi ve kısa süreli satış tahminleri oluşturmayı hedeflemektedir.
Proje kapsamında, veri seti üzerinde detaylı bir veri analizi gerçekleştirilmiş, eksik veriler düzenlenmiş, görselleştirmeler oluşturulmuş ve işletme kararlarını destekleyecek öneriler geliştirilmiştir.
Ayrıca, gelecekteki satış tahminleri için **Prophet modeli** gibi zaman serisi modelleme yaklaşımı önerilmiştir.

---

## Projeyi Hazırlayanlar
1. **Ardahan Aytan**  
   - GitHub: [github.com/ardahanaytan](https://github.com/ardahanaytan)
2. **Yağmur Aktaş**  
   - GitHub: [github.com/yamuraktas](https://github.com/yamuraktas)
3. **Kaggle**
   - https://www.kaggle.com/code/ardahanaytan/veri-analizi-bootcamp?scriptVersionId=209232651
---

## Veri Seti

### Kullanılan Veri Seti
- **Adı:** Coffee Shop Sales
- **Boyutu:** 149.116 satır ve 11 sütun
- **Sütunlar:**
  - `transaction_id`: İşlem kimliği
  - `transaction_date` & `transaction_time`: İşlem zamanı
  - `transaction_qty`: İşlem miktarı
  - `store_location`: Kafe lokasyonu
  - `product_category`: Ürün kategorisi (örneğin, Coffee, Tea, Bakery)
  - `product_type`: Ürün türü (örneğin, Gourmet brewed coffee, Brewed chai tea)
  - `unit_price`: Birim fiyatı
  - `product_detail`: Ürün detayı

---

## Proje Adımları

### 1. Veri Setinin Hazırlanması
- **Eksik Veri Ekleme:** Veri setine rastgele eksik değerler (%3 oranında) eklendi.
- **Eksik Verilerin Düzeltilmesi:** Eksik değerler için belirli kurallar uygulanarak veri temizliği yapıldı:
  - `transaction_date` ve `transaction_time`: Eksik veriler önceki değerlerle dolduruldu.
  - `product_category`: Eksik değerler `product_type` bilgisine göre dolduruldu.
  - `transaction_qty`: Ortalama değere en yakın sayıyla dolduruldu.
  - `unit_price`: Ortalama değere yakın bir fiyatla dolduruldu.
- **Zaman Bazlı Analiz İçin Hazırlık:** `transaction_date` ve `transaction_time` sütunları birleştirilerek `zaman` adında bir datetime index oluşturuldu.

---

### 2. Veri Analizi ve Görselleştirme

#### Veri Dağılımı
- En popüler ürün kategorilerinin Coffee ve Tea olduğu belirlendi. Coffee kategorisindeki en popüler ürün "Gourmet Brewed Coffee" iken, Tea kategorisinde "Brewed Chai Tea" öne çıktı.

#### Zaman Aralığı Analizi
- Sabah 7-12 arası, kahve tüketiminin en yoğun olduğu saatler olarak belirlendi. Bu saatler arasında kahveye talebin daha fazla olması, insanların işe gitmeden önce enerji ihtiyacını karşılamasıyla ilişkilendirildi.
- Saat 12-17 arasında kahve tüketimi azaldı, ancak hala sabah saatlerine göre istikrarlı bir seviyede kaldı.
- Akşam 17-24 arasında, kahve tüketimi öğle saatlerine benzer bir seviyede seyretti. Bu, akşam saatlerinde çalışanlar veya keyfi tüketim yapan müşterilerden kaynaklanıyor olabilir.

#### Kafe Bazında Analiz
- Her kafenin satış dağılımları incelendi. Coffee ve Tea tüm kafe lokasyonlarında en çok tüketilen ürün kategorileri olarak belirlendi.
- Bakery kategorisi dengeli bir şekilde tüm lokasyonlarda popülerlik gösterirken, Loose Tea, Packaged Chocolate ve Coffee Beans kategorilerinin satışlarının düşük olduğu görüldü.

#### Görselleştirme Örnekleri
- Ürün kategorilerinin toplam frekansları (bar grafikleri, yığılmış çubuk grafikleri).
- Zaman aralığına göre kahve satışlarının değişimi.
- Lokasyon bazlı ürün kategorisi satışlarının kıyaslaması.

---

### 3. Öneriler

#### Satış Artışı İçin Öneriler
1. **Bakery Ürünlerini Destekleme:**
   - Bakery ürünleri, kahve ve çayla kombinasyonlar halinde satılabilir. Örneğin, "Kahve + Scone %20 indirimli" gibi kampanyalar düzenlenebilir.
2. **Branded ve Loose Tea Ürünleri için Strateji:**
   - Bu kategoriler için tanıtım artırılabilir veya sezonluk kampanyalar düzenlenebilir. Alternatif olarak, talebin yetersiz olduğu ürünlerin menüden kaldırılması düşünülebilir.
3. **Akşam Promosyonları:**
   - Akşam saatlerinde (17-24), tatlı veya atıştırmalıklarla birlikte kahve promosyonları düzenlenebilir. Örneğin, "Akşam çayına özel paket" gibi teklifler sunulabilir.

#### Promosyon Programları
- Müşterileri daha fazla sipariş vermeye teşvik etmek için bir promosyon programı başlatılabilir:
  - "Her 5 kahve alımında 1 kahve bedava."
  - "2 veya daha fazla ürün alana ekstra puan kazandırma."

---

### 4. Model Önerisi: Prophet

**Prophet modeli**, kısa süreli satış tahminleri yapmak için uygun bir modeldir. Model, mevsimsellik, trend ve tatil günlerini dikkate alarak verimli tahminler sunar.

#### Uygulama ve Faydalar
- **Tahmin:** Belirli bir gün veya saat aralığında artacak talep öngörülebilir.
- **Stok Kontrolü:** Gelecek talebe göre stoklar optimize edilebilir, fazla veya yetersiz stok durumları önlenebilir.
- **Personel Yönetimi:** Yoğun saatler için personel düzenlemeleri yapılabilir.
- **Kârlılık Artışı:** Hedeflenen ürün kategorilerinde (örneğin Coffee ve Tea) kampanyalar düzenlenerek gelir artırılabilir.

---

## Kurulum

### Gereksinimler
Bu projeyi çalıştırmak için aşağıdaki kütüphanelere ihtiyaç vardır:
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `missingno`
- `fbprophet` (tahmin modelleri için)

### Adımlar
1. Veri setini `/kaggle/input/coffee-sales/Coffee Shop Sales.xlsx` yolunda bulundurunuz.
2. Python ortamında yukarıda belirtilen kütüphaneleri yükleyiniz.
3. Kodları adım adım çalıştırarak verilerinizi analiz edebilir ve görselleştirme yapabilirsiniz.

---

## Sonuç

Bu proje, kafe işletmelerine veri odaklı karar alma süreçlerini geliştirmeleri için bir rehber sunmaktadır. 
Geliştirilen analizler ve öneriler, işletmelerin satışlarını artırmalarına ve müşteri memnuniyetini sağlamalarına yardımcı olmayı hedeflemektedir. 
Prophet modeli gibi zaman serisi tahmin yöntemleri, gelecekteki talepleri öngörmek ve işletme operasyonlarını optimize etmek için kullanılabilir.
